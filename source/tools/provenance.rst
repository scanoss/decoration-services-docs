SCANOSS Provenance service
==========================

The SCANOSS Provenance provides information about the location of the contribuitors of a project of the user's choice.

.. note::
    This service is only available to premium users (Shared or Dedicated SaaS and On-Premises).

Ways to consume this service
----------------------------

There are multiple ways to consume this service, one of which is throught the use of `scanoss-py <https://github.com/scanoss/scanoss.py>`_ the SCANOSS Python CLI.

To consume the Provenance service from scanoss-py, you would need to run the following command:

.. code-block:: bash

    scanoss-py comp prov --key <api_key> --purl <package_url>

After running that command, you should receive the output in the following format:

.. literalinclude:: resources/provenance.json
    :language: json

In this example, we are querying the Provenance information for the scanoss.py project and getting the location of the contribuitors for the project: Argentina, Germany, South Korea and so on.

.. note:: 
    For some projects with 5000 or more contribuitors you may receive a message saying "Too many contributors for: <package_url>", that is intentional and related to GitHub's API limit for querying this information.

Other ways to query the service
-------------------------------

There are other ways to query this service, for that we encourage you to refer to the `documentation for the API <https://github.com/scanoss/papi/blob/main/CLIENT_HELP.md>`_ where you will find all methods and specifications.