# apexcov
Maintaining a well-tested codebase is mission-critical. `apexcov` generates public [Apex](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_intro_what_is_apex.htm) test coverage reports for your [Force.com](https://force.com) open-source projects.

  [![CircleCI Build Status](https://circleci.com/gh/jpmonette/apexcov.png?style=shield&circle-token=:circle-token)](https://circleci.com/gh/jpmonette/apexcov)

## Installation

```sh
$ go get -u github.com/jpmonette/apexcov
```

## Usage

To generate your test coverage report:

```sh
$ apexcov --username="jpmonette@example.com" --password="my-password"
```

You can shorten the command by setting the global options as environment variables:

- `APEXCOV_INSTANCE`: Salesforce instance URL
- `APEXCOV_USERNAME`: Account username
- `APEXCOV_PASSWORD`: Account password

### Coveralls

#### Travis CI

Add this to your `.travis.yml`:

```yaml
env:
- GOPATH=$HOME/go PATH=$GOPATH/bin:$PATH
before_script:
- npm install -g coveralls
- go get github.com/jpmonette/apexcov
script:
- apexcov
- codeclimate-test-reporter < ./coverage/lcov.info
```

(make sure you set your `COVERALLS_REPO_TOKEN` environment variable)

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

### Code Climate

#### Travis CI

Add this to your `.travis.yml`:

```yaml
env:
- GOPATH=$HOME/go PATH=$GOPATH/bin:$PATH
before_script:
- npm install -g codeclimate-test-reporter
- go get github.com/jpmonette/apexcov
script:
- apexcov
- codeclimate-test-reporter < ./coverage/lcov.info
```

(make sure you set your `CODECLIMATE_REPO_TOKEN` environment variable)

#### CircleCI

Add this to your `circle.yml`:

```yaml
machine:
  pre:
    - npm install -g codeclimate-test-reporter
    - go get -u github.com/jpmonette/apexcov
test:
  post:
    - apexcov
    - codeclimate-test-reporter < ./coverage/lcov.info
```

(make sure you set your `CODECLIMATE_REPO_TOKEN` environment variable)

## Help

```sh
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
