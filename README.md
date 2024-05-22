# gfs2

[![ansible-lint.yml](https://github.com/linux-system-roles/gfs2/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/linux-system-roles/gfs2/actions/workflows/ansible-lint.yml) [![ansible-test.yml](https://github.com/linux-system-roles/gfs2/actions/workflows/ansible-test.yml/badge.svg)](https://github.com/linux-system-roles/gfs2/actions/workflows/ansible-test.yml) [![codeql.yml](https://github.com/linux-system-roles/gfs2/actions/workflows/codeql.yml/badge.svg)](https://github.com/linux-system-roles/gfs2/actions/workflows/codeql.yml) [![markdownlint.yml](https://github.com/linux-system-roles/gfs2/actions/workflows/markdownlint.yml/badge.svg)](https://github.com/linux-system-roles/gfs2/actions/workflows/markdownlint.yml) [![python-unit-test.yml](https://github.com/linux-system-roles/gfs2/actions/workflows/python-unit-test.yml/badge.svg)](https://github.com/linux-system-roles/gfs2/actions/workflows/python-unit-test.yml) [![shellcheck.yml](https://github.com/linux-system-roles/gfs2/actions/workflows/shellcheck.yml/badge.svg)](https://github.com/linux-system-roles/gfs2/actions/workflows/shellcheck.yml) [![woke.yml](https://github.com/linux-system-roles/gfs2/actions/workflows/woke.yml/badge.svg)](https://github.com/linux-system-roles/gfs2/actions/workflows/woke.yml)

Configure and manage the Global File System 2 (gfs2), a cluster file system in a pacemaker cluster.

## Supported Distributions

* RHEL-8+, CentOS-8+
* Fedora

## Requirements

You must have a working HA cluster.

### Collection requirements

This role uses the `storage` system role.  Please run the following command line
to install it:

```bash
ansible-galaxy collection install -vv -r meta/collection-requirements.yml
```

## Role Variables

See [meta/argument_specs.yml](meta/argument_specs.yml)

## Examples

### Minimal example

```yaml
- name: Configure a GFS2 filesystem on the cluster
  hosts: myapp-servers
  roles:
    - role: linux-system-roles.gfs2
      vars:
        gfs2_cluster_name: myapp-cluster
        gfs2_file_systems:
          - name: myapp-shared-fs
            pvs:
              - /dev/disk/by-path/pci-0000:42:00.0-fc-0xf000-lun-1
            vg: vg_myapp_shared
            lv: lv_myapp_shared
            lv_size: 100G
            mount_point: /mnt/myapp-shared
```

### Minimal example with cluster setup

```yaml
- name: Configure a cluster and a GFS2 filesystem
  hosts: cluster-virts
  vars:
    common_cluster_name: MyCluster
  pre_tasks:
    - name: Check whether cluster has been set up yet
      # We do this because the ha_cluster role removes any resources not specified
      # by its variables. It is safer to run ha_cluster in a separate one-off
      # playbook which will not be used again after the gfs2 resources are created.
      ansible.builtin.command: pcs stonith status
      register: cluster_exists
      changed_when: false
      failed_when: false

    - name: Create cluster if it doesn't exist
      ansible.builtin.include_role:
        name: linux-system-roles.ha_cluster
      vars:
        ha_cluster_cluster_name: "{{ common_cluster_name }}"
        ha_cluster_enable_repos: false
        # Users should vault-encrypt the password
        ha_cluster_hacluster_password: hunter2
        ha_cluster_fence_virt_key_src: fence_xvm.key
        ha_cluster_cluster_properties:
          - attrs:
            - name: stonith-enabled
              value: "true"
        ha_cluster_resource_primitives:
          - id: xvm-fencing
            agent: "stonith:fence_xvm"
      when:
        - cluster_exists.rc != 0
          or "Started" not in cluster_exists.stdout
  roles:
    - role: linux-system-roles.gfs2
      vars:
        gfs2_cluster_name: "{{ common_cluster_name }}"
        # Specify 2 gfs2 file systems
        gfs2_file_systems:
          - name: fs1
            pvs:
              - /dev/disk/by-path/virtio-pci-0000:00:08.0
            vg: vg_gfs2_1
            lv: lv_gfs2_1
            lv_size: 100G
            mount_point: /mnt/test1
          - name: fs2
            pvs:
              - /dev/disk/by-path/virtio-pci-0000:01:00.0
            vg: vg_gfs2_2
            lv: lv_gfs2_2
            lv_size: 100G
            mount_point: /mnt/test2
```

### Example with optional role variables

```yaml
- name: Configure a GFS2 filesystem with optional variables
  hosts: cluster-virts
  roles:
    - role: linux-system-roles.gfs2
      vars:
        gfs2_cluster_name: MyCluster
        gfs2_resource_name_lvmlockd: lvm_locking
        gfs2_resource_name_dlm: dlm_control
        gfs2_group_name_locking: locking
        gfs2_file_systems:
          - name: fs1
            resource_name_fs: gfs2-1
            pvs:
              - /dev/disk/by-path/virtio-pci-0000:00:08.0
            vg: vg_gfs2_1
            lv: lv_gfs2_1
            lv_size: 100G
            resource_name_lv: shared-lv-1
            journals: 3
            mount_point: /mnt/test1
            mount_options:
              - noatime
            state: enabled
          - name: fs2
            resource_name_fs: gfs2-2
            pvs:
              - /dev/disk/by-path/virtio-pci-0000:01:00.0
            vg: vg_gfs2_2
            lv: lv_gfs2_2
            lv_size: 100G
            resource_name_lv: shared-lv-2
            journals: 3
            mount_point: /mnt/test2
            mount_options:
              - rgrplvb
            state: disabled
```

## rpm-ostree

See README-ostree.md

## License

MIT

## Author Information

Andrew Price
