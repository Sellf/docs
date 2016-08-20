# Pagination

Most of the list operations will be paginated. You can control pagination with the `page` and `per_page` parameters. Pages start at `1` and the first page will be returned if no page is specified.

The depicted example shows how to get the third page of all the team deals, limited to fifty deals per page.

```shell
curl https://api.sellf.io/v1/deals?page=3&per_page=50 \
	-H "Api-Key: {YOUR_API_KEY}"
```
