Java Middleware
=================

We have developed a Java program between the JavaScript frontend and Haskell backend. Since there is no known method to integrate JavaScript and Haskell the way that the system requires, we developed this program. It uses Java Spring framework. 
It is responsible of various tasks:

- the program starts the frontend and the backend,
- it translates our multi-model query language into Haskell fold-functions,
- it sends translated queries to the Haskell backend and parses the results,
- it stores queries and results for possible later use.

The program contains a small `JSONDB <http://jsondb.io/>`_ database that stores queries, parsed queries and certain results. The Java program connects to Haskell backend using `ProcessBuilder <https://docs.oracle.com/javase/7/docs/api/java/lang/ProcessBuilder.html>`_.


Query tokenizing, parsing and translating
------------------------------------------

Each selective query becomes and instance of a class called `SelectiveQuery <https://github.com/valterUo/MultiCategory-demo-system/blob/master/src/query/SelectiveQuery.java>`_. 
When SelectiveQuery object is created, the input query string is automatically tokenized, parsed and translated so that user can output the corresponding Haskell code i.e. the sequence of fold functions. 
Each SelectiveQuery consists of one or multiple `QueryBlocks <https://github.com/valterUo/MultiCategory-demo-system/blob/master/src/query/QueryBlock.java>`_ which have one or multiple 
`LambdaFunctions <https://github.com/valterUo/MultiCategory-demo-system/blob/master/src/query/LambdaFunction.java>`_.

This structure of classes creates a simple parse tree of the query and it can be efficiently used to modify and understand the query. Certain keywords (``cons``, ``nil`` which are related to :cite:`Grust2004` and :cite:`Grust1999Compr-709`) are 
modified with respect to the target model of the query and the correct fold function is used with respect to the target model of the query. 
The `CodeGenerator <https://github.com/valterUo/MultiCategory-demo-system/blob/master/src/codeGenerator/CodeGenerator.java>`_ class is partly responsible of this.