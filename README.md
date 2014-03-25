What is it?
-----------

Ansible recipe to prepare debian-based Xen host to create Ubuntu guests.


## Walkthrough

The Ubuntu Precise distribution does not included into Debian Squeeze so fix it.

* Create a distribution
* Create a debootstrap script


## How to run

```bash
ansible-playbook recipe.yml -i hosts.example -S --ask-su-pass
```
