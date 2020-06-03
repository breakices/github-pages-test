.. MultiCategory documentation master file, created by
   sphinx-quickstart on Wed Jun  3 13:38:39 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to MultiCategory's documentation!
=========================================

MultiCategory is a prototype system that demonstrates how applied category theory could be used to model multi-model databases and multi-model query processing.

Multi-model databases are built so that their single backend supports multiple data models. 

MultiCategory can be devided into two different versions depending the programming language used in the backend. The first version is written with functional programming language `Haskell <https://www.haskell.org/>`_. 
The later version, which is currently under development, is written with Python.

The Haskell version is mainly written so that it supports selective multi-model queries that are executed over multi-model data. The data models, that MultiCategory supports, are

- relational,
- hierarchical such as XML and JSON,
- key-value documents,
- property graphs and
- RDF graphs.

The Python version of MultiCategory is developed so that it will support multi-model joins. Also, the theoretical background differs between the versions. 
In our work we consider multi-model databases using category theory and many concepts from database design are translated into category theory. 
This way we obtain unified and consistent theory between different data models.

.. toctree::
   :maxdepth: 3
   :caption: Contents:

   install
   tutorial
   reference
   theoretical_background
   license
   bibliography



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
