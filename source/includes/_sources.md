# <a name="sources"></a>Sources

The Sources API gives you access to your team's sources, in read-only mode. You can retrieve a single source as well as list of all sources associated with your team.

Sources can be associated with any number of [Deals](#deals). Once you sign up in Sellf, we suggests a bunch of common sources, it's up to up enable this feature or not. In the `Settings > Deal > Sources` section of Sellf web app you can turn on the possibility of adding more sources (e.g. `Newsletter`, `Word of mouth`, `Referral`, `Website`, ...). You can add as many deals' sources as you want.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the source
name | string | read | Name of the source
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Sources

```shell
curl https://api.sellf.io/v1/sources -H "Api-Key: {YOUR_API_KEY}"
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
      "created_at": "2016-03-23T11:09:04.239262",
      "id": 1,
      "name": "Referral",
      "updated_at": "2016-05-11T15:29:36.390240"
    },
    {
      "created_at": "2016-03-23T11:09:04.257173",
      "id": 2,
      "name": "Word of mouth",
      "updated_at": "2016-03-29T12:22:20.922757"
    }
  ]
}
```

This endpoint retrieves all deals' sources.

### HTTP Request

`GET /sources`

### Query Parameters

Parameter | Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `created_at`, `updated_at`)




## Get a Specific Source

```shell
# Retrieve a deal source with ID 2
curl https://api.sellf.io/v1/sources/2 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "created_at": "2016-03-23T11:09:04.257173",
  "id": 2,
  "name": "Word of mouth",
  "updated_at": "2016-03-29T12:22:20.922757"
}
```

This endpoint retrieves a specific source according to the ID provided.

### HTTP Request

`GET /sources/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the source to retrieve