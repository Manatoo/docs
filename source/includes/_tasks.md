# Tasks

## Getting a Task

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# task is an instance that helps you easily access a task's attributes
task = Manatoo::Task.find('y6DZ0IDaNpWKsnqQYbVUA0v0pNEUQQ')

# e.g. getting the title and description
title = task.title
description = task.description

# you can still get the json hash displayed below
json = task.last_json_response
```

```shell
curl "https://manatoo.io/api/tasks/y6DZ0IDaNpWKsnqQYbVUA0v0pNEUQQ" \
  -u "API_KEY"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

manatoo.task.find('y6DZ0IDaNpWKsnqQYbVUA0v0pNEUQQ').then(function(task) {
  // task is an instance that helps you easily access a task's attributes
  // e.g. getting the title and description
  var title = task.title;
  var description = task.description;

  // you can still get the json hash displayed below
  var json = task.lastJsonResponse;
});
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "y6DZ0IDaNpWKsnqQYbVUA0v0pNEUQQ",
    "title": "Draft an email",
    "data": {
      "contactName": "Adam O."
    },
    "description": "Draft a sample marketing email to Adam",
    "slug": "y6DZ0IDaNpWKsnqQYbVUA0v0pNEUQQ",
    "status": "open",
    "weight": 1,
    "duration": 7200,
    "labels": [
      "important",
      "emails"
    ],
    "finishedAt": "2018-02-18T12:02:59.521Z",
    "createdAt": "2018-02-16T08:02:59.521Z",
    "dueAt": "2018-02-20T08:02:59.521Z",
    "startedAt": "2018-02-18T10:02:59.521Z",
    "listId": "meqRnGLW6tEOwCcxofz_ZYxsdredxg",
    "users": [
      {
        "token": "PJwjWbo0thleCsA_A7XSfKRSAxNz5w",
        "profileImageUrl": "https://imgur.com/URBc9Kb.png",
        "firstName": "Ashley",
        "lastName": "Vonn"
      }
    ]
  }
}
```

This endpoint retrieves a task.

### HTTP Request

`GET https://manatoo.io/api/tasks/<task_id>`

### URL Parameters

Parameter | Description
--------- | -----------
task_id | The id of the task you are retrieving.

## Creating a Task

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# task is an instance that helps you easily access a task's attributes
task = Manatoo::Task.create({
  list_id: 'meqRnGLW6tEOwCcxofz_ZYxsdredxg',
  title: "Check the sales data on Product X",
  description: "Pull out sales data from April",
  due_at: "2018-02-24T18:02:59.521Z",
  weight: "9",
  status: "started",
  labels: ["sales", "urgent"],
  users: ["john@example.com", "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"],
  data: {
    month: "April",
    region: "us-west"
  }
})

# e.g. getting the title and description
title = task.title
description = task.description

# you can still get the json hash displayed below
json = task.last_json_response
```

```shell
curl "https://manatoo.io/api/tasks" \
  -u "API_KEY" \
  -d list_id='meqRnGLW6tEOwCcxofz_ZYxsdredxg' \
  -d title="Check the sales data on Product X" \
  -d description="Pull out sales data from April" \
  -d due_at="2018-02-24T18:02:59.521Z" \
  -d weight="9" \
  -d status="started" \
  -d labels[]="sales" \
  -d labels[]="urgent" \
  -d users[]="john@example.com" \
  -d users[]="PJwjWbo0thleCsA_A7XSfKRSAxNz5w" \
  -d data[month]="April" \
  -d data[region]="us-west"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

manatoo.task.create({
  listId: 'meqRnGLW6tEOwCcxofz_ZYxsdredxg',
  title: "Check the sales data on Product X",
  description: "Pull out sales data from April",
  dueAt: "2018-02-24T18:02:59.521Z",
  weight: "9",
  status: "started",
  labels: ["sales", "urgent"],
  users: ["john@example.com", "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"],
  data: {
    month: "April",
    region: "us-west"
  }
}).then(function(task) {
  // task is an instance that helps you easily access a task's attributes
  // e.g. getting the title and description
  var title = task.title;
  var description = task.description;

  // you can still get the json hash displayed below
  var json = task.lastJsonResponse;
});
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg",
    "title": "Check the sales data on Product X",
    "data": {
      "month": "April",
      "region": "us-west"
    },
    "description": "Pull out sales data from April",
    "slug": "tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg",
    "status": "started",
    "weight": 9,
    "duration": null,
    "labels": [
      "sales",
      "urgent"
    ],
    "finishedAt": null,
    "createdAt": "2018-02-16T22:16:26.144Z",
    "dueAt": "2018-02-24T18:02:59.521Z",
    "startedAt": "2018-02-16T22:16:26.144Z",
    "listId": "meqRnGLW6tEOwCcxofz_ZYxsdredxg",
    "users": [
      {
        "token": "hrKavGdYRU7YBChs3swqeoDvPl_azw",
        "profileImageUrl": null,
        "firstName": "John",
        "lastName": "Lowe"
      },
      {
        "token": "PJwjWbo0thleCsA_A7XSfKRSAxNz5w",
        "profileImageUrl": "https://imgur.com/URBc9Kb.png",
        "firstName": "Ashley",
        "lastName": "Vonn"
      }
    ]
  }
}
```

This endpoint create a task. There are two required parameters: `title` and `list_id`.

The `title` briefly describes what the task is.  The `list_id` can be found in the overview section of a list's page or can be taken from a list's url: `https://manatoo.io/lists/<list_id>` or  `https://manatoo.io/lists/<list_id>/tasks/tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg`.

### HTTP Request

`POST http://example.com/api/tasks`

### URL Parameters

Parameter | Description
--------- | -----------
title | The title of the task. REQUIRED.
list_id | The id of the list the task is added to. REQUIRED.
description | A task's description and/or instructions. Defaults to an empty `string`.
status | A `string` representing one of four statues a task can have: (`open`, `started`, `finished`, `archived`).  Defaults to `open`.
weight | An `integer` value that is often used to signify the importance or urgency of a task. Defaults to 1.
labels | An `array` of `strings` that acts like tags for a task. Defaults to an empty `array`.
users | An `array` of `strings` that represents the users of the task.  The strings must be the `email` login of a user or the `token` of a user.  Supplied users must also be members of the list the task is added to.  Users that do not fulfill the requirements will not be added to the task. Defaults to an `array` with the creator of the task.
started_at | A `string` representing when a task was started in `ISO 8601` format. Defaults to `null`.
finished_at | A `string` representing when a task was finished in `ISO 8601` format. Defaults to `null`.
duration | An `integer` representing how long the task took in seconds. If `started_at` and `finished_at` are both supplied, the duration is automatically calculated, otherwise, it defaults to `null`.
due_at | A `string` representing when a task is due in `ISO 8601` format. Defaults to `null`.
data | An `object` that is for storing task related data. Defaults to `{}`.


## Updating a Task

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# This can be done two ways

# 1. If you have a task instance
task = Manatoo::Task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
task.update({ title: "Update the customer excel sheet" })

# 2. If you have a task id
Manatoo::Task.update('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', {
  title: "Update the customer excel sheet"
})
```

```shell
curl "https://manatoo.io/api/tasks/tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg" \
  -X PUT \
  -u "API_KEY" \
  -d title="Update the customer excel sheet"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

// This can be done two ways

// 1. If you have a task instance
manatoo.task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
.then(function(task) {
  // this returns a promise that has the task instance as its parameter
  return task.update({
    title: 'Update the customer excel sheet'
  });
});

// 2. If you have a task id
// this returns a promise that has the json body as its parameter
manatoo.task.update('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', {
  title: 'Update the customer excel sheet'
})
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "title": "Update the customer excel sheet"
  }
}
```

This endpoint is used to update the attributes of a task.

<aside class="notice">The response returns the attributes of the task that have been changed.  For example updating the <code>title</code> and <code>description</code> of a task will return a <code>data</code> object containing only the <code>title</code> and <code>description</code> updated attributes.</aside>

<aside class="warning">Attributes are overridden, not added to.  For example, passing in a label <code>array</code> of <code>["one label"]</code> will not add "one label" to the existing labels, but instead will set the labels on the task to "one label".</aside>

### HTTP Request

`PUT https://manatoo.io/tasks/<task_id>`

### URL Parameters

Parameter | Description
--------- | -----------
task_id | The id of the task to update. REQUIRED.
title | The title of the task.
description | A task's description and/or instructions.
status | A `string` representing one of four statues a task can have: (`open`, `started`, `finished`, `archived`).
weight | An `integer` value that is often used to signify the importance or urgency of a task.
labels | An `array` of `strings` that acts like tags for a task. Defaults to an empty `array`.
users | An `array` of `strings` that represents the users of the task.  The strings must be the `email` login of a user or the `token` of a user.  Supplied users must also be members of the list the task is added to.  Users that do not fulfill the requirements will not be added to the task.
started_at | A `string` representing when a task was started in `ISO 8601` format.
finished_at | A `string` representing when a task was finished in `ISO 8601` format.
duration | An `integer` representing how long the task took in seconds.
due_at | A `string` representing when a task is due in `ISO 8601` format.
data | An `object` that is for storing task related data.

## Updating only the Status

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# This can be done two ways

# 1. If you have a task instance
task = Manatoo::Task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
task.update_status('finished')

# 2. If you have a task id
Manatoo::Task.update_status('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', 'finished')
```

```shell
curl "https://manatoo.io/api/tasks/tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg/status" \
  -X PUT \
  -u "API_KEY" \
  -d status="finished"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

// This can be done two ways

// 1. If you have a task instance
manatoo.task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
.then(function(task) {
  // this returns a promise that has the task instance as its parameter
  return task.updateStatus('finished');
});

// 2. If you have a task id
// this returns a promise that has the json body as its parameter
manatoo.task.updateStatus('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', 'finished')
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "status": "finished",
    "finishedAt": "2018-02-16T23:10:44.653Z",
    "startedAt": "2018-02-16T22:16:26.144Z",
    "duration": 3258
  }
}
```

This endpoint only updates the status of a task.

### HTTP Request

`PUT https://manatoo.io/api/tasks/<task_id>/status`

### URL Parameters

Parameter | Description
--------- | -----------
task_id | The id of the task. REQUIRED.
status | A `string` representing one of four statues a task can have: (`open`, `started`, `finished`, `archived`). REQUIRED.

## Adding Labels

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# This can be done two ways

# 1. If you have a task instance
task = Manatoo::Task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
task.add_labels(['awesome', 'another label'])

# 2. If you have a task id
Manatoo::Task.add_labels('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', [
  'awesome',
  'another label'
])
```

```shell
curl "https://manatoo.io/api/tasks/tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg/labels" \
  -u "API_KEY" \
  -d labels[]="awesome" \
  -d labels[]="another label"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

// This can be done two ways

// 1. If you have a task instance
manatoo.task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
.then(function(task) {
  // this returns a promise that has the task instance as its parameter
  return task.addLabels([
    'awesome',
    'another label'
  ]);
});

// 2. If you have a task id
// this returns a promise that has the json body as its parameter
manatoo.task.addLabels('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', [
  'awesome',
  'another label'
]);
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "labels": [
      "sales",
      "urgent",
      "another label",
      "awesome"
    ]
  }
}
```

This endpoint add labels to a task. This endpoint returns the task's updated labels.

### HTTP Request

`POST https://manatoo.io/api/tasks/<task_id>/labels`

### URL Parameters

Parameter | Description
--------- | -----------
task_id | The id of the task. REQUIRED.
labels | An `array` of `strings` that acts like tags for a task. Defaults to an empty `array`. REQUIRED.

## Adding Weight

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# This can be done two ways

# 1. If you have a task instance
task = Manatoo::Task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
task.add_weight(2)

# 2. If you have a task id
Manatoo::Task.add_weight('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', 2)
```

```shell
curl "https://manatoo.io/api/tasks/tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg/weight" \
  -u "API_KEY" \
  -d weight="2"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

// This can be done two ways

// 1. If you have a task instance
manatoo.task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
.then(function(task) {
  // this returns a promise that has the task instance as its parameter
  return task.addWeight(2);
});

// 2. If you have a task id
// this returns a promise that has the json body as its parameter
manatoo.task.addWeight('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', 2);
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "weight": 3
  }
}
```

This endpoint adds weight to a task. For example, if the task already has a weight of 10, passing in a `weight` of 5 to this endpoint will result in the task having an updated weight of 15.  This endpoint returns the updated weight.

### HTTP Request

`POST https://manatoo.io/api/tasks/<task_id>/weight`

### URL Parameters

Parameter | Description
--------- | -----------
task_id | The id of the task. REQUIRED.
weight | An `integer` value of the weight to add. REQUIRED.

## Adding Users

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# This can be done two ways

# 1. If you have a task instance
task = Manatoo::Task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
task.add_users([
  "john@example.com",
  "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
])

# 2. If you have a task id
Manatoo::Task.add_users('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', [
  "john@example.com",
  "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
])
```

```shell
curl "https://manatoo.io/api/tasks/tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg/users" \
  -u "API_KEY" \
  -d users[]="john@example.com" \
  -d users[]="PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

// This can be done two ways

// 1. If you have a task instance
manatoo.task.add('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
.then(function(task) {
  // this returns a promise that has the task instance as its parameter
  return task.addUsers([
    "john@example.com",
    "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
  ]);
});

// 2. If you have a task id
// this returns a promise that has the json body as its parameter
manatoo.task.addUsers('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', [
  "john@example.com",
  "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
]);
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "users": [
      {
        "token": "KLkg8FcZOCas5LnVLHm9hEKdAKw0Wg",
        "profileImageUrl": null,
        "firstName": "John",
        "lastName": "Lowe"
      },
      {
        "token": "hrKavGdYRU7YBChs3swqeoDvPl_azw",
        "profileImageUrl": null,
        "firstName": "Alex",
        "lastName": "Simms"
      },
      {
        "token": "PJwjWbo0thleCsA_A7XSfKRSAxNz5w",
        "profileImageUrl": "https://imgur.com/URBc9Kb.png",
        "firstName": "Ashley",
        "lastName": "Vonn"
      }
    ]
  }
}
```

This endpoint adds users to a task.  It returns an updated list of the users of the task.

### HTTP Request

`POST https://manatoo.io/api/tasks/<task_id>/users`

### URL Parameters

Parameter | Description
--------- | -----------
task_id | The id of the task. REQUIRED.
users | An `array` of `strings` that represents the users of the task.  The strings must be the `email` login of a user or the `token` of a user.  Supplied users must also be members of the list the task is added to.  Users that do not fulfill the requirements will not be added to the task. REQUIRED.

## Removing Users

```ruby
require 'manatoo'
Manatoo.api_key = 'API_KEY'

# This can be done two ways

# 1. If you have a task instance
task = Manatoo::Task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
task.remove_users([
  "john@example.com",
  "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
])

# 2. If you have a task id
Manatoo::Task.remove_users('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', [
  "john@example.com",
  "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
])
```

```shell
curl "https://manatoo.io/api/tasks/tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg/users" \
  -X DELETE \
  -u "API_KEY" \
  -d users[]="john@example.com" \
  -d users[]="PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
```

```javascript
var manatoo = require('manatoo')('API_KEY');

// This can be done two ways

// 1. If you have a task instance
manatoo.task.find('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg')
.then(function(task) {
  // this returns a promise that has the task instance as its parameter
  return task.removeUsers([
    "john@example.com",
    "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
  ]);
});

// 2. If you have a task id
// this returns a promise that has the json body as its parameter
manatoo.task.removeUsers('tRhW-T_EV5gyeMK4sDfSz7rEQWq-Yg', [
  "john@example.com",
  "PJwjWbo0thleCsA_A7XSfKRSAxNz5w"
]);
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "users": [
      {
        "token": "hrKavGdYRU7YBChs3swqeoDvPl_azw",
        "profileImageUrl": null,
        "firstName": "Alex",
        "lastName": "Simms"
      },
    ]
  }
}
```

This endpoint deletes users from a task.  It returns an updated list of the users of the task.

### HTTP Request

`DELETE https://manatoo.io/api/tasks/<task_id>/users`

### URL Parameters

Parameter | Description
--------- | -----------
task_id | The id of the task. REQUIRED.
users | An `array` of `strings` that represents the users of the task.  The strings must be the `email` login of a user or the `token` of a user.  Supplied users must also be members of the list the task is added to.  Users that do not fulfill the requirements will not be deleted from the task. REQUIRED.
