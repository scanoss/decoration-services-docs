SCANOSS Cryptography dataset
==========================

The SCANOSS Cryptography dataset provides information about the cryptography algorithms of a project, as well as export control information related to the project's dependencies. 

.. note::
    This dataset is only available to premium users (Shared or Dedicated SaaS and On-Premises).

Ways to consume this dataset
----------------------------

There are multiple ways to consume this dataset, one of which is throught the use of `scanoss-py <https://github.com/scanoss/scanoss.py>`_ the SCANOSS Python CLI.

To consume the Cryptography dataset from scanoss-py, you would need to run the following command:

.. code-block:: bash

    scanoss-py comp prov --key <api_key> --purl <package_url> 

You can also pass a file containing the list of files to be scanned with the --input parameter, the format for that file goes like this:

.. literalinclude:: resources/cryptography_format.json
    :language: json

After running the scan, you should receive the output in the following format: 

.. literalinclude:: resources/cryptography.json
    :language: json

In this example, we are querying the Cryptography information for the scanoss.py project and getting the .


.. note:: 
    For some projects with 5000 or more contribuitors you may receive a message saying "Too many contributors for: <package_url>", that is intentional and related to GitHub's API limit for querying this information.

Other ways to query the dataset
-------------------------------

There are other ways to query this dataset, one of them is using the SCANOSS API as it follows:

.. code-block:: bash

    curl --location 'https://api.scanoss.com/api/v2/cryptography/algorithms' \
    --header 'Content-Type: application/json' \
    --header 'X-Api-Key: <api_key>' \
    --data '{"purls": [
    {
      "purl": <package_url>,
      "requirement": "v4.0"
    }, 
     {
      "purl": <package_url>,
      "requirement": "4.3"
    }
    ]
    }'

.. code-block:: bash

    curl --location 'https://api.scanoss.com/api/v2/cryptography/algorithmsInRange' \
    --header 'Content-Type: application/json' \
    --header 'X-Api-Key: <api_key>' \
    --data '{
    "purls": [
        {
            "purl": <package_url>,
            "requirement": ">0.5"
        }
    ]
    }'


.. note::
    As a requirement for the API query, you would need to specify the desired version to query or a range of versions.

For more information refer to the `API documentation <https://github.com/scanoss/papi/blob/main/CLIENT_HELP.md>`_ and `protobuff definitions <https://github.com/scanoss/papi/blob/main/protobuf/scanoss/api/cryptography/v2/scanoss-cryptography.proto>`_. 
