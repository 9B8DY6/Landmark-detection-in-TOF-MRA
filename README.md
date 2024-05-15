# Landmark-detection-in-TOF-MRA
The basic step for quantitative analysis of brain artery.

## MRA ?
<img src="https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/assets/67573223/c48866f1-f6a5-4936-a9eb-06c12c1eab50" width=140, height=160>

MRA is an abbreviation of Magnetic Resonance Angiography to image blood vessels, especially in brain. 
The main part of brain artery is called as COW (Circle of Willis). 
It is used to evaluate them for stenosis (abnormal narrowing), occlusions, aneurysms (vessel wall dilatations, at risk of rupture) or other abnormalities in COW. 

From [wiki](https://en.wikipedia.org/wiki/Magnetic_resonance_angiography)

## Purpose
To evalute COW quantitatively, we have to <ins>detect landmarks which cover COW</ins> in advance.  
![image](https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/assets/67573223/03e903db-de13-4ad4-a7d7-2e5023d3e1a6)

💥**I dot landmarks on brain artery by myself** so I can not open landmarks data.

1️⃣ The first try is method using [CNN to regress landmark positions](https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/blob/main/mip_axial_for_CNN.ipynb).

2️⃣ The second try is method using [GNN (Graph Neural Network)](https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/blob/main/GNN_implementation.ipynb).

<img src="https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/assets/67573223/7af41979-6ee9-49c1-9816-c048abea05d6" width=300, height=180>

 - (reference : [Structured Landmark Detection via Topology-Adapting Deep Graph Learning](https://arxiv.org/abs/2004.08190))
 - What is Graph?

   Graph data refers to data that is structured as a graph, which consists of nodes (or vertices) and edges (or links) that connect these nodes. In a graph, nodes represent entities or objects, while edges represent the relationships or connections between these entities.

   A graph $G$ is formally defined as an ordered pair $(V,E)$. $V$ is a set of vertices(or nodes). $E$ is a set of edges, each of which is a pair of vertices.
   The graph is represented by adjacency matrix which shows graph connectivity. It's a square matrix where the rows and columns correspond to vertices, and the presence or absence of an entry in the matrix indicates whether there's an edge between the corresponding vertices.
   
   ![image](https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/assets/67573223/e532fcaa-5bed-443f-aff0-dd9d034d1c7a)

 - Graph Convolution

   Given a learnable graph connectivity $E$ and a graph feature $F$, the $k$-th graph convolution operation updates the $i$-th node feature $f^j_k$ by aggregating all node features weighted by connectivity:

   $$f^i_{k+1}=W_1f^i_k + \sum_j e_{ij}W_2 f^j_k$$
   where $W_1, W_2$ are learnable weight matrices. The graph convolutions can be seen as the mechanism of information collection among neighborhoods. The connectivity $E$ serves as pathways for information flow from one landmark to another.
   
 - Motivation : If we consider landmarks as node and vessels as edge, cerebral vasculature is one big graph of which nodes on vessels are only connected to other nodes along with vessel. Then, a model learns correlation between landmarks with MRA image feature which shows that cerebral vessel is big one graph.
   
 - Result
   
   <img src="https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/assets/67573223/3bc67462-0be0-4815-8beb-69d1c459c17d" width=400, height=200>

   The red dots are ground-truth and the green ones are predicted landmarks.


The relationship between nodes is crucial in second method so, the more landmarks, the more precise it would be. When I wrote this code, there is no github of reference. I did it only based on paper. 
