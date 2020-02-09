Role Name
=========

selinux: Selinux

[![Build Status](https://travis-ci.org/cmihai-ansible/selinux.svg?branch=master)](https://travis-ci.org/cmihai-ansible/selinux)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.selinux](https://galaxy.ansible.com/devops-toolbox.selinux)

```bash
ansible-galaxy install devops-toolbox.selinux
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
selinux_packages_state: present
selinux_remove_packages: true
selinux_enable_service: true
selinux_enable_selinux: true
selinux_copy_templates: true
selinux_firewall_configure: true
selinux_firewall_rules:
  - service: ssh
  - port: 3389
selinux_users:
  - user: devops
    group: docker
selinux_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install selinux on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: selinux is configured
      import_role:
        name: devops-toolbox.selinux
      vars:
        selinux_packages_state: present
        selinux_remove_packages: true
        selinux_enable_service: true
        selinux_enable_selinux: true
        selinux_copy_templates: true
        selinux_firewall_configure: true
        selinux_firewall_rules:
          - service: ssh
          - port: 3389
        selinux_users:
          - user: devops
            group: docker
        selinux_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: selinux
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
