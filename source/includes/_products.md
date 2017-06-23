# <a name="products"></a>Products

The Products API gives you access to your team's [products](https://app.sellf.io/settings/products), in read-only mode. You can retrieve a single margin as well as list of all products associated with your team. Margins are useful when you want to monitor not only the estimated value of a deal but also the profit that is going to be generated when the deal is successfully closed.

Margins can be associated with any number of [Deals](#deals). In the `Settings > Deal > Margins` [section](https://app.sellf.io/settings/products) of Sellf web app you can turn on the possibility of creating a new margin, associating to it a label and a *net value*. The *net value* is the percentage of a deal's estimated value that is considered a net profit.

Since products are identified by labels and we want to extend it to let you manage products in Sellf, hereafter, as well in the API, we use the term *products* referring to the aforementioned products.

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
      "net_rate": 80,
      "id": 1,
      "name": "Life insurance"
    },
    {
      "net_rate": 60,
      "id": 2,
      "name": "Car insurance"
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
  "net_rate": 60,
  "id": 2,
  "name": "Car insurance"
}
```

This endpoint retrieves a specific product according to the ID provided.

### HTTP Request

`GET /products/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the product to retrieve