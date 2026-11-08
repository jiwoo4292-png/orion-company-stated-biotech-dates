# Dataset changelog

## v1.0 · 2026-11-06 snapshot (r3)

- Preserves the 345 records from the calendar feed retrieved at 06:57:16 UTC.
- Separates the exact quote hash, the source receipt digest and time, the SEC filing date and the issuer's separately stated publication date. The primary quote strings, dates and review flags were retained.
- Computes 345 quote hashes and includes 30 matching source receipt pairs. The 315 unresolved receipt pairs remain blank.
- The distribution payload preserves the reviewed CSV and JSON bytes. Both formats contain the same rows. Platform cards, field notes, and checksums document those files.

## Planned v1.1 · November 17, 2026 (KST)

The daily monitor supplies additional source receipt pairs as they are verified.

## Earlier local preparation

- The first draft exported `rows`, `ended`, `disclosed` and `undated` from the captured public feed. The feed's `notListed` was retained as a metadata count.
- The r2 pass tried exact ticker, URL and quote matches against additional public source data. Its reported hashes are distinct from the monitor receipt digest and time used in r3.

For a future correction, record the version, timestamp and timezone, row ID, changed field, prior value, new value, reason and supporting source URL. Distinguish new company wording from a correction to ORION's record. Publish a new version with its own checksums.
