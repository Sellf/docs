# <a name="products"></a>Products

The Products API gives you access to your team's [products](https://app.sellf.io/settings/products). You can retrieve a single product as well as list of all products associated with your team. You can also create new products and update existing ones.

Products can be associated with any number of [Deals](#deals). In the `Settings > Deal > Products` [section](https://app.sellf.io/settings/products) of Sellf web app you can turn on the possibility of using products, giving them a *name* and a *unit price*.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the product
**name** | string | write | Name of the product
**unit_price** | float | write | Price of the product per unit
unit_cost | float | write | Cost of the product per unit
max_discount | integer | write | Max discount (percentage) that can be applied to the product
max_markup | integer | write | Max markup (percentage) that can be applied to the product
code | string | write | Custom identifier of the product
goal_rate | integer | write | Incentive (percentage) for the user computed on the price of the product
rep_rate | integer | write | Representative commission (percentage) computed on the price of the product
is_enabled | boolean | write | Availability of the product




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
      "goal_rate": 110,
      "rep_rate": 80,
      "id": 1,
    },
    {
      "code": "HI789",
      "name": "Home insurance",
      "unit_price": 12,
      "max_discount": 100,
      "max_markup": null,
      "unit_cost": 234,
      "goal_rate": null,
      "rep_rate": null,
      "id": 2
    }
  ]
}
```

This endpoint retrieves all products of the team.

### HTTP Request

`GET /products`

### Query Parameters

Parameter | Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `created_at`, `updated_at`)




## Create a Product

```shell
# Create a new product
curl https://api.sellf.io/v2/products \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"code": "LI455",
               "name": "Life insurance"
               "unit_price": 100,
               "max_discount": 15,
               "max_markup": null,
               "unit_cost": 0,
               "goal_rate": 90,
               "rep_rate": 20,
               "is_enabled": true}"
```

> The above command returns JSON structured like this:

```json
{
  "code": "LI455",
  "name": "Life insurance"
  "unit_price": 100,
  "max_discount": 15,
  "max_markup": null,
  "unit_cost": 0,
  "goal_rate": 90,
  "rep_rate": 20,
  "is_enabled": true,
  "id": 7
}
```

This endpoint allows to create an product.

### HTTP Request

`POST /products`




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
  "goal_rate": null,
  "rep_rate": null,
  "is_enabled": true,
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




## Update a Specific Product

```shell
# Update a product with ID 7
curl https://api.sellf.io/v2/products/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"is_enabled": false, "code": "LI451"}"
```

> The above command returns JSON structured like this:

```json
{
  "code": "LI451",
  "name": "Life insurance"
  "unit_price": 100,
  "max_discount": 15,
  "max_markup": null,
  "unit_cost": 0,
  "goal_rate": 90,
  "rep_rate": 20,
  "is_enabled": false,
  "id": 7
}
```

This endpoint allows to update a specific product.

### HTTP Request

`PUT /products/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the product to retrieve