---
title: Hitblocks API Reference

language_tabs:
  - shell: cURL
  - ruby: Ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors
  - hitblocks
  - items

search: true
---

# Introduction

Welcome to the Hitblocks API documentation! Our API is
[REST](https://en.wikipedia.org/wiki/Representational_state_transfer) based. That means
predictable resource-oriented URLs, which return HTTP response codes to
indicate API errors.

Responses are given in JSON format, which return both errors and data requested.

# Authentication

> To authorize, use this code:

```ruby
require 'hitblocks'

api = Hitblocks.api_key = "8641fb38-294a-41d9-9591-3449dfd99910"
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.hitblocks.ai/v1/hitblocks"
  -u 8641fb38-294a-41d9-9591-3449dfd99910
```

> Make sure to replace `8641fb38-294a-41d9-9591-3449dfd99910` with your API key.

Authentication is done using an API secret key in a given request. Manage API
keys from your dashboard. API keys allow access to all functions of your account
and should be kept secret. Do not put keys on publicly accessable Github
repositories or in client-side code.

Authentication is performed via HTTP Basic Auth. Provide your API key as the
basic auth username value. You do not need to provide a password.

Hitblocks expects for the API key to be included in all API requests to the server in a header that looks like the following:

All API requests will be made of HTTPS. Calls over plain HTTP will fail. API
requests without authentication will also fail.

<aside class="notice">
You must replace <code>8641fb38-294a-41d9-9591-3449dfd99910</code> with your personal API key.
</aside>
