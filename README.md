Role Name
=========

firewalld: Firewalld

[![Build Status](https://travis-ci.org/cmihai-ansible/firewalld.svg?branch=master)](https://travis-ci.org/cmihai-ansible/firewalld)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.firewalld](https://galaxy.ansible.com/devopstoolbox.firewalld)

```bash
ansible-galaxy install devopstoolbox.firewalld
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
firewalld_packages_state: present
firewalld_remove_packages: true
firewalld_enable_service: true
firewalld_enable_selinux: true
firewalld_copy_templates: true
firewalld_firewall_configure: true
firewalld_firewall_rules:
  - service: ssh
  - port: 3389
firewalld_users:
  - user: devops
    group: docker
firewalld_selinux_booleans:
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
- name: Install firewalld on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: firewalld is configured
      import_role:
        name: devopstoolbox.firewalld
      vars:
        firewalld_packages_state: present
        firewalld_remove_packages: true
        firewalld_enable_service: true
        firewalld_enable_selinux: true
        firewalld_copy_templates: true
        firewalld_firewall_configure: true
        firewalld_firewall_rules:
          - service: ssh
          - port: 3389
        firewalld_users:
          - user: devops
            group: docker
        firewalld_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: firewalld
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
