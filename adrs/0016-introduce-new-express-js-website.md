# Introduce new Express/JS based Website with Wordpress as news backend

* Status: accepted
* Deciders: Sheeo, Blodir
* Date: 12.07.2015

## Context and Problem Statement

* The current website uses Wordpress and is very limited for our interactions
* Downloading the latest client, registration, recovering password etc. do not natively integrate

## Decision Drivers <!-- optional -->

* Wordpress allows additional features only via plugins
* The Wordpress ecosystem especially with lots of plugins has issues with updates and stability
* News still should be able to be editored by multiple users

## Considered Options

* Write a new website in Express/JS (using Wordpress as a backend for news articles)
* Keep existing Wordpress

## Decision Outcome

Chosen option: "Write a new website in Express/JS (using Wordpress as a backend for news articles)", there is no further reasoning documented.

### Positive Consequences <!-- optional -->

* more modern website

### Negative Consequences <!-- optional -->

* additional architectural complexity (wordpress remains + new app introduced)
