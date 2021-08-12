This is written more as code than math, as apparently GitHub doesn't support LaTeX.

---

Stockfish is
[one of](https://en.wikipedia.org/wiki/Top_Chess_Engine_Championship#Tournament_results_%28TCEC%29)
the best chess engines of all time. Magnus Carlsen is often said to be the best chess player of all time.
If Carlsen were to play Stockfish at chess, Stockfish would win
[by a landslide](https://www.quora.com/Can-Magnus-Carlsen-draw-Stockfish).


```
self.states_set.append(env.state)

result = none
while result == none
	predicted_states = {move: self.predict(self.compress(env.state), move)) for move in env.legal_moves}
	best_move = move with max self.evaluate(predicted_states[move])
	env.do_move(best_move)

	self.states_set.append(env.state)
	self.moves_set.append(best_move)
	self.eval_set.append(self.evaluate(self.compress(env.state)))

	self.train_compressor()
	self.train_predictor()

self.train_evaluator()
```
