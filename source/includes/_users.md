# <a name="users"></a>Users

The Users API gives you access to your team's users, in read-only mode. You can retrieve a single user as well as list of all users associated with your team.

Once you sign up in Sellf, we create a team by default, and a user with team management privileges (i.e. an administrator). By logging in as the team administrator, you can invite as many additional users as you need, if you purchase at least a [business](https://app.sellf.io/plans) plan.

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | Unique identifier of the user
email | string | Email address of the user
name | string | Name of the user
role | string | Role of the user <br> (i.e. `administrator`, `manager`, `collaborator`)


## Get All Users

```shell
curl https://api.sellf.io/v1/users -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
	  "id": 1,
	  "email": "filippo@sellfapp.com",
	  "role": 0,
	  "name": "Filippo Zanella"
  },
  {
	  "id": 2,
	  "email": "giovanni@sellfapp.com",
	  "role": 1,
	  "name": "Giovanni Barillari"
  },
  { ... }
]
```

This endpoint retrieves all users.

### HTTP Request

`GET /users`




## Get a Specific User

```shell
# Retrieve a user with ID 3
curl https://api.sellf.io/v1/users/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "email": "filippo@sellfapp.com",
  "role": 0,
  "name": "Filippo Zanella"
}
```

This endpoint retrieves a specific user according to the ID provided.

### HTTP Request

`GET /users/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve
