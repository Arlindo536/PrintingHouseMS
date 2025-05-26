
# 🔄 PrintingHouseMS State Diagrams 🔄



## 🌟 Overview

This document explains the state diagrams created for the PrintingHouseMS system. State diagrams show the different states that an entity can exist in and the transitions between these states, illustrating how entities change over time in response to events.

## 🔍 Why State Diagrams?

- 📊 Visualize the **complete lifecycle** of business entities
- 🔀 Show **valid transitions** between different states 
- 🛡️ Help enforce **business rules** for state changes
- 📝 Document **event triggers** that cause state transitions
- 🚫 Prevent **invalid operations** on entities in certain states

## 📑 Included Diagrams

### 1️⃣ Order State Diagram 📦

![Order State Diagram](../Diagrams/OrderStateDiagram.svg)

**Key States:**
- **Draft**: Initial order being configured
- **Submitted**: Order submitted by customer but not yet processed
- **Pending Payment**: Order validated and awaiting payment
- **Confirmed**: Payment received and order approved
- **In Production**: Order currently being manufactured
- **Quality Control**: Finished books undergoing quality checks
- **Ready for Shipping**: Production completed and ready for delivery
- **Shipped**: Order in transit to customer
- **Delivered**: Order successfully delivered to customer
- **Cancelled**: Order terminated prematurely (can occur from multiple states)

**Business Rules:**
- Orders can be cancelled from draft, submitted, or pending payment states
- Quality control failures return the order to production
- Orders must go through all states sequentially except for cancellations
- Only orders that have passed quality control can proceed to shipping

### 2️⃣ Production Job State Diagram 🏭

![Production Job State Diagram](../Diagrams/ProductionJobStateDiagram.svg)

**Key States:**
- **Created**: Production job initially created from an order
- **Assigned**: Staff members assigned to the production job
- **Prepress**: Manuscript formatting and preparation
- **Printing**: Physical printing of book pages
- **Binding**: Binding printed pages into book format
- **Quality Check**: Inspection of finished books
- **Completed**: Production successfully finished
- **On Hold**: Production temporarily paused
- **Rejected**: Failed quality check
- **Cancelled**: Production terminated prematurely

**Business Rules:**
- Production can be placed on hold from any active state
- Jobs on hold can resume to appropriate states
- Failed quality checks move to rejected state
- Rejected jobs can be reworked by returning to printing state
- Production can be cancelled from any state
- Production stages must follow the specific sequence

## 💡 Implementation Notes

- Each state corresponds to a specific status value in the database
- Transitions are implemented as operations in the service layer
- State changes trigger appropriate notifications
- Historical state changes are logged for auditing
- Guards ensure transitions follow business rules
- Invalid state transitions throw exceptions

## 🔄 How These Diagrams Connect

These two state diagrams represent complementary aspects of the PrintingHouseMS system:

1. **Order State Diagram** tracks the customer-facing lifecycle, focusing on the business process from order to delivery

2. **Production Job State Diagram** tracks the internal manufacturing process, focusing on the technical steps needed to produce the books

An order in the "In Production" state connects to a production job that moves through the various production states (prepress, printing, binding). When the production job reaches "Completed", it triggers the order to move to "Quality Control".

Together, these diagrams help ensure that both customer expectations and production requirements are properly managed throughout the printing process.

---
