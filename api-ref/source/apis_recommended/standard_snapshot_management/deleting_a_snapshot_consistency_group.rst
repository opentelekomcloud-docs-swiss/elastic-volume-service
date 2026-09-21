:original_name: DeleteSnapshotGroup.html

.. _DeleteSnapshotGroup:

Deleting a Snapshot Consistency Group
=====================================

Function
--------

This API is used to delete a snapshot consistency group.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

DELETE /v5/{project_id}/snapshot-groups/{snapshot_group_id}

.. table:: **Table 1** URI parameters

   +-------------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                   |
   +===================+=================+=================+===============================================================+
   | project_id        | Yes             | String          | The project ID.                                               |
   |                   |                 |                 |                                                               |
   |                   |                 |                 | For details, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------+
   | snapshot_group_id | Yes             | String          | The snapshot ID.                                              |
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

**Status code: 202**

.. table:: **Table 3** Response body parameter

   +-----------------------+-----------------------+-----------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                 |
   +=======================+=======================+=============================================================================+
   | job_id                | String                | The task ID.                                                                |
   |                       |                       |                                                                             |
   |                       |                       | -  To query the task status, see :ref:`Querying Task Status <evs_04_0054>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 4** Response body parameter

   +-----------+----------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                                                   | Description                                        |
   +===========+========================================================================================+====================================================+
   | error     | :ref:`Error <deletesnapshotgroup__en-us_topic_0000002264643765_response_error>` object | The error information returned if an error occurs. |
   +-----------+----------------------------------------------------------------------------------------+----------------------------------------------------+

.. _deletesnapshotgroup__en-us_topic_0000002264643765_response_error:

.. table:: **Table 5** Error

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

   DELETE https://{endpoint}/v5/{project_id}/snapshot-groups/{snapshot_group_id}

Example Responses
-----------------

**Status code: 202**

.. code-block::

   {
       "job_id": "aee3b92e-e05d-4ff9-a013-c000629fc08d"
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
202         Accepted
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
