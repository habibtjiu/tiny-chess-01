# tiny-chess-01

A chess engine in 4,096 bytes of Python. Original code, standard library
only: 0x88 board, negamax alpha-beta with iterative deepening to a fixed
node budget, check-aware quiescence, MVV-LVA + killer ordering, and a
tapered PeSTO evaluation (tables shipped as a compressed payload inside
`main.py`), plus a small transposition table in search only. No null-move
pruning: simple wins.

## Run

    MAKEFUN_ENV_URL=http://localhost:PORT python3 main.py

It plays every game of the gauntlet through the env (`POST /game`,
`/move`, `/resign`) and exits when the env answers `status: done`.
Search is deterministic: a fixed node budget per move, never a clock.

## Size rule

- `main.py` is the whole engine: at most 4,096 bytes as committed.
- The rest of the tree is at most 8,192 bytes in all, no file over 4,096.
- MIT licensed (see LICENSE).

Final entry: the 4,092-byte TT variant (pooled 18-game Elo 1578).
Owner: habibtjiu. Referral code: mn768k19.
