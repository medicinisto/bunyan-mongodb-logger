# bunyan-mongodb-logger

[![Build Status](https://travis-ci.org/abd2561024/bunyan-mongodb-logger.svg?branch=master)](https://travis-ci.org/abd2561024/bunyan-mongodb-logger)

# Introduction

This logger allows you to save your logs to `MongoDB`, `stdout` or file. It based on a [bunyan](https://github.com/trentm/node-bunyan) logger.

## Usage

### Logger options


|Field          |Required               |Type    |Description  |
| ------------- | --------------------- |------  | ----------- |
|name           |Yes                    |String  |Provided at Logger creation. You must specify a name for your logger when creating it.|
|stream         |Optional               |String  | Single stream name (`mongodb`, `$stdout`, `file`)|
|streams        |Optional               |[String]| Stream names array (`mongodb`, `$stdout`, `file`)|
|level          |Optional               |String  | Level of logging (`fatal`, `error`, `warn`, `info`, `debug` and `trace`)|
|url            |Optional               |String  | Mongodb stream url (e.g. `mongodb://localhost/logger-test`)|
|collections    |Optional               |String  | Mongodb collection name (default: `logs`)|
|path           |Yes, with `file` stream |String | Output file path.|

 
### Using the module.

```js
'use strict';

var logger = require('bunyan-mongodb-logger');

module.exports = logger({
  name: 'some-name',
  streams: ['stdout', 'mongodb'],
  url: 'mongodb://localhost/logger-test',
  level: process.env.LOG_LEVEL || config.logger.level
});

logger.error(new Error('some error'), 'some custom message');
logger.info('Some info');
```

## Tests
Just run:
```js
npm test
```
