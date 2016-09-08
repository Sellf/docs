# <a name="users"></a>Users

The Users API gives you access to your team's users, in read-only mode. You can retrieve a single user as well as list of all users associated with your team.

Once you sign up in Sellf, we create a team by default, and a user with team management privileges (i.e. an administrator). By logging in as the team administrator, you can invite as many additional users as you need, if you purchase at least a [business](https://app.sellf.io/plans) plan.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the user
email | string | read | Email address of the user
name | string | read | Name of the user
created_at | datetime | read | Date of creation


## Get All Users

```shell
curl https://api.sellf.io/v1/users -H "Api-Key: {YOUR_API_KEY}"
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
      "created_at": "2015-11-26T15:25:29",
      "id": 1,
      "name": "Filippo Zanella",
      "email": "filippo@sellf.be"
    },
    {
      "created_at": "2016-08-24T18:25:13",
      "id": 2,
      "name": "Giovanni Barillari",
      "email": "giovanni@sellf.be"
    }
  ]
}
```

This endpoint retrieves all users.

### HTTP Request

`GET /users`




## Get a Specific User

```shell
# Retrieve a user with ID 2
curl https://api.sellf.io/v1/users/2 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "created_at": "2016-08-24T18:25:13",
  "id": 2,
  "name": "Giovanni Barillari",
  "email": "giovanni@sellf.be"
}
```

This endpoint retrieves a specific user according to the ID provided.

### HTTP Request

`GET /users/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the user to retrieve
