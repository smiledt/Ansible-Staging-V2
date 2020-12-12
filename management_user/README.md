# provision_vm

## Table Of Contents

* [About](#about)
* [Role Defaults](#role-defaults)
* [License](#license)
* [Author](#author)

## About

> This role provisions a virtual machine for management by ansible in my infrastructure. It adds a management user with a specified password, via variables, then adds that management user to the sudoers file. Finally, it adds the public SSH key for the management user to this account. 
>
> Note: There are some default roles that apply only to my infrastructure. If used on a different environement, this role needs to be passed a ansible_become_pass, ansible_ssh_pass, and these other variables either via the command line, uncommenting these lines in the playbook, or AWX/Ansible Tower.

[Back to table of contents](#table-of-contents)

## Role Defaults

**Quicklist**: [management_pass](#management_pass),
[management_public_key](#management_public_key),
[management_user](#management_user)

### management_pass 

* *help*: TODO.

[Back to table of contents](#table-of-contents)

### management_public_key 

* *help*: TODO.

[Back to table of contents](#table-of-contents)

### management_user 

* *help*: TODO.

[Back to table of contents](#table-of-contents)

## Example Playbooks

### Basic Usage

```yaml
- name: Provision new host(s)
  hosts: control
  remote_user: "{{ provision_user }}"
  become: true
  become_user: root
  vars: # These variables are needed to connect to the new virtual machine(s)
    ansible_become_pass: "{{ provision_pass }}"
    ansible_ssh_pass: "{{ provision_pass }}"
  roles:
  - role: provision_vm
    management_user_name: "{{ mgmt_user }}"
    management_user_password: "{{ mgmt_pass }}"
    management_public_key: "{{ mgmt_key }}"
```


[Back to table of contents](#table-of-contents)


## License

license (GPLv2, CC-BY, etc)

[Back to table of contents](#table-of-contents)

## Author

Derek Smiley

[Back to table of contents](#table-of-contents)
