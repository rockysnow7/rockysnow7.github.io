## An Idea for a Generally-Intelligent Reinforcement Learning Agent

> "The intelligence of a system is a measure of its skill-acquisition efficiency over a scope of tasks with
respect to priors, experience, and generalization difficulty." - F. Chollet, *On the Measure of Intelligence*

By this definition (which we will be using throughout this post), an intelligent agent must be able to learn
to manipulate various unrelated systems to achieve some goal, and to transfer its abilities from one system
to another, with as little training data as possible. To manage its knowledge of these systems, the agent
must have a controlling part, known hereafter as the *supervisor*. The parts controlled by the supervisor will
be called *system agents*.  

From this, we can approximate an architecture:

![Basic architecture](../images/math/agi/agi-1.svg)

In order for the system agents to learn, they must be given data from the environment. They will then pass on
what they believe to be the best move to the supervisor, which will act on it. The best move will always be
found by a tree search, with the system agent evaluating all positions; the next position will be predicted by
the system agent given the current one and a move.  

So, the architecture of a single system agent is:

![System agent architecture](../images/math/agi/agi-2.svg)

Specifically, a system will be defined as a cluster of points in the latent space of an autoencoder trained on
states previously observed by the supervisor. So if the encoded form of an input is placed in cluster \\\(n\\\),
it will be passed to system agent \\\(n\\\) for analysis. If a new cluster is made, the system agent for the
nearest cluster is duplicated and assigned the new cluster.
