# Dropshipping-Inventory-Order-Orchestrator_software_engineering
Software Engineering Lab Assignments
# PES University – Software Engineering Laboratory

## Student Information

| Details               | Information                                       |
| --------------------- | ------------------------------------------------- |
| **Name**              | Pavithra G C                                      |
| **SRN**               | PES2UG24CS346                                     |
| **Section**           | 5F                                                |
| **Problem Statement** | #38 – Dropshipping Inventory & Order Orchestrator |
| **Domain**            | Retail, E-Commerce & Finance                      |

---

# Project Title

## Dropshipping Inventory & Order Orchestrator

The project focuses on designing a software system that manages customer orders, supplier inventory, multi-vendor order fulfillment, shipment tracking, and notifications.

The Software Engineering Laboratory work is organized into three labs:

1. **Lab 1 – Requirements Engineering & UML Use-Case Modelling**
2. **Lab 2 – Agile Backlog Creation & Sprint Simulation in Jira**
3. **Lab 3 – Component Modelling & Architectural Pattern Selection**

---

# Lab 1 – Requirements Engineering & UML Use-Case Modelling

## Objective

The objective of Lab 1 is to identify and document the requirements of the Dropshipping Inventory & Order Orchestrator and represent the system using UML Use-Case Modelling.

---

## Problem Statement

**Problem Statement #38: Dropshipping Inventory & Order Orchestrator**

The system receives customer orders from an e-commerce platform and coordinates inventory verification, multi-supplier order processing, supplier fulfillment, shipment tracking, and notifications.

---

## Functional Requirements

### FR-001 – Receive Order Webhook

The system shall receive and process inbound order webhooks from platforms such as Shopify or WooCommerce.

**Priority:** High

**Acceptance Criteria:**

* Pass: When a valid order webhook is received, the system extracts the order ID, customer address, product SKU, and quantity.
* Fail: The order data is not processed or required details are missing.

**Rationale:**

Receiving customer orders is the core function of the system.

---

### FR-002 – Verify Inventory

The system shall verify the real-time stock availability of each ordered product using the corresponding supplier API.

**Priority:** High

**Acceptance Criteria:**

* Pass: The system checks stock availability for every ordered SKU before sending a purchase order.
* Fail: A purchase order is sent without verifying stock.

**Rationale:**

This prevents orders from being placed for unavailable products.

---

### FR-003 – Split Multi-Vendor Order

The system shall split an order containing products from multiple suppliers into separate supplier-specific purchase orders.

**Priority:** High

**Acceptance Criteria:**

* Pass: An order containing products from three different suppliers generates three separate purchase orders.
* Fail: Products from different suppliers are incorrectly combined into one purchase order.

**Rationale:**

This supports correct multi-vendor dropshipping fulfillment.

---

### FR-004 – Dispatch Supplier Purchase Order

The system shall send supplier-specific purchase orders containing product details, quantities, and customer delivery information.

**Priority:** High

**Acceptance Criteria:**

* Pass: A purchase order is successfully sent to the correct supplier with the correct products, quantities, and delivery address.
* Fail: The purchase order is missing required information or is sent to the wrong supplier.

**Rationale:**

This automates the fulfillment process.

---

### FR-005 – Store Supplier Tracking Number

The system shall store supplier tracking numbers and associate them with the corresponding customer order.

**Priority:** Medium

**Acceptance Criteria:**

* Pass: When a supplier provides a tracking number, it is stored and linked to the correct customer order.
* Fail: The tracking number is missing or linked to an incorrect order.

**Rationale:**

This enables shipment tracking and order monitoring.

---

# Lab 1 – Non-Functional Requirements

## NFR-001 – Webhook Response Performance

The system shall acknowledge receipt of inbound webhooks with HTTP 200 within 200 milliseconds.

**Priority:** High

**Purpose:**

This prevents webhook retry storms and ensures fast processing.

---

## NFR-002 – Reliability During Supplier Failure

The system shall retain order data and log failures when a supplier API or network connection is temporarily unavailable.

**Priority:** High

**Purpose:**

This ensures reliability and prevents loss of customer orders.

---

# Lab 1 – Actors

## 1. E-Commerce Platform

The E-Commerce Platform sends customer order webhooks to the system.

Examples include:

* Shopify
* WooCommerce

---

## 2. Supplier Partner

The Supplier Partner:

* Provides inventory information.
* Receives purchase orders.
* Sends tracking information.

---

## 3. E-Store Owner

The E-Store Owner:

* Monitors orders.
* Receives failure notifications.
* Monitors fulfillment status.

---

# Lab 1 – Use Cases

The major use cases identified are:

| ID    | Use Case                         |
| ----- | -------------------------------- |
| UC-01 | Receive Order Webhook            |
| UC-02 | Verify Inventory                 |
| UC-03 | Split Multi-Vendor Order         |
| UC-04 | Dispatch Supplier Purchase Order |
| UC-05 | Track Shipment                   |
| UC-06 | Notify E-Store Owner             |

---

# Lab 1 – Main Use Case

## UC-01 – Process Incoming Customer Order

### Primary Actor

E-Commerce Platform (Shopify/WooCommerce)

### Supporting Actors

* Supplier Partner
* E-Store Owner

### Preconditions

1. The E-Commerce Platform is connected to the system.
2. The webhook endpoint is configured and available.
3. Supplier API details are available.
4. Product SKUs are mapped to their corresponding suppliers.

### Postconditions

1. Inventory availability is verified.
2. The order is split into supplier-specific orders if multiple suppliers are involved.
3. Purchase orders are dispatched for available products.
4. Order and fulfillment information is stored.
5. The E-Store Owner is notified if a fulfillment problem occurs.

---

# Lab 1 – Main Success Scenario

1. The E-Commerce Platform sends a customer order webhook.
2. The system receives and validates the webhook.
3. The system acknowledges the webhook with HTTP 200.
4. The system extracts the order ID, customer delivery address, product SKUs, and quantities.
5. The system identifies the supplier associated with each ordered product.
6. The system requests current inventory information from the corresponding Supplier Partner.
7. The system verifies that the required quantity is available.
8. The system groups products according to their suppliers.
9. If multiple suppliers are involved, the system splits the order into separate supplier-specific purchase orders.
10. The system generates a purchase order for each supplier.
11. The system sends the purchase orders to the respective Supplier Partners.
12. The system stores supplier order references and updates the order status to **Processing**.
13. When tracking information is received, the system associates the tracking number with the corresponding customer order.
14. The use case ends successfully.

---

# Lab 1 – Alternate Flow

## Product Out of Stock

If insufficient inventory is detected:

1. The Supplier Partner reports that one or more requested products are out of stock.
2. The system does not dispatch a purchase order for the unavailable product.
3. The system records the order ID, product SKU, supplier, and failure reason.
4. The system marks the affected item as **Out of Stock**.
5. The system triggers the **Notify E-Store Owner** use case.
6. The E-Store Owner receives a notification containing the relevant order and failure details.
7. The affected order is marked as **Requires Attention**.
8. The use case ends.

---

# Lab 2 – Agile Backlog Creation & Sprint Simulation in Jira

## Objective

Lab 2 focuses on creating an Agile product backlog and simulating sprint execution using Jira.

The backlog contains:

* Epics
* User stories
* Story points
* Priorities
* Sprint assignments

The sprint simulation demonstrates how planned work moves through the development workflow.

---

# Lab 2 – Project Information

**Project Title:**

Dropshipping Inventory & Order Orchestrator

**Student:** Pavithra G C

**SRN:** PES2UG24CS346

**Section:** 5F

---

# Lab 2 – Jira Deliverables

The following deliverables were created/planned for the Agile exercise:

1. Jira backlog with Epics and User Stories.
2. Story point assignment.
3. Sprint list.
4. Sprint board showing active sprint view.
5. Burndown chart.
6. Sprint reflection.

---

# Lab 2 – Epics

The Jira backlog contains six epics:

* **Epic 1**
* **Epic 2**
* **Epic 3**
* **Epic 4**
* **Epic 5**
* **Epic 6**

The detailed epic names and user stories are maintained in the Jira backlog and supporting Lab 2 submission files.

---

# Lab 2 – Story Points

Story points were assigned to user stories based on their complexity and estimated effort.

Higher-complexity tasks were given higher story points.

For example, splitting a multi-vendor order requires more processing and coordination than a simple order-related task.

---

# Lab 2 – Sprint Simulation

The sprint board was used to simulate Agile development.

User stories were moved through stages such as:

**To Do → In Progress → Done**

Important stories were selected for the sprint based on their priority and importance to the system.

---

# Lab 2 – Burndown Chart

The burndown chart was used to monitor the remaining story points during the sprint.

It helped show:

* Remaining work.
* Completed work.
* Team capacity.
* Whether the sprint workload was realistic.

---

# Lab 2 – Reflection

## 1. Did your estimations reflect the actual effort?

Yes, the estimations mostly reflected the actual effort.

Stories with higher complexity, such as splitting multi-vendor orders, were given more story points.

The story points helped estimate the effort required for each task.

---

## 2. Was your backlog well-prioritized?

Yes, the backlog was well-prioritized.

Important functions such as receiving orders, checking supplier stock, and splitting orders were given higher priority because they are essential for the system.

---

## 3. How did your simulated sprint align with your plan?

The simulated sprint followed the plan.

Important user stories were selected for the sprint and moved from:

**To Do → In Progress → Done**

This helped demonstrate how planned work is completed during a sprint.

---

## 4. What insights did the burndown chart give about your team's capacity?

The burndown chart helped understand how quickly the team could complete the selected dropshipping tasks during the sprint.

It showed the remaining story points as stories were completed.

This helped determine whether the team had selected a realistic amount of work for the one-week sprint.

---

# Lab 3 – Component Modelling & Architectural Pattern Selection

## Objective

Lab 3 focuses on evaluating architectural styles and selecting an appropriate architecture for the Dropshipping Inventory & Order Orchestrator.

The lab includes:

* Architecture comparison.
* Component identification.
* UML Component Diagram.
* Interface identification.
* Architectural justification.
* Security analysis.
* Performance analysis.

---

# Lab 3 – Selected Architecture

## Microservices Architecture

Microservices Architecture was selected for the system.

The system contains several independent business functions:

* Order Management
* Payment Processing
* Inventory Management
* Supplier Management
* Notifications

These functions can be implemented as separate services.

---

# Lab 3 – Components

The five major components are:

1. **Order Manager Component**
2. **Payment Service Component**
3. **Inventory Management Component**
4. **Supplier Management Component**
5. **Notification Service Component**

---

# Lab 3 – Component Responsibilities

## Order Manager Component

Responsible for:

* Managing orders.
* Tracking order status.
* Coordinating payment.
* Checking inventory.
* Coordinating supplier fulfillment.
* Requesting notifications.

---

## Payment Service Component

Responsible for:

* Processing payments.
* Verifying payment status.
* Returning payment results.

---

## Inventory Management Component

Responsible for:

* Checking product availability.
* Maintaining stock information.
* Updating inventory.
* Synchronizing inventory information.

---

## Supplier Management Component

Responsible for:

* Managing supplier information.
* Communicating with suppliers.
* Sending fulfillment requests.
* Receiving supplier updates.
* Supporting inventory synchronization.

---

## Notification Service Component

Responsible for:

* Sending order notifications.
* Sending status updates.
* Informing the E-Store Owner about fulfillment problems.

---

# Lab 3 – Interfaces

| No. | Source               | Destination          | Interface                     |
| --- | -------------------- | -------------------- | ----------------------------- |
| 1   | Order Manager        | Payment Service      | Payment Processing API        |
| 2   | Order Manager        | Inventory Management | Inventory Check API           |
| 3   | Inventory Management | Supplier Management  | Inventory Synchronization API |
| 4   | Order Manager        | Supplier Management  | Order Fulfillment API         |
| 5   | Order Manager        | Notification Service | Notification API              |

**Communication Technology:** REST API / HTTPS

---

# Lab 3 – Architecture Comparison

## Layered Architecture

### Advantages

* Simple to understand.
* Clear separation of responsibilities.

### Limitations

* Can introduce performance overhead.
* Individual functions are harder to scale independently.

### Suitability

Possible, but not the best choice for this scenario.

---

## Client-Server Architecture

### Advantages

* Simple structure.
* Centralized management.

### Limitations

* Central server can become a bottleneck.
* Server failure can affect the system.
* Limited independent scalability.

### Suitability

Possible, but less suitable for this system.

---

## Microservices Architecture

### Advantages

* Independent scaling.
* Fault isolation.
* Independent development.
* Independent deployment.
* Better service-level separation.

### Limitations

* More complex to manage.
* Network communication can introduce latency.
* Data consistency between services can be challenging.

### Suitability

**Most suitable architecture for this scenario.**

---

# Lab 3 – Architectural Decision

## Reason 1 – Independent Scaling

Individual services can be scaled according to their workload.

For example, Order Manager can be scaled during periods of high order traffic without scaling every other service.

---

## Reason 2 – Fault Isolation

If one service fails, other services can continue working.

For example, a failure in the Notification Service should not necessarily stop order processing.

---

# Lab 3 – Security Advantage

The Payment Service can be isolated from other services and protected using authentication and authorization.

Secure communication such as HTTPS can also be used between services.

---

# Lab 3 – Performance Advantage

Frequently used services can be independently scaled.

For example:

* Order Manager can be scaled during high order traffic.
* Inventory Management can be scaled when inventory requests increase.

This helps the system handle a high number of requests efficiently.

---

# Overall Project Architecture

The overall system can be viewed as:

**E-Commerce Platform**

↓

**Order Manager**

↓

**Inventory Management**

↓

**Supplier Management**

↓

**Supplier Partner**

The Order Manager also communicates with:

* **Payment Service**
* **Notification Service**

---

# Technologies / Tools Used

The laboratory activities involve software engineering modelling and Agile tools such as:

* UML
* Jira
* GitHub
* REST API concepts
* HTTPS
* Microservices Architecture

---

# Conclusion

The three Software Engineering Laboratory activities provide a complete development workflow for the **Dropshipping Inventory & Order Orchestrator**.

### Lab 1

Focused on:

**Requirements → Actors → Use Cases → UML Use-Case Modelling**

### Lab 2

Focused on:

**Product Backlog → Epics → User Stories → Story Points → Sprint → Burndown Chart**

### Lab 3

Focused on:

**Architecture Analysis → Components → Interfaces → UML Component Diagram → Architectural Justification**

Together, these labs demonstrate the process of analyzing requirements, planning Agile development, and designing the software architecture of the Dropshipping Inventory & Order Orchestrator.
