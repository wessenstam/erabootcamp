.. title:: Nutanix Era Bootcamp

.. toctree::
  :maxdepth: 2
  :caption: Era Tech Summit 2019 Lab
  :name: _era_tech_summit_2019_lab
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

Welcome to the Nutanix Era Bootcamp!

Nutanix Era is a software suite that automates and simplifies database administration – bringing One Click simplicity and invisible operations to database provisioning and lifecycle management (LCM).

With One Click database provisioning and Copy Data Management (CDM) as its first services, Nutanix Era enables DBAs to provision, clone, refresh, and backup their databases to any point in time. Line of business applications in every vertical depend on databases, providing use cases in both production and non-production environments.

This workbook accompanies an instructor-led session that introduces Nutanix Era and many common management tasks. Each section has a lesson and an exercise to give you hands-on practice. The instructor explains the exercises and answers any additional questions that you may have.

What's New
++++++++++

- Workshop updated for the following software versions:
    - AOS & PC 5.10.x

- Optional Lab Updates:

Resources
+++++++++

- `Era Software Download <https://portal.nutanix.com/#/page/releases/eraDetails>`_
- `Era User Guide <https://portal.nutanix.com/#/page/docs/details?targetId=Nutanix-Era-User-Guide-v10:Nutanix-Era-User- Guide-v10>`_

Agenda
++++++

- Nutanix Era Labs
    - Era: Deploy and Register
    - Era: Provision Postgres DB
    - Era: Clone Postgres DB
    - Era: Create MSSQL Server
    - Era: Register MSSQL Databases
    - Era: Clone MSSQL DB
    - Era: REST API Explorer

- Optional Labs
    - SSHKey Creation

Introductions
+++++++++++++

- Name
- Familiarity with Nutanix

Initial Setup
+++++++++++++

- Take note of the *Passwords* being used.
- Log into your virtual desktops (connection info below)

Environment Details
+++++++++++++++++++

Nutanix Workshops are intended to be run in the Nutanix Hosted POC environment. Your cluster will be provisioned with all necessary images, networks, and VMs required to complete the exercises.

Networking
..........

Hosted POC clusters follow a standard naming convention:

- **Cluster Name** - POC\ *XYZ*
- **Subnet** - 10.**21**.\ *XYZ*\ .0
- **Cluster IP** - 10.**21**.\ *XYZ*\ .37

If provisioned from the marketing pool:

- **Cluster Name** - MKT\ *XYZ*
- **Subnet** - 10.**20**.\ *XYZ*\ .0
- **Cluster IP** - 10.**20**.\ *XYZ*\ .37

For example:

- **Cluster Name** - POC055
- **Subnet** - 10.21.55.0
- **Cluster IP** - 10.21.55.37

Throughout the Workshop there are multiple instances where you will need to substitute *XYZ* with the correct octet for your subnet, for example:

.. list-table::
  :widths: 25 75
  :header-rows: 1

  * - IP Address
    - Description
  * - 10.21.\ *XYZ*\ .37
    - Nutanix Cluster Virtual IP
  * - 10.21.\ *XYZ*\ .39
    - **PC** VM IP, Prism Central
  * - 10.21.\ *XYZ*\ .40
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
    - 10.21.\ *XYZ*\ .1/25
    - 0
    - 10.21.\ *XYZ*\ .50-10.21.\ *XYZ*\ .124
  * - Secondary
    - 10.21.\ *XYZ*\ .129/25
    - *XYZ1*
    - 10.21.\ *XYZ*\ .132-10.21.\ *XYZ*\ .253

Credentials
...........

.. note::

  The *<Cluster Password>* is unique to each cluster and will be provided by the leader of the Workshop.

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

Each cluster has a dedicated domain controller VM, **DC**, responsible for providing AD services for the **NTNXLAB.local** domain. The domain is populated with the following Users and Groups:

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

Access Instructions
+++++++++++++++++++

The Nutanix Hosted POC environment can be accessed a number of different ways:

Parallels VDI
.................

Login to: https://xld-uswest1.nutanix.com (for PHX) or https://xld-useast1.nutanix.com (for RTP)

**Nutanix Employees** - Use your NUTANIXDC credentials
**Non-Employees** - **Username:** POCxxx-User01 (up to POCxxx-User20), **Password:** *<Provided by Instructor>*

Pulse Secure VPN
..........................

To download the client: login to https://xlv-uswest1.nutanix.com or https://xlv-useast1.nutanix.com - **Username:** POCxxx-User01 (up to POCxxx-User20), **Password:** *<Provided by Instructor>*

Download and install the client.

In Pulse Secure Client, **Add** a connection:

For PHX:

- **Type** - Policy Secure (UAC) or Connection Server
- **Name** - X-Labs - PHX
- **Server URL** - xlv-uswest1.nutanix.com

For RTP:

- **Type** - Policy Secure (UAC) or Connection Server
- **Name** - X-Labs - RTP
- **Server URL** - xlv-useast1.nutanix.com


Nutanix Version Info
++++++++++++++++++++

- **AHV Version** - AHV 20170830.185 (5.9+/5.10+)
- **AOS Version** - 5.10.2
- **PC Version** - 5.10.2
