# <a name="peoples"></a>People

The People API allows you to get, create, update and delete your people. Each person can be associated to a [Company](#companies) and one or more [Deals](#deals).

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | Unique identifier of the person
first_name | string | First name of the person
last_name | string | Last name of the person
title | string | Role in the company
website | string | Website
email | string | Primary email
email_secondary | string | Secondary email
phone | string | Office or home number
mobile | string | Mobile phone number
fax | string | Fax number
facebook | string | Facebook page
skype  | string | Skype nickname
address | string | Office or home address of the person
user_id | integer | Unique identifier of the user that the person is assigned to
company_id | integer | Unique identifier of the person's company
tags | array | An array of tags for a person




## Get All People

```shell
curl https://api.sellf.io/v1/people -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
	  "first_name": "Anthony",
	  "last_name": "Mc Gregor",
	  "title": "CEO",
	  "email": "anthony@acme.org"
  },
  {
    "id": 2,
	  "first_name": "Paul",
	  "last_name": "Hogan",
	  "title": "Manager",
	  "email": "paul.hogan@comma.com"
  },
  { ... }
]
```

This endpoint retrieves all people.

### HTTP Request

`GET /people`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sort | name | Column to sort by <br> e.g. name
suid | ? | Unique identifier of the user the person is owned by




## Create a Person

```shell
# Create a new person
curl https://api.sellf.io/v1/people \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{\"first_name\": \"Filippo\", \"last_name\": \"Zanella\", \"title\": \"Founder of Sellf\", \"email\": \"filippo@sellfapp.com\", \"tags\": [\"Italy\", \"Treviso\"]}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "first_name": "Filippo",
  "last_name": "Zanella",
  "title": "Founder of Sellf",
  "email": "filippo@sellfapp.com",
  "tags": ["Italy", "Treviso"]
}
```

This endpoint allows to create a person.

### HTTP Request

`POST /people`




## Get a Specific Person

```shell
# Retrieve a person with ID 3
curl https://api.sellf.io/v1/people/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "first_name": "Filippo",
  "last_name": "Zanella",
  "title": "Founder of Sellf",
  "email": "filippo@sellfapp.com",
  "tags": ["Italy", "Treviso"]
}
```

This endpoint retrieves a specific person.

### HTTP Request

`GET /people/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the person to retrieve




## Update a Specific Person

```shell
# Update a person with ID 3
curl https://api.sellf.io/v1/people/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{\"title\": \"Ruby on Rails Developer\", \"email\": \"support@sellfapp.com\"}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "first_name": "Filippo",
  "last_name": "Zanella",
  "title": "Ruby on Rails Developer",
  "email": "support@sellfapp.com",
  "tags": ["Italy", "Treviso"]
}
```

This endpoint allows to update a specific person.

<aside class="warning">
In order to modify tags associated to a person, you need to supply the entire set. Tags are replaced every time they are part of a request.
</aside>

### HTTP Request

`PUT /people/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the person to retrieve




## Delete a Specific Person

```shell
# Delete a person with ID 3
curl https://api.sellf.io/v1/people/3 \
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
ID | The unique identifier of the person to retrieve