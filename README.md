ansible-sshd
============

[![Build Status](https://travis-ci.org/galexrt/ansible-sshd.svg?branch=master)](https://travis-ci.org/galexrt/ansible-sshd)

An Ansible role to configure sshd.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

An example playbook on how to use this role:

    - hosts: servers
      roles:
         - { role: galexrt.sshd }

License
-------

Apache 2.0 License

Author Information
------------------

If you have problems with the role, feel free to create an issue on Github or contact me by mail.
