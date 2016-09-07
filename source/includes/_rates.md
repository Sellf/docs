# Rate limits

To prevent API abuse or overload, Sellf APIs are rate limited. The rate limit is considered per API token. The Sellf API has different rates depending on your Sellf plan, as stated in the table below.

Plan | Rate
---------- | -------
Free | n/a
Pro | n/a
Starter | 3/sec (100/min)
Performance | 20/sec (600/min)
Enterprise | Dedicated


If your limit reaches zero, subsequent requests will receive the `429 Too Many Requests` response code until the request reset time has been reached.
