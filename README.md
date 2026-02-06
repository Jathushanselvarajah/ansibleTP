# Ansible Advanced TP

------------------------------------------------------------------------

## Project Structure

    ansible-tp/
    ├ ansible.cfg
    ├ inventory/
    │ └ hosts.ini
    ├ group_vars/
    │ ├ linux.yml
    │ └ windows.yml
    ├ playbooks/
    │ ├ linux_setup.yml
    │ └ windows_setup.yml
    ├ roles/
    │ └ apache/
    │ ├ defaults/
    │ ├ tasks/
    │ └ handlers/

------------------------------------------------------------------------

## Playbooks

### linux_setup.yml

Configure Linux target: - Gather facts - Install Apache - Start
Apache - Set timezone

------------------------------------------------------------------------

### windows_setup.yml

Configure Windows target: - Gather facts - Set timezone

------------------------------------------------------------------------

## Variables

### group_vars/linux.yml

    timezone_name: Europe/Paris
    apache_pkg: apache2
    apache_service: apache2

------------------------------------------------------------------------

## Inventory Example

    [linux]
    linux1 ansible_host=192.X.X.X ansible_user=jathus ansible_become=true

------------------------------------------------------------------------

## How to Run

### Test Linux connection

    ansible linux -i inventory/hosts.ini -m ping

------------------------------------------------------------------------

### Run Linux playbook

    ansible-playbook -i inventory/hosts.ini playbooks/linux_setup.yml

------------------------------------------------------------------------

### Test Windows connection

    ansible windows -i inventory/hosts.ini -m ansible.windows.win_ping

------------------------------------------------------------------------

## Verification

### Apache test

    curl http://192.X.X.X

------------------------------------------------------------------------

### Timezone test

    ansible linux -i inventory/hosts.ini -m command -a "timedatectl"

------------------------------------------------------------------------

## Status

✅ Linux automation working
⬜ Windows automation in progress

------------------------------------------------------------------------

## Screenshots

Screenshots of the project execution can be found in the following folders:

- Linux screenshots → `screenshots/linux/`
- Windows screenshots → `screenshots/windows/`

These screenshots include:
- Ansible ping results
- Playbook execution results
- Apache verification
- Windows configuration (when completed)
  
------------------------------------------------------------------------

## Author

Jathushan SELVARAJAH  
Efrei – DevOps / Ansible TP
