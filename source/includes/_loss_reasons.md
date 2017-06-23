# <a name="loss_reasons"></a>Loss Reasons

The Loss Reasons API gives you access to your team's loss reasons, in read-only mode. You can retrieve a single loss reason as well as list of all loss reasons associated with your team.

Loss Reasons can be associated with any number of [Deals](#deals). Once you sign up in Sellf, we suggests a bunch of common loss reasons, it's up to up enable this feature or not. In the `Settings > Deal > Loss Reasons` section of Sellf web app you can turn on the possibility of adding more loss reasons (e.g. `Price`, `Competition`, `Lack of budget`, `Not interested`, ...). You can add as many deals' loss reasons as you want.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the loss reason
name | string | read | Name of the loss reason
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Loss Reasons

```shell
curl https://api.sellf.io/v2/loss_reasons -H "Api-Key: {YOUR_API_KEY}"
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
      "id": 1,
      "name": "Competition"
    },
    {
      "id": 2,
      "name": "Price"
    }
  ]
}
```

This endpoint retrieves all deals' loss reasons.

### HTTP Request

`GET /loss_reasons`

### Query Parameters

Parameter | Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `created_at`, `updated_at`)




## Get a Specific Loss Reason

```shell
# Retrieve a deal loss reason with ID 2
curl https://api.sellf.io/v2/loss_reasons/2 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Price"
}
```

This endpoint retrieves a specific loss reason according to the ID provided.

### HTTP Request

`GET /loss_reasons/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the source to retrieve