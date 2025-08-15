# Use Python and xdelta3 for creating a patching service

* Status: superseded
* Deciders: ZePil0t
* Date: around 2013

## Context and Problem Statement

* It's 2013 and many users still have very low bandwith (56k).
* Game patches should be as small as possible.
* Since only a few files per patch are changed, a delta between to patches would save lots of bandwith.

## Decision Drivers <!-- optional -->

* Python is well established in FAForever
* Xdelta3 is a well known algorithm and implementation for binary delta patching.

## Considered Options

* Python and Xdelta3
* We have no knowledge about other options considered back then.

## Decision Outcome

Chosen option: "Python and Xdelta3", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* (in theory) smaller downloads

### Negative Consequences <!-- optional -->

* more disk space on the server needed for the delta
* (reality) due the flaw that almost all files were zipped, delta-patching made most patches actually bigger than a fresh download
