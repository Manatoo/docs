# Events

## Creating an Event

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

json = Manatoo::Event.create({
  name: 'user_signup'
})

# Note: the ruby json Hash has its keys snake_cased to follow the ruby naming conventions
```

```shell
curl "https://manatoo.io/api/events" \
  -u "API_KEY" \
  -d name='user_signup'
```

```javascript
var manatoo = require('manatoo')('API_KEY');

manatoo.event.create({
  name: 'user_signup'
}).then(function(json) {
  return json;
});
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "name": "user_signup"
  }
}
```

This endpoint creates an event. The name of the event, `name`, is required. This can be any string.

### HTTP Request

`POST https://manatoo.io/api/events`

### URL Parameters

Parameter | Description
--------- | -----------
name | The name of the event. REQUIRED.
