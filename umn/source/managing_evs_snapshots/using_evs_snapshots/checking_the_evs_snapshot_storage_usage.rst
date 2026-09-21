:original_name: evs_01_2712.html

.. _evs_01_2712:

Checking the EVS Snapshot Storage Usage
=======================================

Scenarios
---------

You can check the storage used by all snapshots of an EVS disk, the total storage used by all snapshots in a specified period, and the total storage used by all snapshots of your account in a specified region.

Constraints
-----------

-  The size of a single snapshot is smaller than the capacity of its source disk.
-  A snapshot chain's storage usage may be greater than the capacity of the corresponding disk, because one disk may have multiple snapshots.

Checking the Total Storage Usage of All Snapshots of a Disk by Snapshot Chain
-----------------------------------------------------------------------------

The total snapshot storage usage of an EVS disk is calculated by snapshot chain. A snapshot chain measures the storage space used by data blocks of all the snapshots of a disk. For details about the measurement principles, see :ref:`Calculating the Standard Snapshot Storage Usage <evs_01_0098__en-us_topic_0197597144_section292714335117>`.

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. Locate the disk that you want to check their total snapshot usage and click |image3| to copy the disk ID.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The **Snapshots** page is displayed.

#. Click the **Snapshot Chains** tab.


   .. figure:: /_static/images/en-us_image_0000002493287732.png
      :alt: **Figure 1** Snapshot Chains

      **Figure 1** Snapshot Chains

#. In the search box above the list, select **Disk ID**, paste the copied disk ID, and click |image4|.

#. View the capacity displayed in the **Snapshot Space Usage** column.

#. (Optional) Click the number displayed in the **Snapshots** column to view all the snapshots in the snapshot chain.

Querying the Total Snapshot Storage Usage in a Specified Period
---------------------------------------------------------------

Perform the following operations on the console to view the total snapshot storage usage in a specified period in the current region.

#. Log in to the console.

#. Click |image5| in the upper left corner and select the desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The **Snapshots** page is displayed.

#. Click the **Snapshot Space Usages** tab.

#. View the snapshot storage usage and snapshot quantity above the tabs.

#. Specify a time range for the query (minimum interval: 1 hour). You can also query the snapshot storage usage by the last 1 day, last 7 days, last 15 days, or last 30 days.


   .. figure:: /_static/images/en-us_image_0000002493444466.png
      :alt: **Figure 2** Querying the total snapshot storage usage in a specified period

      **Figure 2** Querying the total snapshot storage usage in a specified period

Related Links
-------------

-  You are advised to periodically delete snapshots that are no longer used. This helps you avoid unnecessary billing on the snapshots. For details, see :ref:`Deleting an EVS Snapshot <evs_01_0011>`.

.. |image1| image:: /_static/images/en-us_image_0000002301561710.png
.. |image2| image:: /_static/images/en-us_image_0000002301721398.jpg
.. |image3| image:: /_static/images/en-us_image_0000002277743480.png
.. |image4| image:: /_static/images/en-us_image_0000002312353065.png
.. |image5| image:: /_static/images/en-us_image_0000002301561710.png
