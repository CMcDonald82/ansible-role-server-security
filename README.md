# ansible-role-ssh

Ansible role for configuring SSH access on an Ubuntu server

This role disables root login and password authentication.

NOTE: PasswordAuthentication should be set to 'no' by default in sshd_config in Ubuntu 16.04

## Requirements

None

## Role Variables

None

## Example Playbook

```
- name: Configure SSH on Ubuntu server
  hosts: all
  remote_user: "{{ remote_username }}"
  become: yes

  roles:
    - role: ssh_role
```

## Dependencies 

None