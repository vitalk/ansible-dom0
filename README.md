dom0
====

Ansible recipe to prepare debian-based Xen host to manage Ubuntu guests.

The Ubuntu Precise distribution does not included into Debian Squeeze
so fix it:

* Creates a missed distribution
* Creates a missed debootstrap script

Role Variables
--------------

Option | Description
---|---
`dom0_cachedir` | The directory uses to cache packages while bootstraping a new system.
`dom0_vms` | The list of guests vm to create (optional). Each list item may contains the following variables.
`vm_name` | The name of the new instance.
`vm_password` | The root password for the new instance.
`vm_vcpus` | The number of vcpus that the new instance will have.
`vm_size` | The size of the primary disk image.
`vm_memory` | The amount of memory allocated to the new instance.
`vm_swap` | The size of the swap partition.
`vm_fs` | The filesystem type to use for the new istance.
`vm_lvm` | The volume group to save images within.
`vm_dist` | The distribution you wish to install.
`vm_mirror` | The mirror to use when installing via debootstrap.
`vm_hostname` | The hostname of the new guest system. Ideally this will be FQDN.
`vm_ip` | The IP address of the machine.
`vm_mac` | The MAC address to use for a given interface.
`vm_gateway` | The network gateway for the new instance.
`vm_broadcast` | The broadcast address for the new instance.
`vm_netmask` | The netmask for the new instance.
`vm_boot` | Boot the new instance after creating it.
`vm_destroy` | Destroy the existing guest system by its `vm_hostname`, e.g. remove any system logical volumes and configs.

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

```yaml
# file: group_vars/all
---
dom0_cachedir: /var/cache/xen
dom0_vms:
  - vm_name: myapp
    vm_password: r00tpass
    vm_vcpus: 1
    vm_size: 10gb
    vm_memory: 512mb
    vm_swap: 512mb
    vm_lvm: sandbox
    vm_fs: ext4
    vm_dist: precise
    vm_hostname: myapp.at.mybox
    vm_ip: 192.168.1.42
    vm_gateway: 192.168.1.1
    vm_broadcast: 192.168.1.255
    vm_netmask: 255.255.255.0
    vm_mac: "00:16:3e:a5:0c:cd"
    vm_mirror: "http://archive.ubuntu.com/ubuntu/"
    vm_boot: true
    vm_destroy: false
```

License
-------

Licensed under the [MIT license](http://mit-license.org/vitalk).

Author Information
------------------

Created by Vital Kudzelka.

Don't hesitate create [a GitHub Issue](https://github.com/vitalk/ansible-dom0/issues) if you have any suggestions or found a bug.
