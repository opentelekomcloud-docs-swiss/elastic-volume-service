:original_name: ListSnapshotChains.html

.. _ListSnapshotChains:

Listing Snapshot Chains
=======================

Function
--------

This API is used to list snapshot chains.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

GET /v5/{project_id}/snapshot-chains

.. table:: **Table 1** URI parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                   |
   +=================+=================+=================+===============================================================+
   | project_id      | Yes             | String          | The project ID.                                               |
   |                 |                 |                 |                                                               |
   |                 |                 |                 | For details, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                              |
   +=================+=================+=================+==========================================================================================================================+
   | marker          | No              | String          | The ID of the resource from which the pagination query starts. It is the ID of the last resource on the previous page.   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | The maximum number of query results that can be returned.                                                                |
   |                 |                 |                 |                                                                                                                          |
   |                 |                 |                 | The value ranges from **1** to **1000**, and the default value is **1000**. The returned value cannot exceed this limit. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String          | The snapshot chain ID.                                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | volume_id       | No              | String          | The ID of the disk that the snapshot chain belongs to.                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | category        | No              | String          | The snapshot chain type. The value can be **standard**, **backup**, or **server_backup**.                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | The user token.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameter

   +-----------------+---------------------------------------------------------------------------------------------------------------------+------------------------------+
   | Parameter       | Type                                                                                                                | Description                  |
   +=================+=====================================================================================================================+==============================+
   | snapshot_chains | Array of :ref:`snapshot_chains <listsnapshotchains__en-us_topic_0000002264643749_response_snapshot_chains>` objects | The list of snapshot chains. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+------------------------------+

.. _listsnapshotchains__en-us_topic_0000002264643749_response_snapshot_chains:

.. table:: **Table 5** snapshot_chains

   +-------------------+---------+--------------------------------------------------------+
   | Parameter         | Type    | Description                                            |
   +===================+=========+========================================================+
   | id                | String  | The snapshot chain ID.                                 |
   +-------------------+---------+--------------------------------------------------------+
   | availability_zone | String  | The AZ of the disk that the snapshot chain belongs to. |
   +-------------------+---------+--------------------------------------------------------+
   | snapshot_count    | Integer | The number of snapshots on the snapshot chain.         |
   +-------------------+---------+--------------------------------------------------------+
   | capacity          | Integer | The snapshot chain storage usage.                      |
   +-------------------+---------+--------------------------------------------------------+
   | project_id        | String  | The project ID.                                        |
   +-------------------+---------+--------------------------------------------------------+
   | volume_id         | String  | The ID of the disk that the snapshot chain belongs to. |
   +-------------------+---------+--------------------------------------------------------+
   | category          | String  | The snapshot chain type.                               |
   +-------------------+---------+--------------------------------------------------------+
   | created_at        | String  | The creation time.                                     |
   +-------------------+---------+--------------------------------------------------------+
   | updated_at        | String  | The update time.                                       |
   +-------------------+---------+--------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameter

   +-----------+---------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                                                  | Description                                        |
   +===========+=======================================================================================+====================================================+
   | error     | :ref:`Error <listsnapshotchains__en-us_topic_0000002264643749_response_error>` object | The error information returned if an error occurs. |
   +-----------+---------------------------------------------------------------------------------------+----------------------------------------------------+

.. _listsnapshotchains__en-us_topic_0000002264643749_response_error:

.. table:: **Table 7** Error

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | code                  | String                | The error code returned if an error occurs.                             |
   |                       |                       |                                                                         |
   |                       |                       | For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | message               | String                | The error message returned if an error occurs.                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v5/{project_id}/snapshot-chains

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "snapshot_chains" : [ {
       "id" : "e97f57fe-767b-46c6-ac1b-10b77e491406",
       "capacity" : 0,
       "project_id" : "fb640396c4344e4f96057fab643fe5b5",
       "volume_id" : "7c40f5ae-2b26-4922-b586-3d41af4822f1",
       "category" : "standard",
       "availability_zone": "eu-de-01",
       "snapshot_count" : 1,
       "created_at" : "2023-10-25T08:56:26.087002",
       "updated_at" : "2023-10-25T08:56:26.758003"
     }
    ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error" : {
       "message" : "XXXX",
       "code" : "XXX"
     }
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
