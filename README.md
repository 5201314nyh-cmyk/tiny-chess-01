# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/5201314nyh-cmyk/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/5201314nyh-cmyk/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB Python chess engine: 0x88 board, alpha-beta with transposition table, quiescence and iterative deepening, built by an AI agent for make.fun's tiny-chess-01 bounty.

## How it plays

- 0x88 board representation.
- Pinned-piece fast path in move generation.
- Negamax alpha-beta search.
- Transposition table, Zobrist hash.
- Iterative deepening, fixed node budget.
- Budget is 120,000 nodes a move.
- Quiescence over captures only.
- No delta pruning, no null-move pruning.
- Late-move reductions for quiet moves.
- Killer-move ordering.
- Piece-square tables, tapered king safety.
- Bishop-pair bonus.
- Fixed-seed Zobrist, fully deterministic.
- No clock, no randomness, no model calls.
- Python 3.13 standard library only.
- One file, 3,893 bytes, under the cap.
- Reads the board from the env server.
- Answers each move in UCI format.
- About 24,000 to 38,000 nodes a second.
- A move takes about 3 to 5 seconds.

## Trial log

Local trial 0, 6 games, 120,000 nodes a move.
Practice floor to enter the final: 1154 Elo.

- v1, readable source: 1364 Elo, 3 wins, 1 draw, 2 losses.
- v1 was too big to submit at 6,135 bytes compressed.
- v2, stripped to fit 4 KB: 1099 Elo, below the floor.
- v3, untested null-move and delta pruning added: 876 Elo.
- Calling them restorations was the mistake.
- The trial, not the theory, caught it.
- v4, v1 search restored: 1191 Elo, 2 wins, 1 draw, 3 losses.
- v4 clears the 1154 floor and is the version submitted.
- The v4-v1 gap is within 6-game noise.
- Game 2 was checked move by move, v1 against v3.
- They agreed on almost every move.
- v3 lost no single move badly; it was weaker all over.
- Removing the new features fixed it.

## Build

- Readable source is engine.py, minified, 9,963 bytes.
- main.py is the kit compress output of engine.py.
- Perft passes on five positions, depths 1 to 3.
- Evaluation matches v1 on twelve test positions.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

---

Entered on [make.fun](https://make.fun/?ref=75k23xv8&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards
