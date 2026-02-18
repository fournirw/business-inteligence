# Extra Instructions

## Room type filter (exact)
- Use `room_type = 'Entire home/apt'`
- Use `room_type = 'Private room'`
- Use `room_type = 'Shared room'`
- Use `room_type = 'Hotel room'`
- Text matches are **case- and punctuation-sensitive**.
- Do not use partial matching unless explicitly requested.

## Neighbourhood filter (exact)
- Use `neighbourhood = 'Short North'` (example).
- Values are **case-sensitive**.
- If unsure of spelling, first show distinct neighbourhood values.

## Host filter (exact)
- Use `host_name = 'Alex'` or `host_id = 12345678`.
- Prefer `host_id` when identifying a specific host.
- To identify multi-listing hosts, filter using `calculated_host_listings_count > 1`.

## Price handling (very important)
- `price` represents the nightly rate in whole U.S. dollars.
- Do not assume weekly or monthly pricing.
- Use numeric comparisons:
  - `price < 150`
  - `price BETWEEN 100 AND 200`
- Do not treat price as text.

## Reviews handling
- Listings with zero reviews may have:
  - `last_review` = NULL
  - `reviews_per_month` = NULL
- When calculating averages, exclude NULL values unless explicitly instructed.
- Use `number_of_reviews_ltm` for recent demand analysis.

## Availability interpretation
- `availability_365` represents number of days available in the next year.
- `availability_365 = 0` may indicate:
  - Fully booked
  - Temporarily unavailable
  - Delisted
- Do not assume permanent inactivity without additional filtering.

## Aggregation intent (very important)
State whether you want a single row, the raw matching rows, or an aggregate. You can copy/paste:

- **Calculate average price:** `AVG(price)`
- **Calculate total listings:** `COUNT(*)`
- **Calculate total reviews:** `SUM(number_of_reviews)`
- **Show rows:** return the matching row(s) without aggregation

## Sorting and ranking
- Use `ORDER BY price DESC` for most expensive listings.
- Use `ORDER BY number_of_reviews DESC` for most reviewed listings.
- Always specify `LIMIT 10` (or another limit) when requesting “top” results.

## Grouping rules
When grouping, explicitly state grouping columns:

- `GROUP BY room_type`
- `GROUP BY neighbourhood`
- `GROUP BY host_id`
- When grouping, select only grouped columns and aggregated metrics.

## Verification step (recommended)
If any filter is ambiguous, request a preview first:
- “Show distinct room_type values.”
- “Show distinct neighbourhood values.”
- “Show first 10 rows.”

## Action wording (so I take the right next step)
Start your request with:

- **Calculate** / **Compute** → run a query and return computed results
- **Show** / **Filter to** → return matching rows
- **Compare** → run grouped aggregation
- **Rank** → apply ordering and limit

---

# Paste-ready prompt templates

- **Show entire homes under $150**
  `Show: room_type = 'Entire home/apt' AND price < 150`

- **Top 10 most reviewed listings**
  `Rank: ORDER BY number_of_reviews DESC LIMIT 10`

- **Average price by room type**
  `Compute: GROUP BY room_type, AVG(price)`

- **Listings in Short North**
  `Show: neighbourhood = 'Short North'`

- **Multi-listing hosts**
  `Show: calculated_host_listings_count > 1`

---

# Default behavior

If you include relevant filters, I will apply these rules automatically.

If a request is ambiguous (for example, unclear neighbourhood spelling or unclear aggregation intent), I will first show matching rows or distinct values before aggregating.
