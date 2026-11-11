# SlotDrop open data: blackjack expected values

The expected value of every move for every blackjack hand against every dealer upcard, free to reuse with attribution (CC BY 4.0).

| File | Rows | What it is |
|---|---|---|
| `data/slotdrop-blackjack-hands.csv` | 340 | One row per player hand and dealer upcard: expected value of hit, stand, double and split, best move, second-best move, cost of the mistake |
| `data/slotdrop-blackjack-hands.json` | 340 | The same data as JSON |

Live version: [https://slotdropapp.com/blackjack-charts.html](https://slotdropapp.com/blackjack-charts.html).

## What the data shows

A strategy chart tells you what to do. This table tells you by how much.

- **The closest call is Hard 16 vs dealer 10**: hit beats stand by 0.0006 of a bet.
- **The widest gap is on Hard 20 vs dealer 8**, where stand beats hit by 1.64 bets.
- Best moves across the 340 situations: hit 144, stand 99, split 52, double 45.

## Columns

Rules: Multi-deck shoe, dealer stands on soft 17, double after split allowed, no surrender. Last updated 2026-11-10.

| Column | Meaning |
|---|---|
| `hand` | Player hand: `Hard 16`, `Soft 18 (A-7)`, `Pair of 8s`… |
| `hand_type` | `hard`, `soft` or `pair` |
| `dealer_upcard` | Dealer's visible card, 2 to 10 or A |
| `best_move`, `second_best_move` | `hit`, `stand`, `double` or `split` |
| `ev_best` | Expected value of the best move, per unit staked |
| `ev_hit`, `ev_stand`, `ev_double`, `ev_split` | Expected value of each move (`ev_split` is empty when the hand is not a pair) |
| `cost_of_second_best` | Expected value lost by playing the second-best move instead of the best |
| `dealer_bust_probability` | Probability the dealer busts from that upcard |
| `player_bust_probability_one_hit` | Probability the player busts by taking one card |
| `url` | Page that explains the hand on SlotDrop |

## Method

Expected values are computed exactly, not simulated, by recursion over every possible draw.

- Multi-deck game, approximated as an infinite deck: each rank is drawn with its nominal probability (1/13, and 4/13 for ten-valued cards). The gap with a six-deck shoe is of the order of one thousandth.
- Dealer stands on soft 17. Blackjack pays 3:2 and the dealer peeks for blackjack.
- Double allowed on any two cards, and after a split. No surrender. One split only (no resplit).
- Values are per unit staked and are not rounded before being written.

## Licence and citation

Data: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt it, including commercially, as long as you credit the source:

> Source: SlotDrop blackjack hands dataset (slotdropapp.com/blackjack-charts.html), CC BY 4.0

## Corrections

Found a wrong number? Open an issue with the hand and the source you compared it against. If it holds up, the data is corrected.

## About

SlotDrop (https://slotdropapp.com) is an independent site about the maths of casino games. It is funded by casino affiliate commission, which is disclosed on the site.
