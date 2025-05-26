# 📢 Observer Pattern Implementation for Notifications

## Overview
The Observer Pattern establishes a one-to-many dependency between objects, so that when one object (the subject) changes state, all its dependents (observers) are notified automatically. In PrintingHouseMS, this pattern is used to implement the notification system where customers and staff receive updates about order status changes.

## Problem Solved
- **Decoupling**: Separates order status changes from notification delivery
- **Multiple Recipients**: Allows various stakeholders to receive updates without tight coupling
- **Flexible Notification Methods**: Enables different notification types (email, SMS, in-app) without modifying the core order processing

## Implementation in PrintingHouseMS

### Structure

```
NotificationSubject
├─ registerObserver(observer)
├─ removeObserver(observer)
└─ notifyObservers(event)
```

### Key Components

1. **NotificationSubject Interface**: Defines methods to register, remove, and notify observers
2. **OrderStatusSubject**: Concrete subject that tracks order status changes and notifies observers
3. **NotificationObserver Interface**: Defines the update method for observers
4. **Concrete Observers**: EmailNotifier, SMSNotifier, InAppNotifier, etc.

## Benefits in Our System

- **Loose Coupling**: Order processing code doesn't need to know about notification details
- **Extensibility**: New notification methods can be added without changing existing code
- **Configurability**: Users can subscribe to specific notifications based on preferences
- **Consistency**: All observers receive the same notification data

## Usage Example Scenario

When an order status changes from "In Production" to "Quality Control":
1. Production staff updates order status in the system
2. `OrderStatusSubject` detects the status change
3. `OrderStatusSubject` calls `notifyObservers()` with the status change event
4. Each registered observer (EmailNotifier, SMSNotifier, etc.) receives the notification
5. Each observer formats and delivers the notification via its specific channel
6. Customer and relevant staff members receive notifications through their preferred channels

## Diagram
![Observer Pattern for Notifications](../Diagrams/ObserverPattern.svg)