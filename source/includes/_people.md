# <a name="people"></a>People

The People API allows you to get, create, update and delete your people. Each person can be associated to a [Company](#companies) and one or more [Deals](#deals).

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the person
code | string | write | Custom identifier of the person
**first_name** | string | write | First name of the person
**last_name** | string | write | Last name of the person
title | string | write | Role in the company
prospect_status | integer | write | Status of the person
vat | string | write | Value-added tax of the person
birthday | datetime | write | Birthday of the person
website | string | write |  writeebsite
email | string | write | Primary email
email_secondary | string | write | Secondary email
phone | string | write | Office or home number
mobile | string | write | Mobile phone number
fax | string | write | Fax number
skype  | string | write | Skype nickname
address | string | write | Office or home address of the person
latitude | float | write | Geographic coordinate of the person
longitude | float | write | Geographic coordinate of the person
description | string | write |  A description of the person
tags | array | write | An array of tags for a person
company_id | integer | write | Unique identifier of the person's company
**user_id** | integer | write | Unique identifier of the user that the person is assigned to
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit

<aside class="warning">
When you want to update the tags of a person be aware to include any existing tag, otherwise they will be fully replaced by the tags specified in the update request.
</aside>




## Get All People

```shell
curl https://api.sellf.io/v2/people?sort_by=-name -H "Api-Key: {YOUR_API_KEY}"
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
      "website": null,
      "company_id": 2,
      "fax": null,
      "first_name": "Alessia",
      "user_id": 4,
      "description": "Hi! I'm Alessia, head of Customer Support at Sellf",
      "title": "Head of Customer Happiness",
      "prospect_status": 0,
      "vat": "IT1234567890",
      "birthday": "1983-02-04T14:57:54.707662",
      "mobile": null,
      "created_at": "2015-11-27T14:57:54.707662",
      "skype": "sellfapp",
      "updated_at": "2016-07-05T12:19:20",
      "longitude": 12.4274592,
      "id": 1,
      "code": null,
      "phone": null,
      "last_name": "Bellon",
      "address": "Via Sile, 41, 31056 Roncade (TV) Italia",
      "latitude": 45.5648361,
      "email_secondary": null,
      "email": "alessia@sellf.be",
      "tags": [
        "customer",
        "employee"
      ]
    }
  ]
}
```

This endpoint retrieves all people.

### HTTP Request

`GET /people`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `first_name`, `last_name`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the person is owned by
company_id | Unique identifier of the company with whom the person is associated
name | A string containing or matching the name of the person




## Create a Person

```shell
# Create a new person
curl https://api.sellf.io/v2/people \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"first_name": "Filippo",
               "last_name": "Zanella",
               "title": "Founder of Sellf",
               "email": "filippo@sellfapp.com",
               "tags": ["Italy", "Treviso"],
               "user_id": 4}"
```

> The above command returns JSON structured like this:

```json
{
  "website": null,
  "company_id": null,
  "fax": null,
  "first_name": "Filippo",
  "user_id": 4,
  "description": null,
  "title": "Founder of Sellf",
  "prospect_status": 2,
  "vat": null,
  "birthday": null,
  "mobile": null,
  "created_at": "2016-09-08T16:36:52",
  "skype": null,
  "updated_at": "2016-09-08T16:36:52",
  "longitude": null,
  "id": 3,
  "code": null
  "phone": null,
  "last_name": "Zanella",
  "address": null,
  "latitude": null,
  "email_secondary": null,
  "email": "filippo@sellf.be",
  "tags": [
    "Italy",
    "Treviso"
  ]
}
```

This endpoint allows to create a person.

### HTTP Request

`POST /people`




## Get a Specific Person

```shell
# Retrieve a person with ID 3
curl https://api.sellf.io/v2/people/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "website": null,
  "company_id": null,
  "fax": null,
  "first_name": "Filippo",
  "user_id": 4,
  "description": null,
  "title": "Founder of Sellf",
  "prospect_status": 2,
  "vat": null,
  "birthday": null,
  "mobile": null,
  "created_at": "2016-09-08T16:36:52",
  "skype": null,
  "updated_at": "2016-09-08T16:36:52",
  "longitude": null,
  "id": 3,
  "code": null,
  "phone": null,
  "last_name": "Zanella",
  "address": null,
  "latitude": null,
  "email_secondary": null,
  "email": "filippo@sellf.be",
  "tags": [
    "Italy",
    "Treviso"
  ]
}
```

This endpoint retrieves a specific person.

### HTTP Request

`GET /people/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the person to retrieve




## Update a Specific Person

```shell
# Update the person with ID 3
curl https://api.sellf.io/v2/people/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"title": "Ruby on Rails Developer",
              "email": "support@sellfapp.com"}"
```

> The above command returns JSON structured like this:

```json
{
  "website": null,
  "company_id": null,
  "fax": null,
  "first_name": "Filippo",
  "user_id": 4,
  "description": null,
  "title": "Ruby on Rails Developer",
  "prospect_status": 2,
  "vat": null,
  "birthday": null,
  "mobile": null,
  "created_at": "2016-09-08T16:36:52",
  "skype": null,
  "updated_at": "2016-09-08T16:42:30",
  "longitude": null,
  "id": 3,
  "code": null,
  "phone": null,
  "last_name": "Zanella",
  "address": null,
  "latitude": null,
  "email_secondary": null,
  "email": "support@sellfapp.com",
  "tags": [
    "Italy",
    "Treviso"
  ]
}
```

This endpoint allows to update a specific person.

### HTTP Request

`PUT /people/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the person to retrieve

<aside class="warning">
When you want to update the tags of a person be aware to include any existing tag, otherwise they will be fully replaced by the tags specified in the update request.
</aside>




## Delete a Specific Person

```shell
# Delete the person with ID 3
curl https://api.sellf.io/v2/people/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific person. Deleting a person implies that even all the associated entities are deleted, except for the associated company.


### HTTP Request

`DELETE /people/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the person to be deleted