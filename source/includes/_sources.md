# <a name="sources"></a>Sources

The Sources API gives you access to your team's sources, in read-only mode. You can retrieve a single source as well as list of all sources associated with your team.

Sources can be associated with any number of [Deals](#deals). Once you sign up in Sellf, we suggests a bunch of common sources, it's up to up enable this feature or not. In the `Settings > Deal > Sources` section of Sellf web app you can turn on the possibility of adding more sources (e.g. `Newsletter`, `Word of mouth`, `Referral`, `Website`, ...). You can add as many deals' sources as you want.

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | Unique identifier of the source
name | string | Name of the source


## Get All Sources

```shell
curl https://api.sellf.io/v1/sources -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
	  "id": 1,
	  "name": "Newsletter",
  },
  {
	  "id": 2,
	  "name": "Referral",
  },
  { ... }
]
```

This endpoint retrieves all deals' sources.

### HTTP Request

`GET /sources`




## Get a Specific Source

```shell
# Retrieve a deal source with ID 3
curl https://api.sellf.io/v1/sources/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
  {
	  "id": 3,
	  "name": "Word of mouth"
  }
```

This endpoint retrieves a specific source according to the ID provided.

### HTTP Request

`GET /sources/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the source to retrieve