Install
========


MultiCategory with Haskell backend
------------------------------------

You can download the whole demo with all the necessary demo data included from its release page `MultiCategory <https://github.com/valterUo/MultiCategory-demo-system/releases>`_. The version contains all necessary libraries and example data to run MultiCategory. Before running the demo, you need to have Stack tool installed: `Stack Tool for Haskell <https://docs.haskellstack.org/en/stable/README/>`_ and Java version 11 or higher. Stack needs to be in PATH. At the moment MultiCategory runs on Windows and Mac.


Install first Haskell part of the backend
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Install first the Haskell part of the program. Unzip the file that you loaded from the release page of this Github repository and navigate to the folder called MultiCategory. This folder contains source code for the Haskell part of the program. Start the Haskell program by calling stack:

.. code-block::

    stack ghci

First, all the necessary packages are downloaded and after that, the program is compiled. The first run takes some time especially if the stack tool has not been used before. If the execution fails, run the command again. When the execution is successfully finished, you should have REPL open in the console. You can now close the console.

Start the Java Spring server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Navigate to the folder which contains MultiCategory-backend-0.0.1-SNAPSHOT.jar file and execute the command

.. code-block:: bash

    java -jar MultiCategory-backend-0.0.1-SNAPSHOT.jar

This starts the server. You can open the page http://localhost:8080/. Now you see the graphical interface of MultiCategory and you can study the demo.


MultiCategory with Python backend
----------------------------------

MultiCategory has expanded to include polystore like properties such as data and query transformations from a relational database to a graph database. That leads to more complicated installation and configuration process which I have tried to make as simple as possible.

Install `Docker <https://www.docker.com/>`_.

Please go to `MultiCategory-backend-py <https://github.com/valterUo/MultiCategory-backend-py>`_ Github page and clone the repository. The installation scripts are located in the ``provisions`` directory.

On command line go to the ``provisions`` directory and run the script in the file ``setup_multicategory_docker.sh``:

.. code-block::

    bash ./setup_multicategory_docker.sh

If the installation succeeds, you should be able to see the frontend in the address http://localhost:8090/.

The script should start the following procedure:

    1. In the case that this is not the first installation, the ``cleanup_containers.sh`` script is executed and Docker initializes the containers
    2. The following images are pulled and installed from Docker hub:

        1. `Postgres <https://hub.docker.com/_/postgres>`_ (official image)
        2. `Neo4j <https://hub.docker.com/_/neo4j>`_ (official image)
        3. `MultiCategory <https://hub.docker.com/r/valteruo/multicategory>`_

    3. ``multicategory`` Docker network is created
    4. In the case of Postgres, ``ldbcsf1`` named database is created and the data (ldbc_flatfiles.tar.gz) from `MultiCategory flat files <https://github.com/valterUo/multicategory-flatfiles>`_ is downloaded
    5. The SQL in the directory ``provisions/postgres/ldbc`` is executed in the Postgres container which initializes ``ldbcsf1`` database. This database is used to demonstrate data and query transformations.
    6. For Neo4j database no data is included
    7. The script runs MultiCategory docker image and you should see the frontend in http://localhost:8090/

You can initialize Postgres database with any data you wish. In this case modify ``database_docker.ini`` file in ``external_databases/config`` folder. The file contains credentials that are required to connect to the relational database.

Note that although Postgres and Neo4j are running as Docker containers you can access them with standard methods, for example, using pgAdmin, browser or Docker's own command line. Just use the correct host and port.

After installation you can close the system from the Docker Desktop or running the script

.. code-block::

    bash ./stop_multicategory_docker.sh

In the future starting the demo system again, you can use the script

.. code-block::

    bash ./start_multicategory_docker.sh

If you run ``setup_multicategory_docker.sh`` again, this will initialize the system and, for example, some data can be lost.