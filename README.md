# GitHub Runner and Docker Setup Ansible Roles

This repository contains two Ansible roles:
1. `github_runner`: Sets up a GitHub self-hosted runner on Ubuntu.
2. `docker_setup`: Installs Docker and Docker Compose on Ubuntu.

## Requirements

These roles require Ansible to be installed on the control machine. The target nodes should be running Ubuntu 22.04 or later.

## Role Variables

### github_runner

| Variable          | Default Value         | Description                                                         |
|-------------------|-----------------------|---------------------------------------------------------------------|
| `runner_version`  | `"2.316.1"`           | The version of the GitHub runner to install.                        |
| `github_org`      | `"your-github-org"`   | The GitHub organization to which the runner will be registered.     |
| `runner_name`     | `"runner-{{ inventory_hostname }}"` | The name of the runner.                               |
| `runner_labels`   | `"self-hosted,{{ inventory_hostname }}"` | Labels to assign to the runner.                        |
| `github_token`    | `"YOUR_GITHUB_TOKEN"` | The GitHub token to register the runner.                           |

### docker_setup

| Variable               | Default Value | Description                                      |
|------------------------|---------------|--------------------------------------------------|
| `docker_version`       | `"5:20.10"`   | The version of Docker to install.                |
| `docker_compose_version` | `"1.29.2"`   | The version of Docker Compose to install.        |

## Dependencies

None.

## Example Playbook

### Setting up GitHub Runner

```yaml
- hosts: servers
  roles:
    - role: github_runner
      vars:
        runner_version: "2.316.1"
        github_org: "your-github-org"
        runner_name: "my-runner"
        runner_labels: "self-hosted,my-runner"
        github_token: "YOUR_GITHUB_TOKEN"
```

### Setting up Docker and Docker Compose

```yaml
- hosts: servers
  roles:
    - role: docker_setup
      vars:
        docker_version: "5:20.10"
        docker_compose_version: "1.29.2"
```

### Full Playbook Example

```yaml
- hosts: servers
  roles:
    - role: github_runner
      vars:
        runner_version: "2.316.1"
        github_org: "your-github-org"
        runner_name: "my-runner"
        runner_labels: "self-hosted,my-runner"
        github_token: "YOUR_GITHUB_TOKEN"

    - role: docker_setup
      vars:
        docker_version: "5:20.10"
        docker_compose_version: "1.29.2"
```

## License

BSD

## Author Information

These roles were created by [Your Name](mailto:your-email@example.com). For more information, visit [your website](http://yourwebsite.com).
