# Pagination

Most of the list operations will be paginated. You can control pagination with the `page` parameter. Pages start at `1` and the first page will be returned if no page is specified. Data is limited to twenty elements per page.

The depicted example shows how to get the third page of all the team deals.

```shell
curl https://api.sellf.io/v1/deals?page=3 \
	-H "Api-Key: {YOUR_API_KEY}"
```
