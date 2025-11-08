[![Build Status](https://travis-ci.org/oasis-roles/chrony.svg?branch=master)](https://travis-ci.org/oasis-roles/chrony)

CHRONY
===========

This role manages the configuration of the Chrony NTP service on target hosts. It allows you to:

* Configure NTP servers or server pools (chrony_servers, chrony_pools).
* Set the driftfile location (chrony_driftfile_path).
* Control time synchronization behavior such as makestep, rtcsync, hardware timestamping (chrony_makestep_args, chrony_enable_rtcsync, chrony_hwtimestamp_interfaces).
* Define minimum number of sources, client access networks, and authentication key files (chrony_num_minsources, chrony_ntp_client, chrony_keyfile_path).
* Configure logging paths and content (chrony_logdir_path, chrony_logged_information).

Requirements
------------

Ansible 2.16 or higher

Role Variables
--------------

Currently the following variables are supported:

| variable | type | default | description |
|----------|------|----------|-------------|
| `chrony_package` | string | `chrony` | Package name to install |
| `chrony_become_user` | string | `root` | User to run commands as |
| `chrony_servers` | list | `[]` | Explicit list of chrony servers (if set this overrides pools) |
| `chrony_pools` | list | `['1.pool.chrony.eu','2.pool.chrony.eu','3.pool.chrony.eu','4.pool.chrony.eu']` | Default pool servers |
| `chrony_driftfile_path` | string | `/var/lib/chrony/drift` | Driftfile storage path |
| `chrony_makestep_args` | string | `1.0 3` | Arguments passed to chrony makestep |
| `chrony_enable_rtcsync` | boolean | `true` | Enable kernel synchronization of the RTC |
| `chrony_hwtimestamp_interfaces` | string | `undefined` | Space separated list of interfaces for hardware timestamping |
| `chrony_num_minsources` | integer | `undefined` | Minimum number of selectable time sources |
| `chrony_ntp_client` | string | `undefined` | Local network allowed NTP client access |
| `chrony_keyfile_path` | string | `undefined` | Path to keys file used for NTP authentication |
| `chrony_logdir_path` | string | `/var/log/chrony` | Directory where chrony logs are stored |
| `chrony_logged_information` | string | `undefined` | Space separated list of what information to log |


Dependencies
------------

None

Example Playbook
----------------

```
- hosts: servers
  roles:
    - role: itcultus.chrony
```

License
-------

GPLv3

Author Information
------------------

Peter Tselios  
ITCultus LTD
