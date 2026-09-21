:original_name: GetSnapshotChainsCount.html

.. _GetSnapshotChainsCount:

Querying the Number of Snapshot Chains
======================================

Function
--------

This API is used to query the number of snapshot chains.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

GET /v5/{project_id}/snapshot-chains/count

.. table:: **Table 1** URI parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                   |
   +=================+=================+=================+===============================================================+
   | project_id      | Yes             | String          | The project ID.                                               |
   |                 |                 |                 |                                                               |
   |                 |                 |                 | For details, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-------------------+-----------+--------+--------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                            |
   +===================+===========+========+========================================================+
   | volume_id         | No        | String | The ID of the disk that the snapshot chain belongs to. |
   +-------------------+-----------+--------+--------------------------------------------------------+
   | availability_zone | No        | String | The AZ of the disk that the snapshot chain belongs to. |
   +-------------------+-----------+--------+--------------------------------------------------------+
   | category          | No        | String | The snapshot chain type.                               |
   +-------------------+-----------+--------+--------------------------------------------------------+
   | id                | No        | String | The snapshot chain ID.                                 |
   +-------------------+-----------+--------+--------------------------------------------------------+

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
   | error     | :ref:`Error <getsnapshotchainscount__en-us_topic_0000002264643761_response_error>` object | The error information returned if an error occurs. |
   +-----------+-------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _getsnapshotchainscount__en-us_topic_0000002264643761_response_error:

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

   GET https://{endpoint}/v5/{project_id}/snapshot-chains/count

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
