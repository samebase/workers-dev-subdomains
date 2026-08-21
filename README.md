# Available workers.dev subdomains

This repository saves a snapshot of short Cloudflare `workers.dev` account subdomains that were
available on June 20, 2026.

Cloudflare gives each account one configurable subdomain, such as `pfp.workers.dev`. Workers in that
account then use addresses such as `my-worker.pfp.workers.dev`.

## Results

- All 676 two-letter names were unavailable.
- All 17,576 three-letter names from `aaa` through `zzz` were checked.
- 2,985 three-letter names were available at the time of the sweep.
- `pfp` was selected after the sweep.

Availability changes. A name in this repository is not reserved and might no longer be available.
For example, `pfp` appears in the list because it was available before it was selected.

## Files

- [`data/available-three-letter-subdomains.txt`](data/available-three-letter-subdomains.txt) is the
  clean list, with one account subdomain per line. Add `.workers.dev` to get the full account domain.
- [`data/sweep-2026-06-20.md`](data/sweep-2026-06-20.md) is the full dated report. It groups the names
  by first letter and includes the shortlist that led to `pfp`.

## How the list was made

The sweep generated every lowercase three-letter value and sent an authenticated, read-only request
for each candidate:

```text
GET /accounts/{account_id}/workers/subdomains/{candidate}
```

The responses observed during the sweep used these Cloudflare error codes:

- `10031`: unavailable
- `10032`: available but not configured

Temporary server errors were retried. The final check confirmed all 26 first-letter groups, 2,985
unique available names, no duplicate names, and no unresolved requests.

Cloudflare documents how the account subdomain forms each Worker URL in its
[`workers.dev` documentation](https://developers.cloudflare.com/workers/configuration/routing/workers-dev/).
The candidate-check endpoint used for this sweep is not in Cloudflare's
[public Workers Subdomains API reference](https://developers.cloudflare.com/api/resources/workers/subresources/subdomains/)
as of August 21, 2026, so its behavior can change.
