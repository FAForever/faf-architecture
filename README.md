# FAF architecture manifesto
_Last update: 12.09.2025_


This manifesto is a guideline for software development at the FAForever project and explains the general architecture rules and the reasons for these choices.

Due to over 10 years of legacy, these rules are not applied consistently. But they should be taken into account for new developments and refactoring.


## Area of application
This manifesto refers exclusively to the architecture of all server-side services and the FAF client.

The development of the base game as well as maps and mods are explicitly excluded.

## Documentation & changes

We try to implement the "architecture decision record" (ADR) pattern. To explain the landscape as-is, we are currently retroactively populating the ADRs. See the subfolder `adr`.


## Architecture
The FAF project aims for a microservice architecture with a message bus (RabbitMQ) and a shared MariaDB database.

* Microservices allow for contained, more manageable codebases that increase the chance of finding a maintainer / volunteers.
* It simplifies deployments.
* The shared database is a standalone project.
    * Isn't this an anti-pattern in Microservices? Probably. But it's here for legacy reasons, and we need to share the data a lot anyway. \
      So it still gives one big advantage:
    * It avoids multiple replicas of data and needing to keep them in sync.
    * Using the database should follow this rule: 1 writer, many readers per table.


## Technology (language and frameworks)
The FAF project is polyglot. We do not restrict ourselves to a single programming language or associated frameworks. The only mandatory requirement for backend services is deployment via containers.

However, we have to keep in mind that our developer resources are limited and some languages are far less known than others. The same applies for frameworks.

As such we would like to ask you to
* check if your requirement can be handled by 3rd party software (see buy-or-make decisions)
* stick to popular languages inside the FAF project (which are as of 2025: Java, Kotlin, Python and Rust)
* stick to well-established frameworks for these frameworks
* use existing libraries instead of reimplementing code where possible


## Buy or make-decisions

FAF aims to reduce development by utilizing established solutions.

Standard problems should be solved with standard solutions. We have a criteria catalogue to rate your choices:

* must be free software (exceptions like Server Side Public License from MongoDB or Redis are still acceptable if no other option is viable) and self-hostable
* should not require additional infrastructure (MariaDB, Postgres and RabbitMQ are available)
* should integrate with existing software via API where necessary or
* should allow adapting via custom plugins developed by FAF
* should allow single sign on via OIDC
* should be easily to deploy via Docker/Kubernetes

Known deviations from the criteria catalogue:
* The nodebb forum had no SQL backend available back then, but met the other requirements.

## API design and backwards compatibility

The FAF architecture has 3 types of APIs:

* All communication to the outside should be done via HTTP/REST.
* All service-internal messaging must use RabbitMQ with JSON based protocols.
* Each table in the FAF database schema(s) is considered its own API. (Schemas from 3rd party tools do not apply to this rule.)

Each API can have multiple consumers, and it is basically impossible to align deployments. As such, each API change should be backwards compatible. This implies:
* No removal or renaming of existing fields
* No change of type or semantics of existing fields
* Adding of fields is acceptable. All services expect/allow unknown fields.

As of now, there is no solution to announce and enforce gradual deprecation.

Know exceptions:
* ICE adapter cannot use HTTP, but uses UDP and TCP.
* The lobby server still uses raw TCP instead of HTTP for messaging.
* The replay server uses raw TCP (since all data is raw).
* The IRC server still allows connecting via TCP for compatibility (HTTP is enabled though).


## Testing
FAF has no QA department. The complexity of our landscape also makes integration testing in a real testing environment merely impossible.

As a result we have to rely on unit and integration tests on application level. This again becomes difficult for heavy UI centric applications. So focus on the business logic.


## Release

* Releases must have a workflow to build from git tags.
* Workflows must be implemented via GitHub actions.
* Deployment artifacts are container images on Docker Hub.

## Repository/project naming

Naming of repositories and project has not been aligned in the past. The new naming strategy should be this:

* FAF specific projects should start with a prefix `faf-`
* If two implementations exist, the second usually gets a middle name with the technology inolved (e.g. `faf-rust-replayserver`) 
* If we fork other projects we keep the name (e.g. `rust_ws_bridge`)
* If we build addons to non-faf projects, we lead with the name of the project (e.g. `nodebb-plugin-sso-oauth-faforever`)