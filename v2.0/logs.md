This page describes how all UserAccounts packages generate log messages and how their verbosity can be configured changed.


## Logger Package

UserAccounts uses [Pince](https://atmospherejs.com/jag/pince) as its logger both for the server and the client.


## Log Level Conventions

Pince provides different log levels which are used for different purposes:

1. *error*: TBD
2. *warn*: TBD
3. *info*: TBD
4. *debug*: TBD
5. *trace*: track files loads plus additions and operations on the base class among different packages/modules.


## Available Loggers

Different hierarchically organized *loggers* are used for each UserAccounts package/module.
The following is alist of available logges:

* UserAccounts
* ...to be continued


## Default Verbosity

All *loggers* are set to `error` level by default to prevent log pollution ;-)


## Setting Log Level

The overall verbosity level for logs can be easily changed with calls like this:

```javascript
Logger.setLevel('trace');
```

Moreover the log level can be set for each package/module this way:

```javascript
Logger.setLevel('useraccounts:core', 'tarce');
Logger.setLevel('useraccounts:i18n', 'debug');
```

## Setting Log Level via ENV

Since it would be hard to set log levels from the app code (code for packages is usually loaded before top level app code...) the initial log level is possibly picked from ENV variables.

Simply set variables with UPPERCASE module names separated by `_` and ending with `_LOGLEVEL` to provide an intial log level:

* USERACCOUNTS_CORE_LOGLEVEL="trace"
* USERACCOUNTS_I18N_LOGLEVEL="debug"
