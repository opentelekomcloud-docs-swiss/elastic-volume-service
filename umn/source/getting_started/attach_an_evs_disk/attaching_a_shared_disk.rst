:original_name: evs_01_0037.html

.. _evs_01_0037:

Attaching a Shared Disk
=======================

Scenarios
---------

Independently created EVS disks are data disks. In the disk list, the function of such disks is displayed as **Data disk**, and the status is displayed as **Available**. In this case, you need to attach the data disks to servers for use.

This section describes how to attach a shared disk.

Constraints
-----------

-  A shared disk can be attached to a maximum of 16 servers. These servers and the shared disk must be in the same AZ within a region.

   .. important::

      If you simply attach a shared disk to multiple servers, files cannot be shared among them. Because there are no mutually agreed data read/write rules among servers, read and write operations from them may interfere with each other, or unpredictable errors may occur. To share files between servers, set up a shared file system or a clustered management system first.

-  If a shared disk is in the **In-use** state, ensure that the maximum number of servers that the disk can be attached to has not been reached.

-  All the servers attached with a shared disk must run either Windows or Linux.

   For example, if you attach a shared disk to multiple Windows servers and then detach it from these servers, the shared disk cannot be attached to Linux servers later. This is because Windows and Linux support different file systems and cannot identify the original file system on the disk. Improper operations may damage the original file system.

-  A shared disk can only be used as a data disk. It cannot be used as a system disk.
-  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.

Attaching the Disk on the EVS Console
-------------------------------------

#. Log in to the management console.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

   The **Attach Disk** dialog box is displayed.

   Shared disks support batch attachment so you can attach a shared disk to multiple servers. In the **Attach Disk** dialog box, the left area shows the server list. After you select the target servers, they will be displayed in the right area.


   .. figure:: /_static/images/en-us_image_0000001179551782.png
      :alt: **Figure 1** Attach Disk

      **Figure 1** Attach Disk

#. Select the target servers and then select a device name from the drop-down list for each server you selected. Ensure that the disk and servers are in the same AZ.

#. Click **OK** to return to the disk list page. The status of the disk is **Attaching**, indicating that the disk is being attached to the servers. When the disk status changes to **In-use**, the disk is successfully attached.

Attaching the Disk on the ECS Console
-------------------------------------

#. Log in to the management console.

#. Under **Compute**, click **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the ECS name, IP address, or ID for search.

#. Click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **Disks** tab. Then, click **Attach Disk**.

   The **Attach Disk** page is displayed.

#. Select the target disk and set the device name as prompted.

   Device names are as follows:

   -  For Xen ECSs, you can specify the device name of a disk, such as **/dev/sdb**.
   -  For KVM ECSs, you can specify a disk as a system disk or data disk but cannot specify a device name for the disk.

   .. note::

      -  If no disks are available, click **Create Disk** in the lower part of the list.
      -  For the restrictions on attaching disks, see FAQ "What Are the Requirements for Attaching an EVS Disk to an ECS?" in the *Elastic Cloud Server* *User Guide*.

#. Click **OK**.

   After the disk is attached, you can view the information about it on the **Disks** tab.

Follow-Up Operations
--------------------

If you are attaching a new disk, you must then log in to the server and initialize the disk before it can be used. To learn how to initialize disks, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.
