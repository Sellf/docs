# <a name="notes"></a>Notes

The Notes API allows you to get, create, update and delete your notes. Each note can be associated to one [Company](#companies), one [Person](#people), one [User](#users) and one [Deal](#deals).

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the note
**title** | string | write | Title of the note
body | string | write | Content of the note
person_id | integer | write | Unique identifier of the person related to the note
company_id | integer | write | Unique identifier of the company related to the note
deal_id | integer | write | Unique identifier of the deal concerning the note
**user_id** | integer | write | Unique identifier of the user that the note is assigned to
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Notes

```shell
curl https://api.sellf.io/v2/notes?sort_by=-title -H "Api-Key: {YOUR_API_KEY}"
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
      "body": "",
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

This endpoint retrieves all notes.

### HTTP Request

`GET /notes`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `title`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the note is owned by
person_id | Unique identifier of the person with whom the note is associated
company_id | Unique identifier of the company with whom the note is associated
deal_id | Unique identifier of the deal with whom the note is associated
title | A string containing or matching the title of the note




## Create a Note

```shell
# Create a new note
curl https://api.sellf.io/v2/notes \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"title": "Debriefing",
              "body": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
              "person_id": 15,
              "deal_id": 9,
              "user_id": 4}"
```

> The above command returns JSON structured like this:

```json
{
  "title": "Debriefing",
  "body": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint allows to create a note.

### HTTP Request

`POST /notes`




## Get a Specific Note

```shell
# Retrieve a note with ID 7
curl https://api.sellf.io/v2/notes/7 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "title": "Debriefing",
  "body": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint retrieves a specific note.

### HTTP Request

`GET /notes/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the note to retrieve




## Update a Specific Note

```shell
# Update a note with ID 7
curl https://api.sellf.io/v2/notes/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"name": "Debriefing with teammates"}"
```

> The above command returns JSON structured like this:

```json
{
  "title": "Debriefing with teammates",
  "body": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "updated_at": "2017-02-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint allows to update a specific note.

### HTTP Request

`PUT /notes/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the note to retrieve




## Delete a Specific Note

```shell
# Delete the note with ID 7
curl https://api.sellf.io/v2/notes/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific note.


### HTTP Request

`DELETE /notes/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the note to be deleted