![](images/HeaderPic.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Microservices architecture - Infrastructure edition
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
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

- [Microservices architecture -- infrastructure edition hands-on lab step-by-step](#microservices-architecture---infrastructure-edition-hands-on-lab-step-by-step)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Overview](#overview)
    - [Solution architecture](#solution-architecture)
    - [Requirements](#requirements)
    - [Exercise 1: Environment setup](#exercise-1-environment-setup)
        - [Task 1: Download and open the ContosoEventsPoC starter solution](#task-1-download-and-open-the-contosoeventspoc-starter-solution)
        - [Task 2: API Management](#task-2-api-management)
        - [Task 3: Azure Active Directory B2C](#task-3-azure-active-directory-b2c)
        - [Task 4: Web app](#task-4-web-app)
        - [Task 5: Function app](#task-5-function-app)
        - [Task 6: Storage account](#task-6-storage-account)
        - [Task 7: Cosmos DB](#task-7-cosmos-db)
    - [Exercise 2: Placing ticket orders](#exercise-2-placing-ticket-orders)
        - [Task 1: Run the solution](#task-1-run-the-solution)
        - [Task 2: Test the application](#task-2-test-the-application)
        - [Task 3: Service Fabric Explorer](#task-3-service-fabric-explorer)
        - [Task 4: Set up the Ticket Order Sync queue](#task-4-set-up-the-ticket-order-sync-queue)
        - [Task 5: Set up the functions](#task-5-set-up-the-functions)
        - [Task 6: Test order data sync](#task-6-test-order-data-sync)
    - [Exercise 3: Publish the Service Fabric Application](#exercise-3-publish-the-service-fabric-application)
        - [Task 1: Publish the application](#task-1-publish-the-application)
        - [Task 2: Test an order from the cluster](#task-2-test-an-order-from-the-cluster)
    - [Exercise 4: API Management](#exercise-4-api-management)
        - [Task 1: Import API](#task-1-import-api)
        - [Task 2: Retrieve the user subscription key](#task-2-retrieve-the-user-subscription-key)
        - [Task 3: Configure the Function App with the API Management key](#task-3-configure-the-function-app-with-the-api-management-key)
    - [Exercise 5: Configure and publish the web application](#exercise-5-configure-and-publish-the-web-application)
        - [Task 1: Configure the web app settings](#task-1-configure-the-web-app-settings)
        - [Task 2: Running the web app and creating an order](#task-2-running-the-web-app-and-creating-an-order)
        - [Task 3: Publish the web app](#task-3-publish-the-web-app)
    - [Exercise 6: Upgrading](#exercise-6-upgrading)
        - [Task 1: How upgrade works](#task-1-how-upgrade-works)
        - [Task 2: Update an actor state](#task-2-update-an-actor-state)
        - [Task 3: Perform a smooth upgrade](#task-3-perform-a-smooth-upgrade)
        - [Task 4: Submit a new order](#task-4-submit-a-new-order)
    - [Exercise 7: Rollback](#exercise-7-rollback)
        - [Task 1: Add health checks](#task-1-add-health-checks)
        - [Task 2: Perform a troubled upgrade](#task-2-perform-a-troubled-upgrade)
    - [Exercise 8: Load testing](#exercise-8-load-testing)
        - [Task 1: Simulate a 50-order request](#task-1-simulate-a-50-order-request)
    - [BONUS Exercise 9: Load testing w/ partitions](#bonus-exercise-9-load-testing-w-partitions)
        - [Task 1: Using the current partition count, simulate 100 orders](#task-1-using-the-current-partition-count-simulate-100-orders)
        - [Task 2: Setting up for load testing with different partition counts](#task-2-setting-up-for-load-testing-with-different-partition-counts)
        - [Task 3: Using a partition count of 10, simulate 100 orders](#task-3-using-a-partition-count-of-10-simulate-100-orders)
        - [Task 4: Using a partition count of 15, simulate 100 orders](#task-4-using-a-partition-count-of-15-simulate-100-orders)
        - [Task 5: Using a partition count of 20, simulate 100 orders](#task-5-using-a-partition-count-of-20-simulate-100-orders)
        - [Task 6: Determine the performance variations among the different load tests](#task-6-determine-the-performance-variations-among-the-different-load-tests)
    - [BONUS Exercise 10: Secure the web application](#bonus-exercise-10-secure-the-web-application)
        - [Task 1: Configure the Azure Active Directory B2C](#task-1-configure-the-azure-active-directory-b2c)
        - [Task 2: Configure the web app Settings](#task-2-configure-the-web-app-settings)
        - [Azure Active Directory B2C:](#azure-active-directory-b2c)
        - [Task 3: Add security features to the web application](#task-3-add-security-features-to-the-web-application)
        - [Task 4: Running the web app and signing in](#task-4-running-the-web-app-and-signing-in)
    - [After the hands-on lab](#after-the-hands-on-lab)
        - [Task 1: Delete the resource group](#task-1-delete-the-resource-group)

<!-- /TOC -->

# Microservices architecture -- infrastructure edition hands-on lab step-by-step

## Abstract and learning objectives

This whiteboard design session is designed to help attendees gain a better understanding of implementing architectures leveraging aspects from microservices serverless architectures, by helping an online concert ticket vendor survive the first 5 minutes of crushing load. They will handle the client\'s scaling needs through microservices built on top of Service Fabric, and apply smooth updates or roll back failing updates. Finally, students will design an implementation of load testing to optimize the architecture for handling spikes in traffic.??

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

![This illustrationlists key items to remember, which include: Profiles, Application, Queues, TicketManager DB, Functions, APIM Endpoints, Web App, Cluster Endpoints, and Local Endpoints. At this time, we are unable to capture all of the information in the illustration. Future versions of this course should address this.](images/Labs/image4.png "Key items to remember illustration")

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

1.  On your Lab VM, download the starter project from <http://bit.ly/2sQNZCg>. (Note: the URL is case sensitive, so you may need to copy and paste it into your browser's address bar.)

2.  Unzip the contents to the folder C:\\handsonlab.

3.  Locate the solution file (C:\\handsonlab\\ContosoEventsPoC\\Src\\ContosoEventsPOC.sln), and double-click it to open it with Visual Studio 2017.

4.  If prompted about how you want to open the file, select Visual Studio 2017, and select OK.

    ![In the How do you want to open this file dialog box, Visual Studio 2017 is selected.](images/Labs/image43.png "How do you want to open this file?")

5.  Log into Visual Studio or set up an account, when prompted.

    ![The Welcome to Visual Studio window displays, asking you to sign in.](images/Labs/image44.png "Welcome to Visual Studio window")

6.  If presented with a security warning, uncheck Ask me for every project in this solution, and select OK.

    ![A Security Warning displays for contosoEvents.WebApi. A message states that you should only open projects from a trustworthy source. At the bottom, the check box for Ask me for every project in this solution is circled.](images/Labs/image45.png "Security Warning for contosoEvents.WebApi")

7.  If you are missing any prerequisites (listed under Requirements above), you may be prompted to install these at this point.

8.  Before you attempt to compile the solution, set the configuration to x64 by selecting it from the Solution Platforms drop down in the Visual Studio toolbar.

    ![On the Visual Studio Toolbar, The Platforms drop-down carat is circled, and in its drop-down menu, x64 is circled.](images/Labs/image46.png "Visual Studio Toolbar")

9.  Build the solution, by selecting Build from the Visual Studio menu, then selecting Build Solution.

    ![The Build button is circled on the Visual Studio menu. Under that, Build Solution is circled.](images/Labs/image47.png "Visual Studio menu")

10. You will have some compile-time errors at this point. These are expected, and will be fixed as you proceed with the hands-on lab.

### Task 2: API Management

In this task, you will provision an API Management Service in the Azure portal.

1.  In the Azure portal, select +New, enter "API Management" into the Search the Marketplace box, then select API management from the results.

    ![In the Azure Portal Everything pane, API Management is typed in the search field. Under Results, API Management is circled.](images/Labs/image48.png "Azure Portal Everything pane")

2.  In the API Management blade, select Create.

3.  In the API Management service blade, enter the following:

    a.  Name: Enter a unique name, such as contosoevents-SUFFIX

    b.  Subscription: Choose your subscription

    c.  Resource group: Select Use existing, and select the hands-on-labs resource group you created previously.

    d.  Location: Select the same region used for the hands-on-labs resource group

    e.  Organization name: Enter Contoso Events

    f.  Administrator email: Enter your email address

    g.  Pricing tier: Select Developer (No SLA)

    h.  Select Create

    ![On the API Management service blade, fields are set to the previously defined settings.](images/Labs/image49.png "API Management service blade")

4.  After the API Management service is provisioned, the service will be listed in the Resource Group. This may take up to 10-15 minutes, so move to Task 3 and return later to verify.

### Task 3: Azure Active Directory B2C

In this section, you will provision an Azure Active Directory B2C tenant. You will use this if you do Bonus Exercise 10, so it is best to set it up in advance to avoid having to wait for provisioning.

1.  In the Azure portal, select +New, and enter "Azure Active Directory" into the Search the Marketplace box, then select Azure Active Directory B2C from the results.

    ![In the Azure Portal Everything pane, Azure Active Directory is typed in the search field. Under Results, Azure Active Directory B2C is circled.](images/Labs/image30.png "Azure Portal Everything pane")

2.  Select Create in the Azure Active Directory B2C blade.

3.  In the Create new B2C Tenant... blade, select Create a new Azure AD B2C Tenant.

    ![In the Create new B2C Tenant or Link to existing Tenant blade, Create a new Azure AD B2C Tenant is circled.](images/Labs/image31.png "Create new B2C Tenant or Link to existing Tenant blade")

4.  In the Azure AD B2C Create Tenant blade, enter:

    a.  Organization name: Enter a unique name, such as contosoeventsb2cSUFFIX

    b.  Initial domain name: Enter the same name as was entered for Organization name

    c.  Country or region: Select United States

    d.  Select Create

    ![On the Azure AD B2C Create Tenant, fields are set to the previously defined settings.](images/Labs/image32.png "Azure AD B2C Create Tenant")

5.  When the tenant finishes provisioning, you can switch to your new tenant by select the manage your new directory link which will appear in the Azure AD B2C Create Tenant blade.

    ![Screenshot of the Click here to manage your new directory link.](images/Labs/image33.png "Click here to manage your new directory")

6.  It may take a few minutes to provision the new directory. In the meantime, feel free to move on to Task 4, and return later to verify. To find the directory later, you may need to refresh the portal. The directory can be found by clicking your Directory + subscription icon, on the left of your logged in user name in the upper-right corner of the page.

    ![In the Azure Portal, the Directory + subscription icon, contosoeventsb2cSUFFIX and its corresponding address are circled.](images/Labs/image34.png "Azure Portal Directory + subscription pane")

### Task 4: Web App

In these steps, you will provision a Web App in a new App Service Plan.

1.  Select +New in the Azure Portal, select Web, then select Web App.

    ![In the Azure Portal, New pane, under Azure Marketplace, Web and Web App (Quckstart tutorial) are both circled.](images/Labs/image50.png "Azure Portal, New pane")

2.  On the Create Web App blade, enter the following:

    a.  App name: Enter a unique name, such as contosoeventsweb-SUFFIX

    b.  Subscription: Select your subscription

    c.  Resource group: Select Use existing, and select the hands-on-labs resource group created previously.

    d.  OS: Select Windows

    e.  App Service plan/location: Select this, select Create new

        i.  App service plan: Enter contosoeventsplan-SUFFIX

        ii. Location: Select the same location you have been using for other resources in this lab

        iii. Pricing tier: Select S1 Standard

        iv. Select OK

    f.  Select Create to provision the Web App.

    ![On the Create Web App blade, fields are set to the previously defined settings.](images/Labs/image51.png "Create Web App blade")

3.  You will receive a notification in the Azure portal when the Web App deployment completes. From this, select Go to resource.

    ![The Azure Portal Notification displays, indicating that deployment succeeded. In the top, right corner of the notification window, a Bell (notification) icon is circled. At the bottom of the Deployment succeeded message, the Go to resource button is circled.](images/Labs/image52.png "Azure Portal Notification")

4.  On the Web Apps Overview blade, you can see the URL used to access your Web App. If you select this, it will open an empty site, indicating your App Services app is up and running.

    ![On the Web Apps Overview blade, under URL, a quick link to the URL is circled.](images/Labs/image53.png "Web Apps Overview blade")

### Task 5: Function App

In this task, you will provision a Function App using a Consumption Plan. By using a Consumption Plan, you enable dynamic scaling of your Functions.

1.  Select +New in the Azure Portal, and enter "Function App" in the Search the Marketplace box, then select Function App from the results.

    ![In the Azure Portal Everything pane, the search field is set to Function App. Under Results, Function App is circled.](images/Labs/image54.png "Azure Portal Everything pane")

2.  Select Create on the Function App blade.

3.  On the Create Function App blade, enter the following:

    a.  App name: Enter a unique name, such as contosoeventsfn-SUFFIX

    b.  Subscription: Select your subscription

    c.  Resource group: Select Use existing, and select the hands-on-labs resource group created previously

    d.  OS: Select Windows

    e.  Hosting Plan: Select Consumption Plan

    f.  Location: Select the same location as the hands-on-labs resource group

    g.  Storage: Leave Create new selected, and accept the default name

    h.  Application Insights: Select Off

    i.  Select Create to provision the new Function App

    ![In the Function App blade, fields are set to the previously defined settings.](images/Labs/image55.png "Function App blade")

### Task 6: Storage account

In this section, you will create a Storage account for the application to create and use queues required by the solution.

1.  In the Azure portal, select +New, Storage, then select Storage account -- blob, file, table, queue under Featured.

    ![In the Azure Portal, New pane, under Azure Marketplace, Storage is circled. Under Featured, Storage account - blob, file, table, queue (Quickstart tutorial) is circled.](images/Labs/image56.png "Azure Portal, New pane")

2.  In the Create Storage account blade, enter the following:

    a.  Name: Enter a unique name, such as contosoeventsSUFFIX

    b.  Deployment model: Select Resource manager

    c.  Account kind: Select Storage (general purpose v1)

    d.  Location: Select the same location as the hands-on-labs resource group

    e.  Replication: Select Locally-redundant storage (LRS)

    f.  Performance: Select Standard

    g.  Secure transfer required: Leave Disabled

    h.  Subscription: Select your subscription

    i.  Resource group: Select Use existing, and select the hands-on-labs resource group created previously

    j.  Virtual networks: Leave Disabled

    k.  Select Create

    ![In the Create storage account blade, fields are set to the previously defined settings.](images/Labs/image57.png "Create storage account blade")

### Task 7: Cosmos DB

In this section, you will provision a Cosmos DB account, a Cosmos DB Database and a Cosmos DB collection that will be used to collect ticket orders.

1.  In the Azure portal, select +New, Databases, then select Azure Cosmos DB.

    ![In the Azure Portal, New pane, in the left column, Databases is circled. In the right pane, Azure Cosmos DB (Quickstart tutorial) is circled.](images/Labs/image58.png "Azure Portal, New pane")

2.  On the Azure Cosmos DB blade, enter the following:

    a.  ID: Enter a unique value, such as contosoeventsdb-SUFFIX

    b.  API: Select SQL

    c.  Subscription: Select your subscription

    d.  Resource group: Select Use existing, and select the hands-on-labs resource group previously created

    e.  Location: Select the location used for the hands-on-lab resource group. If this location is not available, select one close to that location that is available.

    f.  Enable geo-redundancy: Leave checked

    g.  Select Create to provision the Cosmos DB

    ![In the Azure Cosmos DB blade, fields are set to the previously defined settings.](images/Labs/image59.png "Azure Cosmos DB blade")

3.  When the Cosmos DB account is ready, navigate to the hands-on-labs Resource Group, and select your Cosmos DB account from the list.

    ![In the Resource Group pane, under Name, the contosoeventsdb-SUFFIX Azure Cosmos DB account is circled.](images/Labs/image60.png "Resource Group pane")

4.  On the Cosmos DB account blade, under Collections in the left-hand menu, select Browse.

    ![In the Cosmos DB account blade, Collections section, Browse is circled.](images/Labs/image61.png "Cosmos DB account blade")

5.  On the Browse blade, select +Add Collection.

    ![On the Browse blade menu, the Add Collections button is circled.](images/Labs/image62.png "Browse blade menu")

6.  On the Add Collection dialog, enter the following:

    a.  Database id: Select Create new and enter TicketManager

    b.  Provision database throughput: Leave unchecked

    c.  Collection id: Enter Orders

    d.  Storage capacity: Select Fixed (10 GB)

    e.  Throughput: Enter 2500

    f.  Select OK to create the new collection

    ![On the Add Collections blade, fields are set to the previously defined settings.](images/Labs/image63.png "Add Collections blade")

7.  Select New collection from the screen that appears.

    ![The New Collection button is circled on the New Screen.](images/Labs/image64.png "New Screen")

8.  In the Add Collection dialog, enter the following:

    a.  Database id: Select Use existing and then select TicketManager

    b.  Collection id: Enter Events

    c.  Storage capacity: Select Fixed (10 GB)

    d.  Throughput: Enter 2500

    e.  Select OK to create the new collection

    ![On the Add Collection blade, fields are set to the previously defined settings.](images/Labs/image65.png "Add Collection blade")

9.  You will be able to see that the two collections exist in the new database.

    ![On the New Screen, under Collections, under TicketManager, the Orders and Events collections are circled.](images/Labs/image66.png "New Screen")

## Exercise 2: Placing ticket orders

Duration: 30 minutes

The agreed upon design with Contoso Events involves queuing ticket orders, and executing them asynchronously. A stateless Web API service receives the request, and queues it to a stateful service. An actor processes the request, and persists the order in its state.

The design also calls for saving the state of the ticket order to a Cosmos DB collection for ad hoc queries. This exercise will guide you through adding configurations that will light up the actor code that externalizes its state to a storage queue. In addition, you will set up the Function App to read from the queue, and persist the order to the Orders collection of the Cosmos DB instance you created.

> Note: The code to write to the storage queue is already in place within the actor, so setting up configuration keys is the only requirement to lighting up that feature.

![The Ticket Ordering flowchart starts with Web API (Stateless Service). An arrow points to Ticket Order Service (Stateful Service), then to Ticket Order Actor (Processor). These three items make up the Contoso Events Service Fabric App. From Ticket Order Actor, an arrow points to Order Externalization (Queue). The next step is Process Order Externalization (Azure Function), and ends with Cosmos DB (Orders Collection).](images/Labs/image67.png "Ticket Ordering flowchart")

### Task 1: Run the solution

The purpose of this task is to make sure that the source code compiles, and that you can publish to a local cluster. To make sure that the app is running flawlessly, you will run some API tests and access the Service Fabric explorer.

Note: Not all features are in place, but you will be able to see that the application can run.

1.  On the Lab VM, make sure the local Service Fabric environment is running by selecting the arrow in the system tray, and checking for the appearance of the Service Fabric icon. Note: You may need to restart your VM if you've recently installed the Service Fabric Local Cluster Manager, for the icon to appear.

    ![In the Lab VM, the arrow and the Service Fabric icon are circled.](images/Labs/image72.png "Lab VM")

2.  If it is not there, you will need to start the local Service Fabric cluster. To do this, select the Start menu, scroll down to the apps listed under "S," and select Service Fabric Local Cluster Manager. The icon (Step 1) should now appear.

    ![In the Start Menu, Service Fabric Local Cluster Manager is circled.](images/Labs/image73.png "Start Menu")

3.  Right-click the system tray icon, and select Setup Local Cluster, 1 Node.

    ![In the System tray icon menu, Setup Local Cluster is selected. 1 Node is selected in the sub-menu. ](images/Labs/image74.png "System tray icon menu")

4.  You should see a message that the local cluster is setting up.

    ![The Service Fabric Local Cluster Manager message says that the setting up process may take a few minutes.](images/Labs/image75.png "Service Fabric Local Cluster Manager message")

5.  Note: Sometimes you will see an error message appear indicating the cluster setup is retrying.

6.  Open the ContosoEventsPoc solution in Visual Studio, if it is not still open from the previous exercise.

7.  Rebuild the solution to resolve all NuGet packages, and to make sure there are no compilation errors, by selecting Build from the menu, then selecting Rebuild Solution.

    ![In Visual Studio, Rebuild Solution is circled. In the top menu, Build is circled.](images/Labs/image76.png "Visual Studio")

8.  After the rebuild, you should see a Rebuild All succeeded message in the bottom left corner of Visual Studio, and that there are 0 Errors. Note: You may see some warnings, but these can be safely ignored.

    ![In Visual Studio, under Error List, the 0 Errors message is circled. At the bottom, the Rebuild All succeeded message is circled.](images/Labs/image77.png "Visual Studio")

9.  Now, you will Publish the Service Fabric app to the local cluster.

10.  In Solution Explorer, right-click the Service Fabric Application, ContosoEventsApp, and select Publish.

    ![In Solution Explorer, the Service Fabric folder is expanded, and ContosoEventsApp is circled. In the right-click menu, Publish is circled.](images/Labs/image78.png "Solution Explorer")

11. In the Publish Service Fabric Application dialog, select PublishProfiles\\Local.1Node.xml for the Target profile, ensure the correct account is selected, and select Publish.

    ![In the Publish Service Fabric Application dialog box, the Target profile field is set to PublishProfiles\\Local.1Node.xml, and is circled.](images/Labs/image79.png "Publish Service Fabric Application dialog box")

    > **Note**: If you have an error such as: "The project does not have a package action set." you can restart Visual Studio, re-open the solution, and this will resolve the problem.

12. You can see the publish status in the Visual Studio output pane, at the bottom of the window. When the publish process is complete, you will see a success message in the output pane. The application is ready to be used.

    ![In the Visual Studio output pane, the Publish: 1 succeeded, 0 failed, 0 skipped message at the bottom is circled.](images/Labs/image80.png "Visual Studio output pane")

### Task 2: Test the application

The Service Fabric Application includes a front-end Web API as the public-facing window to internal stateful services. In this task, you will check that you can call the Web API now that you have the application published to the local cluster. Because the app is not yet fully configured, not all Web API methods will be fully functional.

1.  On the Lab VM, open a Chrome browser, navigate to the Swagger endpoint for the Web API at: <http://localhost:8082/swagger/ui/index>. Note the three API endpoints: Admin, Events, and Orders.

    ![In the Swagger endpoint window, under ContosoEvents.WebApi, three endpoints are circled: Admin, Events, and Orders).](images/Labs/image81.png "Swagger endpoint window")

2.  Select the Admin API, and observe the list of methods available.

    ![In the Swagger endpoint window, under ContosoEvents.WebApi, Admin is circled, and its list of methods display below.](images/Labs/image82.png "Swagger endpoint window")

3.  Select /api/admin/partitions, then select Try it out.

    ![In the Swagger endpoint window, the /api/admin/partitions method is circled. Below that, the Model Schema displays. At the bottom, the Try it out button is circled.](images/Labs/image83.png "Swagger endpoint window, Admin method section")

4.  Make sure it returns a Response Code of 200, as shown in the following screen shot. This API endpoint returns the number of tickets queued across all partitions.

    ![In the Swagger endpoint window, under Admin, in the /api/admin/partitions method section, the Response Code 200 is circled.](images/Labs/image84.png "Swagger endpoint window, Admin method section")

5.  After viewing the Swagger definition, and receiving a success response code from the partitions method, your environment is in a good state to continue.

### Task 3: Service Fabric Explorer

In this task, you will browse to the Service Fabric Explorer, and view the local cluster.

1.  On your Lab VM, open a new tab in your Chrome browser, and navigate to the Service Fabric Explorer for the local cluster at <http://localhost:19080/Explorer/index.html>.

    ![In the Service Fabric Explorer window, in the left pane, Cluster is selected. In the right, Cluster http://local host pane, on the Essentials tab, both Cluster Health State and System Application Health State are okay. On the Dashboard, circle graphs show that 1 Node, 1 Application, 4 Services, 4 partitions, and 4 replicas are all healthy, and that there are no upgrades in progress.](images/Labs/image85.png "Service Fabric Explorer")

2.  Observe that the ContosoEventsApp is deployed with the following services:

    a.  fabric:/ContosoEventsApp/EventActorService

    b.  fabric:/ContosoEventsApp/TicketOrderActorService

    c.  fabric:/ContosoEventsApp/TicketOrderService

    d.  fabric:/ContosoEventsApp/WebApi

    ![In the Service Fabric Explorer, in the tree view, the following path is expanded: Closter\\Applications\\ContosoEventsAppType\\fabric:/ContosoEventsApp. Under fabric:/ContosoEventsApp, the previously mentioned four services are circled.](images/Labs/image86.png "Service Fabric Explorer")

### Task 4: Set up the Ticket Order Sync queue

In this task, you will complete features of the Contoso Events POC so that placing an order also syncs with the back-end data store. You will also update the configuration settings to reference the Azure resources you previously created correctly.

1.  Return to Visual Studio, and from Solution Explorer, open Local.1Node.xml, located in the ApplicationParameters folder under the ContosoEventsApp project in the Service Fabric folder.

    ![In Solution Explorer, the following path is expanded in the tree view: Service Fabric\\ContosoEventsApp\\ApplicationParameters. In ApplicationParameters, Local.1Node.xml is circled.](images/Labs/image87.png "Solution Explorer")

2.  Locate the following Parameter block in the file. In the steps below, you will retrieve the values needed to update Local.1Node.xml with your own configuration parameters.

```
    <Parameter Name="DataStorageEndpointUri" Value="" />
    <Parameter Name="DataStoragePrimaryKey" Value="" />
    <Parameter Name="DataStorageDatabaseName" Value="TicketManager" />
    <Parameter Name="DataStorageEventsCollectionName" Value="Events" />
    <Parameter Name="DataStorageOrdersCollectionName" Value="Orders" />
    <Parameter Name="DataStorageLogMessagesCollectionName" Value="LogMessages" />
    <Parameter Name="StorageConnectionString" Value="" />
    <Parameter Name="LogsStorageTableName" Value="prodlogs" />
    <Parameter Name="ExternalizationQueueName" Value="contosoevents-externalization-requests"/>
    <Parameter Name="SimulationQueueName" Value="contosoevents-simulation-requests" />
```

Cosmos DB settings:

1.  In the Azure Portal, browse to the Azure Cosmos DB account you created in Exercise 1, Task 7, and select Keys, under Settings in the left-hand menu.

    ![In the Azure Portal, Azure Cosmos DB account, under Settings, Keys is circled. In the right pane, under Read-write Keys, the URL, Primary Key, and their corresponding coopy buttons are circled.](images/Labs/image88.png "Azure Portal, Azure Cosmos DB account")

2.  Select the Copy button next to the URI value, return to the Local.1Node.xml file in Visual Studio, and paste the URI value into the value for the DataStorageEndpointUri parameter.

3.  Now, on your Cosmos DB keys blade, copy the Primary Key value, return to the Local.1Node.xml file in Visual Studio, and paste the Primary Key value into the value for the DataStoragePrimaryKey parameter.

4.  Back in the Azure portal, select Browse under Collections in the left-hand menu for your Cosmos DB. The database (TicketManager) and collection (Orders and Events) names are pre-set in the Local.1Node.xml file, so verify these match the collection and database names you see in the Azure portal.

    ![In the Azure Portal, Azure Cosmos DB, in the left pane, under Collections, Browse is circled. In the right pane, the Database field is set to All Databases. Under That, the TicketManager databases for Orders and Events are circled.](images/Labs/image89.png "Azure Portal, Azure Cosmos DB")

5.  If you used a different database name, modify the value of the DataStorageDatabaseName parameter to reflect the Cosmos DB database name.

6.  If you used a different collection names for the Orders or Events collections, modify the values of the DataStorageEventsCollectionName and DataStorageOrdersCollectionName parameters to match your names.

7.  Save the Local.1Node.xml file. The Cosmos DB parameters should now resemble the following:

    ![In the 1Node.xml file, the CosmosDB parameters display.](images/Labs/image90.png "1Node.xml file")

Storage settings:

1.  In the Azure Portal, browse to the Storage account you created in Exercise 1, Task 6, and select Access keys under Settings in the left-hand menu.

2.  Select the copy button to the right of key1 Connection String to copy the value.

    ![In Azure Portal, Storage account, in the left pane, under Settings, Access keys is circled. In the right pane, under Default keys, for key1, the Connection string and its corresponding copy button are circled.](images/Labs/image91.png "Azure Portal, Storage account")

3.  Return to the Local.1Node.xml file in Visual Studio, and paste the key 1 Connection String into the value for the StorageConnectionString parameter, and save Local.1Node.xml.

    ![In the 1Node.xml file, the Key 1 Connection String displays.](images/Labs/image92.png "1Node.xml file")

Test configurations:

1.  In Visual Studio, rebuild and publish the application to the local cluster using the steps you followed previously.

2.  After the application is fully published, use Chrome to browse to the Swagger endpoint at <http://localhost:8082/swagger/ui/index>.

3.  Select the Orders API methods, and select the POST operation for /api/orders.

    ![In the Swagger endpoint window, Orders is circled. Below Orders, /api/orders method is circled. While the other methods have Get buttons next to them, the /api/orders method has a Post button next to it.](images/Labs/image93.png "Swagger Endpoint Window")

4.  POST an order to the Contoso Events application. Copy the order request JSON below into the order value box, and select Try it out.

    ```
    {
        "UserName": "johnsmith",
        "Email": "john.smith@gmail.com",
        "EventId": "EVENT1-ID-00001",
        "PaymentProcessorTokenId": "YYYTT6565661652612516125",
        "Tickets": 3
    }
    ```

    ![In the Swagger endpoint window, the POST /api/orders section displays. The Order request JSON is circled, as is the Try it out button at the bottom.](images/Labs/image94.png "Swagger endpoint window")

5.  This should return successfully, with an HTTP 200 response code. The Response Body contains a unique order id that clients could use to track the order.

    ![In the Swagger endpoint window, the Response Body unique order id is circled, and the Response Code of 200 is circled.](images/Labs/image95.png "Swagger Endpoint Window")

    > **Note**: This sends the order to the Web API, which in turn queues the order with the Ticket Order Processing queue. Ultimately, the Ticket Order Actor will pick up the message and process the order.

6.  Now, you should have an order in the Service Fabric App, and it is being processed. In addition, the Ticket Order Actor should have sent the order to the externalization queue you set up in configuration earlier. The actor has pre-existing logic in place to write to this queue.

7.  To verify that the order is in the queue, select View -\> Cloud Explorer from the menu in Visual Studio.

    ![In Visual Studio on the menu bar View and Cloud Explorer are circled.](images/Labs/image96.png "Visual Studio menu bar")

8.  In the Cloud Explorer, select the Account Management icon, and select the check box next to the subscription you are using for this lab, then select Apply. You may need to re-enter your account credentials to see the resources under the subscription.

    ![In the Cloud Explorer pane, the Account Manager icon is circled.](images/Labs/image97.png "Cloud Explorer pane")

9.  Now, expand Storage Accounts under your subscription in Cloud Explorer, and locate the Storage account you set up in Exercise 1, Task 6. You may need to select Load more at the bottom of the list, if you don't see the storage account. Expand the storage account, then expand Queues.

    ![In the Cloud Explorer tree view, under contosoeventskb, Queues is selected.](images/Labs/image98.png "Cloud Explorer tree view")

10. Double-click on the externalization queue, and you should see the message you just sent from Swagger in the document window.

    ![In the Cloud Explorer tree view, under Queues, Contosoeventsexternalization-requests is circled. In the Cloud Explorer document window, a line of message text is circled.](images/Labs/image99.png "Cloud Explorer document window")

11. Now, double-click on the message, and you will see the contents of the message including the JSON representation of the order. Select OK to close the View Message dialog.

    ![In the View Message section, JSON representation of the message displays.](images/Labs/image100.png "View Message section")

### Task 5: Set up the functions

In this task, you will create a function that will be triggered by the externalization queue we created for the app. Each order that is deposited to the queue by the TicketOrderActor type will trigger the ProcessOrderExternalizations function. The function then persists the order to the Orders collection of the Cosmos DB instance.

You will also create a second function that will be used to generate load against the system at runtime. Overall, the ContosoEvents app has the following queue and function architecture. This should help you visualize how the queues and functions are related.

![The ContosoEvents app architecture has two columns - Cosmos DB (Data Store), and Contoso Events (Web API). It also has three rows - Azure Functions, Azure Storage Queues, and Queue Sources. For Cosmos DB, its order of flow begins with Ticket Order Actor, Queue Source. An arrow then points up from Ticket Order Actor to Order Externalization (Its Azure Storage Queue), which then points up to Process order externalization (its Azure Function), which points to its endpoint, Cosmos DB Data Store. For Contoso Events, its order of flow begins with Service Fabric App, its Queue Source. An arrow then points up from there to Order Simulation (Its Azure Storage Queue), which then points up to Process order simulation (its Azure Function), which points to its endpoint, Contoso Events (Web API). its Azure Function is to process order simulization, Its Azure Storage Queue is Order Simulation, and its Queue Source is Service Fabric App. ](images/Labs/image101.png "ContosoEvents app architecture")

1.  There appears to be an issue with Azure Functions detecting Storage accounts, so before creating your function, you will manually add your Storage account connection string to the Application Settings for your Function App.

2.  In the Azure portal, browse to the Storage Account you created in Exercise 1, Step 6, then select Access keys under Settings on the left-hand menu, and copy the key1 Connection String value, as you did previously.

    ![In the Azure Portal, under Settings, Access keys is circled. Under Default keys, the key 1 connection string and its copy button are circled.](images/Labs/image102.png "Azure Portal")

3.  Now, browse to the Function App you created in Exercise 1, Step 5.

4.  Select your Function App in the left-hand menu, then select Application settings under Configured features.

    ![In the Function Apps pane, in the left column, contosoeventsfn-SUFFIX is circled. In the right, Overview column, under Configured features, Application settings is circled.](images/Labs/image103.png "Function Apps pane")

5.  On the Application Settings tab, scroll down and select +Add new setting under Application Settings, then enter contosoeventsstore in the name textbox, and paste the key1 Connection String value you copied from your Storage account into the value textbox.

    ![On the Application settings tab, contosoeventsstore and its corresponding connection string value are circled. At the bottom, the Add new settings button is circled.](images/Labs/image104.png "Application settings tab")

6.  Scroll back to the top of the Application Settings tab, and select Save to apply the change.

    ![Screenshot of the Save button](images/Labs/image105.png "Save button")

7.  From the left-hand menu, place your mouse cursor over Functions, then select the + to the right of Functions.

    ![In the Function Apps section, Functions is selected, and the Plus symbol to its right is circled.](images/Labs/image106.png "Function Apps section")

8.  Select Data processing under the Get started quickly... header, leave CSharp selected for the language, and select the Create this function button.

    ![On the Get started quickly with a premade function page, under Choose a scenario, the Data processing option is circled. Under Choose a language, CSharp is circled. At the bottom, the Create this function button is circled.](images/Labs/image107.png "Get started quickly page")

9.  First, let's rename the function, so it has a more meaningful name.

10. In the left-hand menu, select your Function app, then select the Platform features tab, and select Console under Development Tools.

    ![In the Function Apps pane, in the left column, under Function Apps, contosoeventsfn-SUFFIX is circled. In the right column, at the top, the Platform features tab is circled. Under Development Tools, Console is circled.](images/Labs/image108.png "Function Apps pane")

11. At the Console command prompt, type ls to view the list of functions and files in the wwwroot folder.

    ![The Console command prompt displays.](images/Labs/image109.png "Console command prompt")

12. Next, paste the following command into the console to rename the QueueTriggerCSharp1 function to ProcessOrderExternalizations.

    ```
    rename QueueTriggerCSharp1 ProcessOrderExternalizations
    ```

13. Typing ls at the command prompt again will show the function has been renamed.

    ![The Console command prompt displays with the renamed ProcessOrderExternalizations.](images/Labs/image110.png "Console command prompt")

14. Exit the Console window by selecting the X in the top right corner, just below your account name.

    ![Just below the account icon, the Exit icon is circled.](images/Labs/image111.png "Exit icon")

15. Back on the Function app page, move your mouse cursor over your function app in the left-hand menu, and select the Refresh icon. Note the function name is still QueueTriggerCSharp1 before refreshing.

    ![In the Function Apps section, next to contosoeventsfn-SUFFIX, the refresh icon is circled. under Functions, QueueTriggerCSharp1 is circled.](images/Labs/image112.png "Function Apps section")

16. After the refresh, the function name will change in the display to ProcessOrderExternalizations.

    ![In the Function Apps section, under Functions, QueueTriggerCSharp1 has now changed to ProcessOrderExternalizations.](images/Labs/image113.png "Function Apps section")

17. Under the ProcessOrderExternalizations function, select Integrate.

    ![Under Functions\\ProcessOrderExternalizations, Integrate is circled.](images/Labs/image114.png "Functions  App Section")

18. On the Integrate screen, set the following:

    a.  Message parameter name: Enter orderItem

    b.  Storage account connection: Select the arrows in the box, then select the contosoevents-store connection from the list. This is the Application Setting you added above.

    ![contosoeventsstore is circled on the Integrate screen.](images/Labs/image115.png "Integrate screen")

    c.  Queue name: Enter the name of your externalization queue (from Cloud explorer in Visual Studio). This should be contosoevents-externalization-requests.

    ![On the Integrate screen, the Azure Queue Storage trigger section displays. The Message parameter name is orderItem, the Storage account connection is contosoeventsstore](images/Labs/image116.png "Integrate screen")

    d.  Select Save.

19. While still on the Integrate screen, select +New Output.

    ![On the Integrate Screen, under Outputs, + New Output is circled.](images/Labs/image117.png "Integrate Screen")

20. In the outputs box, locate and select Azure Cosmos DB, then select Select.

    ![In the Azure Cosmos DB output window, next to the Azure Cosmos DB account connection field, the New button is circled.](images/Labs/image118.png "Azure Cosmos DB output window")

21. On the Azure Cosmos DB output screen, enter the following:

    e.  Document parameter name: Enter orderDocument

    f.  Collection name: Enter Orders

    g.  Partition key: Leave empty

    h.  Database name: Enter TicketManager

    i.  Azure Cosmos DB account connection: Select new next to the text box, and select the Cosmos DB you created in Exercise 1, Task 6.

    ![Screenshot of Azure Cosmos DB output window with the values specified above entered into the fields.](images/Labs/image119.png "Azure Cosmos DB output window")

    j.  Select Save. You should now see an Azure Queue Storage trigger and an Azure Cosmos DB output on the Integrate screen.

    ![In the Integrate window, the fields under both Triggers and Outputs are circled. ](images/Labs/image120.png "Integrate window")

22. Next, select your function from the left-hand menu.

    ![Under Functions, ProcessOrderExternailizations is circled.](images/Labs/image121.png "Functions section")

23. Now, you will retrieve the code for the function from a file in Visual Studio.

24. In Visual Studio, go to Solution Explorer, and locate ProcessTicketOrderExternalizationEvent.cs in the Azure Functions folder.

    ![In Solution Explorer, under Azure Functions, ProcessTicketOrderExternalizationEvent.cs is circled.](images/Labs/image122.png "Solution Explorer")

25. Select all the code in that file (CTRL+A) and copy (CTRL+C) it.

26. Return to your function's page in the Azure portal, and replace the code in the run.csx block with the code you just copied from Visual Studio, and select Save. The run.csx code should now look like the following. Note: The ProcessOrdersExternalization function will enable you to process another order, and see that it is saved to the Orders collection of the Cosmos DB.

    ![Code that was copied from Visual Studio displays in the Run.csx block.](images/Labs/image123.png "Azure Portal, Run.csx block")

27. You will now create another function for the load simulation you will use later in this hands-on lab.

28. As before, select + next to Functions in the left-hand menu.

    ![Under Function Apps, contosoeventsfn-SUFFIX is expanded, and under it, the + icon is circled.](images/Labs/image106.png "Function Apps Section")

29. In the Choose a template... screen that appears, locate the Queue trigger box, and select PowerShell.

    ![In the Choose a template screen, in the Queue trigger box, at the bottom, PowerShell is circled.](images/Labs/image124.png "Choose a template, Queue trigger ")

    > **Note**: If the PowerShell option does not show, ensure that the Experimental Language Support is set to Enabled.

30. In the Queue trigger dialog, enter the following:

    k.  Language: Leave PowerShell selected

    l.  Name: Enter ProcessSimulationRequests

    m.  Queue name: Enter your simulation queue name, from Cloud explorer in Visual Studio. The value should be contosoevents-simulation-requests.

    n.  Storage account connection: Select contosoeventsstore from the drop down

    o.  Select Create to create the new function

    ![Fields in the Queue Trigger dialog box are set to the previously defined settings.](images/Labs/image125.png "Queue Trigger dialog box")

31. Select Integrate under the new ProcessSimulationRequests function in the left-hand menu.

    ![Under Functions, under ProcessSimulation Requests, Integrate is circled.](images/Labs/image126.png "Functions section")

32. Make sure Azure Queue Storage is selected under Triggers, then enter the following:

    p.  Message parameter name: Enter simulationRequest

    q.  Storage account connection: Leave set to contosoeventsstore

    r.  Queue name: Leave as contosoevents-simulation-requests

    s.  Select Save.

    ![In the Integrate Window, under Triggers, Azure Queue Storage (triggerInput) is circled. Under Azure Queue Storage trigger, the Message parameter name field is set to simulationRequest.](images/Labs/image127.png "Integrate window")

33. Select the ProcessSimulationRequests function in the left-hand menu.

    ![Under Functions, ProcessSimulation Requests is circled.](images/Labs/image128.png "Functions section")

34. Return to Visual Studio, and open the ProcessTicketOrderSimulationRequest.ps1 file in the Azure Functions folder.

    ![In Solution Explorer, in the Azure Functions folder, ProcessTicketOrderSimulationRequest.ps1 is circled.](images/Labs/image129.png "Solution Explorer")

35. Copy all the contents of this file (CTRL+A, then CTRL+C), then return to your function page in the Azure portal, and paste the code into the run.ps1 code block.

36. Select Save.

37. The final setting to update is the API Management key. You will return to set this up when you set up the API Management service.

### Task 6: Test order data sync

In this task, you will test the ticket order processing back-end, to validate that orders are queued and processed by the ProcessOrderExternalizations function -- ultimately saving the order to the Orders collection of the Cosmos DB instance.

1.  In the Azure Portal, navigate to the Function App.

2.  Select the ProcessOrderExternalizations function (may be listed as the default QueueTriggerCSharp1 name if you did not rename it), and select Logs at the bottom of the screen. Leave the window open with the Logs visible.

    ![At the bottom of the Run.csx block, the Logs button is circled.](images/Labs/image130.png "Azure Portal Run.csx block")

3.  Repeat the steps to post an order via Swagger to the /api/orders endpoint (Task 4, Test configurations, Steps 2 -- 5).

4.  As orders are processed, you will see activity in the function logs in the Azure portal.

    ![In the Azure Portal function log window, the order id of the function is circled.](images/Labs/image131.png "Azure Portal function logs")

5.  Copy the order id of the function just processed. You will use this information below to verify the order was persisted to the Orders collection in Cosmos DB.

6.  If logs are not appearing in this view, click the Monitor tab under the ProcessOrderExternalizations function, then select a log item that has an "id" parameter value passed to the function, as shown below:

    ![In the function apps pane, under Function, the ProcessOrderExternalizations ID parameter value is circled. under Logs, the same ID value is circled.](images/Labs/image132.png "Function apps pane")

7.  In the Azure portal, navigate to your Cosmos DB account, and from the top menu of the Overview blade, select Data Explorer.

    ![In the Azure Cosmos DB account pane, the Data Explorer button is circled.](images/Labs/image133.png "Azure Cosmos DB account pane")

8.  In Cosmos DB Data Explorer, select Orders under the TicketManager database, then select New SQL Query from the toolbar, and enter the following query into the Query 1 window, replacing the ID in red with the order id you copied above.

```
    SELECT * FROM c WHERE c.id = '56dab32a-4154-4ea5-befa-2eb324e142ee'
```

9.  Select Execute Query.

    ![In the Azure Cosmos DB account pane, in the left column, Data Explorer is selected. In the center column, at the top, the New SQL Query button is circled. Under Collections, TicketManager is expanded, and Orders is circled. In the right column, on the Query 1 tab, in the Query 1 field, a callout points to an ID in red, and says, \"Replace with your order ID.\" in the Results pane at the bottom, the same order ID is circled. The Execute Query button is circled as well. ](images/Labs/image134.png "Azure Cosmos DB account pane")

10. If the Cosmos DB query returns the order id specified, the order has been fully processed through to the Cosmos DB.

## Exercise 3: Publish the Service Fabric Application

Duration: 15 minutes

In this exercise, you will publish the Service Fabric Application to the Azure cluster you created previously. After it is deployed, you will validate it by sending orders through the Web API endpoints exposed from the cluster.

### Task 1: Publish the application

In this task, you will deploy the application to a hosted Service Fabric Cluster.

1.  In Visual Studio on your Lab VM, within Solution Explorer, open Cloud.xml from the ApplicationParameters folder of the ContosoEventsApp project, under the Service Fabric folder. This file contains parameters we can use for publishing to the hosted cluster, as opposed to the local cluster.

    ![In the Solution Explorer window, the following path is expanded: Service Fabric\\ContosoEventsApp\\ApplicationParameters. Under ApplicationParameters, Cloud.xml is circled.](images/Labs/image135.png "Solution Explorer window")

2.  Open Local.1Node.XML from the same folder.

3.  To make sure you are using the same parameters you setup earlier for the Local cluster, copy just the following parameters from Local.1Node.xml to Cloud.xml, overwriting the existing parameters in Cloud.xml, then save Cloud.xml.

```
    <Parameter Name="DataStorageEndpointUri" Value="" />
    <Parameter Name="DataStoragePrimaryKey" Value="" />
    <Parameter Name="DataStorageDatabaseName" Value="TicketManager" />
    <Parameter Name="DataStorageEventsCollectionName" Value="Events" />
    <Parameter Name="DataStorageOrdersCollectionName" Value="Orders" />
    <Parameter Name="DataStorageLogMessagesCollectionName" Value="LogMessages" />
    <Parameter Name="StorageConnectionString" Value="" />
    <Parameter Name="LogsStorageTableName" Value="prodlogs" />
    <Parameter Name="ExternalizationQueueName" Value="contosoevents-externalization-requests"/>
    <Parameter Name="SimulationQueueName" Value="contosoevents-simulation-requests" />
```

4.  Review the settings related specifically to cloud publishing.

5.  In Cloud.xml, verify the WebAPi\_InstanceCount parameter is set to -1. This instructs the cluster to create as many instances of the Web API as there are nodes in the cluster.

6.  In Cloud.xml, verify the TicketOrderService\_PartitionCount parameter is set to 5.

```
    <Parameter Name="TicketOrderService_PartitionCount" Value="5" />
    <Parameter Name="TicketOrderService_MinReplicaSetSize" Value="3" />
    <Parameter Name="TicketOrderService_TargetReplicaSetSize" Value="3" />
    <Parameter Name="WebApi_InstanceCount" Value="-1" />
    <Parameter Name="TicketOrderActorService_PartitionCount" Value="5" />
    <Parameter Name="EventActorService_PartitionCount" Value="1" />
```

7.  From Solution Explorer, right-click the ContosoEventsApp project and select Publish.

8.  In the Publish Service Fabric Application dialog, set the Target profile to Cloud.xml, and select your Service Fabric Cluster endpoint from the Connection Endpoint drop down, then select Publish.

    ![In the Publish Service Fabric Application dialog box, the Target profile, which is circled, is set to PublishProfiles\\Cloud.xml. The Connection Endpoint also is circled, and is set to contosoeventssf-SUFFIX.westus2.cloudapp.azure.com:19000.](images/Labs/image136.png "Publish Service Fabric Application dialog box")

9.  Publishing to the hosted Service Fabric Cluster takes about 5 minutes. It follows the same steps as a local publish step with an alternate configuration. The Visual Studio output window keeps you updated of progress.

10. From the Visual Studio output window, validate that the deployment has completed successfully before moving on to the next task.

### Task 2: Test an order from the cluster

In this task, you will test an order against your application deployed to the hosted Service Fabric Cluster.

1.  In a Chrome browser on your Lab VM, navigate to the Swagger endpoint for the Web API exposed by the hosted Service Fabric cluster. The URL is made of:

    > For example:
    >
    > <http://contosoeventssf-SUFFIX.eastus.cloudapp.azure.com:8082/swagger/ui/index>

2.  Expand the Orders API and expand the POST method of the /api/orders endpoint.

    ![On the Swagger Endpoint webpage for ContosoEvents.WebApi, Orders is circled. Under Orders, the POST method for api/orders is expanded, and the order field, which currently is empty, is circled.](images/Labs/image137.png "Swagger Endpoint webpage")

3.  Copy the JSON below, and paste it into the order field, highlighted in the screen shot above, then select Try it out.

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

    ![In the POST method for api/orders section, the order field now contains the previous JSON. At the bottom, the Try it out button is circled.](images/Labs/image138.png "POST api/orders section")

4.  This should return with HTTP 200 response code. The Response Body includes a unique order id that can be used to track the order. Copy the Response Body value. It will be used to verify the order was persisted in Cosmos DB.

    ![In the Try it out section, the Response Body and unique order ID is circled, as is the Response Code (200).](images/Labs/image139.png "Try it out section")

5.  Verify that the order was persisted to the Orders collection.

6.  In the Azure portal, navigate to your Cosmos DB account.

7.  Perform a query against the Orders collection, as you did previously, to verify the order exists in the collection. Replace the id in the query with the order id you copied from the Response Body above.

    ![In the Azure Cosmos DB account, on the top menu, the New SQL Query button is circled. In the left column, under Collections,TicketManager is expanded, and Orders is circled. In the right column, on the Query 1 tab, in the Query 1 field, an ID in red is circled. In the Results pane at the bottom, the same order ID is circled. The Execute Query button is circled as well. ](images/Labs/image140.png "Azure Cosmos DB account")

## Exercise 4: API Management

Duration: 15 minutes

In this exercise, you will configure the API Management service in the Azure portal.

### Task 1: Import API

In this task, you will import the Web API description to your API Management service to create an endpoint.

1.  In the Azure portal, navigate to the hands-on-labs resource group, and select your API Management Service from the list of resources.

    ![In the Resource group list of resources, the contosoevents-SUFFIX API Management service is circled.](images/Labs/image141.png "Resource group list of resources")

2.  In the API Management blade, select APIs under Api Management.

    ![In the API Management blade, on the left, under Api Management, APIs is circled.](images/Labs//image142.png "API Management blade")

3.  In the APIs blade, select OpenAPI specification.

    ![In the APIs blade, OpenAPI specification is circled.](images/Labs//image143.png "APIs blade")

4.  Return to your Swagger browser window, and copy the URL from the textbox at the top of the screen, next to the Swagger logo, as shown in the screen shot below.

    ![In the Swagger browser window, the URL is circled.](images/Labs/image144.png "Swagger browser window")

5.  Return to the Create from OpenAPI specification window, and do the following:

    a. Paste the URL copied from Swagger into the OpenAPI specification textbox.

    b. Select HTTPs as the URL scheme.

    c. Enter events in the API URL suffix textbox.

    d. Note the URL under "Base URL". You will use this URL in your website configuration in the next exercise.

    e. Select Unlimited in the Products.

    f. Select Create.

    ![On the Create from OpenAPI specification window, fields are set to previously defined settings and Base URL is circled.](images/Labs/image145.png "Create from OpenAPI specification")

    > **Note**: You would typically create a new product for each environment in a scenario like this one. For example, Development, Testing, Acceptance and Production (DTAP) and issue a key for your internal application usage for each environment, managed accordingly.

6.  Select Settings in the ContosoEvents.WebApi toolbar, update Web Service URL so that it uses HTTP instead of HTTPS, and select Save

    ![On the right of ContosoEvents.WebApi api blade, the Settings tab is selected, and Web Service URL and Save are circled.](images/Labs/image145a.png "")

7.  Select ContosoEvents.WebApi from the All APIs list, and then select Design. You will see your API backend endpoint.

    ![In the APIs blade, ContosoEvents.WebApi is circled. On the right, the Design tab is selected, and the ContosoEvents.WebApi Backend endpoint URL is circled.](images/Labs/image146.png "Publisher portal")

### Task 2: Retrieve the user subscription key

In this task, you will retrieve the subscription key for the client applications to call the new API Management endpoint.

1.  In the Azure portal, navigate to your API Management service, and from the Overview blade, select Developer portal from the toolbar. This will open a new browser tab, and log you into the Developer portal as an administrator, giving you the rights you need to complete the following steps.

    ![In the API Management service pane, on the toolbar, the Developer portal button is circled.](images/Labs/image147.png "API Management service")

2.  In the Developer portal, expand the Administrator menu, and then select Profile.

    ![In the Contoso Events API Developer portal, the down-arrow next to Administrator is circled, and in its drop-down menu, Profile is circled.](images/Labs/image148.png "Developer portal")

3.  Select Show for the Primary Key of the Unlimited subscription to reveal it.

    ![In the Your Subscriptions section, for the Unlimited (default) subscription\'s Primary key, the Show button is circled.](images/Labs/image149.png "Your Subscriptions section")

4.  Save this key for next steps.

    ![The Unlimited (default) subscription\'s Primary key now displays, and is circled.](images/Labs/image150.png "Unlimited subscription's Primary key")

5.  You now have the API Management application key you will need to configure the Function App settings.

### Task 3: Configure the Function App with the API Management key

In this task, you will provide the API Management key in a setting for the Function App, so it can reach the Web API through the API Management service.

1.  From the Azure Portal, browse to the Function App.

2.  You will create an Application setting for the function to provide it with the API Management consumer key.

3.  Select your Function App in the left-hand menu, then select Application settings under Configured features.

    ![In the Function Apps pane, on the left under Function Apps, contosoeventsfn-SUFFIX is circled. On the right under Configured features, Application settings is circled.](images/Labs/image103.png "Function Apps")

4.  Scroll down to the Application settings section, select +Add new setting, and enter contosoeventsapimgrkey into the name field, and paste the API key you copied from the Developer portal above into the value field.

    ![In the Application settings section, in the name field displays contosoeventsapimgrkey, and the copied API key displays in the value field. At the bottom, the + Add new setting button is circled.](images/Labs/image151.png "Application settings section")

5.  Scroll back to the top of the Application Settings tab, and select Save to apply the change.

    ![Screenshot of the Save button.](images/Labs/image105.png "Save button")

## Exercise 5: Configure and publish the web application

Duration: 15 minutes

In this exercise, you will configure the website to communicate with the API Management service, deploy the application, and create an order.

### Task 1: Configure the web app settings

In this task, you will update configuration settings to communicate with the API Management service. You will be guided through the instructions to find the information necessary to populate the configuration settings.

1.  Within Visual Studio Solution Explorer on your Lab VM, expand the Web folder, then expand the ContosoEvents.Web project, and open Web.config. You will update these appSettings in this file:

    ```
    <add key="apimng:BaseUrl" value="" \>
    <add key="apimng:SubscriptionKey" value="" \>
    ```

    ![In Solution Explorer, the following folders are expanded: Web\\ContosoEvents.Web\\Web.config.](images/Labs/image152.png "Solution Explorer")

2.  For the apimng:BaseUrl key, enter the base URL of the API you created in the API Management Publisher Portal (Exercise 5, Task 1, Step 5), such as <http://contosoeventsSUFFIX.azure-api.net/events/>.

    > **Note**: Make sure to include a trailing "/" or the exercise will not work.

3.  For the apimng:SubscriptionKey key, enter the subscription key you revealed in API Management developer portal (Exercise 5, Task 2, Step 4).

4.  Save Web.config. You should have values for two of the API Management app settings.

    ![In Web.config, two values (one a URL, the other a subscription key), display.](images/Labs/image153.png "Web.config")

### Task 2: Running the web app and creating an order

In this task, you will test the web application calls to API Management by creating an order through the UI.

1.  Using Solution Explorer in Visual Studio, expand the Web folder, then right-click the ContosoEvents.Web project, select Debug, and then Start new instance.

    ![In Solution Explorer, ContosoEvents.Web is circled, and its right-click menu displays.](images/Labs/image154.png "Solution Explorer")

2.  If prompted about whether you would like to trust the IIS Express SSL certificate, select Yes, then select Yes again at the Security Warning prompt.

    ![A Microsoft Visual Studio warning message displays, asking if you trust the IIS Express SSL certificate.](images/Labs/image155.png "Microsoft Visual Studio warning message")

3.  If you receive a warning in the browser that "Your connection is not private," select Advanced.

    ![On the Your connection is not private warning, the Advanced button is circled.](images/Labs/image156.png "Your connection is not private warning")

4.  Under Advanced, select Proceed to localhost (unsafe).

    ![The Advanced warning displays once you click the Advanced button. It explains that the server culd not prove that it is localhost, and its security certificate does not specify SANs. At the bottom, the Proceed to localhost (unsafe) button is circled.](images/Labs/image157.png "Advanced section")

5.  When the application launches you will see the website home page as shown in the following screen shot.

    ![The Contoso Events website displays, with information about the Seattle Rock and Rollers concert tickets. At the bottom of the page is the Order tickets now button.](images/Labs/image158.png "Contoso Events website")

6.  Note the event presented on the home page has an Order Tickets Now button. Click that to place an order.

7.  Choose the number of tickets for the order, and then scroll down to see the billing fields.

    ![The ticket ordering page for the Seattle Rock and Rollers concert displays. Information includes date, time, and price per ticket. Under Order, a drop-down list lets users choose the number of tickets to purchase.](images/Labs/image159.png "Ticket Ordering page")

8.  Since you have not yet integrated Azure Active Directory B2C, the application does not know who you are. You will have to enter values into the empty fields for your email, first name, last name, and Cardholder name.

    ![On the Billing page, on the left under Billing, the Email, First name, and Last name fields are circled. On the right under Credit Card, the Cardholder Name field is circled, as is the Place Order button at the bottom. ](images/Labs/image160.png "Billing information page")

9.  Select Place Order.

10. Once the order is queued for processing, you will be redirected to a results page as shown in the following screen shot. It should indicate Success and show you the order id that was queued as confirmation.

    ![The Results page says Success, and includes an Order ID number.](images/Labs/image161.png "Results page")

11. Close the web browser to stop debugging the application.

### Task 3: Publish the web app

In this task, you will publish the web application to Azure.

1.  From the Visual Studio Solution Explorer, right-click ContosoEvents.Web, and select Publish.

    ![In Solution Explorer, on the right-click menu for ContosoEvents.Web, Publish is circled.](images/Labs/image162.png "Solution Explorer")

2.  Select the App Service option, choose Select Existing, then select Publish.

    ![Under Publish, the Microsoft Azure App Service tile is circled. Under this tile, the radio button is selected for Select Existing, and is circled. At the bottom, the Publish button is circled.](images/Labs/image163.png "Publish section")

3.  You may be prompted to log in to your Microsoft Account with access to the subscription where you created the resources for this hands-on lab. After logging in, you can select the subscription in the App Service screen.

4.  From the list below, expand the Resource Group you created previously (hands-on-labs), and select the web app contosoeventsweb-SUFFIX. Select OK.

    ![In the App Service window, in the Resource group pane, the hands-on-labs folder is expanded, and contosoeventsweb-SUFFIX is selected. At the bottom of the window, the OK button is circled.](images/Labs/image164.png "App Service window")

5.  If the Publish does not start automatically, select Publish next to the Web Deploy publishing profile.

    ![In the Publish section, the Publish button is circled.](images/Labs/image165.png "Publish section")

6.  When publishing is complete, your browser will launch, and navigate to the deployed web app home page. You can optionally submit another order to validate functionality works as in Task 2.

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

1.  In Visual Studio on the Lab VM, open TicketOrder.cs in the ContosoEvents.Models project, under the Common folder.

    ![In Solution Explorer, under Common, under ContosoEvents.Models, TicketOrder.cs is circled.](images/Labs/image167.png "Solution Explorer")

2.  Edit the TicketOrder type to include a status field based on an Enum. Uncomment all TODO: Exercise 6 -- Task 1 -- there are two places as shown below:

```
    //TODO: Exercise 6 - Task 1
    [DataMember]
    public OrderStatuses Status { get; set; }
```

3.  and

```
    //TODO: Exercise 6 - Task 1
    public enum OrderStatuses
    {
    Fufilled,
    TicketsExhausted,
    CreditCardDenied,
    Cancelled,
    Invalid
    }
```

4.  Save TicketOrder.cs.

5.  From Solution Explorer, open TicketOrderActor.cs in the ContosoEvents.TicketOrderActor project, under the Service Fabric folder.

6.  Edit the TicketOrderActor to add the new order status. Uncomment all TODO: Exercise 6 -- Task 1. The change will uncomment several lines that set the new Status field to one of the OrderStatuses enumeration values. Be sure to find all of the following comments (there are 6 total):

```
    //TODO: Exercise 6 - Task 1
    state.Status = OrderStatuses.Invalid;
    //TODO: Exercise 6 - Task 1
    state.Status = OrderStatuses.Fufilled;
    //TODO: Exercise 6 - Task 1
    state.Status = OrderStatuses.CreditCardDenied;
    //TODO: Exercise 6 - Task 1
    state.Status = OrderStatuses.TicketsExhausted;
    //TODO: Exercise 6 - Task 1
    state.Status = OrderStatuses.Invalid;
    //TODO: Exercise 6 - Task 1
    state.Status = OrderStatuses.Cancelled;
```

7.  Save TicketOrderActor.cs.

8.  After adding this field, the actor will now save it with each ticket order.

9.  After making this change, rebuild the solution (Build menu, Rebuild solution), and verify that there are no errors.

### Task 3: Perform a smooth upgrade

In this task, you will configure settings for the Service Fabric application to perform an upgrade.

1.  From the Visual Studio Solution Explorer, expand the Service Fabric folder, then right-click ContosoEventsApp, and select Publish.

2.  In the Public Service Fabric Application dialog, select PublishProfiles\\Cloud.xml for the target profile, and check Upgrade the Application.

    ![In the Public Service Fabric Application dialog box, in the Target profile field, PublishProfiles\\Cloud.xml is circled. The checkbox for Upgrade the Application is selected and circled.](images/Labs/image168.png "Public Service Fabric Application dialog box")

3.  Select Configure Upgrade Settings, under Upgrade the Application. Select Monitored for the upgrade mode, then select OK.

    ![In the Edit Upgrade Settings dialog box, the Upgrade mode is set to Monitored, and is circled.](images/Labs/image169.png "Edit Upgrade Settings dialog box")

4.  From the Publish Service Fabric Application dialog, select Manifest Versions.

5.  Change the TicketOrderActorPkg\\Code New Version to 1.1.0. This change will force the actor package and the app to change to 1.1.0 as well.

    ![In the Edit Versions dialog box, in the Application and Services section, ContosoEventsAppyType is expanded. Under that, ContosoEvents.TicketOrderActorPkg is expanded. Under that, the Code line is circled which shows that the current Code version is 1.0.0, and the new version is 1.1.0.](images/Labs/image170.png "Edit Versions dialog box")

6.  Select Save.

7.  Now that the upgrade configuration is set, select Publish.

8.  Observe the Visual Studio Output window going through the upgrade process, which can take 5 minutes or more.

    ![The Visual Studio Output window shows that the Upgrade completed successfully.](images/Labs/image171.png "Visual Studio Output window")

9.  Navigate to the Service Fabric Explorer for the deployment using your URL, something like: <http://contosoeventssf-SUFFIX.eastus.cloudapp.azure.com:19080/Explorer/index.html>. You can retrieve this from the Azure portal, by navigating to your Service Fabric cluster's blade by selecting the Explorer button on the toolbar, or selecting the Service Fabric Explorer link in the Essentials area.

    ![In the Service Fabric cluster pane, on the top menu, the Explorer button is circled, as is the Service Fabric Explorer URL at the bottom.](images/Labs/image172.png "Service Fabric cluster pane")

10. It will show the app being upgraded one upgrade domain at a time.

    ![In the Service Fabric Explorer window, a callout arrow points to the Status, which is set to Upgrading. Under Upgrade in progress, the Current Version (1.0.0) and the Target Version (1.1.0) are circled.](images/Labs/image173.png "Service Fabric Explorer window")

11. When the upgrade is complete, from Service Fabric Explorer observe the new application version number.

    ![In the Service Fabric Explorer window, The Application Type (ContosoEventsAppType) and Version (1.1.0) are circled. Under Services, the Version numbers are circled for the listed services.](images/Labs/image174.png "Service Fabric Explorer window")

### Task 4: Submit a new order

Now that the upgrade is completed successfully, you will submit a new order, and make sure that the newly submitted order has the extended state.

1.  This time, you will post an order using the Web API for the deployed service. The order can be something like this:

```
    {
    "userName": "testupgrade",
    "email": "test.upgrade@gmail.com",
    "eventId": "EVENT1-ID-00001",
    "paymentProcessorTokenId": "ggashwh565-uiewuu87-ujdsk",
    "tickets": 3
    }
```

2.  Access the Swagger UI for your published Service Fabric Web API at a URL that looks like this: <http://contosoeventssf-SUFFIX.eastus.cloudapp.azure.com:8082/swagger/ui/index>

3.  Access the Orders API and select the POST method for the /api/orders endpoint. From there you can submit a new order using the JSON above.

    ![In the POST method for api/orders section, the order field now contains the previous JSON. At the bottom, the Try it out button is circled.](images/Labs/image175.png "POST /api/orders section")

4.  Once you get back a 200 response code, the order id will be returned in the Response Body.

    ![In the Try it out section, the Response Body unique order ID is circled.](images/Labs/image176.png "Try it out section")

5.  In the Azure portal, navigate to your Cosmos DB account.

6.  Go to Cosmos DB Data Explorer, and query for the order id to see the new extended state actually persisted to the database, as you did in Exercise 3, Task 6, Steps 7-9.

    ![In the Azure Cosmos DB account, on the top menu, the New SQL Query button is circled. In the left column, under Collections,TicketManager is expanded, and Orders is circled. In the right column, on the Query 1 tab, in the Query 1 field, an ID in red is circled. In the Results pane at the bottom, the same order ID is circled. The Execute Query button is circled as well. ](images/Labs/image177.png "Azure Cosmos DB account")

## Exercise 7: Rollback## Exercise 7: Rollback

Duration: 30 minutes

In this exercise, you will deploy an update that causes issues with the application, and will trigger an automatic rollback of the deployment. This exercise will illustrate the mechanism Service Fabric provides for preserving application health and availability in production.

### Task 1: Add health checks

In this task, you will add code to produce health checks that force the monitored upgrade to roll back to the original version of the service.

1.  In Visual Studio, open TicketOrderService.cs located in the ContosoEvents.TicketOrderService project in the Service Fabric folder.

2.  Locate TODO: Exercise 7 - Task 1 and uncomment:

    ```
    //TODO: Exercise 7 - Task 1
    this.HealthReporterService.SendReportForService(HealthState.Error, "Simulated Error");
    ```

3.  Compile the code to ensure there are no issues with the changes.

### Task 2: Perform a troubled upgrade

In this task, you will perform an upgrade, and watch a rollback of the upgrade.

1.  From Solution Explorer in Visual Studio, right-click the ContosoEventsApp project, under the Service Fabric folder, and select Publish.

2.  From the Publish Service Fabric Application dialog, check Upgrade the Application, and click Manifest Versions.

3.  Change the TicketOrderServicePkg\\Code New Version to 1.1.0. This change will force the service package be change to 1.1.0 and the application to 1.2.0.

    ![In the Edit Versions dialog box, in the Application and Services section, ContosoEventsAppyType is expanded. Under that, ContosoEvents.TicketOrderServicePkg is expanded. Under that, the Code line is circled which shows that the current Code version is 1.0.0, and the new version is 1.1.0.](images/Labs/image178.png "Edit Versions dialog box")

4.  Select Save.

5.  Select Publish, and return to Service Fabric Explorer.

6.  Observe the time it is taking to upgrade in Visual Studio and the errors that are now occurring in Service Fabric Explorer.

7.  Notice that the simulated error message 'Simulated error' appears in the event as shown in the following screen shot:

    ![In the Service Fabric Explorer, on the Essentials tab, an Error icon displays next to Health State. Under Upgrade in Progress, a red arrow points from the Current Version 1.1.0 to the Target Version 1.2.0. Under Unhealthy Evaluations, Error icons display in the Health State column for all services, partitions, and event. For Event, the Error description line has the following text circled: Property=\'Simulated Error\'.](images/Labs/image179.png "Service Fabric Explorer")

    > **Note**: Service Fabric is attempting to upgrade, and it is waiting for the service to report healthy status. Because this will not happen, eventually Service Fabric rolls back the upgrade.

8.  In the meantime, observe that the application is still responsive. In the Swagger UI for your Service Fabric Web API, access the Events API and select GET /api/events to see a list of events as shown in the following screen shot:

    ![The GET method for api/events section displays.](images/Labs/image180.png "GET method for api/events section")

9.  So that you do not forget, return to the code and re-comment the failure report so that you can do the next exercise without rollback!
    ```
    //TODO: Exercise 7 - Task 1
    //this.HealthReporterService.SendReportForService(HealthState.Error, "Simulated Error");
    ```

10. Look at the Visual Studio output window and note that after some time (600 seconds by default, and this is configurable) Service Fabric gives up on the app and rolls back the upgrade as shown in the following screen shot:

    ![In the Visual Studio Output Window, the message stating that the Upgrade was rolled back is circled.](images/Labs/image181.png "Visual Studio Output Window")

11. Return to Service Fabric Explorer and note that version 1.2.0 (that contained the simulated error) was rolled back to version 1.1.0, the version that was running in your cluster before the attempted upgrade.

12. Also, note that the error remains until its time to live expires or it is replaced by another health state. Until then, the unhealthy state will remain in the cluster, but the cluster will be running normally. You can proceed without clearing this for now.

13. The subsequent exercises (i.e. 8 and beyond) will be executed using version 1.1.0 and while the cluster shows unhealthy state. You can ignore this for now.

    ![In the Service Fabric Explorer, on the Essentials tab, an Error icon displays next to Health State. To the right, Version 1.1.0 is circled. Under Unhealthy Evaluations, Error icons display in the Health State column for all services, partitions, and event. Under Services, the service versions are circled.](images/Labs/image182.png "Service Fabric Explorer")

14. Optionally, from the Swagger endpoint for the deployed application, you can request health statistics at the following relative URL: /api/admin/applicationhealth.

## Exercise 8: Load testing

Duration: 15 minutes

In this exercise, you will perform a load test against the Service Fabric Cluster and observe how messages are distributed across partitions.

### Task 1: Simulate a 50-order request

In this task, you will simulate a load test of 50 orders against the cluster using the Web application to submit the load test and monitor partitions.

1.  Navigate to the published Web application at a URL like <https://contosoeventsweb-SUFFIX.azurewebsites.net>.

2.  Click the Load Test menu. Optionally give a new name to the tag for tracking. Set load to 50 requests. Click Start Load Test.

    ![In the Load Test section, the Event is Seattle Rock and Rollers. The Tag is load-test-1, and the number of requests is set to 50.](images/Labs/image183.png "Load Test section")

3.  Navigate to the Load Test Status menu. It shows you the partitions that were created for the ticket order service (reliable queue).

    ![The Simulation Status window displays the following columns: Partition ID, Partition Status, Node Name, Health State, and Items in Queue.](images/Labs/image184.png "Simulation Status window")

4.  While the load test is running, refresh this page and watch the changes to the Items in queue across partitions. It will fill while processing completes and then eventually drain.

5.  After a few minutes you will see that the queues are drained, and the orders were processed.

> **Note**: If you still have more time, run this again with additional iterations progressively such as 100, 150, 200, 250. Or, take a look at Exercise 9 which takes you through a much more comprehensive load test and partition analysis process using the API endpoint.

## BONUS Exercise 9: Load testing w/ partitions

> **Note**: If you completed the other work in good time and still have another 50 minutes free, have some load testing and partitioning fun! Otherwise, skip to [After the hands-on lab](#after-the-hands-on-lab).

Duration: 50 minutes

In this task, you will perform several load tests against the Cluster using different partitions. This experimentation is crucial to get an idea of how many partitions you will really need. It is important to note that the number of partitions in your service cannot be changed after you have created the service. The main measure you are going to rely on is the average number of seconds it takes an order to be processed.

### Task 1: Using the current partition count, simulate 100 orders

In this task, you will simulate a load test against the Cluster using the current partition count (that is, 5) of the Ticket Order Service.

1.  Using the Service Fabric Web API Swagger UI, please issue a POST request against /api/admin/simulate/orders

    ![In the POST method for api/admin/simulate/orders section, the request field, which is empty, has a callout saying to place the simulation request here.](images/Labs/image190.png "POST method for api/admin/simulate/orders section")

2.  A sample simulation order request can be formed as follows. The tag identifies the simulation run so we can report on it later. Be sure to replace the values in the baseUrl property:

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

3.  As the simulation request is processed, please issue a GET request against /api/admin/partitions to see how the different partitions are functioning. This returns partition info, health, and the number of items in each partition queue. You should notice that the queues fill up with order requests and are drained.

    ![The GET method for api/admin/partitions displays.](images/Labs/image191.png "GET method for api/admin/partitions section")

4.  The response might look like this.
    ```
    [
        {
            "partitionId": "b308870f-1631-45bd-a256-a61ac9814fff",
            "partitionKind": "Int64Range",
            "partitionStatus": "Ready",
            "nodeName": "_Web_2",
            "healthState": "Ok",
            "serviceKind": "Stateful",
            "itemsInQueue": 1
        },
        {
            "partitionId": "ae2ac24c-d73b-4228-b2d6-2191913b9252",
            "partitionKind": "Int64Range",
            "partitionStatus": "Ready",
            "nodeName": "_Web_1",
            "healthState": "Ok",
            "serviceKind": "Stateful",
            "itemsInQueue": 2
        },
        {
            "partitionId": "8f02f0a8-5e86-497c-b2b0-0e90a612e2d5",
            "partitionKind": "Int64Range",
            "partitionStatus": "Ready",
            "nodeName": "_Web_3",
            "healthState": "Ok",
            "serviceKind": "Stateful",
            "itemsInQueue": 0
        },
        {
            "partitionId": "9642e5dd-6db3-498d-ba79-6609ffaa8af3",
            "partitionKind": "Int64Range",
            "partitionStatus": "Ready",
            "nodeName": "_Web_4",
            "healthState": "Ok",
            "serviceKind": "Stateful",
            "itemsInQueue": 1
        },
        {
            "partitionId": "3cee90e3-0a19-421d-bc0d-7de643531fa0",
            "partitionKind": "Int64Range",
            "partitionStatus": "Ready",
            "nodeName": "_Web_0",
            "healthState": "Ok",
            "serviceKind": "Stateful",
            "itemsInQueue": 0
        }
    ]
    ```

5.  Wait for 2-3 minutes to make sure that queues are drained and that orders are processed before completing this task.

### Task 2: Setting up for load testing with different partition counts

In this task, you will clean the existing orders from the Cosmos DB, so you can start with clean slate. This step is optional but because we are going to rely on reporting about orders in the database, it is much better to keep in the database only the orders that were simulated for load testing.

1.  In the Swagger UI for your Service Fabric Web API, please access the admin APIs DELETE /api/admin/orders and clicl Try it out. When you get back a 200-response code, the orders will have been deleted from the Cosmos DB.

    ![On the Swagger Endpoint webpage for ContosoEvents.WebApi, under Admin, the Delete method for /api/admin/orders section is expanded. Current Response Messages have statuses of 400 and 404.](images/Labs/image185.png "Swagger Endpoint webpage")

2.  Because you have previously performed an upgrade to the Service Fabric application, and we want to play with partition sizes in this exercise, you will unprovision the application type using Service Fabric Explorer. Navigate to the explorer.

3.  Delete the application.

    ![In Service Fabric Explorer, the following tree-view is expanded: Cluster\\Applications\\ContosoEventsAppType\\fabric:/ContosoEventsApp. Below this, a Delete Application button displays.](images/Labs/image186.png "Service Fabric Explorer")

4.  Unprovision the application type.

    ![In Service Fabric Explorer, the following tree-view is expanded: Cluster\\Applications\\ContosoEventsAppType\\fabric:/ContosoEventsApp. Below this, an Unprovision Type button displays.](images/Labs/image187.png "Service Fabric Explorer")

5.  In the tasks that follow in this exercise you will not be upgrading when you publish the application. You will be re-publishing. Make sure Upgrade the application checkbox is unchecked each time you publish.

    ![Screenshot of the Upgrade the Application checkbox](images/Labs/image188.png "Upgrade the Application checkbox")

6.  Service Fabric Explorer shows no application types or applications deployed.

7.  You can verify from Cosmos DB Orders Document Explorer that there are no more orders in the database:

    ![In the Cosmos DB Orders Document Explorer, Databases is set to TicketManager, and Collections is set to Orders.](images/Labs/image189.png "Cosmos DB Orders Document Explorer ")

### Task 3: Using a partition count of 10, simulate 100 orders

In this task, you will repeat the same load test you performed in Task 1 but using a partition count of 10.

1.  Change the service and actor partition count to 10 in the Cloud.xml Application Parameters file.

2.  Double-click the document in Visual Studio and make the following changes:

    ```
    <Parameter Name="TicketOrderService_PartitionCount" Value="10" />
    <Parameter Name="TicketOrderService_MinReplicaSetSize" Value="3" />
    <Parameter Name="TicketOrderService_TargetReplicaSetSize" Value="3" />
    <Parameter Name="WebApi_InstanceCount" Value="-1" />
    <Parameter Name="TicketOrderActorService_PartitionCount" Value="10" />
    <Parameter Name="EventActorService_PartitionCount" Value="1" />
    ```

3.  Using Visual Studio Publish command, redeploy the app to the cluster (as shown in a previous task).

4.  Repeat the same test load you did in Task 1 but with a different tag:

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

5.  Wait for 2-3 minutes until to make sure that queues are drained and that orders are processed before completing this task.

### Task 4: Using a partition count of 15, simulate 100 orders

In this task, you will repeat the same load test you performed in Task 1 but using a partition count of 15.

1.  Change the service and actor partition count to 15 in the Cloud.xml Application Parameters file.

2.  Double-click the document in Visual Studio and make the following changes:

    ```
    <Parameter Name="TicketOrderService_PartitionCount" Value="15" />
    <Parameter Name="TicketOrderService_MinReplicaSetSize" Value="3" />
    <Parameter Name="TicketOrderService_TargetReplicaSetSize" Value="3" />
    <Parameter Name="WebApi_InstanceCount" Value="-1" />
    <Parameter Name="TicketOrderActorService_PartitionCount" Value="15" />
    <Parameter Name="EventActorService_PartitionCount" Value="1" />
    ```

3.  Using the Visual Studio Publish command, redeploy the app to the cluster (as shown in a previous task).

4.  Repeat the same test load you did in Task 1 but with a different tag:

    ```
    {
        "baseUrl": "http://<your-cluster-name>.<your-region>.cloudapp.azure.com:8082",
        "eventId": "EVENT1-ID-00001",
        "userName": "tester",
        "email": "load.tester@gmail.com",
        "tag": "partitions-15-100",
        "iterations": 100
    }

5.  Wait for 2-3 minutes until to make sure that queues are drained and that orders are processed before completing this task.

### Task 5: Using a partition count of 20, simulate 100 orders

In this task, you will repeat the same load test you performed in Task 1 but using a partition count of 20.

1.  Change the service and actor partition count to 20 in the Cloud.xml Application Parameters file.

2.  Double-click the document in Visual Studio and make the following changes:

    ```
    <Parameter Name="TicketOrderService_PartitionCount" Value="20" />
    <Parameter Name="TicketOrderService_MinReplicaSetSize" Value="3" />
    <Parameter Name="TicketOrderService_TargetReplicaSetSize" Value="3" />
    <Parameter Name="WebApi_InstanceCount" Value="-1" />
    <Parameter Name="TicketOrderActorService_PartitionCount" Value="20" />
    <Parameter Name="EventActorService_PartitionCount" Value="1" />
    ```

3.  Using Visual Studio Publish command, redeploy the app to the cluster (as shown in a previous task).

4.  Repeat the same test load you did in Task 1 but with a different tag:

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

5.  Wait for 2-3 minutes until to make sure that queues are drained and that orders are processed before completing this task.

### Task 6: Determine the performance variations among the different load tests

In this task, you will find out how each load test performed and plot the result.

1.  Using the Service Fabric Web API Swagger UI, please issue a GET request against /api/orders/stats. ![The GET method for api/orders/stats displays.](images/Labs/image192.png "GET method for api/orders/stats ")

2.  The command returns stats about each load test you performed in JSON that looks like this:

    ```
    [
        {
            "tag": "partitions-5-100",
            "count": 100,
            "sumSeconds": 879.2576443999999,
            "averageSeconds": 8.792576443999998
        },
        {
            "tag": "partitions-10-100",
            "count": 100,
            "sumSeconds": 340.0996231000001,
            "averageSeconds": 3.400996231000001
        },
        {
            "tag": "partitions-15-100",
            "count": 100,
            "sumSeconds": 162.2106096,
            "averageSeconds": 1.622106096
        },
        {
            "tag": "partitions-20-100",
            "count": 100,
            "sumSeconds": 165.14757820000003,
            "averageSeconds": 1.6514757820000003
        }
    ]
    ```

3.  Scale out the VMs count to 10, for example, in your cluster and repeat tasks 1, 3, 4, and 5. This step is out of scope and is shown here only to complete the picture.

4.  Given the load test results for each Cluster configuration, produce an Excel sheet from the data you collected. A sample may look like this:

    ![An Excel bar graph displays the average number of seconds it takes to process orders for different numbers of partitions (ranging from 5 - 25 partitions). The graph data is split into two sides, 5 VMs on the left, and 10 VMs on the right. Average times are lower for the partition ranges on the 10 VMs side.](images/Labs/image193.png "Excel graph of Average seconds to process orders")

5.  Armed with an average number of seconds it takes to process orders for different partition and VMs count, you are in a better situation to recommend a partition count for your application.

## BONUS Exercise 10: Secure the web application

If you completed the other work in good time and still have another 30 minutes, do this exercise and integrate Azure Active Directory B2C with the application. Otherwise, skip to [After the hands-on lab](#after-the-hands-on-lab).

Duration: 30 minutes

In this exercise, you will configure the Azure Active Directory B2C tenant and configure the Web front end to integrate with it for user login. Once all the settings are in place, you will be able to run the website, register as a user, and login.

### Task 1: Configure the Azure Active Directory B2C

In this task, you will set up the Azure Active Directory B2C directory for your application to integrate with it.

1.  From the Azure Portal browse to Azure B2C. Select it to navigate to the Azure AD B2C Settings blade.

    ![In the Azure Portal left menu, More Services is selected. In the More Services pane, b2c is typed in the Search field. Under it, Azure AD B2C is circled.](images/Labs/image194.png "Azure Portal")

2.  You should see the domain name you created earlier for your B2C directory.

    > **Note**: If you see an authorization error, you may have to select the directory from your profile menu and then repeat steps 1 and 2. Further, if your directory does not yet appear in the profile list, you should refresh the portal page to see it in the list.

    ![In the Azure AD B2C Settings pane, a callout arrow points to the Domain name contosoeventsb2csoll3.onmicrosoft.com](images/Labs/image195.png "Azure AD B2C Settings pane")

    ![In the Profile menu, a callout points to Directory.](images/Labs/image196.png "Profile menu")

3.  From the Settings blade, select Applications.

    ![In the Settings blade, under Manage, a callout arrow points to Applications.](images/Labs/image197.png "Settings blade")

4.  Click +Add.

5.  Set the application name to WebApp.

6.  Select Yes for include Web App / Web API.

7.  Select Yes for Allow implicit flow.

8.  Add a reply URL for local testing: <https://localhost:44327/>

9.  Add a reply URL for the hosted Web App as you named it, for example: <https://contosoeventsweb-SUFFIX.azurewebsites.net/>

    > **Note**: Make sure to include the closing / or the configuration will not work.

10. Click Create.

    ![On the New application blade, fields are set to the previously defined settings.](images/Labs/image198.png "New application blade")

11. In the Settings blade, select Identity providers.

12. Select Username for Local accounts.

13. Click Save.

    ![On the Settings blade, under Manage, Identity providers is selected. in the Identity provider pane, Username is selected in the Local Accounts drop-down menu.](images/Labs/image199.png "Settings blade")

14. In the Settings blade, select Sign-up policies.

15. Click + Add.

16. Set the policy name to 'signup'.

    ![On the Settings blade, under Policies, Sign-up policies is selected. in the Sign-up policies pane, the Add button is selected. In the Add sign-up policy pane, the Name field is set to signup.](images/Labs/image200.png "Settings blade")

17. Select Identity providers.

18. Select User ID signup.

19. Click OK.

    ![In the Add sign-up policy pane, Identity providers is selected. In the Select identity providers pane, User ID signup is selected.](images/Labs/image201.png "Add sign-up policy pane")

20. Select Sign-up attributes.

21. Select Email Address, Given Name, and Surname.

22. Click OK.

    ![In the Add sign-up policy pane, Sign-up attributes is selected. In the Sign-up attributes pane, the following three attributes are selected: Email Address, Given Name, and Surname.](images/Labs/image202.png "Add sign-up policy pane")

23. Select Application Claims.

24. Select Email Addresses, Given Name, Surname, and User's Object ID.

25. Click OK.

    ![In the Add sign-up policy pane, application claims is selected. In the Select application claims pane, the following application claims are selected: City, Email Addresses, Given Name, Surname, and User\'s Object ID.](images/Labs/image203.png "Add sign-up policy")

26. Select Token, session & SSO config.

27. Select acr under Claim representing policy ID.

28. Click OK.

    ![In the Edit Policy pane, Token, session & SSO config (Default) is selected. In the Token, session & SSO config pane, the Claim representing policy ID toggle button is set to acr, and is circled.](images/Labs/image204.png "Edit Policy pane")

29. Click Create.

30. In the Settings blade, select Sign-in policies.

31. Click + Add.

32. Set the policy name to 'signin'.

    ![In the Settings blade, under Policies, Sign-in policies is selected. In the Sign-in policies pane, the Add button is selected. In the Add Sign-in policy blade, the policy name is set to signin.](images/Labs/image205.png "Settings blade")

33. Select Identity providers.

34. Select Local Account Signin.

35. Click OK.

    ![In the Add sign-in policy pane, Identity providers is selected. In the Select identity providers pane, Local Account Signin is selected.](images/Labs/image206.png "Add sign-in policy pane")

36. Select Application Claims.

37. Select Email Addresses, Given Name, Surname, and User's Object ID.

38. Click OK.

    ![In the Add sign-in policy pane, Application claims is selected. In the Select application claims pane, the following application claims are selected: Email Addresses, Given Name, Surname, and User\'s Object ID.](images/Labs/image207.png "Add sign-in policy pane")

39. Select Token, session & SSO config.

40. Select acr under Claim representing policy ID.

41. Click OK.

    ![In the Edit Policy pane, Token, session & SSO config (Default) is selected. In the Token, session & SSO config pane, the Claim representing policy ID toggle button is set to acr, and is circled.](images/Labs/image208.png "Edit Policy pane")

42. Click Create.

43. In the Settings blade, select Profile editing policies.

44. Click + Add.

45. Set the policy name to 'profileedit'.

    ![In the Profile editing policy pane, the Add button is selected. In the Add profile editing policy pane, the Name field is set to profileedit.](images/Labs/image209.png "Profile editing policy pane")

46. Select Identity providers.

47. Select Local Account Signin.

48. Click OK.

    ![In the Add profile editing pane, Identity providers is selected. In the Select identity providers pane, Local Account Signin is selected.](images/Labs/image210.png "Add profile editing pane")

49. Select Profile attributes.

50. Select Given Name and Surname.

51. Click OK.

    ![In the Add profile editing pane, Profile attributes is selected. In the Select Profile attributes pane, the Given Name and Surname attributes are selected.](images/Labs/image211.png "Add profile editing pane")

52. Select Application Claims.

53. Select Email Addresses, Given Name, Surname, and User's Object ID.

54. Click OK.

    ![In the Add profile editing pane, Application claims is selected. In the Select Application claims pane, the following application claims are selected: Email Addresses, Given Name, Surname, and Users\'s Object ID.](images/Labs/image212.png "Add profile editing pane")

55. Click Create.

56. In the Settings blade, select Applications.

57. Select the created app.

58. Take note of the Application ID as you will need this for the next Task.

    ![In the WebApp section, a callout arrow points to the Application ID copy button.](images/Labs/image213.png "WebApp section")

59. In the Settings blade, select All Policies. You should see three policies and the B2C instance. Take note of the names for these policies with the prefix 'B2C' as these names will be used in the next task.

    ![In the Settings blade, under Policies, All policies is selected. In the All policies pane, three policies display: B2C\_1\_profileedit, B2C\_1\_signin, and B2C\_1\_signup.](images/Labs/image214.png "Settings blade")

60. Your B2C directory is ready for use and after Task 2 is complete, you will be able to exercise it.

### Task 2: Configure the web app Settings

In this task, you will update configuration settings in preparation for Azure AD B2C integration.

You will be guided through the instructions to find the information necessary to populate the configuration settings.

1.  Within Visual Studio Solution Explorer, expand the Web folder, then expand the ContosoEvents.Web project, and open Web.config. You will update these appSettings in this file:

    ```
    <add key="ida:Tenant" value="" />
    <add key="ida:ClientId" value="" />
    <add key="ida:SignUpPolicyId" value="" />
    <add key="ida:SignInPolicyId" value="" />
    <add key="ida:UserProfilePolicyId" value="" />
    ```

Azure Active Directory B2C:

1.  For the ida:Tenant enter the domain of the Azure Active Directory B2C you created such as 'contosoeventsb2cSUFFIX.onmicrosoft.com'.

2.  For the ida:ClientId enter the Application ID generated for your B2C application created in the previous task.

3.  For the ida:SignUpPolicyId enter the name of the sign-up policy you created in the tenant (e.g., B2C\_1\_signup).

4.  For the ida:SignInPolicyId enter the name of the sign in policy you created in the tenant (e.g., B2C\_1\_signin).

5.  For the ida:UserProfilePolicyId enter the name of the profile editing policy you created in the tenant (e.g., B2C\_1\_profileedit).

### Task 3: Add security features to the web application

In this task, you will enable security features that will leverage the configuration you just applied.

1.  From Solution Explorer, expand the website folder ContosoEvents.Web.

2.  Open Startup.cs in the root folder and uncomment the line of code below the TODO item. This will set up the authentication middleware so that users are redirected to authenticate to Azure AD B2C when they access protected resources.

    ```
    //TODO Exercise 10 - Task 3
    ConfigureAuth(app);
    ```

3.  Open FilterConfig.cs from the App\_Start folder, and uncomment the line below the TODO item. This will provide default protection for all routes so that authentication is required unless the route allows anonymous callers.

    ```
    //TODO Exercise 10 - Task 3
    filters.Add(new Policies.PolicyAuthorize { Policy = Startup.SignInPolicyId });
    ```

4.  Open \_Layout.cshtml under Views\\Shared and remove the 3 lines following the TODO item, and uncomment area below it. This will prevent the menu items to be hidden unless the user is authenticated. It will look like this when you complete the change.

    ```
    @\*TODO Exercise 10 - Task 3 \*@
    @if (Request.IsAuthenticated)
    {
        <li><a href="@Url.Action("Index", "Orders")"><span class="glyphicon glyphicon-shopping-cart"></span> Orders</a></li>
        <li><a href="@Url.Action("Index", "LoadTest")"><span class="glyphicon glyphicon-flash"></span> LoadTest</a></li>
        <li><a href="@Url.Action("Status", "LoadTest")"><span class="glyphicon glyphicon-stats"></span> LoadTest Status</a></li>
    }
    ```

5.  Open \_LoginPartial.cshtml under Views\\Shared and uncomment the area below the TODO item. This will enable the menus for user sign in and sign out.

    ```
    @\*TODO Exercise 10 - Task 3 \*@
    @if (Request.IsAuthenticated)
    {
        <text>
            <ul class="nav navbar-nav navbar-right">
                <li>
                    <a id="profile-link"><span class="glyphicon glyphicon-user"></span> @User.Identity.Name</a>
                    <div id="profile-options" class="nav navbar-nav navbar-right">
                        <ul class="profile-links">
                            <li class="profile-link">
                                <a href="@Url.Action("Profile", "Account")"><span class="glyphicon glyphicon-pencil"></span> Edit Profile</a>
                            </li>
                        </ul>
                    </div>
                </li>
                <li>
                    <a href="@Url.Action("SignOut", "Account")"><span class="glyphicon glyphicon-log-out"></span> Sign out</a>
                </li>
            </ul>
        </text>
    }
    else
    {
        <ul class="nav navbar-nav navbar-right">
            <li><a id="signUpLink" href="@Url.Action("SignUp", "Account")"><span class="glyphicon glyphicon-user"></span> Sign up</a></li>
            <li><a id="loginLink" href="@Url.Action("SignIn", "Account")"><span class="glyphicon glyphicon-log-in"></span> Sign in</a></li>
        </ul>
    }
    ```

6.  Compile the application and ensure no errors before the next step.

### Task 4: Running the web app and signing in

In this task, you will test the web application and register yourself as a user to log in to the Azure AD B2C tenant.

1.  Using Solution Explorer in Visual Studio, open the Web folder.

2.  Right click the ContosoEvents.Web project, select Debug, and then Start new instance.

3.  When the application launches you will see the website home page

    ![Screenshot of the Contoso Events website home page.](images/Labs/image215.jpeg "Contoso Events webpage")

4.  Click Sign up and complete a new user registration. After that, you will be returned to the website. Note that your username is shown in the menu bar.

    ![Screenshot of the Contoso Events website home page, with the username and a sign-out button displaying on the menu bar.](images/Labs/image216.jpeg "Contoso Events website")

5.  You will be redirected back to the web app

6.  You can now sign in, sign out, and register users to the website.

**Note**: You can optionally publish this application to Azure and test sign in, sign out continues to work from the deployed URL.

## After the hands-on lab

Duration: 10 minutes

In this exercise, attendees will deprovision any Azure resources that were created in support of the lab. You should follow all steps provided after attending the Hands-on lab.

### Task 1: Delete the resource group

1.  Using the Azure portal, navigate to the Resource group you used throughout this hands-on lab by selecting Resource groups in the left menu.

2.  Search for the name of your research group, and select it from the list.

3.  Select Delete in the command bar, and confirm the deletion by re-typing the Resource group name, and selecting Delete.

4.  In the Management portal, from the left-hand menu, select Active Directory.

    ![Screenshot of the Active Directory icon.](images/Labs/image217.png "Active Directory icon")

5.  Select the tenant to delete, and delete it.
