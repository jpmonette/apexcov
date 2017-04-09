# apexcov
A `lcov.info` Test Coverage generator for the [Apex](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_intro_what_is_apex.htm) programming language

  [![CircleCI Build Status](https://circleci.com/gh/jpmonette/apexcov.png?style=shield&circle-token=:circle-token)](https://circleci.com/gh/jpmonette/apexcov)

## Installation

```sh
$ go get -u github.com/jpmonette/apexcov
```

## Usage

To generate your `lcov.info` coverage file:

```sh
$ apexcov --username="jpmonette@example.com" --password="my-password"
```

### Coveralls

If you are using [Travis CI](https://travis-ci.org), add this to your `.travis.yml`:

```yaml
after_script: "cat ./coverage/lcov.info | ./node_modules/coveralls/bin/coveralls.js"
```

Make sure you have the [npm](https://www.npmjs.com/) coveralls package - `npm install coveralls`.

## Help

```sh
go run *.go --help                                                                                                                                 ⏎
NAME:
   apexcov - a Test Coverage Generator for Apex

USAGE:
   apexcov [global options] command [command options] [arguments...]

VERSION:
   1.0.0

AUTHOR:
   Jean-Philippe Monette <contact@jpmonette.net>

COMMANDS:
     help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --instance value  Salesforce instance to use (default: "https://login.salesforce.com")
   --username value  Username of the Salesforge org
   --password value  Password of the Salesforge org
   --help, -h        show help
   --version, -v     print the version
```


## License

This application is distributed under the MIT license found in the [LICENSE](./LICENSE)
file.
