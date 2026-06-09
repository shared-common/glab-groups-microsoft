# glab-groups-microsoft

Thin GitHub Actions wrapper for the Microsoft GitHub organization mirror.

## Scope

- Loads `gh-actions-cfg/glab-groups-microsoft`
- Calls the reusable workflow in `glab-groups-shared@mcr/main`
- Uses the BWS target PAT secret `GL_PAT_GROUP_MICROSOFT_SVC`
- Uses the shared GitHub App secrets `GH_ORG_READ_APP_ID`,
  `GH_ORG_READ_APP_INSTALL_ID`, and `GH_ORG_READ_APP_PEM` for GitHub
  organization discovery and clone auth
- Mirrors the current public `github.com/microsoft` repositories into
  `microsoft/*` beneath `glab-forks`
- Runs deterministic mirror batch shards with five jobs max in parallel
- Schedules at minute 5 of hours 7 and 19 UTC
- Publishes discovery, plan, report, CSV, JSON, and Parquet artifacts for each run

## Validation

```sh
python3 -m unittest discover -s tests
```
