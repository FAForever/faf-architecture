# Introduce OAuth login for clients with API as identity server

* Status: superseded
* Deciders: Downlord, Brutus5000
* Date: 27.12.2016

## Context and Problem Statement

The FAF client so far used the lobby server protocol for authentication. This does not scale for (web-)apps outside the client and also hinders adding personalized features / authorization features to the API.

Therefore we want to introduce the OAuth 2.0 security standard for api login.

## Decision Drivers <!-- optional -->

* Spring Framework used in the Java-API support builtin OAuth 2 compliant identity server almost out-of-the-box.
* External tools add additional complexity and limitations (e.g. username change)

## Considered Options

* Add OAuth identity server to the API
* Add additional service like Keycloak

## Decision Outcome

Chosen option: "Add OAuth identity server to the API"

### Positive Consequences <!-- optional -->

* Other tools could use the FAF login via OAuth as well
* OAuth login is well-documented and libraries are available for all languages

### Negative Consequences <!-- optional -->

* For a while we have 2 authentication services, as the lobby authentication still remains