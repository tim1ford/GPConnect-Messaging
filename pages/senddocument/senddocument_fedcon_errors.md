---
title: Send Federated Consultation Summary - Error Handling
keywords: use-case, itk3, mesh
tags: [use-case, itk3, mesh]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_errors.html
summary: "Send Federated Consultation Summary - Error Handling"
---



## ITK Errors ##

- Where the received message does not conform to the requirements stated for [ITK3 header](senddocument_fedcon_itk3.html), or for the payload, the message SHALL be considered invalid. 
- Where a received message is invalid, an ITK3 Response SHALL be generated, with the corresponding Negative ITK3 Response Code which indicates the nature of the error, and the message SHALL NOT be accepted for downstream processing.

The table below indicates which ITK3 Negative Response should be used per error scenario:

| Error Scenario | ITK3 Negative Response Code |
| -------------- | -----------------------------|
| **ITK3 Header errors** |  |
| Mandated element not present (BusAck, InfAck, RecipientType, Priority, SenderReference, MessageDefinition, Timestamp, Event) |	10008 |
| InfAck element not set to true | 10002 |
| BusAck element not set to true | 10003 |
| RecipientType element not set to `FA` | 10010 |
| Priority element not set to `routine`	| 10006 |
| Event element not set to ITK007C | 10008 |
| **Payload business rules** |
| Payload content business rule violated | 10008 |

Where an ITK3 Response code is used, additional error context SHALL be provided in the `OperationOutcome.diagnostic` element to enable the sender to correctly identify the error which has been found in their sent message.

 
## Errors from MESH Endpoint Lookup ##

The following table describes error codes returned from the MESH server as a result of issues encountered using the facility to [route a message automatically to the registered practice](http://localhost:4006/integration_mesh.html#message-routing-to-registered-practice)

| MESH Error Code | Description |
| --------------- | ----------- |
| EPL-150 ERROR_TOO_MANY_MAILBOX_MATCHES | Multiple mailboxes matches |
| EPL-151 ERROR_NO_MAILBOX_MATCHES | No mailbox matched |
| EPL-152 ERROR_INVALID_NHSNUMBER | Invalid NHS Number |
| EPL-153 ERROR_NHSNUMBER_NOT_FOUND | NHS Number not found |
| EPL-154 ERROR_NO_DEMOGRAPHICS_MATCH |NHS Number supplied does not match the demographics |


MESH will generate these errors in the form of Transfer Reports which will be placed in the sender's mailbox to await collection and processing by the sending organisation.