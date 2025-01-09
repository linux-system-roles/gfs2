Changelog
=========

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

