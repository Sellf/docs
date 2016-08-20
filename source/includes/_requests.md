# Requests

As stated before, the Sellf API is accessed from the secure domain `https://api.sellf.io`. All data is sent and received in the JSON format.

### Pagination

```shell
curl https://api.sellf.io/v1/deals?page=3 \
	-H "Api-Key: {YOUR_API_KEY}"
```

Most of the list operations are paginated. You can control it with the `page` parameter. Pages start at `1` and the first page will be returned if no page is specified. Data is limited to `20` elements per page.

The depicted example shows how to get the third page of all the team deals.


### Sorting

```shell
# To get a list of deals sorted by estimated value in descending order
curl https://api.sellf.io/v1/deals?sort_by=-estimated_value \
	-H "Api-Key: {YOUR_API_KEY}"
```

You can control in what order, according to a criteria, how to sort listed elements using the query parameter `sort_by`.

The default sort order is ascending. If you want to sort the elements in descending order, append a minus sign to the field.
