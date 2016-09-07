# <a name="companies"></a>Companies

The Companies API allows you to get, create, update and delete your companies. Each company can be associated to a [Company](#companies) and one or more [Deals](#deals).

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | Unique identifier of the company
first_name | string | First name of the company
last_name | string | Last name of the company
title | string | Role in the company
website | string | Website
email | string | Primary email
email_secondary | string | Secondary email
phone | string | Office or home number
mobile | string | Mobile phone number
fax | string | Fax number
facebook | string | Facebook page
skype  | string | Skype nickname
address | string | Office or home address of the company
user_id | integer | Unique identifier of the user that the company is assigned to
company_id | integer | Unique identifier of the company's company
tags | array | An array of tags for a company




## Get All Companies

```shell
curl https://api.sellf.io/v1/companies -H "Api-Key: {YOUR_API_KEY}"
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

This endpoint retrieves all companies.

### HTTP Request

`GET /companies`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sort | name | Column to sort by <br> e.g. name
suid | ? | Unique identifier of the user the company is owned by




## Create a Company

```shell
# Create a new company
curl https://api.sellf.io/v1/companies \
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

This endpoint allows to create a company.

### HTTP Request

`POST /companies`




## Get a Specific Company

```shell
# Retrieve a company with ID 3
curl https://api.sellf.io/v1/companies/3 -H "Api-Key: {YOUR_API_KEY}"
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

This endpoint retrieves a specific company.

### HTTP Request

`GET /companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the company to retrieve




## Update a Specific Company

```shell
# Update a company with ID 3
curl https://api.sellf.io/v1/companies/3 \
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

This endpoint allows to update a specific company.

<aside class="warning">
In order to modify tags associated to a company, you need to supply the entire set. Tags are replaced every time they are part of a request.
</aside>

### HTTP Request

`PUT /companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the company to retrieve




## Delete a Specific Company

```shell
# Delete a person with ID 3
curl https://api.sellf.io/v1/companies/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific person. Deleting a person implies that even all the associated entities are deleted, except for the associated company.


### HTTP Request

`DELETE /companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the person to retrieve
