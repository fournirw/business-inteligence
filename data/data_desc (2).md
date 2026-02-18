# Columbus, OH Airbnb Listings (Inside Airbnb) Data Dictionary / Description

**Dataset:** Inside Airbnb Listings for Columbus, Ohio  
**Snapshot date:** 2025-09-26  
**Source CSV:** https://data.insideairbnb.com/united-states/oh/columbus/2025-09-26/visualisations/listings.csv  
**Publisher:** Inside Airbnb (independent, public data project)  
**Geography:** Columbus, Ohio, USA  
**Unit of analysis:** One row per Airbnb listing  

---

## Overview

This dataset contains a snapshot of Airbnb listings in Columbus, Ohio. Each row represents a single listing, including basic listing details, host identifiers, location (neighbourhood and coordinates), room type, nightly price, minimum stay rules, review history, host portfolio size, and availability over the next 365 days.

This dataset is commonly used to explore pricing, availability, neighborhood patterns, room type differences, and host concentration.

---

## Field Definitions (18 columns)

| Field | Description | Example values |
|---|---|---|
| `id` | Unique listing ID. | `12345678` |
| `name` | Listing title (free text). | `"Cozy Short North Studio"` |
| `host_id` | Unique host ID. | `987654321` |
| `host_name` | Host first name (free text). | `"Alex"` |
| `neighbourhood_group` | Neighbourhood group (often blank for Columbus). Treat blank as missing. | `""` or `NA` |
| `neighbourhood` | Neighbourhood name (case sensitive). | `"Short North"` |
| `latitude` | Listing latitude (decimal degrees). | `39.9612` |
| `longitude` | Listing longitude (decimal degrees). | `-82.9988` |
| `room_type` | Room type category. Exact values include: `Entire home/apt`, `Private room`, `Shared room`, `Hotel room`. | `"Entire home/apt"` |
| `price` | Nightly price in USD (whole dollars). | `150` |
| `minimum_nights` | Minimum nights required per booking. | `2` |
| `number_of_reviews` | Total review count since listing creation. | `54` |
| `last_review` | Date of most recent review (`YYYY-MM-DD`). Blank or missing if no reviews. | `"2025-08-14"` or `NA` |
| `reviews_per_month` | Average reviews per month. Blank or missing if no reviews. | `1.25` or `NA` |
| `calculated_host_listings_count` | Number of listings this host has in Columbus. Useful to identify multi listing hosts. | `1`, `5`, `20` |
| `availability_365` | Number of days available in the next 365 days. `0` can mean fully booked or delisted. | `0`, `120`, `365` |
| `number_of_reviews_ltm` | Number of reviews in the last 12 months. | `0`, `12`, `45` |
| `license` | License or registration number, if provided. Often blank. | `""` or `NA` |

---

## Notes on Missing Values and Interpretation

- `neighbourhood_group` is commonly empty for Columbus. Treat empty strings as missing.
- Listings with zero reviews often have `last_review` and `reviews_per_month` as blank or missing.
- `availability_365 = 0` does not always mean permanently unavailable. It can mean fully booked, blocked, or delisted. Interpret carefully.
- `name` and `host_name` are free text fields and may contain punctuation, emojis, or inconsistent formatting.
- `price` is a nightly rate in whole dollars. Do not interpret it as weekly or monthly unless explicitly computed.

---

## Practical Analysis Tips

- Use `room_type` and `neighbourhood` to segment pricing and availability patterns.
- Use `calculated_host_listings_count` to identify hosts with many listings and check if they price differently.
- For review related questions, handle missing values and interpret `number_of_reviews_ltm` as recent demand.

---

## Source Citation

Inside Airbnb. *Columbus, OH Listings (2025-09-26 snapshot).*  
https://data.insideairbnb.com/united-states/oh/columbus/2025-09-26/visualisations/listings.csv

