:original_name: en-us_topic_0014580741.html

.. _en-us_topic_0014580741:

What Is EVS?
============

Overview
--------

Elastic Volume Service (EVS) offers scalable block storage for cloud servers. With high reliability, high performance, and a variety of specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouses, and high-performance computing (HPC) applications.

EVS disks are similar to hard disks in PCs. They must be attached to servers for use and cannot be used alone. You can initialize EVS disks, create file systems on them, and store data persistently on them.

EVS disks are sometimes just referred to as disks in this document.


.. figure:: /_static/images/en-us_image_0000001224414093.png
   :alt: **Figure 1** EVS architecture

   **Figure 1** EVS architecture

EVS Advantages
--------------

EVS has the following advantages:

.. table:: **Table 1** EVS advantages

   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Advantage                     | Description                                                                                                                                                                                                                      | Related Knowledge                                          |
   +===============================+==================================================================================================================================================================================================================================+============================================================+
   | Various disk types            | EVS provides a variety of disk types for you to choose from, and EVS disks can be used as data disks and system disks for servers. You can select an appropriate disk type that best suits your budget and service requirements. | :ref:`Disk Types and Performance <en-us_topic_0014580744>` |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Elastic scalability           | The EVS disk capacity ranges from 10 GiB to 32 TiB. When it no longer meets your needs, you can expand the disk capacity up to 32 TiB in increments of 1 GiB, without interrupting your applications.                            | :ref:`Expansion Overview <evs_01_0006>`                    |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   |                               | Besides the disk capacity limit, the additional space you can add cannot exceed the remaining quota. You can increase the quota if the remaining quota is insufficient.                                                          | :ref:`Querying EVS Resource Quotas <evs_01_0070>`          |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | High security and reliability | Both system disks and data disks support data encryption to ensure data security.                                                                                                                                                | :ref:`EVS Encryption <evs_01_0001>`                        |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   |                               | Data protection functions, such as backups and snapshots, safeguard the disk data, preventing incorrect data caused by application exceptions or attacks.                                                                        | :ref:`EVS Backup <evs_01_0021>`                            |
   |                               |                                                                                                                                                                                                                                  |                                                            |
   |                               |                                                                                                                                                                                                                                  | :ref:`EVS Snapshot <en-us_topic_0066809008>`               |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Real-time monitoring          | On Cloud Eye, you can monitor the disk health and operating status at any time.                                                                                                                                                  | :ref:`Viewing EVS Monitoring Data <evs_01_0044>`           |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+

Differences Between EVS and OBS
-------------------------------

There are currently two types of storage available for you to choose from: EVS and Object Storage Service (OBS). See their differences in the following table.

.. table:: **Table 2** Differences between EVS and OBS

   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Service         | Overall Introduction                                                                                                                                                                                                                                | Typical Application Scenarios                                                           | Storage Capacity                                                                                                  |
   +=================+=====================================================================================================================================================================================================================================================+=========================================================================================+===================================================================================================================+
   | EVS             | EVS provides scalable block storage that features high reliability, high performance, and a variety of specifications for servers.                                                                                                                  | -  Enterprise office applications                                                       | EVS disks start at 10 GiB and can be expanded as required in 1 GiB increments to up to 32 TiB.                    |
   |                 |                                                                                                                                                                                                                                                     | -  Development and testing                                                              |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Enterprise applications, including SAP, Microsoft Exchange, and Microsoft SharePoint |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Distributed file systems                                                             |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Various databases, including MongoDB, Oracle, SQL Server, MySQL, and PostgreSQL      |                                                                                                                   |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | OBS             | OBS provides cloud storage for unstructured data, such as files, pictures, and videos. With multiple options for migration to the cloud, OBS provides low-cost, reliable storage access for massive data and supports online multimedia processing. | -  Enterprise backup and archive                                                        | OBS has limitless storage capacity, and storage resources are available for linear and nearly infinite expansion. |
   |                 |                                                                                                                                                                                                                                                     | -  Big data analysis                                                                    |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Enterprise cloud box                                                                 |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Static website hosting                                                               |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Cloud-native applications                                                            |                                                                                                                   |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

User Permissions
----------------

For details about user permissions, see `Permissions <https://docs.sc.otc.t-systems.com/en-us/permissions/index.html>`__.
