:original_name: evs_04_3016.html

.. _evs_04_3016:

Querying the Number of EVS Disks by Tag
=======================================

Function
--------

This API is used to query the number of EVS disks by tag.

Constraints
-----------

None

URI
---

-  URI format

   POST /v3/{project_id}/os-vendor-volumes/resource_instances/action

-  Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | project_id            | Yes                   | Specifies the project ID.                                                                        |
   |                       |                       |                                                                                                  |
   |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <evs_04_0046>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type             | Mandatory       | Description                                                                                                                                              |
   +=================+==================+=================+==========================================================================================================================================================+
   | tags            | Array of objects | No              | Specifies the key-value pairs of the tag. For details, see :ref:`Parameters in the tags field <evs_04_3016__evs_04_2032_li8528152083214>`.               |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | The **tags** field cannot be left empty.                                                                                                                 |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | One tag list can contain a maximum of 10 keys.                                                                                                           |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | Tag keys in a tag list must be unique.                                                                                                                   |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | When multiple keys are specified in a tag list, only the disks having all specified keys are queried.                                                    |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | .. note::                                                                                                                                                |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 |    If multiple tag lists are specified in the request, only the disks that meet the requirements of the last tag list are queried.                       |
   +-----------------+------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | String           | Yes             | Specifies the operation identifier.                                                                                                                      |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | Specifying **count** queries the number of disks by tag.                                                                                                 |
   +-----------------+------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | Array of objects | No              | Specifies the query criteria that the resource supports. For details, see :ref:`Parameters in the match field <evs_04_3016__evs_04_2032_li15751146383>`. |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | The **matches** field cannot be left empty.                                                                                                              |
   |                 |                  |                 |                                                                                                                                                          |
   |                 |                  |                 | Tag keys in the list must be unique.                                                                                                                     |
   +-----------------+------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3016__evs_04_2032_li8528152083214:

   Parameters in the **resource_tag** field

   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type             | Mandatory       | Description                                                                                                                                                                              |
   +=================+==================+=================+==========================================================================================================================================================================================+
   | key             | String           | Yes             | Specifies the tag key. Tag keys of a disk must be unique.                                                                                                                                |
   |                 |                  |                 |                                                                                                                                                                                          |
   |                 |                  |                 | -  It can contain up to 36 Unicode characters.                                                                                                                                           |
   |                 |                  |                 | -  It cannot contain the following characters:                                                                                                                                           |
   |                 |                  |                 |                                                                                                                                                                                          |
   |                 |                  |                 |    -  Non-printable ASCII characters (0-31).                                                                                                                                             |
   |                 |                  |                 |    -  Special characters, including asterisks (*), left angle brackets (<), right angle brackets (>), backslashes (\\), equal signs (=), commas (,), vertical bars (|), and slashes (/). |
   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values          | Array of objects | Yes             | One value list can contain a maximum of 10 values.                                                                                                                                       |
   |                 |                  |                 |                                                                                                                                                                                          |
   |                 |                  |                 | Tag values in a value list must be unique.                                                                                                                                               |
   |                 |                  |                 |                                                                                                                                                                                          |
   |                 |                  |                 | If the value list is left empty, any tag value can be matched.                                                                                                                           |
   |                 |                  |                 |                                                                                                                                                                                          |
   |                 |                  |                 | When multiple values are specified in a value list and the key requirements are met, disks that have any of the specified values are queried.                                            |
   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3016__evs_04_2032_li15751146383:

   Parameters in the **match** field

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================+
   | key             | String          | Yes             | Specifies the tag key. The value is of the enumerated type.                                                                                 |
   |                 |                 |                 |                                                                                                                                             |
   |                 |                 |                 | The value can be as follows:                                                                                                                |
   |                 |                 |                 |                                                                                                                                             |
   |                 |                 |                 | -  **resource_name**: disk name.                                                                                                            |
   |                 |                 |                 | -  **service_type**: service type.                                                                                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | String          | Yes             | Specifies the tag value.                                                                                                                    |
   |                 |                 |                 |                                                                                                                                             |
   |                 |                 |                 | -  It can contain up to 255 Unicode characters.                                                                                             |
   |                 |                 |                 | -  An empty string specifies an exact match, and a non-empty string specifies a fuzzy query.                                                |
   |                 |                 |                 | -  If **resource_name** is specified for **key**, spaces before and after the tag value will be discarded.                                  |
   |                 |                 |                 | -  If **service_type** is specified for **key**, the value is of the enumerated type. It can be **EVS** or **DSS** and is case-insensitive. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "action": "count",
          "tags": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "matches": [
              {
                  "key": "resource_name",
                  "value": "resource1"
              },
              {
                  "key": "service_type",
                  "value": "EVS"
              }
          ]
      }

Response
--------

-  Parameter description

   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                                                                                                  |
   +=============+=========+==============================================================================================================================================================+
   | total_count | Integer | Specifies the total number of disks that meet the query criteria.                                                                                            |
   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error       | Object  | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3016__evs_04_2032_li0419202382514>`. |
   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3016__evs_04_2032_li0419202382514:

   Parameters in the **error** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | message               | String                | The error message returned if an error occurs.                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | code                  | String                | The error code returned if an error occurs.                             |
   |                       |                       |                                                                         |
   |                       |                       | For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "total_count": 1000
      }

   or

   .. code-block::

      {
          "error": {
              "message": "XXXX",
              "code": "XXX"
          }
      }

   In the preceding example, **error** indicates a general error, for example, **badRequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "computeFault": {
              "message": "The server has either erred or is incapable of performing the requested operation.",
              "code": 500
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
