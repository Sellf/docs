# <a name="appointment_people"></a>Appointment People

The Appointment People API allows you to get, add or remove people associated to your appointments.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
**person_id** | integer | write | Unique identifier of the person related to the appointment
updated_at | datetime | read | Date of last edit


## Get All Appointment's People

```shell
curl https://api.sellf.io/v1/appointments/4 -H "Api-Key: {YOUR_API_KEY}"
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
      "person_id": 12,
      "updated_at": "2017-02-21T10:51:39.467513"
    }
  ]
}
```

This endpoint retrieves all appointment's people.

### HTTP Request

`GET /appointments/:appointment_id/people`

### URL Parameters

Parameter | Description
--------- | -----------
appointment_id | The unique identifier of the chosen appointment




## Add a Person to an Appointment

```shell
# Add a person to an appointment
curl https://api.sellf.io/v1/appointments/4/people \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"person_id": 15}"
```

> The above command returns JSON structured like this:

```json
{
  "person_id": 15,
  "updated_at": "2017-02-21T10:51:39.467513"
}
```

This endpoint allows to associate a person to an appointment.

### HTTP Request

`POST /appointments/:appointment_id/people`

### URL Parameters

Parameter | Description
--------- | -----------
appointment_id | The unique identifier of the chosen appointment




## Remove a Person from an Appointment

```shell
# Remove the person with ID 15 from the appointment with ID 4
curl https://api.sellf.io/v1/appointments/4/people/15 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint removes the association of a person with an appointment.


### HTTP Request

`DELETE /appointments/:appointment_id/people/:person_id`

### URL Parameters

Parameter | Description
--------- | -----------
appointment_id | The unique identifier of the chosen appointment
person_id | The unique identifier of the chosen person