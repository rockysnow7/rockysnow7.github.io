## An Idea for a Generally Intelligent Agent

---

### intro

At each time step, the agent receives an observation of the environment.
It must then choose an action to maximise its utility function.

### structure

- *CU*: the control unit, which contains the agent's utility function, and its history of observations.
- *World AE*: an autoencoder which encodes a given observation into a latent space. Trained on the set of past observations.
- *Topic AEs*: a set of autoencoders which encode a subset of the latent space of the world AE. Each one is stored with the centre coordinates of the corresponding cluster.
- *Subtopic AEs*: a set of autoencoders which encode a subset of the latent space of the topic AEs. Each one is stored along with the centre coordinates of the corresponding cluster.
- *Sub-subtopic AEs*: ....
- *Predictor*: predicts the state of the world at the next time step, encoded by the most recent AE. This is passed back up the chain of AEs to the CU.

### acting

Given an observation \\( o \\), the agent chooses an action \\( a \\) by:

1. Let \\( \mathbf{AE}_0(o) \\) be the encoded form of \\( o \\) by the world AE.