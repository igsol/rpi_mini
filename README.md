Rasperry Pi minimal
===================

This is auxiliary role for mpd_rpi one.
The role and playbook is intended for:
 
* Original [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) installation is "minimized", i.e. redundant packages are deleted (e.g. xserver-xorg, etc.).

Requirements
------------

1. Ansible itself.
1. Running __Raspberry Pi 2__ machine with brand new [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) installed.  

Role Variables
--------------

These variables are all situated in the vars/main.yml and have to be adjusted by you.

|Name                   | Type   | Description                                                                |
|-----------------------|--------|----------------------------------------------------------------------------|
|rpimini_ssh_reset      |boolean | If true, the SSH host keys are regenerated. It's useful to apply once only.|

Inventory
---------
The [inventory file](http://docs.ansible.com/ansible/intro_inventory.html) file has to
contain __mpd_hosts__ group, which is
used in the role. 
You have to add your Raspberry Pi host name into this group. 
Example of inventory file:
    
    [mpd_hosts]
    my_rpi_for_mpd

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts:
        - mpd_hosts
      roles:
        - rpi_mini

Usage examples
--------------

1. It's a good practice to reset default SSH host keys. It's useful to apply once only.
   Note the __"rpimini_ssh_reset=true"__ usage.

        ansible-playbook -i hosts rpi_mini.yml -u root --tags=ssh_reset --extra-vars "rpimini_ssh_reset=true" 

1. To make all role tasks except SSH host keys resetting run following command.

        ansible-playbook -i hosts rpi_mini.yml -u root 

License
-------

GPLv3
