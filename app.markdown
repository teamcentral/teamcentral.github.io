---
layout: page
title: App
permalink: /app/
---

### Definitions

**Connectors**

A connector is a data source that can push and receive data on the Central Integraton Platform.  We have a number of implementation options for connectors.

1. Prebuilt connectors to many of the industry leading SaaS based products like Microsoft Dynamics and Salesforce
2. Connectors to your own company owned REST API's, Relational Databases, or FTP locations
3. Build your own connectors with the Central SDK


**Data Hubs**

A Data Hub is an implementation of what we call "event driven architecture".  What that basically means is inside of a Data Hub we have endpoints on each connector that can trigger an event.  Think of these events in the context of activity within your business - "creating a sale", "hiring a new employee", "billing the customer".  We call the trigger for an event the publisher.  In addition to the publisher you can configure connector endpoints that can listen and consume a particular event.  We call these endpoints the subscribers.

A good example of a typical Data Hub is the automation of creating a sale where my CRM system may trigger an event that an Opportunity has been won (publisher) and my financial system would receive that event and generate a Sales Order (subscriber).


**Workflows**

A Workflow is different than a Data Hub in that it has a defined start and stop with specific logic that orchestrates actions to take.  Workflows are an implementation of what we call "orchestration architecture".  Workflows on the Central Integration Platform are used in 2 main scenarios.

1. Batch processing, where usually some sort of file triggers the workflow or is produced as a result
2. Scenarios that require specific steps to be taken in a particular order that does not fit well into a Data Hub.


**API Gateway**

The API Gateway is the centerpiece of the Central Integration Platform.  All of the data that flows through Central goes through the API Gateway.  That includes all of the event messages triggered from Data Hubs and Workflows.  It also includes two features we call Webhooks and Data Providers.

- Webhooks are endpoints that can receive an event from an external party.  Webhooks can be used to receive an event from a commercial SaaS system.  Webhooks are also a good way for external partners or vendors that you may be sharing data with to send data into Central to trigger a Data Hub or Workflow.
- Data Providers give read/query access into all of your data sources from one spot.  Data Providers are great for aggregating data from multiple sources to provide functionality to custom applications, intranet pages, low code products like Power Apps.

**Version Control**

We will go into more detail on version control in the Deployment Section, but as an introduction all configuration within Central is labeled based on which stage of the process it is in.

1. Live - version that is running in production
2. Draft - version that is currently in design/build phase
3. Previous Deploy - version that was running in production at some previous point in time

### Connectors
Central supports really any type of data source: Web API's, Databases, SFTP, etc.  There are three main ways that we achieve this connectivity.  The first is we have a library of prebuilt connectors for many popular SaaS products like Salesforce, Microsoft Dynamics, and Oracle Netsuite.  The second is we provide the ability for customers to connect their own proprietary REST API's, SQL Server Databases, and SFTP locations into Central.  The third option is individual developers can use the Central SDK to build their own connectors for private use or to publish for the community.

**Adding a Connector to your environment**

From the Build menu you can select "Connectors" to manage all of the connectors for your particular environment.

From the manage connectors screen in the top right you can add a connector from our existing library or you can add your own custom connectors (more on adding your own custom connectors in the SDK section below).

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 30%;"
    src="/images/add-connector.png" 
    alt="Add Connector"
/>

If you select "From Library" there is a simple two step process where you pick one of our existing connectors and then enter the details needed to connect to that particular endpoint.

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/save-connector.png" 
    alt="Add Connector"
/>

Below are detailed instructions for connecting to each data source in our library.

**Managing an existing connector**

Often time connectors need to be updated for a given situation i.e. API version upgrade, Password expiration, etc.  You can change an existing connector by clicking the "pencil" icon on an existing connector.  You can remove a connector as well by clicking the "trash" icon.  Warning that deleted connectors will impact all integrations where that connector was included. 

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/modify-connector.png" 
    alt="Modify Connector"
/>

### Data Hubs

Deciding how to design a Data Hub is largely determined by your requirements and your preferred way to logically organize your integrations.  There is no right or wrong way to do it, but the suggested thought process is to group a particular type of data like "Customers" or a particular business process "Lead to Close".

From the Build menu you can select "Data Hubs" to manage all of the Data Hubs for your particular environment.  In the top left corner you can select "Add" to add a new Data Hub.

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/add-data-hub.png" 
    alt="Add Data Hub"
/>

In the top right of the Data Hub design view is an "Actions" button.  The actions button contains all of the functionality on a Data Hub.

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 30%;"
    src="/images/data-hub-actions-button.png" 
    alt="Add Data Hub"
/>



### Workflows

### API Gateway

### Deployment

### Monitoring

### Individual Connector Instructions

Salesforce

Dynamics

Netsuite

Hubspot

BigCommerce

Payload

ADP

UKG

Taleo

Degreed

Autodesk

