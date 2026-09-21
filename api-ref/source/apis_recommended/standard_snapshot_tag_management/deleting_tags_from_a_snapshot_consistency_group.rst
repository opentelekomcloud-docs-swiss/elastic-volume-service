:original_name: BatchDeleteSnapshotGroupTag.html

.. _BatchDeleteSnapshotGroupTag:

Deleting Tags from a Snapshot Consistency Group
===============================================

Function
--------

This API is used to delete tags from a snapshot consistency group.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

POST /v5/{project_id}/snapshot-groups/{snapshot_group_id}/tags/delete

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

   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                       |
   +==============+===========+========+===================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | The user token. It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameter

   +-----------+-----------+---------------------------------------------------------------------------------------------------------------------------------+-------------------+
   | Parameter | Mandatory | Type                                                                                                                            | Description       |
   +===========+===========+=================================================================================================================================+===================+
   | tags      | Yes       | Array of :ref:`DeleteResourceTag <batchdeletesnapshotgrouptag__en-us_topic_0000002230867392_request_deleteresourcetag>` objects | The list of tags. |
   +-----------+-----------+---------------------------------------------------------------------------------------------------------------------------------+-------------------+

.. _batchdeletesnapshotgrouptag__en-us_topic_0000002230867392_request_deleteresourcetag:

.. table:: **Table 4** DeleteResourceTag

   ========= ========= ====== ==============
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============
   key       Yes       String The tag key.
   value     No        String The tag value.
   ========= ========= ====== ==============

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 5** Response body parameter

   +-----------+------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                                                           | Description                                        |
   +===========+================================================================================================+====================================================+
   | error     | :ref:`Error <batchdeletesnapshotgrouptag__en-us_topic_0000002230867392_response_error>` object | The error information returned if an error occurs. |
   +-----------+------------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _batchdeletesnapshotgrouptag__en-us_topic_0000002230867392_response_error:

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

.. code-block:: text

   DELETE https://{endpoint}/v5/{project_id}/snapshot-groups/{snapshot_group_id}/tags/delete

   {
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value3"
     } ]
   }

Example Responses
-----------------

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
204         No Content
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
