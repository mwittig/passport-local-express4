# User Authentication With Passport and Express 4

Based on the sample server from the tutorial
 [User Authentication With Passport and Express 4](http://mherman.org/blog/2015/01/31/local-authentication-with-passport-and-express-4)

## Getting Started

Install the dependencies:

    npm install

Setup MongoDB if you have not installed it yet

    npm install -g mongodb

Then, in a new terminal window, start the MongoDB daemon:

    sudo mongod

Alternatively, you can setup mongodb as a service. See the [MongoDB manual](http://docs.mongodb.org/manual/)
 for details.

## Changes to the original example

### Logging

The "debug" logger has been replace with "logger-winston". For the logging of express HTTP request messaging the
 package "express-winston is used". The setup as part of "app.js" is done as follows:

    var loggerWinston = require('logger-winston');
    var expressLogger = loggerWinston.getLogger("Express")
    ...

    // we use express-winston instad
    //app.use(logger('dev'));
    app.use(expressWinston.logger({
        winstonInstance: expressLogger
    }));

The setup in "bin/www" is done as follows:

    var config = require("./config.json");
    var loggerWinston = require("logger-winston");
    loggerWinston.init(config);
    var logger = loggerWinston.getLogger("Server");
    ...

    //var debug = require('debug')('passport-local-express4:server');

