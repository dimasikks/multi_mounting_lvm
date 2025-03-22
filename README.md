Multi-mounting LVM
=========

#### This role is subsequently mounted to disks, used on paths that require mounting new disks, mounts disks in place, makes changes to /etc/fstab

Usage
-----------
#### For normal operation, you need to run the command below from the root directory of the project, also specify at least one disk and path for mounting in the format disk:path, also specify the size of the disks via size= in ansible extra_vars, or by editing vars/main.yml - there you can also change other parameters of the role

```bash
ansible-playbook playbooks/configure_disks.yml -i inventories/groups/storage-test.yml --extra-vars 'input=disk:/path/to/mount_point size=some_size'
```

Example
--------------
```bash
ansible-playbook playbooks/configure_disks.yml -i inventories/groups/storage-test.yml --extra-vars 'input=sda:/storage-1,sdb:/storage-2,sdc:/storage-3 size=500'
```

Requirements
----------
- Mandatory presence of --extra-vars
- Disks must be partitionless, disks can be formatted, role is written to mount newly connected disks without any significant changes
- For disks, only the disk name should be specified, for example - sda, not /dev/sda, the disk name should be similar to the output of the NAME field of the lsblk command
- Specify size, otherwise the default size will be applied


