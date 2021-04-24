VMWare-Deploy
=========

This role creates a new virtual machine using on my ESXi host utilizing the vmware_guest module. The defaults are currently set up for my infrastructure, but can be overwritten for application specific uses. Also, many of these variables can be overwritten at the host level for changes in configurations between hosts. This role expects the variables "esxi_host", "vsphere_host", "vsphere_password", and "vshere_user" to be passed, either via the command line or via AWX. Defaults or variable files can also be used.

Requirements
------------

This playbook will not work with the free version of ESXi, and the ESXi host that the virtual machine is being deployed on needs to be managed by a VCenter server. In addition, this playbook assumes that the main DNS on the network is a Windows Server. This can easily be avoided by removing that part of the role. 

Role Variables
--------------
Required variables are listed here, along with default example values. see defaults/main.yml. Many of these variables need to be overwrriten for the playbook to run. This can be done using the vars role directory, the command line, AWX, etc.

    vsphere_host: vcsa01.domain.com

This is the VCenter instance that will be used to deploy the virtual machine. 

    vsphere_datacenter: HomeLab

This is the datacenter group in VCenter the virtual machine will be added to. 

    vsphere_folder: /Production

This is the vm folder the virtual machine will be added to.

    guest_dns_servers:
      - 192.168.1.1
      - 192.168.1.2
      - 8.8.8.8

This is a list of DNS servers on the network. This is installed as the default DNS on the new virtual machine.

    guest_domain_name: domain.com

This is the domain that the virtual machine is on. This domain name is appended to the host name during DNS lookups.

    guest_gateway: 192.168.1.1

The defualt gateway of the vm. This is set using VMWare's guest customization.

    guest_id: ubuntu64Guest
    
The guest OS version. Currently this has only been tested deploying templates running the 64bit version of the Ubuntu Linux distro.



   
The following variables can be overwritten at the host level in the inventory file as well to customize the different virtual machines being deployed.

    guest_memory: 1024

The amount of memory allocated for the new virtual machine (in MB).

    guest_vcpu: 1

The number of virtual cpu threads to allocate for the virtual machine.

    guest_template: Ubuntu 20.04 Server

This is the name of the template in VCenter to copy from. This template must exist, so this should be changed to match your environment.

    hdd_gb: 32

The size of the hard drive for the new virtual machine (in GB).

    hdd_type: thin

How to provision the new virtual machine disk. Acceptable values are thin, thick, and eagerzeroedthick.

    vsphere_datastore: VFMS_Datastore

The datastore to create the new virtual machine disk on. This should also be changed to match your environment. 

    vsphere_user: admin

This is the VCenter administrator. This administrator account must have the permissions to create vms.

    vsphere_password: pass

This is the password for the VCenter administrator account. I do not recommend using plain text like this, instead use a vault variable or something else more secure.

    esxi_host: esxi01.domain.com

This is the ESXi host that the vm will be deployed on. 

    notes: Deployed with ansible

These notes will be added to the virtual machine among creation. The time and date of creation are appended to these notes.

Dependencies
------------

You need a VCenter running and an administrator account on the ESXI host. 

Example Playbook
----------------

    - name: Deploy the new vm from VCenter.
      hosts: deploy
      gather_facts: false
      vars_files:
        - vmware_deploy/vars/vault
    
      vars_prompt:
        - name: "vsphere_user"
          prompt: "VSphere user"
          private: no
        - name: "vsphere_password"
          prompt: "vSphere Password"
          private: yes
        - name: "esxi_host"
          prompt: "ESXi host"
          private: no
          default: esxi01.domain.com
        - name: "notes"
          prompt: "VM notes"
          private: no
          default: "Deployed with ansible"
      roles:
         - vmware_deploy

This playbook prompts the user to enter in the VSphere credentials and host for flexibility. This is optional, these variables can be injected another way. 

License
-------

BSD

Author Information
------------------

Derek Smiley - Homelabber, Network Analyst, aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/

Much of this was created using snippets from other public repositories on github. I claim ownership of none of this code.