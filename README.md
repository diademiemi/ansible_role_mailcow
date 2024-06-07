Ansible Role Mailcow
=========

[![Molecule Test](https://github.com/diademiemi/ansible_role_mailcow/actions/workflows/molecule.yml/badge.svg)](https://github.com/diademiemi/ansible_role_mailcow/actions/workflows/molecule.yml)

This is an Ansible role to install and configure mailcow.

Include more information about mailcow in this section.

Requirements
------------
These platforms are supported:
- Ubuntu 20.04
- Ubuntu 22.04
- Debian 11
- Debian 12
- EL 8 (Tested on Rocky Linux 8)
- EL 9 (Tested on Rocky Linux 9)
- Fedora 40
- openSUSE Leap 15.5

<!--
- List hardware requirements here  
-->

Role Variables
--------------

Variable | Default | Description
--- | --- | ---
`mailcow_git_tag` | `"2023-10a"` | The git tag to use for Mailcow
`mailcow_git_override_changes` | `true` | Prevents updating or changing Mailcow manually
`mailcow_pass_scheme` | `"BLF-CRYPT"` | The password scheme for Mailcow
`mailcow_hostname` | `{{ ansible_fqdn }}` | The fully qualified domain name for Mailcow
`mailcow_dbname` | `"mailcow"` | The database name for Mailcow
`mailcow_dbuser` | `"mailcow"` | The database user for Mailcow
`mailcow_dbpass` | `"mailcow"` | The database password for Mailcow
`mailcow_dbroot` | `{{ mailcow_dbpass }}` | The root password for the Mailcow database
`mailcow_http_port` | `80` | The HTTP port for Mailcow
`mailcow_https_port` | `443` | The HTTPS port for Mailcow
`mailcow_http_bind` | `"0.0.0.0"` | The bind address for Mailcow's HTTP service
`mailcow_https_bind` | `"0.0.0.0"` | The bind address for Mailcow's HTTPS service
`mailcow_tz` | `"UTC"` | The timezone setting for Mailcow
`mailcow_compose_project_name` | `"mailcowdockerized"` | The Docker Compose project name for Mailcow
`mailcow_docker_compose_version` | `"native"` | Indicates the version of Docker Compose to use
`mailcow_additional_san` | `""` | Additional Subject Alternative Names for SSL
`mailcow_additional_server_names` | `""` | Additional server names for Mailcow
`mailcow_letsencrypt` | `true` | Whether to use Let's Encrypt for SSL certificates
`mailcow_ip_check` | `true` | Enables IP checking for Mailcow
`mailcow_http_verification` | `true` | Enables HTTP verification for Mailcow
`mailcow_clamd` | `true` | Whether to enable ClamAV for Mailcow
`mailcow_sogo` | `true` | Whether to enable SOGo for Mailcow
`mailcow_solr` | `true` | Whether to enable Solr for Mailcow
`mailcow_use_watchdog` | `true` | Whether to use the watchdog feature in Mailcow
`mailcow_watchdog_verbose_logging` | `false` | Enables verbose logging for the Mailcow watchdog
`mailcow_internal_ipv4_network` | `"172.22.1"` | The internal IPv4 network range for Mailcow
`mailcow_internal_ipv6_network` | `"fd4d:6169:6c63:6f77::/64"` | The internal IPv6 network range for Mailcow
`mailcow_api_key` | `"mailcow"` | The API key for Mailcow
`mailcow_api_key_readonly` | `"mailcow"` | The read-only API key for Mailcow
`mailcow_api_allow_from` | `{{ ansible_default_ipv4.address }}` | The allowed IP address for Mailcow API access
`mailcow_allow_admin_email_login` | `false` | Whether to allow admin email login in Mailcow

<!--
`variable` | `default` | Variable example
`long_variable` | See [defaults/main.yml](./defaults/main.yml) | Variable referring to defaults
`distro_specific_variable` | See [vars/debian.yml](./vars/debian.yml) | Variable referring to distro-specific variables
-->

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None

Example Playbook
----------------

```yaml
- name: Use diademiemi.mailcow role
  hosts: "{{ target | default('mailcow') }}"
  roles:
    - role: "diademiemi.mailcow"
      tags: ['diademiemi', 'mailcow', 'setup']    ```

```

License
-------

MIT

Author Information
------------------

- diademiemi (@diademiemi)

Role Testing
------------

This repository comes with Molecule that run in Podman on the supported platforms.
Install Molecule by running

```bash
pip3 install -r requirements.txt
```

Run the tests with

```bash
molecule test
```

These tests are automatically ran by GitHub Actions on push. If the tests are successful, the role is automatically published to Ansible Galaxy.

