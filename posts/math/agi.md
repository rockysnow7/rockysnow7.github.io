<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## An Idea for a Generally Intelligent Agent

---

### structure

- *CU*: the control unit, which contains the agent's utility function, and its history
of observations.
- *World AE*: an autoencoder which encodes a given observation into a latent space.
Trained on the set of past observations.
- *Topic AEs*: a set of autoencoders which encode a subset of the latent space of the
world AE. Each one is stored with the centre coordinates of the corresponding cluster.
- *Subtopic AEs*: a set of autoencoders which encode a subset of the latent space of the
topic AEs. Each one is stored along with the centre coordinates of the corresponding
cluster.
- *Sub-subtopic AEs*: ....
- *Predictor*: predicts the state of the world at the next time step, encoded by the
most recent AE. This is passed back up the chain of AEs to the CU.

### acting

Let \\( \text{AE}\_{i,j,k,...} : \mathbb R^{I_{i,j,k,...}} \rightarrow \mathbb
R^{O_{i,j,k,...}} \\) be the autoencoder associated with the cluster centre \\( i \\),
sub-cluster centre \\( j \\), sub-sub-cluster centre \\( k \\), etc., where
\\( i \in \mathbb R^{I_i}, j \in \mathbb R^{I_{i,j}}, k \in \mathbb
R^{I_{i,j,k}},... \\).
Let \\( \text{AE}_0 \\) be the world AE.

Given an observation \\( o \\), the agent chooses an action \\( a \\) by:

1. Let \\( z_0 = \text{AE}_0(o) \\).
2. 
