# Dilemma Tournaments: results

The public record of the Dilemma tournaments (<https://github.com/dilemma-tournaments/dilemma-the-game>), as JSON.
The site at <https://dilemma-site.buster-benson.workers.dev> is built from this repo and nothing else: what is here is what is public.

## Licence

The data in this repo is licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use it, remix it, chart it;
credit "Dilemma Tournaments (dilemma-tournaments/results)" and link back.

## Layout

```
data/
  games.json              the tournament list (schema_version, games[], team_color_order)
  team-colors.json        append-only colour order: a team keeps its colour forever
  <tournament id>/
    game.json             one tournament: settings, teams and players, standings, round summaries and recaps
    round-N.json          one round: every match of the round, with its move-by-move tape once the tournament is complete
    pledges.json          pledge tags on team messages once the tournament is complete: a model's read of what each message
                          pledged (Jev, by TypeSafe), and a verdict computed from the moves played next
```

`schema_version` in `games.json` changes only when a field is removed or changes meaning.

## What is not here, on purpose

Strategy code, agent journals, raw result CSVs, feedback files, audit logs and machine paths are never published. While a
tournament is live, the data holds standings, round recaps and match results only; the move-by-move tapes, team-to-team
threads and strategy self-descriptions appear after the tournament completes.

## How it is written

Only the publisher writes here (`scripts/publish-site.js --push` in the engine repo), one commit per change, titled
`publish <tournament id> round N` or `publish <tournament id> final`. Please do not open pull requests against `data/`:
the next publish would overwrite them. Questions and corrections go to the engine repo's issues.
