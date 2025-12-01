# Rewrite lobby server in Java

* Status: rejected
* Deciders: Brutus5000
* Date: 05.01.2017

## Context and Problem Statement

The current lobby server has a lot of problems:
* It has no current active maintainer
* It is written in Python where the majority of contributors are Java experts and Java projects are massivley more 
  active (e.g. Java client, Java API)
* The ecosystem around the Python lobby server is not stable. It is a hassle to set it up on all systems and even 
  established contributors have troubles getting it to run. This drives away new contributors.
* The Python server is limited to 1 core due to Python limitations and might become a performance bottleneck
* The Java server is more open to change and e.g. already supports Galactic War infrastructure partially


The original author of this ADR has listed more reasons in the projects [readme file](https://github.com/FAForever/faf-java-server/blob/develop/readme.md#why-i-made-this). 

## Decision Drivers <!-- optional -->

* The current list of contributors and their knowledge and capacity
* The risk inherent with replacing a key component of FAF infrastructure

## Considered Options

* Keep using existing Python lobby server
* Migrate to new Java lobby server

## Decision Outcome

(Remark: The decision was made a very long time after the initial proposal)

Chosen option: "Keep using existing Python lobby server"

Reasons:

* The author of the java lobby server left FAForever project
* A new maintainer for the Python lobby server emerged.
* Even though the (remaining) core contributors are Java experts, they do not have the capacity to maintain yet another critical 
  software component.
* Despite the current Python lobby server having bugs, we have very little insight about new bugs introduced in the 
  rewrite. It could be that we just exchange one set of problems with another.
