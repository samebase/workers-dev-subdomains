# Available workers.dev subdomains

This repository saves dated snapshots of short Cloudflare `workers.dev` account subdomains.

Cloudflare gives each account one configurable subdomain, such as `pfp.workers.dev`. Workers in that
account then use addresses such as `my-worker.pfp.workers.dev`.

## Latest snapshot: 2026-08-21

- All 17,576 three-letter names from `aaa` through `zzz` were checked.
- 2,623 three-letter names were available but not configured at the time of the sweep.
- `pfp` is the configured account subdomain.
- 0 candidates remained unresolved after retries.
- Compared with June 20, 2,601 names remained available, 22 became available, and 384 were no
  longer available.

Availability changes. A name in this repository is not reserved and might no longer be available.
The configured name is included for context, but it is not an available choice.

## Files

- [`data/available-three-letter-subdomains.txt`](data/available-three-letter-subdomains.txt) is the
  June 20, 2026 list, with one account subdomain per line.
- [`data/sweep-2026-06-20.md`](data/sweep-2026-06-20.md) is the original dated report.
- [`data/available-three-letter-subdomains-2026-08-21.txt`](data/available-three-letter-subdomains-2026-08-21.txt)
  is the latest clean list, with one available label per line. Add `.workers.dev` to get the full
  account domain.
- [`data/sweep-2026-08-21.md`](data/sweep-2026-08-21.md) is the latest full report, including
  per-prefix counts and every available label.

## How the list was made

The sweep generated every lowercase three-letter value and sent an authenticated, read-only request
for each candidate:

```text
GET /accounts/{account_id}/workers/subdomains/{candidate}
```

The responses observed during the sweep used these Cloudflare error codes:

- `10031`: unavailable
- `10032`: available but not configured

Temporary server errors, including rate-limit responses, were retried with throttling. The latest
check confirmed all 26 first-letter groups, 2,623 unique available names, one configured name, no
duplicate names, and no unresolved requests.

Cloudflare documents how the account subdomain forms each Worker URL in its
[`workers.dev` documentation](https://developers.cloudflare.com/workers/configuration/routing/workers-dev/).
The candidate-check endpoint used for this sweep is not in Cloudflare's
[public Workers Subdomains API reference](https://developers.cloudflare.com/api/resources/workers/subresources/subdomains/)
as of August 21, 2026, so its behavior can change.
