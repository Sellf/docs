# <a name="products"></a>Products

The Products API gives you access to your team's [products](https://app.sellf.io/settings/products), in read-only mode. You can retrieve a single product as well as list of all products associated with your team.

Products can be associated with any number of [Deals](#deals). In the `Settings > Deal > Products` [section](https://app.sellf.io/settings/products) of Sellf web app you can turn on the possibility of using products, giving them a *name* and a *unit price*.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the product
code | string | read | Custom identifier of the product
**name** | string | read | Name of the product
**unit_price** | integer | read | Price of the product per unit
unit_cost | integer | read | Cost of the product per unit
max_discount | integer | read | Max discount that can be applied to the product
max_markup | integer | read | Max markup that can be applied to the product


## Get All Products

```shell
curl https://api.sellf.io/v2/products -H "Api-Key: {YOUR_API_KEY}"
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
      "code": "LI456",
      "name": "Life insurance"
      "unit_price": 10,
      "max_discount": 100,
      "max_markup": null,
      "unit_cost": 0,
      "id": 1,
    },
    {
      "code": "HI789",
      "name": "Home insurance",
      "unit_price": 12,
      "max_discount": 100,
      "max_markup": null,
      "unit_cost": 234,
      "id": 2
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
curl https://api.sellf.io/v2/products/2 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "code": "HI789",
  "name": "Home insurance",
  "unit_price": 12,
  "max_discount": 100,
  "max_markup": null,
  "unit_cost": 234,
  "id": 2
}
```

This endpoint retrieves a specific product according to the ID provided.

### HTTP Request

`GET /products/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the product to retrieve