Install
========


MultiCategory with Haskell backend
------------------------------------

You can download the whole demo with all the necessary demo data included from its release page `MultiCategory <https://github.com/valterUo/MultiCategory-demo-system/releases>`_. The version contains all necessary libraries and example data to run MultiCategory. Before running the demo, you need to have Stack tool installed: `Stack Tool for Haskell <https://docs.haskellstack.org/en/stable/README/>`_ and Java version 11 or higher. Stack needs to be in PATH. At the moment MultiCategory runs on Windows and Mac.

Install first Haskell part of the backend
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Install first the Haskell part of the program. Unzip file that you loaded from the release page of this Github repository and navigate to the folder called MultiCategory. This folder contains a source code for the Haskell part of the program. Start the Haskell program by calling stack:

.. code-block::

    stack ghci

First all the necessary packages are downloaded and after that the program is compiled. The first run takes some time especially if the stack tool has not been used before. If the execution fails, run the command again. When the execution is successfully finished, you should have REPL open in the console. You can now close the console.

Start the Java Spring server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Navigate to the folder which contains MultiCategory-backend-0.0.1-SNAPSHOT.jar file and execute the command

.. code-block:: bash

    java -jar MultiCategory-backend-0.0.1-SNAPSHOT.jar

This starts the server. You can open the page http://localhost:8080/. Now you see the graphical interface of MultiCategory and you can study the demo.


MultiCategory with Python backend
----------------------------------

The guide will be updated.