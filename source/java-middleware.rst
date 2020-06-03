Java Middleware
=================

We have developed a Java program between the JavaScript frontend and Haskell backend. Since there is no known method to integrate JavaScript and Haskell the way that the system requires, we developed this program. It uses Java Spring framework. 
It is responsible of various tasks:

- the program starts the frontend and the backend,
- it translates our multi-model query language into Haskell fold-functions,
- it sends translated queries to the Haskell backend and parses the results,
- it stores queries and results for possible later use.