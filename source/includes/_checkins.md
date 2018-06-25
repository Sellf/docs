# <a name="checkins"></a>Checkins (COMING SOON)

The checkins API allows you to get, create, update and delete your phone checkins. Each checkin can be associated to one [Company](#companies), one [Person](#people), one [User](#users) and one [Deal](#deals).

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the checkin
**checkin_at** | string | write | Date of the checkin
**address** | integer | write | Place of the checkin
latitude | float | read | Latitude of the checkin address
longitude | float | read | Longitude of the checkin address
description | string | write | Content of the checkin
person_id | integer | write | Unique identifier of the person related to the checkin
company_id | integer | write | Unique identifier of the company related to the checkin
deal_id | integer | write | Unique identifier of the deal concerning the checkin
**user_id** | integer | write | Unique identifier of the user that the checkin is assigned to
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Checkins

```shell
curl https://api.sellf.io/v2/checkins?sort_by=-title -H "Api-Key: {YOUR_API_KEY}"
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
      "address": "Via Thomas Alva Edison, Padova, PD",
      "checkin_at": "2016-09-23T13:43:30.826603",
      "description": "Lorem ipsum...",
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

This endpoint retrieves all checkins.

### HTTP Request

`GET /checkins`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `checkin_at`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the checkin is owned by
person_id | Unique identifier of the person with whom the checkin is associated
company_id | Unique identifier of the company with whom the checkin is associated
deal_id | Unique identifier of the deal with whom the checkin is associated




## Create a Checkin

```shell
# Create a new checkin
curl https://api.sellf.io/v2/checkins \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"address": "Via Thomas Alva Edison, Padova, PD",
              "checkin_at": "2016-09-23T13:43:30.826603",
              "description": "Lorem ipsum...",
              "person_id": 15,
              "deal_id": 9,
              "user_id": 4}"
```

> The above command returns JSON structured like this:

```json
{
  "address": "Via Thomas Alva Edison, Padova, PD",
  "checkin_at": "2016-09-23T13:43:30.826603",
  "description": "Lorem ipsum...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint allows to create an checkin.

### HTTP Request

`POST /checkins`




## Get a Specific Checkin

```shell
# Retrieve a checkin with ID 7
curl https://api.sellf.io/v2/checkins/7 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "address": "Via Thomas Alva Edison, Padova, PD",
  "checkin_at": "2016-09-23T13:43:30.826603",
  "description": "Lorem ipsum...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint retrieves a specific checkin.

### HTTP Request

`GET /checkins/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the checkin to retrieve




## Update a Specific Checkin

```shell
# Update a checkin with ID 7
curl https://api.sellf.io/v2/checkins/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"address": "Via Sile, 41, 31056 Roncade (TV) Italia"}"
```

> The above command returns JSON structured like this:

```json
{
  "address": "Via Sile, 41, 31056 Roncade (TV) Italia",
  "checkin_at": "2016-09-23T13:43:30.826603",
  "description": "Lorem ipsum...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint allows to update a specific checkin.

### HTTP Request

`PUT /checkins/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the checkin to retrieve




## Delete a Specific Checkin

```shell
# Delete the checkin with ID 7
curl https://api.sellf.io/v2/checkins/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific checkin.


### HTTP Request

`DELETE /checkins/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the checkin to be deleted