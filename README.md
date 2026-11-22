# makefun-tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/kuroro0125/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/kuroro0125/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine that fits in under 4 KB of Python. `main.py` is the whole
engine: it unpacks a compact negamax searcher (LZMA-packed, as the rules
allow) and plays every game of the gauntlet through the env API.

How it plays:

- 120-cell padded board, full legal move generation (castling, en
  passant, promotions), verified move-for-move against python-chess on
  thousands of positions.
- Negamax alpha-beta search with MVV-LVA ordering and a capture
  quiescence search; deeper search and a larger node budget once the
  board empties out. Fixed budgets only — no clock, no randomness, so
  replays match move for move.
- Evaluation is material plus simple positional terms (pawn advance,
  knight centrality, bishop pair), all computed from the square, so no
  tables eat into the byte budget.

## Run it

```sh
MAKEFUN_ENV_URL=<env url> python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=quiet-comet-69-4734&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
