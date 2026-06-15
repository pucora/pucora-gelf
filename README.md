# Velonetics-gelf

[![Go Report Card](https://goreportcard.com/badge/github.com/velonetics/velonetics-gelf)](https://goreportcard.com/report/github.com/velonetics/velonetics-gelf)

A gelf (Graylog Extended Log Format) Writer for [Velonetics](https://velonetics.io) loggers.

## How to use it

This package just return a gelf writer with the configuration provided via Velonetics ExtraConfig.

You need to add the Writer to the logger writers.
This example uses [Velonetics-gologging](https://github.com/velonetics/velonetics-gologging).

Import the package

```
import "github.com/velonetics/velonetics-gelf"
```

Create a new Writer:

```
gelfWriter, err := gelf.NewWriter(cfg.ExtraConfig)
```

And add it to the logger:

```
gologging.NewLogger(cfg.ExtraConfig, gelfWriter...)
```

## Configuration

Add the `github_com/velonetics/velonetics-gelf` section to the service extra config.

There's 2 parameters:

- address (This parameter is **required**)

  The address (including the port) of your graylog server (or any service that receives gelf inputs).

- enable_tcp

  By default uses UDP but you can enable TCP by setting this option to true (not recommended, your performance may suffer).

Example:

```
"extra_config": {
  "github_com/velonetics/velonetics-gelf": {
    "address": "myGraylogInstance:12201",
    "enable_tcp": false
  }
}
```
