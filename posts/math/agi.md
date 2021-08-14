## A General Reinforcement Learning Agent

This is written more as code than math, as apparently GitHub doesn't support LaTeX (smh).

---

Stockfish is
[one of](https://en.wikipedia.org/wiki/Top_Chess_Engine_Championship#Tournament_results_%28TCEC%29)
the best chess engines of all time. Magnus Carlsen is often said to be the best chess player of all time.  

If Carlsen were to play Stockfish at chess, Stockfish would win
[by a landslide](https://www.quora.com/Can-Magnus-Carlsen-draw-Stockfish). If they were to play draughts,
not only would Carlsen win, but Stockfish would not be able to understand the problem: chess has
fundamental features not shared by draughts. So to create an agent capable of playing both games, we would
need to find shared features; this process would be repeated with new games, finding more fundamental
shared features. Over time, fewer features constrain it, and eventually, with enough games considered, the
agent will be able to be trained to play any game considered in its development (and more!).  

So, what are the shared features of chess and draughts? At any time, the agent gets a view of the state of
the system and a set of legal moves, the playing of any of which changes the state of the system in some
way. This happens to the other agent, and is repeated until the state of the system follows some particular
pattern, at which point either one of the players has won or the result is a draw (this covers most
turn-based games, not just chess and draughts).  

To allow the agent to understand the system despite these vague expectations, it must have 3 particular
functions:
- A *compressor* that takes a system state and returns a smaller representation of it. This forces the
agent to focus on the key features of the system.
- A *predictor* that takes a compressed system state and a move and returns a compressed prediction of the
state after the move has been played.
- An *evaluator* that takes a compressed system state and returns a real number between -1 and 1, with -1
meaning the opponent will win, 0 meaning the state is neutral, and 1 meaning it will win.  

With these functions, the agent can perform the following algorithm each time it plays a given game:
1. Save the current system state and the agent's evaluation of it.
2. Move to maximise the agent's evalutation of the predicted next state.
3. Save the current system state, the move played, and the agent's evaluation of the current system state.
4. Train the agent's compressor and predictor from the saved states and moves.
5. While the game is still being played, repeat steps 2-5.
6. Given a result between -1 and 1, add the result divided by the number of moves played in the past game
to the saved evaluations of states from the past game.  

The saved data is kept between games. This algorithm can be repeated to increase the accuracy of the
compressor, predictor, and evaluator, therefore increasing the agent's chance of winning the game.  

The following is an example implementation in Python3:
```python
self.states_set.append([])
self.moves_set.append([])
self.eval_set.append([])

self.states_set[-1].append(env.state)
self.eval_set[-1].append(self.evaluate(env.state))

result = None
while result == None:
	predicted_states = {move: self.predict(self.compress(env.state), move) for move in env.legal_moves()}
	best_move = max(predicted_states, key=self.evaluate(predicted_states[move]))
	env.do_move(best_move)

	self.states_set[-1].append(env.state)
	self.moves_set[-1].append(best_move)
	self.eval_set[-1].append(self.evaluate(self.compress(env.state)))

	self.train_compressor()
	self.train_predictor()

for i in range(len(self.eval_set[-1])):
	self.eval_set[-1][i] += result / len(self.eval_set[-1])
self.train_evaluator()
```

Note that it separates data from different games to avoid implying that the last move of one game leads to
the first state of the next. The definition and training of the compressor, predictor, and evaluator are
omitted, but all are neural networks, with the compressor being an autoencoder, and are trained on
`states_set`, `states_set` and `moves_set`, and `states_set` and `eval_set` respectively.
