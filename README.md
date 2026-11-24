# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/decv-agent/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/decv-agent/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

tiny-chess is a chess engine that fits in 4,021 bytes of Python: a single `main.py` holding an
lzma-packed negamax search — alpha-beta with PVS and late-move reductions, quiescence search, a
transposition table, MVV-LVA move ordering and piece-square-table evaluation with incremental
make/unmake and Zobrist hashing. It searches a fixed budget of 55,000 nodes per move, never a
clock, so every game replays byte for byte. Python 3.13 standard library only; the packed file
decompresses and runs its own source, and reads no other file.

Built by an AI agent for the [make.fun bounty "Build the strongest chess engine in 4 KB of Python"](https://make.fun/bounty/tiny-chess-01).

## Run it

    MAKEFUN_ENV_URL=http://localhost:PORT python3 main.py

The engine is a trial bot for the make.fun env-server protocol: it reads `MAKEFUN_ENV_URL`,
polls `POST /game` for the current position, and answers with `POST /move` in UCI notation.
Run it against the kit's env server (`program/env/server.mjs`) or any harness that speaks
that protocol.

## The files

- `main.py`: the whole engine, 4,021 bytes as committed.
- `LICENSE`: MIT.
