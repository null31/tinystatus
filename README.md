# Tinystatus

tinystatus generate an html status page via shell script.

## Features

* Parallel checks
* HTTP, ping, port checks, get text
* HTTP expected status code (401, ...)
* DNS-over-HTTPS is resolving names
* Minimal dependencies (curl, nc, jq and coreutils)
* Easy configuration and customisation
* Tiny (~1kb) optimized result page
* Incident history (manual)

## Demo

An example site is available [here](https://lab.bdro.fr/tinystatus/).

## Setup

To install tinystatus:

* Clone the repository and go to the created directory
* Edit the checks file `checks.csv`
* To add incidents or maintenance, edit `incidents.txt`
* Generate status page `./tinystatus > index.html`
* Serve the page with your favorite web server

## Configuration file

The syntax of `checks.csv` file is:
```
Command, Expected Code, Status Text, Host to check
```

Command can be:
* `http` - Check http status
* `ping` - Check ping status 
* `port` - Check open port status
* `info` - Get a simple or json format text using cURL
* `doh`  - Check DoH status

There are also `http4`, `http6`, `ping4`, `ping6`, `port4`, `port6`, `info4`, `info6`, `doh4`, `doh6`  for IPv4 or IPv6 only check.
Note: `port4` and `port6` require OpenBSD `nc` binary.
Note: `info4` and `info6` if JSON is used, then requires jq installed and a key to select the data, otherwise just fill with 0 the `Expected Code` column.
