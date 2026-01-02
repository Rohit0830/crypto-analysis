# CoinGecko Markets API

This file documents the CoinGecko "coins/markets" endpoint used to fetch market data (prices, market caps, volume, and percentage changes).

Endpoint
```
https://api.coingecko.com/api/v3/coins/markets
```

Common query parameters
- `vs_currency` (required): target currency for prices (e.g. `usd`).
- `order`: sort order; common value `market_cap_desc` (by market cap descending).
- `per_page`: number of items per page (e.g. `100`). Max usually 250.
- `page`: page number (1-based).
- `price_change_percentage`: comma-separated periods to include, e.g. `24h,7d`.

Full example URL (used in this project)
```
https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&price_change_percentage=24h,7d
```

Notes
- This is a public API and does not require an API key. Respect CoinGecko rate limits (avoid excessive polling; use caching).
- When `price_change_percentage` is requested, the response includes fields such as `price_change_percentage_24h_in_currency` and `price_change_percentage_7d_in_currency`.
- The query string parameter `authuser=0` is not required by CoinGecko and can be removed; it likely came from a browser/account context.

Quick curl example
```bash
curl -s "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&price_change_percentage=24h,7d"
```

Python example (requests)
```python
import requests

url = 'https://api.coingecko.com/api/v3/coins/markets'
params = {
		'vs_currency': 'usd',
		'order': 'market_cap_desc',
		'per_page': 100,
		'page': 1,
		'price_change_percentage': '24h,7d'
}

resp = requests.get(url, params=params)
data = resp.json()
# `data` is a list of coin objects
```

Sample response (trimmed)
```json
[
	{
		"id": "bitcoin",
		"symbol": "btc",
		"name": "Bitcoin",
		"current_price": 47000.12,
		"market_cap": 890000000000,
		"total_volume": 35000000000,
		"price_change_percentage_24h_in_currency": -1.23,
		"price_change_percentage_7d_in_currency": 4.56
	}
]
```

Best practices
- Cache results for at least a minute depending on your use case to reduce requests.
- Paginate through `page` if you need more than `per_page` results.
- Handle missing/null fields gracefully; use default values when needed.

References
- API docs: https://www.coingecko.com/en/api/documentation


Api= https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&price_change_percentage=24h,7d&authuser=0