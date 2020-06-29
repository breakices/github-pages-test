Haskell backend
=========================================

The Haskell backend is an independent part of the system and the user can use it from the console. You can start the program by navigating its folder ``MultiCategory`` and running the command ``stack ghci`` which starts the  (read evaluate print loop).


Packages and data stuctures
----------------------------

The backend uses the following packages to store different models. Some of the data structures are fairly simple and included in the base.

    - `Data.List <https://hackage.haskell.org/package/base-4.14.0.0/docs/Data-List.html>`_
    - `Data.IntMap.Strict <http://hackage.haskell.org/package/containers-0.6.2.1/docs/Data-IntMap-Strict.html>`_
    - `Data.HashMap.Strict <https://hackage.haskell.org/package/unordered-containers-0.2.11.0/docs/Data-HashMap-Strict.html>`_
    - `aeson <https://hackage.haskell.org/package/aeson>`_
    - `xeno <https://hackage.haskell.org/package/xeno>`_
    - `algebraic graphs <https://hackage.haskell.org/package/algebraic-graphs>`_
    - `rdf4 <https://hackage.haskell.org/package/rdf4h>`_
    -  NimpleGraph (our own graph data manipulation implementation)

Schema and instance categories
--------------------------------

The schema categories are implemented as modules that contain Haskell datatypes. These schema categories can be found from the folder 
`src<https://github.com/valterUo/MultiCategory-demo-system/tree/master/MultiCategory/src>`_ which contains folders named after the data sets. 
Each folder contains a file called `SchemaCategory.hs`. Each of these folders contain a file called `InstanceCategory.hs` which contains the objects that are mapped with collection constructor functors from the schema category. 
The morphisms are not implemented explicitly since we conceptually consider that all the Haskell functions (except the undefined) to be morphisms.

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

.. code-block:: haskell

    let t = 
    foldg  [] (\x -> if customerName x == "Alice" then [x]  else [] ) (\x y -> union x y ) (\x y -> union x y )  customers
    in
    foldg  Algebra.Graph.empty (\x -> if any ( \y -> knows x y customers ) t then Vertex x else Algebra.Graph.empty ) (\x y -> overlay x y ) (\x y -> connect x y )  customers

The user does not need to know the ``cons`` and ``nil`` functions for the colletions. The system can determine them based on the data sets and it knows how to use them in different combinations. 
The user is also allowed to input multiple lambda functions. If the user does not provide a lambda function, then the certain initial setting is used.

Unfortunately, the system cannot know how user wants to build richer structures from primitive structures. For example, if the user is querying a table to graph, they need to define explicitly 
how data is organized in the output graph. On the otherhand, if the user is querying graph to table, then it suffices to use ``cons`` and ``nil`` functions and multiple lambda functions.

The program contains more examples that can be executed.

.. toctree::
   :maxdepth: 2
   :caption: Contents: