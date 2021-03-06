Updating Hasura GraphQL engine on Heroku
========================================

This guide will help you update Hasura GraphQL engine running on Heroku. This guide assumes that you already have
Hasura GraphQL engine running on Heroku.

The current latest version is:

.. raw:: html

   <code>hasura/graphql-engine:<span class="latest-release-tag">latest</span></code>

Follow these steps to update Hasura GraphQL engine to the lastest version:

1) Clone the Hasura GraphQL engine Heroku app
---------------------------------------------

The Hasura app with Heroku buildpack/configuration is available at:
https://github.com/hasura/graphql-engine-heroku

.. code-block:: none

   $ git clone hasura/graphql-engine-heroku

If you already have this, then pull the latest changes (which will have the updated GraphQL engine docker image).

.. code-block:: bash

   # origin is https://github.com/hasura/graphql-engine-heroku
   $ git pull origin master

2) Attach your Heroku app
-------------------------

Let's say your Heroku app is called ``hasura-heroku`` and is on ``https://hasura-heroku.herokuapp.com``.
Configure the git repo you cloned in step 1, to be able to push to this app.

.. code-block:: bash

   # Replace hasura-heroku with your Heroku app's name
   $ heroku git:remote -a hasura-heroku

3) Git push to deploy the latest Hasura GraphQL engine
------------------------------------------------------

When you ``git push`` to deploy, the Heroku app will get updated with the latest changes:

.. code-block:: bash

   $ git push heroku master

Deploy a specific version of Hasura GraphQL engine
--------------------------------------------------

Head to the ``Dockerfile`` in the git repo you cloned in step 1.
Change the ``FROM`` line to the specific version you want. A list of all releases can be found
at https://github.com/hasura/graphql-engine/releases

.. code-block:: Dockerfile
   :emphasize-lines: 1

   FROM hasura/graphql-engine:v1.0.0-alpha01

   ...
   ...

Change ``v1.0.0-alpha01`` to ``v1.0.0-alpha02`` for example, and then ``git push heroku master`` to deploy.
