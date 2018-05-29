---
title: Introduction to GP Connect Messaging
keywords: homepage
tags: [getting_started]
sidebar: home_sidebar
permalink: index.html
toc: false
summary: A brief introduction to getting started with GP Connect Messaging Capabilities 
---

{% include warning.html content="This site is provided for information only and is intended for those engaged with NHS Digital in First of Type activities, other parties are advised not to develop against these specifications until a formal announcement has been made." %}

{% comment %}
[![Semver](http://img.shields.io/badge/semver-2.0.0-yellow.svg)](http://semver.org/spec/v2.0.0.html){:target="_blank" class="no_icon"} [![License](http://img.shields.io/:license-apache2-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html){:target="_blank" class="no_icon"} 
{% endcomment %}

# The GP Connect vision #

GP Connect aims to support better clinical care by opening up information and data held within GP Practice IT systems for use across health and social care. The GP Connect vision will be achieved by standardising integration and simplifying the operating model.

Find out more on the [NHS Digital GP Connect homepage](https://digital.nhs.uk/article/1275/GP-Connect).

GP Connect has initially focused on delivering HTTP FHIR&reg; APIs. The current GP Connect FHIR API specification is found at [https://nhsconnect.github.io/gpconnect/](https://nhsconnect.github.io/gpconnect/) 

An additional set of capabilities are described in this specification, whic are focuse on enabling updates to GP practice systems. 

The resulting full set of capabilities delivered through GP Connect is illustrated below:

![GP Connect capabilities - FHIR&reg; and messaging](images/overview/gpconnect_product_capabilities.png) 

## GP Connect Messaging ##

In contrast to the synchronous FHIR&reg; API approach which has been taken to enable read-only access to patient information, updates to patient data will be fulfilled through a *messaging* approach.

Update messages will:

- be sent using [MESH](https://digital.nhs.uk/services/message-exchange-for-social-care-and-health-mesh "MESH")
- use the [HL7 FHIR&reg; STU3](http://hl7.org/fhir/stu3/index.html) interoperability standard to define their structure
- include FHIR&reg; messaging information as defined by the [ITK3 message distribution](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/) standard


## Who needs to know? ##

Two main audiences will be interested in this specification:

1. Message senders: NHS organisations seeking to send messages
2. Message receivers: NHS organisations seeding to receive and process messages

This specification is primarily aimed at message senders. Where information is aimed at message receivers only, this is made clear.


## Messaging capabilities ##

Following the convention of the GP Connect FHIR&reg; API specification, GP Connect Messaging has identified three main categories of update operations as the following GP Connect Messaging *capabilities*:

1. [Send Document](senddocument.html)
2. Send Task
3. Send Update

The Send Document capability is defined in this version of the specification, with two additional capabilities as roadmap items.


{% include twitterfollow.html %}

{% include gitterbadge.html %}

