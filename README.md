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

# key value config pair
sshd_config:
- key: ListenAddress
  value: "{{ ansible_default_ipv4.address }}"
- key: AllowUsers
  value: "galexrt@*"
  state: absent # a valid ansible lineinfile module state
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
