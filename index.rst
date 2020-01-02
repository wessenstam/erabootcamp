.. title:: Era METI Come Together 2020 Lab

.. toctree::
  :maxdepth: 2
  :caption: Era METI Come Together 2020 Lab
  :name: _era_meti_come_together_lab
  :hidden:

  era/era

.. toctree::
  :maxdepth: 2
  :caption: Era Setup Labs
  :name: _era_setup_labs
  :hidden:

  era_deploy_and_register/era_deploy_and_register

.. toctree::
  :maxdepth: 2
  :caption: Era Postgres Labs
  :name: _era_postgres_labs
  :hidden:

  era_provision_postgresdb/era_provision_postgresdb
  era_clone_postgresdb/era_clone_postgresdb

.. toctree::
  :maxdepth: 2
  :caption: Era MSSQL Labs
  :name: _era_mssql_labs
  :hidden:

  era_create_mssql_server/era_create_mssql_server
  era_register_mssql_dbs/era_register_mssql_dbs
  era_clone_mssqldb/era_clone_mssqldb

..
  .. toctree::
    :maxdepth: 2
    :caption: Era Rest APIs
    :name: _era_rest_apis
    :hidden:

    era_rest_api/era_rest_api

  .. toctree::
    :maxdepth: 2
    :caption: Optional Labs
    :name: _optional_labs
    :hidden:

.. toctree::
  :maxdepth: 2
  :caption: Appendix
  :name: _appendix
  :hidden:

  appendix/glossary
  tools_vms/windows_tools_vm
  tools_vms/linux_tools_vm

.. _getting_started:

---------------
Getting Started
---------------

Welcome to the Nutanix Era Labs! This workbook accompanies an instructor-led session that introduces Nutanix Era and many common management tasks. Each section has a lesson and an exercise to give you hands-on practice. The instructor explains the exercises and answers any additional questions that you may have.

.. note::

	If this is your first encounter with ERA, or you want to update your knowledge on ERA from the beginning, run all the labs. Otherwise run the added MSSQL server labs. All labs will take approx 3 hours. The MSSQL labs approx 1.5 hours.

What's New
++++++++++

- Workshop updated for the following software versions:
    - AOS & PC 5.11.x

- Optional Lab Updates:
    - MS SQL Server part

Agenda
++++++

- Nutanix Era Labs
    - Era: Deploy and Register
    - Era: Provision Postgres DB
    - Era: Clone Postgres DB
    - Era: Install and configure a MSSQL Server
    - Era: Register a MSSQL Server in Era
    - Era: Clone a MSSQL Server

- Optional Labs
    - SSHKey Creation


Environment Details
+++++++++++++++++++

The Nutanix Hosted POC environment has been setup for you. To follow the setup process so you can re-run this workshop, please follow the instructions `here <http://ntnx.tips/HOWTO>`_.

Networking
..........

Hosted POC clusters follow a standard naming convention:

- **Cluster Name** - PHX-POC\ *XYZ*
- **Subnet** - 10.42.\ *XYZ*\ .0
- **Cluster IP** - 10.42.\ *XYZ*\ .37

For example:

- **Cluster Name** - POC055
- **Subnet** - 10.42.55.0
- **Cluster IP** - 10.42.55.37

Throughout the Workshop there are multiple instances where you will need to substitute *XYZ* with the correct octet for your subnet, for example:

.. list-table::
  :widths: 25 75
  :header-rows: 1

  * - IP Address
    - Description
  * - 10.42.\ *XYZ*\ .37
    - Nutanix Cluster Virtual IP
  * - 10.42.\ *XYZ*\ .39
    - **PC** VM IP, Prism Central
  * - 10.42.\ *XYZ*\ .41
    - **DC** VM IP, NTNXLAB.local Domain Controller

Each cluster is configured with 2 VLANs which can be used for VMs:

.. list-table::
  :widths: 25 25 10 40
  :header-rows: 1

  * - Network Name
    - Address
    - VLAN
    - DHCP Scope
  * - Primary
    - 10.42.\ *XYZ*\ .1/25
    - *XYZ*
    - 10.42.\ *XYZ*\ .50-10.21.\ *XYZ*\ .124
  * - Secondary
    - 10.42.\ *XYZ*\ .129/25
    - *XYZ1*
    - 10.42.\ *XYZ*\ .132-10.21.\ *XYZ*\ .253

Credentials
...........

.. note::

  The *<Cluster Password>*, in the below table, is unique to each cluster and will be provided.

.. list-table::
  :widths: 25 35 40
  :header-rows: 1

  * - Credential
    - Username
    - Password
  * - Prism Element
    - admin
    - *<Cluster Password>*
  * - Prism Central
    - admin
    - *<Cluster Password>*
  * - Controller VM
    - nutanix
    - *<Cluster Password>*
  * - Prism Central VM
    - nutanix
    - *<Cluster Password>*

Each cluster has a dedicated domain controller VM, **AutoDC2**, responsible for providing AD services for the **NTNXLAB.local** domain. The domain is populated with the following Users and Groups:

.. list-table::
  :widths: 25 35 40
  :header-rows: 1

  * - Group
    - Username(s)
    - Password
  * - Administrators
    - Administrator
    - nutanix/4u
  * - SSP Admins
    - adminuser01-adminuser25
    - nutanix/4u
  * - SSP Developers
    - devuser01-devuser25
    - nutanix/4u
  * - SSP Power Users
    - poweruser01-poweruser25
    - nutanix/4u
  * - SSP Basic Users
    - basicuser01-basicuser25
    - nutanix/4u

.. _assign-cluster:

Access Instructions
+++++++++++++++++++

To see which cluster has been assigned to you, please use the below table:



.. raw:: html

  <iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRbGExQjI8Xxdndg5OF7WElTDB3YUbeoWf8QfAdhM2Sy8bdW9rzzQO9489rF1RXNv_4jyIryd6wNBgW/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" style="position: relative; height: 600px; width: 98%; border: none"></iframe>

.. note::
    Write down your IP addresses on a piece of paper to make it a bit easier for yourself...




Employee Pulse Secure VPN
..........................

https://sslvpn.nutanix.com - Use your CORP credentials
