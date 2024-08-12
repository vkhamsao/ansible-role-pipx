# Ansible Role: Pip (for Python)

[![CI](https://github.com/vkhamsao/ansible-role-pipx/workflows/CI/badge.svg?event=push)](https://github.com/vkhamsao/ansible-role-pipx/actions?query=workflow%3ACI)

An Ansible Role that installs [Pipx](https://pipx.pypa.io/stable/) on Linux.



## Role Variables
Available variables are listed below:
```yaml
pipx_package_name: "pipx" # Name of the pipx package
pipx_install_packages: [] # List of packages to install see module documentation and example below
```

## Dependencies
[community.general.pipx](https://docs.ansible.com/ansible/latest/collections/community/general/pipx_module.html) module.

## Example Playbook

# Installs pipx to manage python global cli tools
```yaml
- name: Install and setup pipx
  hosts: all
  become: false
  roles:
  - pipx
  vars:
    pipx_install_packages:
      - name: twine
        state: latest
      - name: yamllint
        state: latest
        install_deps: true
      - name: molecule
        state: inject
        install_apps: true
        install_deps: true
        inject_packages:
          - molecule-docker
          - molecule-podman
          - molecule-vagrant
          - name: docker
```
