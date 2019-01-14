[![Build Status](https://travis-ci.org/npm-package-poc.svg?branch=master)](https://travis-ci.org/npm-package-poc)

MS SQL Server connection string parser
=========

A small library that parses mssql connection string and returns database configuration for given libraries:
* [knex](http://knexjs.org/)

## Installation

  `npm install mssql-connection-string`

## Usage

##### JavaScript:

    const parser = require('mssql-connection-string');

    const connectionString = "Data Source=tcp:database.com,1433;Initial Catalog=numbers;User Id=service@database.com;Password=qwerty;";

    const knexDb = parser(connectionString);

##### TypeScript:

    import parse from 'mssql-connection-string';

    const connectionString = "Data Source=tcp:database.com,1433;Initial Catalog=numbers;User Id=service@database.com;Password=qwerty;";

    const knexDb = parser(connectionString);

##### Result should be:

        {
            "host": "database.com",
            "options": {
                "database": "numbers",
                "encrypt": true,
                "port": "1433"
            },
            "password": "qwerty",
            "user": "service"
        }

The protocol and port in 'Data Source' are optional. If the 'User Id' contains an email, only the login will be used as user.

## Tests
  `npm install`
  `npm test`

## Contributing

In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code.
