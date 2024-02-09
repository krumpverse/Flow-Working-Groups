# Inaugural Meeting [00] of the Core Protocol Working Group

**Date**: February 22, 2024 [Thursday], 10-11am PST

## Introduction

**The Core Protocol Working Group [CP-WG]**
* Introduction and overview :point_right: [README.md](../README.md)

* **Upcoming priorities:** 
  * [Path to Zero-downtime protocol upgrades](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group#path-to-zero-downtime-protocol-upgrades):
  * Translate performance improvements from new BLST-based cryptography stack to consensus block rate increase (:point_right: issue [#5302](https://github.com/onflow/flow-go/issues/5302))
  * [Recovering from Epoch-Fallback Mode [EFM] without requiring a Spork](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group#recovering-from-epoch-fallback-mode-without-requiring-a-spork)

* **Mid-term focus:**
  * [Permissionless participation of Consensus Nodes and resulting BFT requirements](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group#permissionless-participation-of-consensus-nodes-and-resulting-bft-requirements)
  * [Scaling the State to Terabytes (single snapshot)](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group#scaling-the-state-to-terabytes-single-snapshot)

**Organizational**
- Planned meeting cadence: roughly monthly
- Meeting announcements:
    - all working group meetings on [Flow Events & Working Groups](https://calendar.google.com/calendar/embed?src=c_47978f5cd9da636cadc6b8473102b5092c1a865dd010558393ecb7f9fd0c9ad0%40group.calendar.google.com&ctz=America%2FVancouver) calendar
    - Mailing list  `protocol@flow.com`
- Will use [ReadAI](www.read.ai) for meeting minutes and recordings 
- Agendas, minutes and meeting recordings tracked in

  [github.com/onflow/**Flow-Working-Groups** :point_right: `core_protocol_working_group`](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group)

**Technical contributions**
- Discord: [protocol-builders](https://discord.com/channels/613813861610684416/1108968095982293002) channel
- [forum.flow.com](https://forum.flow.com/) for exploratory discussions with technical depth

  Please use `category` [:hammer_and_wrench: Builders / Flow Protocol](https://forum.flow.com/c/builders/protocol/38)
- concrete (actionable) Flow Improvement Proposal [FLIP] in [github.com/onflow/**flips**](https://github.com/onflow/flips/)







## Agenda

Attendees:
- a
- b
- c

### [Path to Zero-downtime protocol upgrades](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group#path-to-zero-downtime-protocol-upgrades)
**Short-term goals:** _reduced_ downtime from protocol upgrades

**Status Quo:**
Strong limitations of existing Height-Coordinated Updates [HCU] for Execution Nodes [ENs]
1. only implemented for ENs
2. Requires time-sensitive (manual) coordination upfront and node operator standby during HCU
2. one time event that all affected nodes need to observe

   Failure scenario: 
    * HCU event emitted before Epoch switchover, new node joins at epoch 

3. HCU mechanism only specifies minimum software version at specific block boundary (but not max).
   Only safe if all updates are 100% downwards compatible. 
  
   Failure scenario:
   * Operator brings up node from recent historical state (pre-HCU)
   * uses latest EN image (post HCU)
   => software is happy and produces possibly wrong results 

**Future: [Dynamic Protocol State](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group#dynamic-protocol-state-as-a-foundation-for-threat-response-capabilities-eg-ban-slashed-node-revoke-compromised-keys-software-upgrades)**

The important benefit of an HCU over a spork is that there is no downtime.
Instead, at a protocol-determined height, the nodes of a specific role just reboot with a new software image and continue,
while all other node roles remain available. Nevertheless, there are some notable disadvantages to HCUs in their current form:

1. At the moment, HCUs are only supported for Execution Nodes.
2. Time-sensitive coordination is necessary for node operators to make sure their node loads the correct image after the HCU but not too early
   in case of an unforeseen crash. As software upgrades always entail some non-zero risk, all node operators need to be on standby during the HCU.
3. When all Execution Nodes reboot synchronously, transaction processing stalls for a few minutes. Nevertheless, during Execution Nodes’ HCU,
   the Flow network continues to ingest and order transaction for subsequent execution.
   Execution nodes catch up once they are back online with the new software version.

The goal of this work is (i) to extend and refine the HCU mechanism to allow updates to other node roles (i.e. remove limitation 1)
and (ii) evaluate potential avenues for rolling upgrades that do not require nodes of one role to reboot in a time-coordinated manner
(remove limitation 2 and 3 for some upgrades).

* Status: not started
* Release date: unknown
* Further reading: tbd

Design doc for technical foundation (specifically Key-Value Store as part of the Dynamic Protocol State)

HCU for all node types [crawl]

### [Path to Zero-downtime protocol upgrades](https://github.com/onflow/Flow-Working-Groups/tree/main/core_protocol_working_group#path-to-zero-downtime-protocol-upgrades)



### Key Decisions

1. D1
2. D2

### Links and further reading 



