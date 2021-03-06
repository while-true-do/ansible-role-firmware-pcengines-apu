[![Build Status](https://travis-ci.org/while-true-do/ansible-role-firmware-pcengines-apu.svg?branch=master)](https://travis-ci.org/while-true-do/ansible-role-firmware-pcengines-apu)

# Ansible Role: firmware-pcengines-apu
| This role adds the possibility to do firmware updates on PC Engines devices.

It checks if the firmware is already on the target version and flashes the firmware if required.
Parameters for automatic reboot and enforcement are optionally available.

For an overview about the available firmware please have a look at [PC Engines - Github](https://pcengines.github.io/).

## Motivation

Automating firmware updates is essential to a secure environment.

## Supported Devices

- PC Engines
  - [APU2](https://pcengines.ch/apu2.htm)

## Installation

Install from [Ansible Galaxy](https://galaxy.ansible.com/while_true_do/firmware_pcengines_apu)

```
ansible-galaxy install while_true_do.firmware_pcengines_apu
```

Install from [Github](https://github.com/while-true-do/ansible-role-firmware-pcengines-apu)

```
git clone https://github.com/while-true-do/ansible-role-firmware-pcengines-apu.git while_true_do.firmware_pcengines_apu
```

## Requirements

Used Modules:

-   [command_module](https://docs.ansible.com/ansible/latest/modules/command_module.html)
-   [fail_module](https://docs.ansible.com/ansible/latest/modules/fail_module.html)
-   [file_module](https://docs.ansible.com/ansible/latest/modules/file_module.html)
-   [get_url_module](https://docs.ansible.com/ansible/latest/modules/get_url_module.html)
-   [include_tasks_module](https://docs.ansible.com/ansible/latest/modules/include_tasks_module.html)
-   [package_module](https://docs.ansible.com/ansible/latest/modules/package_module.html)
-   [unarchive_module](https://docs.ansible.com/ansible/latest/modules/unarchive_module.html)

## Dependencies

This role depends on the below roles. You have to install them:

-   [reboot](https://github.com/while-true-do/ansible-role-reboot)
-   [repo-epel](https://github.com/while-true-do/ansible-role-repo-epel)

```
ansible-galaxy install -r requirements.yml
```

## Role Variables

```yaml
# defaults/main.yml for firmware_pcengines_apu

wtd_firmware_pcengines_apu_packages:
 - dmidecode
 - flashrom

# target BIOS version
# example: "v4.8.0.1"
wtd_firmware_pcengines_apu_bios_version: ""

# enforce flashing regardless of version
wtd_firmware_pcengines_apu_force_flash: false

# reboot after flash
wtd_firmware_pcengines_apu_autoreboot: false
```

## Example Playbook

Simple Example:

```yaml
- hosts: servers
  roles:
    - { role: while_true_do.firmware_pcengines_apu }
```

Advanced Example:

```yaml
- hosts: servers
  roles:
    - { role: while_true_do.firmware_pcengines_apu, wtd_firmware_pcengines_apu_autoreboot: true, wtd_firmware_pcengines_apu_force_flash: true }
```

## Testing

All tests are located in [test directory](./tests/).

Basic testing:

```
bash ./tests/test-spelling.sh
bash ./tests/test-ansible.sh
```

## Contribute / Bugs

Thank you so much for considering to contribute. Every contribution helps us.
We are really happy, when somebody is joining the hard work. Please have a look
at the links first.

-   [Code of Conduct](./docs/CODE_OF_CONDUCT.md)
-   [Contribution Guidelines](./docs/CONTRIBUTING.md)
-   [Create an issue or Request](https://github.com/while-true-do/ansible-role-pcengines-apu-firmware/issues)
-   [See who was contributing already](https://github.com/while-true-do/ansible-role-pcengines-apu-firmware/graphs/contributors)

## License

This work is licensed under a [BSD License](https://opensource.org/licenses/BSD-3-Clause).

## Author Information

Site: [while-true-do.org](https://while-true-do.org)

Mail: [hello@while-true-do.org](mailto:hello@while-true-do.org)
