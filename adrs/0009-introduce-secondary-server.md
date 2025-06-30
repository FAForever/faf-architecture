# Introduce secondary server for vault uploads and statistics
(This is mostly guessed with the knowledge of 2025.)

* Status: superseded
* Deciders: ZePil0t
* Date: around 2013

## Context and Problem Statement

* FAF needs additional features like vault upload and statistics.
* We need to put these features "somewhere"

## Decision Drivers <!-- optional -->

* Using Python the lobby server is limited to using 1 cpu core.
* Other non-core task should not consume this limitation and should be a separate.ing connecions

## Considered Options

* Adding features to lobby server
* Creating the "secondary server"

## Decision Outcome

Chosen option: "secondary server", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* Deployments do not break running FAF games.

### Negative Consequences <!-- optional -->

* More deployment overhead
* Code cluttered around
