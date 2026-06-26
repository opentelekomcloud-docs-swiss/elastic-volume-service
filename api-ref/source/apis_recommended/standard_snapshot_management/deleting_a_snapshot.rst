:original_name: DeleteSnapshotV5.html

.. _DeleteSnapshotV5:

Deleting a Snapshot
===================

Function
--------

This API is used to delete a snapshot.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

DELETE /v5/{project_id}/snapshots/{snapshot_id}

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                   |
   +=================+=================+=================+===============================================================+
   | project_id      | Yes             | String          | The project ID.                                               |
   |                 |                 |                 |                                                               |
   |                 |                 |                 | For details, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | snapshot_id     | Yes             | String          | The snapshot ID.                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+

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

   +-----------+-------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                                                | Description                                        |
   +===========+=====================================================================================+====================================================+
   | error     | :ref:`Error <deletesnapshotv5__en-us_topic_0000002264563681_response_error>` object | The error information returned if an error occurs. |
   +-----------+-------------------------------------------------------------------------------------+----------------------------------------------------+

.. _deletesnapshotv5__en-us_topic_0000002264563681_response_error:

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

   DELETE https://{endpoint}/v5/{project_id}/snapshots/{snapshot_id}

Example Responses
-----------------

**Status code: 202**

.. code-block::

   {
       "job_id": "45dd412a-bc5c-4d32-9e94-f7a344c55862"
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
202         Accepted
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
