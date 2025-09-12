# Use Flyway for database schema management

* Status: accepted
* Deciders: Sheeo, Downlord
* Date: 15.09.2016

## Context and Problem Statement

The FAF database schema on Github and on production regularly drift apart. We need strict version control for FAF that can also be tested in CI pipelines.
Flyway is an imperative way to version control any kind of database changes and is the market leader.

## Decision Drivers <!-- optional -->

* Defacto standard, well known
* easy to understand, uses plain SQL

## Considered Options

* Flyway
* We have no knowledge about other options considered back then.

## Decision Outcome

Chosen option: "Flyway"
