nrpe_check_pve_vms
==================

Nagios NRPE for checking running VMs on ProxmoxVE

Galaxy : yes

Requirements
------------

- NRPE is already installed
- python3 (for the check script)

Role Variables
--------------

vars:

- *vms*: list of VMs that should run on target host

e.g. these can be the hostvars for host *pve01*

    vms:
    - almalinux10
    - debian13

This will check if almalinux10 and debian13 both are running as VM on the target host

Dependencies
------------

*role_nrpe* to install/configure NRPE

Example Playbook
----------------

The vms var is optional and can be defined as host_vars.  
Note that the role is only useful if the var is defined.
Else there will be nothing to check.
*arikkert.nrpe_check_pve_vms* will install *arikkert.role_nrpe* as dependency

    - hosts: pve01
      roles:
        - role: arikkert.nrpe_check_pve_vms
          when: vms is defined

Note
-------

This role configures the nrpe user (user running nrpe) to run *check_pve_vms* with elevated privileges

License
-------

BSD

Author Information
------------------

    ARK-ICT
    Andre Rikkert de Koe - ICT
