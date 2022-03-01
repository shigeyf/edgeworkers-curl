# edgeworkers-curl

## Overview

Shell script command wrapper for cURL to enable enhanced debug headers.

ewcurl is a simple wrapper to help triggering http requests against your Akamai property which enables your EdgeWorkers applications. The script intercepts a curl command argument in order to generate a EdgeWorkers trace token as a HTTP request header by using Akamai CLI command, then uses curl to trigger a HTTP request with the HTTP request header to enable EdgeWorkers enhanced debug headers for helping you to show yoru JavaScript debugging logs.

To enable EdgeWorkers enhanced debug headers, you will need to configure your Akamai property to add a secret key. Please follow the instructions in the Akamai EdgeWorkers documentation: [Add a secret key to your property](https://techdocs.akamai.com/edgeworkers/docs/enable-enhanced-debug-headers#add-a-secret-key-to-your-property).


## CONFIGURATION

This script replies on Akamai CLI command and an `~/.edgerc` credentials file that needs to be created in your home directory and organized by [section] following the format below. Each [section] can contain a different credentials set allowing you to store all of your credentials in a single `~/.edgerc` file.

```
    [default]
    client_secret = xxxx
    host = xxxx # Note, don't include the https:// here
    access_token = xxxx
    client_token = xxxx
    max-body = xxxx

    [section1]
    client_secret = xxxx
    host = xxxx # Note, don't include the https:// here
    access_token = xxxx
    client_token = xxxx
    max-body = xxxx
```

Once you have the credentials set up you can use ewcurl.

Use the `-s` argument to specify which section from the configuration file contains the desired credentials for your Akamai CLI command in this script.

## Usage

ewcurl is a wrapper for curl command, and give the following argument to control options for ewcurl command.

```
Usage:
    ewcurl [ewcurl options] -- [curl options] [curl URL]
    optons:
       -a     (optional) Account Switch Key for Akamai CLI command.
       -h     Hostname for EdgeWorkers target property.
       -s     (optional) Section name in ~/.edgerc for Akamai CLI credential.
                         [default value is 'papi'].
```

## CHANGES

2022-03-01:
* Initial releases.
