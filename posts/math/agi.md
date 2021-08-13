## A General Reinforcement Learning Agent

This is written more as code than math, as apparently GitHub doesn't support LaTeX.

---

Stockfish is
[one of](https://en.wikipedia.org/wiki/Top_Chess_Engine_Championship#Tournament_results_%28TCEC%29)
the best chess engines of all time. Magnus Carlsen is often said to be the best chess player of all time.  

If Carlsen were to play Stockfish at chess, Stockfish would win
[by a landslide](https://www.quora.com/Can-Magnus-Carlsen-draw-Stockfish). If they were to play draughts,
not only would Carlsen (probably) win, but Stockfish would not be able to understand the problem:
chess has fundamental features not shared by draughts. So to create an agent capable of playing both games,
we would need to find shared features; this process would be repeated with new games, finding more
fundamental shared features. Over time, fewer features constrain it, and eventually, with enough games
considered, the agent will be able to be trained to play any game considered in its development (and more!).  

So, what are the shared features of chess and draughts? At any time, the agent gets a view of the state of
the system and a set of legal moves, the playing of any of which changes the state of the system in some
way. This happens to the other agent, and is repeated until the state of the system follows some particular
pattern (this covers most turn-based games, not just chess and draughts).  


In Python:
```python
self.states_set.append(env.state)
self.eval_set.append(self.evaluate(env.state))

result = None
t = 0
while result == None:
	predicted_states = {move: self.predict(self.compress(env.state), move)) for move in env.legal_moves}
	best_move = max(predicted_states, key=self.evaluate(predicted_states[move]))
	env.do_move(best_move)

	self.states_set.append(env.state)
	self.moves_set.append(best_move)
	self.eval_set.append(self.evaluate(self.compress(env.state)))

	self.train_compressor()
	self.train_predictor()

	t += 1

for i in range(-1, -t-1, -1):
	self.eval_set[i] += result / t
self.train_evaluator()
```
