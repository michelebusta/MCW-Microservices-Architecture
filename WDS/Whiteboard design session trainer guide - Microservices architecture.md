!["Microsoft Cloud Workshops"](images/HeaderPic.png)

Microservices architecture

Whiteboard design session trainer guide

June 2018

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.
© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Trainer information](#trainer-information)
    - [Role of the trainer](#role-of-the-trainer)
    - [Whiteboard design session flow](#whiteboard-design-session-flow)
    - [Before the whiteboard design session: How to prepare](#before-the-whiteboard-design-session-how-to-prepare)
    - [During the whiteboard design session: Tips for an effective whiteboard design session](#during-the-whiteboard-design-session-tips-for-an-effective-whiteboard-design-session)
- [Microservices architecture whiteboard design session student guide](#microservices-architecture-whiteboard-design-session-student-guide)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Step 1: Review the customer case study](#step-1-review-the-customer-case-study)
        - [Customer situation](#customer-situation)
        - [Customer needs](#customer-needs)
        - [Customer objections](#customer-objections)
        - [Infographic for common scenarios](#infographic-for-common-scenarios)
    - [Step 2: Design a proof of concept solution](#step-2-design-a-proof-of-concept-solution)
    - [Step 3: Present the solution](#step-3-present-the-solution)
    - [Additional references](#additional-references)
- [Microservices architecture whiteboard design session trainer guide](#microservices-architecture-whiteboard-design-session-trainer-guide)
    - [Step 1: Review the customer case study](#step-1-review-the-customer-case-study-1)
    - [Step 2: Design a proof of concept solution](#step-2-design-a-proof-of-concept-solution-1)
    - [Step 3: Present the solution](#step-3-present-the-solution-1)
    - [Wrap-up](#wrap-up)
    - [Preferred target audience](#preferred-target-audience)
    - [Preferred solution](#preferred-solution)
    - [Checklist of preferred objection handling](#checklist-of-preferred-objection-handling)
    - [Customer quote (to be read back to the attendees at the end)](#customer-quote-to-be-read-back-to-the-attendees-at-the-end)

<!-- /TOC -->

# Trainer information

Thank you for taking time to support the whiteboard design sessions as a trainer!

## Role of the trainer

An amazing trainer:

-   Creates a safe environment in which learning can take place.

-   Stimulates the participant's thinking.

-   Involves the participant in the learning process.

-   Manages the learning process (on time, on topic, and adjusting to benefit participants).

-   Ensures individual participant accountability.

-   Ties it all together for the participant.

-   Provides insight and experience to the learning process.

-   Effectively leads the whiteboard design session discussion.

-   Monitors quality and appropriateness of participant deliverables.

-   Effectively leads the feedback process.

## Whiteboard design session flow 

Each whiteboard design session uses the following flow:

**Step 1: Review the customer case study (15 minutes)**

Outcome: Analyze your customer's needs

-   Customer's background, situation, needs and technical requirements

-   Current customer infrastructure and architecture

-   Potential issues, objectives and blockers

**Step 2: Design a proof of concept solution (60 minutes)**

Outcome: Prepare to present a solution for your target customer audience

-   Determine your target customer audience

-   Determine customer's business needs to address your solution

-   Design and diagram your solution

-   Prepare to present your solution

**Step 3: Present the solution (30 minutes)**

Outcome: Present solution to your customer

-   Present solution

-   Respond to customer objections

-   Receive feedback

**Wrap-up (15 minutes)**

-   Review preferred solution

## Before the whiteboard design session: How to prepare

Before conducting your first whiteboard design session:

-   Read the Student guide (including the case study) and Trainer guide

-   Become familiar with all key points and activities.

-   Plan the point you want to stress, which questions you want to drive, transitions, and be ready to answer questions.

-   Prior to the whiteboard design session, discuss the case study to pick up more ideas.

-   Make notes for later.

## During the whiteboard design session: Tips for an effective whiteboard design session

**Refer to the Trainer guide** to stay on track and observe the timings.

**Do not expect to memorize every detail** of the whiteboard design session.

When participants are doing activities, you can **look ahead to refresh your memory**.

-   **Adjust activity and whiteboard design session pace** as needed to allow time for presenting, feedback, and sharing.

-   **Add examples, points, and stories** from your own experience. Think about stories you can share that help you make your points clearly and effectively.

-   **Consider creating a "parking lot"** to record issues or questions raised that are outside the scope of the whiteboard design session or can be answered later. Decide how you will address these issues, so you can acknowledge them without being derailed by them.

***Have fun**! Encourage participants to have fun and share!*

**Involve your participants.** Talk and share your knowledge but always involve your participants, even while you are the one speaking.

**Ask questions** and get them to share to fully involve your group in the learning process.

**Ask first**, whenever possible. Before launching into a topic, learn your audience's opinions about it and experiences with it. Asking first enables you to assess their level of knowledge and experience, and leaves them more open to what you are presenting.

**Wait for responses**. If you ask a question such as, "What's your experience with (fill in the blank)?" then wait. Do not be afraid of a little silence. If you leap into the silence, your participants will feel you are not serious about involving them and will become passive. Give participants a chance to think, and if no one answers, patiently ask again. You will usually get a response.

#  Microservices architecture whiteboard design session student guide

## Abstract and learning objectives 

This whiteboard design session is designed to help attendees gain a better understanding of implementing architectures leveraging aspects from microservices and serverless architectures, by helping an online concert ticket vendor survive the first 5 minutes of crushing load. They will handle the client\'s scaling needs through microservices built on top of Service Fabric, and apply smooth updates or roll back failing updates. Finally, students will design an implementation of load testing to optimize the architecture for handling spikes in traffic.

Attendees will learn how to:

-   Implement scale and resiliency with Service Fabric

-   Enable serverless solutions with Azure Functions

-   Control API access with API Management

-   Provide query flexibility with Cosmos DB

## Step 1: Review the customer case study 

**Outcome** 

Analyze your customer’s needs.
Time frame: 15 minutes 
Directions: With all participants in the session, the facilitator/SME presents an overview of the customer case study along with technical tips. 
1.  Meet your table participants and trainer 
2.  Read all of the directions for steps 1–3 in the student guide 
3.  As a table team, review the following customer case study

### Customer situation

Contoso Events is an online service provider for concerts, sporting and other large event ticket sales. The current Contoso Events solution consists of a collection of web sites implemented in ASP.NET with a SQL Server back-end. The solution is currently hosted by Azure on Virtual Machines (VMs).

Contoso Events has experienced consistent growth trends and now has almost 1 million customers. They intend to further grow market share and increase sales by redesigning their current web sites to improve usability and conversion rates, improve responsiveness across devices. In addition, they will create mobile apps for iPhone, Android and Windows Phone devices. Following this, Contoso Events plans to extend its reach through partners by exposing its core event ticket sales and reporting APIs to partners. The plan is to retire and replace the existing solution to serve customers with a better experience -- preserving code where possible, but migrating to a decoupled design with improved business agility.

To meet demand during peak periods they rely on a combination of auto-scaling and manual intervention to scale in advance of expected bursts of traffic -- such as when a popular event has tickets first go on sale. The CIO, Steve Dormer, is concerned about system performance, scalability and associated costs. The company has already been experiencing more frequent, peak traffic periods and this has increased hosting costs. He would like to investigate ways to control exponential increases in hosting and related operational costs as they grow.

The company also has challenges rolling out new features and supporting new events on demand. Features have evolved in situ to where the solution has many interdependencies that increase the risk of regressions across features when changes are introduced. This is particularly challenging with the ticket ordering process as the data model for new events is often slightly different -- which means that supporting new events may have impact on the user experience and UI, the middle tier and storage. Rolling out changes that impact this area while upwards of 50,000 users are actively placing orders, has proven to be a fragile process and requires them to schedule down time to ensure safe deployment.

The CIO has heard about microservices and serverless architectures, and is interested in exploring how Service Fabric and Azure Functions may help the team to be more agile in their development cycle with impact across features, support their goals for continuous delivery, help them with a lean and effective DevOps strategy, and ultimately help with cost control as they grow and support peak periods. The solution must be capable of supporting increased ongoing and peak loads yet also control costs by making better use of available infrastructure. The team also needs tools for monitoring health and more easily managing deployments, rollbacks and recovery in the event of failure.

In addition, the CIO is looking for a solid strategy around securely exposing and managing solution APIs for both internal and partner consumption. For partners, he is looking for a way to support a partner ecosystem that is easy to setup and manage.

According to the CIO, the current system topology handles the following core use cases:

-   **Admin site**: Internal staff use a web application to manage events, customers, users and orders; and for executives to request reports

-   **Consumer site (Web site)**: Customers search events, place ticket orders, return to view their orders and history of events

    -   **Search events**: Customers will search for events they are interested in, from the event catalog available via the web site. The event catalog is managed by an internal administrative site

    -   **Event details**: Customers may visit a specific event page to order tickets, from search results or a direct link from an email campaign or referral

    -   **Ticket orders**: Customers select tickets to order from the event details page and are taken to an order page to complete the ticket order

        -   This path receives the most traffic as customers compete to get tickets to a popular event that has just gone on sale

        -   This is currently the focus of peak load and scale concerns

        -   The CIO believes they should implement an asynchronous ordering process with email notifications - a pattern many busy ecommerce sites follow whereby the credit card is validated but the actual order is not confirmed until processed from a queue

    -   **Payment**: Credit card payments are handled via a third-party payment processing service

-   **Storage**: The event catalog, customer accounts, users and orders are currently stored in a relational SQL Server database

    -   The CIO feels that a solution that reduces the overhead of state management and keeps the data closer to the compute functionality for faster retrieval will help them with future scale 

### Customer needs

1.  Event tickets can be ordered from multiple channels: the web site, new mobile applications, and third-party site and applications via available APIs.

2.  Customers must be registered / logged in to place orders, so that they can login and find their orders, and for reporting and analytics purposes.

3.  Internal staff will manage orders and view reports from the Admin site.

4.  The ability to rapidly release new features that may involve UI, business logic and data model changes by reducing dependency across features.

5.  Reduced overall downtime caused by system updates. Rollouts must be possible without scheduled downtime. Rollbacks must be possible in the event of failure.

6.  The solution must be able to handle increased system load for ticket purchasing, including higher peak periods without excessive increases in management overhead and cost.

7.  Operations management overhead must be improved through better system monitoring, visibility, self-healing services and auto-scale features.

8.  The customer has decided to migrate from SQL Server to Cosmos DB for a more flexible schema and increased scalability across features.

9.  A solution is required for securing and managing APIs used internally and by external partners, with the ability to easily publish APIs, version APIs, onboard consumers, control policy, monitor and audit usage.

10. The solution currently processes credit cards with a third-party payment-processing provider. This aspect of the solution will remain the same and requires integration into the new design.

### Customer objections 

1.  While we are interested in the microservices approach, we are still comparing Service Fabric with PaaS features such as App Services and SQL DB. How mature is Service Fabric by comparison?

2.  Microservices architectures are completely new to the Contoso Events team. If we were to go forward with Service Fabric, we would like to understand what skills the team can carry forward, and how much of a learning curve exists.

3.  We would like to understand if stateful services or stateful actors will help us with ticket ordering throughput, workflow and state management, and easier rollouts of changes to this process.

4.  We are not clear how and where to incorporate stateful services and actors alongside other storage such as Cosmos DB. We need the ability to support robust ad-hoc queries against our system data such as events, customers, orders and related metrics -- but would like to take advantage of the performance and reliability of Service Fabric stateful options as well.

5.  Could we consider Azure Functions as an alternative back end implementation for our APIs?

1.  We would like to understand more about the benefits of serverless architectures---in Azure does it mean only using Azure Functions or is there more to it?

### Infographic for common scenarios

![This diagram represents a Service Fabric overview for the scenario. At the top of the diagram is a Microservices ribbon. Below that, a Service Fabric ribbon has three arrows that point to Azure (Windows Server, Linux), Private clouds (Windows Server, Linux), and Hosted Clouds (Windows Server, Linux). The Service Fabric ribbon includes several requirements for the service fabric such as (but not limited to) high availability, self-healing, fast startup and shutdown, low latency, and automated rollback.](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image2.png "Common scenarios diagram")

![This diagram presents a comparison of monolithic versus microservices approaches, as described in the text following this diagram.](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image3.png "Monolithic application vs. Microservices application approaches")

***Comparison between Monolithic and Microservices Approaches***

A monolithic application contains domain-specific functionality and is normally divided by functional layers, such as web, business, and data (1). You scale a monolithic app by cloning it on multiple servers/virtual machines/containers (2).

A microservice application separates functionality into separate smaller services (3). The microservices approach scales out by deploying each service independently, creating instances of these services across servers/virtual machines/containers (4).

Reference: [*https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-overview-microservices*](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-overview-microservices)

![This diagram presents a comparison of State storage in monolithic versus microservices approaches, as described in the text following this graphic.](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image4.png "State in Monolithic vs. State in Microservices approaches")

***Storage State between Monolithic and Microservices Approaches***

The monolithic approach on the left has a single database and tiers of specific technologies. The microservices approach on the right has a graph of interconnected microservices where state is typically scoped to the microservice and various approaches are used to manage state.

Source: *<https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-overview-microservices>*

## Step 2: Design a proof of concept solution

**Outcome** 
Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format. 

Time frame: 60 minutes

**Business needs**

Directions: With all participants at your table, answer the following questions and list the answers on a flip chart. 
1.  Who should you present this solution to? Who is your target customer audience? Who are the decision makers? 
2.  What customer business needs do you need to address with your solution?

**Design** 
Directions: With all participants at your table, respond to the following questions on a flip chart.

*High-level architecture*

1.  Without getting into the details (the following sections will address the particular details), diagram your initial vision for handling the top-level requirements for web sites, mobile applications, third party applications, access to APIs, compute and storage.

2.  Based on the customer situation, what core services would you propose as part of the new microservices architecture? What state, if any, would those services hold? Illustrate with a diagram.

*Scalability of ticket orders*

1.  Illustrate in more detail the Service Fabric services and components participating in a ticket order request.

2.  Describe the scalability features of this design, including any partitioning strategies that are applicable.

3.  Describe the resiliency of this use case. How can you create an asynchronous ticket order request and guarantee processing? Are there any potential points of failure? How will you address those?

4.  Describe how you will enable external clients to reach stateless HTTP services exposed from the Azure load balancer.

*Improving DevOps workflows*

1.  How would you structure the Visual Studio solution so that developers can run, debug, and publish the entire solution but also be able to publish and upgrade individual microservices (could be one or more service grouped together)?

2.  Describe to the customer how they can upgrade services in situ and preserve state; handle rollback and roll forward; and service self-healing features.

3.  Explain how the Service Fabric cluster handles auto-scaling. How does Service Fabric help the customer to make better utilization of their compute resources?

4.  How would you recommend the customer plan for high availability (HA) in this solution?

5.  Explain to the customer how Service Fabric can help the customer have visibility into overall solution health.

6.  How can you update cluster settings after the fact? What kind of settings might you want to update?

7.  How will you keep your cluster up to date with the latest Service Fabric SDK?

*Controlling access to APIs*

1.  Describe how API Management may be useful to protect access to APIs exposed by the solution. How would you identify the user and the API consumer or application?

2.  How will you protect Service Fabric APIs from outside callers exposed through API Management?

**Prepare**

Directions: With all participants at your table: 

1.  Identify any customer needs that are not addressed with the proposed solution. 
2.  Identify the benefits of your solution. 
3.  Determine how you will respond to the customer’s objections. 

Prepare a 15-minute chalk-talk style presentation to the customer. 

## Step 3: Present the solution

**Outcome**

Present a solution to the target customer audience in a 15-minute chalk-talk format.

Time frame: 30 minutes

**Presentation** 

Directions:
1.  Pair with another table.
2.  One table is the Microsoft team and the other table is the customer.
3.  The Microsoft team presents their proposed solution to the customer.
4.  The customer makes one of the objections from the list of objections.
5.  The Microsoft team responds to the objection.
6.  The customer team gives feedback to the Microsoft team. 
7.  Tables switch roles and repeat Steps 2–6.

##  Additional references
|    |            |       
|----------|:-------------:|
| **Description** | **Links** |
| Service Fabric - Overview of load balancing and addressing services | <https://azure.microsoft.com/en-us/documentation/articles/service-fabric-connect-and-communicate-with-services/> |
| Service Fabric - HA Configuration | <https://alexandrebrisebois.wordpress.com/2016/05/31/deploy-a-geo-ha-service-fabric-cluster-on-azure/> |
| Azure Functions | <https://azure.microsoft.com/en-us/services/functions/> |
| Cosmos DB | <https://azure.microsoft.com/en-us/documentation/articles/documentdb-introduction/> |
| Azure AD | <https://azure.microsoft.com/en-us/services/active-directory-b2c/> |


# Microservices architecture whiteboard design session trainer guide

## Step 1: Review the customer case study

-   Check in with your table participants to introduce yourself as the trainer.

-   Ask, "What questions do you have about the customer case study?"

-   Briefly review the steps and time frames of the whiteboard design session.

-   Ready, set, go! Let the table participants begin.

## Step 2: Design a proof of concept solution

-   Check in with your tables to ensure that they are transitioning from step to step on time.

-   Provide some feedback on their responses to the business needs and design.

    -   Try asking questions first that will lead the participants to discover the answers on their own.

-   Provide feedback for their responses to the customer's objections.

    -   Try asking questions first that will lead the participants to discover the answers on their own.

## Step 3: Present the solution

-   Determine which table will be paired with your table before Step 3 begins.

-   For the first round, assign one table as the Microsoft team and the other table as the customer.

-   Have the Microsoft team present their solution to the customer team.

    -   Have the customer team provide one objection for the Microsoft team to respond to.

    -   The presentation and objections should be no longer than 10 minutes.

-   Have participants on the customer team give feedback to the Microsoft team.

    -   The feedback should be no longer than 5 minutes.

    -   If needed, the trainer may also provide feedback.

## Wrap-up

-   Have the table participants reconvene with the larger session group to hear a SME share the following preferred solution.

##  Preferred target audience

Steve Dormer, CIO at Contoso Events

The primary audience is the technical strategic decision-maker with influential solution architects, or lead technical personnel in development or operations. For this example, this could include the CIO and his core team. Usually we talk to the key architects, developers and infrastructure managers who report to the CIO, or to key solution sponsors or those that represent the business unit IT or developers that report to those sponsors.

## Preferred solution

After evaluating the benefits of Service Fabric, with the team at Microsoft, Contoso Events decided to move toward a microservices design with Service Fabric including the following technologies:

-   Service Fabric as the core microservices platform

-   API Management for securing and managing consumption of APIs used by internal and third-party applications

-   Azure AD B2C for consumer authentication and access control to API Management endpoints

-   Cosmos DB for aggregate data and ad-hoc queries

-   Azure Functions to handle asynchronous updates to Cosmos DB

*High-level architecture*

1.  Without getting into the details (the following sections will address the particular details), diagram your initial vision for handling the top-level requirements for web sites, mobile applications, third party applications, access to APIs, compute and storage.
    ![The preferred solution is described in the text following this diagram.](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image5.png "Preferred solution diagram")

    Summary of technologies in the topology:

    -   Contoso Events will have both web and mobile applications that consume the back-end APIs for the solution.

    -   Users will authenticate to applications using tokens issued by Azure AD B2C.

    -   The API Management layer will act as a gateway to all HTTP Web APIs exposed by the solution. API Management will be configured to authorize tokens issued by trusted Azure B2C tenants and potentially additional token issuers for third parties in future.

    -   Requests to HTTP Web APIs at the front end will go through Azure Load Balancer and distribute across the available Service Fabric nodes in the cluster.

    -   Business functionality will be implemented with stateful services and actors (microservices). Web APIs call to those microservices.

    -   Stateful services will sync their data back to the Cosmos DB instance for ad-hoc queries. They will write the job to an Azure queue.

    -   An Azure Function will handle processing the queue and updating the TicketOrders and related collections in Cosmos DB according to business rules.

2.  Based on the customer situation, what core services would you propose as part of the new microservices architecture? What state, if any, would those services hold? Illustrate with a diagram.

    ![Diagram of a high-level architecture of the core services that compose the new microservices architecture, as well as the state they hold. The diagram is made up of external services, microservices and state, and externalized state. External services is payment processing, external state is Orders/Events/CustomerAccounts, and Microservices and state is: Event Catalog, Customer Accounts, and Ticket Orders services, Queue, Ticket Actor Service, Ticket, Email Service, and Payment Service. In the diagram, Two arrows labeled \"Read from Externalized state\" point from Externalized state to Customer Accounts Services and Event Catalog Service. The remaining microservices and state have an arrow labeled \"Esternalize state for aggregation\" pointing back to Externalized state.](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image6.png "High-level architecture diagram")

    The Ticket Orders Service will take advantage of reliable queues provided by Service Fabric to persist requests. The Ticket Actor Service processes orders in the queue, and represents a single instance of an order and its processing workflow and state. When an order is processed, the state is externalized for shared read only services to support aggregation across other data and to optimize reads.

*Scalability of ticket orders*

1.  Illustrate in more detail the Service Fabric services and components participating in a ticket ordering request.
    
    ![This Scalability of Ticket Orders diagram illustrates in more detail the Service Fabric services and components participating in a ticket ordering request. The diagram is discussed in slightly more detail in the text following this diagram. However, at this time, we are unable to capture all of the information in the diagram. Future versions of this course should address this.](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image7.png "Scalability of Ticket Orders diagram")

    Summary of technologies in the topology:

    -   Contoso Events will have a consumer web site and mobile applications, plus allow third parties to build applications that place ticket orders.

    -   The UI will pre-flight the credit card charge from the order page and supply the resulting token to the back-end processing of the order.

    -   All ticket order requests will call the Ticket Order API via the API Management layer.

    -   The stateless Ticket Order API will queue the request to process an order, passing the token for credit card validation, order details, and any user details required to complete the request asynchronously.

    -   The Ticket Order Queue stateful service will process requests by instantiating a Ticket Order Actor to handle the processing workflow. This actor is responsible for charging the credit card, finalizing the order, and notifying the customer to give them access to their order.

    -   The actor will also write to a Ticket Order Sync queue to offload sending order data to Cosmos DB for reports, analytics and related ad-hoc queries.

    -   An Azure Function will read from the queue and handle updates to Cosmos DB. To ensure the latest data is always persisted, the function will retrieve the latest order state and update the Cosmos DB Ticket Orders collection.

    -   Web APIs will expose data from Cosmos DB for additional ad-hoc queries against ticket orders.

2.  Describe the scalability features of this design, including any partitioning strategies that are applicable.
    
    When an event is published, and a flurry of customers arrive to the site to order tickets, a flood of requests (potentially in the 100,000s) will be sent from the web front end or various other client channels through the API Management gateway. API Management Premium features support scaling and multi-region topologies to meet demand and high availability requirements.

    The stateless Ticket Order API offloads valid requests to the stateful Ticket Order Queue. This queue is partitioned by instance count (from 1 to n in the diagram below) and requests are randomly distributed by Service Fabric across partitions. Choosing an instance count (partition size) up front is important as today it requires a full redeploy to change this, however with a queue there are other rollover strategies you could employ to work around this. This removes the bottleneck of writes to the queue as it can distribute this load across all partitions in parallel.
    
    ![In this Ticket order Scalability diagram, on the left, an arrow labeled Partition Key equals Random, points right, to a vertical bar labeled 64-bit Addressable Range. To the right of this bar are three gray boxes labeled Partition 1, Partition 2, and Partition n. Each of these boxes has a blue box within labeled \"Ticket Order Queue Service.\" The three gray boxes also have a Reliable Queue section, with differing Order numbers.. ](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image8.png "Ticket order Scalability diagram")

    The stateful Ticket Order Actor handles processing from this queue and, given the number of parallel orders, helps the solution to scale by maintaining the state of any number of parallel orders. The actor is able to negotiate payment, send notifications, persist its own state at each stage of processing, and send the final order data to the order synchronization queue on the back end. The actor is partitioned by order id, which allows for very fine-grained distribution of state, per order, across the cluster. Any number of concurrent orders may be concurrently available to active requests for fast retrieval. Millions of these can exist and distribute across the cluster and inactive actors are evicted from memory automatically to conserve resources.

    ![The Stateful Ticket Order Actor diagram has three partitions/actors: Partition 1, with Actor 1, Partition 2 with Actor 2, and Partition n with Actor n. Three Order IDs have arrows pointing through a 64-bit Addressable Range bar, to the Partition/Actors.](images/Whiteboarddesignsessiontrainerguide-Microservicesarchitectureimages/media/image9.png "Stateful Ticket Order, Actor diagram")

3.  Describe the resiliency of this use case. How can you create an asynchronous ticket order request and guarantee processing? Are there any potential points of failure? How will you address those?

    Web applications will not report success unless the Payment Processing service returns a token for the request, and the ticket order reaches the Ticket Order Queue.

    All Web API calls go through API Management, which can be scaled within a region, or deployed to multiple regions.

    The queue does not report successful receipt of the message until a quorum is reached across the queue partition replicas (more on this in Customer Objections section).

    The Ticket Order Actor does not remove the order from the queue unless it can successfully process payment, send notifications, and save the order. In addition, it must confirm successfully sending the order to the Order Sync Queue. Saving the order to the actor state requires a quorum across replicas.

    The Azure Function that processes the Order Sync Queue will remove messages from the queue if processing is successful -- which means successfully writing to the Cosmos DB collection. Any messages that can't be processed are moved to a poison queue. Those messages can be retried, or code can be written to pull from the poison queue for special processing, for example to move them to a data store for analysis of issues.

    For additional visibility into queue / function processing errors it is good practice to monitor queue sizes that pass a reasonable threshold of standard solution behavior.

4.  Describe how you will enable external clients to reach stateless HTTP services exposed from the Azure load balancer.

    When you publish a stateless HTTP service the Service Fabric provides a relative URL to the service according to the configuration you supply. This way, multiple HTTP services can be deployed to a single node and still be uniquely addressable at port 80 or 443. In the case of this solution, the API Management layer will consume those endpoints and forward requests.

*Improving DevOps Workflows*

1.  How would you structure the Visual Studio solution so that developers can run, debug and publish the entire solution but also be able to publish and upgrade individual microservices (could be one or more service grouped together)?

    A typical service fabric solution has a top-level application that can be used to publish all services associated with it. To publish the entire suite of services in a solution you can add all services to this top-level application, however this is not always ideal for distributed teams and certainly not appropriate for upgrading individual services.

    You can create additional Service Fabric applications in the solution that isolate specific services for deployment. For example, if there are 6 services in the solution, you may have 7 applications: 1 that deploys all services during development and test of the entire solution; and 1 for each individual service so that developers or DevOps workflows can update a single service.

2.  Describe to the customer how they can upgrade services in situ and preserve state; handle rollback and roll forward; and service self-healing features.

    When an application is deployed, you can choose to "upgrade" the application. This preserves any state associated with stateful services if applicable. This will retire previous versions once they complete requests in process, while sending new requests to the new version of the service.

    If during the upgrade process there is a problem with the services being deployed, the upgrade is rolled back, and the previous version of the services continue to operate.

    If the Service Fabric runtime detects any service instances that are no longer operational, new instances of the service are initialized to maintain the required minimum instances for the service.

3.  Explain how the Service Fabric cluster handles auto-scaling. How does Service Fabric help the customer to make better utilization of their compute resources?

    Currently, performance counters emitted by the Service Fabric cluster drive auto-scaling. You can set up a base requirement for minimum nodes in the cluster (based on reliability level chosen) and configure auto-scale rules to scale up or down within that range. As the available nodes in the cluster become fully utilized, additional nodes are created (typically via an auto scale trigger for the scale set). The customer should continue to monitor trends and initiate scaling prior to the auto-scale rule taking effect to ensure scalability for known trends such as the launch of a very popular event.

    What Service Fabric offers is better utilization of each node in the cluster prior to demanding a scale action that adds nodes and cost. This boosts your ROI in particular as the number of nodes in the cluster increases. At the same time, the naming service removes the complexity of this utilization with built-in service discovery.

    Dynamic discovery, or addressing, of service endpoints is a feature that enables the Service Fabric runtime to utilize resources as it sees fit. As such, when you deploy services, they are distributed across the available nodes in the Service Fabric cluster -- including replicas for stateful services. Clients use the naming service to reach the correct service instance and related state, according to partitioning strategies -- and the location of the service instance and related addressing is transparent. Service Fabric will ensure that services are distributed across nodes according to any placement constraints, while ensuring that nodes are densely populated. Greater density helps to reduce scaling requirements and related costs.

4.  How would you plan for high availability (HA) for Service Fabric in this solution?

    Service Fabric inherently provides high availability within the cluster region.

    You achieve multi-region high availability for disaster recovery scenarios by using the backup/restore capability of stateful services. You can also create real time high availability across regions by configuring Traffic Manager to route traffic to both regions. In this case, any stateful services should be capable of reloading their latest state from external storage if not present in the region's cluster.

5.  Explain to the customer how Service Fabric can help the customer have visibility into overall solution health.

    Azure Service Fabric introduces a health model that provides rich, flexible and extensible health evaluation and reporting. Service Fabric components use this health model to report their current state and the same mechanism can be used to report application health state. When your services encounter problems, your ability to respond to and fix incidents and outages depends on your ability to detect the issues quickly. If you report problems and failures to the Azure Service Fabric health manager from your service code, you can use standard health monitoring tools that Service Fabric provides to check the health status.

    For example, you can report configuration errors that would prevent the solution from reliable operation, and report these as exceptions to the Service Fabric. Exceptions that are detected while the Service Fabric tries to perform upgrades will trigger a rollback operation to avoid introducing this failure into the system.

6.  How can you update cluster settings after the fact? What kind of settings might you want to update?

    A ServiceFabric cluster is essentially a collection of VMs behind a load balancer, with ServiceFabric tools and agents predeployed. If you want to update the physical characteristics of the underlying VMs or update aspects of the topology, you can update the ARM template representing the cluster that is currently provisioned, and reapply it. This update can be applied directly in the Azure portal or through your automation procedures if you have those in place.

    Examples of updates you can execute with ARM include:

    -   Adding new node types for additional scale tiers.

    -   Adding memory or CPU capacity to a specific type of node.

    -   Modifying load balancer settings, opening ports, and adding or removing probes (these changes can also be applied directly through the Azure Portal without ARM).

        Once provisioned, you cannot change the security of the ServiceFabric cluster, so it is important to set the cluster up as a secure cluster, from the beginning. It may change in future.

        Other ServiceFabric operations such as deploying applications, upgrading applications, describing placement constraints, and scaling instances, can be done via PowerShell commands or through the FabClient.

7.  How will you keep your cluster up to date with the latest Service Fabric SDK?

    Servicer Fabric can run on any data center including Azure, AWS, or on-premises.

    On Azure, Microsoft updates the ServiceFabric components and runtime SDK automatically when a new version is released, unless the cluster is in an unhealthy state. All other environments require you to install these component updates manually.

*Controlling access to APIs*

1.  Describe how API Management may be useful to control access to APIs exposed by the solution.

    API management is sometimes thought of as a methodology only employed in the past for third party consumers and related usage monitoring and throttling. However, the value of API Management is becoming more mainstream for general purpose APIs and third-party APIs providing consistency with security features, API documentation, monitoring, audit, and logging, and as needed for consumer management and throttling.

    Initially the solution will benefit from API publishing tools and swagger, API security policy and token validation and internal applications that can be created as pre-assigned API consumers without a sophisticated setup.

    Eventually, as the partner ecosystem is built out, the customer will want to leverage many more API Management features such as API consumer onboarding and policy management, API consumer self-service features via the consumer portal, API documentation, incident reporting tools, API consumer throttling and usage metrics reporting.

2.  How would you identify the user and the API consumer or application?

    APIs can be secured by passing, a consumer key for identifying the calling application (be it internal or third party) or a token, issued for the user (e.g., by a trusted identity provider).

    The top-level Web APIs will be published through Azure API Management. This provides a security layer that can leverage Azure AD to authorize callers but also enforce consumer keys.

    All consumers, including internal applications, will be issued a consumer key.

    The solution will employ Azure Active Directory B2C for customer login, and will use the same mechanism for API security. API Management policy will be set up to authorize access only to callers with a signed Azure AD token (JWT) issued by the solution tenant, for consumer applications. Corporate applications may introduce another Azure AD tenant that syncs with their internal AD, for example.

## Checklist of preferred objection handling

*While we are interested in the microservices approach, we are still comparing Service Fabric with PaaS features such as App Services and SQL DB. How mature is Service Fabric by comparison?*

Service Fabric has been battle tested for many years prior to becoming generally available. In fact, Service Fabric is the underlying foundation for Azure's own SQL DB and Cosmos DB services among other high traffic applications such as the very popular Halo game.

As for choosing between Service Fabric and App Services or SQL DB the benefits of the former include:

-   The ability to deploy individual application services without concern over the target infrastructure -- let Service Fabric decide the target nodes appropriate for each tier and service type.

-   Simplified approach to managing data persistence with stateful services.

-   Microservices design from the ground up on a platform that is specifically designed for that purpose -- with the ability to scale.

-   The capability to deploy Service Fabric clusters in Azure and on-premises, across both Windows and Linux hosts.

*Microservices concepts are completely new to the Contoso Events team. If we were to go forward with Service Fabric as our microservices platform, we would like to understand what skills the team can carry forward, and how much of a learning curve exists.*

Service Fabric is a natural transition for .NET developers in many respects:

-   They can continue to use Visual Studio for development, debugging and publishing applications

-   They can continue to develop ASP.NET and Web API applications and can leverage Service Fabric project templates to kick-start their understanding of the specifics of Service Fabric services.

-   The programming model for services is familiar in that it leverages features of existing .NET technologies and related concepts such as WCF endpoints (simplified), channels and serialization.

-   Working with stateful services is also familiar in the sense that state is defined via objects (POCO) and serialized as part of the service implementation. Saving and retrieving state is just a few lines of code and the robustness, availability and reliability of that state is a feature of the stateful service.

*We'd like to understand if stateful services or stateful actors will help us with ticket ordering throughput, workflow and state management, and easier rollouts of changes to this process.*

Stateful services are very powerful as they make it very easy for developers to define state for any service by using familiar serializable types (POCO) and a few simple instructions to handle saving and retrieving state when the service is accessed. This allows for scenarios where compute and data are collocated reducing the latency of accessing this data.

This simplicity is backed by robust and reliable storage. When data (state) is saved by the service, it is not confirmed (committed) unless a quorum is reached -- for example at least 3 replicas have successfully persisted the data. Furthermore, if a replica becomes unavailable, a new replica is automatically created to maintain the required number of replicas for reliable storage.

By using the stateful actor, not only is the persistence of the actual ticket order handled by the Service Fabric at scale, but the actor can be wholly responsible for the workflow required to complete the order including:

-   Completing the payment processing purchase with token

-   Securing the ticket based on availability

-   Notifying the user of the result, success or failure

-   Preserving the state of the workflow as it progresses

When updates to this actor are required, the existing state is preserved, any active instances can continue completing their work, and the new actor functionality or state requirements can be rolled out safely by Service Fabric across the nodes in the cluster, eventually retiring the previous version.

While this solution may not be a typical example of an "Actor Model" in the parallel computing sense, it makes sense to leverage Service Fabric actors for a few reasons. The very nature of the ticket order, its internal workflow and state machine, and the granularity with which the partition is defined (by order) could not as easily be achieved with a traditional stateful service.

*We are not clear how and where to incorporate stateful services and actors alongside other storage such as Cosmos DB. We need the ability to support robust ad-hoc queries against our system data such as events, customers, orders and related metrics -- but would like to take advantage of the performance and reliability of Service Fabric stateful options as well.*

Stateful services make it easy to save and retrieve state, and distribute that state for higher availability by using a partitioning strategy. Each partition has its own replica set for reliability. While you can retrieve data from all partitions and potentially use this for aggregation and metrics -- the recommended way to support alternate query patterns is to store the data to an externally accessible location.

Most Service Fabric solutions can benefit from offloading stateful service state to an external store. This supports not only alternate query patterns and ad-hoc querying from the solution, but also analytics and disaster recovery. In this solution we are employing Azure Function to de-couple the Service Fabric app from its external storage options by providing server-less code that can take input from an Azure queue and send the latest state of the data to Document DB.

*Could we consider Azure Functions as an alternative back end implementation for our APIs?*

While it is possible to create Functions that run behind API Management endpoints, they are best employed for decoupled, asynchronous background operations that can be run at scale without concern for the specific server running that operation.

In this solution, Azure Functions allowed for decoupling the location of the external storage location of orders, without the need to update Service Fabric configurations on change. It also allowed for a separate scale-out tier for that work.

In a solution such as a mobile application back end, functions could be useful if they don't need to comingle with other solutions aspects -- such as acting as their own microservice with a targeted purpose.

*We would like to understand more about the benefits of Serverless architectures---in Azure does this mean only using Azure Functions or is there more to it?*

A Serverless Architecture, as the name implies, aims to provide a solution architecture where concern for individual servers is minimized. While the term "Serverless" has varying interpretations, it typically includes characteristics such as the extensive use of ephemeral services, a focus entirely on scaling the capabilities that support the business logic, the processing capability should be ephemeral (e.g, it can be started nearly instantaneously without preprovisioning on your part), the capability is scaled transparently at a very granular level (e.g. scaling occurs on a per request or function invocation basis and not on an all up server load basis), and the cost is typically associated with time spent supporting business logic computation and not on the time server resources are available to handle requests. In Azure, Functions is a prime component of a Serverless architecture, but not the only service that may be utilized in one. Other Azure Services that, by this definition, can be composed into a Serverless architecture include: Azure Storage Blobs, Tables and Queues, Azure Data Lake Store, API Management, CDN, Media Services, Notification Hubs, IoT Hub, and Service Bus.

## Customer quote (to be read back to the attendees at the end)

"With Service Fabric we are able to move to microservices architecture without the DevOps headache. Service Fabric provides so much to support deployment, compute utilization, health monitoring and recovery -- we could leverage the same team while increasing the size of our solution and feature set!"

Steve Dormer, CIO at Contoso Events