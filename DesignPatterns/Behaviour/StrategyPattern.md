# 📊 Strategy Pattern Implementation for Pricing

## Overview
The Strategy Pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable. In PrintingHouseMS, this pattern is used to implement different pricing strategies based on book specifications, order volume, and customer type.

## Problem Solved
- **Algorithmic Flexibility**: Different pricing calculations can be applied dynamically
- **Business Rule Isolation**: Pricing policies are separated from order processing logic
- **Easy Modification**: New pricing strategies can be added without affecting existing code

## Implementation in PrintingHouseMS

### Structure

```
PricingStrategy
├─ StandardPricingStrategy
├─ BulkDiscountStrategy
├─ LoyalCustomerStrategy
└─ CorporateAccountStrategy
```

### Key Components

1. **PricingStrategy Interface**: Defines the common interface for all pricing strategies
2. **Context Class (PricingCalculator)**: Uses the selected strategy to perform pricing calculations
3. **Concrete Strategies**: Different pricing algorithms implementing the PricingStrategy interface
4. **Strategy Selector**: Logic to determine which strategy to apply based on order/customer factors

## Benefits in Our System

- **Dynamic Pricing**: Pricing can change based on customer type, order volume, or special promotions
- **Simplified Maintenance**: Each pricing algorithm is isolated and independently maintainable
- **Testability**: Pricing strategies can be tested individually
- **Business Flexibility**: Marketing and sales teams can introduce new pricing models without core code changes

## Usage Example Scenario

When a customer places an order:
1. `OrderProcessor` creates a `PricingCalculator` context
2. System evaluates the order and customer details
3. Based on evaluation, a specific pricing strategy is selected:
   - Regular customer with standard order → `StandardPricingStrategy`
   - Order with high volume → `BulkDiscountStrategy`
   - Repeat customer → `LoyalCustomerStrategy`
   - Corporate account → `CorporateAccountStrategy`
4. `PricingCalculator` uses the selected strategy to calculate the final price
5. Order total is computed and presented to the customer

## Diagram
![Strategy Pattern for Pricing](../Diagrams/StrategyPattern.svg)