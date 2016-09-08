# <a name="pipelines"></a>Pipelines

The Pipelines API gives you access to your team's pipelines, in read-only mode. You can retrieve a single pipeline as well as list of all pipelines associated with your team.

Sales pipelines consist of a sequence of [Stages](#stages) in which the deals can be placed. Once you sign up in Sellf, we create a primary pipeline by default, associated with four standard stages: `In progress`, `Won`, `Lost`, `Abandoned`. You can add as many pipelines as you want. Pipelines can be characterized by monetary or quantitative values based on you needs.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the pipeline
name | string | read | Name of the pipeline
type | string | read | Pipeline type <br> (i.e. `money`, `quantity`)


## Get All Pipelines

```shell
curl https://api.sellf.io/v1/pipelines -H "Api-Key: {YOUR_API_KEY}"
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
      "created_at": "2015-11-26T15:25:30.389544",
      "type": "cash",
      "id": 1,
      "name": "Sales Pipeline",
      "updated_at": "2016-05-03T14:19:53.605326"
    },
    {
      "created_at": "2016-01-04T09:29:12.960430",
      "type": "quantity",
      "id": 2,
      "name": "Sold Items",
      "updated_at": "2016-01-25T10:55:13.818873"
    }
  ]
}
```

This endpoint retrieves all pipelines.

### HTTP Request

`GET /pipelines`

Parameter | Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `created_at`, `updated_at`)
type | Type of pipeline in terms of being monetary or quantitative <br> (i.e. `cash`, `quantity`)




## Get a Specific Pipeline

```shell
# Retrieve a pipeline with ID 2
curl https://api.sellf.io/v1/pipelines/2 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "created_at": "2016-01-04T09:29:12.960430",
  "type": "quantity",
  "id": 2,
  "name": "Sold Items",
  "updated_at": "2016-01-25T10:55:13.818873"
}
```

This endpoint retrieves a specific pipeline according to the ID provided.

### HTTP Request

`GET /pipelines/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the pipeline to retrieve
