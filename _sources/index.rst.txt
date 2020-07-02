.. MultiCategory documentation master file, created by
   sphinx-quickstart on Wed Jun  3 13:38:39 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to MultiCategory's documentation!
=========================================

MultiCategory is a prototype system that demonstrates how applied category theory could be used to model multi-model databases and multi-model query processing. Note that the system is mainly meant for demonstration purposes.

Multi-model databases are databases whose single backend supports multiple data models. Category theory is a sort of mathematics 

MultiCategory can be divided into two different versions depending on the programming language used in the backend. The first version is written with functional programming language `Haskell <https://www.haskell.org/>`_. 
The later version, which is currently under development, is written with Python.

Haskell version
-----------------

The Haskell version is mainly written so that it supports selective multi-model queries that are executed over multi-model data. The data models, that MultiCategory supports, are

- relational,
- hierarchical such as XML and JSON,
- key-value documents,
- property graphs and
- RDF graphs. 

The Haskell version of MultiCategory provides:

- category theoretical construction to model data storing and query processing in the conceptual level
- selective multi-model queries based on fold-functions

Python version (under development and not released or published or submitted)
-------------------------------------------------------------------------------

The Python version of MultiCategory is developed so that it will support multi-model joins. Also, the theoretical background differs between the versions.

The Python version of MultiCategory will provide:

- updates to data defined with category theory
- multi-model joins defined with category theory
- machine learning-driven optimization for query processing
- certain updates compared to Haskell version

Audience
--------

The audience for MultiCategory includes database scientists, the functional programming community, category theorists, and anyone interested in constructing fundamentally different database systems. 
Please see the bibliography for interesting resources related to multi-model databases, category theory, and related systems.

History
------------

MultiCategory is strongly inspired by Spivak's work :cite:`DBLP:journals/corr/abs-1009-1166`, :cite:`conf/lfcs/ForssellGS16`, 
:cite:`spivak2014category`, and :cite:`10.1007/978-3-319-72044-9_5`. One of the earliest motivations to use applied category theory to model database was presented in :cite:`Diskin1996FI`.
MultiCategory had originally `SML <https://smlfamily.github.io/>`_ backend which was difficult to use efficiently. We switched to Haskell but followed similar principles as we had with the SML version.

.. toctree::
   :maxdepth: 3
   :caption: Contents:

   install
   tutorial
   data_sets
   reference
   theoretical_background
   license
   citing
   bibliography


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`