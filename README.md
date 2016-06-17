Ansible Role: virtualbox-guest
=====================

Build status for this role: [![Build Status](https://travis-ci.org/PeterMosmans/ansible-role-virtualbox-guest.svg)](https://travis-ci.org/PeterMosmans/ansible-role-virtualbox-guest)


This role installs and configures the requested VirtualBox guest additions. Expected is either a mounted ISO containing the VBoxGuestAdditions, or an ISO file in /root/VBoxGuestAdditions.iso.

Requirements
------------

None, all prerequisites will be installed (and can be removed afterwards). IPlease note that the installer does not check (yet) whether packages were already installed, so it might remove the following previously installed packages, if you don't set the **virtualbox_keep** variable to true:
  - bzip2
  - dkms
  - gcc
  - make
  - linux-headers


Role Variables
--------------

Available variables are listed below, along with default values

**virtualbox_keep**: A boolean stating whether the packages necessary for compiling should be kept on the system. If not specified, defaults to no.

**virtualbox_version**: The requested version of VirtualBox. If the current version does not match that version, it will try to (re)install VirtualBox guest additions. The defaults can be found in ```defaults/main.yml```.
```
virtualbox_version: 5.0.22
```

**virtualbox_x11**: A boolean stating whether VirtualBox guest additions will be compiled with x11 support. If not specified, defaults to no.



Dependencies
------------

None.



Example Playbook
----------------
```
- hosts: all
  become: yes
  become_method: sudo
  roles:
    - role: PeterMosmans.virtualbox-guest
```
This example will install VirtualBox guest additions.


License
-------

GPLv3


Author Information
------------------

Created by Peter Mosmans.
