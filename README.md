ansible-sshd
============

[![Build Status](https://travis-ci.org/galexrt/ansible-sshd.svg?branch=master)](https://travis-ci.org/galexrt/ansible-sshd)

An Ansible role to configure sshd.

Requirements
------------

No special requirements.

Role Variables
--------------

```
# location of sshd_config
sshd_config_file: "/etc/ssh/sshd_config"

# if openssh-server should be installed
sshd_install: true

sshd_listen_address: ""
sshd_listen_address_interface: "eth0"

# will be automatically detected
sshd_subsystem_sftp: "/usr/libexec/openssh/sftp-server"

sshd_use_default: true
# this is the default config
sshd_config_default:
  ListenAddress: "{{ sshd_listen_address|default('', true) }}"
  HostKey:
    - /etc/ssh/ssh_host_rsa_key
    - /etc/ssh/ssh_host_ecdsa_key
    - /etc/ssh/ssh_host_ed25519_key
  SyslogFacility: AUTHPRIV
  LogLevel: INFO
  PermitRootLogin: without-password
  AuthorizedKeysFile: .ssh/authorized_keys
  PasswordAuthentication: no
  ChallengeResponseAuthentication: no
  GSSAPIAuthentication: no
  GSSAPICleanupCredentials: no
  UsePAM: yes
  X11Forwarding: no
  AcceptEnv:
    - LANG LC_CTYPE LC_NUMERIC LC_TIME LC_COLLATE LC_MONETARY LC_MESSAGES
    - LC_PAPER LC_NAME LC_ADDRESS LC_TELEPHONE LC_MEASUREMENT
    - LC_IDENTIFICATION LC_ALL LANGUAGE
    - XMODIFIERS
  Subsystem:
    - "sftp	{{ sshd_subsystem_sftp }}"

# this config will be merged with sshd_config_default when sshd_use_default is true
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
    - { role: galexrt.sshd, sshd_install: true
     }
```

License
-------

Apache 2.0

Author Information
------------------

If you have problems with the role, feel free to create an issue on Github or contact me by mail.
