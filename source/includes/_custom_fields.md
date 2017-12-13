# <a name="custom_fields"></a>Custom Fields

The Custom Fields API gives you access to your team's custom fields for [People](#people), [Companies](#companies) and [Deals](#deals), in read-only mode. You can retrieve a list of all custom fields of your team for a specific entity.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
entity_type | string | read | Entity type that the custom field belongs to
key | string | read | Unique identifier of the custom field (used for APIs calls)
type | string | read | Data type of the custom field
label | string | read | Personalized name of the custom field
is_multiple | boolean | read | Determine if the custom field allows multiple selections
extras | string | read | Any extra informations (e.g. the values of a dropdown field)


## Get All Custom Fields

```shell
curl https://api.sellf.io/v2/custom_fields?entity_type=contact -H "Api-Key: {YOUR_API_KEY}"
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
        "entity_type": "contact",
        "label": "Category",
        "is_multiple": false,
        "extras": {},
        "key": "category",
        "type": "text"
    },
    {
        "entity_type": "contact",
        "label": "Policy expiration date",
        "is_multiple": false,
        "extras": {},
        "key": "policy_expiration_date",
        "type": "date"
    }
  ]
}
```

This endpoint retrieves all deals' custom fields.

### HTTP Request

`GET /custom_fields`

### Query Parameters

Parameter | Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `key`, `created_at`, `updated_at`)
entity_type | Entity to filter by <br> (i.e. `contact`, `company`, `deal`)
