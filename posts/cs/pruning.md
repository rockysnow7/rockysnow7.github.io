<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## Measuring the Effect of Pruning Algorithms on the Evaluation Speed and Rating of a Chess Engine

---

Contents:

- Video of play
- Intro
    - Description of the game of chess (3 paragraphs)
    - Description of the basic engine without pruning (3 paragraphs)
    - Definition of a pruning algorithm (1 paragraph)
- Description of how each pruning algorithm works
    - Alpha-beta pruning
    - ...
- Description of how results were measured
    - Formula for scoring engines (Weissman score,
\\( S = \frac{\displaystyle R}{\displaystyle \bar R} \frac{\displaystyle \bar T}{\displaystyle T} \\)).
    - Details of algorithm
    - Time spent training, measuring
- Programming Diary
    - Design
    - Problems
    - How I overcame them
    - How the design changed over time
    - Code snippets
- Results
    - Move time with each algorithm
    - Rating with each algorithm
    - Score with each algorithm
    - And all of the above without any pruning algorithms
- Conclusions
    - Best pruning algorithm for win rate
    - Best pruning algorithm for move time
    - Best pruning algorithm for general score
    - Finally, are pruning algorthms worth using?
- How I improved
    - What I was bad at when I started
    - Examples of how I have improved in these areas
- Bibliography/further reading
