# Reboot

[![Ansible Galaxy][galaxy_image]][galaxy_link]
[![Build Status][travis_image]][travis_link]
[![Latest tag][tag_image]][tag_url]
[![Gitter chat][gitter_image]][gitter_url]

A role for rebooting hosts.

## Requirements

- Hosts should be bootstrapped for ansible usage (have python,...)
- Root privileges, eg `become: yes`

## Role Variables

| Variable                  | Description                                               | Default value                              |
|---------------------------|-----------------------------------------------------------|--------------------------------------------|
| `reboot_message`          | Reboot message for the logs                               | 'Reboot by Ansible'                        |
| `reboot_wait`             | Wait for hosts to come back online?                       | 'yes'                                      |
| `reboot_wait_host`        | Host to check                                             | `ansible_ssh_host` or `inventory_hostname` |
| `reboot_wait_port`        | Port to check                                             | `ansible_ssh_port` or 22                   |
| `reboot_wait_regex`       | String to match in the socket connection. (ex. `OpenSSH`) | /                                          |
| `reboot_wait_delay`       | Time to wait before polling the host (seconds)            | 10                                         |
| `reboot_wait_timeout`     | Timeout for host to come back up successfully (seconds)   | 300                                        |
| `reboot_wait_ctimeout`    | Timeout for each connection attempt (seconds)             | 5                                          |
| `reboot_interval`         | Interval between reboot and next task?                    | 'no'                                       |
| `reboot_interval_seconds` | Seconds to pause after reboot                             | 0                                          |

#### Attention:
All boolean values can be used with either `'yes'`/`'no'` or `true`/`false`.
This allows you to alter their value from the command line (`-e "bool=yes"`)
without problems.

## Dependencies

None.

## Example Playbook

#### Performing a basic reboot:

```yaml
---
- hosts: servers
  become: yes
  roles:
  - role: GROG.reboot
    reboot_message: 'Test reboot role'
```

#### Performing a rolling reboot:

```yaml
---
- hosts: servers
  become: yes
  serial: 1
  roles:
  - role: GROG.reboot
    reboot_interval: 'yes'
    reboot_interval_seconds: 60
```

## Contributing
All assistance, changes or ideas [welcome][issues]!

## Author
By [G. Roggemans][groggemans]

## License
MIT

[galaxy_image]:         http://img.shields.io/badge/galaxy-GROG.reboot-660198.svg?style=flat
[galaxy_link]:          https://galaxy.ansible.com/GROG/reboot
[travis_image]:         https://travis-ci.org/GROG/ansible-role-reboot.svg?branch=master
[travis_link]:          https://travis-ci.org/GROG/ansible-role-reboot
[tag_image]:            https://img.shields.io/github/tag/GROG/ansible-role-reboot.svg
[tag_url]:              https://github.com/GROG/ansible-role-reboot/tags
[gitter_image]:         https://badges.gitter.im/GROG/chat.svg
[gitter_url]:           https://gitter.im/GROG/chat

[issues]:               https://github.com/GROG/ansible-role-reboot/issues
[groggemans]:           https://github.com/groggemans
