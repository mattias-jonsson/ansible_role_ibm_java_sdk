ansible_role_ibm_java_sdk
==============

This role performs the following actions

* Installs/Upgrades IBM Java SDK on supported Oprating Systems.

Requirements
---------------

This role has been tested on the following Operating Systems.

* CentOS 7


Role variables
---------------

Variables used in the role:

    ansible_role_ibm_java_sdk_path:  
    ansible_role_ibm_java_sdk_version:  
    ansible_role_ibm_java_sdk_installer:


`ansible_role_ibm_java_sdk_path` Install path on target system, default value is /opt/ibm/java-x86_64-80  
`ansible_role_ibm_java_sdk_version` Version of IBM Java SDK, default value is 8.0-6.20  
`ansible_role_ibm_java_sdk_installer` Filename and path to installer file on Ansible controller, default value is files/ibm-java-x86_64-sdk-{{ ibm_java_sdk_version }}.bin.

Sample configuration
---------------

```yaml
ansible_role_ibm_java_sdk_path: /opt/ibm/java-x86_64-80
ansible_role_ibm_java_sdk_version: 8.0-6.20
ansible_role_ibm_java_sdk_installer: files/ibm-java-x86_64-sdk-{{ ibm_java_sdk_version }}.bin
```
