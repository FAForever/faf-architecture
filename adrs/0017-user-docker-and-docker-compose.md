# User Docker & Docker compose

* Status: superseded
* Deciders: Sheeo
* Date: 31.01.2016

## Context and Problem Statement

* Docker containers are a simple way to deploy multiple applications to the same server even if they require different (potentially confliciting) system packages
* Docker containers also isolate applications and file system access from each others and thus improve server security
* Docker compose allows specifying a whole stack of applications
* FAF uses many different applications on the same server

## Considered Options

* Migrate all applications to Docker & Docker Compose
* Run apps as before

## Decision Outcome

Chosen option: "Migrate all applications to Docker & Docker Compose", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* Simplifies setup of FAF infrastructure on local developer machines

### Negative Consequences <!-- optional -->

* All applications must be containerised, adding additional developer effort
