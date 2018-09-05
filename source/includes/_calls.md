# <a name="calls"></a>Calls

The Calls API allows you to get, create, update and delete your phone calls. Each call can be associated to one [Company](#companies), one [Person](#people), one [User](#users) and one [Deal](#deals).

Sellf identifies incoming/outgoing calls with an integer that determines their type: *outgoing*, *incoming*. The match between the two follows the table below:

Type | Description
--------- | -------
0 | Outgoing
1 | Incoming

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the call
**log_at** | string | write | Date of made/received call
**duration** | integer | write | Duration of the call (in seconds)
description | string | write | Content of the call
type | integer | write | Call type (i.e. outgoing, incoming)
person_id | integer | write | Unique identifier of the person related to the call
company_id | integer | write | Unique identifier of the company related to the call
deal_id | integer | write | Unique identifier of the deal concerning the call
**user_id** | integer | write | Unique identifier of the user that the call is assigned to
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Calls

```shell
curl https://api.sellf.io/v2/calls?sort_by=-title -H "Api-Key: {YOUR_API_KEY}"
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
      "title": "Contract negotiation",
      "log_at": "2016-09-23T13:43:30.826603",
      "duration": 600,
      "description": "Lorem ipsum...",
      "type": 1,
      "person_id": null,
      "company_id": 32,
      "deal_id": null,
      "created_at": "2016-09-23T13:43:30.826603",
      "updated_at": "2016-09-23T13:43:30.826603",
      "user_id": 4,
      "id": 3,
    }
  ]
}
```

This endpoint retrieves all calls.

### HTTP Request

`GET /calls`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `log_at`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the call is owned by
person_id | Unique identifier of the person with whom the call is associated
company_id | Unique identifier of the company with whom the call is associated
deal_id | Unique identifier of the deal with whom the call is associated
type | Unique identifier of call type (i.e. `0`, `1`)




## Create a Call

```shell
# Create a new call
curl https://api.sellf.io/v2/calls \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"log_at": "2016-09-23T13:43:30.826603",
              "duration": 60,
              "description": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
              "type": 1,
              "person_id": 15,
              "deal_id": 9,
              "user_id": 4}"
```

> The above command returns JSON structured like this:

```json
{
  "log_at": "2016-09-23T13:43:30.826603",
  "duration": 60,
  "description": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
  "type": 1,
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint allows to create an call.

### HTTP Request

`POST /calls`




## Get a Specific Call

```shell
# Retrieve a call with ID 7
curl https://api.sellf.io/v2/calls/7 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "log_at": "2016-09-23T13:43:30.826603",
  "duration": 60,
  "description": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
  "type": 1,
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint retrieves a specific call.

### HTTP Request

`GET /calls/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the call to retrieve




## Update a Specific Call

```shell
# Update a call with ID 7
curl https://api.sellf.io/v2/calls/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"description": "Debriefing with teammates"}"
```

> The above command returns JSON structured like this:

```json
{
  "log_at": "2016-09-23T13:43:30.826603",
  "duration": 60,
  "description": "Debriefing with teammates",
  "type": 1,
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint allows to update a specific call.

### HTTP Request

`PUT /calls/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the call to retrieve




## Delete a Specific Call

```shell
# Delete the call with ID 7
curl https://api.sellf.io/v2/calls/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific call.


### HTTP Request

`DELETE /calls/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the call to be deleted