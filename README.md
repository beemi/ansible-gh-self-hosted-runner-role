# GitHub Runner and Docker Setup Ansible Roles

This repository contains two Ansible roles:
1. `github_runner`: Sets up a GitHub self-hosted runner on Ubuntu.

## Requirements

These roles require Ansible to be installed on the control machine. The target nodes should be running Ubuntu 22.04 or later.

## Role Variables

### github_runner

| Variable         | Default Value                            | Description                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------|
| `runner_version` | `"2.316.1"`                              | The version of the GitHub runner to install.                    |
| `github_org`     | `"your-github-org"`                      | The GitHub organization to which the runner will be registered. |
| `runner_name`    | `"runner-{{ inventory_hostname }}"`      | The name of the runner.                                         |
| `runner_labels`  | `"self-hosted,{{ inventory_hostname }}"` | Labels to assign to the runner.                                 |
| `github_token`   | `"YOUR_GITHUB_TOKEN"`                    | The GitHub token to register the runner.                        |

## Dependencies

None.

## License

BSD

## Author Information

These roles were created by [Raja Beemi](beemi.rajas@gmail.com)
