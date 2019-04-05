# Ansible Cisco Switch Backup
This is a playbook to backup cisco switch configuration, made to run on a daily base

## Execution Requirements
- Tested with CentOS7
- Tested with Ansible 2.7.9

## Variables

### The following variables may be overridden:
* `creds`: credentials to access the switch configuration, in prod, protect within vault
* `backup_root`: path to store switch configuration

## How to use
`ansible-playbook switchBackup.yml`

## Dependencies
* none

## License
https://opensource.org/licenses/LGPL-3.0    
Copyright (c) Chris Ruettimann <chris@bitbull.ch>  

