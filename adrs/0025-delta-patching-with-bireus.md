# Delta patching with Bireus

* Status: rejected
* Deciders: Brutus5000
* Date: 04.01.2017

## Context and Problem Statement

The current way of providing game patches is massively inefficient. Despite the usage of Xdelta3 the delta files are actually bigger than downloading the files directly. 

Bireus is a new approach to patching:
* It uses the more efficient bsdiff4 over xdelta3
* It unpacks zip files and patches the content recursively
* It saves delta patches forward and backward on major, minor and patch level

## Decision Drivers <!-- optional -->

* Download bandwith on both user side and server side is scarce
* Game patches get bigger and bigger in total size
* Game patch deltas most of the time contain only a few text files

## Considered Options

* Use Bireus
* Disable delta patching entirely

## Decision Outcome

Chosen option: "Disable delta patching entirely"

Reasons:

* The recursive patching of Zip files (extract, patch, repack) caused massive IO and CPU load and especially on slower machines was much slower than most peoples internet speed
* The new patches (forward backward with also major and minor) took much more disk space on server while server disk space is scarce.
