<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## Measuring the Effect of Pruning Algorithms on the Performance of a Chess Engine

---

<!-- VIDEO -->

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
function* and the *minimax search* (both explained below). An engine is
just a program that runs the minimax search with the evaluation function and
plays the resulting move.

An evaluation function is just a mathematical formula that takes in a chess
position and outputs a number representing which player it thinks is winning.
0 indicates an equal position, while a positive number means white is
winning, and a negative number means black is winning. So, for example, if a
position is evaluated as +1.2 then the engine believes white is winning
(by a good amount). This function gets better at guessing who is winning over
time by playing many thousands of games and observing their results. This need
for the engine to train is where the issue of speed comes up, but we will
explore this further in a later section.

The minimax search is the process by which the engine decides the best move
given a position. It does this by playing each possible move in the current
position, and then each possible move in each resulting position, and then each
possible move in the positions resulting from those, and so on, looking a
certain number of moves ahead. It then evaluates each position with the
evaluation function and chooses the move that will lead to the best position
long-term, assuming both it and its opponent play the best moves it can find
for them. This also contributes to the amount of time taken to find the best
move: the number of positions that must be evaluated in order to choose a move
increases exponentially as we increase the search depth - that is, the number
of moves ahead the engine plans. There are, on average, about 30 moves
that can be made in any position. So, looking 4 moves ahead, this means
the engine has to evaluate about 810,000 positions to find the best
move. It takes time to run the evaluation function, and so in evaluating
810,000 positions this time adds up.

<!-- SEARCH TREE DIAGRAM -->

Given that there are two parts to an engine, there are two ways we can try to
speed the engine up. The evaluation function is really just a lot of
multiplication and addition, both of which are already extremely fast on
computers. So, we will look at speeding up the minimax search. This requires
limiting the number of positions the engine evaluates, a process known as
*pruning*[^2]. The specific pruning algorithms[^3] we will use are discussed in
the next section.

### The Pruning Algorithms

### Measuring Their Effects

### Programming Diary

### Results

### Conclusions

### What I Learned

### Bibliography and Further Reading

[^1]: El Ajedrecista was an automaton capable of playing three-piece endgames perfectly: [https://en.wikipedia.org/wiki/El_Ajedrecista](https://en.wikipedia.org/wiki/El_Ajedrecista).
[^2]: The minimax search builds a *search tree*, and so to remove positions we must *prune* the tree.
[^3]: An algorithm is just a set of instructions which, when completed, gives some result. For example, a cake recipe is an algorithm for making cake.
