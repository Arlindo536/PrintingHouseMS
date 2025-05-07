# 🧍‍♂️ Singleton Pattern Implementation

## Overview
The Singleton Pattern restricts the instantiation of a class to a single instance and provides global access to that instance. In PrintingHouseMS, this pattern ensures only one instance of the notification manager exists in the system.

## Problem Solved
- **Resource Control**: Prevents multiple instances of components that should only exist once
- **Global Access**: Provides a single access point to critical system services
- **State Consistency**: Ensures consistent state across the application

## Implementation in PrintingHouseMS

### Structure

```
NotificationManager
├─ -instance: NotificationManager (static)
├─ -NotificationManager() (private constructor)
└─ +getInstance(): NotificationManager (static)
```

### Key Components

1. **Private Constructor**: Prevents external instantiation
2. **Static Instance**: Single shared instance stored as a private static field
3. **Static Access Method**: Public method to access the instance
4. **Thread-Safety Mechanism**: Ensures thread-safe instantiation if needed

## Benefits in Our System

- **Centralized Notification Management**: All system notifications go through a single channel
- **Resource Optimization**: Prevents redundant instances for services requiring system-wide coordination
- **Configuration Consistency**: Ensures consistent notification settings across the application
- **Reduced Memory Footprint**: Single instance of resource-intensive managers

## Usage Example Scenario

When a notification needs to be sent:
1. Different parts of the system call `NotificationManager.getInstance()`
2. All calls receive the same instance of the NotificationManager
3. The NotificationManager tracks notification types, user preferences, and delivery status
4. System-wide notification policies are consistently applied
5. Notification frequency and bundling are managed centrally to prevent notification fatigue

## Singleton Applied To

1. **NotificationManager**: Controls all system notifications
2. **ConnectionPool**: Manages database connections
3. **ConfigurationManager**: Handles system-wide configuration settings
4. **LoggingService**: Provides centralized logging capabilities

## Diagram
![Singleton Pattern Implementation](../Diagrams/SingletonPattern.svg)