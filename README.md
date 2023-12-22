Network Analysis with Wiki-Vote Dataset
This Python script utilizes the NetworkX library to perform basic network analytics on the Wiki-Vote dataset. The dataset represents a directed graph of Wikipedia voting. The script provides insights into the structure and characteristics of the network, including clustering coefficient, centrality measures, eigenvectors, and community detection.

Prerequisites
Ensure you have the following libraries installed:

networkx
pandas
numpy
matplotlib

Steps and Insights
Step 1: Read the dataset and create a network graph
The script reads the dataset and constructs a directed graph using NetworkX.

Step 2: Basic network analytics
Calculates the average clustering coefficient of the graph.

Step 3: Calculate centrality measures and eigenvectors
Calculates degree centrality, closeness centrality, betweenness centrality, and eigenvector centrality. Identifies top nodes based on these measures.

Step 4: Community detection using Louvain method
Applies the Louvain method to detect communities within the network and prints the nodes in each community.

Step 5: Subset of Nodes Visualization
Visualizes a subset of nodes (first 1000 nodes) using a spring layout and displays the graph.
