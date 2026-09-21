:original_name: evs_01_0098.html

.. _evs_01_0098:

EVS Snapshot Overview
=====================

Overview
--------

An EVS snapshot is a complete copy or image of the disk data taken at a specific time. Snapshot is a major disaster recovery (DR) approach, and you can use a snapshot to restore disk data to the time when the snapshot was created.

Currently, there are standard snapshots and legacy snapshots. :ref:`Table 1 <evs_01_0098__en-us_topic_0197597144_table17176122102013>` describes their differences.

.. _evs_01_0098__en-us_topic_0197597144_table17176122102013:

.. table:: **Table 1** Snapshot types

   +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type               | Description                                                                                                                                                                                                                                                              |
   +====================+==========================================================================================================================================================================================================================================================================+
   | Standard snapshots | Snapshot data is stored in OBS. Newly created snapshots are standard snapshots. When creating disks from a standard snapshot, you can change the device type (SCSI or VBD), encryption attribute, AZ, or type of the disks on the console or through the V5 version API. |
   +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Legacy snapshots   | Snapshot data is stored together with disk data on the disks. New legacy snapshots cannot be created. Existing legacy snapshots are retained, but you can only use them to restore data or create new disks in the same AZ, or delete them.                              |
   +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Snapshot-related operations

   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Operation                      | Description                                                                                                                                                                                                       | Reference                                                    |
   +================================+===================================================================================================================================================================================================================+==============================================================+
   | Creating snapshots             | You can create a snapshot to save the disk data at a specified time.                                                                                                                                              | :ref:`Creating an EVS Snapshot <evs_01_2721>`                |
   |                                |                                                                                                                                                                                                                   |                                                              |
   |                                | .. note::                                                                                                                                                                                                         |                                                              |
   |                                |                                                                                                                                                                                                                   |                                                              |
   |                                |    Snapshots are read-only. After snapshots are created, data in the snapshots cannot be modified.                                                                                                                |                                                              |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Rolling back data              | If data on a disk is incorrect or damaged, you can roll back data from a snapshot to the source disk.                                                                                                             | :ref:`Rolling Back Disk Data from a Snapshot <evs_01_0012>`  |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Creating disks from a snapshot | You can create disks from a snapshot to quickly copy the snapshot data to disks.                                                                                                                                  | :ref:`Creating a Disk from a Snapshot <evs_01_0013>`         |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Checking snapshot information  | You can check the storage used by all snapshots of an EVS disk, the total storage used by all snapshots in a specified period, and the total storage used by all snapshots of your account in a specified region. | :ref:`Checking the EVS Snapshot Storage Usage <evs_01_2712>` |
   |                                |                                                                                                                                                                                                                   |                                                              |
   |                                | You can check the snapshot details, including the region and AZ, source disk information, and tags.                                                                                                               | :ref:`Checking EVS Snapshot Details <evs_01_0122>`           |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Deleting snapshots             | If you no longer require certain snapshots or the snapshot quantity reaches the maximum allowed, you can delete some snapshots.                                                                                   | :ref:`Deleting an EVS Snapshot <evs_01_0011>`                |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------+

Snapshot Usage Scenarios
------------------------

The snapshot function helps address your following needs:

-  Routine data backup

   You can create snapshots for disks on a timely basis and use snapshots to recover your data in case that data loss or data inconsistency occurred due to unintended operations, viruses, or attacks.

-  Rapid data restoration

   You can create a snapshot or multiple snapshots before an application software upgrade or a service data migration. If an exception occurs during the upgrade or migration, service data can be rapidly restored to the time when the snapshot was created.

   For example, a fault occurred on system disk A of server A, and therefore server A cannot be started. As system disk A is already faulty, data on system disk A cannot be restored by rolling back data from snapshots. However, you can create disk B using an existing snapshot of system disk A and attach disk B to a properly running server, for example server B. In this case, server B obtains the data of system disk A from disk B.

   .. note::

      When rolling back data from snapshots, data can only be rolled back to the source disk, and a rollback to a different disk is not possible.

-  Multi-service quick deployment

   You can use a snapshot to create multiple disks containing the same initial data. These disks can be used as data resources for various services, for example data mining, report query, and development and testing. This method protects the initial data and creates disks rapidly, meeting diverse service requirements.

Legacy Snapshot Principles
--------------------------

The following example describes the snapshot principles with two snapshots s1 and s2 created for disk v1 at different points in time:

#. Disk v1 was created, which contains no data.

#. Data d1 and d2 were written to disk v1. Data d1 and d2 were written to new spaces.

#. Snapshot s1 was created for disk v1 modified in step 2. Data d1 and d2 were not saved as another copy elsewhere. Instead, a relationship between snapshot s1 and data d1 and d2 was established.

#. Data d3 was written to disk v1, and data d2 was changed to d4. Data d3 and d4 were written to new spaces, and data d2 was not overwritten. The relationship between snapshot s1 and data d1 and d2 was still valid. Snapshot s1 can be used to restore data if needed.

#. Snapshot s2 was created for disk v1 modified in step 4, and a relationship between snapshot s2 and data d1, d3, and d4 was established.


   .. figure:: /_static/images/en-us_image_0000002277743292.png
      :alt: **Figure 1** Snapshot principles

      **Figure 1** Snapshot principles

Standard Snapshot Principles
----------------------------

Standard snapshots back up data by data block. They include **full snapshots** and **incremental snapshots**. The first snapshot created for an EVS disk is a full snapshot, which backs up all data blocks on the disk at the time of the snapshot. Subsequent snapshots are incremental snapshots, which back up only changed data blocks since the last snapshot.

Metadata files of full and incremental snapshots record information about all data blocks when the snapshots were created. So, you can use any snapshot to restore your disk data to the state when the snapshot was created.


.. figure:: /_static/images/en-us_image_0000002312352877.png
   :alt: **Figure 2** Standard snapshot principles

   **Figure 2** Standard snapshot principles

Based on the source of data blocks, a snapshot's metadata file contains information about three types of data blocks: **inherited data blocks** (inherited from the last snapshot), **modified data blocks** (have modifications compared with the last snapshot), and **new data blocks** (new compared with the last snapshot).

A snapshot's data file stores only the changed data blocks (modified and new data blocks) compared with the last snapshot.

Let's use the preceding figure for illustration. Assume that data was written to an EVS disk at 09:30 and 10:30. Snapshot 1 was created at 09:00, snapshot 2 at 10:00, and snapshot 3 at 11:00.

-  At 09:00, snapshot 1 was created for the disk. This was the first time that a snapshot was created for this disk, so snapshot 1 was a full snapshot and it contained all the data on the disk, including data blocks A, B, and C. The metadata file of snapshot 1 recorded information about the disk's full data blocks: A, B, and C.
-  After snapshot 1 was created, data block A was changed to A1, data block B was changed to B1, and data block D was added. Then, snapshot 2 was created at 10:00. It was an incremental snapshot. Compared with snapshot 1, data blocks A1, B1, and D were changed data blocks. The metadata file of snapshot 2 recorded information about the disk's full data blocks: A1, B1, C, and D, among which data block C was inherited from snapshot 1.
-  After snapshot 2 was created, data block A1 was changed to A2, data block C was changed to C1, and data block E was added. Then, snapshot 3 was created at 11:00. It was an incremental snapshot. Compared with snapshot 2, data blocks A2, C1, and E were changed data blocks. The metadata file of snapshot 3 recorded information about the disk's full data blocks: A2, B1, C1, D, and E, among which data blocks B1 and D were inherited from snapshot 2.

.. _evs_01_0098__en-us_topic_0197597144_section292714335117:

Calculating the Standard Snapshot Storage Usage
-----------------------------------------------

The total snapshot storage usage of an EVS disk is calculated by snapshot chain. A snapshot chain collects the storage space used by data blocks of all the snapshots of a disk. The storage usage of a single snapshot will not be greater than the disk capacity. As more snapshots are created for the disk, the storage usage of the snapshot chain may be greater than the disk capacity.

-  **Snapshot chain's storage usage calculation after snapshots are added**

   .. _evs_01_0098__en-us_topic_0197597144_en-us_topic_0066809008_fig18730151114539:

   .. figure:: /_static/images/en-us_image_0000002312239849.png
      :alt: **Figure 3** Snapshot chain with snapshots added

      **Figure 3** Snapshot chain with snapshots added

   Take the scenario in :ref:`Figure 3 <evs_01_0098__en-us_topic_0197597144_en-us_topic_0066809008_fig18730151114539>` as an example. Assume that the size of a snapshot's data block is fixed at 2 MiB. The snapshot chain's storage usage is calculated as follows:

   -  After snapshot 1 is created, the snapshot chain of the disk contains only one snapshot. Snapshot chain's storage usage = Snapshot 1's storage usage = Size of data block A + Size of data block B + Size of data block C = 6 MiB
   -  After snapshot 2 is created, the snapshot chain of the disk contains two snapshots: snapshot 1 and snapshot 2. Snapshot chain's storage usage = Snapshot 1's storage usage + Snapshot 2' storage usage = 6 MiB + (Size of data block A1 + Size of data block B1 + Size of data block D) = 12 MiB
   -  After snapshot 3 is created, the snapshot chain of the disk contains three snapshots: snapshot 1, snapshot 2, and snapshot 3. Snapshot chain's storage usage = Snapshot 1's storage usage + Snapshot 2' storage usage + Snapshot 3's storage usage = 6 MiB + 6 MiB + (Size of data block A2 + Size of data block C1 + Size of data block E) = 18 MiB

-  **Snapshot chain's storage usage calculation after snapshots are deleted**

   When a snapshot is deleted, all data block information in this snapshot's metadata file is traversed, and the following deletion rules are applied:

   -  If a data block is inherited by the next snapshot, it will not be deleted.
   -  If a data block is not inherited by the next snapshot:

      -  For an inherited data block, if the previous snapshot that the data block is inherited from is not deleted, the data block will not be deleted. Otherwise, it will be deleted.
      -  For a modified data block, it will be deleted.
      -  For a new data block, it will be deleted.


   .. figure:: /_static/images/en-us_image_0000002277640202.png
      :alt: **Figure 4** Snapshot data block deletion rules

      **Figure 4** Snapshot data block deletion rules

   The following example describes how to calculate a snapshot chain's storage usage after snapshots are deleted.

   .. _evs_01_0098__en-us_topic_0197597144_en-us_topic_0066809008_fig9261134113584:

   .. figure:: /_static/images/en-us_image_0000002277743340.png
      :alt: **Figure 5** Snapshot chain with snapshots deleted

      **Figure 5** Snapshot chain with snapshots deleted

   Take the scenario in :ref:`Figure 5 <evs_01_0098__en-us_topic_0197597144_en-us_topic_0066809008_fig9261134113584>` as an example. Assume that snapshot 2 is deleted at 14:00 and snapshot 3 is deleted at 15:00. The snapshot chain's storage usage is calculated as follows:

   -  Before any snapshot is deleted, the snapshot chain's storage usage is 18 MiB (Snapshot 1's storage usage + Snapshot 2's storage usage + Snapshot 3's storage usage).

   -  When snapshot 2 is deleted at 14:00, information about all data blocks in the metadata file of snapshot 2 is traversed.

      -  Data block A1: It is not inherited by snapshot 3 and is modified from data block A of snapshot 1. So, data block A1 will be deleted.
      -  Data block B1: It is inherited by snapshot 3, so it will not be deleted.
      -  Data block C: It is not inherited by snapshot 3, but is inherited from snapshot 1 and snapshot 1 is not deleted. So, data block C will not be deleted.
      -  Data block D: It is inherited by snapshot 3. So, it will not be deleted.

      After snapshot 2 is deleted, the snapshot chain's storage usage is 16 MiB (18 MiB - Size of data block A1).

   -  When snapshot 3 is deleted at 15:00, information about all data blocks in the metadata file of snapshot 3 is traversed.

      -  Data block A2: It is not inherited by the next snapshot and is modified from data block A1 of snapshot 2. So, data block A2 will be deleted.
      -  Data block B1: It is not inherited by the next snapshot, but is inherited from snapshot 2 and snapshot 2 has been deleted. So, data block B1 will be deleted.
      -  Data block C1: It is not inherited by the next snapshot and is modified from data block C of snapshot 2. So, data block C1 will be deleted.
      -  Data block D: It is not inherited by the next snapshot, but is inherited from snapshot 2 and snapshot 2 has been deleted. So, data block D will be deleted.
      -  Data block E: It is not inherited by the next snapshot and is newly added in snapshot 3. So, data block E will be deleted.

      After snapshot 3 is deleted, the snapshot chain's storage usage is 6 MiB (16 MiB - Size of data block A2 - Size of data block B1 - Size of data block C1 - Size of data block D - Size of data block E).

EVS allows you to view the snapshot storage usage on the console. For details, see :ref:`Checking the EVS Snapshot Storage Usage <evs_01_2712>`.

Differences Between Disk Backups and Disk Snapshots
---------------------------------------------------

Both disk backups and disk snapshots provide redundancies for improved disk data reliability. :ref:`Table 3 <evs_01_0098__en-us_topic_0197597144_table8676102116384>` lists the differences between them.

.. _evs_01_0098__en-us_topic_0197597144_table8676102116384:

.. table:: **Table 3** Differences between backups and snapshots

   +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Item              | Storage Solution                                                                                                                                                                                        | Data Synchronization                                                                                                                                                                                                                                                                                                                    | DR Range                                                                               | Service Recovery                                                                                               |
   +===================+=========================================================================================================================================================================================================+=========================================================================================================================================================================================================================================================================================================================================+========================================================================================+================================================================================================================+
   | Backup            | Backups are stored in OBS, instead of disks. This ensures data restoration upon disk damage or corruption.                                                                                              | A backup is a copy of a disk taken at a given time and is stored in a different location. Automatic backup can be performed based on backup policies. Deleting a disk will not delete its backups.                                                                                                                                      | A backup and its source disk reside in the same region, but can be in different AZs.   | You can use a backup to roll back data to its source disk or create a new disk. The data durability is high.   |
   +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Legacy Snapshot   | Snapshots are stored on the same disk as the source data.                                                                                                                                               | A snapshot is the state of a disk at a specific point in time and is stored on the same disk. If the disk is deleted, all its snapshots will also be deleted. For example, if you reinstalled or changed the server OS, snapshots of the system disk were also automatically deleted. Snapshots of the data disks can be used as usual. | A snapshot and its source disk reside in the same AZ.                                  | You can use a snapshot to roll back data to its source disk or create a new disk.                              |
   |                   |                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                                                                                         |                                                                                        |                                                                                                                |
   |                   | .. note::                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                         |                                                                                        |                                                                                                                |
   |                   |                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                                                                                         |                                                                                        |                                                                                                                |
   |                   |    Creating a backup requires a certain amount of time because data needs to be transferred to OBS. Creating a snapshot or rolling back data from a snapshot consumes less time than creating a backup. |                                                                                                                                                                                                                                                                                                                                         |                                                                                        |                                                                                                                |
   +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Standard Snapshot | Standard snapshots are stored in OBS, instead of disks. This ensures data restoration upon disk damage or corruption.                                                                                   | A snapshot is the state of a disk at a specific point in time and is stored in OBS. If the disk is deleted, all its snapshots will not be deleted.                                                                                                                                                                                      | A snapshot and its source disk reside in the same region, but can be in different AZs. | You can use a snapshot to roll back data to its source disk or create a new disk. The data durability is high. |
   +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
