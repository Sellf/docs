# Introduction

Welcome to the Sellf API! You can use our API to access Sellf API endpoints, which can get information on [contacts](#contacts) and [deals](#deals) in our database.


```ruby
# To have a response in JSON
Accept: application/json
```


```ruby
# To send a JSON request
Content-Type: application/json
```

We have language bindings in Shell ([cURL](https://en.wikipedia.org/wiki/CURL)). You can view code examples in the dark area to the right.

The API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). All requests should be made over SSL. All request and response bodies, including errors, are encoded in [JSON](https://en.wikipedia.org/wiki/JSON). Please specify the `Accept` and `Content-Type` header as `application/json`.

The API dates are represented in UTC following the [ISO 8601](https://it.wikipedia.org/wiki/ISO_8601) industry-adopted standard.
Each entity has a unique integer ID.

<aside class="notice">
All API calls must be made to `https://api.sellf.io/v1`, where `v1` is the (current) version of the APIs.
</aside>

Please report any issues to <a href="mailto:support@sellfapp.com">support@sellfapp.com</a> or leave any feedback [here](https://sellf.uservoice.com).