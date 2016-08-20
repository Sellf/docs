# Errors

Each API call returns an HTTP status code that reflects the nature of the response. We have done our best to follow the [HTTP status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) conventions.

Any request that did not succeed will return a 4xx or 5xx error. The 4xx range means there was a problem with the request. The 5xx range means that something went wrong on our end.

The Sellf APIs use the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request --  Invalid request parameters
401 | Unauthorized -- API key is missing or wrong (it can be invalid)
403 | Forbidden -- The entity requested is not accessibile due to hierarchy policies or Sellf permissions
404 | Not Found -- The specified entity could not be found
429 | Too Many Requests -- You're requesting too many entities!
500 | Internal Server Error -- We had a problem with our server. Try again later and if the problem persists please contact us
502 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later
