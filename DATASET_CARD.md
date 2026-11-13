# ORION Company-Stated Biotech Dates

Company-stated U.S. biotech FDA target dates and clinical timing, with quoted source wording (a sentence or excerpt), source links, SHA-256 hashes of the stored quote, and recorded wording histories.

For researchers, data journalists, newsletter writers and students.

## Records

Each row is a captured company statement/event record. It includes identifiers, company/ticker, drug/program, indication/application, event type, date or period and precision; quotation/excerpt and context; source URL, form and filing/publication dates; quote hash; checks/review status; and available wording history. Separate source-receipt and presentation fields appear where supplied. See [FIELDS.md](FIELDS.md) for the 54 fields.

CSV blanks map to JSON `null`. Optional nulls can mean missing or inapplicable information. An empty `wording_history` means no entries were supplied; history counts include wording changes beyond FDA dates. Period boundaries are not event dates.

The quote hash fingerprints stored text using the FIELDS.md recipe; it does not prove truth, source authenticity or observation time.

## Load v1.0

```python
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/jiwoo4292-png/orion-company-stated-biotech-dates/v1.0/dataset.csv", dtype=str)
print(data.shape)
```

## Updates

ORION monitors sources daily and publishes separate versioned exports. Version 1.0 is a fixed snapshot dated 2026-11-06.

## License and citation

ORION material is licensed under CC BY-NC 4.0 to the extent of ORION's rights. Company excerpts and other third-party material remain subject to their owners' rights. See [LICENSE.md](LICENSE.md).

Cite the company, source URL and filing/publication date, ORION record URL and check date, and dataset version. Company-stated dates can change and do not establish that an event occurred.

Commercial use or custom data: hello@orionbiotechai.com
