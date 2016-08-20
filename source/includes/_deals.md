# <a name="deals"></a>Deals

## Get All Deals

```shell
curl https://api.sellf.io/v1/deals -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  },
  { ... }
]
```

This endpoint retrieves all deals.

### HTTP Request

`GET /deals`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sort | name | Column to sort by, e.g. name

## Create a Deal

```shell
curl https://api.sellf.io/v1/deals \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X POST
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint allows to create a deal.

### HTTP Request

`POST /deals`

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
name | string | Description of the deal

## Get a Specific Deal

```shell
curl https://api.sellf.io/v1/deals/83 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific deal.

### HTTP Request

`GET /deals/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the deal to retrieve

## Update a Specific Deal

```shell
curl https://api.sellf.io/v1/deals/83 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X PUT
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint allows to update a specific deal.

### HTTP Request

`PUT /deals/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the deal to retrieve

## Delete a Specific Deal

```shell
curl https://api.sellf.io/v1/deals/83 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific deal.

### HTTP Request

`DELETE /deals/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the deal to retrieve