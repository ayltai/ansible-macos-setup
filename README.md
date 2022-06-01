# macOS customization role for Ansible

[![GitHub workflow status](https://img.shields.io/github/workflow/status/ayltai/ansible-macos-setup/CI?style=flat)](https://github.com/ayltai/ansible-macos-setup/actions)
[![Ansible quality score](https://img.shields.io/badge/quality-5-success)](https://galaxy.ansible.com/ayltai/macos_setup)
[![Ansible role](https://img.shields.io/badge/role-ayltai.macos_setup-blue)](https://galaxy.ansible.com/ayltai/macos_setup)
![Maintenance](https://img.shields.io/maintenance/yes/2022?style=flat)
[![Release](https://img.shields.io/github/release/ayltai/ansible-macos-setup.svg?style=flat)](https://github.com/ayltai/ansible-macos-setup/releases)
[![License](https://img.shields.io/github/license/ayltai/ansible-macos-setup.svg?style=flat)](https://github.com/ayltai/ansible-macos-setup/blob/master/LICENSE)

Install and configure software on macOS.

[![Buy me a coffee](https://img.shields.io/static/v1?label=Buy%20me%20a&message=coffee&color=important&style=flat&logo=buy-me-a-coffee&logoColor=white)](https://buymeacoff.ee/ayltai)

## Quick start

Make sure you have [Homebrew](https://brew.sh) installed on macOS.

### Installation
```sh
ansible-galaxy install ayltai.macos_setup
```

### Usage
```yaml
---
- hosts: all
  roles:
    - ayltai.macos_setup
  vars_prompt:
    - name: sudo_password
      prompt: root password
  vars:
    macos_vscode: yes
    macos_java_packages:
      - name: adoptopenjdk-8-openj9.jdk
        package: OpenJDK8U-jdk_x64_mac_openj9_8u262b10_openj9-0.21.0.pkg
        url: https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/downloadjdk8u262-b10_openj9-0.21.0/OpenJDK8U-jdk_x64_mac_openj9_8u262b10_openj9-0.21.0.pkg
        checksum: sha256:662dec036e16ff91868abbce98f9e10c04325bc5b2dafdbdc16935bce1aec758
```

## Variables
| Name | Type | Default | Description |
|------|------|---------|-------------|
| `macos_overwrite` | `boolean` | No | Specifies whether to overwrite an installed application. |
| `macos_download_path` | `path` | `~/Downloads` | Specifies the location to temporarily store installation packages. |
| `macos_vscode` | `boolean` | Yes | Installs and configures [Visual Studio Code](https://code.visualstudio.com/) and extensions. See [vscode-mac](https://github.com/ayltai/ansible-vscode-mac) Ansible Role for configuration instructions. |
| `macos_homebrew_packages` | `list` | `[]` | A list of packages to be installed with [Homebrew](https://brew.sh). |
| `macos_homebrew_cask_packages` | `list` | `[]` | A list of packages to be installed with [Homebrew Cask](https://brew.sh). |
| `macos_archived_packages` | `list` | `[]` | A list of archived packages to be decompressed and moved to `/Applications`. |
| `macos_archived_packages.0.name` | `string` | | The name of the archived package. |
| `macos_archived_packages.0.url` | `string` | | The URL to download the archived package from. |
| `macos_java_packages` | `list` | `[]` | A list of [Java JDK/JRE](https://adoptopenjdk.net) packages to be installed. |
| `macos_java_packages.0.name` | `string` | | The [Java JDK/JRE](https://adoptopenjdk.net) name. |
| `macos_java_packages.0.package` | `string` | | The [Java JDK/JRE](https://adoptopenjdk.net) installation package name. |
| `macos_java_packages.0.url` | `string` | | The [Java JDK/JRE](https://adoptopenjdk.net) package download URL. |
| `macos_java_packages.0.checksum` | `string` | | The file checksum of the [Java JDK/JRE](https://adoptopenjdk.net) package. Supports format `[algorithm]:[checksum]`. |
| `macos_graalvm_packages` | `list` | `[]` | A list of [GraalVM](https://www.graalvm.org/) JDK packages to be installed. |
| `macos_graalvm_packages.0.name` | `string` | | The GraalVM JDK name. |
| `macos_graalvm_packages.0.package` | `string` | | The GraalVM JDK installation package name. |
| `macos_graalvm_packages.0.url` | `string` | | The GraalVM JDK package download URL. |
| `macos_hack_fonts` | `boolean` | Yes | Installs [Hack](https://github.com/source-foundry/Hack) fonts. |
| `macos_resizer` | `boolean` | Yes | Installs [Resizer](https://github.com/ayltai/Resizer). |
| `macos_java_default` | `string` | `java8` | Specifies the default Java JDK on `PATH`. Supports `java8`, `java11`, `java14`, `graalvm8` and `graalvm11`. |

## Dependencies
* [ansible-macos-preferences](https://github.com/ayltai/ansible-macos-preferences)
* [ansible-macos-appstore](https://github.com/ayltai/ansible-macos-appstore)
* [ansible-vscode-mac](https://github.com/ayltai/ansible-vscode-mac)

## License
[MIT](https://github.com/ayltai/ansible-macos-setup/blob/master/LICENSE)

## References
* [Ansible](https://www.ansible.com)
* [Ansible Galaxy](https://galaxy.ansible.com)
