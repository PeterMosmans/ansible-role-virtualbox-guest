# Ansible Role: virtualbox-guest

Build status for this role: [![Build
Status](https://travis-ci.org/PeterMosmans/ansible-role-virtualbox-guest.svg)](https://travis-ci.org/PeterMosmans/ansible-role-virtualbox-guest)

This role builds, installs and configures the requested VirtualBox guest
additions. It searches the guest for a mounted ISO containing the
VBoxGuestAdditions, or an ISO file. When not found, it can download the
necessary ISO file directly from `download.virtualbox.org`.

## Requirements

None, all prerequisites will be installed (and can be removed afterwards). If
you don't set the **virtualbox_keep** variable to true, all packages that were
installed for building will be removed (the installed packages will be exactly
the same as before executing the role).

- bzip2
- dkms
- gcc
- make
- linux-headers

## Role Variables

Available variables are listed below, along with default values.

**virtualbox_keep**: A boolean stating whether the packages necessary for
compiling should be kept on the system. If not specified, defaults to no.

**virtualbox_iso**: The location on the guest where the ISO is expected. Note
that this file will be removed after successful compiling.

**local_virtualbox_iso**: Location on the host where the ISO is located. On
linux, it is located under `/usr/share/virtualbox/VBoxGuestAdditions.iso`. If
this variable is set, the role will copy the ISO file from the host to the
guest.

**virtualbox_remove_os_packages**: A boolean stating whether to remove any
previously installed VirtualBox packages. If not specified, defaults to no.

**virtualbox_version**: The requested version of VirtualBox. If the current
version does not match that version, it will try to (re)install VirtualBox guest
additions. If set to `auto`, it will try to determine the VirtualBox version of
the host system. The defaults can be found in `defaults/main.yml`.

```
virtualbox_version: auto
```

**virtualbox_x11**: A boolean stating whether VirtualBox guest additions will be
compiled with x11 support. If not specified, defaults to no.

## Dependencies

None.

## Example Playbook

```
- hosts: all
  become: yes
  become_method: sudo
  roles:
    - role: PeterMosmans.virtualbox-guest
```

This example will install VirtualBox guest additions, and will **not** keep the
build packages to the system if they are needed to install them.

## License

GPLv3

## Author Information

Created by Peter Mosmans.

Contributions are more than welcome! Thanks to all contributors so far: see [https://github.com/PeterMosmans/ansible-role-virtualbox-guest/graphs/contributors]
