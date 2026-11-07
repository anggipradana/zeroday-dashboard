# Zero-Day Dashboard — data

**A running list of recently disclosed vulnerabilities that were exploited before a patch existed**
— what the flaw is, who makes the affected product, when it was patched, and where the vendor
advisory lives.

It is a **data repository**. The dashboard itself is at
[zeroday.anggipradana.com](https://zeroday.anggipradana.com).

It is for defenders and vulnerability-management teams who want a short, curated view of
zero-day activity, rather than monitoring every vendor advisory feed themselves.

## What's in `data/`

| File | Contents |
|---|---|
| `sheet2.json` | recently disclosed zero-days, with vendor, product, impact type and patch date |
| `sheet3.json` | the same schema, covering a wider historical window |

Each record carries the CVE identifier, vendor, product, vulnerability class, description,
disclosure and patch dates, a link to the vendor advisory, and the public credit line.

## Where the data comes from

The list is maintained as a public spreadsheet and refreshed daily by
`.github/workflows/fetch-json.yml`, which reads it through a public spreadsheet-to-JSON service and
commits the result. Vendors, dates and links come from the vendors' own advisories.

> The `Reported By` field reproduces the credit line the vendor published. It is not an assertion
> about who found the flaw.

## How to use it

```bash
curl -L https://raw.githubusercontent.com/anggipradana/zeroday-dashboard/main/data/sheet2.json
```

Entries marked `???` in a date field are still unknown at the source — typically a vulnerability
disclosed without a public discovery date.

## Licence

The vulnerability data itself is public information published by the affected vendors. The curation
and presentation are provided for defensive security use.
