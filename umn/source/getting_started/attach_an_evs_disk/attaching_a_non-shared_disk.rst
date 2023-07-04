:original_name: evs_01_0036.html

.. _evs_01_0036:

Attaching a Non-Shared Disk
===========================

Scenarios
---------

Independently created EVS disks are data disks. In the disk list, the function of such disks is displayed as **Data disk**, and the status is displayed as **Available**. In this case, you need to attach the data disks to servers for use.

A system disk must be created together with an ECS and is automatically attached. In the disk list, the function of such disks is displayed as **System disk**, and the status is displayed as **In-use**. After a system disk is detached from an ECS, the disk function changes to **Bootable disk**, and the status changes to **Available**.

.. note::

   Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server and be used as a system disk or data disk depending on the device name selected.

This section describes how to attach a non-shared disk. A non-shared disk can be attached to one server only.

Constraints
-----------

Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.

Attaching the Disk on the EVS Console
-------------------------------------

#. Log in to the management console.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

   The **Attach Disk** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001179551366.png
      :alt: **Figure 1** Attach Disk dialog box

      **Figure 1** Attach Disk dialog box

#. Select the server and then select a device name from the drop-down list. Ensure that the disk and server are in the same AZ.

   One device name can be attached with one disk only. For the mapping between device names displayed on the management console and those on the server, see section "What Is the Mapping Between Device Names and Disks?" in the *Elastic Cloud Server User Guide*.

#. Click **OK** to return to the disk list page. The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the disk status changes to **In-use**, the disk is successfully attached.

#. Initialize the disk.

   After the disk has been attached to a server, the disk can be used only after you have initialized it. For details, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

Attaching the Disk on the ECS Console
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the ECS name, IP address, or ID for search.

#. Click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **Disks** tab. Then, click **Attach Disk**.

   The **Attach Disk** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001233686609.png
      :alt: **Figure 2** Attach Disk

      **Figure 2** Attach Disk

#. Select the target disk and specify the disk as the system disk or data disk.

   .. note::

      -  If no disks are available, click **Create Disk** in the lower part of the list.
      -  For the restrictions on attaching disks, see FAQ "What Are the Requirements for Attaching an EVS Disk to an ECS?" in the *Elastic Cloud Server* *User Guide*.

#. Click **OK**.

   After the disk is attached, you can view the information about it on the **Disks** tab.


   .. figure:: /_static/images/en-us_image_0000001188330870.png
      :alt: **Figure 3** Viewing the newly attached disk

      **Figure 3** Viewing the newly attached disk

Follow-Up Operations
--------------------

If you are attaching a new disk, you must then log in to the server and initialize the disk before it can be used. To learn how to initialize disks, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

.. |image1| image:: /_static/images/en-us_image_0210779229.png
