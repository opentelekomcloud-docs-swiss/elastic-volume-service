:original_name: evs_01_0011.html

.. _evs_01_0011:

Deleting an EVS Snapshot
========================

Scenarios
---------

If you no longer require certain snapshots or the snapshot quantity reaches the maximum allowed, you can delete some snapshots.

Prerequisites
-------------

-  The snapshot status must be **Available** or **Error**.

Constraints
-----------

.. table:: **Table 1** Constraints

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                              | Description                                                                                                                                                                                                                                                         |
   +===================================+=====================================================================================================================================================================================================================================================================+
   | Legacy snapshots                  | -  If a snapshot's source disk is deleted, all legacy snapshots of this disk are also deleted.                                                                                                                                                                      |
   |                                   | -  If you reinstall or change the server OS, snapshots of the system disk are automatically deleted. Those of the data disks can be used as usual.                                                                                                                  |
   |                                   | -  A snapshot whose name starts with **autobk_snapshot_vbs\_**, **manualbk_snapshot_vbs\_**, **autobk_snapshot_csbs\_**, or **manualbk_snapshot_csbs\_** is automatically generated during backup. You can check details of such snapshots, but cannot delete them. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Standard snapshots                | -  Standard snapshots are not deleted even if their source disks are deleted.                                                                                                                                                                                       |
   |                                   | -  If you delete a disk whose standard snapshots have Instant Snapshot Restore enabled, the standard snapshots will not be deleted.                                                                                                                                 |
   |                                   | -  If you reinstall or change the server OS, standard snapshots will not be deleted.                                                                                                                                                                                |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | General constraints               | -  If a snapshot is deleted, disks rolled back or created from this snapshot are not affected.                                                                                                                                                                      |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Sign in to the console.

#. Click |image1| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The **Snapshots** page is displayed.

#. In the snapshot list, locate the target snapshot and click **Delete** in the **Operation** column.

#. In the displayed dialog box, confirm the information and click **Yes**.

   If the snapshot disappears from the snapshot list, the snapshot is deleted successfully.

.. |image1| image:: /_static/images/en-us_image_0000001933286285.jpg
