---
tags:
  - paper-reading
aliases:
  - Lud-project2
---
---
![[Pasted image 20250305220524.png]]
# Related work

1. Factorization-based embedding approaches
	1. Previous methods: train node embeddings for individual nodes --> expensive additional training
	2. Authors' methods: leverage feature information --> produce embeddings for unseen nodes
2. Supervised learning over graphs
	1. Previous: classify entire graphs
	2. This work: generating useful representations for individual nodes
3. Graph convolutional networks
	- viewed as an extension of the GCN framework

***

# Proposed method: GraphSage

## Key idea: learn how to aggregate feature information from a node's local neighborhood

1. Embedding generation algorithm
![[Pasted image 20250305191747.png]]
	1. at each iteration, or search depth, nodes aggregate information from their local neighbors, and as this process iterates, nodes incrementally gain more and more information from further reaches of the graph
	2. **Relation to the Weisfeiler-Lehman Isomorphism Test:** the connection between GraphSAGE and the classic WL test provides theoretical context for our algorithm design to learn the topological structure of node neighborhoods
	3.  **Neighborhood definition:** sample a fixed-size set of neighbors --> to keep the computational footprint of each batch fixed
2. Learning the parameters of GraphSage
3. Aggregator Architectures 
	1. **Mean aggregator**: a simple form of a "skip connection"
	2. **LSTM aggregator:** 
		advantage of larger expressive capability
		but arenot inherently symmetric
	3. **Pooling aggregator:** both symmetric and trainable

---
# Theoretical analysis

![[Pasted image 20250305214948.png]]

For any graph there exists a parameter setting for Algorithm 1 such that it can approximate clustering coefficients in that graph to an arbitrary precision, if the features for every node are distinct (and if the model is sufficiently high-dimensional)