.. _era_clone_mssqldb:

-------------------
Era: Clone MSSQL DB
-------------------

Overview
++++++++

.. note::

  Estimated time to complete: **30 MINUTES**

In this lab we will perform some basic management tasks in Era. We will create snapshots, perform log catch ups, and clone/refresh clone DBs.

Create a Manual Snapshot
++++++++++++++++++++++++

The Time Machine for a database will automatically create snapshots based on the defined schedule. There are use cases where creating a snapshot outside of the Time Machine’s automatic schedule is desired. For example, when cloning or refreshing from the current time, it is more efficient to create a manual snapshot and clone or refresh from the manual snapshot

To create a manual snapshot of the **WideWorldImporters** database, do the following:

#. Open \https://*ERA-VM-IP:8443*/ in a new browser tab.

#. Select **Sources** in the **Databases** pane on the left-hand side of the screen.

#. Select the **WideWorldImporters** database.

#. Click **WideWorldImporters_TM** to the right of **WideWorldImporters**.

   .. figure:: images/clonedb_01.png

#. Click **Actions > Snapshot**.

#. Give the snapshot the name *initials*-**Manual**-*date* (ex: xyz-Manual-01012019), and click **Create**.

#. Monitor the registration operation by clicking **The snapshot operation for** *initials*-**Manual**-*todays date* **has started. Click here to see the status**.

   .. note::

     Wait for the operation to complete before attempting to use the snapshot

Initiate a Manual Log Catch Up
++++++++++++++++++++++++++++++

If configured for point in time recovery, the Time Machine for a SQL Server database will automatically collect transaction log backups based on the defined schedule. The process to collect transaction log backups is called Log Catch Up. To clone or refresh from a point in time between the current time and the time of the last automatic log catch up, the log catch up process must be initiated manually to collect the transaction log backups. Once the manual log catch up is complete, an arbitrary point in time can be select from that time window.

To initiate a manual log catch up for the **WideWorldImporters** database, do the following:

#. Open \https://*ERA-VM-IP:8443*/ in a new browser tab.

#. Select **Sources** in the **Databases** pane on the left-hand side of the screen.

#. Select the **WideWorldImporters** database.

#. Click **WideWorldImporters_TM** to the right of **WideWorldImporters**.

#. Click **Actions > Log Catch Up**.

#. Click **Yes** to start the Log Catch Up.

#. Monitor the registration operation by clicking **The log catch up operation has started. Click here to see status**.

   .. note::

     Wait for the operation to complete before attempting to clone or refresh from a point in time between the current time and the time of the last automatic log catch up.

Cloning Your MSSQL Source
+++++++++++++++++++++++++







Refresh Your Cloned MSSQL Database
++++++++++++++++++++++++++++++++++
