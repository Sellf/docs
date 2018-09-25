# <a name="files"></a>Files

The FIles API allows you to get, create, update and delete files in Sellf.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the file
**name** | string | write | Name of the file
**is_public** | boolean | write | File permissions
url | string | write | Url of the file
size | integer | read | File size
type | string | read | File type
parent_id | integer | write | Unique identifier of the parent folder (if none is specified the team's main folder is automatically set)
**user_id** | integer | write | Unique identifier of the user that ownes the file
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit



## Get All Files

```shell
curl https://api.sellf.io/v2/files?sort_by=-name -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
    "meta": {
        "has_more": false,
        "total_objects": 1,
        "object": "list"
    },
    "data": [
        {
            "user_id": 7,
            "name": "file.jpg",
            "url": "https://sellf-storage.s3.eu-central-1.amazonaws.com/1234/dd3e44fgdfr5dffe4y56r5gu/file.jpg",
            "created_at": "2018-04-24T15:31:31.000000",
            "updated_at": "2018-04-24T15:31:32.000000",
            "parent_id": 1,
            "is_folder": false,
            "is_public": false,
            "type": "image/jpeg",
            "id": 2,
            "size": 35
        }
    ]
}
```

This endpoint retrieves all files.

### HTTP Request

`GET /files`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the file is owned by
name | A string containing or matching the name of the file
is_public | A boolean matching the desired permission
type | A string matching the desired file type



## Create a File

```shell
# Create a new file
curl https://api.sellf.io/v2/files \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"name": "file.jpg",
                "url": "https://example.com/file.jpg",
                "parent_id": 1,
                "is_public": false,
                "user_id": 7}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "file.jpg",
    "user_id": 7,
    "url": "https://example.com/file.jpg",
    "created_at": "2018-06-06T15:31:10.000000",
    "updated_at": "2018-06-14T10:04:10.000000",
    "parent_id": 3,
    "is_folder": false,
    "is_public": false,
    "type": "image/jpg",
    "size": 0,
    "id": 4
}
```

This endpoint allows to create a file.

<aside class="warning">
When you create a file, the system will process the request asycronously and return a placeholder json for your file. Depending on the size of the file the system may take some time to process your request. During this time, and untill the process is complete, you won't be able to see your file in the file list. Once the file is successfully created it will automatically be available with the `GET /storage` API, with the definitive url of your Sellf storage container.
</aside>

### HTTP Request

`POST /files`



## Get a Specific File

```shell
# Retrieve a file with ID 1926
curl https://api.sellf.io/v2/files/1926 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
    "user_id": 7,
    "name": "file.jpeg",
    "url": "https://sellf-storage-dev.s3.eu-central-1.amazonaws.com/1234/dd3e44fgdfr5dffe4y56r5gu/file.jpeg",
    "created_at": "2018-07-20T10:36:12.000000",
    "updated_at": "2018-07-20T10:36:13.000000",
    "parent_id": 1,
    "is_public": true,
    "type": "image/jpeg",
    "size": 11,
    "id": 1926
}
```

This endpoint retrieves a specific file.

### HTTP Request

`GET /files/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the file to retrieve



## Update a Specific File

```shell
# Update a file with ID 26
curl https://api.sellf.io/v2/files/1926 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"name": "FILE.jpg"}"
```

> The above command returns JSON structured like this:

```json
{
    "user_id": 7,
    "name": "FILE.jpeg",
    "url": "https://sellf-storage-dev.s3.eu-central-1.amazonaws.com/1234/dd3e44fgdfr5dffe4y56r5gu/file.jpeg",
    "created_at": "2018-07-20T10:36:12.000000",
    "updated_at": "2018-07-20T10:36:13.000000",
    "parent_id": 1,
    "is_folder": false,
    "is_public": true,
    "type": "image/jpeg",
    "size": 11,
    "id": 1926
}
```

This endpoint allows to update a specific file.

### HTTP Request

`PUT /files/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the file to update



## Delete a Specific File

```shell
# Delete the todo with ID 7
curl https://api.sellf.io/v2/files/7 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific file.


### HTTP Request

`DELETE /files/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the file to be deleted



# <a name="files"></a>Folders

The FIles API allows you to get, create, update and delete folders in Sellf.

### Attributes

Parameter | Type | Permission | Description
--------- | ------- | ------- | -----------
id | integer | read | Unique identifier of the folder
**name** | string | write | Name of the folder
**is_public** | boolean | write | Folder permissions
parent_id | integer | write | Unique identifier of the parent folder (if none is specified the team's main folder is automatically set)
**user_id** | integer | write | Unique identifier of the user that ownes the folder
created_at | datetime | read | Date of creation
updated_at | datetime | read | Date of last edit


## Get All Folders

```shell
curl https://api.sellf.io/v2/folders?sort_by=-name -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
    "meta": {
        "has_more": false,
        "total_objects": 1,
        "object": "list"
    },
    "data": [
        {    
            "user_id": 7,
            "name": "Home",
            "created_at": "2018-04-06T13:26:09.000000",
            "updated_at": "2018-04-06T13:26:09.000000",
            "parent_id": null,
            "is_public": true,
            "type": "folder",
            "id": 1
        }
    ]
}
```

This endpoint retrieves all folders.

### HTTP Request

`GET /folders`

### Query Parameters

Parameter| Description
--------- | -----------
sort_by | Column to sort by <br> (i.e. `id`, `name`, `created_at`, `updated_at`)
user_id | Unique identifier of the user the folder is owned by
name | A string containing or matching the name of the folder
is_public | A boolean matching the desired permission
       


## Create a folder

```shell
# Create a new folder
curl https://api.sellf.io/v2/folders \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X POST -d "{"name": "Private subfolder",
                "parent_id": 1,
                "is_public": false,
                "user_id": 7}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "Private subfolder",
    "user_id": 7,
    "created_at": "2018-06-06T15:31:10.000000",
    "updated_at": "2018-06-14T10:04:10.000000",
    "parent_id": 1,
    "is_public": false,
    "type": "folder",
    "id": 3
}
```

This endpoint allows to create a folder.

### HTTP Request

`POST /folders`



## Get a Specific Folders

```shell
# Retrieve a file with ID 3
curl https://api.sellf.io/v2/folders/3 -H "Api-Key: {YOUR_API_KEY}"
```

> The above command returns JSON structured like this:

```json
{
    "user_id": 7,
    "name": "Folder",
    "created_at": "2018-07-20T10:36:12.000000",
    "updated_at": "2018-07-20T10:36:13.000000",
    "parent_id": 1,
    "is_public": false,
    "id": 3
}
```

This endpoint retrieves a specific folder.

### HTTP Request

`GET /folders/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the folder to retrieve



## Update a Specific Folder

```shell
# Update a file with ID 3
curl https://api.sellf.io/v2/folders/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -X PUT -d "{"name": "FOLDER"}"
```

> The above command returns JSON structured like this:

```json
{
    "user_id": 7,
    "name": "FOLDER",
    "created_at": "2018-07-20T10:36:12.000000",
    "updated_at": "2018-07-20T10:36:13.000000",
    "parent_id": 1,
    "is_public": true,
    "id": 3
}
```

This endpoint allows to update a specific folder.

### HTTP Request

`PUT /folders/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the folder to update



## Delete a Specific Folder

```shell
# Delete the todo with ID 3
curl https://api.sellf.io/v2/folders/3 \
  -H "Api-Key: {YOUR_API_KEY}" \
  -X DELETE
```

> The above command returns 200 with no content.

This endpoint deletes a specific folder.


### HTTP Request

`DELETE /folders/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The unique identifier of the folder to be deleted

