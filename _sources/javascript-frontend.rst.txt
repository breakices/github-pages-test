Javascript frontend
=========================================

The frontend of MultiCategory is the same for both Haskell and Python versions and it is responsible for the following properties: 

- providing the interface to input multi-model queries, 
- upload data (will be included to the Python version) and 
- visualizing data:
    
    - results to queries
    - category theoretical constructions (instance and schema categories)
    - multi-model query processing

The frontend is created with React :cite:`React` and data visualizations are implemented with D3js :cite:`bostock2011d3`.

The frontend is able to visualize different kinds of tables, graphs, and hierarchical structures although there are certain limitations regarding the size of the data. 
The frontend is a rather supportive tool and not a real project to study data visualization.