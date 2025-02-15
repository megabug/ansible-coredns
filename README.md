# Ansible Role: CoreDNS

[![Build Status](https://travis-ci.com/cloudalchemy/ansible-coredns.svg?branch=master)](https://travis-ci.com/cloudalchemy/ansible-coredns)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/badge/ansible%20role-cloudalchemy.coredns-blue.svg)](https://galaxy.ansible.com/cloudalchemy/coredns/)
[![GitHub tag](https://img.shields.io/github/tag/cloudalchemy/ansible-coredns.svg)](https://github.com/cloudalchemy/ansible-coredns/tags)

## Description

Deploy [CoreDNS](https://github.com/coredns/coredns) using ansible.

## Requirements

- Ansible >= 2.7 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name                       | Default Value       | Description                                                                                                                                                                                                        |
| -------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `coredns_version`          | 1.8.3               | CoreDNS package version                                                                                                                                                                                            |
| `coredns_binary_local_dir` | ""                  | Allows to use local packages instead of ones distributed on github. As parameter it takes a directory where `coredns` binary is stored on host on which ansible is ran. This overrides `coredns_version` parameter |
| `coredns_dns_port`         | 53                  | Port on which CoreDNS will listen for DNS requests                                                                                                                                                                 |
| `coredns_config_names`     | []                  | List containing config files to enable                                                                                                                                                                             |
| `coredns_zone_files_paths` | ["coredns/zones/*"] | List containing paths to zone files                                                                                                                                                                                |

## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - cloudalchemy.coredns
```

## Zone files

The role will search in the paths defined in `coredns_zone_files_paths` in the Ansible templates paths for files to deploy. These can be used with the [`file` plugin](https://coredns.io/plugins/file/).

## Local Testing

The preferred way of locally testing the role is to use Docker and [molecule](https://github.com/ansible-community/molecule) (v3.x). You will have to install Docker on your system. See "Get started" for a Docker package suitable to for your system. Running your tests is as simple as executing `molecule test`.

## Continuous Intergation

Combining molecule and circle CI allows us to test how new PRs will behave when used with multiple ansible versions and multiple operating systems. This also allows use to create test scenarios for different role configurations. As a result we have a quite large test matrix which can take more time than local testing, so please be patient.

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## Troubleshooting

See [troubleshooting](TROUBLESHOOTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
