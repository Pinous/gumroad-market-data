# Gumroad Market Data 2026

> Real revenue data from 146,271 digital products across 43,884 sellers on Gumroad.

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-March_2026-blue.svg)](CHANGELOG.md)
[![Dataset Size](https://img.shields.io/badge/Products-146K+-green.svg)](#quick-overview)

## Quick Overview

| Category | Est. Revenue | Products | Avg Price | Avg Sales |
|---|---|---|---|---|
| Software Development | $65.8M | 1,083 | $39.95 | 293 |
| Other | $64.2M | 729 | $128.91 | 419 |
| Business & Money | $15.4M | 1,520 | $49.49 | 247 |
| 3D Assets | $13.9M | 2,082 | $40.71 | 290 |
| Design | $8.8M | 1,202 | $29.35 | 331 |
| Self-Improvement | $8.7M | 1,016 | $26.67 | 273 |
| Education | $6.5M | 747 | $235.12 | 249 |
| Drawing & Painting | $6.0M | 1,028 | $18.19 | 401 |
| Films | $4.3M | 550 | $27.95 | 241 |
| Fitness & Health | $4.2M | 379 | $37.45 | 243 |
| Writing & Publishing | $3.6M | 226 | $40.50 | 381 |
| Music & Sound Design | $1.9M | 661 | $26.06 | 161 |
| Photography | $1.5M | 516 | $14.53 | 317 |
| Gaming | $756K | 779 | $14.67 | 71 |
| Comics & Graphic Novels | $373K | 163 | $9.46 | 133 |
| Audio | $77K | 64 | $27.43 | 40 |
| Fiction Books | $32K | 118 | $14.65 | 25 |
| Recorded Music | $32K | 89 | $9.53 | 33 |

[Full data with all columns &rarr;](data/categories.csv)

## What's in This Dataset?

All data is available in both **CSV** and **JSON** formats.

| File | Rows | Description |
|---|---|---|
| [`categories.csv`](data/categories.csv) | 18 | Revenue, pricing, and sales by niche |
| [`pricing-tiers.csv`](data/pricing-tiers.csv) | 8 | Performance by price range ($0.01 to $200+) |
| [`platform-comparison.csv`](data/platform-comparison.csv) | 5 | Gumroad vs Whop vs Payhip vs Lemonsqueezy vs Systeme.io |
| [`revenue-concentration.csv`](data/revenue-concentration.csv) | 5 | How revenue is distributed (top 1% vs bottom 50%) |
| [`seller-distribution.csv`](data/seller-distribution.csv) | 5 | Sales performance by portfolio size |
| [`review-impact.csv`](data/review-impact.csv) | 6 | How review rates correlate with sales |
| [`rating-impact.csv`](data/rating-impact.csv) | 6 | How star ratings correlate with sales |
| [`product-types.csv`](data/product-types.csv) | 6 | Downloads vs e-books vs courses vs bundles |
| [`top-products.csv`](data/top-products.csv) | 8 | Highest-grossing products on Gumroad |

JSON versions of all files are in [`data/json/`](data/json/). Aggregated stats (totals, PWYW vs fixed pricing) are in [`analysis/summary-stats.json`](analysis/summary-stats.json).

## Key Findings

- **Top 1% of products capture 77.3% of total revenue** ($159.3M out of $206M)
- **Pay-What-You-Want products outsell fixed-price by 8%** (287 vs 265 avg sales)
- **$30-$50 is the pricing sweet spot** (highest sales volume at a solid price point)
- **Software Development alone = $65.8M** (32% of all tracked revenue)
- **Products with 4.5-4.9 star ratings average 1,197 sales** vs 18 for unrated products
- **Sellers with 11+ products average 5,201 total sales** vs 269 for single-product sellers
- **Bottom 50% of products share only 0.3% of revenue** ($680K)

## Methodology

This dataset was built by analyzing publicly available data on Gumroad product pages:

- **Coverage**: Products with 5+ ratings across all 18 Gumroad categories
- **Revenue estimation**: `estimated_revenue = avg_price x total_sales` (sales inferred from public rating counts and review rates)
- **Data collection**: Automated scraping of public Gumroad listings
- **Limitations**: Revenue figures are estimates, not official Gumroad data. Actual revenue may differ due to refunds, discounts, and currency conversions
- **Update frequency**: Monthly

## Use Cases

- **Validate a product idea** before building — check category demand and pricing benchmarks
- **Find underserved niches** with high demand density and low competition
- **Benchmark your product** against category averages for pricing, sales, and ratings
- **Academic research** on creator economy markets and digital product economics
- **Build tools** for digital product creators using real market data

## Quick Start

### Python

```python
import pandas as pd

df = pd.read_csv("data/categories.csv")
print(df.sort_values("estimated_revenue_usd", ascending=False).head(5))
```

### JavaScript

```javascript
const categories = require("./data/json/categories.json");
const top5 = categories
  .sort((a, b) => b.estimated_revenue_usd - a.estimated_revenue_usd)
  .slice(0, 5);
console.table(top5);
```

### R

```r
df <- read.csv("data/categories.csv")
head(df[order(-df$estimated_revenue_usd), ], 5)
```

## Data Source

This dataset is maintained by [InsightRaider](https://insightraider.com), a market intelligence platform for digital product creators.

Read the full analysis: [Profitable Niches 2026: 152K Products Analyzed](https://insightraider.com/blog/profitable-niches-2026)

Explore live data: [InsightRaider Gumroad Analytics](https://insightraider.com)

## Cite This Dataset

```bibtex
@misc{insightraider2026gumroad,
  title   = {Gumroad Market Data 2026},
  author  = {InsightRaider},
  year    = {2026},
  url     = {https://github.com/Pinous/gumroad-market-data},
  note    = {146,271 products, 43,884 sellers, 18 categories}
}
```

## Contributing

Found an error? Have a suggestion? See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

This dataset is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to share and adapt this data for any purpose, including commercial use, as long as you provide attribution.
