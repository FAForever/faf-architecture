# Use Nginx as reverse proxy

* Status: superseded
* Deciders: Sheeo
* Date: 31.01.2016

## Context and Problem Statement

* In order to have a single entrypoint for http-based applications using the same default port a reverse proxy is required

## Decision Drivers <!-- optional -->

* FAF wants to use HTTPS via Let's Encrypt TLS certificates
* FAF wants to use subdomains for its different services

## Considered Options

* Nginx
* Other options considered are unknown

## Decision Outcome

Chosen option: "Nginx", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* Nginx handled the creation and renewal of Let's Encrypt certificates automatically

### Negative Consequences <!-- optional -->

* None
