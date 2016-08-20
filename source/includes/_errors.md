# Errors

Each API call returns an HTTP status code that reflects the nature of the response. We follow the [HTTP status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) conventions.

Codes in the 2xx range indicate success, instead any request that did not succeed will return a 4xx or 5xx error. The 4xx range means there was a problem with the request. The 5xx range means that something went wrong on our end.

Specificall, the Sellf API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request --  Invalid request parameters
401 | Unauthorized -- API key is missing or wrong (it can be invalid)
402	| Payment Required --	Subscription payment is required
403 | Forbidden -- The entity requested is not accessibile due to hierarchy policies or Sellf permissions
404 | Not Found -- The specified entity could not be found
409	| Conflict	-- The request could not be completed due to a conflict with the current state of the resource
422	| Unprocessable Entity --	The request is well-formed but cannot be processed due to validation issues with the payload
429 | Too Many Requests -- You're requesting too many entities!
500 | Internal Server Error -- We had a problem with our server. Try again later and if the problem persists please contact us
502 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later
