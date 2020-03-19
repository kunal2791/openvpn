Ansible Role: OpenVPN
=========
An ansible role to install and configure OpenVPN server.

Salient Features
----------------
- This Role automates the VPN setup using OpenVPN.
The role consist of two meta files
- clientlist: Enter the namer of the client you want to add.
- revokelist: Enter the names of the client you want to revoke.

### Note:  
  - Disable Source/Destination Check.

     > From the list of instances, select the VPN instance and then Networking->Change Source/Dest.
     > Check from the drop down menu. Then click Yes, Disable. This is needed as otherwise, your VPN  
     > server will not be able to connect to your other EC2 instances.

Supported OS
------------
  * CentOS:7
  * CentOS:6
  * Ubuntu:bionic
  * Ubuntu:xenial
  * Amazon AMI

Dependencies
------------
* None


Role Variables
--------------

|**Variables**| **Default Values**| **Description**| **Type**|
|----------|---------|---------------|-----------|
| server_name | server | OpenVPN server Name | Optional |
| PROTOCOL | udp | The protocaol on which the server will work | Mandatory |
| PORT | udp | The port on which the server will work | Mandatory |
| openvpn_server_network | 10.8.0.0 | CIDR range given to vpn network | Optional |
| base_directory | /etc/openvpn | Configuration path of openvpn server | Optional |
| easy_rsa_url | url | URL to download Easy RSA | Optional |

Example Playbook
----------------
```
---
- name: It will automate OpenVPN setup
  hosts: server
  become: true
  roles:
    - role: openvpn
...

$  ansible-playbook site.yml -i inventory

```
```
- For generating client keys
$  ansible-playbook site.yml -i inventory --tags "generate_client_keys"


- For revoking client keys
$  ansible-playbook site.yml -i inventory --tags "revoke_client_keys"

```
