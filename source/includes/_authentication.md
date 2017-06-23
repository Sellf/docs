# Authentication

Sellf uses API keys to allow access to the API. Each Sellf team has its own API key that gives full access to the data of the team.

An API key can be obtained by (registering or) signing in to [sellf.io](https://www.sellf.io), and then going to `Settings > API`. If no API key exists, you can generate one clickin on the `GENERATE` button.

Sellf expects for the API key to be included in all API requests to the server in a header that looks like the example in the right bar.

```shell
curl https://api.sellf.io/v2/deals -H "Api-Key: {YOUR_API_KEY}"
```

> Make sure to replace `{YOUR_API_KEY}` with your API key.


<aside class="notice">
You must replace <code>{YOUR_API_KEY}</code> with your personal API key.
</aside>

<aside class="warning">
<strong>Use HTTPS only!</strong> Any HTTP requests will be ignored.
</aside>


