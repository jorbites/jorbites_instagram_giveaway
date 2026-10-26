# Jorbites Instagram Giveaway Scripts

Fetch comments from an Instagram giveaway post, extract `jorbites.com/recipes/{id}` links, tally valid entries per user (one entry per valid comment), and compute each participant's probability of winning.

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Provide credentials via `.env` (copy from `.env.example`):

```bash
cp .env.example .env
```

## Usage

### Compute participants and show table
```bash
python giveaway.py \
  --post-url "https://www.instagram.com/p/DNDunraMPPb/"
```

- The script logs in with `IG_USERNAME`/`IG_PASSWORD` and fetches the post’s comments.
- A comment is counted only if it contains a `https://jorbites.com/recipes/{id}` link.
- Each valid comment = 1 entry for that user.
- The terminal prints a compact, nicely formatted table with rank, username, entries and probability.

### Pick winners

- Pick winner(s) (weighted by number of valid comments):
```bash
python pick_winner.py \
  --post-url "https://www.instagram.com/p/DNDunraMPPb/"
```

- The terminal prints compact and nicely formatted boxes/tables.
