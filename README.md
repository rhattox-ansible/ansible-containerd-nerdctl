# ansible-containerd-nerdctl

Ansible role to automate the installation and setup of [nerdctl](https://github.com/containerd/nerdctl) for [containerd](https://containerd.io/).

## Features

- Downloads and installs nerdctl (configurable version)
- Sets up rootless mode
- Installs prerequisites (e.g., `uidmap`)
- Creates a symbolic link from `nerdctl` to `docker`
- Cleans up temporary files

## Role Variables

Default variables are defined in `setup/defaults/main.yaml`:

- `nerdctl_version`: Version of nerdctl to install (default: `2.1.3`)
- `nerdctl_url`: Download URL for nerdctl
- `install_path`: Path to install binaries (default: `/usr/local/bin`)
- `temporary_folder`: Temporary working directory

## Directory Structure

```
ansible.cfg
main.yaml                # Example playbook
setup/
  defaults/
    main.yaml            # Default variables
  tasks/
    main.yaml            # Main task list
    setup_temporary_folder.yaml
    download_files.yaml
    extract_files.yaml
    copy_files.yaml
    post_install.yaml
    cleanup.yaml
LICENSE
README.md
```

## Usage

Example playbook (`main.yaml`):

```yaml
- name: ContainerD NerdCTL Installation
  hosts: localhost
  become: true
  gather_facts: true
  vars:
    ansible_python_interpreter: /opt/ansible-venv/bin/python
  roles:
    - setup
```

## Requirements

- Ansible 2.9+
- Linux host
- Internet access to download nerdctl

## License

MIT

## Author

[rhattox-ansible](https://github.com/rhattox-ansible)
