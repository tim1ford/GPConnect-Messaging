---
title: Send Federated Consultation Summary - Payload
keywords: use-case
tags: [use-case]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_payload.html
summary: "Details of the FHIR resource which make up the payload for the Send Federated Consultation Summary use-case."
---

Please refer to [Send Document - Payload structure](senddocument_payload) for a summary of the payload structure which SHALL be used to fulfil the "Send Federated Consultation Summary" use case.

The following sections describe the resources which form the payload. I.e. the resources which will be present as entries of the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1) resource which acts as a container for the payload. 

## Task resource ##

The [HL7 FHIR Task](https://www.hl7.org/fhir/task.html) resource is used.

A Task resource SHALL be present in the payload, and the following elements SHALL be present in the resource:

| Task resource element	| Description   |
|------|-------------|
| intent | Fixed value : *plan* |
| status | Fixed value: *requested* |
| priority | Fixed value: *routine*. This is the same value specified in the [ITK3 message header](senddocument_fedcon_itk3) |
| description |	Summary of request in the following text: *Federated GP consultation summary for patient {Patient Name} , NHS Number {NHS Number}, with details of the encounter at practice {ODS Code}* |
| for | Reference to Patient resource profiled to [https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) in the payload |
| authoredOn | The date/time when the message was generated. (A separate process such as the MESH client may be responsible for sending the message at a later date/time.) |
| requester.agent | Reference to federated practice Practitioner resource profiled to [https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) in the payload. |
| requester.onBehalfOf |Reference to federated practice Organization resource profiled to [https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) in the payload. |
| owner | Reference to registered practice Organization resource profiled to [https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) in the payload. |
| Input	| Contains embedded PDF document which describes the federated encounter in base 64 encoded format. May also contain additional binary document such as ECG record. |


## Organization Resource ##

Profiled to [https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

An Organization resource which describes the *federated* practice at which the consultation took place SHALL be present in the payload. This resource will be referenced from the `requester.onBehalfOf` element of the Task resource described above.

An Organization resource which describes the *registered* practice of the patient SHALL be present in the payload. This resource will be referenced from the `owner` element of the Task resource described above.

The table below outlines the elements which MUST be present in these Organization resource instances:

| Organization resource element	| Description |
| --------------- | ---------------|
| identifier | The `odsOrganisationCode` slice of the identifier element | 
| name | The name of the organisation |
| telecom |	The Organization resource describing the organization at which the encounter took place SHALL include the telephone number of that organization. I.e. an instance of a telecom element SHALL be present where `telecom.system` is set to a fixed value of phone, and `telecom.value` contains the telephone number |


## Practitioner Resource ##

Profiled to [https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

A Practitioner resource SHALL be present in the payload, and the following elements SHALL be present:

| Organization resource element	| Description |
| ---------------- | ---------------- |
| identifier | The `sdsUserID` slice of the identifier element | 
| Name       | The name of the practitioner. A single instance of a name element where use is official |	
| Telecom	 | MUST be present if available. |

The Practitioner resource SHALL be referenced from the `requester.agent` element of the Task resource described above

## Patient Resource ##

Profiled to [https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)

A Patient resource SHALL be present in the payload, and the following elements SHALL be present:

| Patient resource element | Description |
| --------------- | -------------- | 
| identifier |The `nhsNumber` identifier slice | 
| name | The name of the patient. A single instance of a name element where use is official |
| birthDate | Date of birth. Date shall be full date represented in YYYY-MM-DD format. Birth time is not required. |

The Patient resource SHALL be referenced from the `for` element of the Task resource described above.

These values SHALL match those specified in MESH metadata `To_DTS` field (for the MESH client) or `Mex_To` (for the MESH API) as described in [MESH message configuration](senddocument_fedcon_mesh.html)
