---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  #- python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - tasks
  - events
  - errors

search: true
---

# Introduction

Welcome to the Manatoo API! You can use our API to access Manatoo API endpoints, which helps you create, update, and view tasks to manage your Manatoo task list.

We have language bindings in shell, Ruby, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Installation

To install cURL, please checkout <a href="https://curl.haxx.se/" target="_blank">https://curl.haxx.se/</a>.

To install the ruby gem, please visit <a href="https://github.com/Manatoo/ruby" target="_blank">https://github.com/Manatoo/ruby</a>.

To install the node package, please visit <a href="https://github.com/Manatoo/node" target="_blank">https://github.com/Manatoo/node</a>.

# Authentication

> To authenticate, use this code:

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'
```

```shell
# With shell, you can just pass the correct header with each request
curl "https:/manatoo.io/api/API_ENDPOINT" \
  -u "API_KEY"
```

```javascript
var manatoo = require('manatoo')('API_KEY');
```

> Make sure to replace `API_KEY` with your API key and `API_ENDPOINT` with the endpoint you are trying to access.

Manatoo uses API keys to allow access to the API. You can view your api key on the home page once you log into your account.

Manatoo expects for the API key to be included in all API requests to the server.

<aside class="notice">
You must replace <code>API_KEY</code> with your personal API key.
</aside>
