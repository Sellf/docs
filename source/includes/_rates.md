# Rate limits

To prevent API abuse or overload, Sellf APIs are rate limited. The rate limit is considered per API token. The Sellf API allows to perform 10 requests/second.

If your limit reaches zero, subsequent requests will receive the `429 Too Many Requests` response code until the request reset time has been reached.
