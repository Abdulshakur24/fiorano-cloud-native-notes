# Fiorano Cloud Native Integration Guideline

# Table of Contents

## [1. Introduction to Cloud-Native Integration with Fiorano](#module-1-introduction-to-cloud-native-integration-with-fiorano)

- [**1.1**: Understanding the Need for Fiorano in Enterprise Integration](#11-the-need-for-fiorano-in-enterprise-integration)
- [**1.2**: Fiorano Product Architecture Overview](#12-fiorano-product-architecture-overview)
- [**1.3**: Deep Dive into Event Processes and Low-Level Architecture](#13-deep-dive-into-event-processes-and-low-level-architecture)
- [**1.4**: Deployment Topologies in Fiorano](#14-deployment-topologies-in-fiorano)
- [**1.5**: Fiorano API Management Architecture](#15-fiorano-api-management-architecture)

---

## [2. Data Transformation](#module-2-data-transformation)

- [**2.1**: Exposing a REST Service](#21-exposing-a-rest-service)
- [**2.2**: Connecting to a Database](#22-connecting-to-a-database)
- [**2.3**: Exposing a REST Service Integrated with a Database](#23-exposing-a-rest-service-integrated-with-a-database)
- [**2.4**: Ways to Debug Fiorano Applications](#24-ways-to-debug-fiorano-applications)
- [**2.5**: Application Context and Its Usage](#25-application-context-and-its-usage)
- [**2.6**: Usage of Property/Properties in Fiorano](#26-usage-of-propertyproperties-in-fiorano)
- [**2.7**: Data Transformation (JSON to XML)](#27-data-transformation-json-to-xml)
- [**2.8**: Data Transformation (XML to JSON)](#28-data-transformation-xml-to-json)
- [**2.9**: Data Transformation (Text to XML)](#29-data-transformation-text-to-xml)
- [**2.10**: Data Transformation (XML to Text)](#210-data-transformation-xml-to-text)
- [**2.11**: Data Modification (JSON Payloads)](#211-data-modification-json-payloads)
- [**2.12**: Data Modification (XML Payloads)](#212-data-modification-xml-payloads)

---

## [3. Database, Web Services, and File Handling](#module-3-database-web-services-and-file-handling)

- [**3.1**: Funclets and Custom Funclets (Creation and Usage)](#31-funclets-and-custom-funclets-creation-and-usage)
- [**3.2**: Integrating with a Database using Stored Procedures](#32-integrating-with-a-database-using-stored-procedures)
- [**3.3**: Consuming Web Services (SOAP)](#33-consuming-web-services-soap)
- [**3.4**: Consuming REST Services (HTTP/HTTPS)](#34-consuming-rest-services-httphttps)
- [**3.5**: Consuming Backend Services Using HTTP Adapter](#35-consuming-backend-services-using-http-adapter)
- [**3.6**: Integrating with Files using FileReader](#36-integrating-with-files-using-filereader)
- [**3.7**: Integrating with Files using FileWriter Part 1](#37-integrating-with-files-using-filewriter-part-1)
- [**3.8**: Integrating with Files using FileWriter Part 2](#38-integrating-with-files-using-filewriter-part-2)

---

## [4. Selectors and Error Handling](#module-4-selectors-and-error-handling)

- [**4.1 Selectors Part 1**: Message Body XPath](#41-selectors-part-1-message-body-xpath)
- [**4.2 Selectors Part 2**: Application Context XPath](#42-selectors-part-2-application-context-xpath)
- [**4.3 Selectors Part 3**: JMS Property Selectors](#43-selectors-part-3-jms-property-selectors)
- [**4.4**: Error Handling in Fiorano](#44-error-handling-in-fiorano)

---

## [5. Email and File Transfer Protocols](#module-5-email-and-file-transfer-protocols)

- [**5.1**: Sending Emails using SMTP](#51-sending-emails-using-smtp)
- [**5.2**: Receiving Emails using POP3](#52-receiving-emails-using-pop3)
- [**5.3**: Receiving Emails using IMAP](#53-receiving-emails-using-imap)
- [**5.4**: FTPGet (Integrating with File Servers) Part 1](#54-ftpget-integrating-with-file-servers-part-1)
- [**5.5**: FTPGet (Integrating with File Servers) Part 2](#55-ftpget-integrating-with-file-servers-part-2)

---

## [6. Flow Adapters](#module-6-flow-adapters)

- [**6.1 Adapter Flow Part 1**: Load Distribution](#61-adapter-flow-part-1-load-distribution)
- [**6.2 Adapter Flow Part 2**: Implementing Cache](#62-adapter-flow-part-2-implementing-cache)
- [**6.3 Adapter Flow Part 3**: Message Splitter using XMLSplitter](#63-adapter-flow-part-3-message-splitter-using-xmlsplitter)
- [**6.4 Adapter Flow Part 4**: Aggregation Techniques](#64-adapter-flow-part-4-aggregation-techniques)
- [**6.5 Adapter Flow Part 5**: Content-Based Routing with JsonCBR](#65-adapter-flow-part-5-content-based-routing-with-jsoncbr)
- [**6.6 Adapter Flow Part 6**: Schema Validation using XMLVerification](#66-adapter-flow-part-6-schema-validation-using-xmlverification)
- [**6.7 Adapter Flow Part 7**: Using Sleep Component in Fiorano](#67-adapter-flow-part-7-using-sleep-component-in-fiorano)

---

## [7. Advanced Data Transformation](#module-7-advanced-data-transformation)

- [**7.1**: Advanced Data Transformation (OFS to XML)](#71-advanced-data-transformation-ofs-to-xml)
- [**7.2**: Advanced Data Transformation (XML to OFS)](#72-advanced-data-transformation-xml-to-ofs)
- [**7.3**: Advanced Data Transformation (XML to PDF)](#73-advanced-data-transformation-xml-to-pdf)
- [**7.4**: Integrating with JMS Adapters (JMSIn and JMSOut)](#74-integrating-with-jms-adapters-jmsin-and-jmsout)

---

## [8. Configurations, Extended Services, and Control Plane Dashboard](#module-8-configurations-extended-services-and-control-plane-dashboard)

- [**8.1 Named Configurations Part 1**: Message Filters](#81-named-configurations-part-1-message-filters)
- [**8.2 Named Configurations Part 2**: Route Transformations](#82-named-configurations-part-2-route-transformations)
- [**8.3**: Retry Mechanism for Reliability](#83-retry-mechanism-for-reliability)
- [**8.4**: Exporting and Importing Event Processes](#84-exporting-and-importing-event-processes)
- [**8.5**: Extended Services in Fiorano](#85-extended-services-in-fiorano)
- [**8.6 FES Dashboard Part 1**: Runtime Management](#86-fes-dashboard-part-1-runtime-management)
- [**8.7 FES Dashboard Part 2**: Document Tracking](#87-fes-dashboard-part-2-document-tracking)
- [**8.8**: Installing and Uninstalling Patches](#88-installing-and-uninstalling-patches)

---

## [9. API Management, Security, Debugging, and Analytics](#module-9-api-management-security-debugging-and-analytics)

- [**9.1**: API Management - Creating a Product and Assigning a Client to Consume](#91-api-management---creating-a-product-and-assigning-a-client-to-consume)
- [**9.2 Create API Project Part 1**: REST/HTTP Services](#92-create-api-project-part-1---resthttp-services)
- [**9.3 Create API Project Part 2**: Using Swagger/OpenAPI Specifications](#93-creating-api-projects-part-2---using-swaggeropenapi-specifications)
- [**9.4 Security**: Verify API Key Policy](#94-security---verifying-api-key-policy)
- [**9.5 Security**: Implementing OAuth 2.0 Authentication](#95-security---implementing-oauth-20-authentication)
- [**9.6**: Debugger and Live Tracing in API Management](#96-debugger-and-live-tracing-in-api-management)
- [**9.7**: Runtime Manager, Logs, and Analytics](#97-runtime-manager-logs-and-analytics)

---

# Module 1: Introduction to Cloud-Native Integration with Fiorano

Welcome to the Fiorano Product Training series. In this module, we introduce Cloud-Native Integration using Fiorano. We will explore the challenges organizations face in enterprise integration and how Fiorano provides solutions to these challenges with its robust integration platform.

---

## 1.1: The Need for Fiorano in Enterprise Integration

### Understanding Organizational Challenges

Modern organizations encounter several challenges when integrating enterprise systems:

1. **Complex Integrations**: Dealing with intricate integrations between various applications and systems is often daunting due to differing protocols, data formats, and interfaces.

2. **Timely Delivery**: Ensuring that integration projects are completed within tight deadlines is critical for staying competitive and meeting business objectives.

3. **Data Security**: Protecting sensitive data during transmission between systems is paramount to prevent breaches and comply with regulatory requirements.

4. **Competitive Advantage**: Organizations need to innovate rapidly, delivering new services and value to customers faster than their competitors.

5. **Real-Time Data Processing**: Access to near-real-time data analytics is essential for making informed, data-driven decisions promptly.

6. **High Performance and Optimization**: Integration solutions must be optimized for high performance to handle large volumes of transactions efficiently.

### The Role of Fiorano in Addressing These Challenges

Fiorano provides an integration platform that directly addresses these organizational challenges by enabling:

- **Simplified Integration**: Offers tools and components that simplify the integration of complex systems.

- **Accelerated Development**: Reduces development time through pre-built components and a configuration-driven approach.

- **Secure Messaging**: Ensures data security during transmission with robust encryption and authentication mechanisms.

- **Decoupled Architecture**: Promotes a flexible architecture where systems can interact without tight coupling, enhancing scalability and maintainability.

- **Real-Time Data Flow**: Facilitates near-real-time data exchange and processing across systems.

- **High Performance**: Optimized for performance to handle high transaction volumes without compromising speed.

#### Depiction of Fiorano's Integration Environment

Imagine an environment where multiple channels and systems interact seamlessly:

- **Channels**:

  - **Customer Engagement**: Mobile applications, websites.
  - **Partner Platforms**: Collaborations with external partners.
  - **IoT Devices**: Sensors and devices generating data.
  - **Third-Party Service Providers**: External services that enhance functionality.

- **Backend Systems**:
  - **Enterprise Databases**: Core data repositories.
  - **Domain-Specific Platforms**: Industry-specific applications.
  - **External Services**: Additional services enhancing capabilities.

Fiorano sits at the center of this environment, enabling these diverse channels to communicate effectively with the backend systems.

### Key Features of Fiorano's Integration Platform

1. **Data Transformation**:

   - **Seamless Conversion**: Transforms data formats (e.g., XML, JSON) to match system requirements.
   - **Compatibility**: Ensures that different systems can understand and process the data exchanged.

2. **Secure Messaging**:

   - **Encryption**: Uses encryption protocols to secure data in transit.
   - **Authentication**: Implements authentication mechanisms to verify identities.

3. **Process Monitoring**:

   - **Real-Time Tracking**: Monitors processes and transactions as they occur.
   - **Analytics**: Provides insights into system performance and potential bottlenecks.

4. **Data Security**:

   - **Compliance**: Helps meet regulatory compliance requirements with robust security features.
   - **Audit Trails**: Maintains logs for auditing and tracking purposes.

5. **Decoupled Environment**:
   - **Flexibility**: Allows components to be modified independently without affecting the entire system.
   - **Scalability**: Facilitates scaling of individual components as needed.

### Benefits of Using Fiorano

- **Accelerated Development Time**:

  - **Pre-Built Components**: Utilizes existing connectors and services to reduce development efforts.
  - **Drag-and-Drop Configuration**: Simplifies the creation of workflows through an intuitive interface.

- **Ease of Implementation**:

  - **Interactive GUI**: Fiorano Studio provides a user-friendly graphical interface for designing integrations.
  - **Extensive Libraries**: Access to over 150 pre-built connectors for various protocols and services.

- **Optimized Performance**:

  - **High Throughput**: Capable of handling large volumes of data efficiently.
  - **Low Latency**: Ensures quick data transmission between systems.

- **Enhanced Security**:

  - **Secure Data Exchange**: Protects sensitive information during integration processes.
  - **Compliance Support**: Assists in meeting industry-specific security standards.

- **Real-Time Analytics and Decision Making**:
  - **Data Visibility**: Offers insights into data flows and system performance.
  - **Informed Decisions**: Enables data-driven strategies with up-to-date information.

### Conclusion of Part 1

Understanding the challenges in enterprise integration is the first step towards implementing an effective solution. Fiorano addresses these challenges by providing a comprehensive integration platform that simplifies complex integrations, enhances security, and accelerates time-to-market. By leveraging Fiorano's capabilities, organizations can focus on innovation and delivering value to their customers efficiently.

---

## 1.2: Fiorano Product Architecture Overview

Welcome back to the introductory series of Fiorano Product Training. In this part, we will explore the product architecture of Fiorano in more detail. Understanding the architecture is crucial for effectively designing, deploying, and managing integration solutions using the Fiorano platform.

---

## Overview of Fiorano's Product Architecture

Fiorano's architecture is designed to facilitate seamless integration and efficient management of enterprise applications. The key components of the architecture are:

- **Fiorano Studio (E-Studio)**
- **Enterprise Server (FES)**
- **Peer Server (FPS)**
- **Microservices and Event Processes**
- **Routes and Messaging System**

These components work together to enable the development, deployment, and execution of integration workflows, referred to as event processes in Fiorano.

## Developer Workflow in Fiorano

Let's navigate through the architecture by following a typical developer workflow:

### Step 1: Designing Integration Workflows in Fiorano Studio (E-Studio)

- **Fiorano Studio** is the Integrated Development Environment (IDE) where developers build integration workflows.
- Workflows in Fiorano are called **event processes**.
- Developers utilize an intuitive drag-and-drop interface to assemble pre-built microservices.
- Microservices represent reusable components that perform specific functions (e.g., data transformation, routing, protocol conversion).

#### Creating a New Event Process

1. **Start Fiorano Studio**:

   - Navigate to your Fiorano installation directory.
   - Launch `eStudio.exe` (Windows) or the corresponding executable on your system.

2. **Connect to the Enterprise Server**:

   - Upon launching, log in to the Enterprise Server using your credentials.
   - The Enterprise Server acts as a central repository and management hub.

3. **Add a New Event Process**:

   - Right-click on the **Event Process Repository** and select **Add Event Process**.
   - Provide a name for your event process (e.g., `DemoTraining`).
   - A new canvas opens for designing the workflow.

4. **Assembling Microservices**:

   - Use the **Microservice Palette** to drag and drop components onto the canvas.
   - For example, you can add two **Chat** components to simulate message exchange.
   - Rename components for clarity (e.g., `Chat1`, `Chat2`).

5. **Connecting Microservices with Routes**:
   - **Routes** define the communication paths between microservices.
   - Connect the output port of one microservice to the input port of another by drawing a route.
   - This connection establishes message flow within the event process.

### Step 2: Understanding Routes and Messaging

- **Routes** are not just visual connectors; they represent underlying JMS (Java Message Service) clients.
- The Fiorano messaging system uses JMS to facilitate communication between microservices.
- **Fiorano MQ** is the messaging backbone that handles message exchange.

#### Behind the Scenes:

- Each route corresponds to a JMS topic or queue.
- Microservices publish messages to these destinations, and subscribing microservices consume them.
- The messaging layer ensures reliable and asynchronous communication.

### Step 3: Managing the Enterprise Server (FES)

- The **Enterprise Server** manages metadata for all event processes and microservices.
- It orchestrates the deployment of event processes to the **Peer Server**.
- The server maintains version control and configurations of workflows.

### Step 4: Deploying and Running Event Processes

#### Starting the Enterprise Server

1. **Navigate to the Enterprise Server Directory**:

   - For example: `C:\Fiorano\13.0\ESB\FES\bin` (on Windows).

2. **Start the Server**:
   - Run `fes.bat` (Windows) or `./fes.sh` (Linux).
   - Look for the message `FES successfully deployed` to confirm startup.

#### Starting the Peer Server

1. **Navigate to the Peer Server Directory**:

   - For example: `C:\Fiorano\13.0\ESB\FPS\bin`.

2. **Start the Peer Server**:
   - Run `fps.bat` (Windows) or `./fps.sh` (Linux).
   - Confirm that the Peer Server is connected to the Enterprise Server.

#### Deploying the Event Process

1. **Check Resources and Connectivity (CRC)**:

   - In E-Studio, click on the **CRC** button to verify that all resources are available and that the Peer Server is running.
   - If the Peer Server is not running, an error message will appear.

2. **Run the Event Process**:
   - Click on the **Run Event Process** button in E-Studio.
   - Microservices will change color (typically to green) to indicate that they are running.

### Step 5: Interacting with the Running Workflow

- Open the microservice components (e.g., Chat components) to interact with them.
- Send messages through one component and observe them in another.
- This demonstrates the real-time data exchange facilitated by Fiorano.

## Deployment Topology

The way Fiorano components are deployed can vary based on organizational needs.

### Single Machine Deployment

- **Development and Testing**: Often, both the Enterprise Server and Peer Server are run on the same machine for simplicity.
- **Advantages**: Easier setup, suitable for development purposes.

### Distributed Deployment

- **Enterprise Server**: Deployed on a central server or in the cloud.
- **Peer Servers**: Deployed across multiple machines or locations.
- **Advantages**:
  - **Scalability**: Add more Peer Servers to handle increased load.
  - **Flexibility**: Deploy Peer Servers closer to the systems they integrate with to reduce latency.

### Hybrid Deployment

- **Combination**: Mix of on-premises and cloud deployments.
- **Use Cases**:
  - **On-Premises Systems**: Integrate legacy systems within a private network.
  - **Cloud Services**: Connect to SaaS applications and cloud services.
  - Fiorano handles communication securely between on-premises Peer Servers and cloud-based Enterprise Servers or vice versa.

## Reliability and Resilience

- If the Enterprise Server goes down, the Peer Server continues to run, ensuring no interruption of live applications.
- **Decoupled Architecture**: The independence of servers enhances reliability.

## Monitoring and Management

- **Fiorano Studio** provides tools to monitor the status of servers and event processes.
- **Runtime Metrics**: View CPU and memory usage, message counts, and other performance indicators.
- **Logging**: Access logs for troubleshooting and auditing purposes.

## Important Concepts

### Microservices

- **Definition**: Modular, reusable components that perform specific tasks within an event process.
- **Types**: There are over 150 pre-built microservices in Fiorano covering various protocols, data formats, and functionalities.

### Event Processes

- **Definition**: Integration workflows composed of interconnected microservices.
- **Function**: Define the flow of data and control logic between systems.

### Messaging System

- **Fiorano MQ**: The messaging backbone using JMS.
- **Purpose**: Handles the transport of messages between microservices reliably.

## Summary

In this session, we explored:

- The key components of Fiorano's product architecture and their roles.
- How to set up and start the Enterprise Server and Peer Server.
- Designing and deploying an event process using Fiorano Studio.
- The underlying messaging system that facilitates communication between microservices.
- Deployment topologies and their implications for scalability and reliability.

Understanding Fiorano's architecture is essential for effectively leveraging its capabilities in enterprise integration projects. The platform's flexibility allows it to adapt to various deployment scenarios, meeting the needs of both small-scale and large-scale integration challenges.

---

## 1.3: Deep Dive into Event Processes and Low-Level Architecture

Welcome back to the Fiorano Product Training series. In this session, we will deepen our understanding of Fiorano's product architecture, focusing on how event processes function at a granular level. This discussion builds upon the concepts introduced in Parts 1 and 2, so it's recommended to review those sections before proceeding.

---

## Low-Level Architecture of Event Processes

In Fiorano, an **event process** represents an integration workflow composed of interconnected microservices. Understanding how these microservices communicate at a low level is crucial for designing efficient and scalable integration solutions.

### Single Peer Deployment

Initially, let's consider a scenario where all components of an event process are deployed on a single **Peer Server** running on one machine.

- **Workflow Execution**: All microservices are executed within the same Peer Server.
- **Communication Between Microservices**:
  - **Routes**: Define the data flow between microservices.
  - **Messaging**: Behind the scenes, routes utilize Fiorano MQ (Messaging Queue) for message exchange.
  - **JMS Clients**: Each route corresponds to a JMS (Java Message Service) client that publishes and subscribes to messages.
- **Simplified Architecture**: This setup is straightforward and suitable for environments where all systems are co-located.

#### Illustration:

- **Peer Server** (Machine 1):
  - **Microservice A**
  - **Microservice B**
  - **Microservice C**
- **Communication**: Microservices communicate via routes using Fiorano MQ within the same Peer Server.

### Distributed Deployment Across Multiple Peer Servers

Fiorano provides the flexibility to distribute microservices across multiple Peer Servers, potentially residing on different machines or in different geographical regions.

#### Scenario:

- **Peer Server 1** (Machine 1):
  - **Microservices**: External Web Service, Request Audit, Email Service.
- **Peer Server 2** (Machine 2):
  - **Microservices**: Value Check, Data Transformation, Database Service.
- **Communication Between Peer Servers**:
  - **Peer-to-Peer Architecture**: Microservices on different Peer Servers communicate seamlessly.
  - **Fiorano MQ**: Manages messaging across Peer Servers, ensuring reliable data exchange.
  - **Security and Connectivity**: Secure and authenticated connections are established between Peer Servers.

#### Advantages:

- **Scalability**: Distribute processing load across multiple servers.
- **Flexibility**: Deploy microservices closer to the systems they integrate with, reducing latency.
- **Fault Isolation**: Issues in one Peer Server do not necessarily impact microservices running on another.

### Cross-Regional Deployment

Fiorano supports deploying Peer Servers in different geographical regions, enabling global integration scenarios.

#### Example:

- **Peer Server in Region A (e.g., Middle East)**:
  - **Microservices**: Specific components relevant to the region.
- **Peer Server in Region B (e.g., US East)**:
  - **Microservices**: Components serving users in the United States.
- **Inter-Region Communication**:
  - **Network Connectivity**: Requires proper network configuration to allow communication between regions.
  - **Latency Considerations**: Acknowledge potential latency in cross-region messaging.

### Key Considerations for Distributed Architectures

1. **Network Configuration**:

   - Ensure that firewall rules and network policies permit communication between Peer Servers.
   - Use VPNs or secure tunnels where necessary.

2. **Security**:

   - Implement secure communication channels using SSL/TLS.
   - Authenticate Peer Servers to prevent unauthorized access.

3. **Performance**:

   - Monitor latency and throughput when messaging across regions.
   - Optimize message sizes and frequencies to enhance performance.

4. **Reliability**:
   - Design for failover and redundancy to handle network interruptions.
   - Use Fiorano's built-in features for message persistence and retry mechanisms.

## Peer-to-Peer Communication in Fiorano

The ability for Peer Servers to communicate directly with each other is a powerful feature of Fiorano's architecture.

- **Decoupled Communication**: Microservices do not need to be aware of the physical location of other services.
- **Dynamic Routing**: Messages are routed based on configurations, allowing for flexible deployment strategies.
- **Scalability**: Add or remove Peer Servers as needed without significant reconfiguration.

## Deployment Scenarios

### Single Region Deployment

- **Use Case**: All systems and services are within the same data center or cloud region.
- **Benefits**:
  - **Low Latency**: Faster communication due to proximity.
  - **Simplified Networking**: Fewer network considerations.

### Multi-Region Deployment

- **Use Case**: Global organizations with systems distributed across different locations.
- **Benefits**:
  - **Localized Processing**: Process data closer to its origin or consumption point.
  - **High Availability**: Distribute services to avoid a single point of failure.

### Hybrid Deployment

- **Combination of On-Premises and Cloud**:
  - **On-Premises Peer Servers**: Connect legacy systems or sensitive data repositories.
  - **Cloud Peer Servers**: Integrate with SaaS applications or provide scalability.

## Practical Implications

- **Flexible Topologies**: Developers can design workflows that span multiple Peer Servers according to business needs.
- **Performance Optimization**: By strategically placing microservices, organizations can optimize performance and resource utilization.
- **Resilience and Fault Tolerance**: Distributing services enhances the system's ability to handle failures gracefully.

## Summary

In this session, we explored the low-level architecture of Fiorano's event processes, focusing on:

- How microservices within an event process communicate using Fiorano MQ and JMS clients.
- The capability of deploying microservices across multiple Peer Servers, either within the same machine or distributed across different machines and regions.
- The benefits of a peer-to-peer architecture, including scalability, flexibility, and reliability.
- Considerations and best practices for distributed deployments, including network configuration and security.

Understanding these aspects of Fiorano's architecture enables developers and architects to design robust integration solutions that can adapt to various deployment scenarios and meet complex enterprise requirements.

---

## 1.4: Deployment Topologies in Fiorano

Welcome back to the Fiorano Product Training series. In this session, we will explore different deployment topologies that Fiorano supports. Understanding deployment models is crucial for architects and developers to design solutions that meet organizational requirements for scalability, reliability, and performance.

---

## Overview of Deployment Topologies

Fiorano's flexible architecture allows for various deployment models to accommodate different operational needs and infrastructure setups. The primary deployment topologies are:

1. **Standalone Deployment**
2. **Distributed Deployment**
3. **Hybrid Deployment**

Each topology has its advantages and is suitable for specific scenarios based on factors like resource availability, performance requirements, and network configurations.

### 1. Standalone Deployment

**Description**:

- Both the **Enterprise Server (FES)** and the **Peer Server (FPS)** are installed and run on a single machine or node.
- This setup is commonly used for development, testing, or small-scale deployments.

**Characteristics**:

- **Simplified Setup**: Easier to configure and manage, ideal for local development environments.
- **Resource Constraints**: Limited scalability due to the resources of a single machine.
- **Use Cases**:
  - Proof of concept implementations.
  - Development and unit testing.
  - Small enterprises or applications with minimal load.

**Illustration**:

```
[Single Machine]
   |
   +-- Enterprise Server (FES)
   |
   +-- Peer Server (FPS)
```

### 2. Distributed Deployment

**Description**:

- The **Enterprise Server** and **Peer Server(s)** are installed on separate nodes or machines.
- Multiple Peer Servers can be deployed across different machines to distribute the processing load.

**Characteristics**:

- **Scalability**: Enhanced ability to handle increased load by adding more Peer Servers.
- **Performance Optimization**: Deploy Peer Servers closer to the systems they integrate with to reduce latency.
- **Isolation**: Faults in one Peer Server do not impact others, improving resilience.
- **Use Cases**:
  - Medium to large enterprises requiring scalability.
  - Environments where different systems are located across multiple servers.
  - Scenarios needing separation of management and execution environments.

**Illustration**:

```
[Node 1]                     [Node 2]
   |                             |
   +-- Enterprise Server (FES)   +-- Peer Server 1 (FPS)

                                [Node 3]
                                   |
                                   +-- Peer Server 2 (FPS)
```

- **Enterprise Server** on one machine.
- **Peer Server 1** and **Peer Server 2** on separate machines.
- Event Processes are deployed to Peer Servers based on resource allocation and proximity to integrated systems.

### 3. Hybrid Deployment

**Description**:

- Combines both on-premises and cloud deployments.
- The **Enterprise Server** and **Peer Server(s)** can be deployed in a mix of on-premises data centers and cloud platforms.

**Characteristics**:

- **Flexibility**: Leverage the benefits of both on-premises and cloud infrastructures.
- **Cost Optimization**: Utilize cloud resources for scalability while maintaining critical systems on-premises.
- **Integration**: Seamlessly integrate cloud-based services with on-premises applications.
- **Use Cases**:
  - Organizations transitioning to the cloud while retaining some systems on-premises.
  - Scenarios requiring data residency compliance by keeping sensitive data on-premises.
  - Distributed teams and systems spread across different geographical locations.

**Illustration**:

```
[On-Premises Data Center]            [Cloud Platform]
       |                                     |
       +-- Enterprise Server (FES)           +-- Peer Server 1 (FPS)
       |                                     |
       +-- Peer Server 2 (FPS)               +-- Peer Server 3 (FPS)
```

- The **Enterprise Server** and **Peer Server 2** are on-premises.
- **Peer Server 1** and **Peer Server 3** are deployed in the cloud (e.g., AWS, Azure, GCP).
- Event Processes can run across both on-premises and cloud Peer Servers.

## Considerations for Each Deployment Topology

### Standalone Deployment

- **Pros**:

  - Simple and quick to set up.
  - Minimal infrastructure requirements.
  - Ideal for development and testing.

- **Cons**:
  - Not suitable for production environments with high availability requirements.
  - Limited scalability and performance.
  - Single point of failure.

### Distributed Deployment

- **Pros**:

  - Enhanced scalability by adding more Peer Servers.
  - Improved performance through load distribution.
  - Fault isolation between Peer Servers.
  - Ability to scale specific parts of the integration solution independently.

- **Cons**:
  - More complex setup and management.
  - Requires careful network configuration and security considerations.
  - Potentially higher infrastructure costs.

### Hybrid Deployment

- **Pros**:

  - Combines the strengths of both on-premises and cloud deployments.
  - Flexible resource allocation based on workload demands.
  - Can reduce infrastructure costs by leveraging cloud scalability.
  - Supports compliance with data residency and regulatory requirements.

- **Cons**:
  - Increased complexity in configuration and management.
  - Requires robust security measures for communication between on-premises and cloud servers.
  - Potential latency issues over the internet if not properly managed.

## Deployment Strategies

### Resource Allocation

- **Event Process Deployment**:

  - Decide which Peer Server(s) an event process should be deployed to based on:
    - Proximity to the systems being integrated.
    - Available resources like CPU, memory, and network bandwidth.
    - Organizational policies and compliance requirements.

- **Server Group Configurations**:
  - Group Peer Servers into logical collections (Server Groups) for easier management.
  - Deploy event processes to server groups instead of individual Peer Servers.

### High Availability and Fault Tolerance

- **Clustering**:

  - Implement clusters of Peer Servers to provide high availability.
  - Use load balancers to distribute requests among multiple Peer Servers.

- **Redundancy**:
  - Deploy multiple instances of the Enterprise Server and Peer Servers.
  - Ensure critical components have failover mechanisms.

### Security Considerations

- **Network Security**:

  - Secure communication between Enterprise Server and Peer Servers using SSL/TLS.
  - Implement firewalls and VPNs as needed.

- **Access Control**:
  - Define user roles and permissions to control access to Fiorano components.
  - Use authentication and authorization mechanisms.

### Monitoring and Management

- **Centralized Monitoring**:

  - Use Fiorano's monitoring tools to oversee all the components from a single interface.
  - Track performance metrics, resource utilization, and system health.

- **Automated Deployment**:
  - Utilize Fiorano's automated deployment features to manage event processes across servers.

## Practical Scenarios

### Scenario 1: Enterprise Integration within a Single Data Center

- **Deployment**: Distributed deployment within an on-premises data center.
- **Use Case**: Integrating multiple internal applications with high transaction volumes.
- **Benefits**:
  - Low network latency.
  - Secure internal network.
  - Scalability by adding more Peer Servers.

### Scenario 2: Global Integration for a Multinational Corporation

- **Deployment**: Hybrid deployment with Peer Servers in different geographical regions.
- **Use Case**: Integrating systems located in different countries, both on-premises and in the cloud.
- **Benefits**:
  - Local processing reduces latency for regional systems.
  - Central management via the Enterprise Server.
  - Compliance with regional data regulations.

### Scenario 3: Cloud Migration Strategy

- **Deployment**: Gradual transition from on-premises to cloud deployment.
- **Use Case**: An organization moving its infrastructure to the cloud but still retains critical systems on-premises.
- **Benefits**:
  - Flexibility during migration.
  - Minimal disruption to existing systems.
  - Ability to leverage cloud services incrementally.

## Summary

In this session, we covered:

- **Standalone Deployment**: Suitable for development and small-scale applications.
- **Distributed Deployment**: Offers scalability and performance optimization by deploying components across multiple machines.
- **Hybrid Deployment**: Combines on-premises and cloud deployments for flexibility and resource optimization.

Understanding these deployment topologies helps in designing integration solutions that align with organizational goals, infrastructure constraints, and scalability requirements. Fiorano's flexible architecture supports a variety of deployment models, allowing architects and developers to tailor solutions to specific needs.

---

## 1.5: Fiorano API Management Architecture

Welcome back to the final part of our introductory series on Fiorano. In this session, we will explore Fiorano's API Management architecture. Understanding the API Management component is crucial as it allows organizations to securely expose, manage, and monitor APIs, which are essential for modern integration strategies.

---

## Introduction to Fiorano API Management

### The Role of API Management

- **API Exposure**: Once APIs or services are developed, they need to be exposed securely for consumption by various clients and partners.
- **Secure and Efficient Delivery**: Organizations require mechanisms to ensure that APIs are delivered securely, efficiently, and reliably.
- **Management and Monitoring**: Administrators need tools to manage API lifecycle, monitor usage, enforce policies, and ensure compliance.

### Fiorano API Management Components

Fiorano's API Management solution consists of two main components:

1. **API Management Server (AMS)**:

   - Acts as the centralized hub for managing API projects, environments, and gateways.
   - Enforces API policies related to security, traffic management, transformation, authentication, authorization, and more.
   - Provides administrative interfaces for configuring and deploying APIs.

2. **API Gateway Server (AGS)**:
   - Functions as the execution server where user requests are processed.
   - Serves as the front-facing component that clients interact with when consuming APIs.
   - Performs actions like request routing, protocol translation, policy enforcement, and response caching.

## Fiorano API Management Architecture

### High-Level Architecture Overview

The architecture includes several key elements:

- **Clients/Consumers**: Various channels such as mobile apps, web applications, partner systems, and IoT devices that consume APIs.
- **API Gateway Server (AGS)**: The entry point for all API requests. It enforces policies, authenticates requests, and routes them to backend services.
- **API Management Server (AMS)**: Centralized management plane that oversees API configurations, policies, and lifecycle.
- **Backend Services**: The actual services or APIs developed, which may be hosted on Fiorano ESB or other platforms.

### Interaction Flow

1. **Client Request**:
   - A client sends an API request to the API Gateway Server.
2. **Gateway Processing**:
   - The Gateway Server authenticates the request using policies defined.
   - It may perform additional actions like rate limiting, routing, and transformation.
3. **Communication with Backend Services**:
   - The Gateway forwards the request to the appropriate backend service.
   - Backend services process the request and return the response.
4. **Response Handling**:
   - The Gateway may modify or enrich the response as per policies before sending it back to the client.

### Key Functions of Fiorano API Management

- **API Creation and Deployment**:
  - Define API endpoints, methods, and mappings.
  - Deploy APIs to the Gateway Server for exposure to clients.
- **Policy Enforcement**:
  - Implement security policies like OAuth 2.0, API keys, and IP filtering.
  - Enforce traffic policies such as throttling and rate limiting.
- **Monitoring and Analytics**:

  - Track API usage metrics, performance, and errors.
  - Gain insights through analytics dashboards.

- **Developer Portal**:
  - Fiorano provides a developer portal where API consumers can discover APIs, read documentation, and manage their subscriptions.

## Deployment Scenarios

### On-Premises Deployment

- **AMS and AGS On-Premises**:
  - Both the API Management Server and Gateway Server are deployed within the organization's infrastructure.
  - Suitable for organizations that require complete control over their API infrastructure.

### Cloud Deployment

- **AMS and/or AGS in the Cloud**:
  - Components can be deployed on cloud platforms like AWS, Azure, or GCP.
  - Enables scalability and reduces the overhead of maintaining on-premises hardware.

### Hybrid Deployment

- **Combination of On-Premises and Cloud**:
  - API Management Server on-premises with Gateway Servers deployed in the cloud, or vice versa.
  - Facilitates integrating on-premises services with cloud-based clients or services.

## Key Features of Fiorano API Management

### Security

- **Authentication and Authorization**:
  - Supports OAuth 2.0, API keys, and custom authentication mechanisms.
- **Secure Communication**:
  - Enforces SSL/TLS for secure data transmission.
- **Policy-Based Access Control**:
  - Allows granular control over who can access specific APIs.

### Traffic Management

- **Rate Limiting**:
  - Controls the number of requests a client can make in a given time period.
- **Throttling**:
  - Manages API consumption to prevent overuse and ensure fair distribution of resources.

### Transformation and Enrichment

- **Data Transformation**:
  - Converts data formats (e.g., XML to JSON) to match client or backend requirements.
- **Message Enrichment**:
  - Adds additional data to requests or responses as needed.

### Analytics and Monitoring

- **Real-Time Monitoring**:
  - Provides dashboards for live tracking of API usage and performance.
- **Logging and Auditing**:
  - Maintains logs for auditing purposes and troubleshooting.

### Developer Engagement

- **Developer Portal**:
  - Offers a self-service portal for developers to access API documentation, test APIs, and manage API keys.
- **API Catalog**:
  - Catalogs all available APIs with descriptions, usage guidelines, and versioning.

## Starting the API Management Servers

To work with Fiorano API Management, both the Management Server and Gateway Server need to be running.

### Starting the API Management Server (AMS)

1. **Navigate to the Server Directory**:
   - For example: `C:\Fiorano\13.0\ESB\Server\bin`.
2. **Run the Server Command**:

   - Open a command prompt and execute:
     ```
     server.bat -mode ams -profile <profile_name>
     ```
   - Replace `<profile_name>` with your profile, e.g., `server1`.

3. **Server Initialization**:
   - The server initializes and establishes connections to the necessary databases (e.g., PostgreSQL).

### Starting the API Gateway Server (AGS)

1. **Run the Gateway Command**:
   - In the same directory, execute:
     ```
     server.bat -mode ags -profile <profile_name>
     ```
2. **Gateway Initialization**:
   - The Gateway Server starts up and connects to the API Management Server.

### Database Connectivity

- Fiorano API Management uses a database to store configurations and metadata.
- Ensure that the database (e.g., PostgreSQL) is running and accessible.

## Accessing the API Management Dashboard

Once the servers are running, you can access the API Management Dashboard via a web browser.

- **URL**: `http://<server_address>:1980/fiorano`.

### Dashboard Features

- **API Projects**:
  - Manage API projects, including creation, modification, and deployment.
- **Products**:
  - Group APIs into products for subscription and access control.
- **Analytics**:
  - View usage statistics, performance metrics, and traffic analysis.
- **Security Policies**:
  - Configure global and API-specific security policies.

## Integration with Backend Services

### Flexibility in Backend Technologies

- Fiorano API Management can manage APIs developed using Fiorano ESB or any other technology stack.
- The Gateway Server acts as a reverse proxy, forwarding API requests to the appropriate backend services.

### Connecting to Fiorano ESB Services

- **Seamless Integration**:
  - If backend services are built on Fiorano ESB, integration is straightforward.
- **Data Transformation and Routing**:
  - Leverage Fiorano ESB capabilities for complex data transformation and intelligent routing before responses are sent back through the Gateway.

## Security Considerations

### SSL/TLS Configuration

- **Securing the Gateway**:
  - Configure SSL/TLS certificates on the Gateway Server to enforce HTTPS communication.
- **Certificate Management**:
  - Manage key stores and trust stores to handle certificates and encryption keys.

### API Security Policies

- **Authentication**:
  - Implement various authentication schemes to verify client identities.
- **Authorization**:
  - Define roles and permissions to control access to APIs.
- **Threat Protection**:
  - Protect APIs from common threats like SQL injection, XML bombs, and DDoS attacks.

## Monitoring and Analytics

- **Dashboard Views**:
  - Get real-time insights into API performance and health.
- **Alerts and Notifications**:
  - Set up alerts for specific events or thresholds.
- **Usage Reports**:
  - Generate reports for usage patterns, helping in capacity planning and optimization.

## Developer Portal and API Consumption

- **Client Onboarding**:
  - Clients can register, obtain API keys, and subscribe to API products.
- **API Documentation**:
  - Provide comprehensive documentation, including API specs and usage examples.
- **Testing Tools**:
  - Offer tools for clients to test APIs directly from the portal.

## Conclusion

Fiorano's API Management architecture complements its integration platform by enabling secure, efficient, and manageable API exposure. It provides organizations with the tools needed to control how their APIs are consumed, ensuring security and compliance while delivering high performance.

Key takeaways:

- **Centralized Management**: The API Management Server serves as the control center for all API configurations and policies.
- **Secure API Exposure**: The Gateway Server securely exposes APIs to clients, enforcing policies and managing traffic.
- **Flexibility**: Fiorano API Management supports various deployment models and integrates with different backend technologies.
- **Developer Engagement**: The platform facilitates collaboration with clients and partners through the developer portal.

---

### Conclusion of the Introductory Series

This concludes our introductory series on Fiorano's Cloud-Native Integration platform. We have covered:

- The challenges in enterprise integration and how Fiorano addresses them.
- The core components and architecture of Fiorano ESB.
- Deployment topologies suitable for different organizational needs.
- The integration of Fiorano API Management for secure API exposure and management.

With this foundational knowledge, you are now better equipped to delve deeper into Fiorano's capabilities, explore advanced features, and begin designing robust integration solutions for your organization.

---

# Module 2: Data Transformation

Welcome to Module 2 of the Fiorano Product Training series. In this module, we'll explore data transformation techniques within Fiorano, focusing on how to expose REST services, integrate with databases, and perform various data transformations.

---

## 2.1 Exposing a REST Service

In this session, we will learn how to expose a RESTful service using Fiorano. Exposing REST services is fundamental for enabling communication between clients and backend systems over HTTP, allowing for seamless integration and data exchange.

### Objectives

- Understand how to use the **REST Stub** component in Fiorano.
- Configure a REST service with appropriate methods and resources.
- Test the exposed REST service using tools like Postman.

### Prerequisites

- Fiorano Studio (E-Studio) installed and connected to the Enterprise Server.
- Basic understanding of RESTful services and HTTP methods.
- Familiarity with Fiorano's development environment.

### Step-by-Step Guide

#### Step 1: Create a New Event Process

1. **Open Fiorano Studio (E-Studio)**:

   - Launch E-Studio and connect to your Enterprise Server if not already connected.

2. **Create a New Event Process**:
   - In the **Event Process Repository**, right-click and select **Add Event Process**.
   - **Name**: Enter a meaningful name (e.g., `ExposeRESTService`).
   - **Category**: Create or select a package (e.g., `FioranoTraining`).
   - Click **Finish** to create the event process.

#### Step 2: Add the REST Stub Component

1. **Locate the REST Stub Component**:

   - In the **Microservice Palette**, search for **REST Stub**.
   - The REST Stub component is used to expose RESTful services within Fiorano.

2. **Add the REST Stub to the Canvas**:
   - Drag and drop the **REST Stub** onto the main canvas.

#### Step 3: Configure the REST Stub Component

1. **Open the REST Stub Configuration**:

   - Double-click on the REST Stub component to open its **Service Descriptor**.

2. **Set the Service Name**:

   - Under the **General** tab, enter a unique **Service Name** (e.g., `ProductService`).

3. **Define Resources**:

   - Navigate to the **Resources** tab.
   - Click **Add Resource** to define the endpoint path.
     - **Path**: Enter the resource path (e.g., `/products`).
     - **ID**: (Optional) Provide an ID for readability (e.g., `ProductsResource`).

4. **Add Methods**:

   - Select the newly created resource and click **Add Method**.
   - Choose the HTTP methods you want to support (e.g., **GET**, **POST**).
   - For the **GET** method:
     - **Request Configuration**: Typically, GET requests do not have a body, but you can define query parameters.
       - Click **Add Parameter** to add query parameters if needed (e.g., `productId`).
     - **Response Configuration**:
       - Click **Add Representation**.
       - **Media Type**: Select `application/json`.
       - Define any schemas if required.
   - For the **POST** method:
     - **Request Configuration**:
       - Click **Add Representation**.
       - **Media Type**: Select `application/json`.
       - Define any schemas if required.
     - **Response Configuration**:
       - Similar to GET, define the media type and schema for the response.

5. **Configure Security (Optional)**:

   - If you want to secure the REST service, navigate to the **Security** tab.
   - Enable **Use SSL** to expose the service over HTTPS.
   - Configure **Key Store** and **Trust Store** with your SSL certificates.

6. **Advanced Settings**:

   - Set **Execution Timeout** and **Message TTL (Time-to-Live)** as per your requirements.
     - **Execution Timeout**: Time in milliseconds Fiorano should wait for the response before timing out.
     - **Message TTL**: Lifespan of a message in milliseconds within Fiorano's messaging system.

7. **Finalize Configuration**:
   - Click **Finish** to save the configuration.

#### Step 4: Connecting Components (Optional)

If your REST service needs to process data or interact with other microservices:

1. **Add Additional Components**:

   - Drag and drop any processing components you need (e.g., a **Mapper**, **Database Connector**, **Transformation** components).

2. **Connect Components with Routes**:

   - Use routes to connect the **REST Stub** to other components.
     - Connect the **Output Port** of the REST Stub to the **Input Port** of the next component.
     - Process the data as required.

3. **Configure Data Transformation**:
   - If you're transforming data, configure the mappings in the Mapper component.
   - Define how incoming data should be processed and what response should be sent back.

#### Step 5: Configure Response Mapping

1. **Map the Response Data**:

   - Right-click on the route connecting to the **Response Port** of the REST Stub.
   - Select **Configure Transformation**.
   - Map the output data to the response structure expected by the client.

2. **Set Response Status (Optional)**:
   - In the transformation configuration, you can set the HTTP response status code (e.g., `200 OK`).

#### Step 6: Run the Event Process

1. **Check Resources and Connectivity**:

   - Click on the **CRC** (Check Resource and Connectivity) button to ensure all configurations are correct.

2. **Run the Event Process**:
   - Click on **Run Event Process** to deploy and start the service.
   - The component should turn green, indicating it is running.

#### Step 7: Test the REST Service

1. **Retrieve the WADL**:

   - Right-click on the REST Stub component and select **View WADL**.
   - Copy the **Endpoint URL** displayed.

2. **Use a REST Client**:

   - **Postman** or **cURL** can be used to test the service.
   - **Example**:
     - **URL**: Paste the endpoint URL (e.g., `http://localhost:1856/products`).
     - **Method**: Select **GET** or **POST** depending on what you configured.
     - **Headers**: Set **Content-Type** to `application/json` if necessary.
     - **Body**: For POST requests, provide a JSON payload.
   - **Send the Request** and observe the response.

3. **Validate the Response**:
   - Ensure that the response matches your expectations.
   - Check for correct status codes, headers, and data formats.

#### Step 8: Troubleshooting

1. **Logs and Debugging**:

   - If the service is not responding as expected, check the logs.
   - Right-click on the component and select **View Logs** to see error and output logs.

2. **Breakpoints and Debugger**:
   - Use Fiorano's debugger to set breakpoints on routes.
   - Monitor the data flowing through the components in real-time.

### Best Practices

- **Naming Conventions**: Use meaningful names for services, resources, and methods to improve readability.
- **Versioning**: Implement API versioning in the context path to manage changes over time (e.g., `/v1/products`).
- **Security**: Always consider securing your REST services, especially in production environments.
- **Error Handling**: Implement proper error handling to return informative responses in case of failures.

### Conclusion

You have successfully exposed a REST service using Fiorano. This service can now be consumed by clients over HTTP, facilitating integration with other applications and systems. Understanding how to expose and configure REST services is a fundamental skill when working with Fiorano and is essential for building robust integration solutions.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this module, we are exploring various aspects of data transformation using Fiorano, which is essential for integrating disparate systems that use different data formats and protocols.

---

## 2.2 Connecting to a Database

In this session, we will learn how to connect to a database using Fiorano's Database microservice. Integrating with databases is a fundamental aspect of enterprise integration, allowing you to read from and write to databases as part of your integration workflows.

### Objectives

- Understand how to use the **Database** component in Fiorano.
- Configure a database connection using JDBC drivers.
- Execute SQL queries and retrieve data from a database.
- Test and validate the database integration within an event process.

### Prerequisites

- Fiorano Studio (E-Studio) installed and connected to the Enterprise Server.
- Basic knowledge of databases and SQL queries.
- A working database instance (e.g., PostgreSQL, MySQL, SQL Server) accessible from your Fiorano environment.
- Relevant JDBC driver for your database type.

### Step-by-Step Guide

#### Step 1: Prepare the Database Component

1. **Open Fiorano Studio (E-Studio)**:

   - Launch E-Studio and connect to your Enterprise Server.

2. **Create a New Event Process**:

   - In the **Event Process Repository**, right-click and select **Add Event Process**.
   - **Name**: Enter a name like `DatabaseIntegration`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

3. **Add the Database Component to the Canvas**:
   - In the **Microservice Palette**, search for **DB** under the **Connectors** category.
   - Drag and drop the **DB** component onto the canvas.
4. **Add Supporting Components**:
   - **Feeder Component**: Acts as a message source to initiate the workflow.
     - Find **Feeder** in the **Inputs** category and add it to the canvas.
   - **Display Component**: Used to display the output data.
     - Find **Display** in the **Outputs** category and add it to the canvas.

#### Step 2: Configure the Database Component

1. **Edit the Service Descriptor to Add JDBC Driver**:

   - Right-click on the **DB** component and select **Edit**.
   - In the **Service Descriptor** window, go to the **Deployment** tab.
   - Under **Runtime Dependencies**, ensure the JDBC driver for your database is added.
     - **Add Library**: Click to add the JDBC driver JAR file.
     - For example, if using PostgreSQL, add `postgresql-<version>.jar`.
   - Click **Save** and **Close** the Service Descriptor.

2. **Configure Database Connection**:

   - Double-click on the **DB** component to open its configuration window.
   - In the **Database Configuration** section:
     - **DB URL**: Enter the JDBC URL of your database.
       - Example for PostgreSQL: `jdbc:postgresql://<hostname>:<port>/<database_name>`
     - **DB User**: Enter your database username.
     - **DB Password**: Enter your database password.
   - **Test Connection**:
     - Click **Test** to verify the connection to the database.
     - If successful, a message `Connection created successfully` appears.

3. **Configure SQL Operations**:

   - Navigate to the **SQL Configuration** tab.
   - Click **Add** to create a new SQL operation.
     - **Operation Type**: Choose the type of operation (e.g., **Select**, **Insert**, **Update**).
     - **Operation Name**: Provide a name, e.g., `FetchPersons`.
   - **Configure the SQL Query**:
     - **Select Statement**: Construct your SQL query using the wizard or manually.
       - Click **Refresh Tables** to load available tables from the database.
       - Choose the desired table (e.g., `persons`) and select the columns to retrieve.
       - Optionally, add a **Where** condition to filter results.
         - For example: `WHERE person_id = ?`
           - `?` denotes a parameter that will be supplied at runtime.
     - **Parameterize the Query**:
       - Ensure that parameters (e.g., `person_id`) are correctly defined for dynamic input.
   - **Advanced Configurations** (Optional):
     - Set options like **Fetch Size**, **Max Rows**, or **Timeout** if necessary.
   - Click **Finish** to save the SQL operation.

4. **Error Handling Configuration** (Optional):
   - Navigate to the **Error Handling** tab.
   - Configure retry mechanisms and error responses as needed.
     - **Retry on Connection Error**: Enable and set retry attempts and intervals.
     - **Retry on Invalid Request**: Enable to retry on statement errors.
   - Click **Finish** to return to the main canvas.

#### Step 3: Connect Components and Configure Routes

1. **Connect the Components**:

   - **Feeder to Database Component**:
     - Draw a route from the **Out Port** of the **Feeder** to the **In Port** of the **Database** component.
   - **Database Component to Display Component**:
     - Draw a route from the **Out Port** of the **Database** component to the **In Port** of the **Display** component.

2. **Configure Input Mapping to Database Component**:

   - Right-click on the route between the **Feeder** and **Database** components.
   - Select **Configure Transformation**.
   - In the **Mapper** window:
     - **Source Schema**: Represents the message from the **Feeder**.
     - **Target Schema**: Represents the input expected by the **Database** component.
   - **Mapping Parameters**:
     - Map the feeder input to the database query parameter.
       - Drag **Text Content** from **JMS Message Functions** to the corresponding parameter (e.g., `person_id`).
   - Click **Save** and **Close** the Mapper.

3. **Configure Output Mapping if Necessary**:
   - If transformations are needed on the output data before displaying, configure the route between the **Database** component and the **Display** component similarly.

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**:

   - Ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - The components should turn green, indicating they are running.

4. **Open the Feeder Component**:

   - Double-click on the **Feeder** component to open the input window.

5. **Provide Input Data**:

   - Enter a value corresponding to a `person_id` in your database.
     - For example: `12345`.
   - Click **Send** to initiate the query.

6. **View the Output**:
   - Double-click on the **Display** component to view the results.
   - The data retrieved from the database should be displayed.
     - Verify that the output matches the expected data for the given `person_id`.

#### Step 5: Validate and Troubleshoot

1. **Testing with Different Inputs**:

   - Run multiple tests with different `person_id` values to ensure the query works as expected.

2. **Error Handling**:

   - Test cases where the `person_id` does not exist to see how the system handles no results.
   - Observe any error messages or exceptions.

3. **Logs and Debugging**:
   - **View Logs**:
     - Right-click on the **Database** component and select **View Logs** to see error and output logs.
   - **Use Breakpoints**:
     - Set breakpoints on routes to inspect data at different stages.
     - Use the debugger to step through the process and examine messages.

### Best Practices

- **Security**:

  - Never hard-code sensitive information like passwords in the process.
  - Use secure storage or configurations for credentials.

- **Connection Pooling**:

  - Configure connection pooling parameters to optimize database connections.

- **Prepared Statements**:

  - Use parameterized queries to prevent SQL injection attacks.

- **Error Handling**:

  - Implement robust error handling to manage database exceptions gracefully.

- **Performance Considerations**:

  - Optimize SQL queries for performance.
  - Limit the amount of data fetched where possible, especially with large datasets.

- **Resource Management**:
  - Ensure database connections are properly managed and closed when not in use.

### Conclusion

You have successfully connected to a database using Fiorano's **Database** component. By integrating with a database, you can incorporate data retrieval and storage operations into your integration workflows, enabling more dynamic and data-driven processes.

Understanding how to configure database connections and execute SQL operations is crucial for many real-world integration scenarios, including data synchronization, reporting, and transaction processing.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will build upon what we've learned by integrating a REST service with a database. This will demonstrate how to expose data from a database via a RESTful API, allowing external clients to access and manipulate data through standard HTTP methods.

---

## 2.3 Exposing a REST Service Integrated with a Database

### Objectives

- Learn how to integrate Fiorano's REST Stub component with the Database component.
- Configure a RESTful API that interacts with a database for data retrieval.
- Understand how to map request parameters to database queries.
- Test the integrated service using a REST client like Postman.

### Prerequisites

- **Fiorano Studio (E-Studio)** installed and connected to the Enterprise Server.
- A working **database instance** (e.g., PostgreSQL, MySQL) accessible from your Fiorano environment.
- Familiarity with exposing REST services and connecting to a database in Fiorano (covered in sessions 2.1 and 2.2).
- Relevant **JDBC driver** for your database type added to Fiorano.
- Basic knowledge of **SQL** and RESTful web services.

### Step-by-Step Guide

#### Step 1: Create a New Event Process

1. **Open Fiorano Studio (E-Studio)**:

   - Launch E-Studio and connect to your Enterprise Server if not already connected.

2. **Create a New Event Process**:
   - In the **Event Process Repository**, right-click and select **Add Event Process**.
   - **Name**: Enter a name like `RESTDBIntegration` or `PersonService`.
   - **Category**: Choose an existing category or create a new one (e.g., `FioranoTraining`).
   - Click **Finish** to create the event process.

#### Step 2: Add and Configure the REST Stub Component

1. **Add the REST Stub**:

   - In the **Microservice Palette**, search for **REST Stub**.
   - Drag and drop the **REST Stub** onto the canvas.

2. **Configure the REST Stub**:
   - **Open Configuration**:
     - Double-click on the **REST Stub** component.
   - **Service Name**:
     - Enter a unique **Service Name**, e.g., `PersonService`.
   - **Resources**:
     - **Add Resource**:
       - Click **Add Resource**.
       - **Path**: Enter `/fetch`.
       - This defines the endpoint's path.
       - **ID**: Optionally, enter `FetchResource` for readability.
     - **Add Method**:
       - With the resource selected, click **Add Method**.
       - **Method**: Choose **GET**.
       - **Request Parameters**:
         - Click **Add Parameter**.
         - **Name**: `personId`.
         - **Style**: Select `Query` (since it's a query parameter).
         - **Required**: Check the box to make it mandatory.
     - **Response Representation**:
       - Under **Response**, click **Add Representation**.
       - **Media Type**: Select `application/json`.
   - **Security Settings** (Optional):
     - If you need to secure the service, configure SSL settings.
   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 3: Add and Configure the Database Component

1. **Add the Database Component**:

   - In the **Microservice Palette**, search for **DB** under **Connectors**.
   - Drag and drop the **DB** component onto the canvas.

2. **Ensure JDBC Driver is Added**:

   - **Edit Service Descriptor**:
     - Right-click on the **DB** component and select **Edit**.
     - Go to the **Deployment** tab.
     - Under **Runtime Dependencies**, ensure the JDBC driver for your database is added.
       - Click **Add Library** if needed.
     - **Save** and **Close** the Service Descriptor.

3. **Configure Database Connection**:

   - **Open Configuration**:
     - Double-click on the **DB** component.
   - **Database Configuration**:
     - **DB URL**: Enter your database JDBC URL.
       - For example: `jdbc:postgresql://localhost:5432/mydatabase`.
     - **DB User**: Enter your database username.
     - **DB Password**: Enter your database password.
     - **Test Connection**:
       - Click **Test** to verify the connection.
       - Ensure the message `Connection created successfully` appears.

4. **Configure SQL Operation**:

   - **SQL Configuration**:
     - Click **Add** to create a new SQL operation.
     - **Operation Type**: Select **Select**.
     - **Operation Name**: Enter `FetchPerson`.
   - **Construct Query**:
     - **Refresh Tables**:
       - Click **Refresh Tables** to load database tables.
     - **Select Table**:
       - Expand the schema (e.g., `public` for PostgreSQL) and select your table (e.g., `persons`).
     - **Select Columns**:
       - Check the columns you want to retrieve (e.g., `person_id`, `first_name`, `last_name`).
     - **Where Condition**:
       - Add a **Where** condition to filter by `person_id`.
       - Click **Add Condition**:
         - **Column**: `person_id`.
         - **Operator**: `=`.
         - **Value**: Enter `:${personId}` (using `:${parameter}` syntax).
     - **Parameters**:
       - Ensure `personId` is listed as a parameter.
     - Click **Finish** to save the SQL operation.

5. **Error Handling** (Optional):
   - Configure retry mechanisms and error responses as needed.

#### Step 4: Connect the Components

1. **Draw Routes**:

   - **From REST Stub to Database**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **DB** component.
   - **From Database to REST Stub Response**:
     - Draw a route from the **Output Port** of the **DB** component to the **Response Port** of the **REST Stub**.

2. **Configure Input Mapping to Database Component**:

   - **Map Request Parameter to SQL Parameter**:
     - Right-click on the route from **REST Stub** to **DB** component.
     - Select **Configure Transformation**.
     - In the **Mapper** window:
       - **Source Schema**: Should display the `personId` query parameter.
       - **Target Schema**: Displays the database operation's input parameters.
       - **Mapping**:
         - Map `personId` from the **Source** to `personId` in the **Target**.
     - **Save** the mapping.

3. **Configure Output Mapping to REST Response**:
   - **Map Database Result to JSON Response**:
     - Right-click on the route from **DB** to **REST Stub Response**.
     - Select **Configure Transformation**.
     - In the **Mapper** window:
       - **Source Schema**: Displays the result set from the database.
       - **Target Schema**: Represents the response structure expected by the REST client.
       - **Mapping**:
         - Map database fields (e.g., `person_id`, `first_name`, `last_name`) to appropriate JSON fields.
       - **Set Media Type**:
         - Ensure the **Media Type** is set to `application/json`.
     - **Save** the mapping.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**:

   - Click **Save** to ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:
   - Click **Run Event Process**.
   - Components should turn green, indicating they are running.

#### Step 6: Test the REST Service with Database Integration

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**, e.g., `http://localhost:1856/fetch`.

2. **Test Using Postman**:

   - **Create a New Request** in Postman.
   - **Method**: Set to **GET**.
   - **URL**: Paste the endpoint URL.
   - **Add Query Parameter**:
     - Click on **Params** and add `personId` with a valid ID from your database.
       - For example, `personId=12345`.
   - **Send the Request**:
     - Click **Send**.
   - **Verify the Response**:
     - Ensure the response body contains the correct person data in JSON format.
     - Check the HTTP status code (should be **200 OK**).

3. **Test with Invalid `personId`**:

   - Try a `personId` that does not exist in the database.
   - Verify how the service handles no results.
     - You might need to handle this in your mapping or database operation settings.

4. **Error Handling**:
   - Ensure that appropriate error messages or status codes are returned for invalid requests.

#### Step 7: Implement Optional Enhancements

1. **Add Error Handling**:

   - Modify the mappings to handle cases where no data is returned.
   - Return meaningful messages or HTTP status codes like **404 Not Found**.

2. **Add More Methods (Optional)**:

   - Implement **POST**, **PUT**, or **DELETE** methods in the REST Stub to allow creating, updating, or deleting records.
   - Configure corresponding SQL operations in the Database component.

3. **Secure the Service**:

   - If exposing the service externally, consider adding authentication and SSL.

4. **Logging and Monitoring**:
   - Enable logging on components to monitor service usage and troubleshoot issues.

### Best Practices

- **Security**:

  - Always parameterize SQL queries to prevent SQL injection.
  - Secure the REST service if it exposes sensitive data.

- **Error Handling**:

  - Return appropriate HTTP status codes and messages for different scenarios.
  - Handle unexpected errors gracefully.

- **Performance**:

  - Optimize SQL queries and consider database indexing for faster retrieval.
  - Limit the amount of data returned when possible.

- **Scalability**:

  - Design your services to handle concurrent requests efficiently.

- **Documentation**:
  - Document the API endpoints, parameters, and expected responses for consumers.

### Conclusion

You have successfully created a RESTful API integrated with a database using Fiorano. External clients can now retrieve data from the database via a REST service, demonstrating an end-to-end integration scenario.

Understanding how to combine REST services with database operations is essential for building dynamic, data-driven applications and services. This integration pattern is common in enterprise environments where data access and manipulation are required through standardized web services.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this module, we are exploring various aspects of data transformation using Fiorano, which is essential for integrating systems with different data formats and protocols.

---

## 2.4 Ways to Debug Fiorano Applications

In this session, we will learn about different methods to debug applications in Fiorano. Effective debugging is crucial for identifying and resolving issues within your integration workflows, ensuring that your applications function as intended.

### Objectives

- Understand the various debugging tools and techniques available in Fiorano Studio.
- Learn how to use breakpoints to inspect data flow.
- Utilize component subscriptions to monitor messages.
- Access and interpret logs for troubleshooting.
- Apply best practices for debugging Fiorano applications.

### Prerequisites

- Fiorano Studio (E-Studio) installed and connected to the Enterprise Server.
- Familiarity with creating and running event processes in Fiorano.
- Basic understanding of Fiorano components and routes.

### Overview of Debugging in Fiorano

Fiorano provides several tools and features to aid in the debugging of integration workflows:

1. **Breakpoints**: Pauses message flow at designated points, allowing inspection of message content.
2. **Component Subscriptions**: Monitors messages coming out of specific components.
3. **Viewing Logs**: Accesses output and error logs of components for diagnostic information.
4. **Error Logs and Console Output**: Provides system-level error messages and logs for deeper troubleshooting.

### Step-by-Step Guide

#### Scenario Setup

For demonstration purposes, we'll use a simple event process that exposes a REST service and processes data:

- **REST Stub**: Exposes a RESTful service that accepts requests.
- **Processing Components**: Components that process the incoming data.
- **Routes**: Define the data flow between components.

Assume that you're encountering an issue where the expected response is not being returned to the client.

#### Method 1: Using Breakpoints

Breakpoints allow you to pause the message flow at specific routes and inspect the message content at that point.

1. **Add Breakpoints to Routes**:

   - **Navigate to the Event Process Canvas**:
     - Open your event process in Fiorano Studio.
   - **Select the Route(s)**:
     - Click on the route where you suspect the issue is occurring.
     - You can add breakpoints to multiple routes as needed.
   - **Add Breakpoint**:
     - Right-click on the route and select **Add Breakpoint**.
     - Alternatively, use the **Debugger** toolbar button:
       - Click on the **Debugger** icon (looks like a bug).
       - Select **Add Breakpoints**.
       - Choose routes to add breakpoints to and click **OK**.
   - **Breakpoint Indicator**:
     - The routes with breakpoints will change color (e.g., red) to indicate that a breakpoint is active.

2. **Run the Event Process**:

   - Ensure the event process is saved and running.
   - If it's not running, click **Run Event Process**.

3. **Invoke the Service**:

   - Use a REST client (e.g., Postman) to send a request to your REST service.
   - Provide the necessary URL, method, headers, and body as per your service configuration.

4. **Inspect Messages at Breakpoints**:

   - When a message reaches a breakpoint, the flow will pause.
   - A **Breakpoint Viewer** window will appear, displaying message details:
     - **Payload**: The message content.
     - **Application Context**: Any context variables.
     - **Headers and Properties**: JMS headers and custom properties.

5. **Analyze the Data**:

   - Examine the message content for correctness.
   - Verify that the data matches what you expect at this point in the process.

6. **Proceed or Discard the Message**:

   - **Send**: Click **Send** to allow the message to proceed to the next component.
   - **Discard**: Click **Discard** to stop the message from continuing.
   - **Modify** (Advanced): You can modify the message content before proceeding if needed.

7. **Remove Breakpoints After Debugging**:

   - Once you've identified the issue, remove breakpoints to resume normal operation.
   - Right-click on the route and select **Remove Breakpoint**.
   - Or use the **Debugger** toolbar to manage breakpoints.

#### Method 2: Using Component Subscriptions

Component subscriptions allow you to monitor messages emitted by a specific component without altering the message flow.

1. **Subscribe to a Component's Output Port**:

   - Right-click on the **Output Port** of the component you wish to monitor.
   - Select **Subscribe**.
   - A **Subscription Viewer** window will open.

2. **Invoke the Service**:

   - Send a request to your service as before.

3. **View Messages in the Subscription Viewer**:

   - The messages emitted by the component will appear in the Subscription Viewer.
   - Examine the message content for correctness.

4. **Interpret the Results**:

   - If messages are appearing in the Subscription Viewer, the component is processing messages as expected.
   - If no messages are appearing, there may be an issue with the component's configuration or the flow leading to it.

5. **Unsubscribe After Debugging**:

   - Close the Subscription Viewer or right-click on the port and select **Unsubscribe**.

#### Method 3: Viewing Logs

Logs provide detailed information about the operation of components, including any errors encountered.

1. **Access Component Logs**:

   - Right-click on the component you wish to inspect.
   - Select **View Logs**.

2. **Choose Log Type**:

   - **Output Logs**: Contains standard output messages from the component.
   - **Error Logs**: Contains error messages and stack traces if exceptions occur.

3. **Analyze Logs**:

   - Look for error messages, exceptions, or any anomalies.
   - Logs can provide insights into issues like connection failures, data parsing errors, or configuration problems.

#### Method 4: Checking Error Logs and Console Output

In addition to component logs, Fiorano provides system-level logs and console outputs.

1. **Check Server Logs**:

   - Navigate to the **Fiorano Logs** directory (e.g., `Fiorano\logs`).
   - Review logs like `fes.log` (Enterprise Server) or `fps.log` (Peer Server) for system-level issues.

2. **Console Output**:

   - If you're running servers or components from the command line, monitor the console output.
   - Look for error messages or warnings.

3. **Error Notifications**:

   - Fiorano Studio may display error messages in the **Console** or **Error Log** views.
   - Access these views via the **Window** menu if not visible.

#### Common Debugging Scenarios

1. **No Response from Service**:

   - **Symptoms**: Client receives no response or a timeout.
   - **Potential Causes**:
     - Service not running or listening on the correct port.
     - Network connectivity issues.
   - **Debugging Steps**:
     - Verify the service is running and accessible.
     - Use breakpoints to see if the request reaches the REST Stub.

2. **No Data at a Component**:

   - **Symptoms**: Expected data is not being received by a component.
   - **Potential Causes**:
     - Incorrect mappings or transformations.
     - Filters or selectors blocking messages.
   - **Debugging Steps**:
     - Use breakpoints before and after the component.
     - Check mappings in the **Mapper Project**.

3. **Incorrect Data Transformation**:

   - **Symptoms**: Data is malformed or incorrect after a transformation.
   - **Potential Causes**:
     - Errors in mapping expressions.
     - Incorrect schemas.
   - **Debugging Steps**:
     - Review mappings in the **Mapper**.
     - Use breakpoints to inspect data before and after transformation.

4. **Component Errors**:

   - **Symptoms**: Components throw exceptions or fail to process messages.
   - **Potential Causes**:
     - Misconfiguration of components.
     - External dependencies (e.g., database not accessible).
   - **Debugging Steps**:
     - View component logs for error details.
     - Verify configuration settings.

### Best Practices for Debugging

- **Incremental Testing**: Test your event process incrementally as you build it to identify issues early.
- **Documentation**: Keep detailed notes or comments within your mappings and configurations.
- **Version Control**: Use Fiorano's versioning features to keep track of changes.
- **Consistent Naming**: Use clear and consistent naming conventions for components and routes to simplify debugging.
- **Component Isolation**: Test components individually where possible.
- **Backup Configurations**: Before making significant changes, back up your event process.

### Conclusion

Effective debugging is essential for developing robust Fiorano applications. By utilizing breakpoints, component subscriptions, and logs, you can gain valuable insights into the behavior of your integration workflows and efficiently identify and resolve issues.

Mastering these debugging techniques will enhance your ability to develop, test, and maintain Fiorano applications, leading to more reliable and efficient integration solutions.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we'll delve into the concept of the **Application Context** in Fiorano and explore how it can be used to store and share data across components within an event process.

---

## 2.5 Application Context and Its Usage

### Introduction

The **Application Context** in Fiorano is a mechanism that allows you to store and share data between different components within the same event process. It acts as a shared, in-memory storage area where you can place data that needs to be accessed by multiple components, even if they are not directly connected via routes.

This feature is particularly useful in complex workflows where:

- Data needs to be passed between components that are not directly connected.
- Multiple backend services or databases are involved.
- You need to maintain state or context information throughout the process.

### Objectives

- Understand what the Application Context is and how it functions in Fiorano.
- Learn how to enable and configure the Application Context in an event process.
- Use the Application Context to store and retrieve data across components.
- Apply best practices for effectively utilizing the Application Context.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of data mapping and transformations in Fiorano.
- Completion of previous sessions in Module 2 is recommended.

### Scenario Overview

We will create a scenario where a REST service needs to:

1. Perform an authentication check through a backend service.
2. Use data from the authentication process for subsequent operations.
3. Fetch information from a database using data obtained earlier.

Since we have multiple processes and steps, we need a way to store data that can be accessed by components at different points in the workflow. The Application Context provides this capability.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `AppContextExample`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:
   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **Backend Service (Mock Authentication Service)**:
     - Use any suitable component or a **Sleep** component to simulate an external service.
     - Drag and drop the backend service component onto the canvas.
   - **Database Component**:
     - Drag and drop the **DB** component onto the canvas to interact with the database.
   - **Add Routes**:
     - Connect the components using routes to define the data flow:
       - From **REST Stub** to **Backend Service**.
       - From **Backend Service** to **Database Component**.
       - From **Database Component** back to the **REST Stub** (for response).

#### Step 2: Enable and Configure the Application Context

1. **Enable the Application Context**:

   - Click on the **white space** on the canvas (ensure no component is selected).
   - In the **Properties** pane at the bottom, go to the **Other** tab.
   - Find **Application Context** and set it to **Enabled**.
   - Save the event process.

2. **Configure the Application Context Schema (Optional)**:
   - If you need to store multiple values or complex data structures, you may need to edit the Application Context schema.
   - Click on **Edit Schema** next to the Application Context setting.
   - Define the structure (XSD) for the data you need to store.
     - For example, add elements like `<personID>`, `<authToken>`, etc.
   - Save the schema.

#### Step 3: Store Data in the Application Context

We will store data obtained from the REST request into the Application Context so that it can be used by subsequent components.

1. **Map Data to the Application Context from the REST Stub**:
   - **From REST Stub to Backend Service**:
     - Right-click on the **Output Port** of the **REST Stub** component.
     - Select **Configure Application Context**.
     - In the mapping window, map the required fields from the request to the Application Context.
       - **Source**: Select the field from the request (e.g., `/personID`).
       - **Target**: Map it to the Application Context path (e.g., `/applicationContext/personID`).
   - Click **OK** to save the mapping.

#### Step 4: Retrieve Data from the Application Context in Subsequent Components

1. **Map Data from the Application Context to the Database Component**:
   - **From Backend Service to Database Component**:
     - Right-click on the route connecting the **Backend Service** to the **Database Component**.
     - Select **Configure Transformation**.
     - In the **Mapper**, you will define how data is mapped to the Database Component.
   - **Access the Application Context**:
     - In the **Mapping Functions**, expand **Application Context** to access stored variables.
     - Drag the required variable (e.g., `/personID`) from the Application Context onto the target field in the Database Component's input schema.
     - This maps the value stored earlier to the input of the Database Component.

#### Step 5: Configure the Backend Service and Database Component

1. **Backend Service Configuration**:

   - Since we are simulating an authentication process, you can leave the Backend Service as is or configure it to perform certain operations.
   - Ensure that it processes the request and passes control to the next component.

2. **Database Component Configuration**:
   - Double-click on the **DB** component to configure it.
   - **Database Connection**:
     - Set up the connection parameters (DB URL, username, password).
     - Test the connection to ensure it's successful.
   - **SQL Configuration**:
     - Define the SQL operation (e.g., **Select** statement to fetch person details).
     - Use a parameterized query where `personID` is a parameter.
       - Example: `SELECT * FROM persons WHERE person_id = :personID`.
     - Ensure the parameter name matches the one used in the mapping (from the Application Context).

#### Step 6: Configure the REST Response

1. **Map Database Output to REST Response**:

   - Draw a route from the **Output Port** of the **Database Component** to the **Response Port** of the **REST Stub** component.
   - Right-click on this route and select **Configure Transformation**.
   - In the **Mapper**:
     - Map the fields from the database result to the response structure expected by the client.
     - Ensure the response is in the correct format (e.g., JSON, based on what the REST service is configured to return).

2. **Set Response Media Type**:
   - Ensure that the **Media Type** for the response is set appropriately (e.g., `application/json`).

#### Step 7: Run and Test the Event Process

1. **Save and Run the Event Process**:

   - Click **Save** to save all configurations.
   - Click **Check Resource and Connectivity (CRC)** to verify configurations.
   - Click **Run Event Process** to start the event process.

2. **Test the Service**:

   - Use Postman or another REST client to send a request to the REST service.
   - Provide necessary input (e.g., `personID` in the request body or as a query parameter).
   - Send the request and observe the response.

3. **Verify Data Flow**:
   - Ensure that:
     - The `personID` is correctly stored in the Application Context.
     - The Backend Service processes the request.
     - The Database Component retrieves `personID` from the Application Context and fetches data.
     - The response is returned to the client with the correct data.

#### Step 8: Debugging and Validation

1. **Use Breakpoints**:

   - Set breakpoints on routes or components to pause execution and inspect the data.
   - Check the **Application Context** at each breakpoint to ensure the data is correctly stored and retrieved.

2. **View Logs**:

   - Right-click on components and select **View Logs** to see component logs.
   - Check for any errors or warnings.

3. **Troubleshoot**:
   - If data is not being passed correctly:
     - Check the Application Context mappings.
     - Ensure that variable names and paths match across mappings.
     - Verify that the Application Context is enabled.

### Best Practices

- **Consistent Variable Naming**:
  - Use clear and consistent names for Application Context variables to avoid confusion.
- **Minimal Use of Application Context**:
  - Use the Application Context only when necessary, as overuse can lead to complexity.
- **Security Considerations**:

  - Be cautious when storing sensitive data in the Application Context.
  - Implement security measures if needed.

- **Schema Definition**:

  - Keep the Application Context schema updated and reflective of the data being stored.

- **Performance**:
  - Be mindful of the size and amount of data stored in the Application Context to maintain optimal performance.

### Advantages of Using the Application Context

- **Data Sharing**:

  - Facilitates sharing of data across components that are not directly connected.

- **Decoupling**:

  - Allows for more modular and decoupled designs.

- **State Management**:
  - Useful for maintaining stateful information throughout the event process.

### Summary

In this session, we've learned:

- What the Application Context is and how it functions in Fiorano.
- How to enable the Application Context in an event process.
- How to store and retrieve data using the Application Context across different components.
- Best practices for effectively utilizing the Application Context.

By leveraging the Application Context, you can build more flexible and robust integration workflows, especially in scenarios where data needs to be shared between components that are not directly connected.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will explore the use of **Properties** in Fiorano and understand how they can be utilized to store and share data across components within an event process, similar to the Application Context covered previously.

---

## 2.6 Usage of Property/Properties in Fiorano

### Introduction

**Properties** in Fiorano are metadata associated with messages flowing through the event process. They provide a means to store key-value pairs within a message's header, allowing components to access and manipulate data without altering the message payload. Properties are particularly useful for passing data between components that may not be directly connected or for storing contextual information that doesn't fit within the message body.

### Objectives

- Understand what Properties are and how they function in Fiorano.
- Learn how to set and retrieve Properties within an event process.
- Compare the use of Properties with the Application Context.
- Apply best practices for effectively utilizing Properties.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of data mapping and transformations in Fiorano.
- Completion of previous sessions in Module 2 is recommended.

### Scenario Overview

We will modify an existing event process to use Properties instead of the Application Context for storing and sharing data. The scenario involves:

1. Receiving a REST request containing data.
2. Storing specific data fields as Properties.
3. Accessing these Properties in subsequent components for processing.

This exercise will demonstrate how to set Properties from the message payload and retrieve them later in the workflow.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `PropertiesExample`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:
   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **Processing Component**: Could be a **Mapper** or any other component needed for your logic.
   - **Backend Service**: Simulating an external service or performing operations using the stored Properties.
   - **Add Routes**:
     - Connect the components to define the data flow:
       - From **REST Stub** to **Processing Component**.
       - From **Processing Component** to **Backend Service**.
       - From **Backend Service** back to the **REST Stub** (for response).

#### Step 2: Configure the REST Stub Component

1. **Configure the REST Service**:

   - Double-click on the **REST Stub** to open its configuration.
   - **Service Name**: Enter `PropertyService`.
   - **Resources**:
     - Define the endpoint path and methods (e.g., POST).
     - Configure the request and response representations (e.g., `application/json`).

2. **Define Input Data Structure**:
   - Define the schema for incoming requests, specifying the data fields (e.g., `elementA`, `elementB`) that will be stored as Properties.

#### Step 3: Setting Properties from the Message Payload

1. **Add Transformation on the Route from REST Stub to Processing Component**:

   - Right-click on the route and select **Configure Transformation**.
   - In the **Mapper**, you'll map fields from the message payload to Properties.

2. **Set Properties Using the Mapper**:

   - In the **Target Schema**, select **Properties** (not **Property**).
   - **For each field you want to store as a Property**:
     - **Add a Function**:
       - In the **Mapping Functions**, expand **String Functions** or relevant function category.
       - Use **Set Property** function.
     - **Configure the Function**:
       - **Name**: Enter the name of the Property (e.g., `A` for `elementA`).
       - **Value**: Map from the payload field (e.g., `/elementA`).
     - **Assign to Properties**:
       - Drag the function result to the **Properties** in the Target Schema.

3. **Repeat for Additional Properties**:

   - Repeat the above steps for each field you wish to store (e.g., `elementB` stored as `B`).

4. **Save the Mapping**.

#### Step 4: Accessing Properties in Subsequent Components

1. **Configure the Route to the Backend Service**:

   - Right-click on the route from the **Processing Component** to the **Backend Service**.
   - Select **Configure Transformation**.

2. **Retrieve Properties Using the Mapper**:

   - In the **Source Schema**, you'll access the Properties set earlier.
   - **For each Property you want to retrieve**:
     - In the **Mapping Functions**, expand **JMS Message Functions**.
     - Use **Get String Property** function.
     - **Configure the Function**:
       - **Name**: Enter the name of the Property (e.g., `A` or `B`).
     - **Assign to Target Fields**:
       - Drag the function result to the corresponding input field of the Backend Service's input schema.

3. **Save the Mapping**.

#### Step 5: Configure the Backend Service (Simulated Component)

1. **Configure the Component**:

   - Double-click on the **Backend Service** to configure it.
   - Ensure it accepts the input fields (e.g., `A`, `B`) and processes them accordingly.
   - For demonstration, you can configure it to concatenate the values or perform some calculation.

2. **Prepare the Response**:
   - Ensure the component outputs the processed data, which will be sent back to the client.

#### Step 6: Configure the REST Response

1. **Map Backend Service Output to REST Response**:

   - Draw a route from the **Backend Service** to the **Response Port** of the **REST Stub**.
   - Right-click on this route and select **Configure Transformation**.
   - In the **Mapper**:
     - Map the output fields to the response structure expected by the client.
     - Set the response **Media Type** (e.g., `application/json`).

2. **Save the Mapping**.

#### Step 7: Run and Test the Event Process

1. **Save and Run the Event Process**:

   - Click **Save** to ensure all configurations are saved.
   - Click **Check Resource and Connectivity (CRC)** to verify configurations.
   - Click **Run Event Process**.

2. **Test the Service**:

   - Use a REST client like Postman to send a request to the REST service.
   - **Request**:
     - **Method**: POST.
     - **URL**: The endpoint URL of your REST Stub.
     - **Headers**: Set `Content-Type` to `application/json`.
     - **Body**: Provide JSON payload with `elementA` and `elementB`.
   - **Send the Request** and observe the response.

3. **Verify Data Flow**:
   - Ensure that:
     - The Properties `A` and `B` are correctly set from the payload.
     - The Backend Service retrieves these Properties and processes them.
     - The response contains the expected data.

#### Step 8: Debugging and Validation

1. **Use Breakpoints**:

   - Set breakpoints on routes to pause execution and inspect Properties.
   - In the **Breakpoint Viewer**, check the **Properties** tab to see the key-value pairs.

2. **View Logs**:

   - Right-click on components and select **View Logs** to see logs.
   - Check for any errors or warnings.

3. **Troubleshoot**:
   - If data is not being passed correctly:
     - Verify that Properties are being set and retrieved with the correct names.
     - Ensure mappings are correctly configured.

### Comparison Between Properties and Application Context

- **Scope**:

  - **Properties**: Attached to individual messages; scope is limited to the message as it flows through the event process.
  - **Application Context**: Shared across the entire event process; accessible from any component.

- **Use Cases**:

  - **Properties**: Best for data that is message-specific and needs to be passed along with the message.
  - **Application Context**: Suitable for storing global data or context that needs to be accessed irrespective of individual messages.

- **Performance**:
  - **Properties**: Lightweight and efficient for passing small pieces of data.
  - **Application Context**: Might introduce overhead if used extensively with large data.

### Best Practices

- **Consistent Naming**:

  - Use clear and consistent names for Properties to avoid confusion.

- **Minimal Use of Properties**:

  - Use Properties for small, essential data. Avoid storing large amounts of data as Properties.

- **Avoid Overwriting**:

  - Be cautious not to overwrite Properties unintentionally as they pass through components.

- **Security Considerations**:

  - Do not store sensitive information in Properties unless necessary. Implement security measures if needed.

- **Logging**:
  - If necessary, log the Properties for auditing and troubleshooting, but ensure compliance with data protection policies.

### Advantages of Using Properties

- **Flexibility**:

  - Easily set and retrieve data without altering the message payload.

- **Decoupling**:

  - Components can read Properties without needing direct connections or complex mappings.

- **Simplicity**:
  - Suitable for simple data passing requirements.

### Conclusion

In this session, we've learned:

- What Properties are and how they function in Fiorano.
- How to set and retrieve Properties within an event process.
- When to use Properties versus the Application Context.
- Best practices for effectively utilizing Properties.

By leveraging Properties, you can design more flexible and decoupled integration workflows, passing necessary data efficiently without modifying message payloads.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will explore how to perform data transformation from **JSON to XML**. This is a common requirement when integrating systems that communicate using different data formats, enabling seamless data exchange between them.

---

## 2.7 Data Transformation (JSON to XML)

### Introduction

Converting JSON data to XML format is essential when integrating modern web services that output JSON with legacy systems or services that require XML input. This transformation ensures compatibility and allows systems to communicate effectively despite differences in data representation.

### Objectives

- Learn how to use Fiorano's **JSON Converter** component to transform JSON data to XML.
- Configure the JSON Converter component with the appropriate schema.
- Test the data transformation process within an event process.
- Understand best practices for data transformation between JSON and XML.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of JSON and XML data formats.
- Completion of previous sessions in Module 2 is recommended.

### Scenario Overview

We will design an event process that:

1. Receives JSON data from a REST service.
2. Uses the **JSON Converter** component to convert the JSON payload to XML.
3. Outputs the XML data for further processing or response.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `JSONtoXMLTransformation`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service to accept JSON input.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **JSON Converter**: Converts JSON to XML.
     - Drag and drop the **JSON Converter** component onto the canvas.
   - **Display** (Optional): To display the XML output.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - **From REST Stub to JSON Converter**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **JSON Converter**.
   - **From JSON Converter to Display** (Optional):
     - Draw a route from the **Output Port** of the **JSON Converter** to the **Input Port** of the **Display** component.
   - **From JSON Converter to REST Stub Response Port**:
     - Draw a route from the **Output Port** of the **JSON Converter** to the **Response Port** of the **REST Stub** (to send the XML back as a response).

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter a unique **Service Name**, e.g., `JSONInputService`.

3. **Resources**:

   - **Add Resource**:
     - Click **Add Resource**.
     - **Path**: Enter `/convert`.
     - **ID**: Optionally, enter `ConvertResource`.
   - **Add Method**:
     - With the resource selected, click **Add Method**.
     - **Method**: Choose **POST** (since we'll be sending JSON data in the body).
   - **Request Representation**:
     - Under **Request**, click **Add Representation**.
     - **Media Type**: Select `application/json`.
     - **Schema**: Define the JSON schema if necessary.
   - **Response Representation**:
     - Under **Response**, click **Add Representation**.
     - **Media Type**: Select `application/xml` (since we are returning XML).
   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 3: Configure the JSON Converter Component

1. **Open Configuration**:

   - Double-click on the **JSON Converter** component.

2. **Conversion Direction**:

   - **Convert JSON to XML**: Ensure this is set to **Yes** (since we want to convert from JSON to XML).

3. **Provide Output XSD Schema**:

   - **Output XSD Schema**: You need to provide an XML Schema Definition (XSD) that defines the structure of the resulting XML.

4. **Obtaining the XSD Schema**:

   - **Define the Sample JSON Payload**:
     - For example:
       ```json
       {
         "person": {
           "id": "123",
           "firstName": "John",
           "lastName": "Doe",
           "email": "john.doe@example.com"
         }
       }
       ```
   - **Generate XSD**:
     - Use an online tool or a JSON to XSD converter to produce the corresponding XSD.
     - Alternatively, create the XSD manually if you are familiar with the structure.

5. **Input the XSD Schema**:

   - Copy and paste the XSD content into the **Output XSD Schema** field in the JSON Converter configuration.

6. **Select Root Element**:

   - Click on **Select Root Element**.
   - Choose the root element defined in the XSD (e.g., `person`).

7. **Configure Additional Options** (Optional):

   - **Skip Root Element**: Set to **No** unless you specifically want to skip the root element.
   - **Namespace Configuration**: Specify namespaces if required.

8. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 4: Configure Routes and Mappings

1. **Map Incoming JSON to JSON Converter**:

   - Right-click on the route from **REST Stub** to **JSON Converter**.
   - Select **Configure Transformation**.
   - **Mapper**:

     - **Source Schema**: Represents the incoming JSON payload.
     - **Target Schema**: Represents the input expected by the JSON Converter.
     - **Mapping**:

       - Map the **Text Content** from **JMS Message Functions** to the **JSON Input** of the JSON Converter.
       - This passes the raw JSON payload to the converter.

   - **Save** the mapping.

2. **Map JSON Converter Output to Response**:

   - Right-click on the route from **JSON Converter** to **REST Stub Response Port**.
   - Select **Configure Transformation**.
   - **Mapper**:

     - **Source Schema**: Represents the XML output from the JSON Converter.
     - **Target Schema**: Represents the response structure.
     - **Mapping**:

       - Map the **Text Content** from **JMS Message Functions** to the response.
       - Ensure the **Media Type** is set to `application/xml`.

   - **Save** the mapping.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**:

   - Ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - The components should turn green, indicating they are running.

#### Step 6: Test the REST Service Using Postman

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**, e.g., `http://localhost:1856/convert`.

2. **Create a New Request in Postman**:

   - **Method**: Set to **POST**.
   - **URL**: Paste the endpoint URL.
   - **Headers**:

     - Add `Content-Type` as `application/json`.
     - Add `Accept` as `application/xml` (if you expect XML response).

   - **Body**:

     - Choose **Raw** and select **JSON**.
     - Paste your sample JSON payload, e.g.:
       ```json
       {
         "person": {
           "id": "123",
           "firstName": "John",
           "lastName": "Doe",
           "email": "john.doe@example.com"
         }
       }
       ```

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - Ensure that you receive an XML response corresponding to the JSON data converted.
   - The response should match the structure expected.

   - **Example XML Response**:
     ```xml
     <person>
       <id>123</id>
       <firstName>John</firstName>
       <lastName>Doe</lastName>
       <email>john.doe@example.com</email>
     </person>
     ```

#### Step 7: Troubleshooting

1. **Check for Errors in Transformation**:

   - If the conversion fails, check the **JSON Converter** logs.
   - Common issues include schema mismatches or incorrect JSON structure.

2. **Use Breakpoints and Debugger**:

   - Set breakpoints on routes to inspect the data at each stage.
   - Verify that the payload is correctly passed between components.

3. **Validate Schemas**:

   - Ensure that the XSD accurately reflects the structure of the resulting XML.
   - Test the XSD separately if necessary.

4. **Check Component Configurations**:

   - Verify that the **Convert JSON to XML** option is set to **Yes**.
   - Ensure that the root element is correctly selected.

### Best Practices

- **Schema Management**:

  - Maintain accurate and up-to-date schemas for both JSON and XML representations.
  - Use version control for schema files to track changes.

- **Error Handling**:

  - Implement error handling to manage cases where the input JSON does not match the expected schema.
  - Return meaningful error messages to the client when failures occur.

- **Testing with Various Data**:

  - Test the transformation with different JSON payloads to ensure robustness.
  - Handle optional elements and attributes appropriately in your schemas.

- **Performance Considerations**:

  - Be cautious with very large payloads; test the performance and adjust configurations as necessary.

### Conclusion

You have successfully implemented data transformation from JSON to XML using Fiorano's **JSON Converter** component. This capability is crucial when integrating modern applications that output JSON with legacy systems or services that require XML input, enabling seamless communication between diverse systems.

Understanding how to perform such transformations enhances the interoperability of your integration solutions, allowing you to connect systems regardless of their data format preferences.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will reverse the process we covered in the previous session by transforming data from **XML to JSON**. This is another common requirement in integration scenarios where systems communicate using different data formats.

---

## 2.8 Data Transformation (XML to JSON)

### Introduction

Converting XML data to JSON format is essential when integrating with modern web services and applications that prefer or require JSON. This transformation enables legacy systems or services that output XML to interact seamlessly with newer systems expecting JSON input.

### Objectives

- Learn how to use Fiorano's **JSON Converter** component to transform XML data to JSON.
- Configure the JSON Converter component with the appropriate schema.
- Test the data transformation process within an event process.
- Understand best practices for data transformation between XML and JSON.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of XML and JSON data formats.
- Completion of previous sessions in Module 2 is recommended, especially **2.7 Data Transformation (JSON to XML)**.

### Step-by-Step Guide

#### Scenario Overview

We will design an event process that:

1. Receives XML data from a service (e.g., a SOAP service or database component).
2. Uses the **JSON Converter** component to convert the XML payload to JSON.
3. Outputs the JSON data for further processing or response.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `XMLtoJSONTransformation`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service to accept XML input (or you can simulate an XML input using a **Feeder** component).
     - Drag and drop the **REST Stub** component onto the canvas.
   - **JSON Converter**: Converts XML to JSON.
     - Drag and drop the **JSON Converter** component onto the canvas.
   - **Display** (Optional): To display the JSON output.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - **From REST Stub to JSON Converter**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **JSON Converter**.
   - **From JSON Converter to Display** (Optional):
     - Draw a route from the **Output Port** of the **JSON Converter** to the **Input Port** of the **Display** component.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter a unique **Service Name**, e.g., `XMLInputService`.

3. **Resources**:

   - **Add Resource**:
     - Click **Add Resource**.
     - **Path**: Enter `/convert`.
     - **ID**: Optionally, enter `ConvertResource`.
   - **Add Method**:
     - With the resource selected, click **Add Method**.
     - **Method**: Choose **POST** (since we'll be sending XML data in the body).
   - **Request Representation**:
     - Under **Request**, click **Add Representation**.
     - **Media Type**: Select `application/xml` or `text/xml`.
     - **Schema**: Define the XML schema if necessary.
   - **Response Representation**:
     - Under **Response**, click **Add Representation**.
     - **Media Type**: Select `application/json` (since we are returning JSON).
   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 3: Configure the JSON Converter Component

1. **Open Configuration**:

   - Double-click on the **JSON Converter** component.

2. **Conversion Direction**:

   - **Convert JSON to XML**: Ensure this is set to **No** (since we want to convert from XML to JSON).

3. **Provide Input XSD Schema**:

   - **Input XSD Schema**: You need to provide an XML Schema Definition (XSD) that defines the structure of the incoming XML.

4. **Obtaining the XSD Schema**:

   - **Option 1**: If you have an existing XSD, you can import it.
   - **Option 2**: Generate an XSD from a sample XML payload.
   - **Example XML Payload**:
     ```xml
     <person>
       <id>123</id>
       <firstName>John</firstName>
       <lastName>Doe</lastName>
       <email>john.doe@example.com</email>
     </person>
     ```
   - **Generate XSD**: Use online tools or XML editors to produce the corresponding XSD.

5. **Input the XSD Schema**:

   - Copy and paste the XSD content into the **Input XSD Schema** field in the JSON Converter configuration.

6. **Select Root Element**:

   - Click on **Select Root Element**.
   - Choose the root element defined in the XSD (e.g., `person`).

7. **Configure Additional Options** (Optional):

   - **Skip Root Element**: If your XML has a root element that you wish to skip, set **Skip Root Element** to **Yes**.
   - **Namespace Configuration**: Specify namespaces if your XML uses them.

8. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 4: Configure Routes and Mappings

1. **Map Incoming XML to JSON Converter**:

   - Right-click on the route from **REST Stub** to **JSON Converter**.
   - Select **Configure Transformation**.
   - **Mapper**:

     - **Source Schema**: Represents the incoming XML payload.
     - **Target Schema**: Represents the input expected by the JSON Converter.
     - **Mapping**:

       - Map the **Text Content** from **JMS Message Functions** to the **XML Input** of the JSON Converter.
       - This passes the raw XML payload to the converter.

   - **Save** the mapping.

2. **Map JSON Converter Output to Response**:

   - Right-click on the route from **JSON Converter** to **REST Stub Response Port**.
   - Select **Configure Transformation**.
   - **Mapper**:

     - **Source Schema**: Represents the JSON output from the JSON Converter.
     - **Target Schema**: Represents the response structure.
     - **Mapping**:

       - Map the **Text Content** from **JMS Message Functions** to the response.
       - Ensure the **Media Type** is set to `application/json`.

   - **Save** the mapping.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**:

   - Ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - The components should turn green, indicating they are running.

#### Step 6: Test the REST Service Using Postman

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**, e.g., `http://localhost:1856/convert`.

2. **Create a New Request in Postman**:

   - **Method**: Set to **POST**.
   - **URL**: Paste the endpoint URL.
   - **Headers**:

     - Add `Content-Type` as `application/xml` or `text/xml`.
     - Add `Accept` as `application/json` (if you expect JSON response).

   - **Body**:

     - Choose **Raw** and select **XML** or **Text**.
     - Paste your sample XML payload, e.g.:
       ```xml
       <person>
         <id>123</id>
         <firstName>John</firstName>
         <lastName>Doe</lastName>
         <email>john.doe@example.com</email>
       </person>
       ```

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - Ensure that you receive a JSON response corresponding to the XML data converted.
   - The response should match the structure expected.

   - **Example JSON Response**:
     ```json
     {
       "person": {
         "id": "123",
         "firstName": "John",
         "lastName": "Doe",
         "email": "john.doe@example.com"
       }
     }
     ```

#### Step 7: Troubleshooting

1. **Check for Errors in Transformation**:

   - If the conversion fails, check the **JSON Converter** logs.
   - Common issues include schema mismatches or incorrect XML structure.

2. **Use Breakpoints and Debugger**:

   - Set breakpoints on routes to inspect the data at each stage.
   - Verify that the payload is correctly passed between components.

3. **Validate Schemas**:

   - Ensure that the XSD accurately reflects the structure of the incoming XML.
   - Test the XSD separately if necessary.

4. **Check Component Configurations**:

   - Verify that the **Convert JSON to XML** option is set to **No**.
   - Ensure that the root element is correctly selected.

### Best Practices

- **Schema Management**:

  - Maintain accurate and up-to-date schemas for XML representations.
  - Use version control for schema files to track changes.

- **Error Handling**:

  - Implement error handling to manage cases where the input XML does not match the expected schema.
  - Return meaningful error messages to the client when failures occur.

- **Testing with Various Data**:

  - Test the transformation with different XML payloads to ensure robustness.
  - Handle optional elements and attributes appropriately in your schemas.

- **Performance Considerations**:

  - Be cautious with very large payloads; test the performance and adjust configurations as necessary.

### Conclusion

You have successfully implemented data transformation from XML to JSON using Fiorano's **JSON Converter** component. This capability is crucial when integrating systems that output XML with applications or services that prefer JSON, enabling seamless communication between diverse systems.

Understanding how to perform such transformations enhances the interoperability of your integration solutions, allowing you to connect systems regardless of their data format preferences.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will explore how to perform data transformation from **Text to XML**. Transforming unstructured or semi-structured text data into structured XML format is essential when dealing with data from flat files, logs, or external systems that produce text outputs. This transformation allows for better data manipulation, validation, and integration with systems that require structured data.

---

## 2.9 Data Transformation (Text to XML)

### Introduction

Converting text data to XML involves parsing the text and mapping it to a predefined XML schema. This is particularly useful when integrating with legacy systems, processing log files, or handling data from CSV or delimited files. The **Text to XML** component in Fiorano facilitates this transformation by defining the structure and mapping of the text data to XML elements.

### Objectives

- Learn how to use Fiorano's **Text to XML** component to transform text data into XML format.
- Understand how to create and use flat file schemas to define the structure of the input text.
- Configure the Text to XML component with the appropriate schema and settings.
- Test and validate the data transformation process within an event process.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of text data formats (e.g., CSV, delimited text) and XML.
- Completion of previous sessions in Module 2 is recommended.

### Scenario Overview

We will design an event process that:

1. Receives text data from a source (e.g., a **Feeder** component).
2. Uses the **Text to XML** component to parse the text data and convert it into structured XML based on a predefined schema.
3. Outputs the XML data for further processing or display.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `TextToXMLTransformation`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **Feeder**: Acts as a message source to provide the text data.
     - Drag and drop the **Feeder** component onto the canvas.
   - **Text to XML**: Converts text data to XML.
     - In the **Microservice Palette**, search for **Text to XML** (under **Transformation** category).
     - Drag and drop the **Text to XML** component onto the canvas.
   - **Display**: Used to display the output XML data.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - **From Feeder to Text to XML**:
     - Draw a route from the **Out Port** of the **Feeder** to the **In Port** of the **Text to XML** component.
   - **From Text to XML to Display**:
     - Draw a route from the **Out Port** of the **Text to XML** component to the **In Port** of the **Display** component.

#### Step 2: Define the Flat File Schema

To correctly parse and map the text data, we need to define a flat file schema that describes the structure of the text input.

1. **Understand the Text Data Format**:

   - For example, suppose our text data is a CSV with two fields: `employeeId` and `salary`.
   - Sample text data:
     ```
     101,5000
     102,6000
     103,5500
     ```

2. **Create the Flat File Schema**:

   - **Option 1**: Use the **Fiorano Flat File Schema Editor**.

     - **Access the Flat File Schema Editor**:
       - In E-Studio, go to **Window** > **Open Perspective** > **Other**.
       - Choose **Fiorano Tools** and click **OK**.
     - **Create a New Flat File Schema Project**:
       - In the **Flat File Schemas** view, right-click and select **New Schema Project**.
       - Give it a name, e.g., `EmployeeSchema`.
     - **Define the Schema**:
       - **Root Element**: Set a root element name, e.g., `Employees`.
       - **Record Definition**:
         - Define a record (e.g., `EmployeeRecord`) with the fields matching your text data.
         - **Fields**:
           - `employeeId` of type **String** or **Integer**.
           - `salary` of type **String** or **Decimal**.
       - **Delimiter Configuration**:
         - Set the **Field Delimiter** to `,` (comma).
         - Set the **Record Delimiter** to `\n` (newline).
     - **Save the Schema**.
     - **Export the Schema**:
       - Right-click on the schema and select **Export Schema**.
       - Save it as an `.xsd` file.

   - **Option 2**: Manually Create the XSD Schema.
     - If you prefer, you can manually write the XSD schema corresponding to the text data.

3. **Sample XSD Schema**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
     <xsd:element name="Employees">
       <xsd:complexType>
         <xsd:sequence>
           <xsd:element name="Employee" maxOccurs="unbounded">
             <xsd:complexType>
               <xsd:sequence>
                 <xsd:element name="employeeId" type="xsd:int"/>
                 <xsd:element name="salary" type="xsd:decimal"/>
               </xsd:sequence>
             </xsd:complexType>
           </xsd:element>
         </xsd:sequence>
       </xsd:complexType>
     </xsd:element>
   </xsd:schema>
   ```

#### Step 3: Configure the Text to XML Component

1. **Open Configuration**:

   - Double-click on the **Text to XML** component.

2. **Configure Flat File Schema**:

   - **Flat File Schema**:
     - Click on **Load from File** to import the XSD schema you created.
     - Select the `.xsd` file and open it.
   - **Root Element**:
     - Set the **Target Namespace** if your schema uses one.
     - Click **Select Root Element** and choose the root element (e.g., `Employees`).

3. **Delimiter Configuration**:

   - In **Advanced Settings** or **Properties**, ensure that the delimiters match your text data.
     - **Field Delimiter**: Set to `,` (comma).
     - **Record Delimiter**: Set to `\n` (newline).

4. **Test the Configuration** (Optional):

   - Use the **Test** feature within the component to ensure that the schema and configuration correctly parse a sample input.

5. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 4: Configure the Feeder Component

1. **Prepare Sample Text Data**:

   - Use the sample text data provided earlier or any text data matching your schema.

2. **Input the Text Data**:

   - Double-click on the **Feeder** component.
   - In the **Input Message** window, paste the sample text data:
     ```
     101,5000
     102,6000
     103,5500
     ```

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**:

   - Ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - The components should turn green, indicating they are running.

4. **Send the Text Data**:

   - In the **Feeder** component, click **Send** to send the text data to the Text to XML component.

5. **View the XML Output**:

   - Double-click on the **Display** component.
   - The XML output based on your schema should be displayed.
   - **Example Output**:
     ```xml
     <Employees>
       <Employee>
         <employeeId>101</employeeId>
         <salary>5000</salary>
       </Employee>
       <Employee>
         <employeeId>102</employeeId>
         <salary>6000</salary>
       </Employee>
       <Employee>
         <employeeId>103</employeeId>
         <salary>5500</salary>
       </Employee>
     </Employees>
     ```

#### Step 6: Troubleshooting

1. **Check for Parsing Errors**:

   - If the data does not parse correctly, check the delimiters and ensure they match the input data.
   - Verify that the schema correctly defines the structure matching your text data.

2. **Use Breakpoints and Debugger**:

   - Set breakpoints to inspect the data at each stage.
   - Confirm that the Text to XML component receives the correct text input.

3. **Review Component Logs**:

   - Right-click on the **Text to XML** component and select **View Logs** to check for any errors.

#### Step 7: Optional Enhancements

1. **Handling Headers in Text Data**:

   - If your text data includes a header row, configure the component to skip the header.

     - In the **Text to XML** component settings, set **Header Count** to `1` to ignore the first line.

2. **Processing Large Files**:

   - For large text files, consider using the **File Reader** component to read from a file source.

     - Connect the **File Reader** to the **Text to XML** component.

   - Configure batching or streaming options if necessary.

3. **Error Handling**:

   - Implement error handling to catch and respond to invalid data formats.

   - Use the **Exception Ports** to direct errors to a logging component or error handler.

### Best Practices

- **Consistent Data Formats**:

  - Ensure that the text data is consistent and matches the expected format.

  - Validate the input data before processing if possible.

- **Schema Versioning**:

  - Maintain version control for your flat file schemas.

  - Update schemas as the data structure changes.

- **Performance Considerations**:

  - Test the performance with large datasets.

  - Optimize the configuration for batch processing if needed.

- **Modular Design**:

  - Separate the data parsing logic from business logic for better maintainability.

### Conclusion

You have successfully implemented data transformation from text to XML using Fiorano's **Text to XML** component. This capability is essential when dealing with unstructured or semi-structured text data, allowing you to integrate data from various sources into systems that require structured XML input.

Understanding how to define and use flat file schemas enables you to handle a wide range of text data formats, increasing the flexibility and interoperability of your integration solutions.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will explore transforming structured **XML** data into **Text** format. This transformation is essential when generating flat files, integrating with legacy systems that require text input, or when exporting data for reporting purposes.

---

## 2.10 Data Transformation (XML to Text)

### Introduction

Converting XML data to text involves mapping structured XML elements to a flat text format based on a predefined schema. This process is particularly useful when:

- Generating reports or documents in text format.
- Integrating with systems that require CSV or other delimited text files.
- Creating human-readable data exports.
- Interfacing with legacy systems that do not support XML.

### Objectives

- Learn how to use Fiorano's **XML to Text** component to transform XML data into text format.
- Understand how to create and use flat file schemas to define the mapping from XML to text.
- Configure the XML to Text component with the appropriate schema and settings.
- Test and validate the data transformation process within an event process.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of XML and text data formats (e.g., CSV, delimited text).
- Completion of previous sessions in Module 2 is recommended, especially **2.9 Data Transformation (Text to XML)**.

### Scenario Overview

We will design an event process that:

1. Receives XML data (e.g., from a **Feeder** component or a **REST Stub**).
2. Uses the **XML to Text** component to convert the XML data into text format based on a predefined flat file schema.
3. Outputs the text data for further processing, storage, or display.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `XMLToTextTransformation`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **Feeder**: Acts as a message source to provide the XML data.
     - Drag and drop the **Feeder** component onto the canvas.
   - **XML to Text**: Converts XML to text.
     - In the **Microservice Palette**, search for **XML to Text** (under **Transformation** category).
     - Drag and drop the **XML to Text** component onto the canvas.
   - **Display**: Used to display the output text data.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - **From Feeder to XML to Text**:
     - Draw a route from the **Out Port** of the **Feeder** to the **In Port** of the **XML to Text** component.
   - **From XML to Text to Display**:
     - Draw a route from the **Out Port** of the **XML to Text** component to the **In Port** of the **Display** component.

#### Step 2: Prepare the XML Data and Schema

1. **Sample XML Data**:

   - For example, suppose our XML data represents employee information:
     ```xml
     <Employees>
       <Employee>
         <employeeId>101</employeeId>
         <salary>5000</salary>
       </Employee>
       <Employee>
         <employeeId>102</employeeId>
         <salary>6000</salary>
       </Employee>
     </Employees>
     ```

2. **Create the Corresponding XSD Schema**:

   - The **XML to Text** component requires an XSD schema to understand the structure of the incoming XML.
   - **Sample XSD Schema**:
     ```xml
     <?xml version="1.0" encoding="UTF-8"?>
     <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
       <xsd:element name="Employees">
         <xsd:complexType>
           <xsd:sequence>
             <xsd:element name="Employee" maxOccurs="unbounded">
               <xsd:complexType>
                 <xsd:sequence>
                   <xsd:element name="employeeId" type="xsd:int"/>
                   <xsd:element name="salary" type="xsd:decimal"/>
                 </xsd:sequence>
               </xsd:complexType>
             </xsd:element>
           </xsd:sequence>
         </xsd:complexType>
       </xsd:element>
     </xsd:schema>
     ```
   - Save this schema as an `.xsd` file.

3. **Define the Flat File Schema**:

   - The **Flat File Schema** defines how the XML data maps to the text format.
   - In this case, we can use the same flat file schema we created in **2.9 Data Transformation (Text to XML)**.
   - The flat file schema should specify the format and delimiters for the output text.
     - **Fields**:
       - `employeeId`
       - `salary`
     - **Field Delimiter**: `,` (comma)
     - **Record Delimiter**: `\n` (newline)

#### Step 3: Configure the XML to Text Component

1. **Open Configuration**:

   - Double-click on the **XML to Text** component.

2. **Configure Flat File Schema**:

   - **Flat File Schema**:
     - Click on **Load from File** to import the flat file schema (if you have exported it from the Flat File Schema Editor).
     - Alternatively, paste the flat file schema content directly into the **Flat File Schema** field.
   - **Root Element**:
     - Set the **Target Namespace** if your XML uses one.
     - Click **Select Root Element** and choose the root element from the XSD schema (e.g., `Employees`).

3. **Delimiter Configuration**:

   - Ensure that the delimiters match your desired text output format.
     - **Field Delimiter**: Set to `,` (comma).
     - **Record Delimiter**: Set to `\n` (newline).

4. **Test the Configuration** (Optional):

   - Use the **Test** feature within the component:
     - Click **Test**.
     - Provide sample XML input in the **Message** field.
     - Click **Execute** to see the resulting text output.

5. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 4: Configure the Feeder Component

1. **Input the Sample XML Data**:

   - Double-click on the **Feeder** component.
   - In the **Input Message** window, paste the sample XML data provided earlier.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**:

   - Ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - The components should turn green, indicating they are running.

4. **Send the XML Data**:

   - In the **Feeder** component, click **Send** to send the XML data to the XML to Text component.

5. **View the Text Output**:

   - Double-click on the **Display** component.
   - The text output based on your schema should be displayed.
   - **Example Output**:
     ```
     101,5000
     102,6000
     ```
   - Each line represents a record, with fields separated by commas.

#### Step 6: Troubleshooting

1. **Check for Transformation Errors**:

   - If the data does not transform correctly, verify that the XSD schema matches the XML data structure.
   - Ensure that the flat file schema accurately defines the desired text output format.

2. **Use Breakpoints and Debugger**:

   - Set breakpoints to inspect the data at each stage.
   - Confirm that the XML to Text component receives the correct XML input and produces the expected text output.

3. **Review Component Logs**:

   - Right-click on the **XML to Text** component and select **View Logs** to check for any errors or warnings.

#### Step 7: Optional Enhancements

1. **Formatting Text Output**:

   - Adjust the flat file schema to include additional formatting, such as fixed-width fields or custom delimiters.
   - For example, use a tab (`\t`) as a field delimiter or include headers.

2. **Handling Optional Fields**:

   - Modify the flat file schema and XSD to accommodate optional fields, ensuring the transformation process handles them correctly.

3. **Integrating with File Writer**:

   - If you need to write the text output to a file:
     - Add a **File Writer** component to the canvas.
     - Connect the **Output Port** of the **XML to Text** component to the **Input Port** of the **File Writer**.
     - Configure the **File Writer** to specify the output file location and naming conventions.

4. **Error Handling**:

   - Implement error handling to manage cases where the XML input does not match the expected schema.
   - Use the **Exception Ports** to direct errors to a logging component or error handler.

### Best Practices

- **Schema Consistency**:

  - Ensure that the XSD schema accurately reflects the structure of the XML data.
  - Keep both the XSD and flat file schemas updated and in sync.

- **Testing with Various Data**:

  - Test the transformation process with different XML inputs to ensure robustness.
  - Handle edge cases, such as missing or additional elements.

- **Performance Considerations**:

  - For large datasets, test the performance and optimize configurations as necessary.
  - Consider streaming or batch processing options if dealing with high-volume data.

- **Modular Design**:

  - Keep the transformation logic separate from business logic for better maintainability.
  - Reuse flat file schemas and configurations across different event processes when applicable.

### Conclusion

You have successfully implemented data transformation from XML to text using Fiorano's **XML to Text** component. This capability is essential when generating flat files, integrating with legacy systems that require text input, or exporting data for reporting purposes. By mastering this transformation, you enhance the flexibility of your integration solutions, enabling seamless communication between systems with different data format requirements.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will explore how to modify JSON data within your integration workflows. Modifying JSON payloads is essential when you need to enrich, transform, or restructure incoming data before passing it on to downstream systems or returning it to clients.

---

## 2.11 Data Modification (JSON Payloads)

### Introduction

In many integration scenarios, it's necessary not only to transform data between formats but also to modify the data within the same format. This might involve changing values, adding or removing fields, or restructuring the JSON payload to meet the requirements of a downstream system or API.

In this session, we will learn how to manipulate and modify JSON data within Fiorano by:

- Converting JSON to XML for easy manipulation.
- Modifying the data using mapping and transformation tools.
- Converting the modified data back to JSON.

This approach leverages Fiorano's powerful data transformation capabilities to effectively modify JSON payloads.

### Objectives

- Understand how to modify JSON payloads within Fiorano workflows.
- Learn how to use the **JSON Converter** component for both JSON-to-XML and XML-to-JSON conversions.
- Configure mapping and transformations to modify data.
- Test and validate the data modification process.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of JSON and XML data formats.
- Completion of previous sessions in Module 2 is recommended, particularly:

  - **2.7 Data Transformation (JSON to XML)**
  - **2.8 Data Transformation (XML to JSON)**

### Scenario Overview

We will design an event process that:

1. **Receives a JSON payload** from a REST service.
2. **Converts the JSON payload to XML** using the **JSON Converter** component.
3. **Modifies the XML data** using a **Mapper** component.
4. **Converts the modified XML back to JSON**.
5. **Sends the modified JSON data back** to the client as a response.

This approach allows us to utilize Fiorano's mapping and transformation capabilities to modify data effectively.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `ModifyJSONPayload`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service to accept JSON input.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **JSON Converter** (JSON to XML): Converts JSON to XML for modification.
     - Drag and drop the **JSON Converter** component onto the canvas.
     - Place it after the REST Stub.
   - **Mapper**: Modifies the XML data.
     - Drag and drop the **Mapper** component onto the canvas.
   - **JSON Converter** (XML to JSON): Converts modified XML back to JSON.
     - Drag and drop another **JSON Converter** component onto the canvas.
   - **Connect Components**:

     - Draw routes to connect the components in the following order:

       - **From REST Stub to JSON Converter (JSON to XML)**.
       - **From JSON Converter (JSON to XML) to Mapper**.
       - **From Mapper to JSON Converter (XML to JSON)**.
       - **From JSON Converter (XML to JSON) to REST Stub Response Port**.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter a unique **Service Name**, e.g., `ModifyJSONService`.

3. **Resources**:

   - **Add Resource**:
     - Click **Add Resource**.
     - **Path**: Enter `/modify`.
     - **ID**: Optionally, enter `ModifyResource`.
   - **Add Method**:
     - With the resource selected, click **Add Method**.
     - **Method**: Choose **POST**.
   - **Request Representation**:
     - Under **Request**, click **Add Representation**.
     - **Media Type**: Select `application/json`.
   - **Response Representation**:
     - Under **Response**, click **Add Representation**.
     - **Media Type**: Select `application/json`.
   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 3: Configure the First JSON Converter (JSON to XML)

1. **Open Configuration**:

   - Double-click on the first **JSON Converter** component.

2. **Conversion Direction**:

   - Ensure **Convert JSON to XML** is set to **Yes**.

3. **Provide Output XSD Schema**:

   - **Output XSD Schema**: Define the XML Schema Definition (XSD) corresponding to the JSON payload you expect to receive.

4. **Obtaining the XSD Schema**:

   - **Define Sample JSON Payload**:

     ```json
     {
       "employee": {
         "id": "123",
         "firstName": "John",
         "lastName": "Doe",
         "email": "john.doe@example.com",
         "department": "Sales"
       }
     }
     ```

   - **Generate XSD**:

     - Use an online tool or software like Altova XMLSpy to convert the sample JSON to an XSD schema.
     - Alternatively, manually create the XSD if you are familiar with schema definitions.

5. **Import the XSD Schema**:

   - Paste the XSD content into the **Output XSD Schema** field in the JSON Converter configuration.

6. **Select Root Element**:

   - Click **Select Root Element**.
   - Choose the appropriate root element (e.g., `employee`).

7. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 4: Configure the Mapper Component

1. **Define the Transformation Logic**:

   - The **Mapper** will be used to modify the XML data.
   - Examples of possible modifications:

     - **Add a new element**: e.g., `fullName`, by concatenating `firstName` and `lastName`.
     - **Modify an existing element**: e.g., change the value of `department`.
     - **Remove an element**: e.g., exclude `email` from the data.

2. **Configure the Mapper**:

   - Right-click on the route between the **JSON Converter (JSON to XML)** and the **Mapper**.
   - Select **Configure Transformation**.
   - In the **Mapper** window:

     - **Source Schema**: Should display the XML structure from the JSON Converter.
     - **Target Schema**: Can be the same as the source or modified if the structure changes.

   - **Implement the Modifications**:

     - **Adding a New Element (fullName)**:

       - In **Transformation Components**, use the **Concat** function under **String Functions**.
       - Concatenate `firstName` and `lastName` with a space in between.
       - Map the result to a new element `fullName` in the target schema.

     - **Modifying an Element (department)**:

       - Use a **String Constant** function to set a new value (e.g., change `department` to `Marketing`).
       - Map it to the `department` element in the target schema.

     - **Removing an Element (email)**:

       - Simply do not map the `email` element from the source schema to the target schema.

   - **Save the Mapping**.

#### Step 5: Configure the Second JSON Converter (XML to JSON)

1. **Open Configuration**:

   - Double-click on the second **JSON Converter** component.

2. **Conversion Direction**:

   - Ensure **Convert JSON to XML** is set to **No**.

3. **Provide Input XSD Schema**:

   - The **Input XSD Schema** should match the structure of the modified XML output from the Mapper.

     - If you added or removed elements, update the XSD accordingly.

4. **Import the Modified XSD Schema**:

   - Paste the updated XSD into the **Input XSD Schema** field.

5. **Select Root Element**:

   - Click **Select Root Element**.
   - Choose the appropriate root element (e.g., `employee`).

6. **Configure Additional Options**:

   - **Skip Root Element**: Set to **Yes** or **No** depending on your requirements.
   - **Other Settings**: Adjust if necessary.

7. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 6: Configure REST Response Mapping

1. **Map JSON Converter Output to REST Response**:

   - Right-click on the route between the **JSON Converter (XML to JSON)** and the **REST Stub Response Port**.
   - Select **Configure Transformation**.

2. **Mapping**:

   - **Source Schema**: Represents the JSON output from the second JSON Converter.
   - **Target Schema**: Represents the expected response structure.

   - **Mapping**:

     - Map the root element from the source schema to the target schema.
     - Ensure that the modified data is correctly structured in the response.

3. **Set Media Type**:

   - Ensure the **Media Type** is set to `application/json`.

4. **Save the Mapping**.

#### Step 7: Run and Test the Event Process

1. **Save the Event Process**:

   - Click **Save** to ensure all configurations are stored.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

#### Step 8: Test the Service Using Postman

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**, e.g., `http://localhost:1856/modify`.

2. **Create a New Request in Postman**:

   - **Method**: Set to **POST**.
   - **URL**: Paste the endpoint URL.
   - **Headers**:
     - **Content-Type**: `application/json`.
     - **Accept**: `application/json`.
   - **Body**:

     - Choose **Raw** and set the type to **JSON**.
     - Paste the sample JSON payload:

       ```json
       {
         "employee": {
           "id": "123",
           "firstName": "John",
           "lastName": "Doe",
           "email": "john.doe@example.com",
           "department": "Sales"
         }
       }
       ```

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - Ensure that the response contains the modified JSON data.
   - Verify that:

     - The `fullName` field has been added (e.g., `"fullName": "John Doe"`).
     - The `department` value has changed to `Marketing`.
     - The `email` field has been removed.

   - **Example Modified Response**:

     ```json
     {
       "employee": {
         "id": "123",
         "firstName": "John",
         "lastName": "Doe",
         "fullName": "John Doe",
         "department": "Marketing"
       }
     }
     ```

#### Step 9: Troubleshooting

1. **Use Breakpoints and Debugger**:

   - Set breakpoints on routes to pause execution and inspect data at each stage.
   - Check the transformation results after each component.

2. **View Logs**:

   - Right-click on components and select **View Logs** to see any error messages or warnings.

3. **Validate Schemas and Mappings**:

   - Ensure that the XSD schemas match the data structures after each transformation.
   - Verify that mappings in the Mapper are correctly configured.

4. **Check Component Configurations**:

   - Make sure the **JSON Converter** components have the correct conversion direction settings.
   - Verify that root elements are correctly selected.

### Best Practices

- **Schema Management**:

  - Keep your XSD schemas updated and version-controlled.
  - Document changes to schemas when modifying data structures.

- **Mapping Clarity**:

  - Use clear and consistent naming conventions in the Mapper.
  - Comment complex mappings within the Mapper for future reference.

- **Performance Considerations**:

  - Be aware of the overhead introduced by multiple conversions.
  - Optimize mappings and component configurations for performance.

- **Error Handling**:

  - Implement error handling mechanisms to catch and manage exceptions.
  - Return meaningful and user-friendly error messages to the client.

- **Testing**:

  - Test the workflow with various data inputs to ensure robustness.
  - Include edge cases and invalid data scenarios in your tests.

### Conclusion

You have successfully learned how to modify JSON payloads within Fiorano by converting JSON to XML, performing modifications using the Mapper component, and converting the modified data back to JSON. This technique allows you to leverage Fiorano's powerful data transformation and mapping capabilities to meet specific data manipulation requirements within your integration workflows.

By mastering data modification within the same format, you can:

- Enrich data with additional information.
- Remove or alter sensitive data fields.
- Adapt data structures to meet the requirements of downstream systems or APIs.

This enhances the flexibility and functionality of your integration solutions, allowing you to handle complex data transformation and manipulation scenarios effectively.

---

You're absolutely correct, and I apologize for the oversight. Let's proceed with **2.12 Data Modification (XML Payloads)**.

---

## Module 2: Data Transformation

Welcome back to Module 2 of the Fiorano Product Training series. In this session, we will explore how to modify XML data within your integration workflows. Modifying XML payloads is essential when you need to enrich, transform, or restructure incoming data before passing it on to downstream systems or returning it to clients.

---

## 2.12 Data Modification (XML Payloads)

### Introduction

In enterprise integration scenarios, it's often necessary to modify XML data to meet the requirements of different systems or to enrich data with additional information. Modifying XML payloads allows you to:

- Add, remove, or modify elements and attributes.
- Transform the structure of the XML data.
- Enrich the data with additional information from other sources.
- Adapt the data to match the schema expected by a destination system.

In this session, we will learn how to manipulate and modify XML data within Fiorano by using the **XSLT** (Extensible Stylesheet Language Transformations) component. XSLT is a powerful language designed for transforming XML documents into other XML documents, or other formats such as HTML or plain text.

### Objectives

- Understand how to modify XML payloads within Fiorano workflows.
- Learn how to use the **XSLT** component to perform transformations on XML data.
- Configure XSLT transformations to modify data as required.
- Test and validate the data modification process.
- Apply best practices for working with XSLT and XML transformations.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of XML and XSLT.
- Completion of previous sessions in Module 2 is recommended.

### Scenario Overview

We will design an event process that:

1. **Receives an XML payload** from a REST or SOAP service.
2. **Uses the XSLT component** to transform and modify the XML data.
3. **Outputs the modified XML data** to be sent back to the client or to a downstream system.

This approach allows us to leverage Fiorano's XSLT component to apply complex transformations and modifications to XML data.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `ModifyXMLPayload`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service to accept XML input.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **XSLT**: Transforms and modifies the XML data.
     - Drag and drop the **XSLT** component onto the canvas.
   - **Connect Components**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **XSLT** component.
     - Draw a route from the **Output Port** of the **XSLT** component to the **Response Port** of the **REST Stub**.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter a unique **Service Name**, e.g., `ModifyXMLService`.

3. **Resources**:
   - **Add Resource**:
     - Click **Add Resource**.
     - **Path**: Enter `/modifyxml`.
     - **ID**: Optionally, enter `ModifyXMLResource`.
   - **Add Method**:
     - With the resource selected, click **Add Method**.
     - **Method**: Choose **POST**.
   - **Request Representation**:
     - Under **Request**, click **Add Representation**.
     - **Media Type**: Select `application/xml` or `text/xml`.
   - **Response Representation**:
     - Under **Response**, click **Add Representation**.
     - **Media Type**: Select `application/xml` or `text/xml`.
   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 3: Prepare the XSLT Stylesheet

1. **Define the Transformation Requirements**:

   - Determine what modifications need to be made to the XML data.
   - Examples of possible modifications:
     - **Add a new element**: e.g., add a `<fullName>` element by concatenating `<firstName>` and `<lastName>`.
     - **Modify an existing element**: e.g., change the value of `<status>` based on certain conditions.
     - **Remove an element**: e.g., exclude the `<password>` element from the data.

2. **Create the XSLT Stylesheet**:

   - Use an XML editor or a text editor to create the XSLT file.

   - **Sample Input XML**:

     ```xml
     <user>
       <id>123</id>
       <firstName>John</firstName>
       <lastName>Doe</lastName>
       <email>john.doe@example.com</email>
       <password>securepassword</password>
       <status>inactive</status>
     </user>
     ```

   - **Sample XSLT Stylesheet** (`modify_user.xsl`):

     ```xml
     <?xml version="1.0" encoding="UTF-8"?>
     <xsl:stylesheet version="1.0"
       xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

       <!-- Identity template to copy all nodes by default -->
       <xsl:template match="@* | node()">
         <xsl:copy>
           <xsl:apply-templates select="@* | node()"/>
         </xsl:copy>
       </xsl:template>

       <!-- Template to remove the <password> element -->
       <xsl:template match="password"/>

       <!-- Template to add a <fullName> element -->
       <xsl:template match="user">
         <xsl:copy>
           <!-- Copy existing child nodes -->
           <xsl:apply-templates select="@* | node()"/>
           <!-- Add new <fullName> element -->
           <fullName>
             <xsl:value-of select="concat(firstName, ' ', lastName)"/>
           </fullName>
         </xsl:copy>
       </xsl:template>

       <!-- Template to modify the <status> element -->
       <xsl:template match="status">
         <status>
           <!-- Change status to 'active' -->
           <xsl:text>active</xsl:text>
         </status>
       </xsl:template>
     </xsl:stylesheet>
     ```

   - **Explanation**:
     - The identity template copies all nodes and attributes by default.
     - The template matching `<password>` removes it by not copying it.
     - The template matching `<user>` adds a new `<fullName>` element.
     - The template matching `<status>` modifies its value.

3. **Save the XSLT Stylesheet**:

   - Save the file as `modify_user.xsl` and place it in an accessible directory.

#### Step 4: Configure the XSLT Component

1. **Open Configuration**:

   - Double-click on the **XSLT** component.

2. **Load the XSLT Stylesheet**:

   - In the **XSLT Configuration** section, click on **Load from File** to import the XSLT file.
   - Browse to the location of `modify_user.xsl` and select it.

3. **Configure Source and Target Namespaces (Optional)**:

   - If your XML uses namespaces, configure them appropriately.

4. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**:

   - Ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - The components should turn green, indicating they are running.

#### Step 6: Test the Service Using Postman

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**, e.g., `http://localhost:1856/modifyxml`.

2. **Create a New Request in Postman**:

   - **Method**: Set to **POST**.
   - **URL**: Paste the endpoint URL.
   - **Headers**:
     - **Content-Type**: `application/xml` or `text/xml`.
     - **Accept**: `application/xml` or `text/xml`.
   - **Body**:

     - Choose **Raw** and set the type to **XML**.
     - Paste the sample input XML:

       ```xml
       <user>
         <id>123</id>
         <firstName>John</firstName>
         <lastName>Doe</lastName>
         <email>john.doe@example.com</email>
         <password>securepassword</password>
         <status>inactive</status>
       </user>
       ```

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - Examine the response to ensure that the XML data has been modified as expected.

   - **Expected Modified XML**:

     ```xml
     <user>
       <id>123</id>
       <firstName>John</firstName>
       <lastName>Doe</lastName>
       <email>john.doe@example.com</email>
       <status>active</status>
       <fullName>John Doe</fullName>
     </user>
     ```

   - **Modifications**:
     - The `<password>` element has been removed.
     - The `<status>` element's value has been changed to `active`.
     - A new `<fullName>` element has been added.

#### Step 7: Troubleshooting

1. **Use Breakpoints and Debugger**:

   - Set breakpoints on routes to inspect the XML data before and after the XSLT transformation.
   - Ensure that the XSLT component is receiving the correct input and producing the expected output.

2. **View Logs**:

   - Right-click on the **XSLT** component and select **View Logs** to check for any errors or warnings.

3. **Validate the XSLT Stylesheet**:

   - Ensure that the XSLT is well-formed and valid.
   - Use an XSLT debugger or validator to check for syntax errors.

4. **Check Component Configurations**:

   - Verify that the XSLT file is correctly loaded in the component.
   - Ensure any namespace configurations are correctly set.

#### Step 8: Optional Enhancements

1. **Parameterizing the XSLT Stylesheet**:

   - Pass parameters to the XSLT stylesheet from the event process if dynamic values are required.
   - Configure the **XSLT Parameters** in the component's configuration.

2. **Using XSLT Version 2.0 or 3.0**:

   - If advanced XSLT features are needed, ensure that the component supports the required XSLT version.
   - Fiorano's XSLT component might need specific configuration or updates to support newer XSLT versions.

3. **Handling Namespaces**:

   - If the input XML uses namespaces, ensure that the XSLT handles them appropriately.
   - Declare namespaces in the XSLT stylesheet and match elements with namespace prefixes.

### Best Practices

- **Modular XSLT Design**:

  - Break down complex transformations into templates and functions for better maintainability.
  - Reuse templates where possible.

- **Version Control**:

  - Keep your XSLT stylesheets under version control to track changes and maintain history.

- **Performance Optimization**:

  - Test the performance of your XSLT transformations, especially with large XML documents.
  - Optimize XSLT code by avoiding unnecessary processing and using efficient XPath expressions.

- **Error Handling**:

  - Implement error handling in the XSLT to manage unexpected input data.
  - Use `<xsl:message>` and `<xsl:variable>` for debugging purposes.

- **Testing with Various Data**:

  - Validate the transformation with different XML inputs to ensure robustness.
  - Include edge cases and invalid data scenarios in your tests.

### Conclusion

You have successfully learned how to modify XML payloads within Fiorano using the **XSLT** component. By applying XSLT transformations, you can:

- Manipulate and enrich XML data to meet specific requirements.
- Perform complex data transformations that might not be achievable with basic mapping tools.
- Adapt data structures to match the expectations of downstream systems or clients.

Mastering XML modifications with XSLT enhances your ability to handle advanced integration scenarios, making your solutions more flexible and powerful.

---

# Module 3: Database, Web Services, and File Handling

Welcome to Module 3 of the Fiorano Product Training series. In this module, we will explore advanced integration techniques involving databases, web services, and file handling. These are essential components for building robust enterprise integration solutions, enabling communication and data exchange across various systems and platforms.

---

## 3.1 Funclets and Custom Funclets (Creation and Usage)

### Introduction

**Funclets** in Fiorano are reusable functions that can be applied within data transformation mappings to perform operations on data. They are available in the **Mapper** component and can be used to manipulate data as it flows through your integration processes.

Sometimes, the built-in funclets are not sufficient to meet specific data manipulation requirements. In such cases, Fiorano allows you to create **Custom Funclets** using JavaScript or Java code. Custom funclets extend the platform's capabilities, providing you with the flexibility to implement complex logic within your data transformations.

### Objectives

- Understand what funclets are and how they are used in Fiorano.
- Learn how to create custom funclets using JavaScript or Java.
- Integrate custom funclets into your data transformation mappings.
- Test and validate the functionality of custom funclets within an event process.
- Apply best practices for creating and using custom funclets.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of data mapping and transformation in Fiorano.
- Knowledge of JavaScript or Java programming languages.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process where:

1. A REST service receives a JSON payload containing data.
2. A custom funclet is used to extract and manipulate specific elements from the JSON payload.
3. The modified data is sent to a database component for storage or further processing.
4. The process demonstrates how custom funclets can be created and utilized within the Mapper.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `CustomFuncletExample`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service to accept JSON input.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **Mapper**: Will use the custom funclet.
     - Drag and drop the **Mapper** component onto the canvas.
   - **Database Component**: For storing or processing the modified data.
     - Drag and drop the **DB** component onto the canvas.
   - **Connect Components**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **Mapper**.
     - Draw a route from the **Output Port** of the **Mapper** to the **Input Port** of the **DB** component.
     - Optionally, draw a route from the **DB** component to the **Response Port** of the **REST Stub** to send a response back to the client.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter a unique **Service Name**, e.g., `CustomFuncletService`.

3. **Resources**:

   - **Add Resource**:

     - Click **Add Resource**.
     - **Path**: Enter `/process`.
     - **ID**: Optionally, enter `ProcessResource`.

   - **Add Method**:

     - With the resource selected, click **Add Method**.
     - **Method**: Choose **POST**.

   - **Request Representation**:

     - Under **Request**, click **Add Representation**.
     - **Media Type**: Select `application/json`.

   - **Response Representation** (Optional):

     - Under **Response**, you can define the response media type (e.g., `application/json`).

   - **Finish Configuration**:

     - Click **Finish** to save.

#### Step 3: Create a Custom Funclet

1. **Open the Mapper Between REST Stub and Mapper Component**:

   - Right-click on the route between the **REST Stub** and the **Mapper** component.
   - Select **Configure Transformation**.

2. **Access User-Defined Functions**:

   - In the **Mapper** window, click on the **Functions** menu.
   - Select **Create or Edit User Defined Functions**.

3. **Add a New Custom Funclet**:

   - In the **User Defined Functions** dialog:

     - Click **Add** to create a new function.
     - **Name**: Enter a meaningful name for the funclet, e.g., `ExtractCity`.

4. **Define the Function**:

   - **Language**: Choose **JavaScript** or **Java**.

   - **JavaScript Example**:

     ```javascript
     function ExtractCity(jsonString) {
       var jsonData = JSON.parse(jsonString);
       return jsonData.address.city;
     }
     ```

     - This function takes a JSON string, parses it, and extracts the `city` value from the `address` field.

   - **Java Example**:

     - If you prefer Java, you can write the function accordingly.

   - **Configure Function Signature**:

     - Define input parameters and return type.
     - For example:

       - **Parameters**: `jsonString` of type `String`.
       - **Return Type**: `String`.

5. **Finish and Save the Function**:

   - Click **OK** to save the function.
   - The new custom funclet `ExtractCity` should now appear under **User Defined Functions** in the **Mapping Functions** pane.

#### Step 4: Use the Custom Funclet in Mapping

1. **Map the Incoming Data to the Function**:

   - In the **Source Schema**, select the element representing the entire JSON payload (e.g., `Text`).

   - Drag the **Text** element to the **jsonString** parameter in the **ExtractCity** function.

2. **Map the Function Output to the Target Schema**:

   - In the **Target Schema**, identify the field where you want to map the extracted city value (e.g., `/address/city` or a database input field).

   - Drag the result of the **ExtractCity** function to the target field.

3. **Map Other Fields as Needed**:

   - Map other fields from the incoming JSON to the target schema as required.

4. **Save the Mapping**:

   - Click **Save** in the **Mapper** window.

#### Step 5: Configure the Database Component

1. **Database Connection**:

   - Double-click on the **DB** component.
   - In the **Database Configuration** section:
     - **DB URL**: Enter your database JDBC URL.
     - **DB User**: Enter your database username.
     - **DB Password**: Enter your database password.
   - **Test Connection**:
     - Click **Test** to verify the connection.

2. **SQL Configuration**:

   - Navigate to the **SQL Configuration** tab.
   - Click **Add** to create a new SQL operation.

     - **Operation Type**: Choose **Insert** (for storing data) or any other appropriate operation.
     - **Operation Name**: Provide a name, e.g., `InsertData`.

   - **Configure the SQL Statement**:

     - **Table**: Select the table where data will be inserted.
     - **Columns**: Select the columns corresponding to the data you're inserting (e.g., `city`).

   - **Parameterize the Query**:

     - Ensure that the parameters (e.g., `city`) are correctly defined and match the fields mapped in the Mapper.

   - **Finish** the configuration.

#### Step 6: Connect the Database Component and Configure Response

1. **Connect Database Output to REST Response (Optional)**:

   - If you wish to send a response back to the client, draw a route from the **Output Port** of the **DB** component to the **Response Port** of the **REST Stub**.

2. **Configure Response Mapping**:

   - Right-click on the route and select **Configure Transformation**.
   - Define any response data you wish to send back to the client, such as a success message or data from the database.

#### Step 7: Run and Test the Event Process

1. **Save and Run the Event Process**:

   - Click **Save** to ensure all configurations are saved.
   - Click **Check Resource and Connectivity (CRC)** to validate configurations.
   - Click **Run Event Process**.

2. **Test the Service Using Postman**:

   - **Endpoint URL**:

     - Right-click on the **REST Stub** component and select **View WADL**.
     - Copy the endpoint URL (e.g., `http://localhost:1856/process`).

   - **Create a New Request in Postman**:

     - **Method**: Set to **POST**.
     - **URL**: Paste the endpoint URL.
     - **Headers**:
       - **Content-Type**: `application/json`.
     - **Body**:

       - Provide a JSON payload. For example:

         ```json
         {
           "name": "Jane Smith",
           "address": {
             "street": "123 Main St",
             "city": "New York",
             "state": "NY"
           }
         }
         ```

   - **Send the Request** and observe the response (if any).

3. **Verify the Data in the Database**:

   - Check your database to ensure that the `city` value (`"New York"`) was correctly extracted and inserted.

#### Step 8: Troubleshooting

1. **Check for Errors**:

   - If data is not being processed as expected, check the logs.
   - Right-click on components and select **View Logs** to see error and output logs.

2. **Debug the Custom Funclet**:

   - Ensure that the custom funclet code is correct.
   - Add logging statements within the custom funclet (if possible) to output variables for debugging.

3. **Use Breakpoints and Debugger**:

   - Set breakpoints on routes to inspect data at each stage.
   - Verify that the data flowing into and out of the Mapper is as expected.

### Best Practices

- **Funclet Naming and Documentation**:

  - Use clear and descriptive names for custom funclets.
  - Document the purpose, parameters, and expected behavior within the code or in accompanying documentation.

- **Error Handling**:

  - Include error handling within the custom funclet to manage unexpected data or exceptions.
  - Return meaningful error messages or default values as appropriate.

- **Reusable Functions**:

  - Create funclets that are generic and reusable across multiple mappings and event processes.
  - Store common funclets in a shared repository or library.

- **Performance Considerations**:

  - Optimize the funclet code for performance, especially if it will be executed frequently or on large datasets.

- **Testing**:

  - Thoroughly test custom funclets with various inputs to ensure reliability.
  - Include unit tests if possible.

- **Security**:

  - Ensure that the funclet code does not introduce security vulnerabilities.
  - Validate and sanitize inputs as necessary.

### Conclusion

You have successfully learned how to create and use custom funclets in Fiorano to extend the data transformation capabilities of your integration workflows. Custom funclets allow you to implement complex data manipulation logic that may not be achievable with built-in functions alone.

By leveraging custom funclets, you can:

- Tailor data transformations to meet specific business requirements.
- Enhance the flexibility and functionality of your integration solutions.
- Reuse code and logic across multiple mappings and processes, improving efficiency and maintainability.

Mastering the creation and usage of custom funclets is a valuable skill that enhances your ability to develop sophisticated and customized integration solutions with Fiorano.

---

## Module 3: Database, Web Services, and File Handling

Welcome back to Module 3 of the Fiorano Product Training series. In this module, we delve into advanced integration techniques involving databases, web services, and file handling. These are critical components for building robust enterprise integration solutions, enabling seamless communication and data exchange across diverse systems and platforms.

---

## 3.2 Integrating with a Database using Stored Procedures

### Introduction

**Stored procedures** are precompiled sets of SQL statements stored in a database that perform a specific task. They encapsulate complex database operations, provide better performance through precompilation, and enhance security by controlling access to data. Integrating with stored procedures allows you to leverage these benefits within your Fiorano workflows, enabling advanced database interactions such as complex queries, transactions, and data manipulation.

In this session, we will learn how to configure Fiorano's **Database** component to interact with stored procedures, enabling your event processes to execute these procedures as part of your integration solutions.

### Objectives

- Understand what stored procedures are and their advantages in database operations.
- Learn how to configure the **Database** component in Fiorano to execute stored procedures.
- Create an event process that integrates with a database using stored procedures.
- Test and validate the stored procedure integration.
- Apply best practices for using stored procedures within Fiorano workflows.

### Prerequisites

- Familiarity with Fiorano Studio (E-Studio) and creating event processes.
- Basic understanding of databases, SQL, and stored procedures.
- A working knowledge of integrating databases in Fiorano (covered in session **2.2 Connecting to a Database**).
- Access to a database (e.g., PostgreSQL, MySQL, SQL Server) with stored procedures defined.
- Relevant JDBC driver for your database type added to Fiorano.

### Scenario Overview

We will create an event process where:

1. A REST service accepts input data from a client.
2. The input data is passed to a stored procedure in the database using the **Database** component.
3. The stored procedure performs operations (e.g., inserting data, updating records, or complex computations).
4. The result is retrieved and sent back to the client as a response.

This scenario demonstrates how to configure and use stored procedures within a Fiorano workflow.

### Step-by-Step Guide

#### Step 1: Prepare the Database with a Stored Procedure

Before configuring Fiorano, ensure that your database has a stored procedure that can be called.

1. **Create a Stored Procedure**:

   - **Example (PostgreSQL)**:

     ```sql
     CREATE OR REPLACE FUNCTION fetch_employee_salary(emp_id INTEGER)
     RETURNS NUMERIC AS $$
     DECLARE
       emp_salary NUMERIC;
     BEGIN
       SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
       RETURN emp_salary;
     END;
     $$ LANGUAGE plpgsql;
     ```

   - This stored procedure `fetch_employee_salary` accepts an `employee_id` as input and returns the `salary` of the employee.

2. **Test the Stored Procedure**:

   - Run a test query to ensure the stored procedure works as expected:

     ```sql
     SELECT fetch_employee_salary(101);
     ```

#### Step 2: Set Up the Event Process Canvas in Fiorano Studio

1. **Create a New Event Process**:

   - Open Fiorano Studio (E-Studio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `DatabaseStoredProcedureIntegration`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service to accept input.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **Database Component**: To execute the stored procedure.
     - In the **Microservice Palette**, find the **DB** component under **Connectors**.
     - Drag and drop the **DB** component onto the canvas.
   - **Connect Components**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **DB** component.
     - Draw a route from the **Output Port** of the **DB** component to the **Response Port** of the **REST Stub** to send results back to the client.

#### Step 3: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `EmployeeSalaryService`.

3. **Resources**:

   - **Add Resource**:

     - Click **Add Resource**.
     - **Path**: Enter `/employee/salary`.
     - **ID**: Optionally, enter `EmployeeSalaryResource`.

   - **Add Method**:

     - With the resource selected, click **Add Method**.
     - **Method**: Choose **GET** (since we are fetching data).

     - **Request Parameters**:

       - Click **Add Parameter**.
         - **Name**: `empId`.
         - **Style**: Select `Query` (since it's a query parameter).
         - **Type**: `Integer`.
         - **Required**: Check the box to make it mandatory.

   - **Response Representation**:

     - Under **Response**, click **Add Representation**.
     - **Media Type**: Select `application/json`.

4. **Finish Configuration**:

   - Click **Finish** to save.

#### Step 4: Configure the Database Component

1. **Ensure JDBC Driver is Added**:

   - Right-click on the **DB** component and select **Edit**.
   - In the **Service Descriptor**, go to the **Deployment** tab.
   - Under **Runtime Dependencies**, ensure the JDBC driver for your database is added.
     - Add the JAR file if necessary.
   - **Save** and **Close** the Service Descriptor.

2. **Open Database Configuration**:

   - Double-click on the **DB** component.

3. **Database Connection**:

   - **DB URL**: Enter your database JDBC URL.
     - Example: `jdbc:postgresql://localhost:5432/mydatabase`.
   - **DB User**: Enter your database username.
   - **DB Password**: Enter your database password.

4. **Test Connection**:

   - Click **Test** to verify the connection.
   - Ensure the message `Connection created successfully` appears.

5. **SQL Configuration**:

   - Navigate to the **SQL Configuration** tab.
   - Click **Add** to create a new SQL operation.

     - **Operation Type**: Select **Stored Procedure**.
     - **Operation Name**: Enter `FetchEmployeeSalary`.

   - **Configure Stored Procedure Call**:

     - **Refresh Schemas**:

       - Click **Refresh Schemas** to load available schemas.

     - **Select Procedure**:

       - In **Schema**, select the correct schema (e.g., `public`).
       - Under **Procedures**, select the stored procedure you've created (`fetch_employee_salary`).

     - **Parameters**:

       - The input and output parameters will be detected automatically.
       - Ensure the input parameter (`emp_id`) is listed.
         - **Name**: `emp_id`.
         - **Type**: `IN`.
         - **Data Type**: Ensure it matches the database definition (e.g., `INTEGER`).
       - Output parameters might be listed depending on the database.

     - **Result Set**:

       - If your stored procedure returns a result set, ensure **Stored Procedure Returns a Result Set** option is selected.

   - **Finish Configuration**:

     - Click **Finish** to save the SQL operation.

6. **Error Handling** (Optional):

   - Configure retry mechanisms and error responses as needed in the **Error Handling** tab.

#### Step 5: Connect Components and Configure Mappings

1. **Map Input Parameters from REST Stub to Database Component**:

   - **Configure Transformation**:

     - Right-click on the route from the **REST Stub** to the **DB** component.
     - Select **Configure Transformation**.

   - **Mapper**:

     - **Source Schema**: Should display the `empId` query parameter.
     - **Target Schema**: Represents the input parameter expected by the stored procedure call (`emp_id`).

   - **Mapping**:

     - Map `empId` from the **Source** to `emp_id` in the **Target**.

   - **Save** the mapping.

2. **Map Output from Database Component to REST Response**:

   - **Configure Transformation**:

     - Right-click on the route from the **DB** component to the **REST Stub** response port.
     - Select **Configure Transformation**.

   - **Mapper**:

     - **Source Schema**: Represents the output from the stored procedure.
     - **Target Schema**: Represents the response structure expected by the REST client.

   - **Mapping**:

     - Map the output (e.g., `salary`) from the **Source** to an appropriate field in the **Target** (e.g., `employeeSalary`).

     - Ensure the response is structured as JSON.

   - **Save** the mapping.

#### Step 6: Run and Test the Event Process

1. **Save the Event Process**:

   - Click **Save**.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click on **Run Event Process**.

   - The components should turn green, indicating they are running.

#### Step 7: Test the REST Service Using Postman

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**, e.g., `http://localhost:1856/employee/salary`.

2. **Create a New Request in Postman**:

   - **Method**: Set to **GET**.
   - **URL**: Paste the endpoint URL.

   - **Add Query Parameter**:

     - Click on **Params** and add:
       - **Key**: `empId`
       - **Value**: A valid employee ID from your database (e.g., `101`).

3. **Send the Request**:

   - Click \*\*Send`.

4. **Verify the Response**:

   - Ensure the response body contains the salary information in JSON format.

     - Example:

       ```json
       {
         "employeeSalary": 5000
       }
       ```

   - Check the HTTP status code (should be **200 OK**).

#### Step 8: Troubleshooting

1. **Test with Different `empId` Values**:

   - Try different employee IDs to ensure the stored procedure works correctly.

2. **Handle Invalid Input**:

   - Test with an invalid `empId` to see how the system handles errors.
   - Ensure appropriate error messages or status codes are returned (e.g., **404 Not Found** if employee doesn't exist).

3. **Logs and Debugging**:

   - **View Component Logs**:

     - Right-click on the **DB** component and select **View Logs** to see any errors or warnings.

   - **Use Breakpoints**:

     - Set breakpoints on routes to inspect data at different stages.

4. **Check Database Connection and Procedure**:

   - Ensure that the database is accessible and the stored procedure exists.
   - Verify permissions for the database user.

### Best Practices

- **Security**:

  - Use parameterized procedures to prevent SQL injection.
  - Secure database credentials and avoid hardcoding sensitive information.

- **Error Handling**:

  - Implement robust error handling for database exceptions.
  - Return meaningful error messages to clients.

- **Performance**:

  - Test the performance of the stored procedure and optimize as necessary.
  - Use indexes and efficient SQL within the stored procedure.

- **Transaction Management**:

  - If the stored procedure involves transactions, ensure proper commit and rollback mechanisms are in place.

- **Maintainability**:

  - Keep the stored procedures and database schemas well-documented.
  - Version control for stored procedures can help in tracking changes.

- **Testing**:

  - Test stored procedures independently before integrating with Fiorano.
  - Include unit tests for different scenarios, including edge cases.

### Advantages of Using Stored Procedures

- **Performance**:

  - Stored procedures are precompiled and optimized by the database, leading to faster execution.

- **Security**:

  - Encapsulate database logic, reducing direct access to underlying tables.
  - Control data access through permissions on stored procedures.

- **Maintainability**:

  - Centralize business logic within the database.
  - Simplify application code by moving complex queries into stored procedures.

- **Reusability**:

  - Stored procedures can be reused by multiple applications or processes.

### Conclusion

You have successfully integrated Fiorano with a database using stored procedures. By configuring the **Database** component to execute stored procedures, you can leverage advanced database capabilities within your integration workflows, enabling:

- Complex data operations and business logic within the database.
- Improved performance and security.
- Cleaner and more maintainable application logic.

Understanding how to interact with stored procedures expands the capabilities of your integration solutions, allowing you to handle sophisticated database interactions effectively.

---

## Module 3: Database, Web Services, and File Handling

Welcome back to Module 3 of the Fiorano Product Training series. In this module, we explore advanced integration techniques involving databases, web services, and file handling. These are critical components for building robust enterprise integration solutions, enabling seamless communication and data exchange across diverse systems and platforms.

---

## 3.3 Consuming Web Services (SOAP)

### Introduction

In this session, we will learn how to consume SOAP-based web services using Fiorano. Consuming SOAP services enables you to integrate with systems that expose their functionality through SOAP APIs, which are widely used in many enterprise environments.

### Objectives

- Understand how to use the **WSConsumer** component in Fiorano to consume SOAP services.
- Configure the WSConsumer with a WSDL file.
- Map request and response data between Fiorano and the SOAP service.
- Test the integration by invoking the SOAP service and verifying the response.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Basic understanding of SOAP web services and WSDL files.
- Familiarity with creating event processes in Fiorano.

### Step-by-Step Guide

#### Step 1: Create a New Event Process

1. **Open Fiorano Studio (eStudio)**:

   - Launch eStudio and connect to your Enterprise Server.

2. **Create a New Event Process**:
   - In the **Event Process Repository**, right-click and select **Add Event Process**.
   - **Name**: Enter a name like `ConsumeSOAPService`.
   - **Category**: Choose or create a category (e.g., `FioranoTraining`).
   - Click **Finish** to create the event process.

#### Step 2: Add Components to the Canvas

1. **Add REST Stub Component**:

   - In the **Microservice Palette**, find and drag the **REST Stub** component onto the canvas.
   - This component exposes a RESTful API that clients can consume.

2. **Add JSON Converter Component**:

   - Drag and drop the **JSON Converter** component onto the canvas.
   - This will convert incoming JSON data to XML, as the SOAP service requires XML input.

3. **Add WSConsumer Component**:

   - Find the **WSConsumer** component (Web Service Consumer).
   - Drag and drop it onto the canvas.
   - This component is used to interact with SOAP-based web services.

4. **Connect the Components**:
   - **From REST Stub to JSON Converter**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **JSON Converter**.
   - **From JSON Converter to WSConsumer**:
     - Draw a route from the **Output Port** of the **JSON Converter** to the **Input Port** of the **WSConsumer**.
   - **From WSConsumer to REST Stub Response**:
     - Draw a route from the **Output Port** of the **WSConsumer** to the **Response Port** of the **REST Stub**.

#### Step 3: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter a unique **Service Name** (e.g., `SOAPConsumerService`).

3. **Define Resources**:
   - Navigate to the **Resources** tab.
   - Click **Add Resource**.
     - **Path**: Enter `/invoke`.
     - **ID**: Optionally, provide an ID (e.g., `InvokeResource`).
   - **Add Method**:
     - With the resource selected, click **Add Method**.
     - **Method**: Choose **POST**.
   - **Request Representation**:
     - Click **Add Representation**.
     - **Media Type**: Select `application/json`.
   - **Response Representation**:
     - Click **Add Representation**.
     - **Media Type**: Select `application/json`.
   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 4: Configure the JSON Converter Component

1. **Open Configuration**:

   - Double-click on the **JSON Converter** component.

2. **Conversion Direction**:

   - **Convert JSON to XML**: Ensure this is set to **Yes**.

3. **Provide Output XSD Schema**:
   - **Output XSD Schema**:
     - You need to provide the XML Schema Definition (XSD) that defines the structure expected by the SOAP service.
   - **Obtaining the XSD**:
     - Extract the XSD from the WSDL file of the SOAP service.
     - Use tools like **XMLSpy** or online WSDL analyzers to generate the XSD.
   - **Load the XSD**:
     - Paste the XSD content into the **Output XSD Schema** field.
   - **Select Root Element**:
     - Click **Select Root Element** and choose the appropriate root element (e.g., `Add` for an add operation).
   - **Namespace Configuration**:
     - Configure namespaces if required.
   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 5: Configure the WSConsumer Component

1. **Open Configuration**:

   - Double-click on the **WSConsumer** component.

2. **Load the WSDL File**:

   - Navigate to the **Service Descriptor** section.
   - Under the **WSDL** tab, click **Import WSDL**.
     - **From URL**:
       - If the WSDL is available online, select **From URL** and enter the WSDL URL.
     - **From File**:
       - If you have a local WSDL file, select **From File** and browse to the file location.
   - **Parse the WSDL**:
     - Click **Parse** to load the WSDL definitions.

3. **Select the Web Service Operation**:

   - After parsing, the **Available Operations** list will display.
   - Select the appropriate service, port, and operation (e.g., `CalculatorSOAP`, operation `Add`).
   - Click **OK**.

4. **Advanced Configurations** (Optional):

   - **Timeout Settings**:
     - Configure timeouts as needed.
   - **Security Settings**:
     - If the SOAP service requires authentication, configure WS-Security settings.
   - **SOAP Headers**:
     - Add any required SOAP headers.

5. **Finish Configuration**:
   - Click **Finish** to save.

#### Step 6: Configure Mappings Between Components

1. **Configure Mapping from JSON Converter to WSConsumer**:

   - Right-click on the route between **JSON Converter** and **WSConsumer**.
   - Select **Configure Transformation**.
   - In the **Mapper**:
     - **Source Schema**: Displays the XML structure from the JSON Converter.
     - **Target Schema**: Displays the input expected by the SOAP service.
   - **Mapping**:
     - Map the necessary fields from the source to the target.
     - For example, map `parameter1` and `parameter2` to the SOAP service's input parameters.
   - **Save** the mapping.

2. **Configure Mapping from WSConsumer to REST Stub Response**:
   - Right-click on the route between **WSConsumer** and **REST Stub** (Response Port).
   - Select **Configure Transformation**.
   - In the **Mapper**:
     - **Source Schema**: Displays the response from the SOAP service.
     - **Target Schema**: Represents the response structure expected by the client.
   - **Mapping**:
     - Map the SOAP response fields to the JSON response.
     - For example, map `AddResult` to `result`.
   - **Save** the mapping.

#### Step 7: Run and Test the Event Process

1. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate all configurations.

2. **Run the Event Process**:
   - Click on **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

#### Step 8: Test the Service Using Postman

1. **Retrieve the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL** (e.g., `http://localhost:1856/invoke`).

2. **Create a New Request in Postman**:

   - **Method**: Set to **POST**.
   - **URL**: Paste the endpoint URL.
   - **Headers**:
     - **Content-Type**: `application/json`.
   - **Body**:
     - Choose **Raw** and select **JSON**.
     - Provide a JSON payload matching your mapping (e.g.):
       ```json
       {
         "parameter1": 10,
         "parameter2": 5
       }
       ```
   - **Send the Request**.

3. **Verify the Response**:
   - Ensure the response contains the expected result.
   - For example:
     ```json
     {
       "result": 15
     }
     ```

#### Step 9: Troubleshooting

1. **View Component Logs**:

   - Right-click on the **WSConsumer** component and select **View Logs** to check for errors.

2. **Use Breakpoints and Debugger**:

   - Set breakpoints on routes to inspect data at different stages.

3. **Validate Mappings and Schemas**:

   - Ensure all mappings are correctly configured.
   - Verify that the XSD and WSDL files are accurate.

4. **Network Connectivity**:
   - Check that the SOAP service endpoint is reachable from your Fiorano environment.

### Best Practices

- **Maintain Up-to-Date Schemas**:

  - Keep your WSDL and XSD files organized and version-controlled.
  - Update your mappings if the SOAP service changes.

- **Error Handling**:

  - Use the **Exception Ports** on the **WSConsumer** component to handle SOAP faults.
  - Implement retry mechanisms if necessary.

- **Security Considerations**:

  - If the SOAP service requires authentication or encryption, configure WS-Security settings accordingly.

- **Performance Optimization**:
  - Monitor the performance and adjust configurations to optimize throughput and latency.

### Conclusion

You have successfully consumed a SOAP web service using Fiorano. By integrating SOAP services, you can extend the functionality of your applications and leverage existing enterprise systems. Understanding how to consume different types of web services is essential for building flexible and interoperable integration solutions.

---

## Module 3: Database, Web Services, and File Handling

Welcome back to Module 3 of the Fiorano Product Training series. In this module, we are exploring advanced integration techniques involving databases, web services, and file handling. These are critical components for building robust enterprise integration solutions, enabling seamless communication and data exchange across diverse systems and platforms.

---

## 3.4 Consuming REST Services (HTTP/HTTPS)

### Introduction

In this session, we will learn how to consume RESTful services using Fiorano's **REST Consumer** component. Consuming REST services is essential when integrating with external APIs or backend services that expose their functionality over HTTP or HTTPS. We'll explore how to configure the REST Consumer component to interact with RESTful services securely and efficiently.

### Objectives

- Understand how to use the **REST Consumer** component in Fiorano.
- Configure the REST Consumer to consume RESTful services over HTTP and HTTPS.
- Handle query parameters, headers, and authentication mechanisms.
- Test and validate the integration with external REST services.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Basic knowledge of RESTful web services and HTTP methods.
- An understanding of how to expose REST services (covered in session 2.1).
- Access to a RESTful API or service that you can consume. For demonstration, we'll use a publicly available dummy API (e.g., [ReqRes](https://reqres.in)).

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Open Fiorano Studio (eStudio)**:

   - Launch eStudio and connect to your Enterprise Server if not already connected.

2. **Create a New Event Process**:

   - In the **Event Process Repository**, right-click and select **Add Event Process**.
   - **Name**: Enter a name like `ConsumeRESTService`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish** to create the event process.

#### Step 2: Add and Configure the REST Stub Component

1. **Add the REST Stub**:

   - In the **Microservice Palette**, search for **REST Stub**.
   - Drag and drop the **REST Stub** onto the canvas.

2. **Configure the REST Stub**:

   - **Open Configuration**:

     - Double-click on the **REST Stub** component to open its configuration window.

   - **Service Name**:

     - Enter a unique **Service Name**, e.g., `RequestService`.

   - **Resources**:

     - **Add Resource**:

       - Click **Add Resource**.
       - **Path**: Enter `/getdata`.
       - **ID**: Optionally, enter `GetDataResource`.

     - **Add Method**:
       - With the resource selected, click **Add Method**.
       - **Method**: Choose **GET**.

   - **Request Parameters**:

     - Under the **Method**, you can define **Parameters** if your REST service accepts any.
     - For this example, we can accept a query parameter (e.g., `page`).
       - Click **Add Parameter**.
       - **Name**: `page`.
       - **Style**: Select `Query`.
       - **Type**: Choose `String` or `Integer` based on expected input.
       - **Required**: Check the box if it is mandatory.

   - **Response Representation**:

     - Under **Response**, click **Add Representation**.
     - **Media Type**: Select `application/json`.

   - **Security Settings** (Optional):

     - If you need to secure the service, configure SSL settings under the **Security** tab.

   - **Finish Configuration**:
     - Click **Finish** to save the configuration.

#### Step 3: Add and Configure the REST Consumer Component

1. **Add the REST Consumer Component**:

   - In the **Microservice Palette**, search for **REST Consumer**.
   - Drag and drop the **REST Consumer** onto the canvas.

2. **Configure the REST Consumer**:

   - **Open Configuration**:

     - Double-click on the **REST Consumer** component.

   - **Initial Configuration**:

     - Under **General**, you can provide a **Service Name** if desired.

   - **Load WADL or OpenAPI Specification** (Optional):

     - If the backend REST service provides a WADL or OpenAPI (Swagger) specification, you can import it.
     - Click **Load WADL** and choose **From URL** or **From File**.

   - **Manual Configuration**:

     - **Base URL**:

       - Enter the base URL of the RESTful service you want to consume.
       - For example, using [ReqRes](https://reqres.in), the base URL is `https://reqres.in`.

     - **Resources**:

       - Under **Resources**, you can define the endpoint paths.
       - **Add Resource**:
         - Click **Add Resource**.
         - **Path**: Enter `/api/users?page={page}` where `{page}` is a path parameter.
         - **ID**: Optionally, enter `GetUsers`.

     - **Methods**:

       - With the resource selected, click **Add Method**.
       - **Method**: Choose **GET**.

     - **Request Parameters**:

       - Since `page` is a query parameter in this API, define it as such.
       - Click **Add Parameter** under **Request Parameters**.
         - **Name**: `page`.
         - **Style**: Select `Query`.
         - **Type**: `Integer`.
         - **Required**: Check if mandatory.

     - **Response Representation**:
       - Under **Response**, click **Add Representation**.
       - **Media Type**: Select `application/json`.

   - **Security Settings** (For HTTPS)\*\*:

     - If consuming an HTTPS endpoint and certificate verification is required, configure SSL settings.

       - Navigate to the **Security** tab.
       - Check **Use SSL**.
       - **Accept Server Certificate**: Enable this to accept the server's SSL certificate.
       - **Ignore Hostname Mismatch**: Enable if the server's hostname does not match the certificate.

     - **Key Store** and **Trust Store**:
       - If the server requires client certificates (mutual TLS), configure the **Key Store** and **Trust Store** with the appropriate certificates in JKS format.

   - **Finish Configuration**:
     - Click **Finish** to save.

#### Step 4: Connect Components and Configure Mappings

1. **Draw Routes**:

   - **From REST Stub to REST Consumer**:

     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **REST Consumer**.

   - **From REST Consumer to REST Stub Response**:
     - Draw a route from the **Output Port** of the **REST Consumer** to the **Response Port** of the **REST Stub**.

2. **Configure Mapping from REST Stub to REST Consumer**:

   - **Map Query Parameters**:

     - Right-click on the route from **REST Stub** to **REST Consumer** and select **Configure Transformation**.
     - In the **Mapper**:

       - **Source Schema**: Represents the input from the **REST Stub** (including the `page` query parameter).

       - **Target Schema**: Represents the input expected by the **REST Consumer**.

       - **Mapping**:
         - Map the `page` parameter from the **Source** to the `page` parameter in the **Target**.
         - Ensure that the parameters are correctly mapped to construct the correct request to the backend service.

     - **Save** the mapping.

3. **Configure Mapping from REST Consumer to REST Stub Response**:

   - **Pass Through the Response**:

     - Right-click on the route from **REST Consumer** to **REST Stub Response**.
     - Select **Configure Transformation**.
     - In the **Mapper**:

       - **Source Schema**: Represents the response from the backend REST service.

       - **Target Schema**: Represents the response that will be sent to the client.

       - **Mapping**:
         - Map the **Text Content** from the **Source** to the **Text Content** in the **Target**.
         - Ensure that the **Media Type** is set to `application/json` if returning JSON.

     - **Save** the mapping.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**:

   - Click **Save** to ensure all configurations are saved.

2. **Check Resources and Connectivity (CRC)**:

   - Click on the **CRC** button to validate configurations.

3. **Run the Event Process**:

   - Click **Run Event Process**.
   - Components should turn green, indicating they are running.

#### Step 6: Test the REST Service Using Postman or a Web Browser

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**, e.g., `http://localhost:1856/getdata`.

2. **Test Using Postman**:

   - **Create a New Request** in Postman.
   - **Method**: Set to **GET**.
   - **URL**: Paste the endpoint URL.
   - **Add Query Parameter**:

     - Click on **Params** and add `page` with a value (e.g., `2`).

   - **Headers**:

     - Add `Accept` header as `application/json` to specify the response format.

   - **Send the Request**:

     - Click **Send**.

   - **Verify the Response**:

     - The response should contain JSON data retrieved from the backend REST service.
     - You should see user data corresponding to page 2 from the [ReqRes](https://reqres.in) API.

3. **Test in a Web Browser** (Optional):

   - Paste the endpoint URL in a browser and append the query parameter (e.g., `http://localhost:1856/getdata?page=2`).
   - Observe the JSON response displayed in the browser.

#### Step 7: Handling Errors and Debugging

1. **Enable Logs**:

   - Right-click on the **REST Consumer** component and select **View Logs**.
   - Monitor **Error Logs** and **Output Logs** for any issues.

2. **Set Breakpoints**:

   - Use breakpoints to inspect data at various points.
   - Click on the route where you want to add a breakpoint.
   - Click the **Debugger** icon and select **Add Breakpoint**.

3. **Common Issues**:

   - **SSL Certificate Errors**:

     - If consuming an HTTPS service and you encounter SSL errors, ensure that **Use SSL** is enabled and SSL settings are correctly configured.

   - **Connection Timeouts**:

     - Check network connectivity to the backend service.
     - Increase **Timeout** settings in the **REST Consumer** if necessary.

   - **Incorrect Mapping**:
     - Verify that query parameters and headers are correctly mapped.

#### Step 8: Optional Enhancements

1. **Handling Authentication**:

   - If the backend service requires authentication (e.g., API keys, OAuth tokens), configure the necessary headers or parameters in the **REST Consumer**.
   - Use the **Headers** tab in the **REST Consumer** configuration to add required headers.

2. **Dynamic Endpoint URLs**:

   - If the endpoint URL needs to be dynamic, you can parameterize the **Base URL** or resource paths using context variables or properties.

3. **Error Handling**:

   - Configure the **Error Port** of the **REST Consumer** to handle exceptions.
   - Add a route from the **Exception Port** to a component that processes errors (e.g., logs them or sends a response to the client).

4. **Response Transformation**:

   - If the response from the backend service needs to be transformed before sending it to the client, use a **Mapper** or **Transformer** component to modify the response.

### Best Practices

- **Security**:

  - Always use HTTPS when consuming services over the internet to ensure data security.
  - Properly handle certificates and SSL settings to prevent man-in-the-middle attacks.

- **Performance**:

  - Optimize timeout settings to prevent long waits in case the backend service is unresponsive.
  - Consider caching responses if appropriate to reduce load on the backend service.

- **Resource Management**:

  - Ensure that any resources (e.g., connections) are properly managed and closed if necessary.

- **Error Handling**:

  - Implement robust error handling to manage exceptions and provide informative responses to clients.

- **Logging and Monitoring**:

  - Enable logging on the **REST Consumer** to monitor requests and responses, which aids in troubleshooting.

### Conclusion

You have successfully learned how to consume RESTful services using Fiorano's **REST Consumer** component. This enables your integration workflows to interact with external APIs and services, facilitating data exchange and integration with third-party systems.

Understanding how to configure and use the REST Consumer is essential for building comprehensive integration solutions that leverage external services and APIs.

---

## 3.5 Consuming Backend Services Using HTTP Adapter

### Introduction

In this session, we will explore how to consume backend services using Fiorano's **HTTP Adapter** component. The HTTP Adapter is a versatile component that allows you to interact with HTTP or HTTPS services that may not conform strictly to RESTful conventions or when you need more control over the HTTP request being sent.

### Objectives

- Understand how to use the **HTTP Adapter** component in Fiorano.
- Configure the HTTP Adapter to send HTTP requests to backend services.
- Handle query parameters, headers, and request bodies.
- Test and validate the integration with backend services.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Basic knowledge of HTTP methods and request/response structure.
- Access to a backend HTTP service for testing (e.g., [ReqRes](https://reqres.in)).

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Open Fiorano Studio (eStudio)**:

   - Launch eStudio and connect to your Enterprise Server.

2. **Create a New Event Process**:

   - In the **Event Process Repository**, right-click and select **Add Event Process**.
   - **Name**: Enter a name like `ConsumeHTTPService`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

#### Step 2: Add and Configure the REST Stub Component

1. **Add the REST Stub**:

   - In the **Microservice Palette**, search for **REST Stub**.
   - Drag and drop the **REST Stub** onto the canvas.

2. **Configure the REST Stub**:

   - **Service Name**: Enter `HTTPAdapterService`.
   - **Resource**:
     - **Path**: Enter `/fetch`.
     - **Method**: Set to **GET**.
   - **Request Parameters**:
     - Define any query parameters required (e.g., `page`).
   - **Response Representation**:
     - Set **Media Type** to `application/json`.

#### Step 3: Add and Configure the HTTP Adapter Component

1. **Add the HTTP Adapter**:

   - In the **Microservice Palette**, search for **HTTP Adapter**.
   - Drag and drop the **HTTP Adapter** onto the canvas.

2. **Configure the HTTP Adapter**:

   - **Connection Configuration**:

     - **Host Name**: Enter the hostname of the backend service (e.g., `reqres.in`).
     - **Port**:
       - For `http`, the default port is `80`.
       - For `https`, the default port is `443`.
     - **Use SSL**: Check this if the backend service uses HTTPS.

   - **Testing Connection**:

     - Click **Test** to ensure connectivity.
     - If successful, you will see `Connection created successfully`.

   - **HTTP Request Property**:

     - **Method**: Select **GET**, **POST**, **PUT**, etc., as required.
     - **Request URI**: Enter the path of the resource (e.g., `/api/users`).
     - **Query Parameters**:
       - Click on **Add Parameter** to add query parameters (e.g., `page`).

   - **Custom Headers** (Optional):

     - If the backend service requires specific headers (e.g., `Authorization`, `Content-Type`), add them under **Custom Headers**.

   - **SSL Security** (For HTTPS):

     - Navigate to **Show Expert Properties** > **SSL Security**.
     - **Accept Server Certificate**: Enable to accept the server's SSL certificate.
     - **Ignore Hostname Mismatch**: Enable if there's a mismatch in the hostname.

     - **Key Store** and **Trust Store**:

       - Configure if the backend service requires client certificates.

   - **Finish Configuration**:

     - Click **OK** to save the settings.

#### Step 4: Connect Components and Configure Mappings

1. **Draw Routes**:

   - **From REST Stub to HTTP Adapter**:

     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **HTTP Adapter**.

   - **From HTTP Adapter to REST Stub Response**:
     - Draw a route from the **Output Port** of the **HTTP Adapter** to the **Response Port** of the **REST Stub**.

2. **Configure Mapping from REST Stub to HTTP Adapter**:

   - **Map Query Parameters**:

     - Right-click on the route from **REST Stub** to **HTTP Adapter** and select **Configure Transformation**.
     - In the **Mapper**:

       - **Source Schema**: Represents input from the **REST Stub**.

       - **Target Schema**: Represents the input expected by the **HTTP Adapter**.

       - **Mapping**:
         - Map the query parameter `page` to the **Parameter** in the **HTTP Adapter**.
         - Ensure that parameters are mapped correctly.

     - **Save** the mapping.

3. **Configure Mapping from HTTP Adapter to REST Stub Response**:

   - **Map Response**:

     - Right-click on the route from **HTTP Adapter** to **REST Stub Response**.
     - Select **Configure Transformation**.
     - In the **Mapper**:

       - Map the **Text Content** from the **Source** to the **Text Content** in the **Target**.

     - **Save** the mapping.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**.
2. **Check Resources and Connectivity (CRC)**.
3. **Run the Event Process**.

#### Step 6: Test the Service Using Postman

1. **Get the Endpoint URL**:

   - Right-click on the **REST Stub** component and select **View WADL**.
   - Copy the **Endpoint URL**.

2. **Create a New Request in Postman**:

   - **Method**: Set to **GET**.
   - **URL**: Paste the endpoint URL.
   - **Add Query Parameter**:

     - Add `page` with a value (e.g., `2`).

   - **Send the Request**:

     - Click **Send**.

   - **Verify the Response**:

     - The response should contain JSON data from the backend service.

#### Step 7: Troubleshooting and Debugging

1. **Enable Logs**:

   - Right-click on the **HTTP Adapter** and select **View Logs**.

2. **Use Breakpoints**:

   - Add breakpoints to monitor data flow.

3. **Common Issues**:

   - **Connection Errors**:

     - Verify network connectivity.
     - Check SSL settings if using HTTPS.

   - **Incorrect Mapping**:

     - Ensure parameters and headers are correctly mapped.

### Best Practices

- **Security**:

  - Use SSL/TLS when communicating with secure services.
  - Properly handle certificates.

- **Flexibility**:

  - The HTTP Adapter allows for more custom configurations compared to the REST Consumer.

- **Error Handling**:

  - Utilize the **Exception Port** for error management.

### Conclusion

You have learned how to consume backend services using the **HTTP Adapter** component in Fiorano. This provides greater flexibility when interacting with services that require custom HTTP configurations or do not adhere to standard REST conventions.

---

## Module 3: Database, Web Services, and File Handling

Welcome back to Module 3 of the Fiorano Product Training series. We have been exploring advanced integration techniques involving databases, web services, and file handling to build robust enterprise integration solutions.

---

## 3.6 Integrating with Files using FileReader

### Introduction

In this session, we will explore how to integrate with files using Fiorano's **FileReader** component. Integrating with files is a common requirement in enterprise integration scenarios, allowing you to read data from files and process it within your workflows.

### Objectives

- **Understand** how to use the **FileReader** component to read files.
- **Configure** the FileReader to read files from a specified directory.
- **Handle** file processing actions such as moving or deleting files after processing.
- **Test** and validate file integration within an event process.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Basic knowledge of file systems and file operations.
- Familiarity with creating event processes in Fiorano.
- Access to a directory containing files for testing.

### Step-by-Step Guide

#### Scenario Overview

We will design an event process that:

1. Uses the **FileReader** component to read files from a specified directory.
2. Processes the file content (e.g., logs it or transforms it).
3. Optionally moves or deletes the files after processing.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `FileIntegrationWithFileReader`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **FileReader**: Reads files from the file system.

     - In the **Microservice Palette**, search for **FileReader** under the **File** category.
     - Drag and drop the **FileReader** component onto the canvas.

   - **Display** (Optional): To display the output data.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **FileReader** to the **Input Port** of the **Display** component.

#### Step 2: Configure the FileReader Component

1. **Open Configuration**:

   - Double-click on the **FileReader** component.

2. **Basic Configuration**:

   - **Use File Data Configuration from Input**:
     - If you prefer to supply file details dynamically during runtime, check this option.
     - For this example, we will configure the component statically, so leave it unchecked.

3. **File Selection Configuration**:

   - **Source Directory**:

     - Enter the path of the directory where the input files are located.
     - Example: `C:\Fiorano\InputFiles` (ensure this directory exists).

   - **File Name / Pattern**:

     - Specify the name or pattern of the files to read.
     - Example: `*.txt` to read all text files.

   - **Working Directory** (Optional):

     - Specify a directory where the file is temporarily moved during processing.
     - Example: `C:\Fiorano\Working`.

   - **Error Directory** (Optional):
     - Specify a directory where files are moved in case of errors during processing.
     - Example: `C:\Fiorano\ErrorFiles`.

4. **Processing Options**:

   - **Line Count**:

     - Enter `0` to read the entire file at once.
     - Enter a positive integer to read files line by line.
       - Example: `1` to read one line at a time.

   - **Header Count**:

     - Specify the number of header lines to skip if your file has headers.
     - Example: `1` to skip the first line.

   - **Post Processing Action**:

     - Choose what to do with the file after processing.
     - Options:
       - **No Action**: Leave the file as is.
       - **Move**: Move the file to a specified directory.
       - **Delete**: Delete the file after processing.
     - For this example, select **Move**.

   - **Target Directory**:
     - Specify the directory where the file will be moved after processing.
     - Example: `C:\Fiorano\ProcessedFiles`.

5. **Advanced Options** (Optional):

   - **File Binary**:
     - Check if you are reading binary files.
     - For text files, leave it unchecked.

6. **Finish Configuration**:

   - Click **Finish** to save the configuration.

#### Step 3: Configure the Route and Display Component (Optional)

1. **Mapping**:

   - Since we are reading text files, the **FileReader** will output the file content as a string.
   - No additional mapping is required unless you need to transform the data.

2. **Display Component**:

   - The **Display** component will show the content of the files read by the **FileReader**.

#### Step 4: Prepare Input Files

1. **Create Input Files**:

   - In the **Source Directory** specified (e.g., `C:\Fiorano\InputFiles`), place some text files to be read.
   - Example: Create `file1.txt` and `file2.txt` with some sample content.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Observe the Processing**:

   - The **FileReader** component will begin monitoring the **Source Directory** for files matching the specified pattern.
   - When it finds matching files, it reads the content and outputs it.

5. **View Output**:

   - Double-click on the **Display** component to see the content of the files.
   - Verify that the content matches the input files.

#### Step 6: Verify Post Processing Actions

1. **Check Processed Files**:

   - The files should have been moved to the **Target Directory** specified (e.g., `C:\Fiorano\ProcessedFiles`).

2. **Check Working and Error Directories** (If Configured):

   - **Working Directory**:

     - Temporarily holds files during processing.
     - Should be empty after processing completes.

   - **Error Directory**:
     - Contains files that failed to process due to errors.

#### Step 7: Handling Errors and Edge Cases

1. **File Access Issues**:

   - Ensure that Fiorano has read/write permissions to the directories involved.

2. **File Locking**:

   - If files are being written to while the **FileReader** attempts to read them, consider configuring **File Locking** options.

3. **Processing Large Files**:

   - For very large files, consider setting **Line Count** to read the file in chunks.

#### Step 8: Optional Enhancements

1. **Dynamic File Configuration**:

   - Enable **Use File Data Configuration from Input** to supply file details at runtime via input messages.

2. **Data Transformation**:

   - Add a **Mapper** or **Transformation** component to process the file content.

3. **Triggering On New Files**:

   - The **FileReader** can be configured to continuously monitor the directory and process new files as they arrive.

### Best Practices

- **File Patterns**:

  - Use file patterns to control which files are processed (e.g., `*.csv` for CSV files).

- **Error Handling**:

  - Configure the **Error Directory** to handle files that cause processing errors.

- **Idempotent Processing**:

  - Ensure that files are not processed multiple times unless intended.

- **Security**:

  - Secure the directories to prevent unauthorized access to sensitive files.

- **Resource Management**:

  - Monitor resource utilization if processing a large number of files.

### Conclusion

You have successfully integrated file reading capabilities into your Fiorano event process using the **FileReader** component. This allows your workflows to ingest data from files, enabling integration with systems that produce or consume data via the file system.

Understanding how to work with files is essential in many enterprise integration scenarios, and the **FileReader** provides a flexible way to incorporate file data into your processes.

---

## 3.7 Integrating with Files using FileWriter Part 1

### Introduction

In this session, we will learn how to write data to files using Fiorano's **FileWriter** component. This enables you to output data from your processes into files, which can be used by other systems or for archiving purposes.

### Objectives

- **Understand** how to use the **FileWriter** component to write data to files.
- **Configure** the FileWriter to write files to a specified directory.
- **Handle** file writing modes such as appending or creating new files.
- **Test** and validate file output within an event process.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Basic knowledge of file systems and file operations.
- Familiarity with creating event processes in Fiorano.

### Step-by-Step Guide

#### Scenario Overview

We will design an event process that:

1. Receives input data (e.g., from a **Feeder** or **REST Stub** component).
2. Uses the **FileWriter** component to write the data to a file.
3. Configures writing modes such as creating new files or appending to existing files.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Create a new event process named `FileIntegrationWithFileWriter`.

2. **Add Components**:

   - **REST Stub** or **Feeder**: Acts as the message source.

     - For interactive input, use a **Feeder** component.
     - For exposing a service, use a **REST Stub** component.

   - **FileWriter**: Writes data to files.
     - In the **Microservice Palette**, search for **FileWriter** under the **File** category.
     - Drag and drop the **FileWriter** component onto the canvas.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **Feeder** or **REST Stub** to the **Input Port** of the **FileWriter**.

#### Step 2: Configure the FileWriter Component

1. **Open Configuration**:

   - Double-click on the **FileWriter** component.

2. **Basic Configuration**:

   - **File Name**:

     - Specify the name of the output file.
     - Example: `output.txt`. If you want unique file names, you can use patterns or timestamps.

   - **Target Directory**:

     - Specify the path where the file will be written.
     - Example: `C:\Fiorano\OutputFiles` (ensure this directory exists).

   - **Append Timestamp** (Optional):
     - Check this option to append a timestamp to the file name for uniqueness.

3. **Output Modes**:

   - **New File For Each Message**:
     - Creates a new file for every message received.
   - **Append And Close On Time Out**:
     - Appends data to the file and closes it after a specified timeout.
   - **Append And Close On Event**:
     - Appends data until a close event is received.
   - For this example, select **New File For Each Message**.

4. **File Encoding**:

   - Default is `UTF-8`. Change if necessary to match your requirements.

5. **Finish Configuration**:

   - Click **Finish** to save settings.

#### Step 3: Configure the Feeder or REST Stub Component

1. **Feeder Component**:

   - If using a **Feeder**, you can input messages manually.
   - Double-click on the **Feeder** to input data.

2. **REST Stub Component**:

   - If using a **REST Stub**, configure the service to accept input via API calls.

   - **Configure the REST Stub**:

     - **Service Name**: Enter `FileWriterService`.

     - **Resources**:
       - **Path**: Enter `/write`.
       - **Method**: Set to **POST**.
       - **Request Representation**:
         - **Media Type**: `text/plain` or `application/json`, depending on your data.
       - **Response Representation**:
         - **Media Type**: `text/plain` or as appropriate.

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Send Data to be Written**:

   - **Feeder**:

     - Enter some text data and click **Send**.
     - Example: `Hello, this is a test message.`

   - **REST Stub**:
     - Use Postman or another client to send data to the REST endpoint.
     - **URL**: `http://localhost:<port>/write` (replace `<port>` with the actual port).
     - **Method**: **POST**.
     - **Headers**:
       - Add `Content-Type` header matching the media type configured.
     - **Body**:
       - Enter the data you want to write to the file.

5. **Verify Output Files**:

   - Check the **Target Directory** specified.
   - You should see new files created with the data you sent.
   - If you enabled **Append Timestamp**, each file will have a unique timestamp in its name.

6. **View File Content**:

   - Open the generated files to verify that they contain the correct data.

#### Step 5: Handling File Writing Modes

1. **Append And Close On Time Out**:

   - **Configuration**:

     - In the **FileWriter** configuration, select **Append And Close On Time Out** under **Output Mode**.
     - Set the **Timeout After Last Message** in milliseconds (e.g., `5000` for 5 seconds).

   - **Behavior**:
     - Messages are appended to the same file.
     - After the timeout period elapses without receiving new messages, the file is closed.

2. **Append And Close On Event**:

   - **Configuration**:

     - Select **Append And Close On Event** under **Output Mode**.

   - **Sending Close Event**:

     - You need to send a special property in the message header to signal the **FileWriter** to close the file.
     - **Property Name**: `closeEvent`
     - **Property Value**: `true`

   - **Feeder Example**:
     - In the **Feeder**, add a property:
       - **Name**: `closeEvent`
       - **Value**: `true`

#### Step 6: Advanced Configuration (Optional)

1. **Using Message Headers to Specify File Details**:

   - Enable **Use File Details From Message Header** in the **FileWriter** configuration.
   - This allows you to specify file names and directories dynamically via message headers.

   - **Message Properties**:
     - **FileName**: Name of the file.
     - **TargetDirectory**: Directory where the file will be written.

2. **Error Handling**:

   - Configure **Error Ports** to handle any exceptions during file writing.

3. **File Content Transformation**:

   - Add a **Mapper** component before the **FileWriter** to transform the data if necessary.

### Best Practices

- **Unique File Names**:

  - Use timestamps or unique identifiers to prevent file name collisions.
  - Enable **Append Timestamp** or include unique identifiers in the file name.

- **File Permissions**:

  - Ensure that Fiorano has write permissions to the target directory.

- **Data Integrity**:

  - Consider transactionality if multiple processes might write to the same file.
  - Use appropriate file locking mechanisms if necessary.

- **Resource Management**:

  - Monitor disk space usage to prevent issues due to large numbers of files.
  - Implement file cleanup policies as needed.

- **Error Handling**:

  - Handle exceptions and errors gracefully.
  - Use the **Exception Port** of the **FileWriter** to manage errors.

### Conclusion

You have successfully learned how to write data to files using the **FileWriter** component in Fiorano. This enables your integration workflows to output data to the file system, facilitating interactions with systems that consume data from files or for logging and archiving purposes.

By mastering both reading and writing files, you can create comprehensive integration solutions that handle file-based data exchanges efficiently.

---

## Module 3: Database, Web Services, and File Handling

Welcome back to Module 3 of the Fiorano Product Training series. So far, we have covered how to read from files using the **FileReader** component and how to write to files using the **FileWriter** component in basic modes. In this session, we will delve deeper into advanced configurations of the **FileWriter** component to handle more complex file writing operations.

---

## 3.8 Integrating with Files using FileWriter Part 2

### Introduction

In the previous session (3.7), we learned how to use the **FileWriter** component to create new files for each message or to append data to a file and close it after a specified timeout. Now, we will explore how to use event-driven mechanisms to control file writing operations, specifically how to append data to a file and close it based on certain events.

This advanced usage is particularly useful when you need to accumulate data from multiple messages into a single file and decide when to finalize and close the file based on specific conditions within your workflow.

### Objectives

- **Understand** how to configure the **FileWriter** to append data to a file and close it upon receiving a specific event.
- **Learn** how to use message headers to send control signals to the **FileWriter** component.
- **Test** and validate the event-based file writing within an event process.
- **Apply** best practices for managing file writing operations in complex scenarios.

### Prerequisites

- Familiarity with:
  - Fiorano Studio (eStudio) and creating event processes.
  - Basic usage of the **FileWriter** component (covered in session 3.7).
  - Concepts of message headers and properties in Fiorano.

---

### Scenario Overview

We will enhance the event process from the previous session by configuring the **FileWriter** to:

1. **Append Data**: Continuously append data from multiple messages to the same file.

2. **Controlled Closure**: Close the file and finalize it when a specific event occurs (e.g., receiving a message with a certain header property).

---

### Step-by-Step Guide

#### Step 1: Modify the Event Process Canvas

1. **Open the Existing Event Process**:

   - Open the event process you created in session 3.7 (`FileIntegrationWithFileWriter`).

2. **Components in Use**:

   - **REST Stub** or **Feeder**: Used to send input messages.
   - **FileWriter**: Configured to write data to a file.

---

#### Step 2: Configure the FileWriter for Append and Close on Event

1. **Open the FileWriter Configuration**:

   - Double-click on the **FileWriter** component to open its configuration window.

2. **Change Output Mode**:

   - Navigate to the **Output Mode** settings.
   - Select **Append and Close on Event**.

3. **Set File Name and Target Directory**:

   - **File Name**: Specify a fixed file name (e.g., `aggregated_output.txt`).
   - **Target Directory**: Ensure it is correctly set (e.g., `C:\Fiorano\OutputFiles`).

   - **Note**: Since we are appending data to the same file, it's important to use a consistent file name.

4. **File Encoding**:

   - Keep it as `UTF-8` unless a different encoding is required.

5. **Other Settings**:

   - **Append Timestamp**: Uncheck this option to maintain a consistent file name.
   - Ensure **Use File Details from Message Header** is unchecked unless you plan to specify file details dynamically.

6. **Finish Configuration**:

   - Click **Finish** to save the changes.

---

#### Step 3: Prepare to Signal File Closure Using Message Headers

To instruct the **FileWriter** to close the file, we need to send a special signal via message headers.

1. **Understand the Close Event Mechanism**:

   - The **FileWriter** listens for a message with a specific header/property that signals it to close the file.
   - **Property Name**: `CloseEvent` (case-sensitive).
   - **Property Value**: Should be set to `true`.

---

#### Step 4: Configure the Input Component to Send Close Events

Depending on whether you are using a **Feeder** or **REST Stub**, you will need to modify how you send messages.

##### **Option A: Using Feeder**

1. **Open the Feeder Component**:

   - Double-click on the **Feeder** component.

2. **Prepare Messages Without Close Event**:

   - Enter the data you want to write to the file.
   - Ensure that no properties are set.
   - Click **Send** to send multiple messages, which will be appended to the same file.

3. **Prepare Message with Close Event**:

   - Enter the final piece of data or leave it empty if not needed.
   - Click on the **Properties** tab in the Feeder window.
   - Add a new property:
     - **Name**: `CloseEvent`
     - **Value**: `true`
   - Click **Send**.

   - **Result**: The **FileWriter** will append any data from this message and then close the file.

##### **Option B: Using REST Stub**

1. **Modify the Route to Handle Close Event**

   - Since HTTP headers are automatically mapped to message properties with the prefix `HTTP_`, we need to extract the `CloseEvent` header.

2. **Add a Mapper Component (Optional)**

   - If necessary, add a **Mapper** component between the **REST Stub** and the **FileWriter** to extract and set the `CloseEvent` property correctly.

3. **Configure the REST Client (e.g., Postman)**

   - **Regular Messages**:

     - Send POST requests to the REST endpoint with the data in the body.
     - Do not include the `CloseEvent` header.

   - **Close Event Message**:

     - Send a POST request with the `CloseEvent` header set to `true`.
     - Include any final data if needed.

   - **Note**: You may need to adjust the mapping to strip the `HTTP_` prefix from the header name when setting the property.

---

#### Step 5: Adjust Mappings for Close Event (If Necessary)

If using a **REST Stub**, additional mapping may be required to correctly set the `CloseEvent` property.

1. **Configure the Route from REST Stub to FileWriter**:

   - Right-click on the route and select **Configure Transformation**.

2. **Use the Mapper to Extract the CloseEvent Header**:

   - **Source Schema**: Contains the message body and properties (headers prefixed with `HTTP_`).

   - **Target Schema**: Should include the `CloseEvent` property.

3. **Mapping Steps**:

   - **Extract the CloseEvent Header**:

     - Use the **Get String Property** function from **JMS Message Functions**.
     - Set the property name to `HTTP_CloseEvent`.

   - **Conditionally Set the CloseEvent Property**:
     - Use the **If-Else** function to check if the extracted property is not null.
     - If it is not null, set the `CloseEvent` property to `true`.
     - Else, set the `CloseEvent` property to `null` or leave it unset.

4. **Save the Mapping**.

---

#### Step 6: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Send Data Messages**:

   - **Feeder**:
     - Send multiple messages without the `CloseEvent` property.
   - **REST Client**:
     - Send multiple POST requests without the `CloseEvent` header.

5. **Verify the File Content**:

   - Open the target file (e.g., `aggregated_output.txt`).
   - Confirm that all messages have been appended to the file.

6. **Send the Close Event**:

   - **Feeder**:
     - Send a message with the `CloseEvent` property set to `true`.
   - **REST Client**:
     - Send a POST request with the `CloseEvent` header set to `true`.

7. **Verify File Closure**:

   - Confirm that the **FileWriter** has closed the file.
   - Any subsequent messages will be written to a new file (depending on configuration).

---

### Handling Multiple File Writing Sessions

If you need to start a new file after closing the previous one, configure the **FileWriter** accordingly:

- **File Name Pattern**:
  - Include a timestamp or unique identifier when the file is closed.
  - Use the **Append Timestamp** option or dynamically set the file name.

### Best Practices

- **Consistent Property Names**:

  - Ensure that you use the exact property name `CloseEvent` (case-sensitive).

- **Message Order**:

  - Be mindful of the order in which messages are sent, especially the close event.

- **Error Handling**:

  - Implement error handling to catch any issues during file writing.
  - Use the **Exception Port** of the **FileWriter** to route errors.

- **Concurrency**:

  - If multiple instances of the process might run concurrently, ensure that file names are unique to prevent conflicts.

- **Resource Utilization**:
  - Monitor the system for any resource bottlenecks, especially when handling a large volume of data.

### Conclusion

You have now advanced your understanding of the **FileWriter** component by learning how to control file writing operations using events. By appending data to files and deciding when to close them based on specific conditions, you can create more sophisticated file integration solutions that meet complex business requirements.

---

# Module 4: Selectors and Error Handling

Welcome to Module 4 of the Fiorano Product Training series. In this module, we will explore the concepts of **Selectors** and **Error Handling** in Fiorano. Selectors are used to route messages based on certain conditions, enabling you to create dynamic and flexible integration workflows. Error handling is crucial for creating robust applications that can gracefully handle exceptions and unexpected conditions.

---

## Overview of Module 4

- **4.1 Selectors Part 1**: Message Body XPath
- **4.2 Selectors Part 2**: Application Context XPath
- **4.3 Selectors Part 3**: JMS Property Selectors
- **4.4**: Error Handling in Fiorano

---

## 4.1 Selectors Part 1: Message Body XPath

### Introduction

**Selectors** in Fiorano are used to filter messages flowing through routes based on specific criteria. By applying selectors to routes, you can control the flow of messages and implement content-based routing, where messages are directed to different paths based on their content.

In this session, we will focus on using **Message Body XPath** selectors to route messages based on the content of their body.

### Objectives

- Understand what selectors are and how they are used in Fiorano.
- Learn how to apply Message Body XPath selectors to routes.
- Implement content-based routing using Message Body XPath selectors.
- Test and validate the selector logic within an event process.
- Apply best practices for using selectors in integration workflows.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Basic understanding of XPath expressions and XML data structures.
- Completion of previous modules is recommended.

---

### Scenario Overview

We will create an event process that:

1. Exposes a REST service that accepts a JSON payload containing an **operation** field.
2. Converts the JSON payload to XML for processing.
3. Uses Message Body XPath selectors to route messages to different backend services based on the **operation** field (e.g., `add`, `divide`).
4. Processes the message using the appropriate backend service.
5. Sends the response back to the client.

By the end of this session, you will understand how to implement content-based routing using Message Body XPath selectors.

---

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `SelectorMessageBodyXPath`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **JSON to XML Converter**: Converts JSON payload to XML.
     - Drag and drop the **JSON Converter** component onto the canvas.
   - **Backend Services**: Simulate backend processing with different services.
     - Use two instances of **Sleep** component to represent different backend services (e.g., `AddService`, `DivideService`).
     - Alternatively, use actual backend components if available.

3. **Connect Components**:

   - Draw a route from the **REST Stub** to the **JSON Converter**.
   - From the **JSON Converter**, draw two separate routes to each backend service component.

4. **Add a Return Path**:

   - From each backend service component, draw a route back to the **Response Port** of the **REST Stub**.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter a unique **Service Name**, e.g., `OperationService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/calculate`.
     - **ID**: Optionally, enter `CalculateResource`.
   - **Add Method**:
     - **Method**: Choose **POST**.

4. **Request Representation**:

   - Under **Request**, click **Add Representation**.
   - **Media Type**: Select `application/json`.
   - **Schema**: Define a simple JSON schema.

     - Example:

       ```json
       {
         "operation": "add",
         "valueA": 10,
         "valueB": 5
       }
       ```

   - **Response Representation**:
     - Under **Response**, click **Add Representation**.
     - **Media Type**: Select `application/json`.

5. **Finish Configuration**.

#### Step 3: Configure the JSON Converter Component

1. **Open Configuration**:

   - Double-click on the **JSON Converter** component.

2. **Conversion Direction**:

   - Ensure **Convert JSON to XML** is set to **Yes**.

3. **Provide Output XSD Schema**:

   - Define the XML schema corresponding to the JSON payload.

   - Example XSD:

     ```xml
     <?xml version="1.0" encoding="UTF-8"?>
     <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                 elementFormDefault="qualified">
       <xsd:element name="Request">
         <xsd:complexType>
           <xsd:sequence>
             <xsd:element name="operation" type="xsd:string"/>
             <xsd:element name="valueA" type="xsd:float"/>
             <xsd:element name="valueB" type="xsd:float"/>
           </xsd:sequence>
         </xsd:complexType>
       </xsd:element>
     </xsd:schema>
     ```

   - Paste the XSD into the **Output XSD Schema** field.

4. **Select Root Element**:

   - Click **Select Root Element** and choose `Request`.

5. **Finish Configuration**.

#### Step 4: Configure Selectors on the Routes

We will apply Message Body XPath selectors on the routes from the **JSON Converter** to the backend service components.

1. **Route to AddService**:

   - **Select the Route**: Click on the route connecting **JSON Converter** to the **AddService** component.
   - **Open Properties**:
     - In the **Properties** pane, go to the **Selectors** tab.
   - **Add Selector**:
     - Click on **Message Body XPath**.
     - Click on the **...** button to open the XPath editor.

2. **Define XPath Expression for Addition**:

   - In the **XPath Editor**:

     - **Source Schema**: Should display the XML structure from the **JSON Converter**.
     - **Build Expression**:
       - Drag the `operation` element from the schema to the expression builder.
       - Use the **Equal To** operator (`=`).
       - Click on **Constants** and enter `add`.
     - **Final XPath Expression**:

       ```xpath
       /Request/operation = 'add'
       ```

   - **Save Expression**.

3. **Route to DivideService**:

   - Repeat the steps above for the route to the **DivideService** component.
   - **XPath Expression**:

     ```xpath
     /Request/operation = 'divide'
     ```

   - **Save Expression**.

#### Step 5: Configure the Backend Service Components

Since we're using **Sleep** components to simulate backend services, we'll configure them to output the result.

1. **AddService Configuration**:

   - Open the **Sleep** component representing **AddService**.
   - **Processing Time**: Set to a small value (e.g., `1000` milliseconds).
   - **Custom Configuration**:
     - Use the **Mapper** to perform the addition operation.
     - **Mapping**:
       - Retrieve `valueA` and `valueB` from the message.
       - Calculate the sum and set it in the output message.

2. **DivideService Configuration**:

   - Configure similarly, performing the division operation.

#### Step 6: Configure Response Mapping

1. **From Backend Service to REST Stub Response**:

   - For each route from the backend services to the **REST Stub** response port:

     - Right-click on the route and select **Configure Transformation**.

     - In the **Mapper**:

       - Map the result from the backend service to the response structure expected by the client.

       - Ensure the **Media Type** is set to `application/json`.

2. **Create a Common Response Structure**:

   - Define a response structure, e.g.:

     ```json
     {
       "result": 15
     }
     ```

#### Step 7: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/calculate`).

   - **Test Addition Operation**:

     - **Method**: **POST**.

     - **Headers**:

       - `Content-Type`: `application/json`.

     - **Body**:

       ```json
       {
         "operation": "add",
         "valueA": 10,
         "valueB": 5
       }
       ```

     - **Send Request**.

     - **Verify Response**: Should receive `{ "result": 15 }`.

   - **Test Division Operation**:

     - Change the `operation` field to `divide`.

     - **Body**:

       ```json
       {
         "operation": "divide",
         "valueA": 10,
         "valueB": 5
       }
       ```

     - **Send Request**.

     - **Verify Response**: Should receive `{ "result": 2 }`.

#### Step 8: Validate Selector Functionality

1. **Monitor Message Flow**:

   - Use **Breakpoints** to pause execution at different components.

   - Verify that messages are routed correctly based on the `operation` field.

2. **Testing Default Behavior**:

   - **Test Invalid Operation**:

     - Set `operation` to an unsupported value (e.g., `multiply`).

     - **Result**: Message should not be routed to any backend service.

   - **Handle Unmatched Messages**:

     - Optionally, add a route from the **JSON Converter** to an error handling component to catch unmatched messages.

---

### Best Practices

- **Selector Expressions**:

  - Ensure that XPath expressions are correctly defined and tested.

  - Use absolute paths (starting from the root element) to avoid ambiguity.

- **Consistent Data Structures**:

  - Maintain consistent XML structures for messages to ensure selectors work as intended.

- **Error Handling**:

  - Implement error handling for messages that do not match any selector.

  - Provide meaningful responses or logs for unmatched messages.

- **Testing Edge Cases**:

  - Test with various input values to ensure selectors route messages correctly.

---

### Conclusion

You have successfully implemented content-based routing using Message Body XPath selectors in Fiorano. By applying selectors on routes, you can create dynamic and flexible integration workflows that respond appropriately to different message contents.

Understanding selectors and how to use them effectively is crucial for building sophisticated integration solutions that can handle diverse processing requirements.

---

## Module 4: Selectors and Error Handling

Welcome back to Module 4 of the Fiorano Product Training series. In the previous session, we explored how to use **Message Body XPath** selectors to implement content-based routing based on the message content. In this session, we will delve into how to use **Application Context XPath** selectors to route messages based on data stored in the application context.

---

## 4.2 Selectors Part 2: Application Context XPath

### Introduction

**Application Context** in Fiorano is a shared, in-memory storage area where you can store and retrieve data across different components within the same event process. Unlike message properties that are tied to individual messages, the application context is shared among all messages within the scope of an event process.

**Application Context XPath selectors** allow you to route messages based on data stored in the application context. This is particularly useful when routing decisions depend on data that may not be present in the message body but is available in the application context.

### Objectives

- Understand how to store and retrieve data from the application context.
- Learn how to apply Application Context XPath selectors to routes.
- Implement content-based routing using Application Context XPath selectors.
- Test and validate the selector logic within an event process.
- Apply best practices for using application context and selectors in integration workflows.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Understanding of selectors and their usage in Fiorano (covered in session 4.1).
- Basic knowledge of XPath expressions.
- Completion of previous modules is recommended.

---

### Scenario Overview

We will create an event process that:

1. Exposes a REST service that accepts a request with a query parameter (e.g., `operation`).
2. Stores the `operation` parameter in the application context.
3. Uses Application Context XPath selectors to route messages to different backend services based on the `operation` value stored in the application context.
4. Retrieves data from a database or other backend systems.
5. Sends the response back to the client.

By the end of this session, you will be able to use the application context to implement dynamic routing and understand how it differs from message body-based routing.

---

### Step-by-Step Guide

#### Step 1: Enable Application Context in the Event Process

1. **Open Fiorano Studio (eStudio)** and create a new event process or open an existing one.

2. **Enable Application Context**:

   - Click on the **canvas background** to ensure no component is selected.
   - In the **Properties** pane at the bottom, go to the **Other** tab.
   - Find **Application Context** and set it to **Enabled**.
   - **Save** the event process.

#### Step 2: Set Up the Event Process Canvas

1. **Create or Open an Event Process** named `SelectorApplicationContextXPath`.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **Mapper**: To store data into the application context.
     - Drag and drop the **Mapper** component onto the canvas.
   - **Backend Services**: Simulate different processing paths.
     - Use components such as **Database** connectors or **Sleep** components to represent backend services (e.g., `EmployeeService`, `TransactionService`).

3. **Connect Components**:

   - Draw a route from the **REST Stub** to the **Mapper**.
   - From the **Mapper**, draw two separate routes to each backend service component.
   - From each backend service component, draw a route back to the **Response Port** of the **REST Stub**.

#### Step 3: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `OperationService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/process`.
     - **ID**: Optionally, `ProcessResource`.
   - **Add Method**:
     - **Method**: Choose **GET**.

4. **Request Parameters**:

   - **Add Parameter**:
     - **Name**: `operation`.
     - **Style**: Select `Query`.
     - **Type**: `String`.
     - **Required**: Check if mandatory.

5. **Response Representation**:

   - **Media Type**: Select `application/json`.

6. **Finish Configuration**.

#### Step 4: Configure the Mapper Component to Store Data in Application Context

1. **Open the Mapper Configuration**:

   - Right-click on the route from **REST Stub** to **Mapper**.
   - Select **Configure Transformation**.

2. **Mapper Settings**:

   - **Source Schema**: Represents the request from the **REST Stub**.
   - **Target Schema**: Since we are storing data in the application context, we need to map to it.

3. **Mapping Steps**:

   - **Access Application Context**:
     - In the **Target Schema**, expand **Application Context**.
     - You should see the application context variables.
   - **Map `operation` Parameter to Application Context**:
     - From the **Source Schema**, drag the `operation` parameter.
     - Drop it onto an application context variable you create (e.g., `/ApplicationContext/operation`).

4. **Save** the mapping.

#### Step 5: Configure Selectors on the Routes Using Application Context XPath

1. **Route to EmployeeService**:

   - **Select the Route** from **Mapper** to **EmployeeService**.
   - **Open Properties**:

     - In the **Properties** pane, go to the **Selectors** tab.
       - Click on **Application Context XPath**.

   - **Define XPath Expression**:

     - Click the **...** button to open the XPath editor.
     - **Build Expression**:

       - Use the **Application Context** functions and variables.
       - **Expression**:

         ```xpath
         /ApplicationContext/operation = 'employees'
         ```

     - **Save** the expression.

2. **Route to TransactionService**:

   - Repeat the steps above for the route to **TransactionService**.
   - **XPath Expression**:

     ```xpath
     /ApplicationContext/operation = 'transactions'
     ```

   - **Save** the expression.

#### Step 6: Configure Backend Service Components

Depending on your scenario, configure the backend services to perform the required operations.

1. **Database Components**:

   - If using **Database** components to retrieve data:

     - Configure the **Database Connection** with appropriate connection parameters.

     - **SQL Configuration**:

       - Define **Select** queries based on the operation.

       - For example:

         - **EmployeeService**: `SELECT * FROM employees`

         - **TransactionService**: `SELECT * FROM transactions`

2. **Error Handling**:

   - Ensure that both backend services can handle errors and provide meaningful responses.

#### Step 7: Configure Response Mapping

1. **From Backend Service to REST Stub Response**:

   - For each route from the backend services to the **REST Stub** response port:

     - Right-click on the route and select **Configure Transformation**.

       - **Mapper**:

         - Map the data retrieved from the backend service to the response structure expected by the client.

         - Ensure the **Media Type** is set to `application/json`.

2. **Response Structure**:

   - Define a common response structure or differentiate based on the operation.

   - Example:

     ```json
     {
       "data": [
         // Array of employee or transaction records
       ]
     }
     ```

#### Step 8: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/process`).

   - **Method**: **GET**.

   - **Add Query Parameter**:

     - **Key**: `operation`.

     - **Value**: `employees` or `transactions`.

   - **Send Request**.

   - **Verify Response**:

     - For `operation=employees`, you should receive employee data.

     - For `operation=transactions`, you should receive transaction data.

#### Step 9: Validate Selector Functionality

1. **Monitor Message Flow**:

   - Use **Breakpoints** to pause execution and inspect the application context at various points.

   - Ensure that the `operation` parameter is correctly stored in the application context.

2. **Verify Routing**:

   - Confirm that messages are routed to the correct backend services based on the value in the application context.

3. **Test Invalid Operations**:

   - Try with an invalid `operation` value to see how the system handles it.

   - Optionally, add a default route or error handling for unmatched operations.

---

### Best Practices

- **Consistent Application Context Usage**:

  - Use clear and consistent variable names in the application context.

  - Document the application context variables used in your event process.

- **Avoid Overuse of Application Context**:

  - Use the application context judiciously to prevent unnecessary complexity.

  - Overusing it can make debugging and maintenance more challenging.

- **Security Considerations**:

  - Avoid storing sensitive data in the application context unless necessary.

  - Implement security measures if sensitive data must be stored.

- **Testing and Validation**:

  - Thoroughly test the selector logic with various operation values.

  - Ensure that the application context is correctly populated and accessed.

---

### Conclusion

You have learned how to use Application Context XPath selectors in Fiorano to route messages based on data stored in the application context. By leveraging the application context, you can make routing decisions based on data that may not be present in the message body, providing greater flexibility in your integration workflows.

Understanding the difference between message body selectors and application context selectors allows you to choose the appropriate approach based on your specific requirements.

---

## Module 4: Selectors and Error Handling

Welcome back to Module 4 of the Fiorano Product Training series. In the previous sessions, we explored how to use **Message Body XPath** and **Application Context XPath** selectors to implement content-based routing based on message content and application context variables. In this session, we will delve into using **JMS Property Selectors** to route messages based on message properties and headers.

---

## 4.3 Selectors Part 3: JMS Property Selectors

### Introduction

**JMS Properties** are custom key-value pairs that can be associated with messages in Fiorano. Unlike the message body, which contains the main data payload, message properties are metadata attached to the message header. **JMS Property Selectors** allow you to route messages based on these properties, enabling you to make routing decisions based on metadata rather than the content.

Using JMS Property Selectors is particularly useful when:

- You need to route messages based on headers or properties set by upstream systems.
- The routing criteria are not part of the message body.
- You want to avoid altering the message body for routing purposes.

### Objectives

- Understand how to set and retrieve JMS properties in messages.
- Learn how to apply JMS Property Selectors to routes.
- Implement content-based routing using JMS Property Selectors.
- Test and validate the selector logic within an event process.
- Apply best practices for using JMS properties and selectors in integration workflows.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Understanding of selectors and their usage in Fiorano (covered in previous sessions).
- Basic knowledge of JMS concepts.
- Completion of previous modules is recommended.

---

### Scenario Overview

We will create an event process that:

1. Exposes a REST service that accepts a request with a query parameter (e.g., `function`).
2. Stores the `function` parameter as a JMS property.
3. Uses JMS Property Selectors to route messages to different backend services based on the `function` property.
4. Processes the message using the appropriate backend service.
5. Sends the response back to the client.

By the end of this session, you will be able to use JMS properties to implement dynamic routing and understand how they differ from message body and application context selectors.

---

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `SelectorJMSProperty`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **Mapper**: To set the JMS property.
     - Drag and drop the **Mapper** component onto the canvas.
   - **Backend Services**: Simulate different processing paths.
     - Use components such as **Database** connectors or **Sleep** components to represent backend services (e.g., `UserService`, `ProductService`).

3. **Connect Components**:

   - Draw a route from the **REST Stub** to the **Mapper**.
   - From the **Mapper**, draw two separate routes to each backend service component.
   - From each backend service component, draw a route back to the **Response Port** of the **REST Stub**.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `FunctionService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/process`.
     - **ID**: Optionally, `ProcessResource`.
   - **Add Method**:
     - **Method**: Choose **GET**.

4. **Request Parameters**:

   - **Add Parameter**:
     - **Name**: `function`.
     - **Style**: Select `Query`.
     - **Type**: `String`.
     - **Required**: Check if mandatory.

5. **Response Representation**:

   - **Media Type**: Select `application/json`.

6. **Finish Configuration**.

#### Step 3: Configure the Mapper Component to Set JMS Property

1. **Open the Mapper Configuration**:

   - Right-click on the route from **REST Stub** to **Mapper**.
   - Select **Configure Transformation**.

2. **Mapper Settings**:

   - **Source Schema**: Represents the request from the **REST Stub**.
   - **Target Schema**: We need to map to JMS properties.

3. **Mapping Steps**:

   - **Set JMS Property**:
     - In the **Target Schema**, expand **Properties**.
     - **Add Function**:
       - From **Mapping Functions**, expand **JMS Message Functions**.
       - Select **Set String Property** or **Set Property** (based on data type).
     - **Configure the Function**:
       - **Name**: Enter the property name, e.g., `function`.
       - **Value**: Map the `function` parameter from the **Source Schema**.
     - **Assign to **Properties\*\*\*\*:
       - Drag the result of the function to the **Properties** node in the **Target Schema**.

4. **Save** the mapping.

#### Step 4: Configure Selectors on the Routes Using JMS Property Selectors

1. **Route to UserService**:

   - **Select the Route** from **Mapper** to **UserService**.
   - **Open Properties**:

     - In the **Properties** pane, go to the **Selectors** tab.
       - Click on **JMS** under **Selectors**.

   - **Define Selector Expression**:

     - Enter the JMS selector expression:

       ```
       function = 'users'
       ```

   - **Save** the expression.

2. **Route to ProductService**:

   - Repeat the steps above for the route to **ProductService**.
   - **Selector Expression**:

     ```
     function = 'products'
     ```

   - **Save** the expression.

#### Step 5: Configure Backend Service Components

Configure the backend services to perform the required operations based on the `function` value.

1. **UserService**:

   - If using a **Database** component:

     - **SQL Configuration**:

       - Define a **Select** query:

         ```sql
         SELECT * FROM users
         ```

2. **ProductService**:

   - **SQL Configuration**:

     - Define a **Select** query:

       ```sql
       SELECT * FROM products
       ```

#### Step 6: Configure Response Mapping

1. **From Backend Service to REST Stub Response**:

   - For each route from the backend services to the **REST Stub** response port:

     - Right-click on the route and select **Configure Transformation**.

       - **Mapper**:

         - Map the data retrieved from the backend service to the response structure expected by the client.

         - Ensure the **Media Type** is set to `application/json`.

2. **Response Structure**:

   - Define a common response structure with appropriate data.

---

#### Step 7: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/process`).

   - **Method**: **GET**.

   - **Add Query Parameter**:

     - **Key**: `function`.

     - **Value**: `users` or `products`.

   - **Send Request**.

   - **Verify Response**:

     - For `function=users`, you should receive user data.

     - For `function=products`, you should receive product data.

5. **Test with Invalid Function**:

   - Try with `function=orders` to see how the system handles unsupported functions.

---

#### Step 8: Validate Selector Functionality

1. **Monitor Message Flow**:

   - Use **Breakpoints** to inspect the JMS properties in the message headers at different stages.

   - Confirm that the `function` property is correctly set and used in selectors.

2. **Verify Routing**:

   - Ensure that messages are routed to the appropriate backend services based on the `function` JMS property.

3. **Unmatched Messages**:

   - Optionally, add an error handling route to capture messages with invalid or unsupported `function` values.

---

### Best Practices

- **Consistent Property Naming**:

  - Use clear and consistent property names.

  - Be aware that JMS property names are case-sensitive in selectors.

- **Avoid Overuse of Properties**:

  - Use message properties judiciously to prevent overhead.

  - Do not store large amounts of data in message properties.

- **Security Considerations**:

  - Be cautious about storing sensitive data in message properties.

- **Error Handling**:

  - Implement mechanisms to handle messages that do not match any selector criteria.

  - Provide meaningful error responses to the client.

- **Testing**:

  - Test with various `function` values to ensure the selectors work correctly.

- **Documentation**:

  - Document the JMS properties used and their purposes for future maintenance.

---

### Conclusion

You have successfully learned how to use JMS Property Selectors in Fiorano to route messages based on message properties. By leveraging JMS properties, you can implement dynamic routing decisions based on metadata, providing flexibility when message content or application context is not suitable for routing criteria.

Understanding the different types of selectors—Message Body XPath, Application Context XPath, and JMS Property Selectors—allows you to choose the most appropriate method for your integration scenarios.

---

## Module 4: Selectors and Error Handling

Welcome back to Module 4 of the Fiorano Product Training series. In the previous sessions, we explored how to use selectors in Fiorano to implement content-based routing based on different criteria such as message body, application context, and JMS properties. In this session, we will focus on **Error Handling** in Fiorano, which is crucial for building robust and resilient integration solutions.

---

## 4.4 Error Handling in Fiorano

### Introduction

In any integration workflow, errors and exceptions are inevitable. Effective error handling ensures that your event processes can gracefully handle exceptions, log errors, and inform appropriate stakeholders or systems about the issues. Fiorano provides mechanisms to handle errors at both the component level and the event process level, allowing you to design workflows that can recover from errors or fail safely.

### Objectives

- Understand the importance of error handling in integration workflows.
- Learn how to enable and use **Exception Ports** in Fiorano components.
- Configure error handling mechanisms in your event processes.
- Implement retry mechanisms and error notifications.
- Apply best practices for designing robust error handling strategies.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Completion of previous modules is recommended.
- Basic understanding of Fiorano components and routes.

---

### Overview of Error Handling in Fiorano

In Fiorano, error handling involves:

- **Exception Ports**: Special output ports on components that emit messages when an error occurs within the component.
- **Error Handling Configurations**: Settings within components that allow you to define how errors are managed, such as retries and logging.
- **Error Routes**: Routes connected to exception ports that define how error messages are processed within the event process.

By leveraging these features, you can design workflows that:

- Retry operations in case of transient errors.
- Log errors for auditing and troubleshooting.
- Notify systems or users of critical errors.
- Continue processing other messages despite errors.

---

### Step-by-Step Guide

#### Scenario Overview

We will create an event process that simulates an error scenario and implements error handling mechanisms. The event process will:

1. Expose a REST service that accepts input.
2. Use a **Database** component to perform an operation that may fail (e.g., due to connection issues or invalid queries).
3. Enable the **Exception Port** on the Database component to handle errors.
4. Configure retry mechanisms for the Database component.
5. Route errors to an error-handling component (e.g., a **Logger** or **REST Stub** for sending error responses).

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `ErrorHandlingExample`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **Database**: Performs database operations.
     - Drag and drop the **DB** component onto the canvas.
   - **Error Handling Component**: Handles error messages.
     - Use a **Display**, **Logger**, or another **REST Stub** to simulate error handling.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **Database** component.
   - Draw a route from the **Output Port** of the **Database** component to the **Response Port** of the **REST Stub**.

---

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `ErrorHandlingService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/process`.
     - **ID**: Optionally, `ProcessResource`.
   - **Add Method**:
     - **Method**: Choose **POST**.

4. **Request Representation**:

   - **Media Type**: Select `application/json`.
   - **Schema**: Define a simple JSON schema if needed.

5. **Response Representation**:

   - **Media Type**: Select `application/json`.

6. **Finish Configuration**.

---

#### Step 3: Configure the Database Component

1. **Open Configuration**:

   - Double-click on the **Database** component.

2. **Database Connection**:

   - **DB URL**: Enter the JDBC URL of your database. Intentionally use an incorrect URL or credentials to simulate a connection error.
   - **DB User**: Enter an invalid username to simulate authentication failure.
   - **DB Password**: Enter an invalid password.

3. **Test Connection**:

   - Click **Test**. It should fail, indicating that there is a connection issue.

4. **Error Handling Configuration**:

   - Navigate to the **Error Handling** tab.

   - **Retry on Connection Error**:

     - Enable **Retry on Connection Error**.
     - **Number of Retries**: Set to `2`.
     - **Retry Interval**: Set to `5000` milliseconds (5 seconds).

   - **Retry on Invalid Request**:

     - Enable **Retry on Invalid Request** if you want to retry on SQL statement errors.

5. **Enable Exception Port**:

   - Click on the **Exception Ports** icon on the Database component in the canvas toolbar.

     - It looks like a small red triangle or exclamation mark.

     - This will toggle the visibility of the **Exception Port**.

6. **Finish Configuration**.

---

#### Step 4: Connect the Exception Port to an Error Handling Component

1. **Add the Error Handling Component**:

   - For this example, drag and drop a **Display** component onto the canvas to simulate error logging.

2. **Draw a Route from the Exception Port**:

   - From the **Exception Port** (usually a red port on the component) of the **Database** component, draw a route to the **Input Port** of the **Display** component.

3. **Configure the Error Handling Route** (Optional):

   - **Mapping**:

     - You can configure a transformation on the error route to extract error details and format them appropriately.

     - Right-click on the route from the **Exception Port** to the **Display** component and select **Configure Transformation**.

     - In the **Mapper**, you can map error properties to the fields expected by the **Display** component.

---

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

---

#### Step 6: Test the Error Handling Mechanism

1. **Use Postman or Another REST Client**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/process`).
   - **Method**: **POST**.
   - **Headers**:
     - `Content-Type`: `application/json`.
   - **Body**:
     - Provide a JSON payload as per your REST Stub configuration.

2. **Send the Request**.

3. **Observe the Behavior**:

   - The **Database** component will attempt to connect and perform the operation, but it will fail due to invalid connection parameters.

   - **Retry Mechanism**:

     - The **Database** component will retry the operation according to the settings (2 retries with 5 seconds interval).

   - **Exception Port Activation**:

     - After the retries are exhausted, the error will be emitted through the **Exception Port**.

4. **View the Error Message**:

   - Open the **Display** component to see the error message.

   - The message will contain details about the error, such as error code, error message, and stack trace.

---

#### Step 7: Handling Errors in the REST Response (Optional)

1. **Send an Error Response to the Client**:

   - Instead of the **Display** component, you can route the error back to the **Response Port** of the **REST Stub**.

   - Draw a route from the **Exception Port** of the **Database** component to the **Response Port** of the **REST Stub**.

2. **Configure Error Response Mapping**:

   - **Mapper**:

     - Map the error details to a JSON structure suitable for the client.

     - For example:

       ```json
       {
         "status": "error",
         "errorCode": "DB_CONN_ERROR",
         "errorMessage": "Unable to connect to the database."
       }
       ```

   - **Set HTTP Status Code**:

     - In the response mapping, set the appropriate HTTP status code (e.g., `500 Internal Server Error`).

3. **Test the Error Response**:

   - Send the request again and verify that the client receives the error response with the correct status code and message.

---

### Best Practices

- **Enable Exception Ports**:

  - Always enable exception ports on components where errors can occur.

- **Implement Retry Mechanisms**:

  - Configure retries for transient errors, such as network issues or temporary unavailability of resources.

  - Be cautious with retry counts to avoid overloading systems.

- **Error Logging**:

  - Log errors for troubleshooting and auditing purposes.

  - Include relevant error details without exposing sensitive information.

- **Notify Appropriate Parties**:

  - Use error handling components to send notifications to administrators or monitoring systems.

- **Graceful Degradation**:

  - Design your workflows to handle errors gracefully, possibly by providing default responses or alternative processing paths.

- **Avoid Unhandled Exceptions**:

  - Ensure that all possible error scenarios are accounted for and that there are no unhandled exceptions that could cause the event process to fail unexpectedly.

- **Security Considerations**:

  - Do not include sensitive information, such as database credentials or personal data, in error messages sent to clients.

---

### Conclusion

You have learned how to implement error handling in Fiorano event processes using exception ports, retry mechanisms, and error handling components. Effective error handling is crucial for building robust integration solutions that can handle unexpected conditions and provide meaningful feedback to users and systems.

By incorporating error handling strategies, you can enhance the reliability and maintainability of your integration workflows, ensuring they meet the demands of enterprise environments.

---

# Module 5: Email and File Transfer Protocols

Welcome to Module 5 of the Fiorano Product Training series. In this module, we will explore how to handle emails and file transfers using protocols like SMTP, POP3, IMAP, and FTP. Integrating with email systems and file servers is a common requirement in enterprise environments, enabling automated communication and data exchange with external systems.

---

## 5.1 Sending Emails using SMTP

### Introduction

In this session, we will learn how to send emails using Fiorano's **SMTP** component. The Simple Mail Transfer Protocol (SMTP) is a standard protocol for sending emails over the internet. Integrating email functionality into your Fiorano workflows allows you to automate notifications, alerts, and other communications with users or systems.

### Objectives

- Understand how to configure the **SMTP** component in Fiorano.
- Learn how to send emails using the SMTP component.
- Configure email properties such as sender, recipient, subject, and body.
- Test and validate email sending within an event process.
- Apply best practices for secure and efficient email integration.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Access to an SMTP server for sending emails.
  - This can be a public SMTP server like Gmail or a corporate SMTP server.
- Basic knowledge of email protocols and settings.

### Step-by-Step Guide

#### Scenario Overview

We will create an event process that:

1. Receives input data (e.g., email content) from a **Feeder** or **REST Stub** component.
2. Uses the **SMTP** component to send emails.
3. Configures email properties such as sender, recipient, subject, and message body.
4. Tests the email sending functionality.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `SendEmailUsingSMTP`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **Feeder** or **REST Stub**: Acts as the message source.

     - For interactive input, use a **Feeder** component.
     - For exposing a service, use a **REST Stub** component.

   - **SMTP**: Sends emails using SMTP.

     - In the **Microservice Palette**, search for **SMTP** under the **Mail** category.
     - Drag and drop the **SMTP** component onto the canvas.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **Feeder** or **REST Stub** to the **Input Port** of the **SMTP** component.

#### Step 2: Configure the SMTP Component

1. **Open Configuration**:

   - Double-click on the **SMTP** component to open its configuration window.

2. **Protocol Selection**:

   - **Protocol**: Ensure that **SMTP** is selected.

3. **Connection Configuration**:

   - **Mail Server**: Enter the hostname or IP address of your SMTP mail server.
     - Example: `smtp.gmail.com` for Gmail.
   - **Port**: Enter the port number used by the SMTP server.
     - Common ports are `25`, `465`, or `587`.
   - **Use SSL/TLS**:

     - Enable **Use SSL** if the SMTP server requires a secure connection (common for port `465`).
     - Enable **Use TLS** if required (common for port `587`).

   - **Authentication Required**:

     - Check this option if authentication is required.
     - **User Name**: Enter your email username (e.g., `yourname@gmail.com`).
     - **Password**: Enter your email password or an application-specific password if required.

   - **Test Connection**:

     - Click **Test** to verify the connection to the SMTP server.
     - Resolve any issues if the test fails (e.g., incorrect credentials, network connectivity).

4. **Email Message Configuration**:

   - **From**: Specify the sender's email address.

     - Example: `yourname@gmail.com`.

   - **To**: Specify the recipient's email address.

     - Example: `recipient@example.com`.
     - Multiple recipients can be separated by commas.

   - **Subject**: Enter a default subject line (can be overridden dynamically).

   - **Message Type**:

     - Choose between **Text Message** or **HTML Message** based on your needs.

   - **Message Body**:

     - Enter a default message body (can be overridden dynamically).
     - This field supports message substitutions if needed.

5. **Advanced Configurations** (Optional):

   - **CC** and **BCC**: Add carbon copy or blind carbon copy recipients.

   - **Attachments**:

     - Configure if you need to send attachments via email.

6. **Finish Configuration**:

   - Click **Finish** to save the configuration.

#### Step 3: Configure Dynamic Email Properties (Optional)

To set email properties dynamically during runtime (e.g., from the message), you need to map the input data to the SMTP component's properties.

1. **Configure Transformation on the Route**:

   - Right-click on the route from the **Feeder** or **REST Stub** to the **SMTP** component and select **Configure Transformation**.

2. **Mapper Configuration**:

   - **Source Schema**: Represents the input message from the **Feeder** or **REST Stub**.
   - **Target Schema**: Represents the SMTP component's input parameters.

3. **Mapping Steps**:

   - Map fields from the source to the SMTP component properties:
     - **From**: Map the sender's email address if provided in the input.
     - **To**: Map the recipient's email address.
     - **Subject**: Map the email subject.
     - **Body**: Map the email message body.
     - **Attachments**: Map any attachment file paths if required.

4. **Save** the mapping.

#### Step 4: Configure the Feeder or REST Stub Component

1. **Feeder Component**:

   - **Open the Feeder**:
     - Double-click on the **Feeder** component.
   - **Input Message**:
     - Enter the message content or structured data (e.g., XML or JSON) matching the expected source schema.
   - **Message Properties** (Optional):
     - Set any properties required for mapping dynamic email fields.

2. **REST Stub Component**:

   - **Configure the REST Service**:

     - Define the **Service Name**, **Resources**, and **Methods**.

   - **Request Representation**:

     - Define the input schema (e.g., JSON) that includes email fields.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Send Test Data**:

   - **Feeder**:

     - Enter the test email data and click **Send**.

   - **REST Client**:

     - Use Postman or another REST client to send data to the REST endpoint.
     - **Method**: **POST**.
     - **URL**: Your REST Stub's endpoint URL.
     - **Headers**:

       - Set `Content-Type` header matching the media type configured.

     - **Body**:

       - Provide the email data in the body.

5. **Verify Email Receipt**:

   - Check the recipient's inbox to confirm that the email was received.

   - Verify that all email properties (subject, body, etc.) are correct.

#### Step 6: Troubleshooting

1. **View Logs**:

   - Right-click on the **SMTP** component and select **View Logs**.

   - Check **Output Logs** and **Error Logs** for any issues.

2. **Common Issues**:

   - **Authentication Errors**:

     - Verify the username and password.
     - For Gmail, you may need to allow less secure apps or use an app password.

   - **Connection Errors**:

     - Ensure network connectivity to the SMTP server.
     - Check firewall settings that may block SMTP ports.

   - **Invalid Email Addresses**:

     - Verify that the sender and recipient email addresses are correct.

   - **SSL/TLS Issues**:

     - Adjust SSL/TLS settings based on the SMTP server requirements.

#### Step 7: Security Considerations

- **Credentials Management**:

  - Avoid hardcoding sensitive information like passwords.
  - Use secure configurations or credential management systems if possible.

- **Email Content**:

  - Be cautious when sending sensitive data via email.
  - Ensure compliance with data protection policies.

- **Spam Prevention**:

  - Avoid sending bulk emails that may be flagged as spam.
  - Ensure proper email headers and formatting.

### Best Practices

- **Testing with Mock Servers**:

  - Use mock SMTP servers for testing to avoid sending test emails to real recipients.

- **Error Handling**:

  - Enable exception ports on the **SMTP** component to handle sending errors.
  - Implement error handling logic to retry or log failures.

- **Dynamic Configuration**:

  - Utilize message mappings to set email properties dynamically based on input data.

- **Logging and Monitoring**:

  - Keep logs of sent emails for auditing purposes.
  - Monitor the SMTP component for any issues during operation.

### Conclusion

You have successfully learned how to send emails using the **SMTP** component in Fiorano. Integrating email functionality into your workflows enables you to automate communications, alerts, and notifications, enhancing the responsiveness and interactivity of your integration solutions.

By mastering the configuration and use of the SMTP component, you can expand the capabilities of your Fiorano applications to include email communications.

---

## 5.2 Receiving Emails using POP3

### Introduction

In this session, we will learn how to receive emails using Fiorano's **POP3** component. The Post Office Protocol version 3 (POP3) is a standard protocol for receiving emails from a remote mail server over a TCP/IP connection. Integrating the ability to receive emails allows your workflows to react to incoming communications.

### Objectives

- Understand how to configure the **POP3** component in Fiorano.
- Learn how to receive emails and process them within an event process.
- Configure email retrieval properties such as server settings, authentication, and message processing.
- Test and validate email reception within an event process.
- Apply best practices for secure and efficient email integration.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Access to a POP3 mail server.
  - This can be a public email service that supports POP3 or a corporate mail server.
- Basic knowledge of email protocols and settings.

### Step-by-Step Guide

#### Scenario Overview

We will create an event process that:

1. Uses the **POP3** component to retrieve emails from a specified mailbox.
2. Processes the received email content.
3. Optionally moves or deletes emails after processing.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `ReceiveEmailUsingPOP3`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **POP3**: Receives emails from a mail server.

     - In the **Microservice Palette**, search for **POP3** under the **Mail** category.
     - Drag and drop the **POP3** component onto the canvas.

   - **Display** (Optional): To display the received email content.

     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **POP3** component to the **Input Port** of the **Display** component.

#### Step 2: Configure the POP3 Component

1. **Open Configuration**:

   - Double-click on the **POP3** component to open its configuration window.

2. **Protocol Selection**:

   - **Protocol**: Select **POP3**.

3. **Connection Configuration**:

   - **Mail Server**: Enter the hostname or IP address of your POP3 mail server.
     - Example: `pop.gmail.com` for Gmail.
   - **Port**: Enter the port number used by the POP3 server.
     - Default port is `110` for POP3.
     - For secure connections (POP3 over SSL/TLS), the port is typically `995`.
   - **Use SSL/TLS**:

     - Enable **Use SSL** if the POP3 server requires a secure connection.
     - Adjust any additional security settings as needed.

   - **Authentication Configuration**:

     - **User Name**: Enter your email username.
     - **Password**: Enter your email password or an app-specific password.

   - **Test Connection**:

     - Click **Test** to verify the connection to the POP3 server.
     - Resolve any issues if the test fails.

4. **Mail Retrieval Configuration**:

   - **Operation**: Choose **ReceiveMail** to retrieve emails.

   - **Message Retrieval Options**:

     - **Delete Messages**: Decide whether to delete emails from the server after retrieval.
     - **Max Message Size**: Set the maximum size of messages to retrieve.
     - **Message Count**: Specify which messages to retrieve.
       - A positive integer to retrieve a specific message.
       - `-1` to retrieve all messages.

   - **Advanced Settings** (Optional):

     - **Ignore Attachments**: Enable if you do not wish to download attachments.
     - **Fetch Headers Only**: Enable if you only need email headers.

5. **Finish Configuration**:

   - Click **Finish** to save the configuration.

#### Step 3: Configure the Route and Display Component (Optional)

1. **Configure Transformation (Optional)**:

   - If you need to process or transform the email content, configure the route accordingly.

2. **Display Component**:

   - The **Display** component will show the content of the emails received by the **POP3** component.

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Monitor Email Retrieval**:

   - The **POP3** component will attempt to connect to the mail server and retrieve emails based on your configuration.

5. **View Received Emails**:

   - Double-click on the **Display** component to view the email content.
   - Messages will be displayed as they are retrieved.

#### Step 5: Troubleshooting

1. **View Logs**:

   - Right-click on the **POP3** component and select **View Logs**.

   - Check **Output Logs** and **Error Logs** for any issues.

2. **Common Issues**:

   - **Authentication Errors**:

     - Verify the username and password.
     - For Gmail and other providers, you may need to enable POP3 access in account settings.
     - May require app-specific passwords.

   - **Connection Errors**:

     - Ensure network connectivity to the mail server.
     - Check firewall settings that may block POP3 ports.

   - **SSL/TLS Issues**:

     - Adjust security settings based on the mail server requirements.

#### Step 6: Security Considerations

- **Credentials Management**:

  - Avoid hardcoding sensitive information like passwords.
  - Use secure configurations or credential management systems if possible.

- **Email Content**:

  - Be cautious when processing emails that may contain sensitive data.
  - Implement security measures to handle potential threats (e.g., malware in attachments).

### Best Practices

- **Secure Connections**:

  - Use SSL/TLS to secure communications with the mail server.

- **Error Handling**:

  - Enable exception ports on the **POP3** component to handle errors.
  - Implement logic to manage connection failures or message retrieval issues.

- **Message Management**:

  - Decide whether to delete emails after processing to prevent duplicate processing.
  - Use message IDs or timestamps to track processed emails.

- **Logging and Monitoring**:

  - Keep logs of retrieved emails for auditing purposes.
  - Monitor the **POP3** component for any issues during operation.

### Conclusion

You have successfully learned how to receive emails using the **POP3** component in Fiorano. This capability allows your integration workflows to react to incoming emails, enabling a wide range of applications such as automated processing of orders, support tickets, or notifications.

By integrating email reception into your workflows, you can enhance the interactivity and responsiveness of your integration solutions.

---

## 5.3 Receiving Emails using IMAP

### Introduction

In this session, we will learn how to receive emails using Fiorano's **POP3** component configured with the **IMAP** protocol. The Internet Message Access Protocol (IMAP) is a standard protocol for accessing email messages stored on a mail server. IMAP provides more advanced features compared to POP3, such as the ability to access multiple folders and manage messages directly on the server.

### Objectives

- Understand how to configure the **POP3** component to use the IMAP protocol.
- Learn how to receive emails from specific folders using IMAP.
- Configure email retrieval properties such as server settings, authentication, and message processing.
- Test and validate email reception within an event process.
- Apply best practices for secure and efficient email integration.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Access to an IMAP mail server.
  - This can be a public email service that supports IMAP or a corporate mail server.
- Basic knowledge of email protocols and settings.

### Step-by-Step Guide

#### Scenario Overview

We will create an event process that:

1. Uses the **POP3** component configured for IMAP to retrieve emails from a specified folder.
2. Processes the received email content.
3. Optionally moves or deletes emails after processing.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `ReceiveEmailUsingIMAP`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **POP3**: Receives emails from a mail server.

     - In the **Microservice Palette**, search for **POP3** under the **Mail** category.
     - Drag and drop the **POP3** component onto the canvas.

   - **Display** (Optional): To display the received email content.

     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **POP3** component to the **Input Port** of the **Display** component.

#### Step 2: Configure the POP3 Component for IMAP

1. **Open Configuration**:

   - Double-click on the **POP3** component to open its configuration window.

2. **Protocol Selection**:

   - **Protocol**: Select **IMAP**.

3. **Connection Configuration**:

   - **Mail Server**: Enter the hostname or IP address of your IMAP mail server.
     - Example: `imap.gmail.com` for Gmail.
   - **Port**: Enter the port number used by the IMAP server.
     - Default port is `143` for IMAP.
     - For secure connections (IMAP over SSL/TLS), the port is typically `993`.
   - **Use SSL/TLS**:

     - Enable **Use SSL** if the IMAP server requires a secure connection.
     - Adjust any additional security settings as needed.

   - **Authentication Configuration**:

     - **User Name**: Enter your email username.
     - **Password**: Enter your email password or an app-specific password.

4. **Mail Retrieval Configuration**:

   - **Folder to Pick Mails**: Enter the folder from which to retrieve emails.
     - Examples: `INBOX`, `Sent Items`, `Archive`.
   - **Operation**: Choose **ReceiveMail** to retrieve emails.

   - **Message Retrieval Options**:

     - Similar to the POP3 configuration.

5. **Finish Configuration**:

   - Click **Finish** to save the configuration.

#### Step 3: Configure the Route and Display Component (Optional)

1. **Configure Transformation (Optional)**:

   - If you need to process or transform the email content, configure the route accordingly.

2. **Display Component**:

   - The **Display** component will show the content of the emails received by the **POP3** component.

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Monitor Email Retrieval**:

   - The **POP3** component will attempt to connect to the mail server and retrieve emails based on your configuration.

5. **View Received Emails**:

   - Double-click on the **Display** component to view the email content.
   - Messages will be displayed as they are retrieved.

#### Step 5: Troubleshooting

1. **View Logs**:

   - Right-click on the **POP3** component and select **View Logs**.

   - Check **Output Logs** and **Error Logs** for any issues.

2. **Common Issues**:

   - **Authentication Errors**:

     - Verify the username and password.
     - For Gmail and other providers, you may need to enable IMAP access in account settings.
     - May require app-specific passwords.

   - **Connection Errors**:

     - Ensure network connectivity to the mail server.
     - Check firewall settings that may block IMAP ports.

   - **Folder Access Issues**:

     - Ensure that the specified folder exists and that your account has permission to access it.

   - **SSL/TLS Issues**:

     - Adjust security settings based on the mail server requirements.

#### Step 6: Security Considerations

- **Credentials Management**:

  - Avoid hardcoding sensitive information like passwords.
  - Use secure configurations or credential management systems if possible.

- **Email Content**:

  - Be cautious when processing emails that may contain sensitive data.
  - Implement security measures to handle potential threats (e.g., malware in attachments).

### Best Practices

- **Secure Connections**:

  - Use SSL/TLS to secure communications with the mail server.

- **Folder Management**:

  - Utilize IMAP's ability to access specific folders to organize email processing.

- **Error Handling**:

  - Enable exception ports on the **POP3** component to handle errors.
  - Implement logic to manage connection failures or message retrieval issues.

- **Message Management**:

  - Decide whether to mark emails as read or move them to another folder after processing.

- **Logging and Monitoring**:

  - Keep logs of retrieved emails for auditing purposes.
  - Monitor the **POP3** component for any issues during operation.

### Conclusion

You have successfully learned how to receive emails using the **POP3** component configured for IMAP in Fiorano. IMAP provides greater flexibility and control over email retrieval, allowing you to access specific folders and manage messages on the server.

By integrating email reception into your workflows using IMAP, you can enhance the interactivity and responsiveness of your integration solutions, and implement more sophisticated email processing scenarios.

---

## 5.4 FTPGet (Integrating with File Servers) Part 1

### Introduction

In this session, we will explore how to download files from an FTP server using Fiorano's **FTPGet** component. Integrating with file servers allows your workflows to access files stored remotely, enabling data exchange and processing of files in your integration scenarios.

### Objectives

- Understand how to use the **FTPGet** component to download files from an FTP server.
- Configure FTP connection settings, including authentication and transfer types.
- Use dynamic configurations to specify the source and destination paths.
- Test and validate file download within an event process.
- Apply best practices for secure and efficient file transfer.

### Prerequisites

- Fiorano Studio (eStudio) installed and connected to the Enterprise Server.
- Access to an FTP server with files to download.
  - This can be a public FTP server or an internal corporate server.
- Basic knowledge of FTP protocols and settings.

### Step-by-Step Guide

#### Scenario Overview

We will create an event process that:

1. Receives input data specifying files to download.
2. Uses the **FTPGet** component to download files from an FTP server to a local directory.
3. Configures FTP connection and file transfer settings.
4. Tests the file download functionality.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `FTPGetIntegration`.
   - **Category**: Choose or create a package, e.g., `FioranoTraining`.
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub** or **Feeder**: Acts as the message source.

     - For dynamic input, use a **REST Stub** component.
     - For interactive testing, use a **Feeder** component.

   - **JSON Converter** (Optional): If you're receiving input in JSON format and need to convert it to XML for processing.

     - Drag and drop the **JSON Converter** component onto the canvas.

   - **FTPGet**: Downloads files from an FTP server.

     - In the **Microservice Palette**, search for **FTPGet** under the **File** category.
     - Drag and drop the **FTPGet** component onto the canvas.

   - **Display** (Optional): To display the result of the operation.

     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - **From REST Stub/Feeder to FTPGet**:

     - Draw a route from the **Output Port** of the **REST Stub** or **Feeder** to the **Input Port** of the **FTPGet** component.

   - **From FTPGet to Display** (Optional):

     - Draw a route from the **Output Port** of the **FTPGet** component to the **Input Port** of the **Display** component.

#### Step 2: Configure the FTPGet Component

1. **Open Configuration**:

   - Double-click on the **FTPGet** component to open its configuration window.

2. **Connection Configuration**:

   - **Protocol**: Select **FTP** (or **SFTP**/**FTPS** if using secure protocols).

   - **Remote Host**: Enter the hostname or IP address of your FTP server.

     - Example: `ftp.example.com`.

   - **Port**: Enter the port number used by the FTP server.

     - Default port is `21` for FTP.

   - **Login**: Enter your FTP username.

   - **Password**: Enter your FTP password.

   - **Test Connection**:

     - Click **Test** to verify the connection to the FTP server.
     - Resolve any issues if the test fails.

3. **Transfer Configuration**:

   - **Response Type**: Choose **File** if downloading files.

   - **Post Processing Action**: Decide what to do with files after download.

     - Options: **No Action**, **Delete**, **Move**.

   - **Enable Debug Responses** (Optional):

     - Enable this option to receive detailed logs, useful for troubleshooting.

4. **Finish Configuration**:

   - Click **Finish** to save the configuration.

#### Step 3: Configure Dynamic File Paths

To specify the files to download and their destination paths dynamically, you can use mappings.

1. **Configure Transformation to FTPGet Component**:

   - Right-click on the route to the **FTPGet** component and select **Configure Transformation**.

2. **Mapper Configuration**:

   - **Source Schema**: Represents the input message from the **REST Stub** or **Feeder**.
   - **Target Schema**: Represents the **FTPGet** component's input parameters.

3. **Mapping Steps**:

   - Map the source fields to the FTPGet parameters:

     - **Local Directory**: Path on your local machine where the file will be saved.

     - **Local File Name**: Name of the file to save as locally.

     - **Source Directory**: Path on the FTP server to the file, including directories and file name.

     - **Transfer Type**:

       - Typically **Binary** for non-text files.
       - Map accordingly.

4. **Sample Input Data**:

   - Prepare JSON input with fields like `localDirectory`, `localFileName`, `sourceDirectory`, `transferType`.

5. **Save** the mapping.

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Send Test Data**:

   - **Feeder**:

     - Enter the JSON input data specifying the file paths.
     - Example:
       ```json
       {
         "localDirectory": "C:\\Fiorano\\DownloadedFiles",
         "localFileName": "example.txt",
         "sourceDirectory": "/remote/files/example.txt",
         "transferType": "Binary"
       }
       ```
     - Click **Send**.

   - **REST Client**:

     - Use Postman or another REST client to send data to the REST endpoint.
     - Configure appropriately.

5. **Verify File Download**:

   - Check the local directory to confirm that the file has been downloaded.
   - Verify that the file content matches the source file.

6. **View Output (Optional)**:

   - If using the **Display** component, double-click to see any messages or confirmations.

#### Step 5: Troubleshooting

1. **View Logs**:

   - Right-click on the **FTPGet** component and select **View Logs**.

   - Check **Output Logs** and **Error Logs** for any issues.

2. **Common Issues**:

   - **Authentication Errors**:

     - Verify the FTP username and password.

   - **Connection Errors**:

     - Ensure network connectivity to the FTP server.
     - Check firewall settings that may block FTP ports.

   - **File Not Found**:

     - Verify the `sourceDirectory` path is correct on the FTP server.

   - **Permission Issues**:

     - Ensure the FTP user has permission to read the specified files.

#### Step 6: Security Considerations

- **Credentials Management**:

  - Avoid hardcoding sensitive information like passwords.
  - Use secure configurations or credential management systems if possible.

- **Secure Protocols**:

  - Use **SFTP** or **FTPS** for secure file transfers when possible.

- **Network Security**:

  - Ensure that data transfers are conducted over secure networks.

### Best Practices

- **Dynamic Configuration**:

  - Utilize message mappings to set file paths dynamically based on input data.

- **Error Handling**:

  - Enable exception ports on the **FTPGet** component to handle errors.
  - Implement logic to manage connection failures or file transfer issues.

- **Logging and Monitoring**:

  - Keep logs of file transfers for auditing purposes.
  - Monitor the **FTPGet** component for any issues during operation.

- **Post-Processing Actions**:

  - Decide whether to delete or move files on the FTP server after download to prevent duplicate processing.

### Conclusion

You have successfully learned how to download files from an FTP server using the **FTPGet** component in Fiorano. Integrating file transfers into your workflows allows you to exchange data and process files stored remotely, enhancing the capabilities of your integration solutions.

By mastering the configuration and use of the FTPGet component, you can handle various file transfer scenarios efficiently and securely.

---

## 5.5 FTPGet (Integrating with File Servers) Part 2

### Introduction

In this session, we will explore additional features of the **FTPGet** component, focusing on advanced configurations such as monitoring directories, processing multiple files, and handling different file patterns. This will enable you to create more sophisticated file transfer workflows.

### Objectives

- Learn how to configure the **FTPGet** component to monitor directories and process multiple files.
- Understand how to use file patterns to select specific files.
- Configure post-processing actions on the FTP server.
- Test and validate advanced file download functionalities.
- Apply best practices for secure and efficient file handling.

### Prerequisites

- Completion of **5.4 FTPGet (Integrating with File Servers) Part 1**.
- Access to an FTP server with multiple files and directories.
- Basic knowledge of FTP protocols and settings.

### Step-by-Step Guide

#### Scenario Overview

We will enhance the previous event process by configuring the **FTPGet** component to:

1. Monitor a directory on the FTP server for new files.
2. Download multiple files matching a specific pattern.
3. Move or delete files on the FTP server after processing.
4. Handle errors and exceptions effectively.

#### Step 1: Modify the Existing Event Process

1. **Open the Existing Event Process**:

   - Open the `FTPGetIntegration` event process created in the previous session.

2. **Components in Use**:

   - **REST Stub** or **Feeder** (message source).
   - **JSON Converter** (if used).
   - **FTPGet**.
   - **Display** (optional).

#### Step 2: Configure FTPGet for Monitoring and Multiple Files

1. **Open FTPGet Configuration**:

   - Double-click on the **FTPGet** component.

2. **Transfer Configuration**:

   - **Request Type**: Select **Directory** if you want to process multiple files.

3. **Monitor Directory**:

   - **Enable Monitor Directory**:

     - Check the option **Monitor Directory** to enable directory monitoring.

   - **Monitor Directory Configuration**:

     - **Parent Directory**: Specify the parent directory on the FTP server to monitor.
       - Example: `/remote/files/`.
     - **Monitor Subdirectories**: Enable if you want to monitor all subdirectories.
     - **Monitor Time Configuration**:
       - Set the **Monitor Interval** to specify how often to check for new files.
       - Example: `60000` milliseconds (1 minute).

4. **File Selection Configuration**:

   - **File Name/Pattern**:

     - Use wildcards to specify the files to process.
     - Examples:
       - `*.txt` to process all text files.
       - `data_*.csv` to process CSV files starting with `data_`.

5. **Post Processing Action**:

   - Decide what to do with the files after download.
     - **No Action**: Leave the files as is.
     - **Delete**: Delete files from the FTP server after download.
     - **Move**: Move files to another directory on the FTP server.
   - **Target Directory** (if moving files):
     - Specify the directory where files should be moved after processing.

6. **Advanced Settings**:

   - **Fetch Subdirectories**: Enable if you want to include files from subdirectories.
   - **Include Hidden Files**: Enable if you need to process hidden files.

7. **Finish Configuration**:

   - Click **Finish** to save the configuration.

#### Step 3: Configure Dynamic Mappings (Optional)

1. **Dynamic Configuration**:

   - If you want to specify certain parameters dynamically (e.g., file patterns), adjust the mappings accordingly.

2. **Use Connection Details from Input**:

   - In the **FTPGet** component's **Advanced Properties**, enable **Use Connection Details from Input** if you wish to supply connection details at runtime via input messages.

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

4. **Monitor File Download**:

   - **FTPGet** will monitor the specified directory and download files matching the pattern at the configured intervals.

5. **Verify Downloaded Files**:

   - Check the local directory to confirm that files are being downloaded as per the configuration.

6. **View Output (Optional)**:

   - Use the **Display** component to log or display confirmation messages.

#### Step 5: Verify Post-Processing Actions

1. **Check FTP Server**:

   - Verify that files are being moved or deleted from the FTP server after processing, based on your configuration.

2. **Monitor for New Files**:

   - Add new files to the FTP server matching the pattern and observe how the **FTPGet** component processes them.

#### Step 6: Troubleshooting

1. **View Logs**:

   - Right-click on the **FTPGet** component and select **View Logs**.

   - Check **Output Logs** and **Error Logs** for any issues.

2. **Common Issues**:

   - **File Access Issues**:

     - Ensure that the FTP user has permission to read, delete, or move files as configured.

   - **Connection Interruptions**:

     - Monitor for network issues that may disrupt the connection to the FTP server.

   - **File Pattern Errors**:

     - Verify that the file pattern correctly matches the intended files.

#### Step 7: Security Considerations

- **Credentials Management**:

  - Avoid hardcoding sensitive information like passwords.
  - Use secure configurations or credential management systems if possible.

- **Secure Protocols**:

  - Use **SFTP** or **FTPS** for secure file transfers when possible.

- **Network Security**:

  - Ensure that data transfers are conducted over secure networks.

### Best Practices

- **Efficient Monitoring**:

  - Set appropriate monitor intervals to balance system load and timely processing.

- **Error Handling**:

  - Enable exception ports on the **FTPGet** component to handle errors.
  - Implement logic to manage connection failures or file transfer issues.

- **File Processing Logic**:

  - Consider adding components to process files after download (e.g., parsing, data transformation).

- **Logging and Auditing**:

  - Keep detailed logs of file transfers and processing for auditing purposes.

### Conclusion

You have enhanced your integration by configuring the **FTPGet** component to monitor directories, process multiple files, and manage files on the FTP server after processing. These advanced configurations enable you to create robust file transfer workflows suitable for enterprise integration scenarios.

By mastering these advanced features, you can handle a variety of complex file transfer requirements efficiently and securely.

---

This concludes Module 5. You have learned how to integrate email and file transfer protocols into your Fiorano workflows, enabling automated communication and data exchange with external systems. These skills are essential for building robust enterprise integration solutions.

---

# Module 6: Flow Adapters

Welcome to Module 6 of the Fiorano Product Training series. In this module, we will explore **Flow Adapters** in Fiorano, which are specialized components that control and enhance the flow of messages within your integration workflows. Flow Adapters enable advanced processing patterns such as load distribution, caching, message splitting, aggregation, content-based routing, and schema validation.

Understanding and utilizing Flow Adapters effectively can greatly improve the performance, scalability, and maintainability of your integration solutions.

---

## 6.1 Adapter Flow Part 1: Load Distribution

### Introduction

In this session, we will learn how to use Fiorano's **Distribution Service** component to implement load distribution in your integration workflows. Load distribution is essential for ensuring scalability and optimal performance in enterprise integrations, especially under high load or concurrent requests.

By distributing incoming messages evenly or according to specified weights across multiple instances of a component or service, you can prevent bottlenecks, reduce latency, and enhance the responsiveness of your applications.

### Objectives

- Understand the concept and importance of load distribution in integration workflows.
- Learn how to use the **Distribution Service** component to distribute load across multiple service instances.
- Configure the Distribution Service with different distribution algorithms and weights.
- Test and validate load distribution within an event process.
- Apply best practices for implementing load distribution in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Familiarity with creating event processes in Fiorano.
- Understanding of basic messaging patterns and Fiorano components.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process where:

1. **Message Source**: A **Feeder** component simulates incoming requests or messages.
2. **Distribution Service**: The **Distribution Service** component distributes incoming messages across multiple backend service instances.
3. **Backend Service Instances**: Multiple instances of a backend service (e.g., using **Sleep** components for simulation) process the messages.
4. **Response Handling**: Processed messages are returned or further routed as needed.

This scenario demonstrates how to implement load distribution to balance the processing load and improve performance.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `LoadDistributionExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **Feeder**: Acts as the message source.
     - Drag and drop the **Feeder** component onto the canvas.
   - **Backend Service Instances**:
     - Simulate the backend services using **Sleep** components.
     - Add three instances of the **Sleep** component to represent multiple backend service instances.
   - **Rename Components for Clarity**:
     - Rename the **Sleep** components:
       - `BackendInstance1`
       - `BackendInstance2`
       - `BackendInstance3`

#### Step 2: Add and Configure the Distribution Service Component

1. **Add the Distribution Service**:

   - In the **Microservice Palette**, locate **Distribution Service** under **Flow Components**.
   - Drag and drop the **Distribution Service** onto the canvas.

2. **Configure the Distribution Service**:

   - **Open Configuration**:
     - Double-click on the **Distribution Service** component to open the configuration window.
   - **Set Number of Output Ports**:
     - Set the **Number of Output Ports** to `3`, matching the number of backend instances.
   - **Assign Weights to Output Ports**:
     - Under **Output Port Configurations**, assign weights to each output port to control the distribution ratio.
     - For example:
       - **Output Port 0** (to `BackendInstance1`): Weight `5`
       - **Output Port 1** (to `BackendInstance2`): Weight `3`
       - **Output Port 2** (to `BackendInstance3`): Weight `2`
   - **Select Distribution Algorithm**:
     - The default algorithm is **Weighted Round Robin**, which distributes messages based on the assigned weights.
     - Other algorithms can be selected based on requirements, such as **Random** or **Least Connections**.
   - **Finish Configuration**:
     - Click **Finish** to save the settings.

3. **Connect Components**:

   - **Feeder to Distribution Service**:
     - Draw a route from the **Output Port** of the **Feeder** to the **Input Port** of the **Distribution Service**.
   - **Distribution Service to Backend Instances**:
     - Draw routes from each **Output Port** of the **Distribution Service** to the corresponding backend instance:
       - **Output Port 0** to `BackendInstance1`
       - **Output Port 1** to `BackendInstance2`
       - **Output Port 2** to `BackendInstance3`

4. **Set Labels for Clarity** (Optional):

   - Right-click on each route from the **Distribution Service** and select **Properties**.
   - Under the **General** tab, set labels to indicate the weight or destination (e.g., `Weight 5`, `Weight 3`, `Weight 2`).

#### Step 3: Configure the Backend Service Instances

1. **Configure Each Sleep Component**:

   - **BackendInstance1**:
     - Double-click to open the configuration.
     - **Processing Time**: Set to `1000` milliseconds (1 second).
     - **Custom Configuration**: Add any message or identifier to indicate it's from `BackendInstance1`.
   - **BackendInstance2**:
     - **Processing Time**: Set to `2000` milliseconds (2 seconds).
     - **Custom Configuration**: Add a message to indicate it's from `BackendInstance2`.
   - **BackendInstance3**:
     - **Processing Time**: Set to `3000` milliseconds (3 seconds).
     - **Custom Configuration**: Add a message to indicate it's from `BackendInstance3`.

#### Step 4: Add an Output Component (Optional)

- **Display**:
  - Add a **Display** component to view the messages after processing.
  - Connect the **Output Port** of each backend instance to the **Input Port** of the **Display** component. Alternatively, route them back to a common response handler.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**.

2. **Add Breakpoints (Optional)**:

   - To observe the flow of messages, set breakpoints on routes or components.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

4. **Send Test Messages**:

   - **Open the Feeder Component**:
     - Double-click on the **Feeder** to open the input window.
   - **Configure Message Sending**:
     - Enter a message in the **Text** field (e.g., `Test Message`).
     - **Send N Times**: Click on **Send N Times**.
     - **Number of Messages**: Enter `10` or any desired number.
     - **Interval**: Set the interval between messages, if needed.
     - Click **Send**.

5. **Observe Message Distribution**:

   - As messages are sent, observe how they are distributed to the backend instances.
   - Based on the assigned weights (`5`, `3`, `2`), messages should be distributed proportionally:
     - `BackendInstance1` should receive approximately 50% of the messages.
     - `BackendInstance2` should receive approximately 30% of the messages.
     - `BackendInstance3` should receive approximately 20% of the messages.
   - Use the **Debugger** or **Breakpoints** to verify the distribution.

6. **Verify Processing**:

   - Check the messages in the **Display** component to see which backend instance processed each message.
   - Observe the processing times based on the configurations of the **Sleep** components.

#### Step 6: Adjust and Experiment (Optional)

1. **Modify Weights**:

   - Change the weights assigned to the output ports in the **Distribution Service**.
   - Re-run the event process and observe how the distribution changes.

2. **Change Distribution Algorithm**:

   - Explore different distribution algorithms in the **Distribution Service** configuration.
   - Test **Round Robin**, **Random**, or any other available algorithms.

3. **Increase Number of Instances**:

   - Add more backend service instances and adjust the **Number of Output Ports** accordingly.
   - Configure their processing times and observe the effects.

### Best Practices

- **Appropriate Weighting**:

  - Assign weights based on the processing capacity and performance of each backend instance.
  - Higher weights send more messages to instances capable of handling more load.

- **Monitoring and Logging**:

  - Include logging components or use Fiorano's monitoring tools to track message flow and performance.
  - Monitor the distribution to ensure it meets the desired load balancing objectives.

- **Scalability**:

  - Design your workflows to allow easy scaling by adding or removing backend instances as needed.
  - Use server groups or dynamic configurations for large-scale deployments.

- **Error Handling**:

  - Implement error handling for backend instances to manage failures gracefully.
  - Use exception ports and error routes to reroute or retry messages if needed.

- **Performance Testing**:

  - Conduct performance testing under realistic load conditions to ensure the distribution achieves the desired effect.
  - Adjust configurations based on test results.

### Conclusion

You have successfully learned how to implement load distribution in Fiorano using the **Distribution Service** component. By distributing messages across multiple backend service instances, you can enhance the scalability and performance of your integration workflows.

Load distribution is a critical aspect of enterprise integrations, especially in environments with high throughput and concurrent processing requirements. Understanding how to configure and use the Distribution Service enables you to design robust solutions that efficiently manage processing resources.

In the next session, we will explore implementing caching mechanisms using the **Cache** component to further optimize performance.

---

## 6.2 Adapter Flow Part 2: Implementing Cache

### Introduction

In this session, we will explore how to implement caching in your Fiorano integration workflows using the **Cache** component. Caching is an effective technique to improve performance and reduce latency by storing frequently accessed data in memory. By retrieving data from the cache instead of querying external systems like databases repeatedly, you can significantly enhance the responsiveness of your applications, especially in read-intensive scenarios.

### Objectives

- Understand the concept and benefits of caching in integration workflows.
- Learn how to use the **Cache** component to store and retrieve data.
- Configure the Cache component to manage cache size, expiration, and data structures.
- Implement a workflow that utilizes caching to reduce database load.
- Test and validate the caching mechanism within an event process.
- Apply best practices for implementing caching in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Basic understanding of Fiorano components and event processes.
- Familiarity with databases and basic SQL operations.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Exposes a REST service** that accepts data to be stored.
2. **Processes and stores** the data in both a database and the cache.
3. **Retrieves data** from the cache when a client requests it.
4. **Handles cache expiration** to ensure data consistency.

This scenario demonstrates how to implement caching to improve performance by reducing database hits, thereby lowering latency and enhancing user experience.

### Step-by-Step Guide

#### Architecture Diagram

An overview of the workflow:

1. **Client Request**: Sends data to be stored via a REST service (e.g., transaction information).
2. **Data Storage**:
   - **Database Storage**: Data is stored in the database for persistence.
   - **Cache Storage**: Data is stored in the cache for quick retrieval.
3. **Data Retrieval**:
   - **Cache Retrieval**: When a client requests data, the system first checks the cache.
     - **Cache Hit**: If data is found, it is returned immediately.
     - **Cache Miss**: If data is not found (e.g., expired or never cached), the system queries the database, stores the result in the cache, and then returns it to the client.

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `CacheImplementationExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **JSON to XML Converter**: Converts JSON payloads to XML.
     - Drag and drop the **JSON Converter** component.
   - **Cache**: Stores data in memory.
     - Drag and drop the **Cache** component from the **Flow Components** category.
   - **Database Component**: Stores data in a database.
     - Drag and drop the **DB** component from the **Connectors** category.
   - **Additional Components**:
     - **Mapper**: For data transformations.
     - **Decision**: To handle logic for cache hits and misses.
     - **Display**: For testing purposes (optional).

3. **Layout of the Workflow**:

   - **Data Ingestion**:
     - **REST Stub** → **JSON Converter** → **Cache** → **Database**.
   - **Data Retrieval**:
     - **Client Request** → **Cache Lookup** → If **Cache Hit**:
       - Return data from **Cache**.
     - If **Cache Miss**:
       - Query **Database** → Update **Cache** → Return data to **Client**.

#### Step 2: Configure the Components

##### Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `TransactionService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/transaction`.
     - **ID**: Optionally, `TransactionResource`.
   - **Add Methods**:
     - **POST**: For storing data.
     - **GET**: For retrieving data.

4. **Request and Response Representations**:

   - **POST Method**:
     - **Request Media Type**: `application/json`.
     - Define JSON schema for the transaction data (e.g., `transactionId`, `amount`, `date`).
   - **GET Method**:
     - **Query Parameter**: `transactionId` (to specify which transaction to retrieve).
     - **Response Media Type**: `application/json`.

5. **Finish Configuration**.

##### Configure the JSON Converter Component

1. **Open Configuration**:

   - Double-click on the **JSON Converter** component.

2. **Conversion Direction**:

   - **Convert JSON to XML**: Set to **Yes**.

3. **Provide Output XSD Schema**:

   - Define an XSD schema that represents the structure of your transaction data in XML.
   - Example:

     ```xml
     <?xml version="1.0" encoding="UTF-8"?>
     <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
       <xsd:element name="Transaction">
         <xsd:complexType>
           <xsd:sequence>
             <xsd:element name="transactionId" type="xsd:int"/>
             <xsd:element name="amount" type="xsd:decimal"/>
             <xsd:element name="date" type="xsd:date"/>
           </xsd:sequence>
         </xsd:complexType>
       </xsd:element>
     </xsd:schema>
     ```

4. **Select Root Element**:

   - Choose `Transaction`.

5. **Finish Configuration**.

##### Configure the Cache Component

1. **Open Configuration**:

   - Double-click on the **Cache** component.

2. **Field Definition Table**:

   - Define the fields to be stored in the cache.
   - **Add Fields**:
     - **Field Name**: `transactionId`
       - **Type**: `int`
       - **Key**: Check the box to make it a key field.
     - **Field Name**: `transactionData`
       - **Type**: `xml` (or the appropriate type)
       - **Key**: Leave unchecked (it's the value).

3. **Cache Settings**:

   - **Initial Cache Size**: Set according to expected load.
   - **Cache Threshold**: Maximum number of entries before eviction occurs.
   - **Expire After Timeout**:
     - **Enable**: Check this option.
     - **Timeout Interval**: Set the time in milliseconds after which the cache entry expires (e.g., `60000` ms for 1 minute).

4. **Data Structure for Value**:

   - **XSD Schema**: If you want to store complex data structures, provide the XSD for `transactionData`.

5. **Finish Configuration**.

##### Configure the Database Component

1. **Open Configuration**:

   - Double-click on the **Database** component.

2. **Database Connection**:

   - **DB URL**: Enter your database JDBC URL.
   - **DB User**: Enter your database username.
   - **DB Password**: Enter your database password.
   - **Test Connection**: Verify the connection.

3. **SQL Configuration**:

   - **Insert Operation**: For storing transactions.
     - **Table**: Specify the table where transaction data will be stored.
     - **Columns**: Map the fields accordingly.
   - **Select Operation**: For retrieving transactions.
     - Use parameterized queries to fetch data based on `transactionId`.

4. **Error Handling**:

   - Configure as needed for retry mechanisms and error responses.

5. **Finish Configuration**.

##### Configure the Mapper Components

- **POST Request Mapping**:
  - Map the JSON fields from the **JSON Converter** to the **Cache** and **Database** components.
- **GET Request Mapping**:
  - Map the `transactionId` from the **REST Stub** to the **Cache** for lookup.
  - Implement logic to handle cache hit or miss.

##### Configure Decision Logic for Cache Hit/Miss

1. **Add a **Decision** Component**:

   - Place the **Decision** component after attempting to retrieve data from the **Cache**.

2. **Configure the Decision Component**:

   - **Condition**: Check if the cache returned data.
     - **Expression**: For example, check if `cacheResponse` exists in the application context or message properties.
   - **Routes**:
     - **Cache Hit**: If data is found in the cache.
     - **Cache Miss**: If data is not found in the cache.

3. **Cache Miss Handling**:

   - If a cache miss occurs:
     - Route the request to the **Database** component to fetch data.
     - Update the **Cache** with the retrieved data.

4. **Cache Hit Handling**:

   - Return the data from the cache directly to the client.

#### Step 3: Connect the Components and Define the Workflow

1. **For POST Requests**:

   - **REST Stub (POST)** → **JSON Converter** → **Cache** (Store Data) → **Database** (Insert Data).

2. **For GET Requests**:

   - **REST Stub (GET)** → **Cache** (Retrieve Data).
     - **Cache Hit**:
       - Return data from **Cache** to **REST Stub** Response.
     - **Cache Miss**:
       - **Decision** Component routes to **Database** to fetch data.
       - **Database** → **Cache** (Update Cache) → **REST Stub** Response.

3. **Configure Routes**:

   - Use appropriate routing and mapping to ensure data flows correctly between components.

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**.

#### Step 5: Test the Workflow Using Postman

1. **Testing POST Requests** (Storing Data):

   - Send a **POST** request to `http://localhost:1856/transaction` with transaction data.
   - Verify that:
     - Data is stored in the **Database**.
     - Data is stored in the **Cache**.

2. **Testing GET Requests** (Retrieving Data):

   - Send a **GET** request to `http://localhost:1856/transaction?transactionId=123`.
   - Scenario 1: **Cache Hit**:
     - If data is present in the cache (within the expiration time), it should be returned immediately.
     - Observe that the database is not queried.
   - Scenario 2: **Cache Miss**:
     - If the data is not in the cache (e.g., after cache expiration), the system should:
       - Query the **Database**.
       - Update the **Cache** with the retrieved data.
       - Return the data to the client.

3. **Testing Cache Expiration**:

   - Wait for the cache expiration time to pass (e.g., 1 minute).
   - Send a **GET** request for the same `transactionId`.
   - Observe that the system performs a cache miss, fetches data from the database, and updates the cache.

#### Step 6: Validate and Troubleshoot

1. **Use Breakpoints and Debugger**:

   - Set breakpoints to inspect data at different stages.
   - Verify that the application context or message properties are correctly set.

2. **Check Cache Contents**:

   - Use Fiorano's built-in tools or logs to view current cache entries.

3. **Monitor Database Access**:

   - Observe database logs or use monitoring tools to verify when the database is accessed.

4. **Logs and Error Handling**:

   - Ensure that logs are available for troubleshooting.
   - Implement error handling for scenarios such as database failures or cache errors.

### Best Practices

- **Cache Configuration**:

  - Set appropriate cache sizes and expiration times based on application requirements.
  - Avoid overloading the cache with excessive data.

- **Data Consistency**:

  - Implement cache invalidation strategies to keep data consistent between the cache and the database.
  - Be cautious with cache expiration to balance performance and data accuracy.

- **Security Considerations**:

  - Ensure that sensitive data is stored securely in the cache.
  - Implement access controls if necessary.

- **Performance Monitoring**:

  - Monitor cache hit rates to assess the effectiveness of the caching strategy.
  - Use performance metrics to adjust cache configurations as needed.

- **Error Handling**:

  - Implement robust error handling for cache misses, timeouts, and exceptions.
  - Provide meaningful error messages to clients when appropriate.

- **Scalability**:

  - Consider distributed caching solutions if scaling across multiple servers.
  - Ensure the cache component does not become a bottleneck.

### Conclusion

You have successfully learned how to implement caching in Fiorano using the **Cache** component. By leveraging caching, you can significantly improve the performance of your integration workflows by reducing unnecessary database access and lowering latency.

Caching is a powerful technique in enterprise integrations, especially for read-heavy operations. Understanding how to configure and use the Cache component enables you to design efficient and responsive solutions that enhance user experience.

In the next session, we will explore message splitting techniques using the **XMLSplitter** component to handle and process large or complex messages effectively.

---

## 6.3 Adapter Flow Part 3: Message Splitter Using XMLSplitter

### Introduction

In this session, we will explore how to split large or complex XML messages into smaller, manageable fragments using Fiorano's **XMLSplitter** component. Message splitting is essential in scenarios where you need to process individual elements of a large message separately, enabling parallel processing and improving performance.

By splitting messages based on specific XML paths or namespaces, you can route individual fragments to appropriate components for processing, apply transformations, or aggregate results as needed.

### Objectives

- Understand the purpose and benefits of message splitting in integration workflows.
- Learn how to use the **XMLSplitter** component to split XML messages.
- Configure the XMLSplitter with appropriate namespaces and XPath expressions.
- Implement a workflow that splits an XML message and processes each fragment.
- Test and validate the message splitting mechanism within an event process.
- Apply best practices for using the XMLSplitter in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Basic understanding of XML and XPath expressions.
- Familiarity with Fiorano components and event processes.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Receives a JSON message** via a REST service containing an array of elements.
2. **Converts the JSON message to XML** using the JSON Converter component.
3. **Uses the XMLSplitter** component to split the XML message into individual elements.
4. **Processes each split message** (e.g., by logging or further processing).
5. **Sends responses** back as needed.

This scenario demonstrates how to use the XMLSplitter to handle messages containing arrays or collections, splitting them into individual messages for processing.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `MessageSplitterExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **JSON to XML Converter**:
     - Drag and drop the **JSON Converter** component.
   - **XMLSplitter**:
     - In the **Microservice Palette**, find the **XMLSplitter** component under **Flow Components**.
     - Drag and drop the **XMLSplitter** onto the canvas.
   - **Display** (Optional): To show the split messages.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **JSON Converter**.
   - Draw a route from the **Output Port** of the **JSON Converter** to the **Input Port** of the **XMLSplitter**.
   - Draw a route from the **Output Port** of the **XMLSplitter** to the **Input Port** of the **Display** component or further processing components.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `SplitMessageService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/splitmessage`.
     - **ID**: Optionally, `SplitMessageResource`.
   - **Add Method**:
     - **Method**: Choose **POST**.

4. **Request Representation**:

   - Under **Request**, click **Add Representation**.
   - **Media Type**: Select `application/json`.
   - **Schema**: Define a JSON schema that includes an array.

     Example JSON payload:

     ```json
     {
       "items": [
         { "id": 1, "name": "Item1", "quantity": 10 },
         { "id": 2, "name": "Item2", "quantity": 20 }
       ]
     }
     ```

5. **Finish Configuration**.

#### Step 3: Configure the JSON Converter Component

1. **Open Configuration**:

   - Double-click on the **JSON Converter** component.

2. **Conversion Direction**:

   - Ensure **Convert JSON to XML** is set to **Yes**.

3. **Provide Output XSD Schema**:

   - Define an XSD schema that represents the structure of your JSON data in XML.

   Example XSD:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
     <xsd:element name="Items">
       <xsd:complexType>
         <xsd:sequence>
           <xsd:element name="Item" maxOccurs="unbounded">
             <xsd:complexType>
               <xsd:sequence>
                 <xsd:element name="id" type="xsd:int"/>
                 <xsd:element name="name" type="xsd:string"/>
                 <xsd:element name="quantity" type="xsd:int"/>
               </xsd:sequence>
             </xsd:complexType>
           </xsd:element>
         </xsd:sequence>
       </xsd:complexType>
     </xsd:element>
   </xsd:schema>
   ```

4. **Select Root Element**:

   - Choose `Items`.

5. **Finish Configuration**.

#### Step 4: Configure the XMLSplitter Component

1. **Open Configuration**:

   - Double-click on the **XMLSplitter** component.

2. **Operation**:

   - **Select Operation**: Choose **Split** (default).

3. **Processor**:

   - **Processor Type**: Choose **XPath**.

4. **Namespaces**:

   - If your XML uses namespaces, define them here.
   - For this example, we'll assume no namespaces are used.

5. **Split Path**:

   - **XPath Expression**:

     - Enter the XPath expression that points to the repeating element you want to split on.

     - For our example, since each `Item` is nested under `Items`, the XPath would be:

       ```xpath
       /Items/Item
       ```

6. **Schema Configuration**:

   - **Input Schema**:

     - If necessary, provide the XSD schema to define the structure of the incoming XML.

   - **Validate Input**:

     - Enable if you want to validate incoming messages against the schema.

7. **Other Configuration**:

   - **Include Root Element in Split Messages**:

     - Choose whether to include the root element in each split message.
     - For our example, set accordingly based on your processing needs.

8. **Finish Configuration**.

#### Step 5: Configure the Display Component (Optional)

- The **Display** component will show each split message as it is processed.
- No additional configuration is needed unless you want to format the output.

#### Step 6: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/splitmessage`).
   - **Method**: **POST**.
   - **Headers**:

     - `Content-Type`: `application/json`.

   - **Body**:

     ```json
     {
       "items": [
         { "id": 1, "name": "Item1", "quantity": 10 },
         { "id": 2, "name": "Item2", "quantity": 20 },
         { "id": 3, "name": "Item3", "quantity": 30 }
       ]
     }
     ```

   - **Send the Request**.

5. **Observe the Split Messages**:

   - Open the **Display** component to see each split message.
   - Each split message should be an XML fragment representing one `Item` element.

   Example split message:

   ```xml
   <Item>
     <id>1</id>
     <name>Item1</name>
     <quantity>10</quantity>
   </Item>
   ```

6. **Further Processing (Optional)**:

   - Instead of (or in addition to) the **Display** component, you can route the split messages to other components for processing, such as:

     - **Mapper**: To transform the data.
     - **Database** component: To store each item individually.
     - **REST Consumer**: To send each item to an external service.

#### Step 7: Validate and Troubleshoot

1. **Use Breakpoints and Debugger**:

   - Set breakpoints after the **XMLSplitter** to inspect each split message.
   - Verify that the messages are correctly split according to the XPath expression.

2. **Check for Errors**:

   - If messages are not being split correctly, review the following:

     - **XPath Expression**: Ensure it accurately targets the repeating element.
     - **Namespaces**: If your XML uses namespaces, make sure they are correctly defined in the XMLSplitter configuration.
     - **Input XML Structure**: Verify that the XML structure matches the expected schema.

3. **View Logs**:

   - Right-click on the **XMLSplitter** component and select **View Logs**.
   - Check for any error messages or warnings.

#### Step 8: Optional Enhancements

1. **Aggregate Processing**:

   - After processing individual messages, you may want to aggregate results.
   - Use the **Aggregation** component to collect responses from individual messages.

2. **Error Handling**:

   - Configure exception handling to manage errors during message splitting or processing.

3. **Dynamic Configuration**:

   - Modify the XPath expression dynamically if needed by using message properties or application context variables.

### Best Practices

- **Accurate XPath Expressions**:

  - Ensure that your XPath expressions correctly identify the elements to split.
  - Use absolute paths for clarity.

- **Namespace Handling**:

  - If your XML uses namespaces, define them accurately in the XMLSplitter configuration.
  - Use prefixes in your XPath expressions as required.

- **Performance Considerations**:

  - Be cautious when splitting very large messages, as it may impact performance.
  - Test with realistic data volumes to assess impact.

- **Error Handling**:

  - Implement error handling to manage scenarios where the expected elements are not present.
  - Use the **Exception Port** of the XMLSplitter to route errors appropriately.

- **Logging and Monitoring**:

  - Include logging to track the processing of split messages.
  - Monitor the flow to ensure messages are processed as expected.

### Conclusion

You have successfully learned how to use the **XMLSplitter** component in Fiorano to split XML messages based on XPath expressions. This technique allows you to process individual elements of a message separately, enabling you to handle complex or large messages efficiently.

Message splitting is a valuable pattern in enterprise integrations, especially when dealing with batch processing or multiple data records within a single message. Understanding how to configure and use the XMLSplitter component enhances your ability to design flexible and scalable integration solutions.

In the next session, we will explore aggregation techniques using the **Aggregation** component to combine messages or results, complementing the splitting process.

---

## 6.4 Adapter Flow Part 4: Aggregation Techniques

### Introduction

In this session, we will explore how to aggregate multiple messages or responses in your Fiorano integration workflows using the **Aggregation** component. Aggregation is a crucial pattern when you need to combine multiple related messages into a single message before further processing or responding to a client. This technique is commonly used in scenarios such as collecting responses from multiple backend services and presenting a unified result to the client.

By using the Aggregation component, you can:

- Collect and combine messages from different sources.
- Control the aggregation based on conditions such as the number of messages or a timeout.
- Improve efficiency by parallelizing requests to multiple services and aggregating their responses.

### Objectives

- Understand the purpose and benefits of message aggregation in integration workflows.
- Learn how to use the **Aggregation** component to aggregate messages.
- Configure the Aggregation component with appropriate settings for your scenario.
- Implement a workflow that aggregates responses from multiple backend services.
- Test and validate the aggregation mechanism within an event process.
- Apply best practices for using the Aggregation component in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Familiarity with Fiorano components and event processes.
- Understanding of basic messaging patterns and components in Fiorano.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Receives a client request** via a REST service.
2. **Sends requests** to multiple backend services in parallel.
3. **Aggregates responses** from these backend services using the Aggregation component.
4. **Sends a unified response** back to the client.

This scenario simulates a common pattern where, for example, a client requests information that needs to be retrieved from multiple sources, such as flight information from different airlines or product pricing from different vendors.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `AggregationExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **Backend Service Simulations**:
     - For demonstration purposes, use multiple **Sleep** components to simulate backend services (`BackendService1`, `BackendService2`, `BackendService3`).
     - Add three **Sleep** components to represent different backend services.
     - **Rename Components**:
       - `BackendService1`
       - `BackendService2`
       - `BackendService3`
   - **Aggregation**:
     - In the **Microservice Palette**, find the **Aggregation** component under **Flow Components**.
     - Drag and drop the **Aggregation** component onto the canvas.
   - **Display** (Optional): To view the aggregated result.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - **REST Stub to Backend Services**:
     - Draw routes from the **Output Port** of the **REST Stub** to each **Backend Service** component.
   - **Backend Services to Aggregation**:
     - Draw routes from the **Output Port** of each **Backend Service** to the **Input Port** of the **Aggregation** component.
   - **Aggregation to REST Stub Response**:
     - Draw a route from the **Output Port** of the **Aggregation** component to the **Response Port** of the **REST Stub**.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `AggregationService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/aggregate`.
     - **ID**: Optionally, `AggregateResource`.
   - **Add Method**:
     - **Method**: Choose **GET** (or **POST** if you prefer).

4. **Request Parameters** (Optional):

   - If you want to pass parameters to influence backend requests, define them here (e.g., `destination`).

5. **Response Representation**:

   - **Media Type**: Select `application/json`.

6. **Finish Configuration**.

#### Step 3: Configure the Backend Service Simulations

Since we are using **Sleep** components to simulate backend services, we will configure them to output sample data.

1. **Configure Each Backend Service**:

   - **BackendService1**:

     - **Open Configuration**:
       - Double-click on `BackendService1`.
     - **Processing Time**: Set to `1000` milliseconds (1 second) to simulate a response time.
     - **Custom Output**:

       - Use the **Custom Transformation** tab or **Set Constant** function in the **Mapper** to return sample data.
       - Example output:

         ```json
         {
           "service": "BackendService1",
           "data": "Response from Service 1"
         }
         ```

   - **BackendService2**:
     - Similar configuration with different sample data.
   - **BackendService3**:
     - Similar configuration with different sample data.

2. **Configure Output**:

   - Ensure that the output from each backend service is consistent in structure to facilitate aggregation.

#### Step 4: Configure the Aggregation Component

1. **Open Configuration**:

   - Double-click on the **Aggregation** component.

2. **Aggregation Condition**:

   - **Condition**: Select **Wait for End Messages**.
   - **Completeness Condition**:
     - **Number of Messages**: Set to `3` (since we have three backend services).
     - The Aggregation component will wait until it has received the specified number of messages before proceeding.

3. **Aggregation Settings**:

   - **Ignore Duplicate Messages**: Set to **No** (default).
   - **Input XSD Schema**:
     - Provide an XSD that defines the input message structure if necessary.
     - For our example, the messages are simple JSON; however, an XSD can still be used if converting to XML.

4. **Output XSD Schema**:

   - Define the structure of the aggregated message.
   - Example XSD for the aggregated output:

     ```xml
     <?xml version="1.0" encoding="UTF-8"?>
     <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
       <xsd:element name="AggregatedResponse">
         <xsd:complexType>
           <xsd:sequence>
             <xsd:element name="Responses" maxOccurs="unbounded">
               <xsd:complexType>
                 <xsd:sequence>
                   <xsd:element name="service" type="xsd:string"/>
                   <xsd:element name="data" type="xsd:string"/>
                 </xsd:sequence>
               </xsd:complexType>
             </xsd:element>
           </xsd:sequence>
         </xsd:complexType>
       </xsd:element>
     </xsd:schema>
     ```

5. **Select Root Element**:

   - Choose `AggregatedResponse`.

6. **Finish Configuration**.

#### Step 5: Configure Mappings and Transformations

1. **From REST Stub to Backend Services**:

   - If necessary, map any request parameters to the backend services.
   - Since we are simulating, we may not need additional mapping.

2. **From Backend Services to Aggregation**:

   - **Configure Transformation** on each route from a backend service to the **Aggregation** component.
   - Ensure that the messages sent to the **Aggregation** component conform to the expected input schema.

3. **From Aggregation to REST Stub Response**:

   - **Configure Transformation** to map the aggregated XML message back to JSON format expected by the client.
   - Use the **Mapper** to convert the aggregated response to JSON.

#### Step 6: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/aggregate`).
   - **Method**: **GET**.
   - **Send the Request**.

5. **Observe Aggregation Behavior**:

   - Since we have set the Aggregation component to wait for 3 messages, it will collect responses from all three backend services before proceeding.
   - The total processing time will be approximately equal to the longest processing time of the backend services plus any overhead.

6. **Verify the Response**:

   - The client should receive a single aggregated response combining data from all backend services.
   - Example response:

     ```json
     {
       "AggregatedResponse": {
         "Responses": [
           {
             "service": "BackendService1",
             "data": "Response from Service 1"
           },
           {
             "service": "BackendService2",
             "data": "Response from Service 2"
           },
           {
             "service": "BackendService3",
             "data": "Response from Service 3"
           }
         ]
       }
     }
     ```

#### Step 7: Validate and Troubleshoot

1. **Use Breakpoints and Debugger**:

   - Set breakpoints to inspect messages at different stages.
   - Verify that messages are correctly passed to the Aggregation component.

2. **Monitor Aggregation**:

   - Confirm that the Aggregation component waits for all messages before proceeding.
   - Check the messages being aggregated for correctness.

3. **View Logs**:

   - Right-click on the **Aggregation** component and select **View Logs**.
   - Check for any error messages or warnings.

4. **Test with Fewer Responses** (Optional):

   - Simulate a scenario where not all backend services respond.
   - Adjust the **Completeness Condition** or test timeout behaviors.

#### Step 8: Optional Enhancements

1. **Handle Timeouts**:

   - Configure the Aggregation component to handle scenarios where not all responses are received within a certain time.
   - Use the **Timeout Condition** to proceed after a specified time even if not all messages have been received.

2. **Dynamic Number of Messages**:

   - If the number of backend services is variable, use a **Correlation ID** or other techniques to manage dynamic aggregation.

3. **Error Handling**:

   - Implement error handling for failed requests to backend services.
   - Use the **Exception Ports** to route and handle errors accordingly.

4. **Enhance Backend Services**:

   - Replace the **Sleep** components with actual backend service connectors if available.
   - Configure real endpoints and process actual data.

### Best Practices

- **Consistent Message Structures**:

  - Ensure that messages from different sources have a consistent structure to facilitate aggregation.

- **Timeout Management**:

  - Use timeouts to prevent indefinite waiting in case a backend service fails to respond.
  - Provide default values or handle missing data gracefully.

- **Use of Correlation Keys**:

  - When necessary, use correlation keys to correlate messages belonging to the same aggregation group.

- **Scalability**:

  - Consider the impact of message volume on the Aggregation component.
  - Test with realistic data sizes to ensure performance remains acceptable.

- **Error Handling**:

  - Implement robust error handling to manage failures in backend services.
  - Provide meaningful error messages or fallbacks to the client if needed.

- **Logging and Monitoring**:

  - Include logging to track the aggregation process.
  - Monitor for any bottlenecks or delays in message processing.

### Conclusion

You have successfully learned how to use the **Aggregation** component in Fiorano to aggregate multiple messages or responses. This technique allows you to combine data from various sources into a unified message, enabling you to present comprehensive results to clients or perform consolidated processing.

Aggregation is a fundamental pattern in enterprise integration, especially in scenarios like:

- Collecting search results from multiple sources.
- Combining data from different systems for reporting.
- Synchronizing data from various services.

Understanding how to configure and use the Aggregation component enhances your ability to design complex integration workflows that can efficiently manage multiple data streams.

In the next session, we will explore content-based routing using the **JsonCBR** component to route messages based on their content.

---

## 6.5 Adapter Flow Part 5: Content-Based Routing with JsonCBR

### Introduction

In this session, we will explore how to implement **Content-Based Routing (CBR)** using Fiorano's **JsonCBR** component. Content-Based Routing allows you to route messages to different processing paths based on the content of the message. This technique is essential when you need to apply different processing logic or direct messages to different destinations depending on specific data within the message payload.

By using the JsonCBR component, you can evaluate JSON message content using JSONPath expressions, enabling you to route messages dynamically and create flexible integration workflows.

### Objectives

- Understand the concept and importance of Content-Based Routing in integration workflows.
- Learn how to use the **JsonCBR** component to route messages based on JSON content.
- Configure the JsonCBR component with appropriate JSONPath expressions and routing logic.
- Implement a workflow that routes messages to different paths based on message content.
- Test and validate the Content-Based Routing mechanism within an event process.
- Apply best practices for using the JsonCBR component in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Basic understanding of JSON and JSONPath expressions.
- Familiarity with Fiorano components and event processes.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Exposes a REST service** that accepts JSON messages containing a `companyName` field.
2. **Uses the JsonCBR component** to evaluate the `companyName` field and route messages accordingly.
3. **Routes messages** to different paths based on the value of `companyName` (e.g., `Microsoft`, `Apple`).
4. **Provides default handling** for messages that do not match any specified criteria.
5. **Sends appropriate responses** back to the client.

This scenario demonstrates how to use the JsonCBR component to implement Content-Based Routing based on JSON message content.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `ContentBasedRoutingExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **JsonCBR**: Performs Content-Based Routing on JSON messages.
     - In the **Microservice Palette**, locate **JsonCBR** under **Flow Components**.
     - Drag and drop the **JsonCBR** component onto the canvas.
   - **Responder Components**: For generating responses.
     - Add **Mapper** components or **Display** components as needed to simulate different processing paths.
     - For this example, you can use **Mapper** components to set custom responses.

3. **Connect Components**:

   - **REST Stub to JsonCBR**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **JsonCBR** component.
   - **JsonCBR Outputs**:
     - The **JsonCBR** component will have multiple **Output Ports** based on the routing configuration.
     - Connect each **Output Port** to a corresponding **Mapper** or **Response** component.
   - **Responses back to REST Stub**:
     - From each **Mapper** or **Response** component, draw a route to the **Response Port** of the **REST Stub** to send the response back to the client.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `CompanyRoutingService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/routecompany`.
     - **ID**: Optionally, `RouteCompanyResource`.
   - **Add Method**:
     - **Method**: Choose **POST**.

4. **Request Representation**:

   - Under **Request**, click **Add Representation**.
   - **Media Type**: Select `application/json`.
   - **Schema**: Define a simple JSON schema including the `companyName` field.

     - Example:

       ```json
       {
         "companyName": "string",
         "otherData": "any"
       }
       ```

5. **Finish Configuration**.

#### Step 3: Configure the JsonCBR Component

1. **Open Configuration**:

   - Double-click on the **JsonCBR** component.

2. **Add Routing Conditions**:

   - **Routing Conditions**:

     - Click on **Add** to create a new routing condition.
     - **Name**: Enter `Microsoft`.
     - **JSONPath Expression**: Enter the JSONPath expression to evaluate `companyName`.

       - For example:

         ```jsonpath
         $.companyName == 'Microsoft'
         ```

     - **Port Number**: Assign a unique port number (e.g., `1`).

   - Repeat the above steps to add another routing condition for `Apple`:

     - **Name**: Enter `Apple`.
     - **JSONPath Expression**:

       ```jsonpath
       $.companyName == 'Apple'
       ```

     - **Port Number**: Assign a unique port number (e.g., `2`).

3. **Default Route**:

   - The **JsonCBR** component has a default output port (`False` port) for messages that do not match any conditions.
   - This port is used to handle messages that do not match the specified criteria.

4. **Finish Configuration**.

#### Step 4: Connect and Configure Response Components

1. **Connect Output Ports**:

   - **Output Port 1** (Microsoft):
     - Draw a route from **Output Port 1** of the **JsonCBR** component to a **Mapper** component (`MicrosoftMapper`).
   - **Output Port 2** (Apple):
     - Draw a route from **Output Port 2** to another **Mapper** component (`AppleMapper`).
   - **False Output Port** (Default):
     - Draw a route from the **False** port to a **Mapper** component (`DefaultMapper`).

2. **Configure Mapper Components**:

   - **MicrosoftMapper**:

     - **Transformation**:

       - Set a custom response indicating that the company is Microsoft.
       - For example, use a **Set Constant** function to create the response:

         ```json
         {
           "message": "Welcome, Microsoft!"
         }
         ```

   - **AppleMapper**:

     - **Transformation**:

       - Set a custom response indicating that the company is Apple.
       - Example response:

         ```json
         {
           "message": "Welcome, Apple!"
         }
         ```

   - **DefaultMapper**:

     - **Transformation**:

       - Set a default response for companies not matched.
       - Example response:

         ```json
         {
           "message": "Company not recognized."
         }
         ```

3. **Connect Mappers to REST Stub Response**:

   - Draw routes from each **Mapper** component to the **Response Port** of the **REST Stub**.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/routecompany`).
   - **Method**: **POST**.
   - **Headers**:

     - `Content-Type`: `application/json`.

   - **Body**:

     - **Test Case 1**: `companyName` is **Microsoft**.

       ```json
       {
         "companyName": "Microsoft",
         "otherData": "Sample data"
       }
       ```

     - **Expected Response**:

       ```json
       {
         "message": "Welcome, Microsoft!"
       }
       ```

     - **Test Case 2**: `companyName` is **Apple**.

       ```json
       {
         "companyName": "Apple",
         "otherData": "Sample data"
       }
       ```

     - **Expected Response**:

       ```json
       {
         "message": "Welcome, Apple!"
       }
       ```

     - **Test Case 3**: `companyName` is **Google**.

       ```json
       {
         "companyName": "Google",
         "otherData": "Sample data"
       }
       ```

     - **Expected Response**:

       ```json
       {
         "message": "Company not recognized."
       }
       ```

   - **Send the Requests** and verify the responses.

#### Step 6: Validate and Troubleshoot

1. **Use Breakpoints and Debugger**:

   - Set breakpoints on routes or components to inspect message flow.
   - Verify that messages are routed to the correct ports based on `companyName`.

2. **Check JsonCBR Configuration**:

   - Ensure that the JSONPath expressions are correctly defined.
   - JSONPath expressions should accurately evaluate the `companyName` field.

3. **View Logs**:

   - Right-click on the **JsonCBR** component and select **View Logs**.
   - Check for any error messages or warnings.

4. **Test Edge Cases**:

   - Try with different values for `companyName`, including null or missing fields.
   - Verify that the system handles invalid data gracefully.

#### Step 7: Optional Enhancements

1. **Add More Routing Conditions**:

   - Add additional routing conditions for other companies or criteria.

2. **Dynamic Response Content**:

   - Use data from the incoming message to customize responses further.

3. **Error Handling**:

   - Implement error handling for malformed JSON or missing required fields.
   - Use the **Exception Port** of the JsonCBR component to route errors.

4. **Logging and Monitoring**:

   - Add logging components to record routing decisions and message content for auditing.

### Best Practices

- **Accurate JSONPath Expressions**:

  - Ensure that JSONPath expressions used in routing conditions are accurate and tested.
  - Use tools or online testers to validate JSONPath expressions.

- **Default Handling**:

  - Always provide a default route to handle messages that do not match any conditions.
  - This prevents messages from being lost and allows for graceful handling of unexpected data.

- **Performance Considerations**:

  - Be cautious of complex JSONPath expressions that may impact performance.
  - Test the JsonCBR component under expected load conditions.

- **Security Considerations**:

  - Validate and sanitize incoming messages to prevent injection attacks.
  - Ensure that sensitive data is handled securely.

- **Error Handling**:

  - Implement robust error handling to manage exceptions or invalid data.
  - Provide meaningful error responses to clients when appropriate.

- **Logging and Auditing**:

  - Include logging to record routing decisions and errors.
  - This aids in troubleshooting and auditing.

### Conclusion

You have successfully learned how to implement Content-Based Routing using the **JsonCBR** component in Fiorano. By routing messages based on their JSON content, you can create dynamic and flexible integration workflows that respond to the specific needs of your data.

Content-Based Routing is a powerful pattern in enterprise integration, allowing you to:

- Route messages to different processing paths based on content.
- Apply specific business logic depending on the data.
- Enhance scalability by separating processing concerns.

Understanding how to configure and use the JsonCBR component enables you to design intelligent and responsive integration solutions.

In the next session, we will explore schema validation using the **XMLVerification** component to ensure that messages conform to expected schemas.

---

## 6.6 Adapter Flow Part 6: Schema Validation using XMLVerification

### Introduction

In this session, we will explore how to validate XML messages against a predefined schema using Fiorano's **XMLVerification** component. Schema validation is essential in integration workflows to ensure that incoming messages conform to the expected structure and data types before processing them further. By validating messages against an XML Schema Definition (XSD), you can prevent processing errors, enforce data integrity, and maintain consistency across your applications.

### Objectives

- Understand the importance of schema validation in integration workflows.
- Learn how to use the **XMLVerification** component to validate XML messages.
- Configure the XMLVerification component with the appropriate XSD schema.
- Implement a workflow that validates incoming messages and handles validation errors.
- Test and validate the schema validation mechanism within an event process.
- Apply best practices for using the XMLVerification component in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Basic understanding of XML and XSD schemas.
- Familiarity with Fiorano components and event processes.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Exposes a REST service** that accepts XML messages.
2. **Uses the XMLVerification component** to validate incoming messages against a predefined XSD schema.
3. **Routes messages** to different paths based on the validation result:
   - If the message is valid, it proceeds to further processing.
   - If the message is invalid, it is routed to an error handling component.
4. **Sends appropriate responses** back to the client, indicating success or validation errors.

This scenario demonstrates how to use the XMLVerification component to enforce message conformity and handle validation failures gracefully.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `SchemaValidationExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **XMLVerification**: Validates XML messages against an XSD schema.
     - In the **Microservice Palette**, locate **XMLVerification** under **Flow Components**.
     - Drag and drop the **XMLVerification** component onto the canvas.
   - **Success Handler**: Processes valid messages.
     - Add a **Mapper** or **Display** component to simulate further processing.
   - **Error Handler**: Handles invalid messages.
     - Add a **Mapper** or **Display** component to handle validation errors.

3. **Connect Components**:

   - **REST Stub to XMLVerification**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **XMLVerification** component.
   - **XMLVerification Outputs**:
     - **Output Port** (valid messages):
       - Draw a route from the **Output Port** of the **XMLVerification** to the **Success Handler** component.
     - **Exception Port** (invalid messages):
       - Draw a route from the **Exception Port** (red port) of the **XMLVerification** to the **Error Handler** component.
   - **Handlers back to REST Stub Response**:
     - From both the **Success Handler** and **Error Handler** components, draw routes to the **Response Port** of the **REST Stub** to send responses back to the client.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `ValidationService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/validate`.
     - **ID**: Optionally, `ValidateResource`.
   - **Add Method**:
     - **Method**: Choose **POST**.

4. **Request Representation**:

   - Under **Request**, click **Add Representation**.
   - **Media Type**: Select `application/xml`.
   - **Schema**: Optionally provide an XSD schema to define the expected XML structure.

5. **Finish Configuration**.

#### Step 3: Define the XSD Schema for Validation

Create an XSD schema that defines the expected structure of the incoming XML messages.

Example XSD (`message.xsd`):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
            elementFormDefault="qualified">
  <xsd:element name="Customer">
    <xsd:complexType>
      <xsd:sequence>
        <xsd:element name="CustomerID" type="xsd:int"/>
        <xsd:element name="FirstName" type="xsd:string"/>
        <xsd:element name="LastName" type="xsd:string"/>
        <xsd:element name="Email" type="xsd:string"/>
        <xsd:element name="PhoneNumber" type="xsd:string" minOccurs="0"/>
      </xsd:sequence>
    </xsd:complexType>
  </xsd:element>
</xsd:schema>
```

- The `PhoneNumber` element is optional (`minOccurs="0"`).

#### Step 4: Configure the XMLVerification Component

1. **Open Configuration**:

   - Double-click on the **XMLVerification** component.

2. **Validation Configuration**:

   - **Source of Content to Validate**:
     - Select **Body** (to validate the message body).
   - **Structure for Message Body**:
     - **Import XSD Schema**:
       - Click **Load from File** and select the `message.xsd` file you created.
     - **Select Root Element**:
       - After importing, click **Select Root Element** and choose `Customer`.
     - **Validate Input**:
       - Ensure **Validate Input** is set to **Yes**.

3. **Other Settings**:

   - Leave other settings at their default values unless specific configurations are needed.

4. **Finish Configuration**.

#### Step 5: Configure Success and Error Handlers

1. **Success Handler**:

   - **Transformation**:

     - Use a **Mapper** to create a success response.
     - For example, set a constant message:

       ```xml
       <Response>
         <Status>Success</Status>
         <Message>Request aligns with the schema.</Message>
       </Response>
       ```

   - **Media Type**:
     - Ensure the response is set to `application/xml`.

2. **Error Handler**:

   - **Transformation**:

     - Use a **Mapper** to create an error response.
     - For example, set a constant message:

       ```xml
       <Response>
         <Status>Error</Status>
         <Message>Request does not align with the schema.</Message>
       </Response>
       ```

   - **Media Type**:
     - Ensure the response is set to `application/xml`.

#### Step 6: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/validate`).
   - **Method**: **POST**.
   - **Headers**:

     - `Content-Type`: `application/xml`.

   - **Test Cases**:

     - **Valid XML Message**:

       ```xml
       <Customer>
         <CustomerID>123</CustomerID>
         <FirstName>John</FirstName>
         <LastName>Doe</LastName>
         <Email>john.doe@example.com</Email>
         <PhoneNumber>123-456-7890</PhoneNumber>
       </Customer>
       ```

       - **Expected Response**:

         ```xml
         <Response>
           <Status>Success</Status>
           <Message>Request aligns with the schema.</Message>
         </Response>
         ```

     - **Invalid XML Message (missing required element)**:

       ```xml
       <Customer>
         <CustomerID>123</CustomerID>
         <!-- Missing FirstName -->
         <LastName>Doe</LastName>
         <Email>john.doe@example.com</Email>
       </Customer>
       ```

       - **Expected Response**:

         ```xml
         <Response>
           <Status>Error</Status>
           <Message>Request does not align with the schema.</Message>
         </Response>
         ```

     - **Invalid XML Message (extra element)**:

       ```xml
       <Customer>
         <CustomerID>123</CustomerID>
         <FirstName>John</FirstName>
         <LastName>Doe</LastName>
         <Email>john.doe@example.com</Email>
         <MiddleName>Alan</MiddleName> <!-- Element not defined in schema -->
       </Customer>
       ```

       - **Expected Response**:

         ```xml
         <Response>
           <Status>Error</Status>
           <Message>Request does not align with the schema.</Message>
         </Response>
         ```

   - **Send the Requests** and verify the responses.

#### Step 7: Validate and Troubleshoot

1. **Use Breakpoints and Debugger**:

   - Set breakpoints on the routes after the **XMLVerification** component to inspect which path the messages take.
   - Verify that valid messages proceed to the **Success Handler** and invalid messages to the **Error Handler**.

2. **Check Logs**:

   - Right-click on the **XMLVerification** component and select **View Logs**.
   - Look for detailed validation error messages that can help identify why a message failed validation.

3. **Review XSD Schema**:

   - Ensure the XSD schema accurately represents the expected message structure.
   - Check for typos or incorrect data types.

4. **Test Edge Cases**:

   - Test with various messages, including optional elements, empty elements, or incorrect data types, to ensure validation works as expected.

#### Step 8: Optional Enhancements

1. **Detailed Error Responses**:

   - Modify the **Error Handler** to include specific validation error messages returned by the **XMLVerification** component.
   - Use mapping functions to extract error details from the exception message.

2. **Validation of Namespaces**:

   - If your XML messages use namespaces, configure the **XMLVerification** component accordingly.
   - Ensure that the XSD schema includes the appropriate namespace definitions.

3. **Dynamic Schema Selection**:

   - Implement logic to select different XSD schemas based on message content or other criteria.

4. **Error Logging and Notifications**:

   - Add components to log validation errors or notify administrators when validation failures occur.

### Best Practices

- **Accurate and Up-to-Date Schemas**:

  - Maintain accurate XSD schemas that reflect the current expected message structures.
  - Update schemas as your data models evolve.

- **Consistent Use of Namespaces**:

  - When using namespaces, ensure consistency between the XML messages and the XSD schemas.
  - Define and use prefixes appropriately.

- **Performance Considerations**:

  - Be mindful of the performance impact of schema validation, especially with large messages.
  - Test the validation component under expected load conditions.

- **Error Handling**:

  - Provide meaningful error messages to clients to help them correct the issues.
  - Avoid exposing sensitive information in error responses.

- **Security Considerations**:

  - Validate all incoming messages to prevent injection attacks or malformed data from entering your system.
  - Implement additional security measures as needed.

- **Logging and Monitoring**:

  - Keep logs of validation successes and failures for auditing and troubleshooting.
  - Monitor validation error rates to identify potential issues.

### Conclusion

You have successfully learned how to use the **XMLVerification** component in Fiorano to validate XML messages against XSD schemas. By implementing schema validation, you can ensure that incoming messages conform to expected structures and data types, enhancing the reliability and integrity of your integration workflows.

Schema validation is a critical practice in enterprise integrations, allowing you to:

- Enforce data integrity and prevent processing errors.
- Protect backend systems from invalid or malicious data.
- Simplify debugging by catching errors early in the processing chain.

Understanding how to configure and use the XMLVerification component enables you to build robust and secure integration solutions that adhere to defined data contracts.

In the next session, we will explore the **Sleep** component in Fiorano and learn how to implement delays or simulate processing times within your workflows.

---

## 6.7 Adapter Flow Part 7: Using Sleep Component in Fiorano

### Introduction

In this session, we will explore how to use Fiorano's **Sleep** component to introduce delays within your integration workflows. The Sleep component is useful when you need to simulate processing times, throttle message flow, or introduce controlled latency between operations. This can be particularly important when coordinating with backend systems that require time to process requests or when you need to ensure that certain operations occur after a specified delay.

### Objectives

- Understand the purpose and use cases of the **Sleep** component in integration workflows.
- Learn how to configure the Sleep component to introduce delays.
- Implement a workflow that utilizes the Sleep component to handle timing dependencies.
- Test and validate the Sleep component's effect within an event process.
- Apply best practices for using the Sleep component in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Basic understanding of Fiorano components and event processes.
- Familiarity with creating REST services and invoking backend services.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Exposes a REST service** that accepts data to be posted to a backend service.
2. **Sends data to a backend service** (simulated using a Sleep component or another suitable component).
3. **Introduces a delay** using the Sleep component before attempting to retrieve data from the backend service.
4. **Fetches data from the backend service** after the delay and processes it as needed.
5. **Sends the response** back to the client.

This scenario addresses a common issue where a backend service takes time to process data, and attempting to retrieve the data immediately after posting might result in incomplete or missing data. By introducing a delay, we ensure that the backend service has enough time to process the request before we attempt to fetch the data.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `SleepComponentExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** onto the canvas.
   - **REST Consumer (Post to Backend)**: Simulates posting data to a backend service.
     - Drag and drop the **REST Consumer** component.
     - Rename it to `PostToBackend`.
   - **Sleep**: Introduces a delay.
     - Drag and drop the **Sleep** component from the **Flow Components** category.
   - **REST Consumer (Get from Backend)**: Simulates fetching data from a backend service.
     - Drag and drop another **REST Consumer** component.
     - Rename it to `GetFromBackend`.
   - **Mapper** (Optional): For data transformations.
     - Drag and drop the **Mapper** component if needed.
   - **Response Component**: Sends the response back to the client.
     - Use the **Mapper** component or connect directly to the **REST Stub** response port.

3. **Connect Components**:

   - **REST Stub to PostToBackend**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the `PostToBackend` component.
   - **PostToBackend to Sleep**:
     - Draw a route from the **Output Port** of the `PostToBackend` component to the **Input Port** of the **Sleep** component.
   - **Sleep to GetFromBackend**:
     - Draw a route from the **Output Port** of the **Sleep** component to the **Input Port** of the `GetFromBackend` component.
   - **GetFromBackend to Response Component**:
     - Draw a route from the **Output Port** of the `GetFromBackend` component to the **Response Port** of the **REST Stub**.
     - Add a **Mapper** component if you need to transform the data before sending the response.

#### Step 2: Configure the REST Stub Component

1. **Open Configuration**:

   - Double-click on the **REST Stub** component.

2. **Service Name**:

   - Enter `SleepComponentService`.

3. **Resources**:

   - **Add Resource**:
     - **Path**: Enter `/process`.
     - **ID**: Optionally, `ProcessResource`.
   - **Add Method**:
     - **Method**: Choose **POST**.

4. **Request Representation**:

   - Under **Request**, click **Add Representation**.
   - **Media Type**: Select `application/json`.
   - **Schema**: Define the JSON schema as needed.

5. **Finish Configuration**.

#### Step 3: Configure the PostToBackend Component

1. **Open Configuration**:

   - Double-click on the `PostToBackend` **REST Consumer** component.

2. **Endpoint Configuration**:

   - **Base URL**: Enter the URL of the backend service endpoint for posting data.
     - For simulation purposes, you can use a mock service or a placeholder URL.
   - **Resource**:
     - **Path**: Enter the specific resource path if needed.
   - **HTTP Method**:
     - Set to **POST**.

3. **Request Settings**:

   - **Request Body**:
     - Configure to send the data received from the client.
     - Use mappings if needed.

4. **Security and Advanced Settings**:

   - Configure SSL, authentication, or headers as required.

5. **Finish Configuration**.

#### Step 4: Configure the Sleep Component

1. **Open Configuration**:

   - Double-click on the **Sleep** component.

2. **Sleep Time Configuration**:

   - **Sleep Time**:
     - Enter the delay duration in milliseconds.
     - For example, if you want a 6-second delay, enter `6000`.
     - Alternatively, select **Time Unit** as **Seconds** and enter `6` for easier readability.

3. **Finish Configuration**.

#### Step 5: Configure the GetFromBackend Component

1. **Open Configuration**:

   - Double-click on the `GetFromBackend` **REST Consumer** component.

2. **Endpoint Configuration**:

   - **Base URL**: Enter the URL of the backend service endpoint for fetching data.
   - **Resource**:
     - **Path**: Enter the specific resource path if needed.
   - **HTTP Method**:
     - Set to **GET**.

3. **Request Settings**:

   - **Query Parameters**:
     - If needed, map any identifiers (e.g., `ID`) required to fetch the correct data.
     - Use the **Mapper** component to extract and pass the required parameters from previous components.

4. **Security and Advanced Settings**:

   - Configure SSL, authentication, or headers as required.

5. **Finish Configuration**.

#### Step 6: Configure Mappings

1. **From REST Stub to PostToBackend**:

   - Ensure that request data from the client is correctly passed to the `PostToBackend` component.

2. **From PostToBackend to Sleep Component**:

   - If any data needs to be passed through, configure mappings accordingly.

3. **From Sleep Component to GetFromBackend**:

   - Use a **Mapper** component if you need to extract identifiers or data required for the `GetFromBackend` request.
   - Map any necessary properties, such as transaction IDs or record IDs.

4. **From GetFromBackend to REST Stub Response**:

   - Ensure that the response from `GetFromBackend` is correctly mapped back to the client.
   - Use a **Mapper** component to transform the data into the required format.

#### Step 7: Run and Test the Event Process

1. **Save the Event Process**.

2. **Check Resources and Connectivity (CRC)**.

3. **Run the Event Process**:

   - Click on **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

4. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/process`).
   - **Method**: **POST**.
   - **Headers**:
     - `Content-Type`: `application/json`.
   - **Body**:
     - Provide sample JSON data as per your schema.
   - **Send the Request**.

5. **Observe the Delay**:

   - Note that the response will be delayed by the duration specified in the **Sleep** component (e.g., 6 seconds).
   - This delay allows the backend service to process the data before fetching.

6. **Verify the Response**:

   - Ensure that the data retrieved from the `GetFromBackend` component is as expected.
   - Check for any errors or issues in the data retrieval process.

#### Step 8: Validate and Troubleshoot

1. **Use Breakpoints and Debugger**:

   - Set breakpoints on the routes or components to inspect data at different stages.
   - Verify that the delay is occurring as configured.

2. **Check Component Logs**:

   - Right-click on components and select **View Logs** to check for any error messages.

3. **Test with Different Delay Durations**:

   - Adjust the sleep duration to match the processing time of your backend service.
   - Ensure that the delay is sufficient for the backend service to complete processing.

4. **Simulate Backend Processing Time**:

   - If you do not have an actual backend service, you can use a **Sleep** component or a **Mock** service to simulate processing time in the `PostToBackend` component.

### Best Practices

- **Accurate Delay Configuration**:

  - Determine the appropriate delay by testing how long the backend service takes to process the data.
  - Avoid unnecessary long delays that could impact user experience.

- **Error Handling**:

  - Implement error handling to manage scenarios where the backend service fails to process the data within the expected time.
  - Consider adding retries or alternative logic if data is not available after the delay.

- **Dynamic Delay Adjustment**:

  - If backend processing times vary, consider implementing dynamic delay adjustments based on context or response indicators.

- **Resource Management**:

  - Be mindful of the impact of the Sleep component on system resources and throughput.
  - Use the Sleep component judiciously, especially in high-throughput systems.

- **Logging and Monitoring**:

  - Include logging to monitor delays and processing times.
  - Monitor the workflow to identify any bottlenecks or inefficiencies.

### Conclusion

You have successfully learned how to use the **Sleep** component in Fiorano to introduce delays within your integration workflows. By incorporating delays, you can coordinate timing dependencies between different components, ensuring that operations occur in the correct sequence and that backend services have sufficient time to process data.

The Sleep component is particularly useful in scenarios where:

- **Backend Processing Time**: A backend service takes time to process data, and you need to wait before attempting to retrieve the results.
- **Rate Limiting**: You need to throttle message flow to prevent overloading a service.
- **Simulating Processing Time**: During testing, you want to simulate delays to mimic real-world conditions.

Understanding how to configure and use the Sleep component allows you to design more robust and reliable integration solutions that can handle timing challenges effectively.

---

### End of Module 6: Flow Adapters

This concludes Module 6 of the Fiorano Product Training series. In this module, we explored various **Flow Adapters** and how they can enhance and control the flow of messages within your integration workflows. By mastering components like Load Distribution, Cache, XMLSplitter, Aggregation, JsonCBR, XMLVerification, and Sleep, you are now equipped to design complex and efficient workflows that meet enterprise integration requirements.

---

# Module 7: Advanced Data Transformation

Welcome to Module 7 of the Fiorano Product Training series. In this module, we will delve into advanced data transformation techniques using Fiorano. These techniques are essential for integrating with specialized systems, handling complex data formats, and enabling seamless communication between diverse applications.

---

## Overview of Module 7

- **7.1 Advanced Data Transformation (OFS to XML)**
- **7.2 Advanced Data Transformation (XML to OFS)**
- **7.3 Advanced Data Transformation (XML to PDF)**
- **7.4 Integrating with JMS Adapters (JMSIn and JMSOut)**

---

## 7.1 Advanced Data Transformation (OFS to XML)

### Introduction

In this session, we will learn how to transform data from **OFS (Open Financial Services)** format to **XML** using Fiorano's **OFSXMLConverter** component. OFS is a specialized format used in the banking industry, particularly with systems like **Temenos T24**, which is a core banking software widely used by financial institutions.

Transforming OFS messages to XML enables organizations to process and integrate banking transactions efficiently, leveraging XML's structured and widely accepted format.

### Objectives

- Understand what OFS format is and its role in banking integrations.
- Learn how to use the **OFSXMLConverter** component to convert OFS messages to XML.
- Configure the OFSXMLConverter component for OFS to XML transformation.
- Test and validate the transformation using a sample message.
- Apply best practices for handling OFS messages in Fiorano.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- Basic understanding of Fiorano components and event processes.
- Familiarity with XML structure and data formats.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Receives an OFS message** using a **Feeder** component.
2. **Transforms the OFS message to XML** using the **OFSXMLConverter** component.
3. **Displays the resulting XML message** using a **Display** component.

This scenario simulates a typical integration where OFS messages from a core banking system like Temenos T24 are transformed into XML for further processing.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter `OFS2XMLTransformation`.
   - **Category**: Choose or create a package (e.g., `AdvancedTransformations`).
   - Click **Finish**.

2. **Add Components**:

   - **Feeder**: Acts as the message source.
     - Drag and drop the **Feeder** component onto the canvas.
   - **OFSXMLConverter**:
     - In the **Microservice Palette**, find **OFSXMLConverter** under **Transformation** components.
     - Drag and drop the **OFSXMLConverter** onto the canvas.
   - **Display**: Used to display the output XML message.
     - Drag and drop the **Display** component onto the canvas.

3. **Connect Components**:

   - **From Feeder to OFSXMLConverter**:
     - Draw a route from the **Output Port** of the **Feeder** to the **Input Port** of the **OFSXMLConverter**.
   - **From OFSXMLConverter to Display**:
     - Draw a route from the **Output Port** of the **OFSXMLConverter** to the **Input Port** of the **Display** component.

#### Step 2: Configure the OFSXMLConverter Component

1. **Open Configuration**:

   - Double-click on the **OFSXMLConverter** component.

2. **Conversion Direction**:

   - **Select Operation**: Choose **OFS to XML** (default).

3. **Root Element Name** (Optional):

   - **Root Element**: You can specify a root element name for the resulting XML document.
     - For example, enter `TransactionMessage`.
   - **Note**: The root element is optional and can be left blank if not needed.

4. **Delimiter Settings** (Optional):

   - If your OFS message uses a specific delimiter other than the default, configure it here.
   - **Field Delimiter**: Specify the delimiter used in the OFS message fields (e.g., `,`).

5. **Finish Configuration**:

   - Click **Finish** to save the settings.

#### Step 3: Prepare the OFS Message in the Feeder Component

1. **Understand the OFS Message Format**:

   - An OFS message typically consists of a header and a message body, with fields delimited by a specific character (e.g., comma).
   - **Example OFS Message**:

     ```
     HEADER:REQUESTID:SECURITYTOKEN:SERVICENAME
     CUSTOMER:60665,SMITH,JOHN,NATIONALITY,COUNTRY
     ```

   - **Explanation**:
     - `HEADER`: Represents the message header with details like `REQUESTID`, `SECURITYTOKEN`, `SERVICENAME`.
     - `CUSTOMER`: Entity type (e.g., customer information).
     - Fields are delimited by commas.

2. **Input the OFS Message into the Feeder**:

   - Double-click on the **Feeder** component.
   - **Input Message**:
     - Enter the OFS message in the **Text** field.
   - **Sample OFS Message**:

     ```
     CUSTOMER:60665,SMITHJOHN,NATIONALITY,US,RESIDENCE,US,DOB,1980-01-01
     ```

#### Step 4: Run and Test the Event Process

1. **Save the Event Process**.

2. **Run the Event Process**:

   - Click on **Run Event Process**.
   - Ensure that all components turn green, indicating they are running.

3. **Send the OFS Message**:

   - In the **Feeder** component, with the OFS message entered, click **Send**.

4. **View the Transformed XML Message**:

   - Double-click on the **Display** component to view the output.
   - **Expected Output**:

     ```xml
     <TransactionMessage>
       <Entity>
         <Type>CUSTOMER</Type>
         <Field1>60665</Field1>
         <Field2>SMITHJOHN</Field2>
         <Field3>NATIONALITY</Field3>
         <Field4>US</Field4>
         <Field5>RESIDENCE</Field5>
         <Field6>US</Field6>
         <Field7>DOB</Field7>
         <Field8>1980-01-01</Field8>
       </Entity>
     </TransactionMessage>
     ```

   - **Explanation**:
     - The OFS message fields are mapped to XML elements.
     - If a mapping configuration is provided, field names can be more meaningful.

#### Step 5: (Optional) Configure Field Mapping

If you need to map OFS fields to specific XML element names, you can configure a mapping.

1. **Edit the OFSXMLConverter Configuration**:

   - Double-click on the **OFSXMLConverter** component.
   - Navigate to the **Field Mapping** section.

2. **Define Field Mappings**:

   - Map each OFS field to a meaningful XML element name.
   - **Example Mapping**:

     - **Field1**: Map to `CustomerNumber`.
     - **Field2**: Map to `CustomerName`.
     - **Field3**: Map to `Attribute`.
     - **Field4**: Map to `Value`.
     - Continue mapping as needed.

3. **Finish Configuration**.

4. **Run the Event Process Again**:

   - Stop and restart the event process for the changes to take effect.
   - Send the OFS message again and view the output in the **Display** component.
   - **Updated Output**:

     ```xml
     <TransactionMessage>
       <Entity>
         <Type>CUSTOMER</Type>
         <CustomerNumber>60665</CustomerNumber>
         <CustomerName>SMITHJOHN</CustomerName>
         <Attribute>NATIONALITY</Attribute>
         <Value>US</Value>
         <!-- Additional fields as mapped -->
       </Entity>
     </TransactionMessage>
     ```

#### Step 6: Validate and Troubleshoot

1. **Check for Errors**:

   - If the transformation does not produce the expected output, check the **Logs** of the **OFSXMLConverter** component.

2. **Confirm Delimiters**:

   - Ensure that the field delimiter configured matches the delimiter used in the OFS message.

3. **Verify Field Mappings**:

   - Confirm that the field mappings correspond to the correct field positions in the OFS message.

### Best Practices

- **Consistent OFS Format**:

  - Ensure that all OFS messages conform to the expected format and delimiter usage.

- **Field Mapping**:

  - Provide meaningful field mappings to enhance the readability of the resulting XML.

- **Error Handling**:

  - Implement error handling mechanisms to manage invalid messages or transformation failures.

- **Integration with T24**:

  - When integrating with Temenos T24 or similar systems, collaborate with the system administrators to understand the exact OFS message structure.

- **Testing with Real Data**:

  - Use actual OFS messages from your environment for testing to ensure accuracy.

### Summary

In this session, you have learned how to:

- Use the **OFSXMLConverter** component to transform OFS messages to XML.
- Configure the component for OFS to XML transformation.
- Map OFS fields to meaningful XML element names.
- Test the transformation using sample messages.

By mastering OFS to XML transformation, you can facilitate integration with core banking systems like Temenos T24, enabling efficient processing and routing of financial transactions.

---

## 7.2 Advanced Data Transformation (XML to OFS)

### Introduction

In this session, we will learn how to transform data from **XML** to **OFS (Open Financial Services)** format using the **OFSXMLConverter** component in Fiorano. Converting XML messages to OFS format is essential when sending data to core banking systems like Temenos T24, which require OFS-formatted messages for processing transactions.

### Objectives

- Understand how to use the **OFSXMLConverter** component to convert XML messages to OFS format.
- Configure the OFSXMLConverter component for XML to OFS transformation.
- Prepare XML messages and test the transformation.
- Apply best practices for generating OFS messages in Fiorano.

### Prerequisites

- Familiarity with XML structure and data formats.
- Understanding of OFS message requirements for the target system.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Receives an XML message** using a **Feeder** component.
2. **Transforms the XML message to OFS format** using the **OFSXMLConverter** component.
3. **Displays the resulting OFS message** using a **Display** component.

This scenario simulates preparing data to be sent to a core banking system that accepts OFS-formatted messages.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Name: `XML2OFSTransformation`.
   - Category: `AdvancedTransformations`.

2. **Add Components**:

   - **Feeder**: Input XML message.
   - **OFSXMLConverter**: For XML to OFS conversion.
   - **Display**: To show the OFS output.

3. **Connect Components**:

   - From **Feeder** to **OFSXMLConverter**.
   - From **OFSXMLConverter** to **Display**.

#### Step 2: Configure the OFSXMLConverter Component

1. **Conversion Direction**:

   - **Select Operation**: Choose **XML to OFS**.

2. **Root Element Name**:

   - Specify the root element if required (e.g., `TransactionMessage`).

3. **Finish Configuration**.

#### Step 3: Prepare the XML Message in the Feeder Component

1. **Sample XML Message**:

   ```xml
   <TransactionMessage>
     <FunctionName>ADD.CUSTOMER</FunctionName>
     <Operation>D</Operation>
     <TransactionId>123456</TransactionId>
     <TransactionDetails>
       <CustomerNumber>60665</CustomerNumber>
       <ShortName>SMITHJOHN</ShortName>
       <Nationality>US</Nationality>
       <Residence>US</Residence>
       <DateOfBirth>1980-01-01</DateOfBirth>
     </TransactionDetails>
   </TransactionMessage>
   ```

2. **Input the XML Message**:

   - Paste the XML message into the **Feeder** component's **Input Message** field.

#### Step 4: Run and Test the Event Process

1. **Save and Run** the event process.

2. **Send the XML Message** using the **Feeder** component.

3. **View the OFS Message** in the **Display** component.

   - **Expected Output**:

     ```
     ADD.CUSTOMER,D,123456,60665,SMITHJOHN,NATIONALITY.US,RESIDENCE.US,DOB.1980-01-01
     ```

   - **Explanation**:
     - The XML elements are converted to OFS fields, delimited appropriately.
     - The hierarchy and element names may affect the output format.

#### Step 5: Configure Field Mapping (Optional)

1. **Customize Field Mapping**:

   - In the **OFSXMLConverter** configuration, map XML elements to specific positions in the OFS message.

2. **Field Mapping Example**:

   - Map `/TransactionMessage/FunctionName` to Field1.
   - Map `/TransactionMessage/Operation` to Field2.
   - Map `/TransactionMessage/TransactionId` to Field3.
   - Map `/TransactionMessage/TransactionDetails/CustomerNumber` to Field4.
   - Continue mapping as required.

3. **Test the Transformation Again**:

   - Send the XML message and verify that the OFS output reflects the mapping.

### Best Practices

- **Accurate Field Mapping**:

  - Carefully map XML elements to OFS fields to ensure data integrity.

- **Delimiter Consistency**:

  - Ensure that the OFS message uses the correct field delimiters expected by the receiving system.

- **Validation**:

  - Validate the XML input against an XSD schema before transformation.

- **Testing with the Target System**:

  - Test the OFS messages with the actual core banking system (e.g., Temenos T24) to confirm compatibility.

### Summary

You have learned how to:

- Use the **OFSXMLConverter** component for XML to OFS transformation.
- Configure field mappings to control the output format.
- Prepare XML messages and generate corresponding OFS messages.

By mastering XML to OFS transformation, you can efficiently prepare data for core banking systems that require OFS-formatted messages, ensuring seamless integration and data exchange.

---

## 7.3 Advanced Data Transformation (XML to PDF)

### Introduction

In this session, we will learn how to transform XML data into PDF documents using Fiorano's **XML to PDF** component. Generating PDFs from XML data is a common requirement for creating reports, invoices, receipts, or any documents that need to be shared in a universally accepted format.

### Objectives

- Understand how to use the **XML to PDF** component to generate PDF documents from XML data.
- Configure the component using XSL-FO or XML with XSLT.
- Prepare XML and XSL-FO input for PDF generation.
- Test and validate the PDF output.
- Apply best practices for generating PDFs in Fiorano.

### Prerequisites

- Familiarity with XML and XSL-FO (Extensible Stylesheet Language Formatting Objects).
- Basic understanding of XSLT transformations.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Receives XML data** using a **Feeder** component.
2. **Uses the XML to PDF component** to generate a PDF document.
3. **Stores the generated PDF** in a specified directory.

This scenario demonstrates how to produce PDF documents from XML data, which can be used for generating reports or documents in integration workflows.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Name: `XML2PDFTransformation`.
   - Category: `AdvancedTransformations`.

2. **Add Components**:

   - **Feeder**: Input XML data with styling information.
   - **XML to PDF**: For PDF generation.

3. **Connect Components**:

   - From **Feeder** to **XML to PDF**.

#### Step 2: Configure the XML to PDF Component

1. **Open Configuration**:

   - Double-click on the **XML to PDF** component.

2. **PDF Creation Method**:

   - **Create PDF Using**:
     - Choose **XSL-FO** if you have XML data with embedded formatting objects.
     - Alternatively, choose **XML and XSL** if you have separate XML data and XSLT for transformation.

3. **Output File Configuration**:

   - **Target Directory**:
     - Specify the directory where the PDF file will be saved.
     - Example: `C:\Fiorano\PDFOutput`.
   - **Output File Name**:
     - Provide a name for the generated PDF file.
     - Example: `Report.pdf`.

4. **Advanced Settings** (if using XML and XSL):

   - **XSL File**:
     - Provide the path to the XSLT file used to transform XML into XSL-FO.

5. **Finish Configuration**.

#### Step 3: Prepare the XML Input in the Feeder Component

1. **Sample XML with XSL-FO**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <root xmlns:fo="http://www.w3.org/1999/XSL/Format">
     <fo:root>
       <fo:layout-master-set>
         <fo:simple-page-master master-name="simple">
           <fo:region-body margin="1in"/>
         </fo:simple-page-master>
       </fo:layout-master-set>
       <fo:page-sequence master-reference="simple">
         <fo:flow flow-name="xsl-region-body">
           <fo:block font-size="14pt" font-weight="bold" text-align="center">
             Welcome to Fiorano Training
           </fo:block>
         </fo:flow>
       </fo:page-sequence>
     </fo:root>
   </root>
   ```

   - **Explanation**:
     - The XML includes XSL-FO elements that define the layout and content of the PDF.

2. **Input the XML Data**:

   - Paste the XML content into the **Feeder** component's **Input Message** field.

#### Step 4: Run and Test the Event Process

1. **Save and Run** the event process.

2. **Send the XML Data** using the **Feeder** component.

3. **Verify PDF Generation**:

   - Navigate to the **Target Directory** specified in the XML to PDF component configuration.
   - Confirm that the `Report.pdf` file has been created.

4. **Open the PDF File**:

   - Open the PDF file using a PDF reader.
   - **Expected Content**:
     - The PDF should display the text "Welcome to Fiorano Training" centered and in bold 14pt font.

#### Step 5: Using XML and XSL for PDF Generation (Optional)

If you prefer to use separate XML data and an XSLT stylesheet to generate the XSL-FO, you can configure the component accordingly.

1. **Prepare XML Data**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <message>
     <content>Welcome to Fiorano Training</content>
   </message>
   ```

2. **Prepare XSLT Stylesheet** (`style.xsl`):

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <xsl:stylesheet version="1.0"
     xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
     xmlns:fo="http://www.w3.org/1999/XSL/Format">
     <xsl:template match="/message">
       <fo:root>
         <fo:layout-master-set>
           <fo:simple-page-master master-name="simple">
             <fo:region-body margin="1in"/>
           </fo:simple-page-master>
         </fo:layout-master-set>
         <fo:page-sequence master-reference="simple">
           <fo:flow flow-name="xsl-region-body">
             <fo:block font-size="14pt" font-weight="bold" text-align="center">
               <xsl:value-of select="content"/>
             </fo:block>
           </fo:flow>
         </fo:page-sequence>
       </fo:root>
     </xsl:template>
   </xsl:stylesheet>
   ```

3. **Configure the XML to PDF Component**:

   - **Create PDF Using**: Select **XML and XSL**.
   - **XSL File**: Provide the path to `style.xsl`.

4. **Update the Feeder Input**:

   - Enter the XML data without the XSL-FO styling.

5. **Run and Test**:

   - Send the XML data via the **Feeder**.
   - Verify that the PDF is generated correctly.

### Best Practices

- **Valid XSL-FO**:

  - Ensure that the XSL-FO content is valid and adheres to the XSL-FO specification.

- **Separate Styling**:

  - Consider using separate XML and XSLT files for better maintainability.

- **Error Handling**:

  - Implement error handling to manage transformation errors or invalid input.

- **Fonts and Resources**:

  - Ensure that any fonts or external resources referenced in the XSL-FO are available.

- **Testing with Real Data**:

  - Use actual data and complex layouts to test the PDF generation thoroughly.

### Summary

In this session, you have learned how to:

- Use the **XML to PDF** component to generate PDF documents from XML data.
- Configure the component using XSL-FO or XML with XSLT.
- Prepare input data and test the PDF output.

By integrating PDF generation into your workflows, you can automate the creation of documents, reports, and other materials, enhancing the functionality of your integration solutions.

---

## 7.4 Integrating with JMS Adapters (JMSIn and JMSOut)

### Introduction

In this session, we will learn how to integrate with **Java Messaging Service (JMS)** adapters using the **JMSIn** and **JMSOut** components in Fiorano. JMS is a messaging standard that allows application components to create, send, receive, and read messages. By integrating with JMS, you can enable asynchronous communication between distributed systems, enhancing scalability and reliability.

### Objectives

- Understand the role of **JMSIn** and **JMSOut** components in messaging.
- Learn how to configure JMS adapters to publish and consume messages.
- Integrate Fiorano with external JMS providers (e.g., FioranoMQ, ActiveMQ).
- Test and validate message exchange using JMS adapters.
- Apply best practices for messaging in Fiorano.

### Prerequisites

- Familiarity with messaging concepts and JMS.
- Access to a JMS provider (e.g., FioranoMQ, ActiveMQ, RabbitMQ).
- Basic understanding of topics and queues in messaging systems.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Publishes messages** to a JMS destination using the **JMSIn** component.
2. **Consumes messages** from the JMS destination using the **JMSOut** component.
3. **Transforms and displays** the messages.

This scenario demonstrates how to set up messaging between components using JMS adapters, enabling decoupled and asynchronous communication.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Name: `JMSIntegrationExample`.
   - Category: `AdvancedTransformations`.

2. **Add Components**:

   - **Feeder**: Input messages to be published.
   - **JMSIn**: Publishes messages to a JMS destination.
   - **JMSOut**: Consumes messages from the JMS destination.
   - **Display**: To show the consumed messages.

3. **Connect Components**:

   - From **Feeder** to **JMSIn**.
   - From **JMSOut** to **Display**.

#### Step 2: Configure the JMSIn Component

1. **Open Configuration**:

   - Double-click on the **JMSIn** component.

2. **JMS Provider Configuration**:

   - **JMS Provider**: Select your JMS provider (e.g., **FioranoMQ**).
   - **Connection Configuration**:
     - **Provider URL**: Enter the URL of your JMS provider.
     - **Credentials**: Provide any required username and password.
     - **Test Connection**: Click to verify connectivity.

3. **Destination Configuration**:

   - **Destination Name**: Enter a unique name (e.g., `JMSDemoDestination`).
   - **Destination Type**: Choose **Topic** or **Queue**.
   - **Create Destination**: Enable if the destination should be created if it doesn't exist.

4. **Message Producer Settings**:

   - **Delivery Mode**: Choose **Persistent** or **Non-Persistent**.
   - **Priority**: Set the message priority if needed.
   - **Time to Live**: Specify the message expiration time in milliseconds.

5. **Finish Configuration**.

#### Step 3: Configure the JMSOut Component

1. **Open Configuration**:

   - Double-click on the **JMSOut** component.

2. **JMS Provider Configuration**:

   - Use the same JMS provider settings as in the JMSIn component.
   - **Test Connection**: Verify connectivity.

3. **Destination Configuration**:

   - **Destination Name**: Use the same name as in JMSIn (`JMSDemoDestination`).
   - **Destination Type**: Ensure it matches the JMSIn component (Topic or Queue).

4. **Message Consumer Settings**:

   - **Subscription**: For topics, decide if you want a durable subscription.
   - **Message Selector**: Optionally, use a selector to filter messages.

5. **Finish Configuration**.

#### Step 4: Run and Test the Event Process

1. **Save and Run** the event process.

2. **Send Messages Using the Feeder**:

   - Enter sample messages in the **Feeder** component.
   - Send messages to be published to the JMS destination.

3. **View Consumed Messages**:

   - Check the **Display** component to see the messages consumed by JMSOut.

#### Step 5: Validate Message Exchange

1. **Send Multiple Messages**:

   - Send several messages to observe the message flow.

2. **Use Breakpoints**:

   - Set breakpoints to inspect messages at different stages.

3. **Check JMS Destination**:

   - Use JMS provider tools to monitor the destination and verify messages are being published and consumed.

### Best Practices

- **Consistent Configuration**:

  - Ensure that the JMSIn and JMSOut components use the same destination configuration.

- **Message Durability**:

  - Use **Persistent** delivery mode for important messages that should not be lost.

- **Error Handling**:

  - Implement exception handling for connection errors or message consumption issues.

- **Security Configuration**:

  - Secure your JMS connections with proper authentication and encryption if required.

- **Scalability**:

  - Use topics for publish-subscribe patterns where multiple consumers need the same messages.
  - Use queues for point-to-point messaging.

### Summary

You have learned how to:

- Configure **JMSIn** and **JMSOut** components for message publishing and consumption.
- Integrate Fiorano with a JMS provider for asynchronous messaging.
- Test and validate message exchange using JMS adapters.

By integrating JMS adapters into your workflows, you can enable loose coupling between components, enhance scalability, and support enterprise messaging patterns.

---

## Conclusion of Module 7

In Module 7, we explored advanced data transformation techniques, including:

- **OFS to XML Transformation**: Converting specialized banking messages to XML for integration.
- **XML to OFS Transformation**: Preparing XML data for systems that require OFS format.
- **XML to PDF Transformation**: Generating PDF documents from XML data for reporting and documentation.
- **Integrating with JMS Adapters**: Enabling asynchronous messaging using JMSIn and JMSOut components.

By mastering these techniques, you can handle complex data formats, integrate with specialized systems like core banking platforms, and implement robust messaging solutions in your integration workflows.

---

# Module 8: Configurations, Extended Services, and Control Plane Dashboard

Welcome to Module 8 of the Fiorano Product Training series. In this module, we will delve into advanced configurations, explore extended services, and learn how to effectively use the Control Plane Dashboard for managing your Fiorano environment.

---

## Overview of Module 8

- **8.1 Named Configurations Part 1**: Message Filters
- **8.2 Named Configurations Part 2**: Route Transformations
- **8.3**: Retry Mechanism for Reliability
- **8.4**: Exporting and Importing Event Processes
- **8.5**: Extended Services in Fiorano
- **8.6 FES Dashboard Part 1**: Runtime Management
- **8.7 FES Dashboard Part 2**: Document Tracking
- **8.8**: Installing and Uninstalling Patches

---

## 8.1 Named Configurations Part 1: Message Filters

### Introduction

**Named Configurations** in Fiorano are reusable configurations that can be applied to components or routes within your event processes. They enhance reusability and maintainability by allowing you to define configurations once and apply them wherever needed.

In this session, we will focus on using named configurations for **Message Filters**. Message Filters allow you to define properties that can be dynamically referenced during runtime, aiding in scenarios where certain values are not provided by the client but are necessary for processing.

### Objectives

- Understand how to create and use named configurations for message filters.
- Learn how to define and assign message properties.
- Utilize message filters to fetch hard-coded properties during runtime.
- Apply best practices for using message filters in Fiorano.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Basic understanding of data mapping and transformations.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Exposes a REST service** to accept input from a client.
2. **Consumes a backend calculator service** that performs operations like **divide** and **add**.
3. **Uses named configurations** for message filters to provide necessary values that are not supplied by the client.
4. **Fetches these values** during runtime using message properties.

This scenario demonstrates how to use message filters to supply hard-coded values for properties that are required by the backend service but are not provided by the client.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Open Fiorano Studio (eStudio).
   - Right-click on **Event Process Repository** and select **Add Event Process**.
   - **Name**: Enter a name like `MessageFilterExample`.
   - **Category**: Choose or create a package (e.g., `FioranoTraining`).
   - Click **Finish**.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
     - Drag and drop the **REST Stub** component onto the canvas.
   - **REST Consumer**: Consumes the backend calculator service.
     - Drag and drop the **REST Consumer** component onto the canvas.
   - **Connect Components**:
     - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **REST Consumer**.

3. **Configure the REST Stub**:

   - **Service Name**: Enter `CalculatorService`.
   - **Resources**:
     - **Add Resource**:
       - **Path**: Enter `/calculate`.
       - **Add Method**: Choose **POST**.
     - **Request Representation**:
       - **Media Type**: `application/json`.
       - **Schema**: Define as needed.
   - **Finish Configuration**.

4. **Connect the **Response Port** of the **REST Consumer** back to the **Response Port** of the **REST Stub\*\* to send the result back to the client.

#### Step 2: Configure Named Configurations for Message Filters

1. **Create a Named Configuration**:

   - In the **Event Process** canvas, right-click on **Named Configurations** in the **Event Process Explorer**.
   - Select **Add Configuration**.
   - **Name**: Enter `CalculatorValues`.
   - **Type**: Choose **Message Filters**.
   - Click **Finish**.

2. **Define Message Properties**:

   - In the **Message Filters** window:
     - **Add Property**:
       - **Property Name**: `elementA`.
       - **Value**: `50`.
     - **Add Another Property**:
       - **Property Name**: `elementB`.
       - **Value**: `5`.
   - Click **OK** to save.

3. **Assign Message Properties to the Component Port**:

   - **Click on the Output Port** of the **REST Stub** component.
   - In the **Properties** pane, go to the **Message Properties** tab.
   - Under **Named Configurations**, select `CalculatorValues`.
   - The properties `elementA` and `elementB` will now be attached to the messages passing through this port.

#### Step 3: Configure the Route Transformation to Fetch Properties

1. **Configure Transformation on the Route**:

   - Right-click on the route from the **REST Stub** to the **REST Consumer**.
   - Select **Configure Transformation**.

2. **Use Message Properties in Mapper**:

   - **Source Schema**: Represents the request from the client.
   - **Target Schema**: Represents the input expected by the backend service.
   - **Mapping**:
     - In the **Mapping Functions** pane, expand **JMS Message Functions**.
     - Use **Get String Property** function to fetch properties.
     - **Configure the Function**:
       - **Name**: Enter `elementA`.
       - Drag the function result to the corresponding field in the **Target Schema**.
     - Repeat the steps to map `elementB`.

3. **Save** the mapping.

#### Step 4: Configure the REST Consumer Component

1. **Open Configuration**:

   - Double-click on the **REST Consumer** component.

2. **Endpoint Configuration**:

   - **Endpoint URL**: Configure the URL of the backend calculator service.
   - **HTTP Method**: Choose **POST** or as required.

3. **Finish Configuration**.

#### Step 5: Run and Test the Event Process

1. **Save the Event Process**.

2. **Run the Event Process**:

   - Click **Run Event Process**.
   - Ensure all components turn green, indicating they are running.

3. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component (e.g., `http://localhost:1856/calculate`).
   - **Method**: **POST**.
   - **Headers**:
     - `Content-Type`: `application/json`.
   - **Body**:
     ```json
     {
       "operation": "add"
     }
     ```
   - **Send the Request**.

4. **Observe the Backend Service Input**:

   - Use **Breakpoints** on the route to the **REST Consumer** to inspect the input.
   - Verify that `elementA` and `elementB` are present with values `50` and `5` respectively.

5. **Verify the Response**:

   - Ensure that the backend service uses the provided values and returns the correct result.
   - The response should contain the result of the calculation (e.g., `55` for addition).

#### Step 6: Troubleshooting

1. **Logs and Debugging**:

   - **View Logs**:
     - Right-click on components and select **View Logs** to check for any errors.
   - **Use Breakpoints**:
     - Inspect data at different stages to ensure properties are being fetched correctly.

2. **Property Names**:

   - Ensure that property names in the named configuration match exactly when fetching them in the mapper.

### Conclusion

You have successfully learned how to use named configurations for message filters in Fiorano. By defining message properties and attaching them to component ports, you can supply necessary values that are not provided by the client. This technique enhances flexibility and maintainability in your integration workflows.

---

## 8.2 Named Configurations Part 2: Route Transformations

### Introduction

In this session, we will explore how to use named configurations for **Route Transformations**. Reusing route transformations allows you to apply existing mappings to new routes, ensuring consistency and reducing development time.

### Objectives

- Understand how to create and use named configurations for route transformations.
- Learn how to save a route transformation as a named configuration.
- Apply an existing route transformation to a new route.
- Recognize the prerequisites for reusing route transformations.
- Apply best practices for using route transformations in Fiorano.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Basic understanding of data mapping and transformations.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process where:

1. **A REST service** is configured to perform an operation (e.g., **multiply**).
2. **A route transformation** is applied to map the request to the backend service.
3. **The same route transformation** is saved as a named configuration and reused in another route.
4. **Understand** the conditions necessary for reusing route transformations.

This scenario demonstrates how to reuse complex route transformations in different parts of your event processes.

### Step-by-Step Guide

#### Step 1: Prepare the Original Route Transformation

1. **Create a New Event Process** or open an existing one where you have a route transformation.

2. **Identify the Route Transformation**:

   - For example, from a **REST Stub** to a **REST Consumer** component configured for the **Multiply** operation.

3. **Open the Existing Transformation**:

   - Right-click on the route and select **Configure Transformation**.
   - Verify the mapping between the source and target schemas.

#### Step 2: Save the Route Transformation as a Named Configuration

1. **Save Configuration as Named Configuration**:

   - In the **Mapper**, click on **File** > **Save Configuration as Named Configuration**.
   - **Name**: Enter `MultiplyRoute`.
   - **Category**: Choose or create a category (e.g., `Transformation`).
   - Click **Finish**.

2. **Verify the Named Configuration**:

   - In the **Event Process Explorer**, expand **Named Configurations** > **Transformation**.
   - You should see `MultiplyRoute` listed.

#### Step 3: Reuse the Route Transformation in Another Route

1. **Add a New Route**:

   - In the same or another event process, create a route that requires the same transformation.
   - For example, from a **REST Stub** to a **REST Consumer** configured for the same **Multiply** operation.

2. **Apply the Named Configuration**:

   - Right-click on the new route and select **Configure Transformation**.
   - In the **Mapper**, click on **File** > **Use Named Configuration**.
   - Select `MultiplyRoute` and click **OK**.

3. **Verify the Transformation**:

   - The mapping should be applied to the new route.
   - Ensure that the schemas match; otherwise, you may see dotted lines indicating schema mismatches.

#### Step 4: Understand Prerequisites for Reusing Transformations

- **Schema Consistency**:

  - The source and target schemas in the new route must match those in the original transformation.
  - If the schemas differ, the mapping may not apply correctly.

- **Component Compatibility**:

  - The components connected by the route should be similar to those in the original route.

- **Adjustments**:

  - If necessary, update schemas using **Update Structure** in the **Mapper** to match the expected structures.

#### Step 5: Test the Reused Transformation

1. **Run the Event Process**.

2. **Test Using Postman**:

   - Send requests to the REST service and verify that the transformation works as expected.

3. **Monitor Logs and Outputs**:

   - Ensure that the backend service receives the correct data and responds appropriately.

### Best Practices

- **Consistent Schemas**:

  - Ensure that components and schemas are consistent when reusing route transformations.

- **Meaningful Naming**:

  - Use clear and descriptive names for named configurations to make them easily identifiable.

- **Document Mappings**:

  - Keep documentation or comments within the mappings to explain any complex logic.

- **Version Control**:

  - Manage versions of named configurations if mappings evolve over time.

- **Testing**:

  - Always test reused transformations to confirm they work correctly in the new context.

### Conclusion

You have successfully learned how to reuse route transformations using named configurations in Fiorano. This capability enhances efficiency by allowing you to define complex mappings once and apply them across multiple routes, ensuring consistency and reducing development time.

---

## 8.3 Retry Mechanism for Reliability

### Introduction

In integration workflows, transient errors such as network issues, temporary unavailability of services, or intermittent failures can occur. Implementing a **Retry Mechanism** enhances the reliability of your applications by attempting operations multiple times before failing.

In this session, we will learn how to configure retry mechanisms in Fiorano components like the **Database** and **REST Consumer** components.

### Objectives

- Understand the importance of implementing retry mechanisms for reliability.
- Learn how to configure retries on connection errors and request processing errors.
- Test and observe the retry behavior within an event process.
- Apply best practices for configuring retries in Fiorano.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Understanding of error handling in Fiorano.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an event process that:

1. **Exposes a REST service** to accept client requests.
2. **Uses a Database component** to perform operations that may fail due to connection errors.
3. **Configures retries** for connection errors and request processing errors.
4. **Observes** the retry behavior and handles exceptions.

This scenario demonstrates how to enhance the reliability of your event processes by implementing retry mechanisms.

### Step-by-Step Guide

#### Step 1: Set Up the Event Process Canvas

1. **Create a New Event Process**:

   - Name: `RetryMechanismExample`.
   - Category: `FioranoTraining`.

2. **Add Components**:

   - **REST Stub**: Exposes the REST service.
   - **Database**: Performs database operations.
   - **Display** (Optional): To display error messages.

3. **Connect Components**:

   - Draw a route from the **Output Port** of the **REST Stub** to the **Input Port** of the **Database** component.

#### Step 2: Configure the Database Component

1. **Open Configuration**:

   - Double-click on the **Database** component.

2. **Database Connection**:

   - **DB URL**: Intentionally enter an incorrect URL to simulate a connection error.
   - **DB User**: Enter an invalid username.
   - **DB Password**: Enter an invalid password.
   - **Test Connection**: It should fail, indicating a connection issue.

3. **Configure Error Handling**:

   - Navigate to the **Error Handling** tab.
   - **Retry on Connection Error**:
     - Enable the option.
     - **Number of Retries**: Set to `2`.
     - **Retry Interval**: Set to `5000` milliseconds (5 seconds).
   - **Retry on Invalid Request**:
     - Enable if you want to retry on request processing errors.

4. **Enable Exception Port**:

   - Click on the **Exception Ports** icon on the **Database** component in the canvas toolbar to toggle the **Exception Port** visibility.

5. **Finish Configuration**.

#### Step 3: Connect the Exception Port

1. **Add a **Display** Component**:

   - To handle and display error messages.

2. **Draw a Route from the Exception Port**:

   - From the **Exception Port** of the **Database** component to the **Input Port** of the **Display** component.

#### Step 4: Run and Test the Event Process

1. **Save and Run** the event process.

2. **Test Using Postman**:

   - **Endpoint URL**: Obtain from the **REST Stub** component.
   - **Send a Request**.

3. **Observe the Behavior**:

   - The **Database** component will attempt to connect and fail.
   - It will retry according to the settings.
   - After retries are exhausted, the error will be emitted through the **Exception Port**.

4. **View the Error Messages**:

   - Open the **Display** component to see the error messages.
   - You should see messages indicating connection failures.

#### Step 5: Check the Logs

1. **View Logs**:

   - Right-click on the **Database** component and select **View Logs**.
   - Observe the timestamps and error messages corresponding to each retry attempt.

### Best Practices

- **Configure Appropriate Retry Counts**:

  - Set a reasonable number of retries to avoid excessive delays or system overload.

- **Set Retry Intervals**:

  - Use retry intervals to prevent immediate repeated attempts, giving time for recovery.

- **Use Exception Ports**:

  - Enable and handle exception ports to manage errors gracefully.

- **Avoid Infinite Retries**:

  - Do not set retries to infinite; it can cause queues to pile up and impact system performance.

- **Monitor and Log**:

  - Keep logs of retry attempts for troubleshooting and monitoring.

### Conclusion

You have successfully learned how to implement a retry mechanism in Fiorano components to enhance the reliability of your integration workflows. By configuring retries for connection errors and request processing errors, you can handle transient issues gracefully and improve the resilience of your applications.

---

## 8.4 Exporting and Importing Event Processes

### Introduction

In a collaborative development environment or when moving applications between environments (e.g., from development to production), you may need to **export** and **import** event processes. Fiorano provides straightforward mechanisms to perform these actions.

### Objectives

- Learn how to export event processes from Fiorano Studio.
- Understand how to import event processes into Fiorano Studio.
- Apply best practices for managing event processes.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and the Event Process Repository.
- Completion of previous modules is recommended.

### Step-by-Step Guide

#### Step 1: Export an Event Process

1. **Open Fiorano Studio (eStudio)**.

2. **Navigate to the Event Process Repository**:

   - Locate the event process you want to export.

3. **Export the Event Process**:

   - Right-click on the event process.
   - Select **Export**.
   - Choose the destination directory where you want to save the exported file (e.g., your desktop).
   - Click **Save**.

4. **Verify the Exported Files**:

   - Navigate to the destination directory.
   - You should see the exported event process files, including configuration files and any dependencies.

#### Step 2: Import an Event Process

1. **Right-Click on the Event Process Repository**:

   - In the **Event Process** pane, right-click and select **Import**.

2. **Select the Event Process to Import**:

   - Browse to the location of the exported event process file (e.g., `SampleEventProcess.zip`).
   - Click **Open**.

3. **Handle Duplicate Event Processes**:

   - If the event process already exists in the repository, you will be prompted.
   - Choose to **Overwrite** if you want to replace the existing event process.

4. **Verify the Imported Event Process**:

   - The imported event process should now appear in the **Event Process Repository**.
   - Open it to ensure all configurations are intact.

### Best Practices

- **Version Control**:

  - Consider using version control systems for event processes to track changes and manage versions.

- **Dependencies**:

  - Ensure that any dependencies (e.g., custom components, configurations) are also exported and imported if needed.

- **Naming Conventions**:

  - Use clear naming conventions to avoid confusion when importing event processes.

- **Environment Configuration**:

  - Be aware of environment-specific configurations that may need adjustment after importing.

- **Testing After Import**:

  - Always test the imported event process to confirm it functions as expected in the new environment.

### Conclusion

You have successfully learned how to export and import event processes in Fiorano. These capabilities facilitate collaboration among developers and ease the movement of applications between different environments, enhancing productivity and maintainability.

---

## 8.5 Extended Services in Fiorano

### Introduction

In Fiorano, each component in an event process runs in its own Java Virtual Machine (JVM) by default. While this provides isolation and flexibility, there are scenarios where you might prefer a **memory and CPU optimized** solution with all components running within the same JVM. **Extended Services** allow you to achieve this by consolidating components into a single JVM, improving performance and reducing resource overhead.

### Objectives

- Understand what extended services are and when to use them.
- Learn how to create an extended service in Fiorano.
- Deploy extended services across server groups for scalability and disaster recovery.
- Apply best practices for using extended services.

### Prerequisites

- Familiarity with Fiorano Studio (eStudio) and creating event processes.
- Understanding of JVM and resource allocation.
- Completion of previous modules is recommended.

### Scenario Overview

We will create an **Extended Service** that:

1. **Consolidates multiple components** into a single JVM.
2. **Deploys the extended service** across multiple server groups.
3. **Runs** the extended service and observes its behavior.
4. **Manages** the extended service deployment.

This scenario demonstrates how to optimize resource utilization using extended services.

### Step-by-Step Guide

#### Step 1: Create an Extended Service

1. **Open Fiorano Studio (eStudio)**.

2. **Add an Extended Service**:

   - In the **Event Process Repository**, right-click on **Extended Services**.
   - Select **Add Extended Service**.
   - **Name**: Enter `DemoExtendedService`.
   - Click **Finish**.

3. **Design the Extended Service**:

   - The extended service canvas opens.
   - **Add Components** as you would in a regular event process.
     - For example, add a **REST Stub** to expose a service.
     - Configure it as needed.

4. **Connect Components**:

   - Design your workflow within the extended service.
   - Add any routes, mappings, and configurations as required.

#### Step 2: Configure Server Groups

1. **Configure Peer Server Groups**:

   - In the **Peer Server Repository**, right-click and select **Configure Peer Server Groups**.
   - **Add Group**: Create new server groups as needed (e.g., `Group1`, `Group2`).
   - **Assign Peer Servers** to the groups.
     - Peer servers can be running on different nodes (machines).

2. **Create a Resource Configuration**:

   - In the extended service canvas, click on **Resource**.
   - **Add Configuration**:
     - **Name**: Enter `ServerGroupConfig`.
     - **Type**: Select **Peer Server Groups Configuration**.
     - **Specify Groups**: Enter the names of the server groups (e.g., `Group1,Group2`).
     - Click **Finish**.

3. **Assign Resource Configuration**:

   - **Click on the Canvas Background** (ensure no component is selected).
   - In the **Properties** pane, go to the **Deployment** tab.
   - **Resource Configuration**: Select `ServerGroupConfig`.

#### Step 3: Run the Extended Service

1. **Save and Run** the extended service.

2. **Deployment View**:

   - Right-click on the extended service and select **Open Deployment View**.
   - **Select Peer Servers** in the groups to see where the extended service is running.
   - You can manage and monitor the extended service from the deployment view.

#### Step 4: Manage the Extended Service

1. **Adding Breakpoints**:

   - In the **Deployment View**, you can add breakpoints for debugging.
   - Breakpoints can only be added in the deployment view for extended services.

2. **Monitoring**:

   - Monitor resource utilization and performance.
   - Use Fiorano's monitoring tools to observe the behavior of the extended service.

### Best Practices

- **Resource Optimization**:

  - Use extended services when you need to optimize memory and CPU usage.
  - Be aware that running all components in a single JVM reduces isolation.

- **Scalability**:

  - Deploy extended services across multiple server groups for scalability and high availability.

- **Management**:

  - Use the **Control Plane Dashboard** or **FES Dashboard** for managing extended services.

- **Testing**:

  - Thoroughly test extended services to ensure they behave as expected when consolidated.

- **Documentation**:

  - Document your extended services and configurations for maintainability.

### Conclusion

You have successfully learned how to create and deploy extended services in Fiorano. By consolidating components into a single JVM, you can optimize resource utilization and improve performance, especially in scenarios where memory and CPU optimization is critical.

---

## 8.6 FES Dashboard Part 1: Runtime Management

### Introduction

The **FES (Fiorano Enterprise Server) Dashboard** provides a web-based interface for managing servers, applications, services, and endpoints in your Fiorano environment. It offers runtime management capabilities, allowing you to monitor and control various aspects of your deployment from a central location.

### Objectives

- Learn how to access and navigate the FES Dashboard.
- Understand how to manage servers, event processes, extended services, and endpoints.
- Utilize the dashboard for runtime monitoring and management tasks.
- Apply best practices for using the FES Dashboard.

### Prerequisites

- Access to the Fiorano Enterprise Server and appropriate credentials.
- Understanding of Fiorano components and deployments.
- Completion of previous modules is recommended.

### Step-by-Step Guide

#### Step 1: Access the FES Dashboard

1. **Open a Web Browser**.

2. **Navigate to the FES Dashboard URL**:

   - **URL**: `http://<server_address>:1980`
     - Replace `<server_address>` with the actual server IP or hostname.
     - Use `https` and port `1984` if SSL is enabled.

3. **Log In**:

   - Enter your **Username** and **Password**.
   - Click **Login**.

#### Step 2: Explore the Dashboard Interface

1. **Home Page**:

   - The dashboard displays an overview of the Fiorano environment.

2. **Servers**:

   - **Enterprise Server**:
     - View details of the FES, including status, logs, and configurations.
     - Start, stop, or restart the server as needed.
   - **Peer Servers**:
     - View and manage peer servers.
     - Perform actions like stopping or restarting servers.
     - Access logs and thread dumps.

3. **Event Processes**:

   - **View Deployed Processes**:
     - See a list of event processes deployed in the environment.
   - **Manage Processes**:
     - Start, stop, or redeploy event processes.
     - Download event process artifacts.
   - **Process Details**:
     - View components within an event process.
     - Monitor resource usage and performance metrics.
     - Access logs specific to components.

4. **Extended Services**:

   - View and manage extended services.
   - Start or stop extended services.
   - Monitor runtime behavior.

5. **Endpoints**:

   - **View Endpoints**:
     - See all active endpoints (e.g., REST services, SOAP services).
   - **Test Endpoints**:
     - Invoke services directly from the dashboard for testing.
   - **Manage Endpoints**:
     - View details, configurations, and perform actions.

6. **Named Configurations**:

   - Manage named configurations like transformations and message filters.
   - Import, export, or version control configurations.

#### Step 3: Perform Runtime Management Tasks

1. **Starting and Stopping Servers**:

   - Navigate to **Servers** > **Peer Servers**.
   - Select a server and choose **Start**, **Stop**, or **Restart**.

2. **Managing Event Processes**:

   - Navigate to **Event Processes**.
   - Select an event process.
   - Use **Start**, **Stop**, or **Redeploy** to manage the process.

3. **Monitoring Logs**:

   - Access logs for servers and components directly from the dashboard.
   - View **Output Logs** and **Error Logs** to troubleshoot issues.

4. **Testing Services**:

   - Navigate to **Endpoints**.
   - Select a service and click **Test**.
   - Provide input parameters and invoke the service.
   - View responses to verify functionality.

### Best Practices

- **Secure Access**:

  - Ensure that access to the FES Dashboard is secured with proper authentication and authorization.

- **Monitor Regularly**:

  - Use the dashboard for regular monitoring of servers and applications to detect issues early.

- **Centralized Management**:

  - Leverage the dashboard's capabilities to manage deployments efficiently from a single interface.

- **Log Management**:

  - Utilize the logging features to keep track of system behavior and troubleshoot problems.

- **Testing and Validation**:

  - Use the endpoint testing tools to validate services after deployment.

### Conclusion

You have successfully learned how to use the FES Dashboard for runtime management of your Fiorano environment. The dashboard provides powerful tools for monitoring, managing, and troubleshooting servers, applications, and services, enhancing operational efficiency.

---

## 8.7 FES Dashboard Part 2: Document Tracking

### Introduction

**Document Tracking** in Fiorano allows you to trace and monitor the flow of messages (events) through your event processes. By enabling document tracking, you can capture detailed information about each event, including payloads, headers, properties, and processing times.

This is particularly useful for troubleshooting, auditing, and analyzing system behavior.

### Objectives

- Understand how to enable and configure document tracking.
- Learn how to use the FES Dashboard to view and analyze tracked documents.
- Utilize document tracking for troubleshooting and performance analysis.
- Apply best practices for using document tracking in Fiorano.

### Prerequisites

- Access to the Fiorano Enterprise Server and appropriate credentials.
- Familiarity with Fiorano event processes and components.
- Completion of previous modules is recommended.

### Step-by-Step Guide

#### Step 1: Configure Document Tracking

1. **Access Document Tracking Settings**:

   - In the FES Dashboard, navigate to **Document Tracking**.

2. **Select Database Configuration**:

   - Fiorano supports various databases for storing document tracking data (e.g., **H2**, **PostgreSQL**, **MS SQL**).
   - For development purposes, **H2** is sufficient.
   - For production environments, use a robust database like **PostgreSQL**.

3. **Configure Database Connection**:

   - **Driver Class**: Ensure the appropriate JDBC driver is specified.
   - **Database URL**: Provide the connection string to your database.
   - **Credentials**: Enter the database username and password.
   - **Test Connection**: Verify the connection settings.

4. **Save Configuration**.

#### Step 2: Enable Document Tracking in an Event Process

1. **Open the Event Process in eStudio**.

2. **Enable Tracking on Ports**:

   - For each component where you want to track events:
     - **Select the Output Port**.
     - In the **Properties** pane, go to the **Workflow** tab.
     - Set **Workflow Item** to **Workflow** (green icon) to indicate processing continues.
   - On the **Response Port** of the initiating component (e.g., **REST Stub**):
     - Set **Workflow Item** to **Workflow End** (red icon) to indicate processing ends.

3. **Save and Run** the event process.

#### Step 3: Trigger Events and Capture Data

1. **Invoke the Service**:

   - Use a tool like **Postman** to send requests to your service.
   - Perform several transactions to generate events.

#### Step 4: View and Analyze Tracked Documents

1. **Access Document Tracking in the Dashboard**:

   - Navigate to **Document Tracking** > **Documents**.

2. **Select Application and Time Frame**:

   - Choose the event process (application) you are interested in.
   - Select the time frame (e.g., **Last Hour**).

3. **View Events**:

   - A list of events (transactions) will be displayed.
   - Each event shows details like **Status**, **Start Time**, and **Execution Time**.

4. **Analyze Event Details**:

   - Click on an event to view detailed information.
   - **Components**: See how the event flowed through each component.
     - View processing times for each component.
   - **Data**:
     - **Payload**: View the message content at each stage.
     - **Properties**: View message headers and properties.
     - **Application Context**: View context variables.
   - **Reinject Messages**:
     - If needed, you can reinject messages for troubleshooting.

#### Step 5: Verify Data in the Database (Optional)

- Access the database you configured for document tracking.
- Query tables like `InstEventHistory` and `InstEventHeader` to view raw tracking data.

### Best Practices

- **Selective Tracking**:

  - Enable tracking only on necessary ports to minimize performance impact.

- **Secure Sensitive Data**:

  - Be cautious when tracking messages containing sensitive information.
  - Implement data masking or avoid tracking sensitive payloads.

- **Monitor Performance**:

  - Be aware that enabling document tracking can affect system performance.
  - Use in development or troubleshooting scenarios as needed.

- **Data Retention Policy**:

  - Implement a data retention policy to manage the size of the tracking database.

- **Use for Auditing**:

  - Leverage document tracking for auditing transactions and compliance purposes.

### Conclusion

You have successfully learned how to configure and use document tracking in Fiorano using the FES Dashboard. Document tracking provides valuable insights into the flow and processing of messages within your event processes, aiding in troubleshooting, auditing, and performance analysis.

---

## 8.8 Installing and Uninstalling Patches

### Introduction

Periodically, Fiorano may release patches to address issues or provide enhancements. Properly installing and uninstalling patches is crucial for maintaining the stability and security of your Fiorano environment.

### Objectives

- Learn how to install patches in Fiorano.
- Understand how to uninstall patches if necessary.
- Follow best practices for patch management.

### Prerequisites

- Access to the Fiorano server file system.
- Appropriate permissions to modify installation files.
- Completion of previous modules is recommended.

### Step-by-Step Guide

#### Step 1: Obtain the Patch

1. **Receive the Patch File**:

   - Fiorano provides patches as ZIP files.
   - **Example**: `Patch_1.zip`.

2. **Extract the Patch Contents**:

   - Unzip the patch file to a temporary location.
   - Review the **README** file for specific instructions.

#### Step 2: Install the Patch

1. **Copy the Patch to the Patches Directory**:

   - Navigate to the Fiorano installation directory.
   - **Path**: `<Fiorano_Home>/esb/server/patches/`.
   - Copy the extracted patch folder into the `patches` directory.

2. **Stop the Server**:

   - It is recommended to stop the Fiorano Enterprise Server before applying patches.
   - Use the **FES Dashboard** or command line to stop the server.

3. **Apply the Patch**:

   - Open a command prompt or terminal window.
   - Navigate to the `bin` directory.
     - **Path**: `<Fiorano_Home>/esb/server/bin/`.
   - Run the patch script:
     - **Windows**: `patch.bat`
     - **Linux/Unix**: `./patch.sh`
   - Follow the prompts:
     - Select **P** for **Patch**.
     - Choose the patch number corresponding to the patch you want to install.
     - Wait for the installation to complete successfully.

4. **Verify Installation**:

   - The patch directory should now be moved to `installed_patches`.
   - Check logs to confirm successful installation.

5. **Restart the Server**:

   - Start the Fiorano Enterprise Server.
   - Ensure all services are running properly.

#### Step 3: Uninstall the Patch (If Necessary)

1. **Stop the Server**.

2. **Run the Patch Script**:

   - Navigate to the `bin` directory.
   - Run the patch script:
     - **Windows**: `patch.bat`
     - **Linux/Unix**: `./patch.sh`
   - Follow the prompts:
     - Select **U** for **Unpatch**.
     - Choose the patch number corresponding to the patch you want to uninstall.

3. **Verify Uninstallation**:

   - The patch should be removed from `installed_patches` and appear back in `patches`.

4. **Restart the Server**.

#### Step 4: Post-Patch Activities

- **Testing**:

  - Verify that all event processes and services are functioning as expected.

- **Backup**:

  - Maintain backups before and after patching.

### Best Practices

- **Read Instructions Carefully**:

  - Always read the **README** or installation notes that come with the patch.

- **Test in a Non-Production Environment**:

  - Apply patches in a test environment before deploying to production.

- **Backup**:

  - Backup your Fiorano environment before applying patches.

- **Server Restart**:

  - Plan for server downtime when applying patches.

- **Patch Management**:

  - Keep a record of installed patches and corresponding changes.

### Conclusion

You have successfully learned how to install and uninstall patches in Fiorano. Proper patch management ensures that your environment benefits from the latest fixes and improvements while maintaining stability and reliability.

---

## Module 8 Summary

In Module 8, we covered:

- **Named Configurations**: How to use message filters and route transformations to enhance reusability.
- **Retry Mechanism**: Configuring retries for reliability in your event processes.
- **Exporting and Importing**: Techniques for sharing and deploying event processes.
- **Extended Services**: Optimizing resource usage by consolidating components.
- **FES Dashboard**: Utilizing runtime management and document tracking features.
- **Patch Management**: Installing and uninstalling patches to keep your environment up-to-date.

By mastering these advanced features, you can create more efficient, reliable, and maintainable integration solutions using Fiorano.

---

I'm sorry for the confusion earlier. Module 10 was included in error. Let's continue with **Module 9** as per your instructions.

---

# Module 9: API Management, Security, Debugging, and Analytics

Welcome to Module 9 of the Fiorano Product Training series. In this module, we will focus on **API Management** in Fiorano, covering how to create API projects, apply security policies, utilize debugging tools, and leverage analytics for monitoring and optimization.

---

## Overview of Module 9

- **9.1**: API Management - Creating a Product and Assigning a Client to Consume
- **9.2**: Creating API Projects Part 1 - REST/HTTP Services
- **9.3**: Creating API Projects Part 2 - Using Swagger/OpenAPI Specifications
- **9.4**: Security - Verifying API Key Policy
- **9.5**: Security - Implementing OAuth 2.0 Authentication
- **9.6**: Debugger and Live Tracing in API Management
- **9.7**: Runtime Manager, Logs, and Analytics

---

## 9.1: API Management - Creating a Product and Assigning a Client to Consume

### Introduction

In this session, we will explore how to create API products in Fiorano's API Management module and how to assign clients to consume these products. API Management allows organizations to securely expose, manage, and monitor APIs, enabling controlled access for internal or external clients.

### Objectives

- Understand the concept of API Products in Fiorano.
- Learn how to start the API Management Server and Gateway Server.
- Create an API Product and assign it to a client for consumption.
- Configure organizations and clients within API Management.
- Apply best practices for managing API subscriptions and access.

### Prerequisites

- **Fiorano Studio (eStudio)** installed and connected to the Enterprise Server.
- **Cassandra Database** running (as required by Fiorano API Management).
- Basic understanding of Fiorano components and deployment.
- Completion of previous modules is recommended.

---

### Step-by-Step Guide

#### Step 1: Start the API Management Server and Gateway Server

1. **Navigate to the Server Directory**:

   - For example: `C:\Fiorano\13.0\esb\server\bin`.

2. **Start the Management Server**:

   - Open a command prompt in the directory.
   - Run the command:

     ```
     server.bat -mode ams -profile server1
     ```

     - Replace `server1` with your profile name if different.

3. **Start the Gateway Server**:

   - Open another command prompt in the same directory.
   - Run the command:

     ```
     server.bat -mode ags -profile server1
     ```

4. **Verify Server Startup**:

   - Check the console output to ensure both servers have started successfully.
   - Look for messages indicating successful initialization and connections.

5. **Ensure Cassandra Database is Running**:

   - Fiorano API Management uses Cassandra as the data store.
   - Start Cassandra as a standalone service or as a Windows service (`DataStax Cassandra Community Edition` for development purposes).

#### Step 2: Access the API Management Dashboard

1. **Open a Web Browser**:

   - Navigate to `http://localhost:1980` (or `https://localhost:1984` if SSL is enabled).

2. **Login**:

   - Use your credentials to log into the Fiorano API Management Dashboard.

3. **Dashboard Overview**:

   - The dashboard displays an overview of API projects, products, clients, and subscriptions.
   - These configurations are stored in the Cassandra database connected to the management server.

#### Step 3: Create an API Product

1. **Navigate to Products**:

   - In the dashboard, go to **Products**.

2. **Create a New Product**:

   - Click on **Add Product**.
   - **Name**: Enter `TrainingProduct` or a suitable name.
   - **Access**: Choose **Public** or **Private** depending on your requirements.
   - **Workflow**: Select **Automatic** for automatic approval of subscriptions, or **Manual** for administrator approval.

3. **Assign API Projects to the Product**:

   - Initially, no API projects are associated.
   - You can add API projects after creating them.

4. **Save the Product**:

   - Click **Save**.
   - A success message will confirm the creation of the product.

#### Step 4: Create an Organization and Assign the Product

1. **Navigate to Organizations**:

   - Go to **Organizations** in the dashboard.

2. **Add an Organization**:

   - Click on **Add Organization**.
   - **Name**: Enter `TrainingOrg`.
   - **Email**: Provide an email address (e.g., `training@example.com`).
   - **Administrator**: Assign an administrator for the organization.
   - **Select Products**:
     - Choose the product (`TrainingProduct`) you created earlier to assign it to the organization.

3. **Save the Organization**:

   - Click **Save**.

#### Step 5: Create a Client Subscription

1. **Navigate to Client Subscriptions**:

   - Go to **Clients** > **Client Subscriptions**.

2. **Add a Client Subscription**:

   - Click on **Add Client Subscription**.
   - **Name**: Enter `TrainingSubscription`.
   - **Client**: Select or create a client (e.g., `training@example.com`).
   - **Application Name**: Provide an application name if desired.
   - **Subscribed Products**:
     - Select `TrainingProduct`.

3. **Save the Subscription**:

   - Click **Save**.
   - A consumer key and secret will be generated for the client.

#### Step 6: Understanding the Workflow

- **API Projects**: Represent individual APIs or services you want to expose.
- **Products**: Bundles of API projects grouped for subscription.
- **Organizations**: Groups or companies that can have access to products.
- **Clients**: Individual users or applications consuming the APIs.
- **Subscriptions**: Assigning products to clients, providing them with access credentials.

---

### Best Practices

- **Access Control**:

  - Use **Private** access for sensitive APIs.
  - Implement **Manual** workflows for subscription approvals when needed.

- **Organization Management**:

  - Organize clients into organizations for better management.
  - Assign administrators to organizations for delegated control.

- **Security**:

  - Keep consumer keys and secrets secure.
  - Implement appropriate authentication mechanisms (covered in later sessions).

- **Documentation**:

  - Provide clear documentation for API products to assist clients in consumption.

---

### Conclusion

You have successfully learned how to create an API product in Fiorano API Management and assign clients to consume it. Understanding the structure of API projects, products, organizations, and client subscriptions is crucial for effective API management, secure access control, and efficient client onboarding.

In the next sessions, we will explore how to create API projects using REST services and Swagger/OpenAPI specifications, as well as how to implement security policies.

---

## 9.2: Create API Project Part 1 - REST/HTTP Services

### Introduction

In this session, we will learn how to create an API project in Fiorano API Management using a REST or HTTP service as the target. This allows you to expose existing services through the API Gateway with added policies and security measures.

### Objectives

- Understand how to create an API project based on a REST/HTTP service.
- Configure the target service URL and context paths.
- Deploy the API project to the Gateway Server.
- Test the exposed API endpoint.

### Prerequisites

- An existing REST or HTTP service to use as the target (can be an event process you've previously created).
- Access to Fiorano API Management Dashboard.
- Completion of previous sessions is recommended.

---

### Step-by-Step Guide

#### Step 1: Create a New API Project

1. **Navigate to API Projects**:

   - In the API Management Dashboard, go to **API Projects**.

2. **Add a New API Project**:

   - Click on **Add Project**.
   - Choose **Create API from REST/HTTP Service**.

3. **Configure the Basic Settings**:

   - **Project Name**: Enter `CalculatorAPI` or a suitable name.
   - **Version**: Keep the default or set as needed.
   - **Method**: Select the HTTP method used by the target service (e.g., **POST**).
   - **Context Path**: Define the path under which the API will be exposed (e.g., `/api/calculator`).
   - **Proxy Method**: Set it to the same as the target method.

4. **Configure the Target Service URL**:

   - **Target Service URL**: Enter the full URL of the target service.
     - For example, `http://localhost:1856/calculate` (replace with your actual service URL).
   - **Resource Path**: Include any additional path if necessary.

#### Step 2: Configure Authentication (Optional)

- For this session, we'll leave authentication as **None**.
- Authentication policies can be added later through **Policy Configuration**.

#### Step 3: Attach the API Project to a Product

1. **Select the Product**:

   - In the **Products** selection, choose `TrainingProduct` or the product you created earlier.

2. **Finish Configuration**:

   - Click **Next** and then **Finish**.

#### Step 4: Save and Deploy the API Project

1. **Save the Project**:

   - Click **Save** to save your configurations.

2. **Deploy the Project**:

   - Click **Deploy** to deploy the API project to the Gateway Server.
   - A success message will confirm the deployment.

#### Step 5: Retrieve the Gateway Endpoint

1. **Access the API Project Overview**:

   - Open the **CalculatorAPI** project.
   - Navigate to the **Overview** tab.

2. **Retrieve Deployed URLs**:

   - Find the **Deployed URLs** section.
   - You will see both **HTTP** and **HTTPS** endpoints provided by the Gateway Server.
   - The endpoints will include the context path you specified.

#### Step 6: Test the Exposed API Endpoint

1. **Use a REST Client**:

   - Open **Postman** or any REST client.

2. **Configure the Request**:

   - **URL**: Use the deployed HTTP endpoint from the Gateway.
   - **Method**: **POST** (or as configured).
   - **Headers**:
     - `Content-Type`: `application/json`
   - **Body**:
     - Provide a JSON payload as required by your target service.
       ```json
       {
         "elementA": 10,
         "elementB": 5,
         "operation": "add"
       }
       ```

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - You should receive a response from the target service through the Gateway.
   - The response will be returned to the client.

#### Step 7: Verify Backend Service Invocation

- **Check the Backend Service**:

  - Ensure that the request is reaching the backend service.
  - Use breakpoints or logs in the backend event process to monitor requests.

---

### Best Practices

- **SSL Configuration**:

  - Configure SSL settings for the Gateway Server to securely expose HTTPS endpoints.
  - Update the Keystore and Truststore as needed.

- **Endpoint Security**:

  - Implement security policies to protect your APIs (covered in later sessions).

- **Documentation**:

  - Document your API endpoints, methods, and expected input/output.

- **Testing**:

  - Thoroughly test the API endpoints to ensure they function correctly.

---

### Conclusion

You have successfully created an API project in Fiorano API Management using a REST/HTTP service. By deploying the project to the Gateway Server, you have exposed the service securely and can now manage it using Fiorano's API Management capabilities.

In the next session, we will learn how to create API projects using Swagger or OpenAPI specifications for more complex APIs.

---

## 9.3: Creating API Projects Part 2 - Using Swagger/OpenAPI Specifications

### Introduction

In this session, we will learn how to create an API project in Fiorano API Management by importing a **Swagger** or **OpenAPI** specification file. This method is useful when you have an existing API definition and want to expose it through Fiorano's API Gateway.

### Objectives

- Understand how to create an API project by importing OpenAPI or Swagger specifications.
- Configure the project settings and context paths.
- Deploy the API project to the Gateway Server.
- Test the exposed API endpoints.

### Prerequisites

- An OpenAPI (YAML or JSON) or Swagger specification file for the API.
- Access to Fiorano API Management Dashboard.
- Completion of previous sessions is recommended.

---

### Step-by-Step Guide

#### Step 1: Prepare the OpenAPI/Swagger Specification File

- Ensure you have a valid OpenAPI or Swagger specification file.
- The file should define all the API endpoints, methods, parameters, and responses.
- For this example, we'll use a file named `petstore.yaml`.

#### Step 2: Create a New API Project by Importing the Specification

1. **Navigate to API Projects**:

   - In the API Management Dashboard, go to **API Projects**.

2. **Add a New API Project**:

   - Click on **Add Project**.
   - Choose **Import from OpenAPI file**.

3. **Upload the Specification File**:

   - Click on **Browse** and select the `petstore.yaml` file.
   - Click **Open** to upload the file.

4. **Parse the OpenAPI Specification**:

   - Click on **Parse OpenAPI**.
   - The API Management tool will parse the file and display the available resources.

5. **Select Resources**:

   - Review the listed resources.
   - By default, all resources are selected.
   - You can deselect any resources you do not wish to include.

6. **Configure Project Details**:

   - **Project Name**: Enter `PetStoreAPI` or a suitable name.
   - **Context Path**: Define the context path under which the API will be exposed (e.g., `/api/petstore`).

#### Step 3: Configure Authentication (Optional)

- For this session, we'll leave authentication as **None**.
- Authentication policies can be added later through **Policy Configuration**.

#### Step 4: Attach the API Project to a Product

1. **Select the Product**:

   - In the **Products** selection, choose `TrainingProduct` or the product you created earlier.

2. **Finish Configuration**:

   - Click **Next** and then **Finish**.

#### Step 5: Save and Deploy the API Project

1. **Save the Project**:

   - Click **Save** to save your configurations.

2. **Deploy the Project**:

   - Click **Deploy** to deploy the API project to the Gateway Server.
   - A success message will confirm the deployment.

#### Step 6: Retrieve the Gateway Endpoints

1. **Access the API Project Overview**:

   - Open the **PetStoreAPI** project.
   - Navigate to the **Overview** tab.

2. **Retrieve Deployed URLs**:

   - The resources defined in the specification are now available through the Gateway.
   - Each resource will have its own endpoint URL.

#### Step 7: Test the Exposed API Endpoints

1. **Use a REST Client**:

   - Open **Postman** or any REST client.

2. **Configure a Request**:

   - **URL**: Use one of the deployed endpoints, such as `http://<gateway_address>/api/petstore/v1/pet`.
   - **Method**: Set the HTTP method as defined (e.g., **GET**, **POST**).
   - **Headers**:
     - `Content-Type`: As required by the API (e.g., `application/json`).
   - **Body**:
     - Provide the necessary payload if the method requires it.

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - You should receive a response from the backend service through the Gateway.
   - The response will be returned to the client.

---

### Best Practices

- **Review Imported Definitions**:

  - After importing, review the resources and methods for accuracy.
  - Update any configurations as necessary.

- **Attach Policies at Resource Level**:

  - Apply security or transformation policies at the resource level if required.

- **Documentation**:

  - Ensure the API documentation is clear and accurate for clients.

- **Testing**:

  - Test each endpoint thoroughly to ensure correct functionality.

---

### Conclusion

You have successfully created an API project in Fiorano API Management by importing a Swagger/OpenAPI specification. This method simplifies the process of exposing complex APIs and ensures consistency with existing API definitions.

In the next sessions, we will learn how to implement security policies like API key verification and OAuth 2.0 authentication to protect your APIs.

---

## 9.4: Security - Verifying API Key Policy

### Introduction

In this session, we will learn how to secure your APIs by implementing an **API Key Verification** policy. This policy ensures that only authorized clients with valid API keys can access your API endpoints.

### Objectives

- Understand how to create and configure an API Key Verification policy.
- Attach the policy to an API project resource.
- Test the API with and without a valid API key.

### Prerequisites

- An API project deployed on the Gateway Server (e.g., `CalculatorAPI`).
- A client subscription with a consumer key (API key).
- Completion of previous sessions is recommended.

---

### Step-by-Step Guide

#### Step 1: Create an API Key Verification Policy

1. **Navigate to Policies**:

   - In the API Management Dashboard, go to **Policies**.

2. **Create a New Policy**:

   - Click on **Add Policy**.
   - **Policy Name**: Enter `VerifyAPIKeyPolicy`.
   - **Policy Type**: Select **Security Policies**.

3. **Select the Policy**:

   - Choose **Verify API Key** from the list of available policies.

4. **Configure the Policy**:

   - **Select Environments**: Choose **Development** (or as appropriate).
   - **API Key Location**: Specify where the API key will be expected.
     - **Header**: Typically, API keys are sent in the request header.
     - **Header Name**: Enter `APIKey` or the desired header field name.

5. **Save the Policy**:

   - Click **Finish** to save the policy.

#### Step 2: Attach the Policy to an API Project Resource

1. **Navigate to the API Project**:

   - Open your API project (e.g., `CalculatorAPI`).

2. **Go to Resources**:

   - Navigate to the **Resources** tab.
   - Select the resource you want to secure (e.g., the default resource).

3. **Edit Policy Configuration**:

   - In the **Policy Configuration** section, click on **Edit**.

4. **Attach the Policy**:

   - Remove any existing security policies (e.g., **None**).
   - Add the **VerifyAPIKeyPolicy** before the **Proxy Request** in the policy chain.

5. **Save and Deploy the API Project**:

   - Click **Save** to save the changes.
   - Click **Deploy** to redeploy the API project with the new policy.

#### Step 3: Test the API without the API Key

1. **Use a REST Client**:

   - Open **Postman** or any REST client.

2. **Configure the Request**:

   - **URL**: Use the API endpoint from the Gateway.
   - **Method**: **POST** (or as configured).
   - **Headers**:
     - `Content-Type`: `application/json`
     - Do **not** include the `APIKey` header.

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - You should receive a **401 Unauthorized** response.
   - The error message may indicate that the API key is missing or invalid.

#### Step 4: Test the API with a Valid API Key

1. **Retrieve the Consumer Key**:

   - Navigate to **Clients** > **Client Subscriptions**.
   - Find the client subscription associated with your API product.
   - Copy the **Consumer Key** (this is the API key).

2. **Configure the Request with API Key**:

   - **Headers**:
     - Add a header named `APIKey` (or the header name you configured).
     - Set the value to the consumer key you copied.

3. **Send the Request**:

   - Click **Send**.

4. **Verify the Response**:

   - You should receive a **200 OK** response.
   - The API should process the request successfully.

#### Step 5: Test with an Invalid API Key

1. **Configure the Request with an Invalid API Key**:

   - **Headers**:
     - Set the `APIKey` header to an incorrect value.

2. **Send the Request**:

   - Click **Send**.

3. **Verify the Response**:

   - You should receive a **401 Unauthorized** response.

---

### Best Practices

- **Secure API Keys**:

  - Ensure that API keys are kept confidential.
  - Rotate API keys periodically.

- **Error Handling**:

  - Provide meaningful error messages without revealing sensitive information.

- **Monitoring**:

  - Monitor API key usage to detect unauthorized access attempts.

---

### Conclusion

You have successfully implemented an API Key Verification policy to secure your APIs. By requiring clients to provide a valid API key, you can control access to your services and protect them from unauthorized use.

In the next session, we will learn how to implement OAuth 2.0 authentication for enhanced security.

---

## 9.5: Security - Implementing OAuth 2.0 Authentication

### Introduction

In this session, we will learn how to secure your APIs using **OAuth 2.0** authentication in Fiorano API Management. OAuth 2.0 is an industry-standard protocol for authorization that enables clients to access server resources on behalf of a resource owner. Implementing OAuth 2.0 provides enhanced security by issuing access tokens to clients, which are then used to access protected resources.

### Objectives

- Understand how to create and configure an **OAuth Verify Access Token** policy.
- Set up an OAuth 2.0 token endpoint for generating access tokens.
- Attach the OAuth policy to an API project resource.
- Test the API by obtaining and using an access token.
- Apply best practices for OAuth 2.0 authentication.

### Prerequisites

- An API project deployed on the Gateway Server (e.g., `CalculatorAPI`).
- A client subscription with a consumer key and secret.
- Completion of previous sessions is recommended.

---

### Step-by-Step Guide

#### Step 1: Create an OAuth Verify Access Token Policy

1. **Navigate to Policies**:

   - In the API Management Dashboard, go to **Policies**.

2. **Create a New Policy**:

   - Click on **Add Policy**.
   - **Policy Name**: Enter `OAuthVerifyAccessTokenPolicy`.
   - **Policy Type**: Select **Security Policies**.

3. **Select the Policy**:

   - Choose **OAuth Verify Access Token** from the list of available policies.

4. **Configure the Policy**:

   - **Select Environments**: Choose **Development** (or as appropriate).
   - **Access Token Location**: Specify where the access token will be expected.
     - **Header**: Typically, access tokens are sent in the `Authorization` header.
   - **Header Name**: Enter `Authorization`.

5. **Save the Policy**:

   - Click **Finish** to save the policy.

#### Step 2: Attach the OAuth Policy to an API Project Resource

1. **Navigate to the API Project**:

   - Open your API project (e.g., `CalculatorAPI`).

2. **Go to Resources**:

   - Navigate to the **Resources** tab.
   - Select the resource you want to secure (e.g., the default resource).

3. **Edit Policy Configuration**:

   - In the **Policy Configuration** section, click on **Edit**.

4. **Attach the OAuth Policy**:

   - Remove any existing security policies (e.g., **VerifyAPIKeyPolicy**) if present.
     - Uncheck the policies you want to remove.
   - Add the **OAuthVerifyAccessTokenPolicy** before the **Proxy Request** in the policy chain.
     - Check the **OAuthVerifyAccessTokenPolicy** to add it.

5. **Save and Deploy the API Project**:

   - Click **Save** to save the changes.
   - Click **Deploy** to redeploy the API project with the new policy.

#### Step 3: Set Up an OAuth 2.0 Token Endpoint

1. **Create an OAuth 2.0 Token Endpoint**:

   - In the API Management Dashboard, navigate to **OAuth2 Token Endpoints**.
   - Click on **Add Token Endpoint**.

2. **Configure the Token Endpoint**:

   - **Name**: Enter `TrainingGenerateToken`.
   - **Version**: Keep the default or set as needed.
   - **Proxy Context Path**: Define the path under which the token endpoint will be exposed (e.g., `/generateToken`).
   - **Proxy Method**: **POST** (default).
   - **Access Token Expiry Time**: Set the desired expiry time for access tokens (e.g., `300` seconds for 5 minutes).
   - **Refresh Token Expiry Time**: Set the expiry time for refresh tokens if used.

3. **Attach the Token Endpoint to a Product**:

   - In the **Products** selection, choose `TrainingProduct` or the product you created earlier.

4. **Save and Deploy the Token Endpoint**:

   - Click **Save** to save the configurations.
   - Click **Deploy** to deploy the token endpoint to the Gateway Server.

#### Step 4: Obtain an Access Token Using Client Credentials

1. **Retrieve Client Credentials**:

   - Navigate to **Clients** > **Client Subscriptions**.
   - Find the client subscription associated with your API product.
   - Copy the **Consumer Key** and **Consumer Secret**.
     - **Consumer Key**: Acts as the `client_id`.
     - **Consumer Secret**: Acts as the `client_secret`.

2. **Use a REST Client**:

   - Open **Postman** or any REST client.

3. **Configure the Request to Obtain Access Token**:

   - **URL**: Use the token endpoint URL from the Gateway (e.g., `http://<gateway_address>/generateToken`).
   - **Method**: **POST**.
   - **Headers**:
     - `Content-Type`: `application/x-www-form-urlencoded`
   - **Body**:
     - Select **x-www-form-urlencoded**.
     - Add the following key-value pairs:
       - `grant_type`: `client_credentials`
       - `client_id`: `<Consumer Key>`
       - `client_secret`: `<Consumer Secret>`

4. **Send the Request**:

   - Click **Send**.

5. **Verify the Response**:

   - You should receive a response containing the `access_token` and other token information.
     ```json
     {
       "access_token": "your_access_token_value",
       "token_type": "Bearer",
       "expires_in": 300
     }
     ```

#### Step 5: Test the API Using the Access Token

1. **Configure the API Request with Access Token**:

   - **URL**: Use the API endpoint from the Gateway.
   - **Method**: **POST** (or as configured).
   - **Headers**:
     - `Content-Type`: `application/json`
     - `Authorization`: `Bearer your_access_token_value`
       - Replace `your_access_token_value` with the actual access token obtained.
   - **Body**:
     - Provide the necessary JSON payload as required by your API.

2. **Send the Request**:

   - Click **Send**.

3. **Verify the Response**:

   - You should receive a **200 OK** response.
   - The API should process the request successfully.

#### Step 6: Test the API with an Invalid or Expired Access Token

1. **Tamper with the Access Token**:

   - Modify the access token to simulate an invalid token.
     - For example, change one character in the token.

2. **Send the Request**:

   - Click **Send**.

3. **Verify the Response**:

   - You should receive a **401 Unauthorized** response.
   - The error message may indicate that the token is invalid or expired.

---

### Best Practices

- **Understand OAuth 2.0 Flows**:

  - Familiarize yourself with OAuth 2.0 grant types (e.g., client credentials, authorization code).
  - Choose the appropriate flow based on your use case.

- **Secure Client Credentials**:

  - Ensure that client IDs and secrets are kept confidential.
  - Do not expose them in client-side code or logs.

- **Token Expiry and Refresh**:

  - Set appropriate expiry times for access and refresh tokens.
  - Implement token refresh mechanisms if needed.

- **Error Handling**:

  - Provide meaningful error messages without exposing sensitive information.
  - Handle token expiration and invalid token scenarios gracefully.

- **Compliance and Security**:

  - Adhere to OAuth 2.0 security considerations.
  - Implement HTTPS to secure communications.

- **Monitoring**:

  - Monitor token issuance and usage to detect anomalies.
  - Log authentication attempts for auditing purposes.

---

### Conclusion

You have successfully implemented OAuth 2.0 authentication in Fiorano API Management to secure your APIs. By issuing access tokens and verifying them on each request, you provide a robust security mechanism that controls access to your services.

Understanding OAuth 2.0 and its grant types is essential for implementing secure and efficient authorization workflows. Fiorano API Management simplifies this process by providing built-in policies and token endpoints that integrate seamlessly with your API projects.

In the next session, we will explore the debugger and live tracing features in API Management, which aid in troubleshooting and monitoring your APIs.

---

## 9.6: Debugger and Live Tracing in API Management

### Introduction

In this session, we will explore the **Debugger** and **Live Tracing** features in Fiorano API Management. These tools are essential for testing, troubleshooting, and monitoring your APIs. The Debugger allows you to simulate API requests and observe how they are processed through the API Gateway, while Live Tracing lets you monitor real-time traffic and inspect messages as they pass through the system.

### Objectives

- Understand how to use the **Debugger** to test API workflows interactively.
- Learn how to enable and utilize **Live Tracing** for real-time monitoring.
- Identify and troubleshoot issues within API policies and processing stages.
- Apply best practices for debugging and monitoring APIs in Fiorano.

### Prerequisites

- An API project deployed on the Gateway Server with security policies applied (e.g., OAuth 2.0 authentication).
- Access to Fiorano API Management Dashboard.
- Completion of previous sessions is recommended.

---

### Step-by-Step Guide

#### Step 1: Accessing the Debugger

1. **Navigate to the API Project**:

   - Open your API project (e.g., `CalculatorAPI`) in the API Management Dashboard.

2. **Open the Debugger**:

   - Click on the **Debugger** tab within the API project.
   - You will see a visual representation of the API workflow, including the request flow from the client to the target service and back.

#### Step 2: Using the Debugger to Test API Requests

1. **Configure the Debugger Session**:

   - On the left panel, you can configure the request details.
   - **Headers**: Add required headers such as `Content-Type` and `Authorization`.
     - For example:
       - `Content-Type`: `application/json`
       - `Authorization`: `Bearer your_access_token_value`
   - **Body**: Provide the request payload in JSON format.
     - For example:
       ```json
       {
         "elementA": 12,
         "elementB": 8,
         "operation": "add"
       }
       ```

2. **Set Breakpoints (Optional)**:

   - You can set breakpoints at different stages of the API workflow to pause execution and inspect the state.
   - Click on the breakpoint icon next to stages like **Verify Access Token**, **Proxy Request**, or **Target Endpoint**.

3. **Start Debugging**:

   - Click **Start Debugging** or **Send** to initiate the request.
   - The debugger will execute the API call, pausing at any breakpoints you've set.

4. **Inspect the Flow**:

   - At each breakpoint, you can inspect:
     - **Request and Response Payloads**: View the message content.
     - **Headers and Properties**: Examine HTTP headers and other properties.
     - **Variables**: Check any variables used in policies or transformations.

5. **Continue Execution**:

   - After inspecting, click **Resume** or **Continue** to proceed to the next stage or until the request completes.

6. **Analyze the Results**:

   - Upon completion, review the final response returned to the client.
   - Check for any errors or unexpected behavior in the processing stages.

#### Step 3: Enabling Live Tracing

1. **Navigate to Live Tracing**:

   - Within the API Management Dashboard, go to **Live Tracing**.

2. **Configure Live Tracing Session**:

   - **Select API Project**: Choose the API project you want to monitor (e.g., `CalculatorAPI`).
   - **Duration**: Set the duration for the live tracing session (e.g., 5 minutes).
   - **Filters** (Optional):
     - You can set filters based on client IDs, operation names, or other criteria to focus on specific traffic.

3. **Start Live Tracing**:

   - Click **Start Trace** to begin the live tracing session.
   - A session ID will be generated, and real-time data will start streaming in as requests are processed.

#### Step 4: Using Live Tracing to Monitor API Traffic

1. **Monitor Incoming Requests**:

   - As API requests are received and processed, they will appear in the Live Tracing interface.
   - Each entry includes details like timestamp, client, operation, and status code.

2. **Inspect Individual Transactions**:

   - Click on a transaction to view detailed information.
   - **Stages**:
     - View the flow of the request through various stages (e.g., security policies, transformations).
   - **Data**:
     - Examine request and response payloads at each stage.
     - Check headers, properties, and any modifications made during processing.

3. **Analyze Errors and Issues**:

   - Identify any requests that resulted in errors or unexpected responses.
   - Inspect at which stage the error occurred and what caused it.

4. **Stop the Live Tracing Session**:

   - After you've gathered the necessary information, click **Stop Trace** to end the session.

#### Step 5: Troubleshooting Common Issues

1. **Authentication Failures**:

   - **Symptom**: Requests receive a `401 Unauthorized` response.
   - **Resolution**:
     - Verify that the access token or API key is valid and not expired.
     - Ensure that the `Authorization` header is correctly set.
     - Check the OAuth policy configuration for any issues.

2. **Policy Misconfigurations**:

   - **Symptom**: Requests fail at a specific policy stage.
   - **Resolution**:
     - Use the debugger to inspect the policy processing.
     - Confirm that policy sequences are correctly ordered.
     - Adjust policy settings as needed.

3. **Data Transformation Errors**:

   - **Symptom**: Incorrect data is sent to the backend or returned to the client.
   - **Resolution**:
     - Inspect payloads during transformations.
     - Ensure that mappings and transformations are correctly defined.

4. **Target Service Issues**:

   - **Symptom**: The backend service is not responding or returns errors.
   - **Resolution**:
     - Check the availability and health of the backend service.
     - Verify that the target URL and endpoints are correct.

---

### Best Practices

- **Use Breakpoints Strategically**:

  - Set breakpoints at stages where issues are likely to occur for efficient debugging.

- **Minimize Live Tracing Duration**:

  - Limit the duration of live tracing sessions to what is necessary to reduce performance impact.

- **Secure Sensitive Information**:

  - Be cautious when inspecting payloads containing sensitive data.
  - Ensure compliance with data protection policies.

- **Document Findings**:

  - Keep records of issues discovered and resolutions for future reference.

- **Collaborate with Team Members**:

  - Share insights and troubleshooting steps with your team to enhance collective knowledge.

---

### Conclusion

You have learned how to utilize the **Debugger** and **Live Tracing** features in Fiorano API Management to test and monitor your APIs. These tools are invaluable for identifying and resolving issues, ensuring that your APIs function correctly and efficiently.

By incorporating debugging and live tracing into your development and maintenance workflows, you can enhance the reliability and performance of your integration solutions.

---

## 9.7: Runtime Manager, Logs, and Analytics

### Introduction

In this session, we will explore how to utilize the **Runtime Manager**, access and interpret **Logs**, and configure **Analytics** within Fiorano API Management. These tools are crucial for maintaining the health of your APIs, optimizing performance, and gaining insights into API usage. Effective monitoring and logging allow you to proactively address issues, ensure smooth operation, and make data-driven decisions.

### Objectives

- **Runtime Manager**:
  - Understand how to monitor and manage the API Gateway and Management Servers.
  - Start, stop, and restart servers as needed.
  - View server resource usage and performance metrics.
- **Logs**:
  - Learn how to access and interpret various logs for troubleshooting and auditing.
  - View API Management Server logs and Gateway Server logs.
- **Analytics**:
  - Configure analytics to collect and visualize API usage data.
  - Understand how to generate reports and set up notifications.
- Apply best practices for monitoring and optimizing API performance.

### Prerequisites

- **Fiorano API Management Servers**:
  - Management Server and Gateway Server are running.
  - You have administrative access to the servers.
- **Cassandra Database**:
  - Ensure that the Cassandra database is running and connected to the API Management Servers.
- **Previous Configurations**:
  - Completion of previous sessions, including deploying API projects and implementing security policies.

---

### Step-by-Step Guide

#### Step 1: Accessing the Runtime Manager

1. **Open the API Management Dashboard**:

   - Navigate to `http://localhost:1980` (or the appropriate URL for your server).

2. **Log In**:

   - Use your administrative credentials to log into the dashboard.

3. **Navigate to Server Status**:

   - In the dashboard, click on the **Administration** tab.
   - Under **Runtime**, select **Server Status**.

4. **View Server Details**:

   - **Management Server**:
     - Check the status, CPU usage, memory usage, and uptime.
     - Perform actions like **Start**, **Stop**, or **Restart** if necessary.
   - **Gateway Server**:
     - Similarly, view the details for the Gateway Server.
     - Monitor resource utilization and health indicators.

5. **Server Groups** (if applicable):

   - If you have multiple server groups (e.g., Development, Production), you can switch between them.
   - Manage servers within each group according to your deployment topology.

6. **Monitoring Resource Usage**:
   - Use the graphs and charts provided to monitor CPU and memory usage over time.
   - Identify any spikes or anomalies that may require attention.

#### Step 2: Viewing and Analyzing Logs

1. **Navigate to the Logs Section**:

   - In the **Administration** tab, select **Logs**.

2. **Select Log Types**:

   - **Management Server Logs**:
     - **API Out Logs**: View logs related to standard operations of the API Management Server.
     - **API Error Logs**: View error logs for troubleshooting issues.
   - **Gateway Server Logs**:
     - **API Gateway Out Logs**: View standard output logs for the Gateway Server.
     - **API Gateway Error Logs**: View errors specific to the Gateway operations.

3. **Analyze Logs**:

   - **Error Identification**:
     - Look for error messages, exceptions, or stack traces that indicate problems.
     - Common issues include failed connections, authentication errors, or policy violations.
   - **Output Logs**:
     - Review logs for normal operation messages.
     - Useful for auditing and verifying that services are running as expected.

4. **Filtering and Searching Logs**:

   - Use the provided filters to narrow down logs by date, severity level, or keywords.
   - This helps in quickly locating relevant information.

5. **Downloading Logs**:
   - You can download logs for offline analysis.
   - Click on **Download** to save the log files to your local machine.

#### Step 3: Configuring Analytics

1. **Navigate to Analytics DB Configuration**:

   - In the **Administration** tab, select **Analytics DB Configuration**.

2. **Configure the Analytics Database**:

   - **Database Type**: Choose **PostgreSQL**, **H2**, or another supported database.
   - **Driver Class**: Ensure the correct JDBC driver is specified for your database.
   - **Database URL**: Provide the connection string to your analytics database.
     - Example: `jdbc:postgresql://localhost:5432/fiorano_analytics`
   - **Username**: Enter the database username.
   - **Password**: Enter the database password.

3. **Test the Connection**:

   - Click on **Test Connection** to verify that the API Management Server can connect to the database.
   - If the connection is successful, proceed to the next step.
   - If it fails, check your database credentials and network connectivity.

4. **Save the Configuration**:

   - Click on **Save** to apply the analytics database settings.

5. **Enable Data Collection**:
   - Ensure that analytics data collection is enabled for your API projects to begin gathering usage statistics.

#### Step 4: Accessing and Using Analytics

1. **Navigate to the Analytics Section**:

   - In the dashboard, select the **Analytics** tab.

2. **Viewing Usage Metrics**:

   - **Usage**:
     - View total API calls over a selected time period (day, week, month).
     - Analyze trends and peak usage times.
   - **Filter Data**:
     - Use filters to view analytics for specific API projects, products, or clients.

3. **Monitoring Performance Metrics**:

   - **Performance**:
     - Examine average processing times and maximum processing times for API requests.
     - Identify any performance bottlenecks or slow endpoints.

4. **Analyzing Bandwidth Consumption**:

   - **Bandwidth**:
     - Assess the amount of data transferred in requests and responses.
     - Helps in understanding network load and optimizing data transfer.

5. **Inspecting Status Codes**:

   - **Status Codes**:
     - View the distribution of HTTP status codes returned by your APIs.
     - High rates of 4xx or 5xx errors may indicate issues that need attention.

6. **Generating Reports**:

   - **Report Configuration**:
     - Set up customized reports based on the metrics you are interested in.
     - Schedule reports to be generated and sent via email at specified intervals.

7. **Setting Up Notifications** (Optional):
   - **Notifications**:
     - Configure alerts for specific events, such as when error rates exceed a threshold.
     - Requires setting up email server configurations in the **Email Configuration** section.

#### Step 5: Managing API Projects and Endpoints

1. **Navigate to API Projects**:

   - Review the list of deployed API projects.

2. **Perform Actions on API Projects**:

   - **Start**, **Stop**, or **Redeploy** projects as needed.
   - Access **Runtime Details** for each project to monitor their operation.

3. **Endpoint Management**:
   - **Endpoints**:
     - View all active endpoints exposed by your API projects.
     - Test endpoints directly from the dashboard using the **Test** feature.

---

### Best Practices

- **Regular Monitoring**:

  - Consistently check server statuses, logs, and analytics to stay aware of your system's health.
  - Set up regular reports and notifications to automate monitoring tasks.

- **Proactive Maintenance**:

  - Address errors and performance issues promptly before they impact users.
  - Use analytics data to make informed decisions about scaling and resource allocation.

- **Security and Compliance**:

  - Ensure that logs and analytics data are secured and comply with data protection regulations.
  - Limit access to sensitive information to authorized personnel only.

- **Documentation**:

  - Document any changes made to server configurations, deployments, and policy updates.
  - Maintain an audit trail through logs and change management processes.

- **Resource Optimization**:
  - Monitor resource utilization and optimize configurations for better performance.
  - Consider scaling resources or optimizing code if consistent bottlenecks are identified.

---

### Conclusion

You have learned how to use the **Runtime Manager** to monitor and manage your Fiorano API Management servers, access and analyze **Logs** for troubleshooting and auditing, and configure **Analytics** to gain insights into API usage and performance.

Effective use of these tools is essential for maintaining high availability, ensuring security, and optimizing the performance of your APIs. By regularly monitoring and analyzing data, you can proactively address issues, improve user satisfaction, and make informed decisions to align your API services with business objectives.


