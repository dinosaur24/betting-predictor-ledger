# Prediction ledger

Every forecast this engine has published, filed before kickoff.

`ledger.sqlite` is append-only: a row is written when a prediction is
issued and its `result_*` columns are filled in once the match is
played. Nothing else about an issued row is ever modified, and the
code refuses to write a row at or after kickoff.

The point of this repository is the history rather than the file.
Each commit here is timestamped by GitHub, so you can check that a
prediction existed before the match it is about — which is the one
thing a downloaded file cannot tell you.

```sh
git log --format='%H %ci' -- ledger.sqlite     # when each state existed
sqlite3 ledger.sqlite "SELECT kickoff, home_team, away_team,
  p_home, p_draw, p_away, result_home, result_away FROM predictions
  ORDER BY kickoff DESC LIMIT 20;"
```

Published automatically by the engine. Nothing here is written by hand.
