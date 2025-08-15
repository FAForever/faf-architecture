# Introduce Python based API

* Status: superseded
* Deciders: Sheeo, Eximius
* Date: 08.04.2015

## Context and Problem Statement

* All interaction with the FAF client was either via embedded PHP pages (e.g. map vault and mod vault) with special JS logic for the client or custom TCP protocol to the lobby or secondary server.
* The web API best practices have improved and got simpler with e.g. REST and OAuth 

## Decision Drivers <!-- optional -->

* We want to provide more features to the client
* Web development is faster and easier to deploy via a separate API
* We want to deprecate the PHP code as it was unsafe (unsafe ways to check for user login data etc.)

## Considered Options

* Add new application use Python with flask
* Add more php code
* Extend lobby server tcp protocol

## Decision Outcome

Chosen option: "Add new application use Python with flask", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* faster development due to using standard libraries and tooling

### Negative Consequences <!-- optional -->

* additional architectural complexity for a transitioning period (until e.g. all PHP code can is removed)
