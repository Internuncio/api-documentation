# Hitblocks

## Get Hitblock

```ruby
require 'hitblocks'

Hitblocks.api_key('8641fb38-294a-41d9-9591-3449dfd99910')

Hitblocks::Hitblocks.get(<ID>)
```

```shell
curl "https://api.hitblocks.ai/v1/hitblock/<ID>" \
  -u 8641fb38-294a-41d9-9591-3449dfd99910
```

> The above command returns JSON structured like this:

```json
{
  "object": "hitblock",
  "id": 4,
  "type": "image-transcription",
  "title": "Receipt Transcription",
  "description": "for transcribing bbq shop receipts"
  "created": 1495230848,
  "cost_per_item": 0.10,
  "total_spent": 2.00,
  "workers_per_item": 1,
  "currency": "usd"
}
```

This endpoint retrieves a specific hitblock.

### HTTP Request

`GET https://www.hitblocks.ai/v1/hitblock/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the hitblock to retrieve


## List Hitblocks

```ruby
require 'hitblocks'

Hitblocks.api_key('8641fb38-294a-41d9-9591-3449dfd99910')

Hitblocks::Hitblocks.list
```

```shell
curl "https://api.hitblocks.ai/v1/hitblocks" \
  -u 8641fb38-294a-41d9-9591-3449dfd99910
```

> The above command returns JSON structured like this:

```json
{
  "object": "list",
  "url": "/v1/hitblocks",
  "data": [
    {
      "object": "hitblock",
      "id": 4,
      "type": "image-transcription",
      "title": "Receipt Transcription",
      "description": "for transcribing bbq shop receipts"
      "created": 1495230848,
      "cost_per_item": 0.10,
      "workers_per_item": 1,
      "currency": "usd"
    },
    {
      "object": "hitblock",
      "id": 5,
      "type": "image-transcription",
      "title": "Handwriting Transcription",
      "description": "for transcribing notes into digital copies"
      "created": 1495230848,
      "cost_per_item": 0.25,
      "workers_per_item": 1,
      "currency": "usd"
    }
  ]
}
```

This endpoint retrieves all hitblocks.

### HTTP Request

`GET https://api.hitblocks.ai/v1/hitblocks`
