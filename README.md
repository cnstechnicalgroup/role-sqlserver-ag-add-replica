Role: cnstechnicalgroup.sqlserver-ag-add-replica
========

* Ansible role that adds a replica to a SQL Server Always On Availability Group with ReadOnly Scale. 
* The role role-sqlserver-ha-config has to be played first on the primary and at least one secondary before adding a replica. 
* The role role-sqlserver-ag-config has to be played first on the primary and at least one secondary before adding a replica. 
* This role doesn't create the AG, it simply adds a replica to it. 
* Even though this role depends upon sqlserver-ha-config and sqlserver-ag-config, it is not possible to add them as a dependency in anisble because this replica is unaware of the first replica. 

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
| primary_host          |   ---   | The name of the host that is being mirrored (principal)     . |
| secondary_host        |   ---   | The name of the host that is mirroring (replica)            . |


Dependencies
------------

Depends upon 

* [role-sqlserver-server](https://github.com/cnstechnicalgroup/role-sqlserver-server)



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

```

