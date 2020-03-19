Ansible Role: OpenVPN
=========
An ansible role to install and configure OpenVPN server.

Salient Features
----------------
- This Role automates the VPN setup using OpenVPN.
The role consist of two meta files
- clientlist: Enter the namer of the client you want to add.
- revokelist: Enter the names of the client you want to revoke.

Supported OS
------------
  * CentOS
  * Ubuntu
  * Amazon AMI

Dependencies
------------
* None

Example Playbook
----------------
```
---
- name: It will automate OpenVPN client cert genetation and revoke
  hosts: all
  become: true
  roles:
    - role: openvpn
...

$  ansible-playbook openvpn.yml -i inventory

```
```
- For generating client keys
$  ansible-playbook client.yml -i inventory --tags "generate_client_keys"


- For revoking client keys
$  ansible-playbook client.yml -i inventory --tags "revoke_client_keys"

```
