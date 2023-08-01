:original_name: evs_01_0005.html

.. _evs_01_0005:

Deleting EVS Disks
==================

Scenarios
---------

If an EVS disk is no longer used, you can release the virtual resources by deleting the disk from the system.

-  The disk status is **Available**, **Error**, **Expansion failed**, **Restoration failed**, or **Rollback failed**.
-  The disk is not locked by any service.
-  The disk has been detached from all its servers.

.. important::

   -  When you delete a disk, all the disk data including the snapshots created for this disk will be deleted. Exercise caution when performing this operation.
   -  A deleted disk cannot be recovered.

Procedure
---------

#. Log in to the management console.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. In the disk list, locate the row that contains the target disk, click **More** in the **Operation** column, and choose **Delete**.

#. (Optional) If multiple disks are to be deleted, select |image1| in front of each disk and click **Delete** in the upper area of the list.

#. In the displayed dialog box, confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0238263087.png
