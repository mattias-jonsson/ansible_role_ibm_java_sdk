Ansible Role: ansible_role_ibm_java_sdk
==============

Installs/Upgrades IBM Java SDK on the following Operating Systems:

<ul>
<li> Enterprise Linux 7/8/9
</ul>

Role Variables
--------------

| Variable | Required | Default | Comments |
| -------- | -------- | ------- | -------- |
| `ansible_role_ibm_java_sdk_path` | No | /opt/ibm/java-x86_64-80 | Install path on target system. |
| `ansible_role_ibm_java_sdk_version` | No | 8.0-6.20 | Version of IBM Java SDK. |
| `ansible_role_ibm_java_sdk_installer` | No | files/ibm-java-x86_64-sdk-{{ ansible_role_ibm_java_sdk_version }}.bin | Filename and path to installer file available on Ansible controller. |

Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------

    - hosts: servers

      vars:
        ansible_role_ibm_java_sdk_version: 8.0-6.20

      roles:
         - ansible_role_ibm_java_sdk

License
-------

MIT

Author Information
------------------

Mattias Jonsson
