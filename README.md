# Reboot

[![Ansible Galaxy](http://img.shields.io/badge/galaxy-GROG.reboot-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/4667)
[![Build Status](https://travis-ci.org/GROG/ansible-role-reboot.svg?branch=master)](https://travis-ci.org/GROG/ansible-role-reboot)

A role for rebooting hosts.

## Requirements

None.

## Role Variables

| Variable | Description | Default value |
|----------|-------------|---------------|
| `reboot_message` | Reboot message for the logs | 'Reboot by Ansible' |
| `reboot_wait` | Wait for hosts to come back online? | 'yes' |
| `reboot_wait_port` | Port to check | `ansible_ssh_port` or 22 |
| `reboot_wait_delay` | Time to wait before polling the host (seconds) | 10 |
| `reboot_wait_timeout` | Timeout for host to come back up successfully (seconds) | 300 |
| `reboot_interval` | Interval between reboot and next task? | 'no' |
| `reboot_interval_seconds` | Seconds to pause after reboot | 0 |

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
  roles:
  - role: GROG.reboot
    reboot_message: 'Test reboot role'
```

#### Performing a rolling reboot:

```yaml
---
- hosts: servers
  serial: 1
  roles:
  - { role: GROG.reboot,
      become: yes,
        reboot_interval: 'yes',
        reboot_interval_seconds: 60
    }
```

## License

LGPLv3

## Contributing

All assistance, changes or ideas [welcome](https://github.com/GROG/ansible-role-reboot/issues)!

## Author Information

[G. Roggemans](https://github.com/groggemans)
