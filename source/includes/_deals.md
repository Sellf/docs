# <a name="deals"></a>Deals

The Deals API allows you to get, create, update and delete your deals.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | Unique identifier of the deal
name | string | Brief description of the deal
user_id | integer | Unique identifier of the user that the deal is assigned to
estimated_value | float | Value of the deal, with decimal part if needed
is_hot | boolean | To point if the deal is important or not
stage_id | integer | Unique identifier of the deal’s current stage in the pipeline
source_id | integer | Unique identifier of the deal source
main_person_id | integer | Unique identifier of a primary person
main_company_id | integer | Unique identifier of a primary company
estimated_close_at | datetime | Estimated close date of the deal
tags | array | An array of tags for a deal




## Get All Deals

```shell
curl https://api.sellf.io/v1/deals -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "First deal",
    "estimated_value": 1234.56,
    "is_hot": true,
    "tags": ["Italy", "Treviso"]
  },
  {
    "id": 2,
    "name": "Second deal",
    "estimated_value": 12,
    "is_hot": false
  },
  { ... }
]
```

This endpoint retrieves all deals.

### HTTP Request

`GET /deals`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `value`, `estimated_close_at`, `stage_changed_at`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the person is owned by
company_id | Unique identifier of the company with whom the person is associated
name | A string containing or matching the name of the person




## Create a Deal

```shell
# Create a new deal
curl https://api.sellf.io/v1/deals \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{\"name\": \"New deal\", \"estimated_value\": 0, \"is_hot\": true, \"tags\": [\"Italy\", \"Treviso\"]}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "name": "New deal",
  "estimated_value": 0,
  "is_hot": true,
  "tags": ["Italy", "Treviso"]
}
```

This endpoint allows to create a deal.

### HTTP Request

`POST /deals`




## Get a Specific Deal

```shell
# Retrieve a deal with ID 3
curl https://api.sellf.io/v1/deals/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "name": "New deal",
  "estimated_value": 0,
  "is_hot": true,
  "tags": ["Italy", "Treviso"]
}
```

This endpoint retrieves a specific deal.

### HTTP Request

`GET /deals/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the deal to retrieve




## Update a Specific Deal

```shell
# Update a deal with ID 3
curl https://api.sellf.io/v1/deals/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{\"name\": \"Modified deal\", \"estimated_value\": null, \"tags\": [\"Italy\", \"Treviso\", \"Roncade\"]}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "name": "Modified deal",
  "estimated_value": null,
  "is_hot": true,
  "tags": ["Italy", "Treviso", "Roncade"]
}
```

This endpoint allows to update a specific deal.

<aside class="warning">
In order to modify tags associated to a deal, you need to supply the entire set. Tags are replaced every time they are part of a request.
</aside>

### HTTP Request

`PUT /deals/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the deal to retrieve




## Delete a Specific Deal

```shell
# Delete a deal with ID 3
curl https://api.sellf.io/v1/deals/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific deal. Deleting a deal implies that even all the associated entities are deleted, except for people and companies.


### HTTP Request

`DELETE /deals/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the deal to retrieve