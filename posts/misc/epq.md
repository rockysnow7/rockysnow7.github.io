<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## Measuring the Effect of Pruning Algorithms on the Performance of a Chess Engine

---

[video]

### Intro

Chess is a turn-based strategy board game for two players, taking place on a
grid. On a player's turn, they move one piece according to the rules of how that
piece can move - for example, the turret-shaped *rook* can move in straight
horizontal or vertical lines of any length, while the *king* can move one square
in any direction. However, knowledge of the specific rules of the game are not
necessary for understanding this project, and so I will not go through them all
here: just know that on each turn there are many possible moves the player can
make, and their ultimate goal is to trap their opponent's king, winning the
game. If there reaches a point in the game where it will be impossible for
either player to win, then the game ends as a draw.

In the early 20th century, people began creating machines that could play
chess, in some instances[^1] better than humans. These have improved in design
over time, and now chess engines (computers that play and analyse chess games)
are consistently far better than humans. One issue faced by all modern chess
engines is the amount of time it takes the engine to decide which move to make.
Various attempts have been made to speed this process up, and in this project
we will compare the effects of two of the most popular methods.

The next section provides an outline of how a basic chess engine works and what
can be done to speed them up.

### The Structure of a Chess Engine

There are two main components of a chess engine, namely the *evaluation
function* and the *minimax algorithm*[^2] (both explained below). An engine is
just a program that runs the minimax algorithm with the evaluation function and
plays the resulting move.

An evaluation function is just a mathematical formula that takes in a chess
position and outputs a number representing which player is winning. \\( 0 \\)
indicates an equal position, while a positive number means white is winning,
and a negative number means black is winning. So, for example, if a position is
evaluated as \\( +1.2 \\) then the engine believes white is winning (by a good
amount).

### The Pruning Algorithms

### Measuring Their Effects

### Programming Diary

### Results

### Conclusions

### What I Learned

### Bibliography and Further Reading

[^1]: El Ajedrecista was an automaton capable of playing three-piece endgames perfectly: [https://en.wikipedia.org/wiki/El_Ajedrecista](https://en.wikipedia.org/wiki/El_Ajedrecista).
[^2]: An *algorithm* is just a set of instructions which, when completed, gives some result. For example, a cake recipe could be considered an algorithm for making cake.
