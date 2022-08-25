---
layout: page
title: App
permalink: /app/
---

### Definitions <br/>
**Connectors** <br/>
A connector is a data source that can push and receive data on the Central Integraton Platform.  We have a number of implementation options for connectors.

1. Prebuilt connectors to many of the industry leading SaaS based products like Microsoft Dynamics and Salesforce
2. Connectors to your own company owned REST API's, Relational Databases, or FTP locations
3. Build your own connectors with the Central SDK


**Data Hubs** <br/>
A Data Hub is an implementation of what we call "event driven architecture".  What that basically means is inside of a Data Hub we have endpoints on each connector that can trigger an event.  Think of these events in the context of activity within your business - "creating a sale", "hiring a new employee", "billing the customer".  We call the trigger for an event the publisher.  In addition to the publisher you can configure connector endpoints that can listen and consume a particular event.  We call these endpoints the subscribers.

A good example of a typical Data Hub is the automation of creating a sale where my CRM system may trigger an event that an Opportunity has been won (publisher) and my financial system would receive that event and generate a Sales Order (subscriber).


**Workflows** <br/>
A Workflow is different than a Data Hub in that it has a defined start and stop with specific logic that orchestrates actions to take.  Workflows are an implementation of what we call "orchestration architecture".  Workflows on the Central Integration Platform are used in 2 main scenarios.

1. Batch processing, where usually some sort of file triggers the workflow or is produced as a result
2. Scenarios that require specific steps to be taken in a particular order that does not fit well into a Data Hub.


**API Gateway** <br/>
The API Gateway is the centerpiece of the Central Integration Platform.  All of the data that flows through Central goes through the API Gateway.  That includes all of the event messages triggered from Data Hubs and Workflows.  It also includes two features we call Webhooks and Data Providers.

- Webhooks are endpoints that can receive an event from an external party.  Webhooks can be used to receive an event from a commercial SaaS system.  Webhooks are also a good way for external partners or vendors that you may be sharing data with to send data into Central to trigger a Data Hub or Workflow.
- Data Providers give read/query access into all of your data sources from one spot.  Data Providers are great for aggregating data from multiple sources to provide functionality to custom applications, intranet pages, low code products like Power Apps.


### Connectors
Central supports really any type of data source: Web API's, Databases, SFTP, etc.  There are three main ways that we achieve this connectivity.  The first is we have a library of prebuilt connectors for many popular SaaS products like Salesforce, Microsoft Dynamics, and Oracle Netsuite.  The second is we provide the ability for customers to connect their own proprietary REST API's, SQL Server Databases, and SFTP locations into Central.  The third option is individual developers can use the Central SDK (detailed below) to build their own connectors for private use or to publish for the community.

**Adding a Connector to your environment**
From the Build menu you can select "Connectors" to manage all of the connectors for your particular environment.

![Add Connector](/images/add-connector.png "Add Connector")

### Data Hubs

### Workflows

### API Gateway

### Deployment

