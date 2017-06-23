# Requests

As stated before, the Sellf API is accessed from the secure domain `https://api.sellf.io`. All data is sent and received in the JSON format.

### Pagination

```shell
curl https://api.sellf.io/v2/deals?page=3 \
	-H "Api-Key: {YOUR_API_KEY}"
```

Most of the list operations are paginated. You can control it with the `page` parameter. Pages start at `1` and the first page will be returned if no page is specified. Data is limited to `20` entities per page.

The depicted example shows how to get the third page of all the team deals.


### Sorting

```shell
# To get a list of deals sorted by estimated value in descending order
curl https://api.sellf.io/v2/deals?sort_by=-estimated_value \
	-H "Api-Key: {YOUR_API_KEY}"
```

You can control in what order, according to a criteria, how to sort listed entities using the query parameter `sort_by`.

The default sort order is ascending. If you want to sort the entities in descending order, append a minus sign to the field.


### Ownership

In general, the identifier of a user needs to be specified when you want to add a new entity (e.g. a deal or a contact), via the `user_id` field. If you want to list a set of entities (e.g. all the deals owned by a specific user) you can do that via the `user_id` query parameter; be aware that if you do not specify any `user_id`, the APIs will return all the entities in your team.


### Permission

Each entity in Sellf has some attributes that are read-only and attributes that can be both retrieved and overwritten, via REST calls. In each section you'll find a table in which for each entity field is specified if it is possibile not only to read it but also sent it to Sellf through POST or PUT methods.


### Required fields

One or more attributes are usually required when creating or updating an entity. These required fields are highlighted with a bold font within each attributes table that you can find at the beginning of each entity section.


### Query language

Each entity in Sellf has some attributes that can be queried to apply filters on retrieval requests. The allowed operators related to the Sellf query language are listed below:

| Operator | Description | Comparison |
| --- | --- | --- |
| eq | query for *value equal to* | single term |
| neq | query for *value differs from* | single term |
| lt | query for *value less than* | single term |
| gt | query for *value greater than* | single term |
| lte | query for *value less than or equal to* | single term |
| gte | query for *value greater than or equal to* | single term |
| in | query for *value is contained into* | array of terms |
| contains | query for *value contains* | array of terms |

The rule to apply the above mentioned operators is the following:

`<attribute>:<operator>=<comparison>`

where `<comparison>` can be a single value or an array of values (e.g. `user_id:neq=12` or `tags:contains=["customer", "insolvent"]`).

<aside class="notice">
Note that the system implicitly use `and` connection between queries, and `eq` operator as default argument if not specified (e.g. `user_id:23` is the implicit form of `user_id:eq=23`).
</aside>

For entities which have *nested* objects (if queries are allowed) you should use the dot notation, (e.g. `custom_fields.<key>`).

Be aware that some operators applies to specific attributes' types (e.g. you cannot use numeric operators on string types).




