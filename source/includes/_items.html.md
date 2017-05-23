# Items

## List All Items

```ruby
require 'hitblocks'

Hitblocks.api_key('8641fb38-294a-41d9-9591-3449dfd99910')

hitblock = Hitblocks::Hitblock.get(<hitblock_id>)
hitblock.items
```

```shell
curl "https://api.hitblocks.ai/v1/hitblock/<hitblock_id>/items" \
  -u 8641fb38-294a-41d9-9591-3449dfd99910
```

> The above command returns JSON structured like this:

```json
{
  "object": "list",
  "url": "v1/hitblock/<hitblock_id>/items",
  "data": [
    {
      "object": "item",
      "id": 2,
      "type": "image",
      "created": 1495230848,
      "cost": 0.10,
      "currency": "usd",
      "status": "completed",
      "params": {
        "image_url": "https://upload.wikimedia.org/wikipedia/commons/0/0b/ReceiptSwiss.jpg",
        "description": "image of receipt1.jpg"
      },
      "responses": [
        {
          "object": "response",
          "data": {...},
          "approved": "false"
        },
        {
          "object": "response",
          "data": {...},
          "approved": "true"
        }
      ]
    },
    {
      "object": "item",
      "id": 3,
      "type": "image",
      "created": 1495230905,
      "cost": 0.10,
      "currency": "usd",
      "status": "completed",
      "params": {
        "image_url": "https://upload.wikimedia.org/wikipedia/commons/0/0b/ReceiptSwiss.jpg",
        "description": "image of receipt2.jpg"
      },
      "responses": [
        {
          "object": "response",
          "data": {...},
          "approved": "false"
        },
        {
          "object": "response",
          "data": {...},
          "approved": "true"
        }
      ]
    }
  ]
}
```

This endpoint retrieves all items in a given hitblock.

### HTTP Request

`GET https://api.hitblocks.ai/v1/hitblock/<hitblock_id>/items`


### URL Parameters

Parameter | Description
--------- | -----------
**hitblock_id** | The ID of the hitblock to get items from.


## Get an Item

```ruby
require 'hitblocks'

Hitblocks.api_key('8641fb38-294a-41d9-9591-3449dfd99910')

Hitblocks::Item.get(item_id)
```

```shell
curl "https://api.hitblocks.ai/v1/item/<ID>" \
  -u 8641fb38-294a-41d9-9591-3449dfd99910
```

> The above command returns JSON structured like this:

```json
{
  "object": "item",
  "id": 2,
  "type": "image",
  "created": 1495230848,
  "cost": 0.10,
  "currency": "usd",
  "status": "completed",
  "params": {
    "image_url": "https://upload.wikimedia.org/wikipedia/commons/0/0b/ReceiptSwiss.jpg",
    "description": "image of receipt1.jpg"
  },
  "responses": [
    {
      "object": "response",
      "data": {...},
      "approval": "approved"
    },
    {
      "object": "response",
      "data": {...},
      "approval": "rejected"
    }
  ]
}
```

This endpoint retrieves a specific item.

### HTTP Request

`GET https://www.hitblocks.ai/v1/item/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
**ID** | The ID of the item to retrieve


## Create an Item

```ruby
require 'hitblocks'

Hitblocks.api_key('8641fb38-294a-41d9-9591-3449dfd99910')

hitblock = Hitblocks::Hitblock.get(<hitblock_id>)

Hitblocks::Item.create(
    :type => "image",
    :hitblock => hitblock,
    :image_url => "http://www.images.com/my-image.jpg",
    :description => "My image from personal website"
)
```

```shell
curl "https://api.hitblocks.ai/v1/hitblocks/<hitblock_id>/items" \
  -u 8641fb38-294a-41d9-9591-3449dfd99910 \
  -d type="image" \
  -d image_url="http://www.images.com/my-image.jpg" \
  -d description="My image from personal website"
```

> The above command returns JSON structured like this:

```json
{
  "object": "item",
  "id": 3,
  "type": "image",
  "created": 1495231005,
  "cost": 0.10,
  "currency": "usd",
  "status": "completed",
  "params": {
    "image_url": "http://www.images.com/my-image.jpg"
    "description": "My image from personal website"
  },
  "responses": {
  }
}
```

This endpoint creates a specific item.

### HTTP Request

`POST https://www.hitblocks.ai/v1/hitblocks/<hitblock_id>/items`

### Arguments

Arguments | Required | Description
--------- | -------- | -----------
**type** | yes | The type of item, for verification against allowed hitblock inputs.
**hitblock_id** | yes | the ID of the hitblock the item should be placed in.
**image_url** | yes | a parameter for the "image" item that points to the hosted image.
**description** | no | an optional string. Useful for displaying information to users.

## Delete an Item

```ruby
require 'hitblocks'

Hitblocks.api_key('8641fb38-294a-41d9-9591-3449dfd99910')

item = Hitblocks::Item.get(<ID>)
item.delete

```

```shell
curl "https://api.hitblocks.ai/v1/item/<ID>" \
  -u 8641fb38-294a-41d9-9591-3449dfd99910 \
  -X DELETE
```

> The above command returns JSON structured like this:

```json
{
  "deleted": true,
  "id": "<ID>"
}
```

This endpoint deletes a specific item. 

<aside class="notice">
<ul>
  <li>
    If an item is posted already then it is canceled and unspent credits are refunded.
  </li>
<li>
 Items that have already been answered will not be refunded, and will still be available through a direct GET request.
</li>
<li>
Deleted items will not show up when being listed unless specifically requested.
</li>
</ul>
</aside>

### HTTP Request

`DELETE https://www.hitblocks.ai/v1/item/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
**ID**    | The ID of the item to be deleted.


## Post an Item

```ruby
require 'hitblocks'

Hitblocks.api_key('8641fb38-294a-41d9-9591-3449dfd99910')

item = Hitblocks::Item.get(<ID>)
item.post

```

```shell
curl "https://api.hitblocks.ai/v1/item/<ID>/post" \
  -u 8641fb38-294a-41d9-9591-3449dfd99910 \
```

> The above command returns JSON structured like this:

```json
{
  "object": "HIT",
  "url": "www.google.ca",
  "service": "AMT",
  "status": "published",
  "created": 1495230848,
  "item": {
    "object": "item",
    "id": 2,
    "type": "image",
    "created": 1495230848,
    "cost": 0.10,
    "currency": "usd",
    "status": "published",
    "params": {
      "image_url": "https://upload.wikimedia.org/wikipedia/commons/0/0b/ReceiptSwiss.jpg",
      "description": "image of receipt1.jpg"
    },
    "responses": {
    }
  }
}
```

This endpoint posts a specific item to crowdsourced workers on [Amazon Mechanical Turk](https://www.mturk.com/mturk/welcome)

### HTTP Request

`POST https://www.hitblocks.ai/v1/item/<ID>/post`

### URL Parameters

Parameter | Description
--------- | -----------
**ID**    | The ID of the item to be deleted.


