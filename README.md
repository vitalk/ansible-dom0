dom0
====

Ansible recipe to prepare debian-based Xen host to create Ubuntu guests.

The Ubuntu Precise distribution does not included into Debian Squeeze
so fix it:

* Creates a missed distribution
* Creates a missed debootstrap script

Role Variables
--------------

At that moment role does not support any configuration.

Example Playbook
----------------

```bash
ansible-playbook recipe.yml -i hosts.example -S --ask-su-pass
```

```yaml
# file: recipe.yml
---
- hosts: mybox
  roles:
    - .
```

License
-------

Licensed under the [MIT license](http://mit-license.org/vitalk).

Author Information
------------------

Created by Vital Kudzelka.

Don't hesitate create [a GitHub Issue](https://github.com/vitalk/ansible-dom0/issues) if you have any suggestions or found a bug.
