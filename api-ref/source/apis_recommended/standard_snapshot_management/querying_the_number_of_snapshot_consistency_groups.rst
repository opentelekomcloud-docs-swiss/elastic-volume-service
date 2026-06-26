:original_name: GetSnapshotsGroupCount.html

.. _GetSnapshotsGroupCount:

Querying the Number of Snapshot Consistency Groups
==================================================

Function
--------

This API is used to query the number of snapshot consistency groups.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

GET /v5/{project_id}/snapshot-groups/count

.. table:: **Table 1** URI parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                   |
   +=================+=================+=================+===============================================================+
   | project_id      | Yes             | String          | The project ID.                                               |
   |                 |                 |                 |                                                               |
   |                 |                 |                 | For details, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type   | Description                                                                                 |
   +=======================+===========+========+=============================================================================================+
   | name                  | No        | String | The name of the snapshot consistency group.                                                 |
   +-----------------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | status                | No        | String | The status of the snapshot consistency group.                                               |
   +-----------------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | id                    | No        | String | The ID of the snapshot consistency group.                                                   |
   +-----------------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | enterprise_project_id | No        | String | The ID of the enterprise project to which the snapshot consistency group belongs.           |
   +-----------------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | tag_key               | No        | String | The tag key of the snapshot consistency group.                                              |
   +-----------------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | tags                  | No        | String | The key-value pairs of the snapshot consistency group tags, for example, {"key1":"value1"}. |
   +-----------------------+-----------+--------+---------------------------------------------------------------------------------------------+

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

   ========= ======= ======================
   Parameter Type    Description
   ========= ======= ======================
   count     Integer The resource quantity.
   ========= ======= ======================

**Status code: 400**

.. table:: **Table 5** Response body parameter

   +-----------+-------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                                                      | Description                                        |
   +===========+===========================================================================================+====================================================+
   | error     | :ref:`Error <getsnapshotsgroupcount__en-us_topic_0000002229724194_response_error>` object | The error information returned if an error occurs. |
   +-----------+-------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _getsnapshotsgroupcount__en-us_topic_0000002229724194_response_error:

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

   GET https://{endpoint}/v5/{project_id}/snapshot-groups/count

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "count" : 100
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

=========== ================
Status Code Description
=========== ================
200         Success response
400         Bad Request
=========== ================

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
