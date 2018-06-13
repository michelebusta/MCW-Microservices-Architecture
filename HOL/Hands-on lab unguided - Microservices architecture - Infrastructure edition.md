![](images/HeaderPic.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Microservices architecture - Infrastructure edition
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

- [Microservices architecture -- infrastructure edition hands-on lab unguided](#microservices-architecture----infrastructure-edition-hands-on-lab-unguided)
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
        - [Task 3: Azure Active Directory B2C](#task-3-azure-active-directory-b2c)
            - [Tasks to complete:](#tasks-to-complete-2)
            - [Exit criteria:](#exit-criteria-2)
        - [Task 4: Web App](#task-4-web-app)
            - [Tasks to complete:](#tasks-to-complete-3)
            - [Exit criteria:](#exit-criteria-3)
        - [Task 5: Function App](#task-5-function-app)
            - [Tasks to complete:](#tasks-to-complete-4)
            - [Exit criteria:](#exit-criteria-4)
        - [Task 6: Storage account](#task-6-storage-account)
            - [Tasks to complete:](#tasks-to-complete-5)
            - [Exit criteria:](#exit-criteria-5)
        - [Task 7: Cosmos DB](#task-7-cosmos-db)
            - [Tasks to complete:](#tasks-to-complete-6)
            - [Exit criteria:](#exit-criteria-6)
    - [Exercise 2: Placing ticket orders](#exercise-2-placing-ticket-orders)
        - [Task 1: Run the solution](#task-1-run-the-solution)
            - [Tasks to complete:](#tasks-to-complete-7)
            - [Exit criteria:](#exit-criteria-7)
        - [Task 2: Test the application](#task-2-test-the-application)
            - [Tasks to complete:](#tasks-to-complete-8)
            - [Exit criteria:](#exit-criteria-8)
        - [Task 3: Service Fabric Explorer](#task-3-service-fabric-explorer)
            - [Tasks to complete:](#tasks-to-complete-9)
            - [Exit criteria:](#exit-criteria-9)
        - [Task 4: Set up the Ticket Order Sync queue](#task-4-set-up-the-ticket-order-sync-queue)
            - [Tasks to complete:](#tasks-to-complete-10)
            - [Exit criteria:](#exit-criteria-10)
        - [Task 5: Set up the functions](#task-5-set-up-the-functions)
            - [Tasks to complete:](#tasks-to-complete-11)
            - [Exit criteria:](#exit-criteria-11)
        - [Task 6: Test order data sync](#task-6-test-order-data-sync)
            - [Tasks to complete:](#tasks-to-complete-12)
            - [Exit criteria:](#exit-criteria-12)
    - [Exercise 3: Publish the Service Fabric Application](#exercise-3-publish-the-service-fabric-application)
        - [Task 1: Publish the application](#task-1-publish-the-application)
            - [Tasks to complete:](#tasks-to-complete-13)
            - [Exit criteria:](#exit-criteria-13)
        - [Task 2: Test an order from the cluster](#task-2-test-an-order-from-the-cluster)
            - [Tasks to complete:](#tasks-to-complete-14)
            - [Exit criteria:](#exit-criteria-14)
    - [Exercise 4: API Management](#exercise-4-api-management)
        - [Task 1: Import API](#task-1-import-api)
            - [Tasks to complete:](#tasks-to-complete-15)
            - [Exit criteria:](#exit-criteria-15)
        - [Task 2: Retrieve the user subscription key](#task-2-retrieve-the-user-subscription-key)
            - [Tasks to complete:](#tasks-to-complete-16)
            - [Exit criteria:](#exit-criteria-16)
        - [Task 3: Configure the Function App with the API Management key](#task-3-configure-the-function-app-with-the-api-management-key)
            - [Tasks to complete:](#tasks-to-complete-17)
            - [Exit criteria:](#exit-criteria-17)
    - [Exercise 5: Configure and publish the web application](#exercise-5-configure-and-publish-the-web-application)
        - [Task 1: Configure the web app settings](#task-1-configure-the-web-app-settings)
            - [Tasks to complete:](#tasks-to-complete-18)
            - [Exit criteria:](#exit-criteria-18)
        - [Task 2: Running the web app and creating an order](#task-2-running-the-web-app-and-creating-an-order)
            - [Tasks to complete:](#tasks-to-complete-19)
            - [Exit criteria:](#exit-criteria-19)
        - [Task 3: Publish the web app](#task-3-publish-the-web-app)
            - [Tasks to complete:](#tasks-to-complete-20)
            - [Exit criteria:](#exit-criteria-20)
    - [Exercise 6: Upgrading](#exercise-6-upgrading)
        - [Task 1: How upgrade works](#task-1-how-upgrade-works)
        - [Task 2: Update an actor state](#task-2-update-an-actor-state)
            - [Tasks to complete:](#tasks-to-complete-21)
            - [Exit criteria:](#exit-criteria-21)
        - [Task 3: Perform a smooth upgrade](#task-3-perform-a-smooth-upgrade)
            - [Tasks to complete:](#tasks-to-complete-22)
            - [Exit criteria:](#exit-criteria-22)
        - [Task 4: Submit a new order](#task-4-submit-a-new-order)
            - [Tasks to complete:](#tasks-to-complete-23)
            - [Exit criteria:](#exit-criteria-23)
    - [Exercise 7: Rollback](#exercise-7-rollback)
        - [Task 1: Add health checks](#task-1-add-health-checks)
            - [Tasks to complete:](#tasks-to-complete-24)
            - [Exit criteria:](#exit-criteria-24)
        - [Task 2: Perform a troubled upgrade](#task-2-perform-a-troubled-upgrade)
            - [Tasks to complete:](#tasks-to-complete-25)
            - [Exit criteria:](#exit-criteria-25)
    - [Exercise 8: Load testing](#exercise-8-load-testing)
        - [Task 1: Simulate a 50-order request](#task-1-simulate-a-50-order-request)
            - [Tasks to complete:](#tasks-to-complete-26)
            - [Exit criteria:](#exit-criteria-26)
    - [BONUS Exercise 9: Load testing w/ partitions](#bonus-exercise-9-load-testing-w-partitions)
        - [Task 1: Using the current partition count, simulate 100 orders](#task-1-using-the-current-partition-count-simulate-100-orders)
            - [Tasks to complete:](#tasks-to-complete-27)
            - [Exit criteria:](#exit-criteria-27)
        - [Task 2: Setting up for load testing with different partition counts](#task-2-setting-up-for-load-testing-with-different-partition-counts)
            - [Tasks to complete:](#tasks-to-complete-28)
            - [Exit criteria:](#exit-criteria-28)
        - [Task 3: Using a partition count of 10, simulate 100 orders](#task-3-using-a-partition-count-of-10-simulate-100-orders)
            - [Tasks to complete:](#tasks-to-complete-29)
            - [Exit criteria:](#exit-criteria-29)
        - [Task 4: Using a partition count of 15, simulate 100 orders](#task-4-using-a-partition-count-of-15-simulate-100-orders)
            - [Tasks to complete:](#tasks-to-complete-30)
            - [Exit criteria:](#exit-criteria-30)
        - [Task 5: Using a partition count of 20, simulate 100 orders](#task-5-using-a-partition-count-of-20-simulate-100-orders)
            - [Tasks to complete:](#tasks-to-complete-31)
            - [Exit criteria:](#exit-criteria-31)
        - [Task 6: Determine the performance variations among the different load tests](#task-6-determine-the-performance-variations-among-the-different-load-tests)
            - [Tasks to complete:](#tasks-to-complete-32)
            - [Exit criteria:](#exit-criteria-32)
    - [BONUS Exercise 10: Secure the web application](#bonus-exercise-10-secure-the-web-application)
        - [Task 1: Configure the Azure Active Directory B2C](#task-1-configure-the-azure-active-directory-b2c)
            - [Tasks to complete:](#tasks-to-complete-33)
            - [Exit criteria:](#exit-criteria-33)
        - [Task 2: Configure the Web App Settings](#task-2-configure-the-web-app-settings)
            - [Tasks to complete:](#tasks-to-complete-34)
            - [Exit criteria:](#exit-criteria-34)
        - [Task 3: Add security features to the web application](#task-3-add-security-features-to-the-web-application)
            - [Tasks to complete:](#tasks-to-complete-35)
            - [Exit criteria:](#exit-criteria-35)
        - [Task 4: Running the Web App and signing in](#task-4-running-the-web-app-and-signing-in)
            - [Tasks to complete:](#tasks-to-complete-36)
            - [Exit criteria:](#exit-criteria-36)
    - [After the hands-on lab](#after-the-hands-on-lab)
            - [Tasks to complete:](#tasks-to-complete-37)
            - [Exit criteria:](#exit-criteria-37)

<!-- /TOC -->

# Microservices architecture -- infrastructure edition hands-on lab unguided

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

### Task 3: Azure Active Directory B2C

In this section, you will provision an Azure Active Directory B2C tenant. You will use this if you do BONUS Exercise 10, so it is best to set it up in advance to avoid having to wait for provisioning.

#### Tasks to complete:

1.  Create a new Azure Active Directory B2C tenant in the same region as your other items. Use the domain 'contosoeventsb2cSUFFIX'. Set it up as a B2C directory.

2.  Configure the tenant for Username sign in.

3.  Create three profiles: sign in, sign up, and profile edit.

#### Exit criteria:

-  After the tenant is provisioned, it will be displayed in the Active Directory list in the Management Portal. This may take up to 5 minutes, so move to Task 4 and return later to verify.

### Task 4: Web App

In these steps, you will provision a Web App in a new App Service Plan.

#### Tasks to complete:

1.  Provision a web app to host the website. Create an App Service Plan in the Resource Group and region you used previously. Name the Web App something like 'contosoeventsweb-SUFFIX'.

2.  Select pricing tier S1 Standard.

#### Exit criteria:

-  You can navigate to your new Web App at the URL you noted earlier based on your Web App name such as <https://contosoeventsweb-SUFFIX.azurewebsites.net>. You should see an empty website.

### Task 5: Function App

In this task, you will provision a Function App using a Consumption Plan. By using a Consumption Plan, you enable dynamic scaling of your Functions.

#### Tasks to complete:

1.  Provision a Function App to host the functions in the Visual Studio solution, in a Consumption Plan. Create a new Resource Group with a name similar to your main Resource Group such as 'contosoeventsfn-SUFFIX'.

2.  Name the App something like 'contosoeventsfn-SUFFIX'.

#### Exit criteria:

-  When the provisioning completes, your Web App and Function App are listed in the Azure Portal.

### Task 6: Storage account

In this section, you will create a Storage account for the application to create and use queues required by the solution.

#### Tasks to complete:

1.  Provision a Resource Manager based Storage account of type Standard LRS in the same Location and Resource Group as your other services.

2.  Name it something like 'contosoeventsSUFFIX'.

#### Exit criteria:

-  After provisioning is complete, the Storage account will be listed in the Azure Portal.

### Task 7: Cosmos DB

In this section, you will provision a Cosmos DB account, a Cosmos DB Database and a Cosmos DB collection that will be used to collect ticket orders.

#### Tasks to complete:

1.  Provision a new Cosmos DB account in the same region and Resource Group as your other services. Use the name 'contosoeventsdocdb-SUFFIX'.

2.  Add a database with ID 'TicketManager'.

3.  Add two collections named 'Orders' and 'Events'.

#### Exit criteria:

-  You will be able to see the two collections in the new database.

## Exercise 2: Placing ticket orders

Duration: 30 minutes

The agreed upon design with Contoso Events involves queuing ticket orders, and executing them asynchronously. A stateless Web API service receives the request, and queues it to a stateful service. An actor processes the request, and persists the order in its state.

The design also calls for saving the state of the ticket order to a Cosmos DB collection for ad hoc queries. This exercise will guide you through adding configurations that will light up the actor code that externalizes its state to a storage queue. In addition, you will set up the Function App to read from the queue, and persist the order to the Orders collection of the Cosmos DB instance you created.

> Note: The code to write to the storage queue is already in place within the actor, so setting up configuration keys is the only requirement to lighting up that feature.

![The Ticket Ordering flowchart starts with Web API (Stateless Service). An arrow points to Ticket Order Service (Stateful Service), then to Ticket Order Actor (Processor). These three items make up the Contoso Events Service Fabric App. From Ticket Order Actor, an arrow points to Order Externalization (Queue). The next step is Process Order Externalization (Azure Function), and ends with Cosmos DB (Orders Collection).](images/Labs/image67.png "Ticket Ordering flowchart")

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

## Exercise 3: Publish the Service Fabric Application

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

## Exercise 4: API Management

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

-  You will be able to issue a load test from the Web site in Exercise 5, and see that orders have been processed through the function -- as it will have successfully called the API and you will see results in the reports page.

## Exercise 5: Configure and publish the web application

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

## Exercise 6: Upgrading

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

1.  Add a state field to the TicketOrderActor by uncommenting the TODO: Exercise 6 - Task 1 sections in the solution.

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

## Exercise 7: Rollback

Duration: 30 minutes

In this exercise, you will deploy an update that causes issues with the application, and will trigger an automatic rollback of the deployment. This exercise will illustrate the mechanism Service Fabric provides for preserving application health and availability in production.

### Task 1: Add health checks

In this task, you will add code to produce health checks that force the monitored upgrade to roll back to the original version of the service.

#### Tasks to complete:

1.  Locate all TODO: Exercise 7 - Task 1 in the solution and uncomment the code as indicated.

#### Exit criteria:

-  Compile the code to ensure there are no issues with the changes.

### Task 2: Perform a troubled upgrade

In this task, you will perform an upgrade and watch a rollback of the upgrade.

#### Tasks to complete:

1.  Publish the application to the cluster again. During the process, set the TicketOrderService new version to 1.1.0.

2.  From Service Fabric Explorer note the errors that appear.

3.  Try posting to the service and note that the application is still responsive.

4.  So that you do not forget, return to the code and re-comment the failure report so that you can do future exercise without rollback!

#### Exit criteria:

-  Look at the Visual Studio output window and note the rollback takes place after some seconds.

-  Note that Service Fabric Explorer shows the rollback as well with the current deployment now set to the previous version.

-  Also, note that the error remains until it is time to live expires or it is replaced by another health state. Until then, the unhealthy state will remain in the cluster, but the cluster will be running normally. You can proceed without clearing this for now.

-  The subsequent exercises (i.e. 8 and beyond) will be executed using version 1.1.0 and while the cluster shows unhealthy state. You can ignore this for now.

-  Optionally, from the Swagger endpoint for the deployed application, you can request health statistics at the following relative URL: /api/admin/applicationhealth.

## Exercise 8: Load testing

Duration: 15 minutes

In this exercise, you will perform a load test against the Service Fabric Cluster and observe how messages are distributed across partitions.

### Task 1: Simulate a 50-order request

In this task, you will simulate a load test of 50 orders against the cluster using the Web application to submit the load test and monitor partitions.

#### Tasks to complete:

1.  Navigate to the published Web application at a URL like <https://contosoeventsweb-SUFFIX.azurewebsites.net>.

2.  From the Load Test page, issue a load test for 50 iterations.

3.  From the Load Test Status page, refresh and view the distribution of messages across the partitions where they are queued.

#### Exit criteria:

-  After a few minutes you will see that the queues are drained, and the orders were processed.

> **Note**: If you still have more time, run this again with additional iterations progressively such as 100, 150, 200, 250. Or, take a look at Exercise 9 in the answers area which takes you through a much more comprehensive load test and partition analysis process using the API endpoint.

## BONUS Exercise 9: Load testing w/ partitions

> **Note**: If you completed the other work in good time and still have another 50 minutes free, have some load testing and partitioning fun! Otherwise, skip to [After the hands-on lab](#after-the-hands-on-lab).

Follow the steps in the answers area for Exercise 9 and learn how to produce a partitioning metrics report.

### Task 1: Using the current partition count, simulate 100 orders

In this task, you will simulate a load test against the Cluster using the current partition count (that is, 5) of the Ticket Order Service.

#### Tasks to complete:

1.  Using the Swagger UI, issue an order POST request, such as:

    ```
    {
        "baseUrl": "http://<your-cluster-name>.<your-region>.cloudapp.azure.com:8082",
        "eventId": "EVENT1-ID-00001",
        "userName": "tester",
        "email": "load.tester@gmail.com",
        "tag": "partitions-5-100",
        "iterations": 100
    }
    ```

2.  Issue a GET request against /api/admin/partitions to see how the different partitions are functioning.

#### Exit criteria:

-  Verify that queues are drained and that orders are processed before completing this task.

### Task 2: Setting up for load testing with different partition counts

In this task, you will clean the existing orders from the Cosmos DB, so you can start with clean slate. This step is optional but because we are going to rely on reporting about orders in the database, it is much better to keep in the database only the orders that were simulated for load testing.

#### Tasks to complete:

1.  Use the Swagger UI to delete orders from the Cosmos DB.

2.  Unprovision the application type, using Service Fabric Explorer.

3.  Make sure Upgrade the application checkbox is unchecked each time you publish.

#### Exit criteria:

-  Service Fabric Explorer shows no application types or applications deployed.

-  You can verify from Cosmos DB Orders Document Explorer that there are no more orders in the database.

### Task 3: Using a partition count of 10, simulate 100 orders

In this task, you will repeat the same load test you performed in Task 2 but using a partition count of 10.

#### Tasks to complete:

1.  Change the service and actor partition count to 10 in the Cloud.xml Application Parameters file.

2.  Redeploy the app to the cluster.

3.  Repeat the same load test you did in Task 1, but with a different tag:

    ```
    {
        "baseUrl": "http://<your-cluster-name>.<your-region>.cloudapp.azure.com:8082",
        "eventId": "EVENT1-ID-00001",
        "userName": "tester",
        "email": "load.tester@gmail.com",
        "tag": "partitions-10-100",
        "iterations": 100
    }
    ```

#### Exit criteria:

-  Verify that queues are drained and that orders are processed before completing this task.

### Task 4: Using a partition count of 15, simulate 100 orders

In this task, you will repeat the same load test you performed in Task 2 but using a partition count of 15.

#### Tasks to complete:

1.  Change the service and actor partition count to 15 in the Cloud.xml Application Parameters file.

2.  Redeploy the app to the cluster.

3.  Repeat the same test load you did in Task 1 but with a different tag:

    ```
    {
        "baseUrl": "http://<your-cluster-name>.<your-region>.cloudapp.azure.com:8082",
        "eventId": "EVENT1-ID-00001",
        "userName": "tester",
        "email": "load.tester@gmail.com",
        "tag": "partitions-15-100",
        "iterations": 100
    }

#### Exit criteria:

-  Verify that queues are drained and that orders are processed before completing this task.

### Task 5: Using a partition count of 20, simulate 100 orders

In this task, you will repeat the same load test you performed in Task 1 but using a partition count of 20.

#### Tasks to complete:

1.  Change the service and actor partition count to 15 in the Cloud.xml Application Parameters file.

2.  Redeploy the app to the cluster.

3.  Repeat the same test load you did in Task 2 but with a different tag:

    ```
    {
        "baseUrl": "http://<your-cluster-name>.<your-region>.cloudapp.azure.com:8082",
        "eventId": "EVENT1-ID-00001",
        "userName": "tester",
        "email": "load.tester@gmail.com",
        "tag": "partitions-20-100",
        "iterations": 100
    }
    ```

#### Exit criteria:

-  Verify that queues are drained and that orders are processed before completing this task.

### Task 6: Determine the performance variations among the different load tests

In this task, you will find out how each load test performed and plot the result.

> **Note**: This step is out of scope and is shown here only to complete the picture.

#### Tasks to complete:

1.  Using the Service Fabric Web API Swagger UI, please issue a GET request against /api/orders/stats.

2.  Scale out the VMs count to 10 in your cluster, and repeat Tasks 1, 3, 4, and 5.

3.  Produce an Excel sheet from the data you collected.

#### Exit criteria:

-  You have an Excel sheet displaying the data you've collected.

    ![An Excel bar graph displays the average number of seconds it takes to process orders for different numbers of partitions (ranging from 5 - 25 partitions). The graph data is split into two sides, 5 VMs on the left, and 10 VMs on the right. Average times are lower for the partition ranges on the 10 VMs side.](images/Labs/image193.png "Excel graph of Average seconds to process orders")

## BONUS Exercise 10: Secure the web application

If you completed the other work in good time and still have another 30 minutes, do this exercise and integrate Azure Active Directory B2C with the application. Otherwise, skip to [After the hands-on lab](#after-the-hands-on-lab).

For a challenge, follow these steps here, or go to the answers area for explicit steps and save some time researching.

In this exercise, you will configure the Azure Active Directory B2C tenant and configure the Web front end to integrate with it for user login. Once all the settings are in place, you will be able to run the website, register as a user, and login.

### Task 1: Configure the Azure Active Directory B2C

In this task, you will set up the Azure Active Directory B2C directory for your application to integrate with it.

#### Tasks to complete:

1.  Register a new application in the Azure Active Directory B2C tenant you created previously.

2.  Add a reply URL for local testing: <https://localhost:44327/>

3.  Add a reply URL for the hosted Web App as you named it, for example: <https://contosoeventsweb-SUFFIX.azurewebsites.net/>

4.  Set local accounts to Username.

5.  Define policies for sign up, sign in and profile editing.

6.  For all policies, set Application Claims select Email Addresses, Given Name, Surname, and User's Object ID.

7.  For the sign up and sign in policies, set the Claim representing policy ID to acr.

8.  For profile attributes, choose Given Name and Surname.

9.  When done take note of the Application ID for later. Also, take note of the policy names.

#### Exit criteria:

-  Your B2C directory is ready for use and after Task 2 is complete, you will be able to exercise it.

### Task 2: Configure the Web App Settings

In this task, you will update configuration settings in preparation for Azure AD B2C integration.

You will be guided through the instructions to find the information necessary to populate the configuration settings.

#### Tasks to complete:

1.  For the ida:Tenant enter the domain of the Azure Active Directory B2C you created such as 'contosoeventsb2cSUFFIX.onmicrosoft.com'.

2.  For the ida:ClientId enter the Application ID generated for your B2C application created in the previous task.

3.  For the ida:SignUpPolicyId enter the name of the sign-up policy you created in the tenant (e.g., B2C\_1\_signup).

4.  For the ida:SignInPolicyId enter the name of the sign in policy you created in the tenant (e.g., B2C\_1\_signin).

5.  For the ida:UserProfilePolicyId enter the name of the profile editing policy you created in the tenant (e.g., B2C\_1\_profileedit).

#### Exit criteria:

-  You will have set all the required settings.

### Task 3: Add security features to the web application

In this task, you will enable security features that will leverage the configuration you just applied.

#### Tasks to complete:

1.  In the solution, look for all TODO Exercise 10 - Task 3 instructions and follow the steps.

2.  Compile the solution to ensure no issues.

#### Exit criteria:

-  Compile the application and ensure no errors before the next step.

### Task 4: Running the Web App and signing in

In this task, you will test the web application and register yourself as a user to log in to the Azure AD B2C tenant.

#### Tasks to complete:

1.  Run the Web App.

2.  Register a new user and authenticate.

3.  Sign out and sign in again.

#### Exit criteria:

-  Note your email is shown in the application header after you sign in.

**Note**: You can optionally publish this application to Azure and test sign in, sign out continues to work from the deployed URL.

## After the hands-on lab

Duration: 10 minutes

In this exercise, attendees will deprovision any Azure resources that were created in support of the lab. You should follow all steps provided after attending the Hands-on lab.

#### Tasks to complete:

1.  Delete the Resource Group you created during this hands-on lab.

2.  Delete the Azure Active Directory B2C tenant.

#### Exit criteria:

-  After all the deletion tasks are complete, the resources will no longer be listed in the Azure portal or the Management portal. This may take about 10 minutes. You can optionally wait to see a confirmation. Otherwise, you are done!
