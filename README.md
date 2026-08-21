# Available workers.dev subdomains

This repository saves dated snapshots of short Cloudflare `workers.dev` account subdomains.

Cloudflare gives each account one configurable subdomain, such as `your-name.workers.dev`. Workers
in that account then use addresses such as `my-worker.your-name.workers.dev`.

## Coolest available now

This ranking is subjective. It favors mirrored spelling, repeated letters, and real or word-like
sounds. No triple-letter label is available in the latest snapshot.

| Rank | Label | Why it stands out |
| ---: | --- | --- |
| 1 | `xrx` | Mirrored, repeats `x`, and has a strong visual shape. |
| 2 | `yiy` | Mirrored, repeats `y`, and is easy to say letter by letter. |
| 3 | `uyu` | Mirrored, repeats `u`, and sounds like "oo-you". |
| 4 | `zfz` | Mirrored, with a sharp repeated `z`. |
| 5 | `zpz` | Mirrored and close in sound to "zips". |
| 6 | `vkv` | A clean mirrored consonant pattern. |
| 7 | `wrw` | Mirrored, with two wide `w` characters. |
| 8 | `iyi` | Mirrored and face-like. |
| 9 | `woe` | A short, memorable English word. |
| 10 | `nub` | A real word that also works as a compact handle. |
| 11 | `urn` | A recognizable three-letter English word. |
| 12 | `fiv` | Short and close in sound to "five". |
| 13 | `buv` | Compact and easy to pronounce. |

## Latest snapshot: 2026-08-21

- All 17,576 three-letter names from `aaa` through `zzz` were checked.
- 2,621 three-letter names remain in the latest available list.
- 0 candidates remained unresolved after retries.
- Compared with June 20, 2,599 names remained available, 22 became available, and 386 were no
  longer available.

Availability changes. A name in this repository is not reserved and might no longer be available.

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
check confirmed all 26 first-letter groups, 2,621 unique available names, no duplicate names, and no
unresolved requests.

Cloudflare documents how the account subdomain forms each Worker URL in its
[`workers.dev` documentation](https://developers.cloudflare.com/workers/configuration/routing/workers-dev/).
The candidate-check endpoint used for this sweep is not in Cloudflare's
[public Workers Subdomains API reference](https://developers.cloudflare.com/api/resources/workers/subresources/subdomains/)
as of August 21, 2026, so its behavior can change.
