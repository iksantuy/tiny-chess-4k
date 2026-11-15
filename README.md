# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/iksantuy/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/iksantuy/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB Python chess engine for make.fun's *Build the strongest chess engine in
4 KB of Python* bounty.

`main.py` is the whole engine, under the 4,096-byte cap. It is a packed
LZMA payload written by `makefun compress`; the readable source it was packed
from is `engine_src.py` (kept out of the tree by `.gitignore`, since the
committed snapshot has to stay under 8 KB).

## How it plays

- 10x12 mailbox board, own move generator, pseudo-legal moves with the
  king-capture test standing in for a legality check.
- Negamax alpha-beta, iterative deepening to a fixed node budget (never a
  clock, so a replay plays the same moves), quiescence on captures,
  MVV-LVA ordering, killer moves and a small history table.
- Material plus piece-square evaluation, mirror-indexed for black.
- Each move it reads the FEN and the env's legal move list, searches, and
  posts the best move back to the env.

## Run it

```sh
MAKEFUN_ENV_URL=<env> python3 main.py
```

## Layout

- `main.py` — the engine, the only file it reads
- `engine_src.py` — the readable source `main.py` is packed from
- `LICENSE` — MIT

---

<sub>Entered on [make.fun](https://make.fun/?ref=t9mzww6d&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
