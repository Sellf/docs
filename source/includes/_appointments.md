# <a name="appointments"></a>Appointments

The Appointments API allows you to get, create, update and delete your appointments. Each appointment can be associated to one or more [Companies](#companies), one or more [People](#people), one or more [Users](#users) and one [Deal](#deals).

Sellf identify the type of the appointment with a string that determines a corresponding action: *call*, *meeting*, *lunch*, *dinner*, *presentation*. The match between the two follows the table below:

Action | Description
--------- | -------
call | Phone call
meeting | Meeting
lunch | Lunch
dinner | Dinner
presentation | Presentation

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the appointment
name | string | write | Name of the appointment
action | string | write | Type of appointment
start_at | datetime | Moment in which the appointment starts
end_at | datetime | Moment in which the appointment ends
remind_at | datetime | At what time the user needs to be notified of the upcoming appointment
is_all_day | boolean | It determines whether the appointment lasts all day or less
address | string | write | Place in which the appointment occurs
description | string | write | Appointment's notes
deal_id | integer | write | Unique identifier of the deal concerning the appointment
user_id | integer | write | Unique identifier of the user that the appointment is assigned to
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Appointments

```shell
curl https://api.sellf.io/v1/appointments?sort_by=-name -H "Api-Key: {YOUR_API_KEY}"
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
      "start_at": "2016-09-15T01:13:15.608045",
      "name": "Contract negotiation",
      "deal_id": null,
      "created_at": "2016-09-23T13:43:30.826603",
      "address": "via Sile 41, 31056, Roncade (TV)",
      "updated_at": "2016-09-23T13:43:30.826603",
      "end_at": "2016-09-23T14:10:45.787592",
      "remind_at": null,
      "is_all_day": true,
      "action": "meeting",
      "user_id": 4,
      "id": 3,
      "description": null
    }
  ]
}
```

This endpoint retrieves all appointments.

### HTTP Request

`GET /appointments`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `start_at`, `end_at`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the appointment is owned by
deal_id | Unique identifier of the deal with whom the appointment is associated
name | A string containing or matching the name of the appointment




## Create an Appointment

```shell
# Create a new appointment
curl https://api.sellf.io/v1/appointments \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"name": "Debriefing",
              "start_at": "2016-09-08T16:25:00",
              "end_at": "2016-09-08T16:50:00",
              "deal_id": 9
              "user_id": 4}"
```

> The above command returns JSON structured like this:

```json
{
  "start_at": "2016-09-08T16:25:00.000000",
  "name": "Debriefing",
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "address": null,
  "updated_at": "2017-02-21T10:32:49.000000",
  "end_at": "2016-09-08T16:50:00.000000",
  "remind_at": null,
  "is_all_day": false,
  "action": null,
  "user_id": 4,
  "id": 7,
  "description": null
}
```

This endpoint allows to create an appointment.

### HTTP Request

`POST /appointments`




## Get a Specific Appointment

```shell
# Retrieve a appointment with ID 7
curl https://api.sellf.io/v1/appointments/7 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "start_at": "2016-09-08T16:25:00.000000",
  "name": "Debriefing",
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "address": null,
  "updated_at": "2017-02-21T10:32:49.000000",
  "end_at": "2016-09-08T16:50:00.000000",
  "remind_at": null,
  "is_all_day": false,
  "action": null,
  "user_id": 4,
  "id": 7,
  "description": null
}
```

This endpoint retrieves a specific appointment.

### HTTP Request

`GET /appointments/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the appointment to retrieve




## Update a Specific Appointment

```shell
# Update a appointment with ID 7
curl https://api.sellf.io/v1/appointments/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"name": "Debriefing with teammates",
              "start_at": "2016-10-08T16:25:00"}",
              "end_at": "2016-10-08T16:50:00"}"
```

> The above command returns JSON structured like this:

```json
{
  "start_at": "2016-10-08T16:25:00.000000",
  "name": "Debriefing with teammates",
  "deal_id": 9,
  "created_at": "2017-02-21T10:32:49.000000",
  "address": null,
  "updated_at": "2017-02-21T10:40:05.000000",
  "end_at": "2016-10-08T16:50:00.000000",
  "remind_at": null,
  "is_all_day": false,
  "action": null,
  "user_id": 4,
  "id": 7,
  "description": null
}
```

This endpoint allows to update a specific appointment.

### HTTP Request

`PUT /appointments/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the appointment to retrieve




## Delete a Specific Appointment

```shell
# Delete the appointment with ID 7
curl https://api.sellf.io/v1/appointments/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific appointment.


### HTTP Request

`DELETE /appointments/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the appointment to be deleted