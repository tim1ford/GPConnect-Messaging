---
title: MESH
keywords: spine, mesh, integration
tags: [integration, spine, mesh]
sidebar: overview_sidebar
permalink: integration_mesh.html
summary: "Overview of the role of MESH in GP Connect messaging"
---

MESH is the strategic platform for asynchronous messaging in the NHS.

Viewed very simply, MESH is like a [post-restante](https://en.wikipedia.org/wiki/Poste_restante) service for electronic message delivery. Messages flow around the NHS using MESH as follows:

1. Sender creates message and sends to the MESH server
2. MESH server puts the message in the destination mailbox
3. Receiver retrieves the message from their inbox

For a more complete introduction to MESH, including details on how to get going if your organisation does not yet have MESH connectivity, see [MESH - Message Exchange for Health and Social Care]()

TODO: make sure there is enough info here to enable message senders to get going with connectivity and NHSD engagement.

Message senders and receivers have two options when connecting to the central MESH server: MESH API, or the MESH client.



### Message Routing to Registered Practice ###

Where message senders create messages destined for a patient's registered practice, MESH message automated message routing SHOULD be used.

Automated message routing enables a message sender to send a message to the
MESH server without specifying a destination MESH mailbox ID. MESH takes care of routing the message to the mailox of the patient's registered GP. This simplifies the task of message creation for the sending organisation.

Rather than specifying the destination mailbox ID, the message sender simply specifies the NHS Number, Surname and Date of Birth of the patient in the message header.

Refer to details below in the MESH API and MESH client for how to do this. 


TODO: Please also refer to MESH [end-point addressing]() which provides details of potential error messages returned when using automated addressing

### MESH API ###

The MESH API is a simple REST HTTP API which enables message senders to send messages through MESH. Please refer to the MESH API specification for details.

When using automated message routing, the Mex-To HTTP header must be populated according to following syntactic conventions.

`<GPPROVIDER>[delimiter]<Nhs No>[delimiter]<d.o.b>[delimiter]<Surname>`

The underscore `_` character is used as the delimeter.

Date of birth is specified in DDMMYYYY format.

For example, when sending a message about a patient Mr Brian Smith, born 14 February 2001, with NHS Number 12345678, the To_DTS field will be as:

`GPPROVIDER_12345678_14022001_Smith`

TODO: further standrd header requirements

### MESH Client ###

TODO: description of MESH client and link to doco.

When using automated message routing, the To_DTS field in the MESH message control (.ctl) file must be populated according to the same syntactic conventions described above.

TODO: further standard header requirements

### WorkflowID and Workflow Group configuration ###

Configuration rules

### Sending a MESH Message ###

Example DAT and CTL files?




