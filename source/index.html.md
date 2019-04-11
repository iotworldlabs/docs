---
title: D4DT IIRP API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

The D4DT IIRP API is organized around REST. You can use our API to access IIRP API endpoints, which can get information on various things4 in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'd4dtiirp'

api = D4DTIIRP::APIClient.authorize!('<YOUR API KEY>')
```

```python
import d4dtiirp

api = d4dtiirp.authorize('<YOUR API KEY>')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: <YOUR API KEY>"
```

```javascript
const d4dtiirp = require('d4dtiirp');

let api = d4dtiirp.authorize('<YOUR API KEY>');
```

> Make sure to replace `<YOUR API KEY>` with your API key.

D4DTIIRP uses API keys to allow access to the API. You can register a new D4DT IIRP API key at our [developer portal](https://d4dt.com/developers).

D4DT IIRP expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: <YOUR API KEY>`

<aside class="notice">
You must replace <code><YOUR API KEY></code> with your personal API key.
</aside>

# D4DT IIRP

## Get All Things

```ruby
require 'd4dtiirp'

api = D4DTIIRP::APIClient.authorize!('<YOUR API KEY>')
api.things.get
```

```python
import d4dtiirp

api = d4dtiirp.authorize('<YOUR API KEY>')
api.things.get()
```

```shell
curl "https://d4dt.com/api/things"
  -H "Authorization: <YOUR API KEY>"
```

```javascript
const d4dtiirp = require('d4dtiirp');

let api = d4dtiirp.authorize('<YOUR API KEY>');
let things = api.things.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "truck"
  },
  {
    "id": 2,
    "name": "vehicle"
  }
]
```

This endpoint retrieves all things.

### HTTP Request

`GET https://d4dt.com/api/things`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_sensors | false | If set to true, the result will also include sensors.
available | true | If set to false, the result will include things that have no active sensor.

<aside class="success">
Remember — renew your token!
</aside>

## Get a Specific Thing

```ruby
require 'd4dtiirp'

api = D4DTIIRP::APIClient.authorize!('<YOUR API KEY>')
api.things.get(2)
```

```python
import d4dtiirp

api = d4dtiirp.authorize('<YOUR API KEY>')
api.things.get(2)
```

```shell
curl "https://d4dt.com/api/things/2"
  -H "Authorization: <YOUR API KEY>"
```

```javascript
const d4dtiirp = require('d4dtiirp');

let api = d4dtiirp.authorize('<YOUR API KEY>');
let max = api.things.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific Thing.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://d4dt.com/things/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the thing to retrieve

## Delete a Specific Thing

```ruby
require 'd4dtiirp'

api = d4dtiirp::APIClient.authorize!('<YOUR API KEY>')
api.things.delete(2)
```

```python
import d4dtiirp

api = d4dtiirp.authorize('<YOUR API KEY>')
api.things.delete(2)
```

```shell
curl "https://d4dt.com/api/things/2"
  -X DELETE
  -H "Authorization: <YOUR API KEY>"
```

```javascript
const d4dtiirp = require('d4dtiirp');

let api = d4dtiirp.authorize('<YOUR API KEY>');
let max = api.things.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific thing.

### HTTP Request

`DELETE https://d4dt.com/things/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the thing to delete

