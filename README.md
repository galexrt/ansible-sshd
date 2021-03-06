ansible-sshd
============

[![Build Status](https://travis-ci.org/galexrt/ansible-sshd.svg?branch=master)](https://travis-ci.org/galexrt/ansible-sshd)

An Ansible role to configure sshd.

Inspired by https://github.com/willshersystems/ansible-sshd.

Requirements
------------

No special requirements.

Role Variables
--------------

```
# location, group, owner and mode of the sshd_config
sshd_config_file: "/etc/ssh/sshd_config"
sshd_config_group: "root"
sshd_config_owner: "root"
sshd_config_mode: "0600"

# if openssh-server should be installed
sshd_packages_install: true
# the packages to install for openssh server
sshd_packages:
  - openssh
  - openssh-server

sshd_service: sshd

sshd_listen_addresses: []
sshd_listen_addresses_auto_detect: true
sshd_listen_addresses_default_to_v4: true
sshd_listen_addresses_default_to_v6: true

sshd_subsystem_sftp: "/usr/lib/openssh/sftp-server"

sshd_use_default: true
sshd_use_default_dist: true
sshd_config_default_dist: {}
sshd_config_default:
  ListenAddress: "{{ sshd_listen_addresses|default([], true) }}"
  Protocol: 2
  LogLevel: INFO
  LoginGraceTime: 120
  PermitRootLogin: without-password
  PermitEmptyPasswords: no
  PubkeyAuthentication: yes
  AuthorizedKeysFile: .ssh/authorized_keys
  PasswordAuthentication: no
  HostbasedAuthentication: no
  ChallengeResponseAuthentication: no
  GSSAPIAuthentication: yes
  GSSAPICleanupCredentials: no
  UsePAM: yes
  X11Forwarding: yes
  IgnoreRhosts: yes
  AcceptEnv:
    - LANG LC_CTYPE LC_NUMERIC LC_TIME LC_COLLATE LC_MONETARY LC_MESSAGES
    - LC_PAPER LC_NAME LC_ADDRESS LC_TELEPHONE LC_MEASUREMENT
    - LC_IDENTIFICATION LC_ALL LANGUAGE
    - XMODIFIERS
  Subsystem:
    - "sftp {{ sshd_subsystem_sftp }}"

# key value config pairs like above
sshd_config: {}
```

Dependencies
------------

Depends on:
* [galexrt.common-facts](https://galaxy.ansible.com/galexrt/common-facts/) ([Github galexrt/ansible-common-facts](https://github.com/galexrt/ansible-common-facts)).

Example Playbook
----------------

An example playbook on how to use this role:
```
- hosts: servers
  roles:
    - { role: galexrt.sshd, sshd_packages_install: true
     }
```

License
-------

Apache 2.0

Author Information
------------------

If you have problems with the role, feel free to create an issue on Github or contact me by mail.
