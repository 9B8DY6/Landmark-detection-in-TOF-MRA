# Landmark-detection-in-TOF-MRA
The basic step for quantitative analysis of brain artery.

## MRA ?
<img src="https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/assets/67573223/c48866f1-f6a5-4936-a9eb-06c12c1eab50" width=140, height=160>

MRA is an abbreviation of Magnetic Resonance Angiography to image blood vessels, especially in brain. 
It is used to evaluate them for stenosis (abnormal narrowing), occlusions, aneurysms (vessel wall dilatations, at risk of rupture) or other abnormalities. 
The main part of brain artery is called as COW (Circle of Willis). 

From [wiki](https://en.wikipedia.org/wiki/Magnetic_resonance_angiography)

## Purpose
To evalute COW quantitatively, we have to <ins>detect landmarks which cover COW and needs quantitative analysis like how much narrow the vessel is</ins>.  
![image](https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/assets/67573223/03e903db-de13-4ad4-a7d7-2e5023d3e1a6)

💥**I dot landmarks on brain artery by myself** so I can not open landmarks data.

1️⃣ The first try is method using [CNN to regress landmark positions](https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/blob/main/mip_axial_for_CNN.ipynb).

2️⃣ The second try is method using [GNN (Graph Neural Network)](https://github.com/9B8DY6/Landmark-detection-in-TOF-MRA/blob/main/GNN_implementation.ipynb).
 - (reference : [Structured Landmark Detection via Topology-Adapting Deep Graph Learning](https://arxiv.org/abs/2004.08190))
 - Motivation : If we consider landmarks as node and vessels as edge, cerebral vasculature is one big graph of which nodes on vessels are only connected to other nodes along with vessel. Then, a model learns correlation between landmarks with MRA image feature which shows that cerebral vessel is big one graph. 
 - When I wrote this code, there is no github of reference. I did it only based on paper. 

The relationship between nodes is crucial in second method so, the more landmarks, the more precise it would be. 
