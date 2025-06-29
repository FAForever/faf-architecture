# Using Python and PyQt for the lobby server 

* Status: superseded
* Deciders: ZePil0t
* Date: around 2013

## Context and Problem Statement

To emulate the GPGnet Lobby an application has to be written that allowed long-running TCP sockets.

A technology stack has to be selected.

## Decision Drivers <!-- optional -->

* The developer has skills in Python and PHP.
* Python is very popular
* PHP can not handle long running connecions

## Considered Options

* Python with PyQt
* C++ / Qt (probably)
* We have no knowledge about other options considered back then.

## Decision Outcome

Chosen option: "Python", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* Python has a low entry barrier as a programming language
* Python has a garbage collector making development easier
* Qt is a well-known stable set of networking classes
* PyQt is a bridge technology.

### Negative Consequences <!-- optional -->

* Python can only run single threaded. Should the server load ever exceed one core, other solutions must be looked at.
* Python has a weak type system (in 2013)
* PyQt is badly documented and the further development unclear
* Setting up the stack across different OS architectures is difficult
