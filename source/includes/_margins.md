# <a name="margins"></a>Margins

The Margins API gives you access to your team's margins, in read-only mode. You can retrieve a single margin as well as list of all margins associated with your team. Margins are useful when you want to monitor not only the estimated value of a deal but also the profit that is going to be generated when the deal is successfully closed.

Margins can be associated with any number of [Deals](#deals). In the `Settings > Deal > Margins` section of Sellf web app you can turn on the possibility of creating a new margin, associating to it a label and a *net value*. The *net value* is the percentage of a deal's estimated value that is considered a net profit.

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | Unique identifier of the margin
name | string | Name of the margin
net_rate | integer | A percentage applied to the estimated value of a deal


## Get All Margins

```shell
curl https://api.sellf.io/v1/margins -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
	  "id": 1,
	  "name": "Wild animals insurance",
	  "net_rate": 90
  },
  {
	  "id": 2,
	  "name": "Car insurance",
	  "net_rate": 60
  },
  { ... }
]
```

This endpoint retrieves all margins of the team.

### HTTP Request

`GET /margins`




## Get a Specific Margin

```shell
# Retrieve a margin with ID 3
curl https://api.sellf.io/v1/margins/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
  {
	  "id": 3,
	  "name": "Life insurance",
	  "net_rate": 80
  }
```

This endpoint retrieves a specific margin according to the ID provided.

### HTTP Request

`GET /margins/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the margin to retrieve