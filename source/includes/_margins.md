# <a name="margins"></a>Products

The Products API gives you access to your team's [margins](https://app.sellf.io/settings/margins), in read-only mode. You can retrieve a single margin as well as list of all margins associated with your team. Margins are useful when you want to monitor not only the estimated value of a deal but also the profit that is going to be generated when the deal is successfully closed.

Margins can be associated with any number of [Deals](#deals). In the `Settings > Deal > Margins` [section](https://app.sellf.io/settings/margins) of Sellf web app you can turn on the possibility of creating a new margin, associating to it a label and a *net value*. The *net value* is the percentage of a deal's estimated value that is considered a net profit.

Since margins are identified by labels and we want to extend it to let you manage products in Sellf, hereafter, as well in the API, we use the term *products* referring to the aforementioned margins.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the product
name | string | read |Name of the product
net_rate | integer | read | A percentage applied to the estimated value of a deal
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit

## Get All Products

```shell
curl https://api.sellf.io/v1/products -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "meta": {
    "has_more": false,
    "object": "list"
  },
  "data": [
    {
      "created_at": "2016-04-19T16:16:52.111686",
      "net_rate": 80,
      "id": 1,
      "name": "Life insurance",
      "updated_at": "2016-05-10T08:35:31.732557"
    },
    {
      "created_at": "2016-04-19T16:26:37.789595",
      "net_rate": 60,
      "id": 2,
      "name": "Car insurance",
      "updated_at": "2016-05-03T13:55:13.897777"
    }
  ]
}
```

This endpoint retrieves all products of the team.

### HTTP Request

`GET /products`

Parameter | Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `created_at`, `updated_at`)




## Get a Specific Product

```shell
# Retrieve a product with ID 2
curl https://api.sellf.io/v1/products/2 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "created_at": "2016-04-19T16:26:37.789595",
  "net_rate": 60,
  "id": 2,
  "name": "Car insurance",
  "updated_at": "2016-05-03T13:55:13.897777"
}
```

This endpoint retrieves a specific product according to the ID provided.

### HTTP Request

`GET /products/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the product to retrieve