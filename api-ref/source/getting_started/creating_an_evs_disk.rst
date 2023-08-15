:original_name: evs_04_0016.html

.. _evs_04_0016:

Creating an EVS Disk
====================

Scenarios
---------

This topic describes how to create an EVS disk by calling APIs. For details about how to call APIs, see :ref:`Calling APIs <evs_04_0009>`.

In the following example, APIs are called to create a disk from a snapshot.

Prerequisites
-------------

You have planned the region where you want to create the disk and obtained the endpoint required for calling the API. For details, see :ref:`Endpoints <evs_04_0004>`.

Procedure
---------

#. Create a disk from the snapshot.

   API: :ref:`Creating EVS Disks <evs_04_2013>`

   -  Example request

      POST https://*{endpoint}*/v2/ba546eb46e7247c9aadb566ed7a1d31f/cloudvolumes

      .. code-block::

         {
             "volume": {
                 "count": 1,
                 "availability_zone": "az-dc-1",
                 "description": "test_volume_1",
                 "size": 120,
                 "snapshot_id": "0b126d3b-f2af-404d-8d39-a42fce70065a",
                 "name": "test_volume_1",
                 "volume_type": "SAS"
             }
         }

   -  Example response

      .. code-block::

         {
           "job_id": "ff8080816b512df7016b6ab8982b496b"
         }
