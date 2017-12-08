ansible-winpackages
===============
Install or remove Windows Server packages

Summary
--------
This playbook will install or remove a list of defined software packages on a AWS EC2 Windows 2016 server

Prerequisities
----------------
- Creation of an ansible-vault encrypted string to seed the `admin_pass` variable.  See [ansible-vault encrypt_string](https://docs.ansible.com/ansible/2.4/vault.html#use-encrypt-string-to-create-encrypted-variables-to-embed-in-yaml)

Example Playbook execution
-------------------------
`ansible-playbook site.yml --ask-vault-pass`

role
--------
ansible-role-winpackages

default role vars
------------

| variable name | description | default |
|---------------|-------|---------|
|ansible_connection| method of connection |winrm|
|ansible_port| port to connect  |5986|
|ansible_user| User Account |Administrator|
|admin_pass| ansible-vault encrypted string for initial Windows Administrator password |N/A|
|ansible_password| ansible password to use to login to new Windows instance |"{{ admin_pass }}"|
|ansible_winrm_server_cert_validation| Validate or ignore certificate| ignore|

role vars
------------
| variable name | description | default |
|---------------|-------|---------|
|windows_packages| list of software packages to install |firefox, curl, git, notepad++ |

Example playbook
-----------
```
---
- name: Add or remove Windows packages
  hosts: all

  roles:
    - ansible-role-winpackages
```

License
-------
BSD
