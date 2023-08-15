:original_name: evs_04_3011.html

.. _evs_04_3011:

Batch Adding Tags for the Specified EVS Disk
============================================

Function
--------

This API is used to batch add tags for the specified EVS disk.

-  When adding tags, if a tag key is consistent with an existing one, the new tag will overwrite the existing tag.
-  A maximum of 10 tags can be created for a disk.

Constraints
-----------

None

URI
---

-  URI format

   POST /v3/{project_id}/os-vendor-volumes/{volume_id}/tags/action

-  Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | project_id            | Yes                   | Specifies the project ID.                                                                        |
   |                       |                       |                                                                                                  |
   |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | volume_id             | Yes                   | Specifies the disk ID.                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+--------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type               | Mandatory       | Description                                                                                                                      |
   +=================+====================+=================+==================================================================================================================================+
   | tags            | List<resource_tag> | Yes             | Specifies the tag list. For details, see :ref:`Parameters in the resource_tag field <evs_04_3011__evs_04_2027_li4495404118563>`. |
   +-----------------+--------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | action          | String             | Yes             | Specifies the operation to perform. The value can be **create** or **delete**.                                                   |
   |                 |                    |                 |                                                                                                                                  |
   |                 |                    |                 | **create**: specifies to add tags.                                                                                               |
   +-----------------+--------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3011__evs_04_2027_li4495404118563:

   Parameters in the **resource_tag** field

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================================================+
   | key             | String          | Yes             | Specifies the tag key. Tag keys of a disk must be unique.                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                          |
   |                 |                 |                 | -  It can contain up to 36 Unicode characters.                                                                                                                                           |
   |                 |                 |                 | -  It cannot contain the following characters:                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                          |
   |                 |                 |                 |    -  Non-printable ASCII characters (0-31).                                                                                                                                             |
   |                 |                 |                 |    -  Special characters, including asterisks (*), left angle brackets (<), right angle brackets (>), backslashes (\\), equal signs (=), commas (,), vertical bars (|), and slashes (/). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | String          | Yes             | Specifies the tag value.                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                          |
   |                 |                 |                 | -  It can contain up to 43 Unicode characters.                                                                                                                                           |
   |                 |                 |                 | -  It cannot contain the following characters:                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                          |
   |                 |                 |                 |    -  Non-printable ASCII characters (0-31).                                                                                                                                             |
   |                 |                 |                 |    -  Special characters, including asterisks (*), left angle brackets (<), right angle brackets (>), backslashes (\\), equal signs (=), commas (,), vertical bars (|), and slashes (/). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "action": "create",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value3"
              }
          ]
      }

Response
--------

None

Status Codes
------------

-  Normal

   204

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
