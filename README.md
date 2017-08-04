Role: cnstechnicalgroup.sqlserver-ag-add-replica
========

* Ansible role that adds a replica to a SQL Server Always On Availability Group with ReadOnly Scale. 
* This role doesn't create the AG, it simply adds a replica to it. 

Requirements
------------

* CentOS7 
* Ubuntu Xenial Xenus


Role Variables
--------------

In the current version, you can specify the following variables:

| Name                  | Default |                                                               |
|-----------------------|---------|---------------------------------------------------------------|
| sa_password           |   ---   | system administrator password for SQL Server install        . |
| availability_group    |   ---   | The name that will be assigned to the Availability Group    . |
| primary_host_name     |   ---   | The name of the host that is being mirrored (principal)     . |
| secondary_host_name   |   ---   | The name of the host that is mirroring (replica)            . |


Dependencies
------------

Depends upon 

* [role-sqlserver-server](https://github.com/cnstechnicalgroup/role-sqlserver-server)
* [role-sqlserver-ha-config](https://github.com/cnstechnicalgroup/role-sqlserver-ha-config)



License
-------

GPLv2

Author Information
------------------

Created by CNS Technical Group (https://www.cnstechgroup.com/)

Documentation
------------------

Install example (https://github.com/cnstechnicalgroup/ansible-sqlserver/blob/master/documents/sqlserver-ag-add-replica.md)



Examples
--------

```yaml
---
- hosts: replicas
  sudo: yes
  roles: 
  - sqlserver-ag-add-replica
  gather_facts: yes
  environment:
   SA_PASSWORD: "{{sa_password}}"
   ACCEPT_EULA: "Y"
   MSSQL_PID: "evaluation"
```

