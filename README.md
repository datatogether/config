# Config

<!-- Repo Badges for: Github Project, Slack, License-->

[![GitHub](https://img.shields.io/badge/project-Data_Together-487b57.svg?style=flat-square)](http://github.com/datatogether)
[![Slack](https://img.shields.io/badge/slack-Archivers-b44e88.svg?style=flat-square)](https://archivers-slack.herokuapp.com/)
[![License](https://img.shields.io/github/license/datatogether/config/.svg)](./LICENSE) 

`config` is hassle-free config struct setting for golang, setting things like
configStruct.StringField to the value of the enviornment variable STRING_FIELD.
It wraps the lovely godotenv package, which itself is a go port of the ruby
dotenv gem.

## License & Copyright

Copyright (C) 2017 Data Together
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

Technical documentation can be built with `godoc .` or, if your `$GOPATH` and 
repo structure is set up correctly, with something like `godoc -http=:6060 &` 
followed by browsing to http://localhost:6060/pkg/github.com/datatogether.

## Development

Coming soon.
