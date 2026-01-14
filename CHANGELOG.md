Changelog
=========

[1.0.5] - 2026-01-13
--------------------

### Other Changes

- ci: bump actions/checkout from 5 to 6 (#72)
- ci: add qemu tests for Fedora 43, drop Fedora 41 (#73)
- ci: bump actions/upload-artifact from 5 to 6 (#74)
- ci: use ANSIBLE_INJECT_FACT_VARS=false by default for testing (#75)
- refactor: handle INJECT_FACTS_AS_VARS=false by using ansible_facts instead (#76)

[1.0.4] - 2025-11-17
--------------------

### Bug Fixes

- fix: cannot use community-general version 12 - no py27 and py36 support (#70)

### Other Changes

- ci: ansible-plugin-scan is disabled for now (#39)
- ci: bump ansible-lint to v25; provide collection requirements for ansible-lint (#42)
- ci: Check spelling with codespell (#43)
- ci: Add test plan that runs CI tests and customize it for each role (#44)
- ci: In test plans, prefix all relate variables with SR_ (#45)
- ci: Fix bug with ARTIFACTS_URL after prefixing with SR_ (#46)
- ci: several changes related to new qemu test, ansible-lint, python versions, ubuntu versions (#47)
- ci: use tox-lsr 3.6.0; improve qemu test logging (#48)
- ci: skip storage scsi, nvme tests in github qemu ci (#49)
- ci: bump sclorg/testing-farm-as-github-action from 3 to 4 (#50)
- ci: bump tox-lsr to 3.8.0; rename qemu/kvm tests (#51)
- ci: Add Fedora 42; use tox-lsr 3.9.0; use lsr-report-errors for qemu tests (#52)
- ci: Add support for bootc end-to-end validation tests (#53)
- ci: Use ansible 2.19 for fedora 42 testing; support python 3.13 (#54)
- ci: bump actions/checkout from 4 to 5 (#55)
- ci: rollout several recent changes to CI testing (#57)
- ci: support openSUSE Leap in qemu/kvm test matrix (#58)
- ci: use the new epel feature to enable EPEL for testing farm (#59)
- ci: use tox-lsr 3.12.0 for osbuild_config.yml feature (#61)
- ci: use JSON format for __bootc_validation (#62)
- ci: bump actions/setup-python from 5 to 6 (#63)
- ci: bump actions/github-script from 7 to 8 (#64)
- ci: bump actions/upload-artifact from 4 to 5 (#65)
- ci: bump github/codeql-action from 3 to 4 (#66)
- ci: use versioned upload-artifact instead of master; bump codeql-action to v4; bump upload-artifact to v5 (#67)
- ci: bump tox-lsr to 3.13.0 (#68)
- ci: bump tox-lsr to 3.14.0 - this moves standard-inventory-qcow2 to tox-lsr (#69)

[1.0.3] - 2025-01-09
--------------------

### Other Changes

- ci: bump codecov/codecov-action from 4 to 5 (#35)
- ci: Use Fedora 41, drop Fedora 39 (#36)
- ci: Use Fedora 41, drop Fedora 39 - part two (#37)

[1.0.2] - 2024-11-19
--------------------

### Bug Fixes

- fix: remove el10 support (#33)

[1.0.1] - 2024-10-30
--------------------

### Other Changes

- ci: Add tags to TF workflow, allow more [citest bad] formats (#27)
- ci: ansible-test action now requires ansible-core version (#28)
- ci: add YAML header to github action workflow files (#29)
- refactor: Use vars/RedHat_N.yml symlink for CentOS, Rocky, Alma wherever possible (#31)

[1.0.0] - 2024-08-22
--------------------

### New Features

- feat: role does not work on el10, aarch64 (#25)

### Other Changes

- ci: Add tft plan and workflow (#19)
- ci: Update fmf plan to add a separate job to prepare managed nodes (#21)
- ci: Bump sclorg/testing-farm-as-github-action from 2 to 3 (#22)
- ci: Add workflow for ci_test bad, use remote fmf plan (#23)
- ci: Fix missing slash in ARTIFACTS_URL (#24)

[0.0.4] - 2024-07-02
--------------------

### Bug Fixes

- fix: add support for EL10 (#17)

### Other Changes

- ci: ansible-lint action now requires absolute directory (#16)

[0.0.3] - 2024-06-11
--------------------

### Other Changes

- ci: Bump mathieudutour/github-tag-action from 6.1 to 6.2 (#2)
- docs: Update README.md to clarify purpose of gfs2 role (#9)
- ci: use tox-lsr 3.3.0 which uses ansible-test 2.17 (#10)
- ci: tox-lsr 3.4.0 - fix py27 tests; move other checks to py310 (#13)
- ci: Add supported_ansible_also to .ansible-lint (#14)

[0.0.2] - 2024-04-25
--------------------

### Other Changes

- test: do not enable repos on RedHat systems (#6)

[0.0.1] - 2024-04-25
--------------------

### New Features

- feat: gfs2 role to manage GFS2 clustered filesystems (#1)

### Other Changes

- ci: fix ci tests (#4)

