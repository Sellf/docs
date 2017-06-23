# <a name="appointment_users"></a>Appointment Users

The Appointment Users API allows you to get, add or remove users associated to your appointments. A user is a guest, that is, the appointments in which it is invited are shown in its calendar.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
**user_id** | integer | write | Unique identifier of the user related to the appointment
updated_at | datetime | read | Date of last edit


## Get All Appointment's Users

```shell
curl https://api.sellf.io/v2/appointments/4 -H "Api-Key: {YOUR_API_KEY}"
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
      "user_id": 12,
      "updated_at": "2017-02-21T10:51:39.467513"
    }
  ]
}
```

This endpoint retrieves all appointment's users.

### HTTP Request

`GET /appointments/:appointment_id/users`

### URL Parameters

Parameter | Description
--------- | -----------
appointment_id | The unique identifier of the chosen appointment




## Add a User to an Appointment

```shell
# Add a user to an appointment
curl https://api.sellf.io/v2/appointments/4/users \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"user_id": 15}"
```

> The above command returns JSON structured like this:

```json
{
  "user_id": 15,
  "updated_at": "2017-02-21T10:51:39.467513"
}
```

This endpoint allows to associate a user to an appointment.

### HTTP Request

`POST /appointments/:appointment_id/users`

### URL Parameters

Parameter | Description
--------- | -----------
appointment_id | The unique identifier of the chosen appointment




## Remove a User from an Appointment

```shell
# Remove the user with ID 15 from the appointment with ID 4
curl https://api.sellf.io/v2/appointments/4/users/15 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint removes the association of a user with an appointment.


### HTTP Request

`DELETE /appointments/:appointment_id/users/:user_id`

### URL Parameters

Parameter | Description
--------- | -----------
appointment_id | The unique identifier of the chosen appointment
user_id | The unique identifier of the chosen user