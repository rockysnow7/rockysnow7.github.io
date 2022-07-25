<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## An Idea for a Generally Intelligent Agent

---

### Definitions

- Let \\( \mathbb W \\) be the set of possible states of the world.
- Let \\( f : \mathbb W \rightarrow \mathbb R \\) be some function to be maximised.
- Let \\( \text{AE} : \mathbb W \rightarrow \mathbb R^n \\) be an autoencoder,
which returns a set of coordinates in an \\( n \\)-dimensional lantent space \\( L \\).

### Acting

1. Get input \\( w\_i \in \mathbb W \\) from the world.
2. Let \\( w\_e = \text{AE}(w\_i) \\).


```
def act():
    w_i = world state
    w_e = AE(e)
    p = cluster centre closest to w_e
    p_dist = distance between w_e and p

    if p_dist > self.topic_split_threshold:
        
```
