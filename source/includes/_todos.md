# <a name="todos"></a>Todos

The Todos API allows you to get, create, update and delete your todos. Each todo can be associated to one [Company](#companies), one [Person](#people), one [User](#users) and one [Deal](#deals).

Sellf identifies the type of the todo with a string that determines a corresponding action: *call*, *meeting*, *email*. The match between the two follows the table below:

Action | Description
--------- | -------
call | Phone call
email | Email
meeting | Meeting

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the todo
**name** | string | write | Name of the todo
description | string | write | Content of the todo
person_id | integer | write | Unique identifier of the person related to the todo
company_id | integer | write | Unique identifier of the company related to the todo
deal_id | integer | write | Unique identifier of the deal concerning the todo
assignee_id | integer | write | Unique identifier of the user to whom the todo is assigned
assignator_id | integer | write | Unique identifier of the user that assignes the todo
completer_id | integer | write | Unique identifier of the user that completed the todo
action | integer | write | Type of todo
address | string | write | Place linked to the todo
done | boolean | write | Completion of the todo
done_at | datetime | write | Date of completion
is_overdue | boolean | read | It indicates wether the todo is overdue or not
overdue_at | datetime | write | Date of overdue
overdue_frequency | datetime | write | Frequency of recurring overdue
stop_overdue_at | datetime | write | Final date for recurrency 
**user_id** | integer | write | Unique identifier of the user that ownes the todo
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Todos

```shell
curl https://api.sellf.io/v2/todos?sort_by=-name -H "Api-Key: {YOUR_API_KEY}"
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
        "assignator_id": 4,
        "assignee_id": null,
        "is_overdue": false,
        "user_id": 4,
        "description": null,
        "created_at": "2018-09-24T14:46:47.000000",
        "done_at": null,
        "updated_at": "2018-09-27T07:55:06.000000",
        "company_id": null,
        "deal_id": null,
        "person_id": null,
        "overdue_at": "2018-09-28T08:00:00.000000",
        "completer_id": null,
        "done": false,
        "address": null,
        "action": "meeting",
        "overdue_frequency": "never",
        "stop_overdue_at": null,
        "id": 3,
        "name": "My todo"
    }
  ]
}
```

This endpoint retrieves all todos.

### HTTP Request

`GET /todos`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `done_at`, `overdue_at`, `done`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the todo is owned by
person_id | Unique identifier of the person with whom the todo is associated
company_id | Unique identifier of the company with whom the todo is associated
deal_id | Unique identifier of the deal with whom the todo is associated
assignator_id | Unique identifier of the user that assignes the todo
assignee_id | Unique identifier of the user to whom the todo is assigned
name | A string containing or matching the name of the todo


## Create a todo

```shell
# Create a new todo
curl https://api.sellf.io/v2/todos \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"name": "Attend meeting",
                "action": "meeting",
                "description": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
                "person_id": 15,
                "deal_id": 9,
                "user_id": 4}"
```

> The above command returns JSON structured like this:

```json
{
  "name": "Attend meeting",
  "body": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2018-09-21T10:32:49.000000",
  "updated_at": "2018-09-21T10:32:49.000000",
  "user_id": 4,
  "id": 3
}
```

This endpoint allows to create a todo.

### HTTP Request

`POST /todos`




## Get a Specific Todo

```shell
# Retrieve a todo with ID 7
curl https://api.sellf.io/v2/todos/7 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "title": "Sample todo",
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

This endpoint retrieves a specific todo.

### HTTP Request

`GET /todos/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the todo to retrieve




## Update a Specific Todo

```shell
# Update a todo with ID 7
curl https://api.sellf.io/v2/todos/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"name": "Debriefing with teammates"}"
```

> The above command returns JSON structured like this:

```json
{
  "name": "Debriefing with teammates",
  "description": "Lorem ipsum dolor sit amet, consectetur adipisci elit...",
  "person_id": 15,
  "company_id": null,
  "deal_id": 9,
  "created_at": "2018-09-21T10:32:49.000000",
  "updated_at": "2018-09-21T10:32:49.000000",
  "user_id": 4,
  "id": 7
}
```

This endpoint allows to update a specific todo.

### HTTP Request

`PUT /todos/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the todo to retrieve




## Delete a Specific Note

```shell
# Delete the todo with ID 7
curl https://api.sellf.io/v2/todos/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific todo.


### HTTP Request

`DELETE /todos/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the todo to be deleted