:original_name: UpdateSnapshotGroup.html

.. _UpdateSnapshotGroup:

Updating a Snapshot Consistency Group
=====================================

Function
--------

This API is used to update a snapshot consistency group.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

PUT /v5/{project_id}/snapshot-groups/{snapshot_group_id}

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
   | X-Auth-Token    | No              | String          | The user token.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameter

   +----------------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+
   | Parameter      | Mandatory | Type                                                                                                                                      | Description                                               |
   +================+===========+===========================================================================================================================================+===========================================================+
   | snapshot_group | Yes       | :ref:`UpdateSnapshotGroupResponseBody <updatesnapshotgroup__en-us_topic_0000002264563697_request_updatesnapshotgroupresponsebody>` object | The snapshot consistency group information to be updated. |
   +----------------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+

.. _updatesnapshotgroup__en-us_topic_0000002264563697_request_updatesnapshotgroupresponsebody:

.. table:: **Table 4** UpdateSnapshotGroupResponseBody

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | name            | No              | String          | The name of the snapshot consistency group. It can contain a maximum of 255 bytes.        |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Minimum length: 0                                                                         |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Maximum length: 255                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | description     | No              | String          | The description of the snapshot consistency group. It can contain a maximum of 255 bytes. |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Minimum length: 0                                                                         |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Maximum length: 255                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameter

   +----------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | Parameter      | Type                                                                                                               | Description                                         |
   +================+====================================================================================================================+=====================================================+
   | snapshot_group | :ref:`SnapshotGroupDetail <updatesnapshotgroup__en-us_topic_0000002264563697_response_snapshotgroupdetail>` object | The updated snapshot consistency group information. |
   +----------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+

.. _updatesnapshotgroup__en-us_topic_0000002264563697_response_snapshotgroupdetail:

.. table:: **Table 6** SnapshotGroupDetail

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

.. table:: **Table 7** Response body parameter

   +-----------+-----------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                      | Description                                        |
   +===========+===========================================================+====================================================+
   | error     | :ref:`Error <updatesnapshotgroup__response_error>` object | The error information returned if an error occurs. |
   +-----------+-----------------------------------------------------------+----------------------------------------------------+

.. _updatesnapshotgroup__response_error:

.. table:: **Table 8** Error

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

   PUT https://{endpoint}/v5/{project_id}/snapshot-groups/{snapshot_group_id}

   {
     "snapshot_group": {
       "name": "snap-group-001",
       "description": "test"
     }
   }

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
