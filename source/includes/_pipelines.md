# <a name="pipelines"></a>Pipelines

The Pipelines API gives you access to your team's pipelines, in read-only mode. You can retrieve a single pipeline as well as list of all pipelines associated with your team.

Sales pipelines consist of a sequence of [Stages](#stages) in which the deals can be placed. Once you sign up in Sellf, we create a primary pipeline by default, associated with four standard stages: `In progress`, `Won`, `Lost`, `Abandoned`. You can add as many pipelines as you want. Pipelines can be characterized by monetary or quantitative values based on you needs.

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | Unique identifier of the pipeline
name | string | Name of the pipeline
type | string | Pipeline type <br> (i.e. `money`, `quantity`)


## Get All Pipelines

```shell
curl https://api.sellf.io/v1/pipelines -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
	  "id": 1,
	  "name": "Sales Pipeline",
	  "type": "money"
  },
  {
	  "id": 2,
	  "name": "Stocks Placed",
	  "type": "quantity"
  },
  { ... }
]
```

This endpoint retrieves all pipelines.

### HTTP Request

`GET /pipelines`




## Get a Specific Pipeline

```shell
# Retrieve a pipeline with ID 3
curl https://api.sellf.io/v1/pipelines/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
  {
	  "id": 3,
	  "name": "Sales Pipeline",
	  "type": "money"
  }
```

This endpoint retrieves a specific pipeline according to the ID provided.

### HTTP Request

`GET /pipelines/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the pipeline to retrieve
