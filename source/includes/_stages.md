# <a name="stages"></a>Stages

The Stages API gives you access to your team's stages, in read-only mode. You can retrieve a single stage as well as list of all stages associated with your team.

Sales stages are related to a specific pipeline and you can associate any number of [Deals](#deals). Once you sign up in Sellf, we create a primary stage by default, associated with four standard stages, editable based on your needs.

Sellf identify stages with an integer that determines their type: *active*, *won*, *lost*, *abandoned*. The match between the two follows the table below:

Type | Description
--------- | -------
0 | Active
1 | Won
2 | Lost
3 | Abandoned


You can add as many *active* stages as you want to each pipeline. The *active* stages concern deals that are still on going, i.e. neither won or lost/abandoned. Stages are sequentially positioned, following the flow of your sales process. Moreover, each stage is linked to a *win probability*, i.e. the likelihood (from 0 to 100) that a deal in that stage will be won.

In the `Settings > Deal > Pipelines` section of Sellf web app you can turn on the possibility of adding more pipelines and working with the probability of closing deals successfully. In this case, the default stages are automatically modified as stated in the table below:

Name | Position | Win Probability
--------- | ------- | ----------- | -----------
Lead | 1 | 5
Established contact | 2 | 10
Identified needs | 3 | 30
Proposal | 4 | 50
Negotiation | 5 | 70

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the stage
name | string | read | Name of the stage
win_probability | integer | read | The likelihood that a deal will be won, as percentage
position | integer | read | The position of the stage in the pipeline
pipeline_id | integer | read | Unique identifier of the associated pipeline
type | integer | read | Stage type (i.e. active, won, lost, abandoned)
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Stages

```shell
curl https://api.sellf.io/v1/stages -H "Api-Key: 44O7IrHnf5eJFGfyA0UOun6r6LUMpA==QEBTM2xsRk9yQXBpVDE0MSEhMTI2ISE="
```

> The above command returns JSON structured like this:

```json
{
  "meta": {
    "has_more": true,
    "object": "list"
  },
  "data": [
    {
      "name": "Qualified",
      "created_at": "2015-11-26T15:25:30.399687",
      "updated_at": "2016-04-28T10:40:00.508475",
      "pipeline_id": 1,
      "win_probability": 20,
      "position": 1,
      "type": 0,
      "id": 3
    },
    {
      "name": "Negotiation",
      "created_at": "2015-11-26T15:25:30.409568",
      "updated_at": "2016-05-11T11:58:02.441383",
      "pipeline_id": 1,
      "win_probability": 80,
      "position": 6,
      "type": 0,
      "id": 9
    }
  ]
}
```

This endpoint retrieves all stages of all pipelines. If you want to get the stages of a specific pipeline, you need to specify the `pipeline_id` as query param.

### HTTP Request

`GET /stages`

### Query Parameters

Parameter | Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `position`, `win_probability`, `created_at`, `updated_at`)
pipeline_id | Unique identifier of the pipeline to which stages belongs
type | Unique identifier of stage type (i.e. `0`, `1`, `2`, `3`)




## Get a Specific Stage

```shell
# Retrieve a stage with ID 9
curl https://api.sellf.io/v1/stages/9 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
  "name": "Negotiation",
  "created_at": "2015-11-26T15:25:30.409568",
  "updated_at": "2016-05-11T11:58:02.441383",
  "pipeline_id": 1,
  "win_probability": 80,
  "position": 6,
  "type": 0,
  "id": 9
}
```

This endpoint retrieves a specific stage according to the ID provided.

### HTTP Request

`GET /stages/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The unique identifier of the stage to retrieve
