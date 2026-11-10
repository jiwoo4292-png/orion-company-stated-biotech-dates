# ORION statement sample

Twelve selected statements cover three companies and four events: AGIO mitapivat, VIR-5818, VIR ECLIPSE 1, and NTHI NEO212. This sample illustrates an exact-date change, stated periods, and a later quotation with no date or period.

## Inspect in ten minutes

Open [sample.csv](sample.csv) or [sample.json](sample.json). Filter `record_id=C0139` for the AGIO date change and subsequent SEC evidence; `C0316` for VIR-5818. Follow a `source_url` and `location_in_document` to read the sentence in context. Use `pinned_url` to cite the saved statement payload.

Each row is a statement, not an outcome or forecast. `record_id` groups an event. `statement_id`, `version`, and `previous_version` order this sample's selected statements; they are separate from production change-page versions. The November AGIO filing supports the date stated in October; it is not another date change. Repeated ECLIPSE statements retain separate sources.

## Fields and saved versions

`verbatim_quote` preserves the selected sentence after removing HTML tags and decoding character references. Sentence whitespace, including non-breaking spaces and source line breaks, is preserved; surrounding list bullets are excluded. Some hashes differ from earlier stored text. Those records are unchanged; [provenance.json](provenance.json) documents the differences.

`stated_timing` copies a date or period. `date_precision` is `day`, `half`, `quarter`, or empty. For the later VIR-5818 quotation: **No date or period is stated in this later quotation.** Unknown indications remain empty.

`filed_date` is the SEC filing date. The press release has `published_date` instead. `collected_date` and `collected_at_utc` identify the retained response, including later re-collection. Review dates describe automated checks (`check_type=auto`); human review dates remain empty. Historical filing dates do not establish when ORION first recorded a statement.

`pinned_url` points to a GitHub commit containing one JSON statement payload. Payloads omit their own URL to avoid self-reference. CSV blanks equal JSON empty strings. CSV is UTF-8 with BOM; decode quoted multiline cells with a CSV parser. JSON versions are numbers.

## Verify text and files

Decode `verbatim_quote`, encode that exact string as UTF-8, then calculate SHA-256. Do not trim, normalize spaces or Unicode, add a BOM, or append a newline. Compare with `quote_sha256`; the rule is also in each row. A match checks saved text against its digest, not publisher identity, factual accuracy, or a clinical result.

`source_file_sha256` separately hashes response-body bytes after transport decompression. Responses are not distributed here and can change when fetched again. For the October AGIO release, this sample checked the saved excerpt and existing receipt, without reopening the full response. [SHA256SUMS.txt](SHA256SUMS.txt) checks package files separately.

## License

ORION-owned material is under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/); credit ORION and identify changes. Company quotations retain their original rights and are outside that grant. See [LICENSE.md](../../LICENSE.md). Commercial data inquiries: [For Teams](https://www.orionbiotechai.com/teams).
