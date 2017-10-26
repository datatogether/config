# <Repository Name>

<!-- Repo Badges for: Github Project, Slack, License-->

[![GitHub](https://img.shields.io/badge/project-Data_Together-487b57.svg?style=flat-square)](http://github.com/datatogether)
[![Slack](https://img.shields.io/badge/slack-Archivers-b44e88.svg?style=flat-square)](https://archivers-slack.herokuapp.com/)
[![License](https://img.shields.io/github/license/mashape/apistatus.svg)](./LICENSE) 

`config` is hassle-free config struct setting for golang, setting things like
configStruct.StringField to the value of the enviornment variable STRING_FIELD.
It wraps the lovely godotenv package, which itself is a go port of the ruby
dotenv gem.

## License & Copyright

Copyright (C) <year> Data Together
This program is free software: you can redistribute it and/or modify it under
the terms of the GNU Affero General Public License as published by the Free Software
Foundation, version 3.0.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

See the [`LICENSE`](./LICENSE) file for details.

## Getting Involved

We would love involvement from more people! If you notice any errors or would like to submit changes, please see our [Contributing Guidelines](./.github/CONTRIBUTING.md). 

We use GitHub issues for [tracking bugs and feature requests](https://github.com/datatogether/config/issues) and Pull Requests (PRs) for [submitting changes](https://github.com/datatogether/config/pulls)

## ...

## Usage

Add config to any golang package with `import "github.com/datatogether/config"`

Basic use has three steps:

    1. declare a struct that defines all your config values (eg: type cfg struct{ ... })
    2. (optional) create a file or two that sets enviornement vars.
    3. call config.Load(&cfg, "envfilepath")

config will read that env file, setting environment variables for the running
process and infer any ENVIRIONMENT_VARIABLE value to it's
cfg.EnvironmentVariable counterpart/

config uses a CamelCase -> CAMEL_CASE convention to map values. So a struct
field cfg.FieldName will map to an environment variable FIELD_NAME. Types are
inferred, with errors returned for invalid env var settings.

Using an env file is optional, calling Load(cfg) is perfectly valid.

config uses the reflect package to infer & set values reflect is a good choice
here because setting config happens seldom in the course of a running program,
and these days if you're parsing JSON, the reflect package is already included
in your binary.

### Functions
`config` provides the following functions:

#### func  EnvVarKey

```go
func EnvVarKey(key string) string
```
EnvVarKey takes a CamelCase string and converts it to a CAMEL_CASE string
(uppercase snake_case)

#### func  Load

```go
func Load(dst interface{}, filenames ...string) error
```
Load will read any passed-in env file(s) and load them into ENV for this
process, then assign values to the passed in dst struct pointer. Call this
function as close as possible to the start of your program (ideally in main) If
you call Load without any args it will default to loading .env in the current
path You can otherwise tell it which files to load (there can be more than one)
like

    godotenv.Load("fileone", "filetwo")

It's important to note that it WILL NOT OVERRIDE an env variable that already
exists - consider the .env file to set dev vars or sensible defaults

#### func  Overload

```go
func Overload(dst interface{}, filenames ...string) error
```
Overload will read any passed-in env file(s) and load them into ENV for this
process, then assign values to the passed in dst struct pointer. Call this
function as close as possible to the start of your program (ideally in main) If
you call Overload without any args it will default to loading .env in the
current path You can otherwise tell it which files to load (there can be more
than one) like

    godotenv.Overload("fileone", "filetwo")

It's important to note this WILL OVERRIDE an env variable that already exists -
consider the .env file to forcefilly set all vars.


[Step-by-step instructions about how to set up a local dev environment and any dependencies]

## Development

Coming soon.
