# Rate limits

To prevent API abuse or overlad, Sellf APIs are rate limited. The rate limit is considered per API token. API allows to perform 10 requests/second.

If your limits reaches zero, subsequent requests will receive the `429 Too Many Requests` response code until the request reset time has been reached.
