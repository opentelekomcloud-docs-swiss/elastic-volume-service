:original_name: evs_01_2721.html

.. _evs_01_2721:

Creating an EVS Snapshot
========================

Scenarios
---------

You can create EVS snapshots to save disk data at specific time points. Before you perform any critical operation, such as a data rollback, software upgrade, or data migration, you are advised to create snapshots to back up data. This ensures that your data is not affected even if an exception occurred during the operation.

Constraints
-----------

-  Snapshots can be created for both system disks and data disks.
-  Snapshots of encrypted disks are stored encrypted, and those of non-encrypted disks are stored non-encrypted.

-  You can create one standard snapshot for a disk at a time. You can only create the next standard snapshot for the same disk after the previous snapshot has been created.
-  It usually takes several minutes to create a standard snapshot. The time required varies depending on the amounts of data written to the disk. The larger the data volume, the longer the time required. The initial standard snapshot usually takes more time because data of the entire disk is backed up. Subsequent standard snapshots are quicker, but the time required is still determined by the amounts of changed data compared with each last snapshot. The more the changed data, the longer the time required.
-  If the data on a disk is rolled back from a snapshot, the next standard snapshot created for this disk will be a full snapshot.
-  During the creation of a standard snapshot, any incremental data written to the disk will not be backed up to the snapshot created.
-  During the creation of a standard snapshot, deleting the snapshot's source disk does not affect the creation of the snapshot.

Impacts on Performance
----------------------

During the snapshot creation, disk I/Os are affected, so you may experience slow reads or writes at some points. It is recommended that you create snapshots at off-peak hours.

Prerequisites
-------------

Snapshots can only be created for **Available** or **In-use** disks.

Creating a Snapshot on the **Disks** Page
-----------------------------------------

#. Sign in to the console.

#. Click |image1| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the target disk and click **Create Snapshot** in the **Operation** column.

   Configure the snapshot parameters according to :ref:`Table 1 <evs_01_2721__en-us_topic_0066615262_table17584125003610>`.

   .. _evs_01_2721__en-us_topic_0066615262_table17584125003610:

   .. table:: **Table 1** Snapshot parameters

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Parameter             | Description                                                                                                                                                                                              | Example Value                   |
      +=======================+==========================================================================================================================================================================================================+=================================+
      | Region                | The region to which the snapshot belongs.                                                                                                                                                                | eu-ch2                          |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | The snapshot must be in the same region as its source disk.                                                                                                                                              |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Disk Name/ID          | The name and ID of the source disk.                                                                                                                                                                      | ``-``                           |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Snapshot Name         | Mandatory                                                                                                                                                                                                | snapshot-01Created_from_evstest |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | The name can contain a maximum of 64 characters.                                                                                                                                                         |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Snapshot Description  | Optional                                                                                                                                                                                                 | ``-``                           |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | The description can contain up to 255 characters.                                                                                                                                                        |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Snapshot Type         | The type of the snapshot. Only standard snapshot is supported currently.                                                                                                                                 | Standard snapshot               |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | The time required for creating a standard snapshot depends on the size of data being backed up, but the initial snapshot usually takes a bit longer.                                                     |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Advanced Settings     | Optional                                                                                                                                                                                                 | ``-``                           |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | You can add tags when creating standard snapshots. Tags can help you to identify, classify, and search for your snapshots.                                                                               |                                 |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | .. note::                                                                                                                                                                                                |                                 |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       |    -  You can add a maximum of 20 tags to a snapshot.                                                                                                                                                    |                                 |
      |                       |    -  Tag keys of the same snapshot must be unique.                                                                                                                                                      |                                 |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | A tag consists of a tag key and a tag value.                                                                                                                                                             |                                 |
      |                       |                                                                                                                                                                                                          |                                 |
      |                       | -  A tag key cannot start or end with a space, or start with **\_sys\_**. It can contain a maximum of 128 characters and contain letters, digits, spaces, and the following special characters: \_.:=+-@ |                                 |
      |                       | -  A tag value can contain a maximum of 255 characters and contain letters, digits, spaces, and the following special characters: ``_.:/=+-@``                                                           |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

#. Click **Create Now**.

#. On the displayed **Details** page, view the details of the snapshot.

   -  If you do not need to modify the configuration, click **Submit**.
   -  If you need to modify the configuration, click **Previous**.

#. Go back to the **Snapshots** page and view the snapshot creation progress in the snapshot list.

   After the snapshot status changes to **Available**, the snapshot has been created.

   |image2|

Creating a Snapshot on the **Snapshots** Page
---------------------------------------------

#. Sign in to the console.

#. Click |image3| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   On the **Snapshots** page, click **Create Snapshot**.

   Configure the snapshot parameters according to :ref:`Table 2 <evs_01_2721__en-us_topic_0066615262_table1097922420177>`.

   .. _evs_01_2721__en-us_topic_0066615262_table1097922420177:

   .. table:: **Table 2** Snapshot parameters

      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Parameter               | Description                                                                                                                                                                                              | Example Value                   |
      +=========================+==========================================================================================================================================================================================================+=================================+
      | Region                  | Mandatory                                                                                                                                                                                                | eu-ch2                          |
      |                         |                                                                                                                                                                                                          |                                 |
      |                         | After you select a region, disks in the selected region will be displayed for you to choose from.                                                                                                        |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Select Disk             | Mandatory                                                                                                                                                                                                | ``-``                           |
      |                         |                                                                                                                                                                                                          |                                 |
      |                         | Select a disk for which you want to create a snapshot.                                                                                                                                                   |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Snapshot Name           | Mandatory                                                                                                                                                                                                | snapshot-01Created_from_evstest |
      |                         |                                                                                                                                                                                                          |                                 |
      |                         | The name can contain a maximum of 64 characters.                                                                                                                                                         |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Snapshot Description    | Optional                                                                                                                                                                                                 | ``-``                           |
      |                         |                                                                                                                                                                                                          |                                 |
      |                         | The description can contain up to 255 characters.                                                                                                                                                        |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Snapshot Type           | The type of the snapshot. Only standard snapshot is supported currently.                                                                                                                                 | Standard snapshot               |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Advanced Settings > Tag | Optional                                                                                                                                                                                                 | ``-``                           |
      |                         |                                                                                                                                                                                                          |                                 |
      |                         | You can add tags when creating standard snapshots. Tags can help you to identify, classify, and search for your snapshots.                                                                               |                                 |
      |                         |                                                                                                                                                                                                          |                                 |
      |                         | A tag consists of a tag key and a tag value.                                                                                                                                                             |                                 |
      |                         |                                                                                                                                                                                                          |                                 |
      |                         | -  A tag key cannot start or end with a space, or start with **\_sys\_**. It can contain a maximum of 128 characters and contain letters, digits, spaces, and the following special characters: \_.:=+-@ |                                 |
      |                         | -  A tag value can contain a maximum of 255 characters and contain letters, digits, spaces, and the following special characters: ``_.:/=+-@``                                                           |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

#. Click **Create Now**.

#. On the displayed **Details** page, view the details of the snapshot.

   -  If you do not need to modify the configuration, click **Submit**.
   -  If you need to modify the configuration, click **Previous**.

#. Go back to the **Snapshots** page and view the snapshot creation progress in the snapshot list.

   After the snapshot status changes to **Available**, the snapshot has been created.

   |image4|

.. |image1| image:: /_static/images/en-us_image_0000001933286285.jpg
.. |image2| image:: /_static/images/en-us_image_0000002277743436.png
.. |image3| image:: /_static/images/en-us_image_0000001933286285.jpg
.. |image4| image:: /_static/images/en-us_image_0000002348345941.png
