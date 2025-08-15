# Introduce ice adapter

* Status: accepted
* Deciders: Sheeo, Downlord, geosearchef
* Date: 19.06.2016

## Context and Problem Statement

* The internet is changing and getting more complicated. The old approach of port-forwarding the Forged Alliance UDP Port 6112 is no longer sufficient to establish connectivity for games across local NATs, carrier grade NATs, ipv6-ipv4 tunnels, mobile connections, ip sharing etc.
* The rate of failed connections in FAF game is rising. A better networking solution for FAF was voted the #1 priorrity topic.
* A new IETF standard in web based audio- and video-telephony arose: WebRTC with ICE (internet connectivity establishment)

## Decision Drivers <!-- optional -->

* Direct peer to peer connections are always lowest-latency compared to relay server relayed connections
* Server relay connections are they only way to guarantee success on connections.

## Considered Options

* WebRTC with data channels
* ICE with manual connection management
* VPN based solutions

## Decision Outcome

Chosen option: "ICE with manual connection management"
Originally WebRTC with data channels was the preferred solutions. However, due to its strong encryption requirements in our test cases it caused to a doubling of bandwith required. Since encryption cannot be disabled, we picked the next closest option.

VPN solutions were not convincing due to connection isolation of users and session based connection overhead.

### Positive Consequences <!-- optional -->

* There are open source relays like Coturn available

### Negative Consequences <!-- optional -->

* Manual ICE implementation is difficult and error prone
* There is only 1 real ICE only library in Java and it needs to run as a separate process
