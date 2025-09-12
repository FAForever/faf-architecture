# Rewrite Python API with Java API 

* Status: accepted
* Deciders: Downlord, Brutus5000
* Date: 22.06.2016

## Context and Problem Statement

The FAF client wants to add a lot of features for which it needs to access data from the database. 
Moderator tools also need access to data, but parts of them are private and must no be publicly accessible.
Writing dedicated code for each data request along with permissions, test etc. in the existing (Python) api is a very time consuming and error-prone process.

The Java API builds on top of a library called Elide which allows to expose the existing database model to the open for read and write, while fine graned access control and validations can be hooked in were necessary.
As Elide was the only library found capable of doing this, we plan to migrate all remaining API features from the Python API to the Java API as well and entirely replace the Python API.

## Decision Drivers <!-- optional -->

* FAF developer time is the scarcest resource
* CPU or RAM usage can be solve by throwing money at it. (It's not that bad anyway.)

## Considered Options

* Move to Java API
* Stick with existing Python API

## Decision Outcome

Chosen option: "Move to Java API"

### Positive Consequences <!-- optional -->

* Unified access to queries with standardized parameter language, pagination options etc.
* API gets auto-exposed to Swagger
* Unified audit log for changes
* Every table can be simple exposed by adding a few annotations to a Hibernate model of the table.

### Negative Consequences <!-- optional -->

* The query language of Elide is so powerful that it is possible to create very slow queries which can overwhelm the database.
* Generally queries are less optimized than hand-crafted queries.
* The database model gets tightly coupled with our API. But since we consider the database as a shared API anywhere, this is conform with the existing strategoy.
* The Swagger API is hard to understand for new developers.
