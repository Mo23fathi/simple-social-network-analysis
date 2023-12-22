import networkx as nx
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt


# Step 1: Read the dataset and create a network graph
file_path = "Wiki-Vote.csv"

# Read only the necessary columns
df = pd.read_csv(file_path, usecols=['FromNodeId', 'ToNodeId'])

# Use a directed graph for better performance
G = nx.from_pandas_edgelist(df, 'FromNodeId', 'ToNodeId', create_using=nx.DiGraph())

# Step 2: Basic network analytics
average_clustering_coefficient = nx.average_clustering(G)
print("Average Clustering Coefficient:", average_clustering_coefficient)


# Step 3: Calculate centrality measures and eigenvectors
# Note: Centrality measures and eigenvectors can be resource-intensive for large graphs
# Consider skipping this step or using parallelization techniques for better performance
degree_centrality = nx.degree_centrality(G)
closeness_centrality = nx.closeness_centrality(G)
betweenness_centrality = nx.betweenness_centrality(G)
eigenvector_centrality = nx.eigenvector_centrality(G)

# Identify top nodes based on centrality measures
top_degree_nodes = sorted(degree_centrality, key=degree_centrality.get, reverse=True)[:5]
top_closeness_nodes = sorted(closeness_centrality, key=closeness_centrality.get, reverse=True)[:5]
top_betweenness_nodes = sorted(betweenness_centrality, key=betweenness_centrality.get, reverse=True)[:5]
top_eigenvector_nodes = sorted(eigenvector_centrality, key=eigenvector_centrality.get, reverse=True)[:5]

# Print insights
print("\nTop Nodes based on Degree Centrality:")
for rank, node in enumerate(top_degree_nodes, 1):
    print(f"Top {rank}: Node {node} - Degree Centrality: {degree_centrality[node]}")

print("\nTop Nodes based on Closeness Centrality:")
for rank, node in enumerate(top_closeness_nodes, 1):
    print(f"Top {rank}: Node {node} - Closeness Centrality: {closeness_centrality[node]}")

print("\nTop Nodes based on Betweenness Centrality:")
for rank, node in enumerate(top_betweenness_nodes, 1):
    print(f"Top {rank}: Node {node} - Betweenness Centrality: {betweenness_centrality[node]}")

print("\nTop Nodes based on Eigenvector Centrality:")
for rank, node in enumerate(top_eigenvector_nodes, 1):
    print(f"Top {rank}: Node {node} - Eigenvector Centrality: {eigenvector_centrality[node]}")

# Step 4: Community detection using Louvain method
communities = nx.algorithms.community.asyn_lpa_communities(G, seed=42)
communities = [list(community) for community in communities]
print("Communities:")
for community_id, community in enumerate(communities, 1):
    print(f"Community {community_id}:")
    print(" ".join(map(str, community)))
    print("-" * 20)  # Add a separator between communities

# Additional details concluded from community detection
num_communities = len(communities)
average_community_size = np.mean([len(community) for community in communities])

print("\nDetails Concluded from Community Detection:")
print(f"Number of Communities: {num_communities}")
print(f"Average Community Size: {average_community_size}")

# Step 5: Subset of Nodes Visualization
subset_nodes = list(G.nodes())[:1000]
subgraph = G.subgraph(subset_nodes)
pos = nx.spring_layout(subgraph, seed=42)

plt.figure(figsize=(12, 12))
nx.draw(subgraph, pos, with_labels=False, node_size=5, node_color="skyblue", edge_color="gray", alpha=0.7)
plt.title("Subset of Nodes Visualization from Wiki-Vote Dataset")
plt.show()
