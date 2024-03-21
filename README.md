Ansible Role: ansible_role_ibm_java_sdk
==============

Installs/Upgrades IBM Java SDK version 8 on the following Operating Systems:

<ul>
<li> Enterprise Linux 7/8/9
</ul>

Requirements
------------

This role depends on the `community.general` Ansible collection.

Role Variables
--------------

The following table lists the configurable variables for this role, their default values, and descriptions:

| Variable                                | Required | Default Value                                                                                               | Comments                                                                                                  |
|-----------------------------------------|----------|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| `ansible_role_ibm_java_sdk_path`        | No       | `/opt/ibm/java-x86_64-80`                                                                                   | The installation path for the IBM Java SDK on the target system. Defined in `vars/main.yml`.             |
| `ansible_role_ibm_java_sdk_version`     | No       | `8.0-8.21`                                                                                                  | The version of the IBM Java SDK to install. Defaults can be found in `defaults/main.yml`.                |
| `ansible_role_ibm_java_sdk_installer`   | No       | See dynamic value*                                                                                          | URL/Path and filename of the installer. Dynamic defaults in `defaults/main.yml`.   |
| `ansible_role_ibm_java_sdk_set_default_java` | No   | `false`                                                                                                    | Whether to set IBM Java as the system's default Java interpreter.                                        |
| `ansible_role_ibm_java_sdk_set_default_java_path` | No   | `/usr/bin/java`                                                                                       | This path will be used by `alternatives` to point to the IBM Java SDK as the default Java interpreter, allowing it to be used when the `java` command is invoked. |
| `ansible_role_ibm_java_sdk_sha1sums`    | No       | See SHA1 checksums below**                                                                                  | Map of Java installers to their SHA1 checksums. Ensure you update this with newer versions as necessary. |
| `ansible_role_ibm_java_sdk_file_ext`    | No       | See dynamic value***                                                                                        | File extension for the installer, dependent on the SDK version. Defined in `vars/main.yml`.              |
| `ansible_role_ibm_java_sdk_gpg_check`   | No       | See dynamic value****                                                                                       | Whether to enable GPG check for the RPM package, dependent on the SDK version. Defined in `vars/main.yml`.|

*Default installer path and filename are derived from the SDK version, switching between `.bin` for versions before `8.0-8.15` and `.x86_64.rpm` for `8.0-8.15` and above.

**Default SHA1 checksums in `defaults/main.yml` for verifying the integrity of downloaded SDK installers:
- `ibm-java-x86_64-sdk-8.0-6.31.bin`: `5a2511794305da488ac6a5ebc4304f1b8c0a5ed6`
- ... (list continues with other versions and their checksums)

***The file extension for the installer is dynamically set based on the Java SDK version.

****GPG check is enabled or disabled based on the SDK version, with conditions defined in `vars/main.yml`.


Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------

    - hosts: servers
      vars:
        ansible_role_ibm_java_sdk_version: "8.0-8.21"
        ansible_role_ibm_java_sdk_installer: "files/ibm-java-x86_64-sdk-{{ ansible_role_ibm_java_sdk_version }}.{{ 'bin' if ansible_role_ibm_java_sdk_version is version('8.0-8.15', '<') else 'x86_64.rpm' }}"
      roles:
         - ansible_role_ibm_java_sdk

License
-------

MIT

Author Information
------------------

Mattias Jonsson
