# 🏭 Factory Pattern Implementation for Book Configurations

## Overview
The Factory Pattern provides an interface for creating different types of book configurations without exposing the instantiation logic to the client. This pattern centralizes book creation, making the system more maintainable as new book types are added.

## Problem Solved
- **Complexity Management**: Book configurations have many variations (hardcover, paperback, specialty bindings)
- **Encapsulation**: Creation logic is separated from business logic
- **Extensibility**: New book types can be added without changing existing client code

## Implementation in PrintingHouseMS

### Structure

```
BookConfigFactory
├─ createBookConfig(type, specs)
├─ validateSpecifications(specs)
└─ applyDefaultValues(type, specs)
```

### Key Components

1. **BookConfigFactory**: Central factory class that creates various book configurations
2. **BookConfig Interface**: Common interface implemented by all book types
3. **Concrete Book Classes**: HardcoverBook, PaperbackBook, SpiralBoundBook, etc.

## Benefits in Our System

- **Standardization**: All book configurations follow consistent validation rules
- **Simplified Client Code**: Customer portal only needs to call factory methods
- **Centralized Configuration Logic**: Changes to creation logic occur in one place
- **Default Values**: Factory can apply sensible defaults for each book type

## Usage Example Scenario

When a customer selects "Hardcover Book" in the configuration wizard, the system:
1. Collects base specifications (dimensions, page count, etc.)
2. Calls `BookConfigFactory.createBookConfig("hardcover", specs)`
3. Factory validates specifications and applies defaults for hardcover books
4. Factory instantiates a `HardcoverBook` with appropriate parameters
5. Returns configured book object to the client

## Diagram
![Factory Pattern for Book Configurations](../Diagrams/FactoryPattern.svg)