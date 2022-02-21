# Ansible Cisco Switch Backup
This is a playbook to backup cisco switch configuration, made to run on a daily base

## Execution Requirements
- Tested with Alma8
- Tested with Ansible 2.9, but keep in mind, that name of modules will change in later version

## Variables
  It is strongly recommended to protect the passwords in group_vars at least in a vault   
  https://github.com/joe-speedboat/workshop.ansible/blob/master/20 Protect variables with vaults.md
* check ansible config for
  * vault settings    
  * group_vars

### The following variables may be overridden:
* `ansible_become_password`
* `ansible_password`
* `config_backup_dir_cisco`

## How to use
`ansible-playbook switchBackup.yml`

## Dependencies
* You need an existing git repo with deployment key    
  for the backup location: ```config_backup_dir_cisco```
* You need the ansible collections    
  depending on your ansible version and device types:
  * ```ansible-galaxy collection install community.network```
  * https://docs.ansible.com/ansible/5/collections/community/network/

## License
https://opensource.org/licenses/LGPL-3.0    
Copyright (c) Chris Ruettimann <chris@bitbull.ch>  

## Inventory host_var example
```
ansible-inventory --list --vars
...snip...
            "fw-asa-01": {
                "ansible_become": true,
                "ansible_become_method": "enable",
                "ansible_become_password": "xxxxxx",
                "ansible_connection": "network_cli",
                "ansible_network_os": "asa",
                "ansible_password": "xxxxxx",
                "ansible_user": "admin",
                "config_backup_dir_cisco": "/etc/git/cisco_backup"
            },
            "switch-01": {
                "ansible_become": true,
                "ansible_become_method": "enable",
                "ansible_become_password": "xxxxxx",
                "ansible_connection": "network_cli",
                "ansible_network_os": "ios",
                "ansible_password": "xxxxxx",
                "ansible_user": "admin",
                "config_backup_dir_cisco": "/etc/git/cisco_backup"
            },
            "wlan-controller-01": {
                "ansible_become": false,
                "ansible_connection": "local",
                "ansible_network_os": "aireos",
                "ansible_password": "xxxxxx",
                "ansible_user": "admin",
                "config_backup_dir_cisco": "/etc/git/cisco_backup"
            }
...snip...
```
