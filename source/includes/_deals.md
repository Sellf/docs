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
  }
]
```

This endpoint retrieves all deals.

### HTTP Request

`GET /deals`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

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

[//]: <> POST http|https://tapi.sellf.io/v1/deals -> puborg_v1_deals.create_deal
[//]: <> PUT|PATCH http|https://tapi.sellf.io/v1/deals/<int:rid> -> puborg_v1_deals.update
[//]: <> DELETE http|https://tapi.sellf.io/v1/deals/<int:rid> -> puborg_v1_deals.delete
