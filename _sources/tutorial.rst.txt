Tutorial
=========================================

MultiCategory is relatively simple to use thanks to the web interface. On the right side of the main view of the web interface, you can find the implemented data sets.


View schema and instance categories
------------------------------------

For the selected data set you can click the buttons ''Schema category'' and ''Instance category'' to open the wanted category. The categories are drawn as D3js graphs. 


Executing queries
------------------

Click the ''Examples'' button that opens a collection of dropdown menus. Behind the dropdown menus, you will find various multi-model query examples. Choose an example that opens it in the input editor. You can modify the query if you wish and then execute
it by clicking the play button. Depending on the query the result should appear below the input field. The ''Result'' button toggles the result.

In some property graphs nodes contain lots of information. If you want to view this information, you can click ''Contents of a node'' that opens a field. If you now move the mouse over the nodes
you can study data inside the nodes. This applies to all the graphs.

Categorical view of query and fold-function
---------------------------------------------

After executing a query, you can click ''Categorical view of query'' that examines the query and draws it as a graph. This graph is a visualization of the sequence of the fold-functions. You can click the nodes that are related to the main fold-function (the largest nodes in the graph). After clicking these nodes, a new graph is drawn. This graph is a visualization of the inner structure of the clicked fold-function. If you want to view the corresponding fold-function, you
can click the ''Fold-function'' button. You can also copy this function and execute it in the Haskell program that runs, for instance, in REPL.


Query processing example
-------------------------

For example: ::

    LET t BE 
    QUERY (\x -> if customerName x == "Alice" then cons x else nil) 
    FROM customers
    TO relational 
    IN
    QUERY (\x -> if any (\y -> knows x y customers) t then cons x else nil)
    FROM customers
    TO algebraic graph

becomes a sequence of folds: 

.. code-block:: Haskell

    let t = 
    foldg  [] (\x -> if customerName x == "Alice" then [x]  else [] ) (\x y -> union x y ) (\x y -> union x y )  customers
    in
    foldg  Algebra.Graph.empty (\x -> if any ( \y -> knows x y customers ) t then Vertex x else Algebra.Graph.empty ) (\x y -> overlay x y ) (\x y -> connect x y )  customers

The user does not need to know the ``cons`` and ``nil`` functions for the collections. The system can determine them based on the data sets and it knows how to use them in different combinations. 
The user is also allowed to input multiple lambda functions. If the user does not provide a lambda function, then a certain initial setting is used.

Unfortunately, the system cannot know how the user wants to build richer structures from primitive structures. For example, if the user is querying a table to the graph, they need to define explicitly how data is organized in the output graph. On the other hand, if the user is querying graph to the table, then it suffices to use ``cons`` and ``nil`` functions and multiple lambda functions.

The program contains more examples that can be executed.