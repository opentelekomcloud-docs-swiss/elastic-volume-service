:original_name: en-us_topic_0052554220.html

.. _en-us_topic_0052554220:

Device Types and Usage Instructions
===================================

What Device Types Are Available?
--------------------------------

There are two EVS device types: Virtual Block Device (VBD) and Small Computer System Interface (SCSI).

-  VBD is the default EVS device type. VBD EVS disks support only basic read/write SCSI commands.
-  SCSI EVS disks support transparent SCSI command transmission and allow the server OS to directly access the underlying storage media. Besides basic read/write SCSI commands, SCSI disks support advanced SCSI commands.

Device type is configured during creation. It cannot be changed after the disk has been created.

Common Application Scenarios and Usage Instructions of SCSI EVS Disks
---------------------------------------------------------------------

-  A SCSI EVS disk can be a system disk or a data disk.

-  Shared SCSI EVS disks: Shared SCSI EVS disks must be used together with a distributed file system or cluster software. Because most cluster applications, such as Windows MSCS, Veritas VCS, and Veritas CFS, require SCSI reservations, you are advised to use shared EVS disks with SCSI.

   SCSI reservations take effect only when shared SCSI EVS disks are attached to ECSs in the same ECS group. For more information about shared EVS disks, see :ref:`Shared EVS Disks and Usage Instructions <en-us_topic_0032860759>`.

Do I Need to Install a Driver for SCSI EVS Disks?
-------------------------------------------------

To use SCSI EVS disks, you need to install a driver for certain server OSs.

-  KVM ECS

   You are advised to use SCSI EVS disks with KVM ECSs. Linux images and Windows images for KVM ECSs already have the required driver. Therefore, no driver needs to be installed for KVM ECSs.

   .. note::

      Currently, only KVM ECSs are supported.
