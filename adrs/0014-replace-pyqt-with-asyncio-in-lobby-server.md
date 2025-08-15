# Replace PyQt with asyncio in Lobby server

* Status: accepted
* Deciders: Sheeo
* Date: 06.02.2015

## Context and Problem Statement

* The future of the Qt framework and especially its integration with Python are unknown.
* PyQt caused a few packaging issues in the past
* Python has finally its own model for handling multiple io streams: asyncio

## Decision Drivers <!-- optional -->

* Asyncio is a native part of the Python ecosystem
* PyQt is rarely used

## Considered Options

* Migrate to asyncio
* Keep using PyQt

## Decision Outcome

Chosen option: "Migrate to asyncio", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* (in theory) more performance

### Negative Consequences <!-- optional -->

* potentially new bugs introduced
