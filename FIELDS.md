# Field reference

All types below allow `null`. The JSON wrapper has `metadata` and `records`. The 54 columns describe each record. Dates are ISO `YYYY-MM-DD` when supplied as a single day. Times are shown as recorded. Use `date_precision` to distinguish a day from a period.

| Field | JSON type | Meaning |
| --- | --- | --- |
| `record_id` | string | Identifier inside this snapshot. |
| `source_collection` | string | Original feed array. It does not establish the event outcome. |
| `source_index` | integer | Original zero-based position in that array. |
| `program_id` | string | Program or event record identifier in the source feed. |
| `ticker` | string | Ticker as shown in the feed. |
| `company` | string | Company name as shown in the feed. |
| `drug_or_program` | string | Drug, program or other subject name. |
| `indication` | string | Indication text as provided. |
| `application_type` | string | Application type, when stated. |
| `event_type_raw` | string | Feed event code. |
| `event_type_label` | string | English label for the feed event code. |
| `event_type_ko` | string | Korean label for the feed event code. |
| `date_or_period` | string | Date or period wording as captured from the feed. |
| `date_precision` | string | `day`, `month`, `quarter`, `half`, `year`, `ambiguous` or `none`. |
| `event_date` | string | Company-stated date for a day-precision record. |
| `window_start` | string | Period start boundary, where supplied. |
| `window_end` | string | Period end boundary. A boundary alone is not an event date. |
| `company_sentence` | string | Primary issuer quotation or excerpt. |
| `timing_legend_quote` | string | Quoted legend used to read the timing statement. |
| `timing_context_quote` | string | Additional quoted context for the timing statement. |
| `source_url` | string | Primary source URL for `company_sentence`. |
| `source_publish_date` | string | Publication date stated separately by the issuer. |
| `source_publish_at` | string | More precise issuer publication time, if explicitly provided. |
| `source_filing_date` | string | SEC filing day as supplied by the feed. |
| `source_form` | string | Primary source form or document type. |
| `source_accession` | string | SEC accession number as recorded. |
| `quote_sha256` | string | SHA-256 of the primary quotation using the recipe below. |
| `source_snapshot_sha256` | string | Monitor-reported SHA-256 of one exact source receipt, paired with `source_fetched_at`. |
| `source_fetched_at` | string | UTC fetch time of the paired source receipt. |
| `orion_checked_at` | string | Source-check timestamp given in the feed. |
| `orion_last_checked_date` | string | Date-only source-check label. |
| `source_check_method` | string | Source-check method as provided. |
| `review_status` | string | `automated`, `human` or `unknown` according to the feed. |
| `review_status_raw` | string | Original review code from the feed. |
| `quote_verified` | boolean | Feed's quote-match flag. Human review is identified separately. |
| `wording_history` | array | Reported earlier text and source details. An empty array means no entries were supplied. |
| `wording_changes_count` | integer | Feed's count of wording changes. It does not count only FDA date changes. |
| `disclosure` | object | Linked follow-up disclosure as provided by the feed. |
| `presentation_event_type` | string | Event type of a separately documented conference presentation. |
| `presentation_date` | string | Presentation day from the separate source. |
| `presentation_format` | string | Format from the separate source. |
| `presentation_sentence` | string | Quoted presentation wording from the separate source. |
| `presentation_source_url` | string | Source URL for the separate presentation. |
| `presentation_source_date` | string | Date of that source as provided. |
| `presentation_reported_source_sha256` | string | Source digest supplied for the separate presentation. |
| `presentation_reported_quote_sha256` | string | Quotation digest supplied for the separate presentation. |
| `presentation_verified_by` | string | Supplied reviewer label. `codex` denotes AI. |
| `presentation_review_decision_date` | string | Date of the separate display decision. |
| `presentation_review_decision_scope` | string | Scope of that display decision. |
| `presentation_start_time` | string | Presentation start time as written. |
| `presentation_end_time` | string | Presentation end time as written. |
| `presentation_time_zone_as_written` | string | Time zone label as written, without conversion. |
| `presentation_conference` | object | Conference name and period, as supplied. |
| `company_url` | string | ORION company page. |

The `presentation_*` fields cover separate source statements. Their dates and hashes belong to those statements. They are independent of the primary quote and its source receipt. `source_filing_date`, `source_publish_date`, `source_fetched_at`, `orion_checked_at` and `event_date` each mark a different event. Keep them separate when filtering or citing.

## Reproduce a quote hash

Trim only the ends of `company_sentence` using `U+0009–000D`, `U+001C–0020`, `U+0085`, `U+00A0`, `U+1680`, `U+2000–200A`, `U+2028–2029`, `U+202F`, `U+205F` and `U+3000`. Keep all internal characters and line endings. Encode as UTF-8 without a BOM and hash with SHA-256. This recipe applies no Unicode normalization.

```python
import hashlib

points = [*range(0x09, 0x0E), *range(0x1C, 0x21), 0x85, 0xA0, 0x1680,
          *range(0x2000, 0x200B), 0x2028, 0x2029, 0x202F, 0x205F, 0x3000]
trim = ''.join(map(chr, points))
print(hashlib.sha256('  abc\n'.strip(trim).encode('utf-8')).hexdigest())
# ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f20015ad
```

## Blanks

- Empty CSV cells correspond to JSON `null`. A blank in one field leaves the row's other evidence and review flags intact.
- The daily monitor fills the paired source receipt fields on an exact URL and current quote match. A missing receipt leaves both receipt fields blank. Possible reasons are a missing URL receipt, a missing match to the current quote version, and a missing receipt corresponding to an earlier retained observation.
- Filing and publication dates are populated only when the feed provides the matching kind of date. Timestamp-level checks can be absent even when a date-only check is present.
- For other optional fields, null can mean the source omitted the field or the field did not apply. The source does not always distinguish those cases.
