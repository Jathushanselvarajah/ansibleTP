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
    │     ├ defaults/
    │     ├ tasks/
    ├ screenshots/
    │ ├ linux/
    │ └ windows/

------------------------------------------------------------------------

## Playbooks

### linux_setup.yml

Configure Linux target: - Gather facts - Install Apache (role apache) -
Start Apache service - Set timezone

------------------------------------------------------------------------

### windows_setup.yml

Configure Windows target: - Gather facts - Set timezone using
ansible.windows.win_timezone - Verify timezone using PowerShell
Get-TimeZone

------------------------------------------------------------------------

## Variables

### group_vars/linux.yml

    timezone_name: Europe/Paris
    apache_pkg: apache2
    apache_service: apache2

### group_vars/windows.yml

    timezone_name: Romance Standard Time

------------------------------------------------------------------------

## Inventory Example

    [linux]
    linux1 ansible_host=192.X.X.X ansible_user=jathus ansible_become=true

    [windows]
    win1 ansible_host=192.X.X.X
         ansible_user=jathus
         ansible_password=*****
         ansible_connection=winrm
         ansible_winrm_transport=basic
         ansible_winrm_server_cert_validation=ignore

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

### Run Windows playbook

    ansible-playbook -i inventory/hosts.ini playbooks/windows_setup.yml

------------------------------------------------------------------------

## Verification

### Apache test (Linux)

    curl http://192.X.X.X

------------------------------------------------------------------------

### Linux timezone verification

    ansible linux -i inventory/hosts.ini -m command -a "timedatectl"

------------------------------------------------------------------------

### Windows timezone verification

PowerShell on Windows VM:

    Get-TimeZone

------------------------------------------------------------------------

## Status

✅ Linux automation working
✅ Windows automation working

------------------------------------------------------------------------

## Screenshots

Screenshots of the project execution can be found in:

-   Linux → screenshots/linux/
-   Windows → screenshots/windows/

Including: - Ansible ping results - Playbook execution results - Apache
verification - Windows timezone verification

------------------------------------------------------------------------

## Author

Jathushan SELVARAJAH
EFREI -- DevOps / Ansible TP
