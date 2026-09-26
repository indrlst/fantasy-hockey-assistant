# Fantasy Hockey Lineup Assistant

A small personal script that recommends my daily lineup in one Yahoo Fantasy
Hockey league. It is not a product. There is nothing to sign up for, nothing
to download and nothing to buy — this page exists only to describe what the
tool does.

## What it does

Every morning a scheduled job:

1. Reads NHL player statistics and the day's game schedule from the public
   NHL API.
2. Converts those statistics into expected fantasy points under my league's
   scoring settings.
3. Works out which of my players should start today, solving the position
   assignment exactly rather than greedily.
4. Emails me the changes I need to make — which player to move into the
   starting lineup, which one to bench, and why.

I then make those changes by hand in the Yahoo Fantasy app. The tool does
not touch my Yahoo account and cannot change anything there.

## Scope

- One user: me.
- One league: a 12-team head-to-head points league.
- One team: my own.
- Non-commercial. Not published, not distributed, not monetised.

## Data sources

- **NHL public API** (`api-web.nhle.com`, `api.nhle.com`) — player
  statistics and the game schedule.
- **Injury list** — a public injury feed, used only to avoid starting a
  player who is already ruled out.

## Why Yahoo Fantasy API access would help

The tool currently has no connection to Yahoo at all. My roster lives in a
configuration file that I edit by hand whenever I add or drop a player, and
the league scoring is a copy that can drift out of date.

Read-only access would let the tool read my own team instead:

- my roster, with eligible positions and injury status
- my league's scoring settings and roster positions
- the free agent pool of my league, to suggest pickups
- my weekly matchup opponent, for a weekly preview

That is a handful of requests once per day, for a single team in a single
league. No write access is needed or wanted — I set my lineup myself.

## Source code

The implementation lives in a private repository. I am happy to share it on
request.
