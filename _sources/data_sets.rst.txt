Data sets
===========

MultiCategory comes with six different multi-model data sets: simple e-commerce data set, Patent, Film, University, Person, and Unibench data set.

If you download the Haskell version of MultiCategory, you will download all the data sets simultaneously. Notice that the data sets have been modified and cleaned certain ways
because Haskell is very strict that data follows the lines that typing sets for it. We have also made data sets smaller because originally the idea was not to create a big data platform.

On the other hand, the Python version does not come with most of the data. Python version is developed to support bigger data sets and this means that all the data sets can be uploaded into the demo system as they are presented. You can read more about installing the data sets from the `Install <install.html>`_ tab.


Simple E-commerce data sets
----------------------------

This data set is a very small e-commerce data set. It contains 

- a property graph of customer --knows--> customer, 
- a table of locations and 
- an XML document of Orders and Products. 

The data set suffices for demonstrating category theoretical ideas but more comprehensive and real-life motivated data sets are implemented or are under implementation.


Data sets from Helsinki multi-model data repository
---------------------------------------------------

You can find schemas and detailed descriptions in Helsinki multi-model data repository :cite:`UDMS_dataset`.


Unibench
---------

Unibench :cite:`10.1007/978-3-030-11404-6_2` is a benchmark for multi-model databases. It comes along a data set that has been slightly scaled for this demo.


Online Market Place (under development)
----------------------------------------

This data set is an expanded version of the simple E-commerce data set. It consists of an online market place such as Amazon, eBay, or Alibaba. This online market place collects different sellers together which requires novel techniques to combine
different data models together. Currently, this demo data set has three third-party sellers which are using relational, JSON, and XML models and formats to store their product and invoice information. The online market place implements a multi-model database
based on category theory which demonstrates how multi-model query processing and multi-model joins can be applied in this demonstration scenario.

The online market place demonstration scenario includes:

- property graph of customer -- friends with --> customer (Facebook friendship graph from :cite:`snapnets`)
- RDF graphs of capitals and countries in separate graphs (`Telegraphis <http://telegraphis.net/data/>`_)
- Each third-party seller has information on their products and invoices stored either in relational tables, JSON objects, or XML trees. Contents of the data for each third-party sellers vary. (Amazon product metadata from :cite:`snapnets`)

.. toctree::
   :maxdepth: 2
   :caption: Contents: