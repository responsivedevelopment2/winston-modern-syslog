# winston-modern-syslog

[![Build Status](https://travis-ci.org/skybet/winston-modern-syslog.svg)](https://travis-ci.org/skybet/winston-modern-syslog)

A syslog transport for [winston](https://www.npmjs.com/package/winston) that is a simple wrapper for the [modern-syslog](https://www.npmjs.com/package/modern-syslog) library.

## Installation

```
npm install --save winston-modern-syslog-with-circular-reference-protection
```

## Usage

To use the ModernSyslog transport in winston, simply require the module and then attach it to the winston logger, or a logger of your own creation:

```javascript
var winston = require('winston');

// Requiring the module will return `winston.transports.ModernSyslog`
require('winston-modern-syslog');

// Tell winston that you're using the syslog levels instead of the defaults
winston.setLevels(winston.config.syslog.levels);

winston.add(winston.transports.ModernSyslog, {level: 'alert'});
```

The ModernSyslog transport has the following options:

* __level__: Level of messages that this transport should log (default 'info').
* __label__: The message prefix (default `process.title`).
* __logPid__: Whether to log the application's PID with the log messages (default false).
* __facility__: syslog facility (default `syslog.facility.LOG_USER`).
* __prefixLevel__: Whether to prefix the log level on the log messages (default false).

As syslog only supports a subset of the levels available in winston, in the example above we explicitly configure winston to use the syslog levels.

Metadata objects are logged via `JSON.stringify(meta)`.

## Tests

The tests are written in [Mocha](https://www.npmjs.org/package/mocha). They can be run with npm:

```javascript
npm test
```
