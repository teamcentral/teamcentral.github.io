---
layout: page
title: App
permalink: /app/
---

### Definitions

**Connectors**

A connector is a data source that can push and receive data on the Central Integraton Platform.  Think of a connector as the foundation of the house, and everything else sits on top of it.  We have a number of implementation options for connectors.

1. Prebuilt connectors to many of the industry leading SaaS based products like Microsoft Dynamics and Salesforce
2. Connectors to your company owned REST API's, Relational Databases, or FTP locations
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

- Webhooks are endpoints that can receive an event from an external party.  Webhooks can be used to receive an event from a commercial SaaS system.  Webhooks are also a good way for external partners or vendors to send data into Central to trigger a Data Hub or Workflow.
- Data Providers give read/query access into all of your data sources from one spot.  Data Providers are great for aggregating data from multiple sources to provide functionality to custom applications, intranet pages, low code products like Power Apps.

**Endpoints**

Each connector exposes what we call "Endpoints".  Endpoints are the basic capabilities exposed by a connector. Think of these capabilities as things like "Save a Sales Order", "Query for recently changed Contacts".  We will go into much more detail about how endpoints are configured, but some of the basic uses are Data Hub publishers and subscribers, Workflow triggers and actions, and API Gateway Data Providers.

**Version Control**

We will go into more detail on version control in the Deployment Section, but as an introduction all configuration within Central is labeled based on which stage of the process it is in.

1. Live - version that is running in production
2. Draft - version that is currently in design/build phase
3. Previous Deploy - version that was running in production at some previous point in time

**Central Index**

The Central Integration Platform is not just a "data mover" product.  We are a full data management platform that is actively monitoring the health of your data.  One of the key aspects in doing that is a feature we call the Central Index.  Think of the Central Index as a master database that links and cross references all of the key pieces of information that run your business.

How is this helpful?  A great example of that is a pretty typical automation we perform for generating Sales Orders in your financial system.  A Sales Order can be a somewhat complex data structure.  It has the basic information like the Order Date, but it also holds references to many other pieces of information spread across your business - Sales Rep, Customer, Region/Area of the Business the Order was placed for, Products/Services being purchased.  The Central Index plays a large role in aggregating master data across systems so that when an automation like "Creating a Sales Order" is executing in your financial system all of those bits of information mentioned above can be set appropriately.

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

From the Build menu you can select "Data Hubs" to manage all of the Data Hubs for your particular environment.  In the top left corner you can select "Add" to add a new Data Hub.  All Data Hubs are created initially as Drafts and will not be flipped to Live until it is ready for production.

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
    alt="Actions"
/>

**Add Endpoint**

Adding an endpoint is a simple 3 step process.
1. Select your connector - pick from the existing connectors you have configured
2. Give the endpoint a name and select your data source - the data source is the type of data provided by the connector i.e. Customers, Orders, Invoices, Employees
3. Pick the type of connector - for a Data Hub this is going to be publisher (pushes data), subscriber (receives data), both (bi-directional)

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/add-endpoint.png" 
    alt="Add Endpoint"
/>


**Manage Drop Downs**

A Drop Down is a type of Cross Reference and Master Data Management capability within Central.  Think of a scenario where you are synchronizing something like an Employee from your HRIS to your ERP, and part of that Employee data you want replicated into the ERP is the Job Title.  A Drop Down allows you to store the values of that Job Title across your HRIS and ERP so that when that Employee record gets written to the ERP the correct Job Title Id is selected.

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/manage-drop-downs.png" 
    alt="Manage Drop Downs"
/>

Each Drop Down value is name value pair just like what would show up in a "drop down" list in an application.  The Name and System are used to match the correct value for the connector that is executing the logic.

Every Drop Down Field is associated inside the Data Hub with a particular Entity Type, which in this case for a Job Title is a "Person".  Also the Field Name of the Drop Down MUST have the same name as the Foreign Key field it is mapped to.  More on field mapping below under Endpoint Configuration.

**View Code**

It is not actual code.  Think of this as the configured instructions that you want your Data Hub to interpret and execute.  The "View Code" capability allows you to see the raw Json that the App is maintaining.  View Code can also be used for more advanced platform features that we have not yet included in the UI.

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/code-view.png" 
    alt="Code View"
/>


**View Current Draft/Live**

If you have both a current Draft and Live version of the Data Hub this allows you to flip back and forth across both versions.

**Deploy**

If you are viewing a Draft version of the Data Hub you can deploy directly from the Build screens.  This will do the same thing as deploying from the actual Deploy screens.

**Delete Data Hub**

If a Data Hub is no longer needed it can be deleted.  If a Data Hub is accidentally deleted it can always be recovered by making a support request.

### Workflows

As mentioned above in the definitions Workflows are used in two specific cases within Central.  

1. For batch oriented processing that usually requires some sort of file upload or download
2. For automations that require a more structured or orchestrated set of steps that would not work well within a Data Hub.

It is important to note that currently the design view for Workflows only works with Scenario #1.  If your use case requires Scenario #2 someone on the Central support team can assist in building that out.

There a 3 main constructs that make up a Central Workflow.
1. Trigger - the event that starts a workflow, Triggers can fire based on a schedule or based on a real time event with a webhook
2. Step - there are two types of Steps, General Steps are just a logical way to group Actions and organize your Workflow, Conditional Steps are a way to establish logic in your Workflow i.e. If This Then That
3. Action - code that can be executed on a particular Connector End Point, there are 3 types of Actions, Save Actions can process a save much like a Data Hub and then save any keys back to the Central Index, Set Data Actions can mutate the data that is running through the Workflow adding additional data to it, Simple Execute Actions are actions that just fire and have not return value i.e. Send an Email, Execute a Power Shell script

From the Build menu you can select "Workflows" to manage all of the Workflows for your particular environment.  In the top left corner you can select "Add" to add a new Workflow.  All Workflows are created initially as Drafts and will not be flipped to Live until it is ready for production.

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/add-workflow.png" 
    alt="Add Workflow"
/>

In the top right of the Workflow design view is an "Actions" button.  The actions button contains all of the functionality on a Workflow.  The action button for Workflow has some of the same capability as Data Hub - Code View, Deploy, Flip between Versions.

**Add Trigger**

The user experience for adding a Trigger to your Workflow is the same as adding a Data Hub Endpoint.  Select a Connector, give the Trigger a Name and Data Source, and then select the type of Trigger.

<img 
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 80%;"
    src="/images/add-workflow-trigger.png" 
    alt="Add Workflow Trigger"
/>

### API Gateway

### Endpoint Configuration

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

