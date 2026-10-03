# leadlaglab-data

Append-only raw data archive for [Lead/Lag Lab](https://leadlaglab.com).

## Structure

```
raw/
  prices/year=YYYY/month=MM/day=DD/
  gdelt/year=YYYY/month=MM/day=DD/
  wikipedia/year=YYYY/month=MM/day=DD/
  edgar/year=YYYY/month=MM/day=DD/
  trends/year=YYYY/month=MM/day=DD/
processed/
  security_master/
  features/
  predictions/
  outcomes/
manifest.json
```

## Rules

- **Append only.** No file is ever modified after it is committed.
- Every file has a `schema_version` field embedded.
- Raw files are immutable snapshots of exactly what was fetched.
- `manifest.json` is updated on each pipeline run with build time and data hashes.

## Size monitoring

The pipeline CI checks this repo's size and opens a warning issue when it exceeds 600 MB.
At ~800 MB we migrate to Cloudflare R2. See [docs/PLAN.md](../leadlaglab/docs/PLAN.md).
