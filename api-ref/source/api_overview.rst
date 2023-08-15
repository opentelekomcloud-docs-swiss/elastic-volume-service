:original_name: en-us_topic_0124881427.html

.. _en-us_topic_0124881427:

API Overview
============

EVS APIs include APIs and OpenStack Cinder APIs.

A combination of these two types of APIs allows you to use all EVS functions.

.. table:: **Table 1** API overview

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                  | Subtype               | Description                                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================================+
   | API                   | EVS disk              | These APIs provide the functions, such as creating disks, deleting disks, and querying disk details.                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | EVS snapshot          | An EVS snapshot is a complete copy or image of the disk data at a specific time point.                                                                                              |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | These APIs provide the function of rolling back the snapshot data to the disk.                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | EVS tag               | Tags are used to identify cloud resources for purposes of easy categorization and quick search.                                                                                     |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | These APIs provide the functions, such as adding, deleting, and querying tags.                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OpenStack Cinder API  | EVS disk              | These APIs provide the functions, such as creating disks, updating disks, querying disks, querying images, and querying quotas.                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | EVS disk action       | These APIs provide the functions, such as expanding disks, reserving disks, exporting disk data as images, and setting the bootable attribute for disks.                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | EVS snapshot          | An EVS snapshot is a complete copy or image of the disk data at a specific time point.                                                                                              |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | These APIs provide the functions, such as creating snapshots, querying snapshots, updating snapshot metadata, and querying snapshot metadata.                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | EVS disk transfer     | Through the disk transfer function, disks can be transferred from one tenant to another. After the transfer succeeds, the ownerships of the disks belong to the target tenant only. |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | These APIs provide the functions, such as creating, accepting, deleting, and querying disk transfers.                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
