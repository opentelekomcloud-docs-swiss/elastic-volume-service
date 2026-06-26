:original_name: ShowSnapshotGroup.html

.. _ShowSnapshotGroup:

Querying a Snapshot Consistency Group
=====================================

Function
--------

This API is used to query a snapshot consistency group.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

GET /v5/{project_id}/snapshot-groups/{snapshot_group_id}

.. table:: **Table 1** URI parameters

   +-------------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                   |
   +===================+=================+=================+===============================================================+
   | project_id        | Yes             | String          | The project ID.                                               |
   |                   |                 |                 |                                                               |
   |                   |                 |                 | For details, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------+
   | snapshot_group_id | Yes             | String          | The snapshot consistency group ID.                            |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

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

.. table:: **Table 3** Response body parameter

   +----------------+------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter      | Type                                                                                                             | Description                                          |
   +================+==================================================================================================================+======================================================+
   | snapshot_group | :ref:`SnapshotGroupDetail <showsnapshotgroup__en-us_topic_0000002229564402_response_snapshotgroupdetail>` object | The returned snapshot consistency group information. |
   +----------------+------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _showsnapshotgroup__en-us_topic_0000002229564402_response_snapshotgroupdetail:

.. table:: **Table 4** SnapshotGroupDetail

   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | Parameter             | Type               | Description                                                                       |
   +=======================+====================+===================================================================================+
   | id                    | String             | The ID of the snapshot consistency group.                                         |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | created_at            | String             | The time when the snapshot consistency group was created.                         |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | status                | String             | The status of the snapshot consistency group.                                     |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | updated_at            | String             | The time when the snapshot consistency group was updated.                         |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | name                  | String             | The name of the snapshot consistency group.                                       |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | description           | String             | The description of the snapshot consistency group.                                |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | enterprise_project_id | String             | The ID of the enterprise project to which the snapshot consistency group belongs. |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | tags                  | Map<String,String> | The tags of the snapshot consistency group.                                       |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+
   | server_id             | String             | The server ID.                                                                    |
   +-----------------------+--------------------+-----------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameter

   +-----------+---------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                    | Description                                        |
   +===========+=========================================================+====================================================+
   | error     | :ref:`Error <showsnapshotgroup__response_error>` object | The error information returned if an error occurs. |
   +-----------+---------------------------------------------------------+----------------------------------------------------+

.. _showsnapshotgroup__response_error:

.. table:: **Table 6** Error

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "snapshot_group" : {
       "id" : "5e0fc839-9a2f-4d45-8ae5-a54859083673",
       "server_id" : null,
       "project_id" : "060576838600d5762f2dc000470eb164",
       "enterprise_project_id" : "0",
       "name" : "test_ssg_name",
       "description" : "test_ssg_description",
       "status" : "available",
       "tags" : {
         "this_is_test_key" : "this_is_test_value"
       },
       "created_at" : "2024-02-17T02:58:48.583012",
       "updated_at" : "2024-02-17T02:58:48.736012"
     }
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error" : {
       "message" : "XXXX",
       "code" : "EVS.XXX"
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
