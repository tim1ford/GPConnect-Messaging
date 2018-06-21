---
title: GP Connect Messaging - Design Principles
keywords: design, messaging
tags: [design,messaging]
sidebar: overview_sidebar
permalink: design_principles.html
summary: "Principles which guide the GP Connect Messaging product"
---

## Design Principles ## 

The following design principles have guided the approach to how updates to GP systems are facilitated.

### Business process integration ###

GP system suppliers have implemented rich workflow solutions to enable management of incoming healthcare events. Frequently these incoming events result in the creation of tasks with associated workflows, which are assigned in a flexible and configurable way by each practice to suite their particular requirements. These solutions provide options for practices to define how this information is treated according to message type and content - enabling the definition of rules to automate the application of updates where this is deemed appropriate.

Senders of healthcare events frequently follow business processes which include a requirement that the target organisation not only acknowledges receipt of the message, but also includes expectation of notification of workflow events which cannot immediately be generated upon message receipt.  

Therefore approach taken to facilitate updates to GP systems originating outside the practice has sought to align closely with these existing practice workflow capabilities and requirements.

### Communication paradigm: Asynchronous messaging ###

An asynchronous messaging approach offered a clearest alignment to the long-running workflow processes described above.  

An HTTP synchronous approach, as used by the GP Connect FHIR API, was considered. However a synchronous model fits best the immediacy of a request/response scenario for accress to read only GP data for a direct care use case.  For this reason, the extension of the GP Connect FHIR API to support record updates was not selected.

### Asynchronous transport: MESH ###

In selecting the transport mechanism to support an asynchronous update approach, two key criteria were in play:
- What existing capabilities are in place in the NHS to support messaging?



- What is the strategic platform for NHS asynchronous messaging.


reach - existing capability in primary care and social care.
strategic
existing capa

### Asynchronous messaging paradigm: Point-to-point ###

Candidates: pub/sub, point to point

### Reliability: ITK3 ###

Candidates: synchronous, itk3

### Re-usability: Payload re-use ###

Payload re-use



 