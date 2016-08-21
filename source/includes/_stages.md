# <a name="stages"></a>Stages

The Stages API gives you access to your team's stages, in read-only mode. You can retrieve a single stage as well as list of all stages associated with your team.

Sales stages are related to a specific pipeline and you can associate any number of [Deals](#deals). Once you sign up in Sellf, we create a primary stage by default, associated with four standard stages, editable based on your needs. You can add as many *active* stages as you want to each pipeline. The *active* stages concern deals that are still on going, i.e. neither won or lost/abandoned. Stages are sequentially positioned, following the flow of your sales process. Moreover, each stage is linked to a *win probability*, i.e. the likelihood (from 0 to 100) that a deal in that stage will be won.

In the `Settings > Deal > Pipelines` section of Sellf apps you can turn on the possibility of adding more pipelines and working with the probability of closing deals successfully. In this case, the default stages are automatically modified as stated in the table below:

Name | Status | Position | Win Probability
--------- | ------- | ----------- | -----------
Lead | active | 1 | 10
Established contact | active | 2 | 25
Identified needs | active | 3 | 35
Proposal | active | 4 | 50
Negotiation | active | 5 | 75
Won | won | 6 | n/a
Lost | lost | 7 | n/a
Abandoned | abandoned | 8 | n/a

### Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | Unique identifier of the stage
name | string | Name of the stage
win_probability | integer | The likelihood that a deal will be won, as percentage
position | integer | The position of the stage in the pipeline
pipeline_id | integer | Unique identifier of the associated pipeline


## Get All Stages

```shell
curl https://api.sellf.io/v1/stages -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
[
  {
	  "id": 1,
	  "name": "Lead",
	  "win_probability": "10",
	  "position": 1,
	  "pipeline_id": 2
  },
  {
	  "id": 9,
	  "name": "Won",
	  "win_probability": "100",
	  "position": 6,
	  "pipeline_id": 2
  },
  { ... }
]
```

This endpoint retrieves all stages of all pipelines.

### HTTP Request

`GET /stages`




## Get a Specific Stage

```shell
# Retrieve a stage with ID 3
curl https://api.sellf.io/v1/stages/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
  {
	  "id": 3,
	  "name": "Identified needs",
	  "win_probability": "35",
	  "position": 3,
	  "pipeline_id": 2
  }
```

This endpoint retrieves a specific stage according to the ID provided.

### HTTP Request

`GET /stages/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the stage to retrieve
