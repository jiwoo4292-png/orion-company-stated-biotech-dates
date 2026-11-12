# ORION Company-Stated Biotech Dates

ORION records the dates and periods U.S. biotech companies state in SEC filings and press releases, alongside the quoted wording, source links and available wording history. This is a research and source-checking reference. Company-stated dates can change and do not establish that an event occurred.

## Snapshot

Release **v1.0**. The preserved source export is `dataset-v1-local-20261106-r3`. The source [ORION calendar feed](https://www.orionbiotechai.com/calendar.json) was generated on **2026-11-06** and retrieved at `2026-11-06T06:57:16.079853Z`. This fixed snapshot has **345 records and 54 fields**, comprising 276 `rows`, 60 `disclosed`, 9 `undated` and 0 `ended` records. The feed's aggregate `notListed` is outside the row export. The live calendar may now show different dates or records.

Original review flags show 344 automated checks and 1 human review. Review flags describe the source feed's process. The export is a selected set of statements rather than a comprehensive registry of companies, events or outcomes. ORION provides no investment advice.

## Files and reading

| File | Contents |
| --- | --- |
| [dataset.csv](dataset.csv) | All records in source order. UTF-8 with BOM and CRLF. |
| [dataset.json](dataset.json) | UTF-8 object with `metadata` and `records`. The metadata preserves the original export version and its status at creation. The `local_only_not_published` value describes that source export. |
| [FIELDS.md](FIELDS.md) | All 54 fields, types and how to interpret dates, reviews and blanks. |
| [schema.json](schema.json) | JSON Schema for the JSON file. |
| [LICENSE.md](LICENSE.md) | ORION license, attribution and separate rights for company excerpts. |
| [CHANGELOG.md](CHANGELOG.md) | Dataset revision and correction conventions. |
| [SHA256SUMS.txt](SHA256SUMS.txt) | SHA-256 of every other file in this payload. |

CSV and JSON carry the same records. A CSV blank maps to JSON `null`. CSV values for `wording_history`, `disclosure` and `presentation_conference` contain serialized JSON. Keep `false`, `0` and `[]` as values. Preserve the `source_accession` and other identifiers as text.

From the payload directory, use `sha256sum -c SHA256SUMS.txt` or compare hashes computed with `Get-FileHash -Algorithm SHA256`. The checksum list verifies the released file bytes. It is separate from quote hashes, original-source digests and timestamps.

## Evidence and blanks

- `quote_sha256` is present on all 345 records. It binds the exact quoted text after trimming the fixed boundary character set in [FIELDS.md](FIELDS.md). The hash alone cannot establish that the source contains the text.
- The paired `source_snapshot_sha256` and `source_fetched_at` are available on 30 records. They come from the retained monitor observation that links the same URL and current quote. Source bytes and the monitor ledger are outside this payload. The pair represents a specific collection receipt and does not establish publication, first observation across all history, human review, or public timestamp attestation.
- The other 315 pairs are blank. There was no receipt for that URL on 299 records, no matching quote version on 11, and no corresponding receipt for an earlier observation on 5. A blank applies to the export field. Other evidence or review flags may still exist for the row.
- SEC `source_filing_date` is available on 344 records. The separately stated issuer `source_publish_date` is available on 1. These describe different events and are kept separate from `event_date` and `orion_checked_at`.

## Daily source monitoring and v1.1

The `source_snapshot` columns (`source_snapshot_sha256` and `source_fetched_at`) are filled through daily monitoring when a source receipt matches the same URL and exact current quotation. Unmatched pairs stay blank. This v1 release is a fixed snapshot. Newly matched receipts are reflected in later exports. **v1.1 is planned for November 17, 2026 (KST).**

`source_snapshot` 관련 두 칸은 매일 감시에서 원문 URL과 현재 인용문이 일치한 수신 기록으로 채웁니다. 일치하는 기록이 없는 칸은 비워 둡니다. **v1.1은 2026년 11월 17일(KST) 공개 예정입니다.**

## Citation

> ORION. *ORION Company-Stated Biotech Dates*, v1.0 (`dataset-v1-local-20261106-r3`). Calendar snapshot retrieved 2026-11-06T06:57:16.079853Z. Original feed https://www.orionbiotechai.com/calendar.json. ORION-authored material under CC BY-NC 4.0. Issuer excerpts remain subject to their original rights.

Add the verified release or mirror URL and the SHA-256 of the file you used. For a row, include `record_id`, `program_id`, the issuer and `source_url`, and specify whether the cited date is a company-stated event date, a filing date or a publication date. Keep ORION attribution and the license link when sharing the ORION-authored material, and indicate any changes. Cite issuer excerpts separately when you quote them. [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

ORION licenses its original compilation, documentation and recorded history under CC BY-NC 4.0 to the extent of its rights. Issuer excerpts, including quotes in context and history fields, and other third-party material remain subject to their original rights. See [LICENSE.md](LICENSE.md).
