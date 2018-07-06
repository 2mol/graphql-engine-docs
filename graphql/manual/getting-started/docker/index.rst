Run Hasura GraphQL Engine and Postgres using Docker
===================================================

This guide will help you get Hasura Graphql engine and Postgres running as Docker containers using Docker Compose.
This is the easiest way of setting up Hasura on your **local environment**.

If you're looking for instructions on how to run the Hasura GraphQL engine connected to an existing postgres database, head to :doc:`Run Hasura with docker <docker-run>`.

**Prerequisites**:

- `Docker <https://docs.docker.com/install/>`_
- `Docker Compose <https://docs.docker.com/compose/install/>`_

Step 1: Install the Hasura CLI
------------------------------

.. rst-class:: api_tabs
.. tabs::

   .. tab:: Mac

      In your terminal enter the following command:

      .. code-block:: bash

         curl -L https://cli.hasura.io/install.sh | bash

      This will install the ``hasura`` CLI in ``/usr/local/bin``. You might have to provide
      your ``sudo`` password depending on the permissions of your ``/usr/local/bin`` location.

   .. tab:: Linux

      Open your linux shell and run the following command:

      .. code-block:: bash

         curl -L https://cli.hasura.io/install.sh | bash

      This will install the ``hasura`` CLI tool in ``/usr/local/bin``. You might have to provide
      your ``sudo`` password depending on the permissions of your ``/usr/local/bin`` location.

   .. tab:: Windows

      .. note::

         You should have ``git bash`` installed to use ``hasura`` CLI. Download git bash using the following `(link)
         <https://git-scm.com/download/win>`_. Also, make sure you install it in ``MinTTY`` mode, instead of Windows'
         default console.

      Download the ``hasura`` installer:

      * `hasura (64-bit Windows installer) <https://cli.hasura.io/install/windows-amd64>`_
      * `hasura (32-bit Windows installer) <https://cli.hasura.io/install/windows-386>`_

      **Note:** Please run the installer as Administrator to avoid PATH update errors. If you're still
      getting a `command not found` error after installing Hasura, please restart Gitbash.


Step 2: Initialize a project
----------------------------

.. code-block:: none

  hasura init --directory my-project

Step 3: Run Hasura & Postgres
-----------------------------

.. code-block::  none

   cd my-project/install-scripts
   docker-compose up -d

Check if the containers are running:

.. code-block:: none

  $ docker ps

  CONTAINER ID IMAGE                 ... CREATED STATUS PORTS          ...
  097f58433a2b hasura/graphql-engine ... 1m ago  Up 1m  8080->8080/tcp ...
  b0b1aac0508d postgres              ... 1m ago  Up 1m  5432/tcp       ...

Step 4: Open the hasura console
-------------------------------

In the ``my-project/config.yaml`` file set the endpoint:

.. code-block:: yaml

  endpoint: http://localhost:8080

Now, open the hasura console:

.. code-block:: bash

  # Run this command in the my-project/ directory
  hasura console

Next: Make your first GraphQL query!
------------------------------------

Next, make your :doc:`first graphql query <../first-graphql-query>`.

Advanced:
---------

.. toctree::
   :titlesonly:

   Run Hasura with your postgres <docker-run>
   securing-graphql-endpoint
   import-database
