# vmware_deploy

## Table Of Contents

* [About](#about)
* [Role Defaults](#role-defaults)
* [License](#license)
* [Author](#author)

## About

> This role creates a new virtual machine using my ESXi server and the vmware_guest module. The defaults are currently set up for my infrastructure, but can be overriden for application specific uses. Also, many of these variables can be overriden at the host level for changes in configurations between hosts. 
>
> Note: This role expects the variables "esxi_host", "vsphere_host", "vsphere_password", and "vshere_user" to be passed, either via the command line or via AWX. Defaults can also be used. 

[Back to table of contents](#table-of-contents)

## Role Defaults

**Quicklist**: [guest_dns_server](#guest_dns_server), [guest_domain_name](#guest_domain_name),
[guest_gateway](#guest_gateway), [guest_id](#guest_id),
[guest_memory](#guest_memory), [guest_netmask](#guest_netmask),
[guest_network](#guest_network), [guest_template](#guest_template),
[guest_vcpu](#guest_vcpu), [hdd_gb](#hdd_gb), [hdd_type](#hdd_type),
[vsphere_datacenter](#vsphere_datacenter),
[vsphere_datastore](#vsphere_datastore), [vsphere_folder](#vsphere_folder),
[vsphere_host](#vsphere_host), [vsphere_user](#vsphere_user)

### guest_dns_server 

* *help*: TODO.
* *default*: ``172.16.1.2``

[Back to table of contents](#table-of-contents)

### guest_domain_name 

* *help*: TODO.
* *default*: ``plumbus.lab``

[Back to table of contents](#table-of-contents)

### guest_gateway 

* *help*: TODO.
* *default*: ``172.16.1.1``

[Back to table of contents](#table-of-contents)

### guest_id 

* *help*: TODO.
* *default*: ``ubuntu64Guest``

[Back to table of contents](#table-of-contents)

### guest_memory 

* *help*: TODO.
* *default*: ``1024``

[Back to table of contents](#table-of-contents)

### guest_netmask 

* *help*: TODO.
* *default*: ``255.255.255.0``

[Back to table of contents](#table-of-contents)

### guest_network 

* *help*: TODO.
* *default*: ``prod``

[Back to table of contents](#table-of-contents)

### guest_template 

* *help*: TODO.
* *default*: ``Basic Ubuntu 18.04.2``

[Back to table of contents](#table-of-contents)

### guest_vcpu 

* *help*: TODO.
* *default*: ``1``

[Back to table of contents](#table-of-contents)

### hdd_gb 

* *help*: TODO.
* *default*: ``32``

[Back to table of contents](#table-of-contents)

### hdd_type 

* *help*: TODO.
* *default*: ``thin``

[Back to table of contents](#table-of-contents)

### vsphere_datacenter 

* *help*: TODO.
* *default*: ``Lab``

[Back to table of contents](#table-of-contents)

### vsphere_datastore 

* *help*: TODO.
* *default*: ``Dev RAID``

[Back to table of contents](#table-of-contents)

### vsphere_folder 

* *help*: TODO.
* *default*: ``/Dev``

[Back to table of contents](#table-of-contents)

### vsphere_host 

* *help*: TODO.

[Back to table of contents](#table-of-contents)

### vsphere_user 

* *help*: TODO.

[Back to table of contents](#table-of-contents)

## License

license (GPL-2.0-or-later, MIT, etc)

[Back to table of contents](#table-of-contents)

## Author

Derek Smiley

Not claiming as my original work, got part from an ansible-galaxy role and other websites

[Back to table of contents](#table-of-contents)
