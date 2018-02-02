# ansible-role-ssh

[![Build Status](https://travis-ci.org/CMcDonald82/ansible-role-ssh.svg?branch=master)](https://travis-ci.org/CMcDonald82/ansible-role-ssh)

Ansible role for configuring SSH access and fail2ban on an Ubuntu server

This role disables root login and password authentication.

NOTE: PasswordAuthentication should be set to 'no' by default in sshd_config in Ubuntu 16.04

NOTE: This role adds some common security-hardening features to your server but IS NOT meant to be a comprehensive, bulletproof security solution. It is also recommended to further research and customize the security of your server setup to suit your needs. 

## Requirements

None

## Role Variables

```
server_security_ssh_password_authentication: no
server_security_ssh_permit_root_login: no
```

The security settings for SSH authentication. The possible values are booleans (true/false, yes/no). These are inserted into the sshd_config file. These should usually be set to the default (no) but sometimes, such as when you are initially configuring a server or do not have key-based auth in place, it may be appropriate to set these to yes.

```
server_security_enable_fail2ban: true
```

Leave this set to true (the default) if you want to install & enable fail2ban. If you're already using another tool for auth/intrusion detection, you may want to set this to false.

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