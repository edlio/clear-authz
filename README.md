# clear-authz

A simple tool to clear pending ACME v1 authorizations based upon a Certbot private ACME account key (in `private_key.json` format) and Certbot logs (from `/var/log/letsencrypt`).

## A better alternative

You may want to check out https://tools.letsdebug.net/clear-authz instead. It runs in your browser and supports both ACME v1 and ACME v2.

## Installation

This is easiest to install using `go get` like so:

    go get -u github.com/edlio/clear-authz

Alternatively, you can cross-compile for amd64 if you wish to build from source:

    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o clear-authz -v clear-authz.go

## Usage

    sudo ./clear-authz < /var/log/letsencrypt/letsencrypt.log*

### With a custom directory server (ACME v1 only)

    sudo CLEAR_AUTHZ_SERVER=acme-staging.api.letsencrypt.org ./clear-authz < /var/log/letsencrypt/letsencrypt.log*

### With a custom ACME account key
Typically the account key will be automatically located from `/etc/letsencrypt/accounts` for the nominated directory server, but you can specify the path to the `account_key.json` as the first argument.

    sudo ./clear-authz /path/to/account_key.json < ...
