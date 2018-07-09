---
title: Use of the ITK3 to support GP Connect Messaging
keywords: mesh, itk3
tags: [integration, mesh, itk3]
sidebar: overview_sidebar
permalink: integration_itk3.html
summary: "Use of ITK3 to support GP Connect Messaging"
---

## Using ITK3 to support GP Connect Messaging ##

As described in [Design Principles](design_principles.html#reliability-itk3), the ITK3 Message Distribution standard has been adopted by GP Connect Messaging capabilities to provide message reliability facilitate alignment with practice workflow.

### FHIR Messages ###

All messages sent according to the GP Connect Messaging specification will be constructed using the HL7 FHIR STU3 standard using the FHIR Messaging framework.

The ITK3 standard builds on the [FHIR Messaging framework](https://www.hl7.org/fhir/messaging.html) by through a set of messaging extensions which are provided through a [profile of FHIR MessageHeader](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-MessageHeader-2) resource. 

This extension of the FHIR messaging framework provide some messaging options such as:

- The ability for a sender to request a positive or negative "infrastructure" acknowledgement message to be returned which indicates the success or failure of the processing of the message at a technical level.
- The ability for a sender to request a positive or negative "business" acknowledgement message to be returned which indicates the success or failure of the processing of the message at a business process level.
- Various message meta-data elements

Please refer to the messaging capability and messaging use case pages for details of which of these options is mandated or recommended for the particular message being created.

### ITK3 Response processing ###

Where the message sender requests an ITK3 ackowledgement (known as ITK3 Response), the sending system is responsible for processing the received ackowledgement and acting according accordingly.

For example, where an ITK3 Response indicates that an technical error was by the receiver when validating the message, the message sender is responsible for taking the action necessary to re-send a corrected message.    