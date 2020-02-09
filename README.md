Role Name
=========

spark: Spark

[![Build Status](https://travis-ci.org/cmihai-ansible/spark.svg?branch=master)](https://travis-ci.org/cmihai-ansible/spark)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.spark](https://galaxy.ansible.com/devopstoolbox.spark)

```bash
ansible-galaxy install devopstoolbox.spark
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
spark_packages_state: present
spark_remove_packages: true
spark_enable_service: true
spark_enable_selinux: true
spark_copy_templates: true
spark_firewall_configure: true
spark_firewall_rules:
  - service: ssh
  - port: 3389
spark_users:
  - user: devops
    group: docker
spark_selinux_booleans:
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
- name: Install spark on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: spark is configured
      import_role:
        name: devopstoolbox.spark
      vars:
        spark_packages_state: present
        spark_remove_packages: true
        spark_enable_service: true
        spark_enable_selinux: true
        spark_copy_templates: true
        spark_firewall_configure: true
        spark_firewall_rules:
          - service: ssh
          - port: 3389
        spark_users:
          - user: devops
            group: docker
        spark_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: spark
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
