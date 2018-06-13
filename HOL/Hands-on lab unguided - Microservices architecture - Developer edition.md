![](images/HeaderPic.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Microservices architecture - Developer edition
</div>

<div class="MCWHeader2">
Hands-on lab unguided
</div>

<div class="MCWHeader3">
June 2018
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Microservices architecture -- developer edition hands-on lab unguided](#microservices-architecture----developer-edition-hands-on-lab-unguided)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Overview](#overview)
    - [Solution architecture](#solution-architecture)
    - [Requirements](#requirements)
    - [Exercise 1: Environment setup](#exercise-1-environment-setup)
        - [Task 1: Download and open the ContosoEventsPoC starter solution](#task-1-download-and-open-the-contosoeventspoc-starter-solution)
            - [Tasks to complete:](#tasks-to-complete)
            - [Exit criteria:](#exit-criteria)
        - [Task 2: API Management](#task-2-api-management)
            - [Tasks to complete:](#tasks-to-complete-1)
            - [Exit criteria:](#exit-criteria-1)
        - [Task 3: Web App](#task-3-web-app)
            - [Tasks to complete:](#tasks-to-complete-2)
            - [Exit criteria:](#exit-criteria-2)
        - [Task 4: Function App](#task-4-function-app)
            - [Tasks to complete:](#tasks-to-complete-3)
            - [Exit criteria:](#exit-criteria-3)
        - [Task 5: Storage account](#task-5-storage-account)
            - [Tasks to complete:](#tasks-to-complete-4)
            - [Exit criteria:](#exit-criteria-4)
        - [Task 6: Cosmos DB](#task-6-cosmos-db)
            - [Tasks to complete:](#tasks-to-complete-5)
            - [Exit criteria:](#exit-criteria-5)
    - [Exercise 2: Implementing the Service Fabric solution](#exercise-2-implementing-the-service-fabric-solution)
        - [Task 1: Interacting with an Actor's State](#task-1-interacting-with-an-actors-state)
            - [Tasks to complete:](#tasks-to-complete-6)
            - [Exit criteria:](#exit-criteria-6)
        - [Task 2: Interacting with a Stateful Service](#task-2-interacting-with-a-stateful-service)
            - [Tasks to complete:](#tasks-to-complete-7)
            - [Exit criteria:](#exit-criteria-7)
        - [Task 3: Interacting with an Actor from a Web API Controller](#task-3-interacting-with-an-actor-from-a-web-api-controller)
            - [Tasks to complete:](#tasks-to-complete-8)
            - [Exit criteria:](#exit-criteria-8)
        - [Task 4: Inspecting Service Partitions](#task-4-inspecting-service-partitions)
            - [Tasks to complete:](#tasks-to-complete-9)
            - [Exit criteria:](#exit-criteria-9)
    - [Exercise 3: Placing ticket orders](#exercise-3-placing-ticket-orders)
        - [Task 1: Run the solution](#task-1-run-the-solution)
            - [Tasks to complete:](#tasks-to-complete-10)
            - [Exit criteria:](#exit-criteria-10)
        - [Task 2: Test the application](#task-2-test-the-application)
            - [Tasks to complete:](#tasks-to-complete-11)
            - [Exit criteria:](#exit-criteria-11)
        - [Task 3: Service Fabric Explorer](#task-3-service-fabric-explorer)
            - [Tasks to complete:](#tasks-to-complete-12)
            - [Exit criteria:](#exit-criteria-12)
        - [Task 4: Set up the Ticket Order Sync queue](#task-4-set-up-the-ticket-order-sync-queue)
            - [Tasks to complete:](#tasks-to-complete-13)
            - [Exit criteria:](#exit-criteria-13)
        - [Task 5: Set up the functions](#task-5-set-up-the-functions)
            - [Tasks to complete:](#tasks-to-complete-14)
            - [Exit criteria:](#exit-criteria-14)
        - [Task 6: Test order data sync](#task-6-test-order-data-sync)
            - [Tasks to complete:](#tasks-to-complete-15)
            - [Exit criteria:](#exit-criteria-15)
    - [Exercise 4: Publish the Service Fabric Application](#exercise-4-publish-the-service-fabric-application)
        - [Task 1: Publish the application](#task-1-publish-the-application)
            - [Tasks to complete:](#tasks-to-complete-16)
            - [Exit criteria:](#exit-criteria-16)
        - [Task 2: Test an order from the cluster](#task-2-test-an-order-from-the-cluster)
            - [Tasks to complete:](#tasks-to-complete-17)
            - [Exit criteria:](#exit-criteria-17)
    - [Exercise 5: API Management](#exercise-5-api-management)
        - [Task 1: Import API](#task-1-import-api)
            - [Tasks to complete:](#tasks-to-complete-18)
            - [Exit criteria:](#exit-criteria-18)
        - [Task 2: Retrieve the user subscription key](#task-2-retrieve-the-user-subscription-key)
            - [Tasks to complete:](#tasks-to-complete-19)
            - [Exit criteria:](#exit-criteria-19)
        - [Task 3: Configure the Function App with the API Management key](#task-3-configure-the-function-app-with-the-api-management-key)
            - [Tasks to complete:](#tasks-to-complete-20)
            - [Exit criteria:](#exit-criteria-20)
    - [Exercise 6: Configure and publish the web application](#exercise-6-configure-and-publish-the-web-application)
        - [Task 1: Configure the web app settings](#task-1-configure-the-web-app-settings)
            - [Tasks to complete:](#tasks-to-complete-21)
            - [Exit criteria:](#exit-criteria-21)
        - [Task 2: Running the web app and creating an order](#task-2-running-the-web-app-and-creating-an-order)
            - [Tasks to complete:](#tasks-to-complete-22)
            - [Exit criteria:](#exit-criteria-22)
        - [Task 3: Publish the web app](#task-3-publish-the-web-app)
            - [Tasks to complete:](#tasks-to-complete-23)
            - [Exit criteria:](#exit-criteria-23)
    - [Exercise 7: Upgrading](#exercise-7-upgrading)
        - [Task 1: How upgrade works](#task-1-how-upgrade-works)
        - [Task 2: Update an actor state](#task-2-update-an-actor-state)
            - [Tasks to complete:](#tasks-to-complete-24)
            - [Exit criteria:](#exit-criteria-24)
        - [Task 3: Perform a smooth upgrade](#task-3-perform-a-smooth-upgrade)
            - [Tasks to complete:](#tasks-to-complete-25)
            - [Exit criteria:](#exit-criteria-25)
        - [Task 4: Submit a new order](#task-4-submit-a-new-order)
            - [Tasks to complete:](#tasks-to-complete-26)
            - [Exit criteria:](#exit-criteria-26)
    - [After the hands-on lab](#after-the-hands-on-lab)
            - [Tasks to complete:](#tasks-to-complete-27)
            - [Exit criteria:](#exit-criteria-27)

<!-- /TOC -->

# Microservices architecture -- developer edition hands-on lab unguided

## Abstract and learning objectives

This whiteboard design session is designed to help attendees gain a better understanding of implementing architectures leveraging aspects from microservices and serverless architectures, by helping an online concert ticket vendor survive the first 5 minutes of crushing load. They will handle the client\'s scaling needs through microservices built on top of Service Fabric, and apply smooth updates or roll back failing updates. Finally, students will design an implementation of load testing to optimize the architecture for handling spikes in traffic.

Attendees will learn how to:

-   Implement scale and resiliency with Service Fabric

-   Enable serverless solutions with Azure Functions

-   Control API access with API Management

-   Provide query flexibility with Cosmos DB

## Overview

Contoso Events is an online service for concerts, sporting and other event ticket sales. They are redesigning their solution for scale with a microservices strategy and want to implement a POC for the path that receives the most traffic: ticket ordering.

In this hands-on lab, you will construct an end-to-end POC for ticket ordering. You will leverage Service Fabric, API Management, Function Apps, Web Apps, and Cosmos DB.

![The Event Ticket sales flowchart begins with Azure AD B2C, which points to Contoso Events Site Web App. A bi-directional arrow points between the Web App and API Manager, which in turn has a bi-direction arrow pointing between it and Web API (Stateless Service). An arrow points from there to Ticket Order Service (Stateful Service), which points to Ticket Order Actor (Processor). The Web API, Ticket Order Service, and Ticket Order Actor are all part of the Contoso Events Service Fabric App. from Ticket Order Actor, an arrow points to Order Externalization (Queue), then on to Process Order Externalization (Azure Function), and ends at Cosmos DB (Orders Collection). ](images/Labs/image2.png "Event Ticket sales flowchart")

## Solution architecture

The following figures are intended to help you keep track of all the technologies and endpoints you are working with in this hands-on lab. The first figure is the overall architecture, indicating the Azure resources to be employed. The second figure is a more detailed picture of the key items you will want to remember about those resources as you move through the exercises.

![Diagram of the preferred solution (just one of many viable options). From a high-level, Contoso Events applications will consume back-end APIs managed through API Management, authenticating users with tokens issued by Azure AD B2C. API requests will go through Azure Load Balancer, and distribute across Service Fabric nodes. Business functionality will be implemented through stateful services and actors, and Azure Functions will handle processing the queues and updating Cosmos DB.](images/Labs/image3.png "Preferred solution diagram")

![This illustration lists key items to remember, which include: Profiles, Application, Queues, TicketManager DB, Functions, APIM Endpoints, Web App, Cluster Endpoints, and Local Endpoints. At this time, we are unable to capture all of the information in the illustration. Future versions of this course should address this.](images/Labs/image4.png "Key items to remember illustration")

## Requirements

1.  Microsoft Azure subscription must be pay-as-you-go or MSDN.

    a.  Trial subscriptions will not work.

2.  A virtual machine configured with (see Before the hands-on lab):

    b.  Visual Studio 2017 Community edition, or later

    c.  Azure Development workload enabled in Visual Studio 2017 (enabled by default on the VM)

    d.  Service Fabric SDK 3.1 or later for Visual Studio 2017

    e.  Google Chrome browser (Swagger commands do not work in IE)

    f.  PowerShell 3.0 or higher (v5.1 already installed on VM)

## Exercise 1: Environment setup

Duration: 30 minutes

Contoso Events has provided a starter solution for you. They have asked you to use this as the starting point for creating the Ticket Order POC solution with Service Fabric.

Because this is a "born in Azure" solution, it depends on many Azure resources. You will be guided through creating those resources before you work with the solution in earnest. The following figure illustrates the resource groups and resources you will create in this exercise.

![The Starter Solution begins with a Start button, with two arrows pointing to two different Resource Groups. The first Resource group includes only the Function App. The second Resource group includes the following resources: Service Fabric Cluster, API Management, Azure AD B2C, Web App, Storage Account, and Cosmos DB.](images/Labs/image42.png "Starter Solution Resources")

### Task 1: Download and open the ContosoEventsPoC starter solution

#### Tasks to complete:

1.  On your Lab VM, download the starter project from <http://bit.ly/2t1HhbS>. (Note: the URL is case sensitive, so you may need to copy and paste it into your browser's address bar.)

2.  Unzip the contents to the folder C:\\handsonlab.

3.  Open the ContosoEventsPoc.sln with Visual Studio.

4.  Before you compile the solution, set the configuration to x64.

#### Exit criteria:

-  You cannot successfully build the solution.

> **Note**: If you have the prerequisites on your VM, this solution should open without requesting additional software to be installed. You should have some compile-time errors at this point. These are expected, and will be fixed as you proceed with the hands-on lab.

### Task 2: API Management

In this task, you will provision an API Management Service in the Azure portal.

#### Tasks to complete:

1.  Create a new API Management service with a URL like 'contosoevents-SUFFIX', in the same region you used previously. Use Developer pricing tier.

#### Exit criteria:

-  After the service is provisioned, it will be listed in the API management list in the portal. This may take up to 10-15 minutes, so move to Task 3 and return later to verify.

### Task 3: Web App

In these steps, you will provision a Web App in a new App Service Plan.

#### Tasks to complete:

1.  Provision a web app to host the website. Create an App Service Plan in the Resource Group and region you used previously. Name the Web App something like 'contosoeventsweb-SUFFIX'.

2.  Select pricing tier S1 Standard.

#### Exit criteria:

-  You can navigate to your new Web App at the URL you noted earlier based on your Web App name such as <https://contosoeventsweb-SUFFIX.azurewebsites.net>. You should see an empty website.

### Task 4: Function App

In this task, you will provision a Function App using a Consumption Plan. By using a Consumption Plan, you enable dynamic scaling of your Functions.

#### Tasks to complete:

1.  Provision a Function App to host the functions in the Visual Studio solution, in a Consumption Plan. Create a new Resource Group with a name similar to your main Resource Group such as 'contosoeventsfn-SUFFIX'.

2.  Name the App something like 'contosoeventsfn-SUFFIX'.

#### Exit criteria:

-  When the provisioning completes, your Web App and Function App are listed in the Azure Portal.

### Task 5: Storage account

In this section, you will create a Storage account for the application to create and use queues required by the solution.

#### Tasks to complete:

1.  Provision a Resource Manager based Storage account of type Standard LRS in the same Location and Resource Group as your other services.

2.  Name it something like 'contosoeventsSUFFIX'.

#### Exit criteria:

-  After provisioning is complete, the Storage account will be listed in the Azure Portal.

### Task 6: Cosmos DB

In this section, you will provision a Cosmos DB account, a Cosmos DB Database and a Cosmos DB collection that will be used to collect ticket orders.

#### Tasks to complete:

1.  Provision a new Cosmos DB account in the same region and Resource Group as your other services. Use the name 'contosoeventsdocdb-SUFFIX'.

2.  Add a database with ID 'TicketManager'.

3.  Add two collections named 'Orders' and 'Events'.

#### Exit criteria:

-  You will be able to see the two collections in the new database.

## Exercise 2: Implementing the Service Fabric solution

Duration: 60 minutes

The agreed upon design with Contoso Events involves queuing ticket orders, and executing them asynchronously. A stateless Web API service receives the request, and queues it to a stateful service. An actor processes the request, and persists the order in its state.

The design also calls for saving the state of the ticket order to a Cosmos DB collection for ad hoc queries. This exercise will guide you through adding configurations that will light up the actor code that externalizes its state to a storage queue. In addition, you will set up the Function App to read from the queue, and persist the order to the Orders collection of the Cosmos DB instance you created.

> Note: The code to write to the storage queue is already in place within the actor, so setting up configuration keys is the only requirement to lighting up that feature.

![The Ticket Ordering flowchart starts with Web API (Stateless Service). An arrow points to Ticket Order Service (Stateful Service), then to Ticket Order Actor (Processor). These three items make up the Contoso Events Service Fabric App. From Ticket Order Actor, an arrow points to Order Externalization (Queue). The next step is Process Order Externalization (Azure Function), and ends with Cosmos DB (Orders Collection).](images/Labs/image67.png "Ticket Ordering flowchart")

### Task 1: Interacting with an Actor's State

In this task, you will write code to process the cancellation of an order by interacting with the Ticket Order Actor. To cancel an order, a Ticket Order Actor instance must be retrieved, and the CancelTicket operation it provides is invoked that changes the actor's state to reflect a "canceled" status.

#### Tasks to complete:

1.  With the ContosoEventsPoC solution open in Visual Studio, using Solution Explorer navigate to TicketOrderActor.cs underneath the ContosoEvents.TicketOrderActor project.

2.  Locate the CancelOrder method.

3.  Locate and complete the lines commented with //TODO: Task 1.1 to //TODO: Task 1.5

4.  Save TicketOrderActor.cs.

#### Exit criteria:

-  All TODOs in TicketOrderActor.cs should be addressed.

### Task 2: Interacting with a Stateful Service

In this task, you will write code to enqueue an order to the Ticket Order Stateful Service whenever and order is being processed. This Order is enqueued by the Web API and then dequeued by the Ticket Order Stateful Service for processing by the Ticket Order Actor. To accomplish this, the order will be enqueued into a reliable queue.

#### Tasks to complete:

1.  Using Solution Explorer navigate to TicketOrderService.cs underneath the ContosoEvents.TicketOrderService project.

2.  Locate the EnqueueOrder method.

3.  Locate and complete the lines commented with //TODO: Task 2.1 to //TODO: Task 2.4

4.  Save TicketOrderService.cs.

#### Exit criteria:

-  All TODOs in TicketOrderService.cs should be addressed

### Task 3: Interacting with an Actor from a Web API Controller

In this task, you will write code that runs within the Orders Web API controller that delegates the cancellation request to the actor.

#### Tasks to complete:

1.  Using Solution Explorer navigate to TicketOrderService.cs underneath the Controllers folder in the ContosoEvents.WebApi project.

2.  Locate the CancelOrder method.

3.  Locate and complete the lines commented with //TODO: Task 3.1 to //TODO: Task 3.3

4.  Save TicketOrderService.cs.

#### Exit criteria:

-  All TODOs in TicketOrderService.cs controller should be addressed

### Task 4: Inspecting Service Partitions

In this task, you will write code that runs within the Admin Web API controller that uses the Fabric Client to get information about all the Ticket Order Service partitions.

#### Tasks to complete:

1.  Using Solution Explorer navigate to AdminControllers.cs underneath the Controllers folder in the ContosoEvents.WebApi project.

2.  Locate the GetTicketOrderPartitions method.

3.  Locate and complete the lines commented with //TODO: Task 4.1 to //TODO: Task 4.2

4.  Save AdminControllers.cs.

#### Exit criteria:

-  All TODOs in AdminControllers.cs should be addressed

## Exercise 3: Placing ticket orders

Duration: 30 minutes

In this exercise, you will test that your completed solution works by running locally on your Lab VM.

### Task 1: Run the solution

The purpose of this task is to make sure that the source code compiles, and that you can publish to a local cluster. To make sure that the app is running flawlessly, you will run some API tests and access the Service Fabric explorer.

Note: Not all features are in place, but you will be able to see that the application can run.

#### Tasks to complete:

1.  First, make sure the local Service Fabric environment is running. If not, set up the local cluster.

2.  From Visual Studio, compile the solution and publish ContosoEventsApp to the local Service Fabric cluster.

#### Exit criteria:

-  In Visual Studio view the publish status. After it shows that it succeeded, the application is ready to be used.

### Task 2: Test the application

The Service Fabric Application includes a front-end Web API as the public-facing window to internal stateful services. In this task, you will check that you can call the Web API now that you have the application published to the local cluster. Because the app is not yet fully configured, not all Web API methods will be fully functional.

#### Tasks to complete:

1.  Browse to the Swagger endpoint for the Web API at: <http://localhost:8082/swagger/ui/index>

2.  Select the Admin API and select the method /api/admin/partitions. This returns the number of tickets queued across all partitions.

#### Exit criteria:

-  If you were able to view the Swagger definition and select the partitions method with a successful response, your environment is in a good state to continue.

### Task 3: Service Fabric Explorer

In this task, you will browse to the Service Fabric Explorer, and view the local cluster.

#### Tasks to complete:

1.  Browse to the Service Fabric Explorer for the local cluster at: <http://localhost:19080/Explorer/index.html>

2.  Observe the services deployed with the application.

#### Exit criteria:

-  If you are able to access the Service Fabric Explorer, your environment is in a good state to continue.

### Task 4: Set up the Ticket Order Sync queue

In this task, you will complete features of the Contoso Events POC so that placing an order also syncs with the back-end data store. You will also update the configuration settings to reference the Azure resources you previously created correctly.

#### Tasks to complete:

1.  Update Local.xml in the ApplicationParameters folder with your own configuration parameters for the following items:

    ```
        <Parameter Name="DataStorageEndpointUri" Value="" />
        <Parameter Name="DataStoragePrimaryKey" Value="" />
        <Parameter Name="StorageConnectionString" Value="" />
    ```

2.  Set DataStorageEndpointUri to the Cosmos DB endpoint Uri.

3.  Set DataStoragePrimaryKey to the Cosmos DB Primary Key.

4.  Set StorageConnectionString to the connection for your storage account in this format:

    ```
        DefaultEndpointsProtocol=https;AccountName=ACCOUNTNAME;AccountKey=KEY1
    ```

5.  Rebuild and publish the application to the local cluster.

6.  Browse to the local Swagger endpoint and test the POST /api/orders method by posting the following JSON formatted order payload:

    ```
        {
        "UserName": "johnsmith",
        "Email": "john.smith@gmail.com",
        "EventId": "EVENT1-ID-00001",
        "PaymentProcessorTokenId": "YYYTT6565661652612516125",
        "Tickets": 3
        }
    ```

#### Exit criteria:

-  In Visual Studio, open the Cloud Explorer, navigate to the externalization queue, and verify that the new order is in the queue.

### Task 5: Set up the functions

In this task, you will create a function that will be triggered by the externalization queue we created for the app. Each order that is deposited to the queue by the TicketOrderActor type will trigger the ProcessOrderExternalizations function. The function then persists the order to the Orders collection of the Cosmos DB instance.

You will also create a second function that will be used to generate load against the system at runtime. Overall, the ContosoEvents app has the following queue and function architecture. This should help you visualize how the queues and functions are related.

![The ContosoEvents app architecture has two columns - Cosmos DB (Data Store), and Contoso Events (Web API). It also has three rows - Azure Functions, Azure Storage Queues, and Queue Sources. For Cosmos DB, its order of flow begins with Ticket Order Actor, Queue Source. An arrow then points up from Ticket Order Actor to Order Externalization (Its Azure Storage Queue), which then points up to Process order externalization (its Azure Function), which points to its endpoint, Cosmos DB Data Store. For Contoso Events, its order of flow begins with Service Fabric App, its Queue Source. An arrow then points up from there to Order Simulation (Its Azure Storage Queue), which then points up to Process order simulation (its Azure Function), which points to its endpoint, Contoso Events (Web API). its Azure Function is to process order simulization, Its Azure Storage Queue is Order Simulation, and its Queue Source is Service Fabric App. ](images/Labs/image101.png "ContosoEvents app architecture")

#### Tasks to complete:

1.  From the Azure portal, find the Function App you created previously.

2.  Create a function called 'ProcessOrderExternalizations' based on the QueueTrigger C\# template. Select the queue contosoevents-externalization-requests. Connect it to the Storage account created previously.

3.  Select Azure Storage Queue as the trigger and select the queue name contosevents-externalization-requests.

4.  Connect the output to the Orders collection of the Cosmos DB instance you created previously.

5.  Copy the code from the ProcessTicketOrderExternalizationEvent.cs file in the solution.

6.  Create the ProcessSimulationRequests function from the QueueTrigger PowerShell template. Name the queue contosevents-simulation-requests.

7.  There is no need to connect this function to an output. Copy the code from the ProcessOrderTicketSimulationRequest.PS1 file in the solution.

8.  You will set up the API Management key in a later step when we use this function.

#### Exit criteria:

-  If each function successfully compiled as you went through these steps, you are ready to proceed to the next exercise.

### Task 6: Test order data sync

In this task, you will test the ticket order processing back-end, to validate that orders are queued and processed by the ProcessOrderExternalizations function -- ultimately saving the order to the Orders collection of the Cosmos DB instance.

#### Tasks to complete:

1.  Open the logs for the ProcessOrderExternalizations function.

2.  Process an order following your steps on Task 4. Note the order id that appears in the logs.

3.  From the Azure portal, navigate to your Cosmos DB account and use query explorer to query the Orders collection for the order id.

#### Exit criteria:

-  If the Cosmos DB query returns the order id specified, the order has been fully processed through to the Cosmos DB.

## Exercise 4: Publish the Service Fabric Application

Duration: 15 minutes

In this exercise, you will publish the Service Fabric Application to the Azure cluster you created previously. After it is deployed, you will validate it by sending orders through the Web API endpoints exposed from the cluster.

### Task 1: Publish the application

In this task, you will deploy the application to a hosted Service Fabric Cluster.

#### Tasks to complete:

1.  Open the Cloud.xml configuration file for the ContosoEventsApp project and validate that the settings modified in Exercise 2 also match this file.

2.  Verify the TicketOrderService\_PartitionCount is set to 5.

3.  Publish the application using the Cloud.xml configuration to the cluster you created previously.

#### Exit criteria:

-  From the Visual Studio output window, you can validate that the deployment has completed with success.

### Task 2: Test an order from the cluster

In this task, you will test an order against your application deployed to the hosted Service Fabric Cluster.

#### Tasks to complete:

1.  From the browser, navigate to the Swagger endpoint for the deployed application. The URL is made of:

    > <http://contosoeventssf-SUFFIX.eastus.cloudapp.azure.com:8082/swagger/ui/index>

2.  POST an order to the Order API /api/orders endpoint using this JSON:

    ```
        {
        "UserName": "johnsmith",
        "Email": "john.smith@gmail.com",
        "Tag": "Manual",
        "EventId": "EVENT1-ID-00001",
        "PaymentProcessorTokenId": "YYYTT6565661652612516125",
        "Tickets": 3
        }
    ```

#### Exit criteria:

-  Verify that the order has persisted to the Orders collection. From the Azure Portal, find your Cosmos DB account that you previously created. Perform a query as you did previously to verify that the order exists in the collection.

## Exercise 5: API Management

Duration: 15 minutes

In this exercise, you will configure the API Management service in the Azure portal.

### Task 1: Import API

In this task, you will import the Web API description to your API Management service to create an endpoint.

#### Tasks to complete:

1.  From the Azure Portal, select the API Management Service that you created earlier.

2.  Import the API that was deployed to the Service Fabric cluster.

3.  Associate the "Unlimited" product.

    > **Note**: You would typically create a new product subscription for each environment in a scenario like this one. For example, Development, Testing, Acceptance and Production (DTAP) and issue a key for your internal application usage for each environment, managed accordingly.

#### Exit criteria:

-  You will see your API listed under All APIs.

### Task 2: Retrieve the user subscription key

In this task, you will retrieve the subscription key for the client applications to call the new API Management endpoint.

#### Tasks to complete:

1.  Return to the API Management dashboard for the same service. Select the publisher portal link and navigate from there to the developer portal.

2.  Reveal the primary key of the "Unlimited" subscription, storing that info for future usage.

#### Exit criteria:

-  You can view the revealed key and save it for other configuration steps.

### Task 3: Configure the Function App with the API Management key

In this task, you will provide the API Management key in a setting for the Function App, so it can reach the Web API through the API Management service.

#### Tasks to complete:

1.  From the Azure Portal browse to the Function App. Create an application setting called 'contosoeventsapimgrkey' and set the value to the API Management key you saved in the previous step.

#### Exit criteria:

-  You will be able to issue a request from the website, and see that orders have been processed through the function -- as it will have successfully called the API and you will see results in the reports page.

## Exercise 6: Configure and publish the web application

Duration: 15 minutes

In this exercise, you will configure the website to communicate with the API Management service, deploy the application, and create an order.

### Task 1: Configure the web app settings

In this task, you will update configuration settings to communicate with the API Management service. You will be guided through the instructions to find the information necessary to populate the configuration settings.

#### Tasks to complete:

1.  Open the web.config for the ContosoEvents.Web project.

2.  For the apimng:BaseUrl enter the base URL of the API you created in API Management such as <https://contosoeventsSUFFIX.azure-api.net/events/>. Make sure to include the closing /.

3.  For the apimng:SubscriptionKey enter the subscription key you revealed in API Management developer portal.

#### Exit criteria:

-  You should have values for the API Management app settings.

### Task 2: Running the web app and creating an order

In this task, you will test the web application calls to API Management by creating an order through the UI.

![The Contoso Events website displays, with information about the Seattle Rock and Rollers concert tickets. At the bottom of the page is the Order tickets now button.](images/Labs/image158.png "Contoso Events website")

#### Tasks to complete:

1.  From Visual Studio, run the ContosoEvents.Web application.

2.  Place an order from the website, filling in the missing billing fields.

#### Exit criteria:

-  Once the order is queued for processing, you will be redirected to a results page indicating Success and showing you your order id that was queued as confirmation.

### Task 3: Publish the web app

In this task, you will publish the web application to Azure.

#### Tasks to complete:

1.  Publish the application to the Azure Web App you created previously named something like 'contosoeventsweb-SUFFIX'.

#### Exit criteria:

-  When publishing is complete, your browser will launch and navigate to the deployed Web app home page. You can optionally submit another order to validate functionality works as in Task 2.

## Exercise 7: Upgrading

Duration: 30 minutes

In this task, you will make changes to the code, and deploy an update to the application to enhance functionality. Specifically, the update addresses the area of concern related to changes in the ticket order model, and the impact on the system.

This task will illustrate the mechanism that Service Fabric provides for upgrading an application in production.

### Task 1: How upgrade works

In Service Fabric, deployments can be either regular or upgrade. A regular deployment erases any previous deployment data while the upgrade deployment preserves it. There are advantages to upgrades:

-   Stateful service data will not be lost during upgrade

-   Availability remains during the upgrade

The following figure illustrates the deployment hierarchy:

![The Deployment hierarchy diagram starts on the left with Deployment, which has two lines leading to Regular (Replaces,) and Upgrade (Preserves). Upgrade has two lines leading to Control, and Modes. Control has two lines to Health Check Policies, and Upgrade Parameters. Upgrade Parameters has two two lines to Healthy Check Retry Timeout, and Others. From Upgrade, as previously stated, the second line leads to Modes. Modes then has three lines to Monitored, which automates the upgrade and health check; Unmonitored Auto, which Automates the upgrade but skips the health check; and Unmonitored Manual, which manually upgrades each upgrade domain.](images/Labs/image166.png "Deployment hierarchy diagram")

If you set the upgrade mode to Monitored, Service Fabric will be in full control of the upgrade process. There is a configurable time to wait after the upgrade has finished before Service Fabric evaluates the health of the application. This value defaults to 600 seconds.

### Task 2: Update an actor state

Currently, the TicketOrderActor does not have a status property to make it easier to check on the actor order status quickly. In this task, you will modify the Ticket Order State model to add a new status property.

#### Tasks to complete:

1.  Add a state field to the TicketOrderActor by uncommenting the TODO: Exercise 6 -- Task 1 sections in the solution.

#### Exit criteria:

-  After making this change, compile the solution and verify that there are no errors.

### Task 3: Perform a smooth upgrade

In this task, you will configure settings for the Service Fabric application to perform an upgrade.

#### Tasks to complete:

1.  Publish the ContosoEventsApp using the Cloud.xml configuration, selecting the Upgrade option.

2.  Use 'Monitored' for the upgrade settings.

3.  Update the TicketOrderActor version to 1.1.0.

4.  View the upgrade status from the Visual Studio output window.

5.  Navigate to Service Fabric Explorer for the hosted cluster and watch the upgrade in progress.

#### Exit criteria:

-  When the upgrade is complete, from Service Fabric Explorer observe the new application version number.

### Task 4: Submit a new order

Now that the upgrade is completed successfully, you will submit a new order, and make sure that the newly submitted order has the extended state.

#### Tasks to complete:

1.  From the Swagger endpoint of the API Management instance, submit a new order such as this:

    ```
        {
        "userName": "testupgrade",
        "email": "test.upgrade@gmail.com",
        "eventId": "EVENT1-ID-00001",
        "paymentProcessorTokenId": "ggashwh565-uiewuu87-ujdsk",
        "tickets": 3
        }
    ```

#### Exit criteria:

-  Navigate to the Cosmos DB query explorer and create a query using this order id to see the new extended state actually persisted to the database.

## After the hands-on lab

Duration: 10 minutes

In this exercise, attendees will deprovision any Azure resources that were created in support of the lab. You should follow all steps provided after attending the Hands-on lab.

#### Tasks to complete:

1.  Delete the Resource Group you created during this hands-on lab.

#### Exit criteria:

-  After all the deletion tasks are complete, the resources will no longer be listed in the Azure portal or the Management portal. This may take about 10 minutes. You can optionally wait to see a confirmation. Otherwise, you are done!
