:original_name: ListSnapshotGroupTags.html

.. _ListSnapshotGroupTags:

Querying All Snapshot Consistency Group Tags
============================================

Function
--------

This API is used to query all snapshot consistency group tags.

Calling Method
--------------

For details, see :ref:`Calling APIs <evs_04_0009>`.

URI
---

GET /v5/{project_id}/snapshot-groups/tags

.. table:: **Table 1** URI parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                   |
   +=================+=================+=================+===============================================================+
   | project_id      | Yes             | String          | The project ID.                                               |
   |                 |                 |                 |                                                               |
   |                 |                 |                 | For details, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                       |
   +==============+===========+========+===================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | The user token. It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameter

   ========= ========================= ====================================
   Parameter Type                      Description
   ========= ========================= ====================================
   tags      Map<String,Array<String>> Information about all resource tags.
   ========= ========================= ====================================

**Status code: 400**

.. table:: **Table 4** Response body parameter

   +-----------+------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                                                     | Description                                        |
   +===========+==========================================================================================+====================================================+
   | error     | :ref:`Error <listsnapshotgrouptags__en-us_topic_0000002231027184_response_error>` object | The error information returned if an error occurs. |
   +-----------+------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _listsnapshotgrouptags__en-us_topic_0000002231027184_response_error:

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

   GET https://{endpoint}/v5/{project_id}/snapshot-groups/tags

Example Responses
-----------------

**Status code: 200**

.. code-block::

   {
     "tags" : {
       "key_0" : [ "value_0" ],
       "key_1" : [ "value_1", "value_2", "value_3", "value_4" ]
     }
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
