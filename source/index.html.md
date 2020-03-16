---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - php
  - shell


toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

The Golfana Golf Course DB API is organized around REST. Our API has predictable, resource-oriented URLs,
accepts form-encoded request bodies, returns JSON-encoded responses and uses standard HTTP response codes, 
authentication and verbs.

You can view code examples in the dark area to the right and you can switch the programming language of 
the examples with the tabs in the top right.

The Golfana Golf Course DB API can be used in test or in live mode. The access token you use to authenticate 
the request determines whether the request is test mode or live mode.

This API documentation page was created with [Slate](https://github.com/lord/slate) and heavily inspired by [Stripe's API documentation](https://stripe.com/docs/api).

# HTTP Clients

Our examples use the follwoging HTTP clients:

## PHP 

```php
<?php
# We use GuzzleHttp in all our examples.
$client = new \GuzzleHttp\Client(
    [
        'http_errors'   => false,   # Do not throw exceptions when receiving protocol errors. 
        'base_uri'      => 'https://api.golfana.local:444/golfcoursedb/v1/' # Note the forward slash at the end
    ]);
``` 

All PHP examples use [GuzzleHttp](http://docs.guzzlephp.org/en/stable/) to create a HTTP client, which is easily installed
with [Composer like so](http://docs.guzzlephp.org/en/stable/overview.html#installation). The parameters passed to GuzzleHttp 
in the examples are optional and may of course be adjusted to suite your specific needs.

If you want to use another HTTP Client library than GuzzleHttp, please note that the Golfana Golf Course DB API expects PSR-7 
compliant messages.

## Shell 

```shell
curl https://api.stripe.com/v1/charges \
  -u sk_test_4eC39HqLyjWDarjtT1zdp7dc:
```

All shell examples use [curl](https://curl.haxx.se/)

# Authentication

The Golfana Golf Course DB API uses access tokens to authenticate requests. You can view and manage your access tokens in the **Golfana Golf Course DB settings**.

Your access tokens carry many privileges, so please keep them secure! Do not share your access tokens in publicly accessible areas such as GitHub, client-side code, and so forth.

Authentication to the API is performed via **bearer authentication** and all API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

```php
<?php
$headers = ['Authorization' => 'Bearer ' . $apiAccessToken];

$response = $client->request('GET', 'golfclubs/info', ['headers' => $headers]);
```
```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```
> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
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

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

