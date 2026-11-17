# Dataset changelog

## v1.0 · 2026-11-06 snapshot (r3)

- Preserves the 345 records from the calendar feed retrieved at 06:57:16 UTC.
- Separates the exact quote hash, the source receipt digest and time, the SEC filing date and the issuer's separately stated publication date. The primary quote strings, dates and review flags were retained.
- Computes 345 quote hashes and includes 30 matching source receipt pairs. The 315 unresolved receipt pairs remain blank.
- The distribution payload preserves the reviewed CSV and JSON bytes. Both formats contain the same rows. Platform cards, field notes, and checksums document those files.

## Planned v1.1 · November 17, 2026 (KST)

The daily monitor supplies additional source receipt pairs as they are verified.

### Q3 2026 filing check (new company wording, not corrections to ORION's record)

- Scope: 131 records from 83 companies whose stated window ends in 2027 or later and whose source was filed before October 15, 2026. Each was compared with the company's Q3 2026 10-Q, 6-K or earnings release on SEC EDGAR (a 10-K or fiscal-year release where the company's fiscal year ends in July or September).
- 98 records: the company restates the same timing.
- 19 records: new company wording. 17 state a new period, 1 is the company's statement that it "will discontinue" a Phase 3 study (argenx UNITY, 6-K filed October 8, 2026), and 1 is a company announcement of an FDA approval (Nuvation Bio IBTROZI sNDA). Each keeps the company sentence as written with its SEC source; the earlier sentence stays in the record's history.
- 13 records: not restated. The Q3 filing no longer states the timing; the record keeps the last stated sentence with its source and date.
- 1 record: no Q3 filing yet (Veru; fiscal year ends September 30).
- Changed sentences are checked word for word against the SEC copies before the release.

## Earlier local preparation

- The first draft exported `rows`, `ended`, `disclosed` and `undated` from the captured public feed. The feed's `notListed` was retained as a metadata count.
- The r2 pass tried exact ticker, URL and quote matches against additional public source data. Its reported hashes are distinct from the monitor receipt digest and time used in r3.

For a future correction, record the version, timestamp and timezone, row ID, changed field, prior value, new value, reason and supporting source URL. Distinguish new company wording from a correction to ORION's record. Publish a new version with its own checksums.
