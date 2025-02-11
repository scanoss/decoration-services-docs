SCANOSS Provenance dataset
==========================

The SCANOSS Provenance provides information about the location of the contribuitors of a project of the user's choice.

.. note::
    This dataset
 is only available to premium users (Shared or Dedicated SaaS and On-Premises).

Ways to consume this dataset
----------------------------

There are multiple ways to consume this dataset, one of which is throught the use of `scanoss-py <https://github.com/scanoss/scanoss.py>`_ the SCANOSS Python CLI.

To consume the Provenance dataset from scanoss-py, you would need to run the following command:

.. code-block:: bash

    scanoss-py comp prov --key <api_key> --purl <package_url>

After running that command, you should receive the output in the following format:

.. literalinclude:: resources/provenance.json
    :language: json

In this example, we are querying the Provenance information for the scanoss.py project and getting the location of the contribuitors for the project: Argentina, Germany, South Korea and so on.


You will also see a two different lists of provenance information: curated_locations and declared_locations. At SCANOSS we strive for getting the most accurate results, because of this our team of curators work on validating the veracity of the information we gather. However, this isn't possible for all the information we gather, the declared_locations list contains data made available by the contribuitors.


.. note:: 
    For some projects with 5000 or more contribuitors you may receive a message saying "Too many contributors for: <package_url>", that is intentional and related to GitHub's API limit for querying this information.

Other ways to query the dataset
-------------------------------

There are other ways to query this dataset, one of them is using the SCANOSS API as it follows:

.. code-block:: bash

    curl --location 'https://api.scanoss.com/api/v2/provenance/countries' \
    --header 'Content-Type: application/json' \
    --header 'X-Api-Key: <api_key>' \
    --data '{
    "purls": [
        {
        "purl": <package_url>
        }
    ]
    }'

For more information refer to the `API documentation <https://github.com/scanoss/papi/blob/main/CLIENT_HELP.md>`_ and `protobuff definitions <https://github.com/scanoss/papi/blob/main/protobuf/scanoss/api/provenance/v2/scanoss-provenance.proto>`_. 