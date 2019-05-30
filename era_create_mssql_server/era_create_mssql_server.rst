.. _era_create_mssql_server:

--------------------------
Era: Create MSSQL Server
--------------------------

Overview
++++++++

.. note::

  Estimated time to complete: **30 MINUTES**

This lab will show you how to provision, connect, and view a Postgres Database.


Create The Database Storage Container
+++++++++++++++++++++++++++++++++++++

Before creating a VM, a container will need to be created that will host the SQL Server disks. Inline compression should be enabled on this container. Both deduplication and erasure coding should be disabled on this container.

.. note::

  An existing container can be used, if the capacity optimization options are configured according to Nutanix SQL Server best practices.

Let's use Prism Element to perform the container setup.

#. In **Prism Element> Storage**, click **Storage**, click **Table**, then click **+ Storage Container**.

#. Use the following specifications:

   - **Name** - *Initials*-Database
   - Select **Advanced Settings**
   - Select **Compression**
   - **Delay (In Minutes)** - 0
   - Select **Erasure Coding**

   #. Click **Save**.

   .. figure:: images/storage_01.png

Deploy MSSQL Server VM
++++++++++++++++++++++

Now we will use Prism Central to deploy the MSSQL Server VM.

#. In **Prism Central**, select :fa:`bars` **> Virtual Infrastructure > VMs**.

#. Click **Create VM**.

#. Fill out the following fields:

   - **Name** - *Initials*-MSSQL-PROD
   - **Description** - (Optional) Description for your VM.
   - **vCPU(s)** - 4
   - **Number of Cores per vCPU** - 1
   - **Memory** - 16 GiB

   - Select **+ Add New Disk**
       - **Type** - DISK
       - **Operation** - Clone from Image Service
       - **Image** - MSSQL-2016-VM.qcow2
       - Select **Add**

   - Select **Add New NIC**
       - **VLAN Name** - Primary
       - Select **Add**

#. Click **Save** to create the VM.

#. Select your MSSQL Server VM and click **Power On**.

.. note::

    The VM name must be a valid Windows server name. Valid Windows server names must be less than 15 characters long and cannot contain certain characters such as spaces or periods.

Configure the MSSQL Server VM
+++++++++++++++++++++++++++++

We will run some sstaged scripts to configure the Server VM and create/restore some databases.

Initialize the Server
.....................

#. In **Prism Central**, select :fa:`bars` **> Virtual Infrastructure > VMs**, and select *Initials*-**MSSQL-PROD**.

#. Click **Launch Console**.

#. Verfiy Region, Language, Keyboard layout, and click **Next**.

#. Click **Accept** to accept the license terms.

#. Set the Administrator password, **nutanix/4u**, and click **Finish**.

#. Login as the local Administrator.

#. Click **No** on the **Networks** pop-up appears on the right-hand side of the screen.

Rename the Server
.................

The SQL Server VM image includes a PowerShell script that will rename the Windows server so that it matches the name of the VM.

  .. note::

    If the VM name is more than 15 characters, this step will fail.

    Verify that the VM name is 15 characters or less before proceeding.

#. Double click the **01 - Rename Server** powershell script.

#. When prompted, enter the following information:

   - **Nutanix Cluster IP** - *Nutanix Cluster Virtual IP*
   - **Nutanix User Name** - admin
   - **Nutanix Password** - *Cluster Password*

   .. figure:: images/mssqlvm_01.png

#. The VM will restart. After it restarts, login as local Administrator.

Complete the MSSQL Server Build
...............................

The SQL Server VM image includes a PowerShell script that will complete the build of the SQL Server VM.

   .. note::

    During this process, Nutanix SQL Server best practices will be applied.

#. Double click the **02 - Complete Build** powershell script.

#. When prompted, enter the following information:

   - **Nutanix Cluster IP** - *Nutanix Cluster Virtual IP*
   - **Nutanix User Name** - admin
   - **Nutanix Password for "admin"** - *Cluster Password*
   - **Nutanix Container Name** - *Initials*-Database

   .. figure:: images/mssqlvm_02.png

#. The VM will restart. After it restarts, login as local Administrator.

Create the Sample databases
...........................

The SQL Server VM image includes a T-SQL script that will create two sample SQL Server databases:

- WideWorldImporters
- WideWorldImportersDW

#. Double click the **SQL Server Management Studio 17** icon.

#. When the **Connect to Server** dialoge box appears, Verify the **Server** name, and click **Connect**.

   .. figure:: images/mssqlvm_03.png

#. Select **File**, select **Open**, and then select **File...**.

#. When the **Open File** dialog box appears, navigate to **C:\NTNX-Setup**, select **RestoreWWIDatabases.sql**, and click **Open**.

   .. figure:: images/mssqlvm_04.png

#. Click **Execute** on the toolbar.

   .. figure:: images/mssqlvm_05.png

#. When you see the *RESTORE DATABASE successfully processed*, Close **SQL Server Management Studio**.
