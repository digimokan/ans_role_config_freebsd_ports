# ans_role_config_freebsd_ports

Build and install packages using the FreeBSD ports tree.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_freebsd_ports.svg?label=release)](https://github.com/digimokan/ans_role_config_freebsd_ports/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Build and install a list of packages using the FreeBSD ports tree.
* Run the build on the host system, without using Poudriere/etc build systems.

## Supported Operating Systems

* FreeBSD.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_freebsd_ports
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Build and install packages using the FreeBSD ports tree"
         ansible.builtin.include_role:
           name: ans_role_config_freebsd_ports
         vars:
           freebsd_ports_package_list:
             - "graphics/drm-kmod"
             - "x11/wezterm"
   ```

## Role Options

Vars that must be defined when including the role in the playbook:

  * [dependencies](../defaults/main/dependencies/main.yml)

Vars with default values, which can be overridden in the playbook:

  * [overridable](../defaults/main/overridable/main.yml)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_freebsd_ports/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

