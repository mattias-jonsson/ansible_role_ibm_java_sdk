Ansible Role: ibm_java_sdk
==============

Installs/Upgrades IBM Java SDK version 8 on the following Operating Systems:

<ul>
<li> Enterprise Linux 7/8/9
</ul>

Requirements
------------

This role requires the `community.general` Ansible collection. If not already installed, you can install it using the following command:

```shell
ansible-galaxy collection install community.general
```

Role Variables
--------------

The following table lists the configurable variables for this role, their default values, and descriptions:

| Variable                                | Required | Default Value                                                                                               | Comments                                                                                                  |
|-----------------------------------------|----------|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| `ibm_java_sdk_file_ext`    | No       | Dynamic based on version                                                                                     | File extension for the installer, determined by the SDK version. Defined in `vars/main.yml`.              |
| `ibm_java_sdk_gpg_check`   | No       | Dynamic based on version                                                                                  | Whether to perform a GPG check on the RPM package, dependent on the SDK version. Defined in `vars/main.yml`.|
| `ibm_java_sdk_installer`   | No       | Dynamic based on version                                                                                         | URL or local path, including filename, of the installer.  |
| `ibm_java_sdk_path`        | No       | `/opt/ibm/java-x86_64-80`                                                                                   | Path where the IBM Java SDK is installed on the target system.           |
| `ibm_java_sdk_set_default_java_path` | No   | `/usr/bin/java`                                                                                       | Path used by alternatives to set the IBM Java SDK as the default Java interpreter. |
| `ibm_java_sdk_set_default_java` | No   | `false`                                                                                                    | If true, sets IBM Java as the system's default Java interpreter.                                        |
| `ibm_java_sdk_sha1sums`    | No       | SHA1 checksums listed below                                                                               | Map of Java installer filenames to their SHA1 checksums for integrity verification. |
| `ibm_java_sdk_version`     | No       | `8.0-8.21`                                                                                                  | The version of the IBM Java SDK to install.              |

Special Variable Notes:
------------
- **Installer Path and Filename**:
  - The default path and filename for the installer are dynamically determined by the SDK version.
  - For versions **prior to 8.0-8.15**, the installer uses a `.bin` file extension.
  - For versions **8.0-8.15 and later**, the installer is provided as a `.x86_64.rpm` file.

- **SHA1 Checksums**:
  - SHA1 checksums are provided within `defaults/main.yml`.
  - These areused for verifying the integrity of the downloaded SDK installer.

- **File Extension and GPG Check**:
  - Both the file extension and the GPG verification settings are set dynamically, depending on the Java SDK version.
  - These settings are defined in `vars/main.yml`.



Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------

```shell
- hosts: servers
  vars:
    ibm_java_sdk_version: "8.0-8.21"
    ibm_java_sdk_installer: "files/ibm-java-x86_64-sdk-{{ ibm_java_sdk_version }}.{{ 'bin' if ibm_java_sdk_version is version('8.0-8.15', '<') else 'x86_64.rpm' }}"
  roles:
      - ibm_java_sdk
```

License
-------

MIT

Author Information
------------------

Mattias Jonsson
