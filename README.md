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

You can simplify the command by defining the global options as environment variables:

- `APEXCOV_INSTANCE`: Salesforce instance URL
- `APEXCOV_USERNAME`: Account username
- `APEXCOV_PASSWORD`: Account password

Then, you can generate your `lcov.info` by simply running the binary:

```sh
$ apexcov
```

### Coveralls

#### Travis CI

Add this to your `.travis.yml`:

```yaml
before_install:
- npm install -g coveralls
- go get -u github.com/jpmonette/apexcov
after_script:
- apexcov
- "cat ./coverage/lcov.info | coveralls"
```

#### CircleCI

Add this to your `circle.yml`:

```yaml
machine:
  pre:
    - npm install -g coveralls
    - go get -u github.com/jpmonette/apexcov
test:
  post:
    - apexcov
    - cat ./coverage/lcov.info | coveralls
```

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
