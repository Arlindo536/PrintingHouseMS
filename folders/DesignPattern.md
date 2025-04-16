# 📘 PrintingHouseMS - Design Patterns Implementation

## 🧭 Overview
This document outlines the design patterns applied in the PrintingHouseMS system. Design patterns are proven solutions to common problems in software design that help create more maintainable, flexible, and extensible code. These patterns support the architectural requirements of the printing house management system.

## 🔁Applied Design Patterns

### 🏭  1. Factory Pattern
**Purpose**: Create different types of book configurations without exposing the instantiation logic.

**Implementation**:
```java
// The BookConfigFactory creates different book configurations based on type
public class BookConfigFactory {
    public static BookConfig createBookConfig(String configType) {
        switch(configType) {
            case "HARDCOVER":
                return new HardcoverBookConfig();
            case "PAPERBACK":
                return new PaperbackBookConfig();
            case "SPIRAL":
                return new SpiralBookConfig();
            case "CUSTOM":
                return new CustomBookConfig();
            default:
                throw new IllegalArgumentException("Unknown book configuration type");
        }
    }
}

// Usage:
BookConfig bookConfig = BookConfigFactory.createBookConfig("HARDCOVER");
```

**Benefits**:
- Encapsulates book configuration creation logic
- Makes adding new book types easier without changing existing code
- Centralizes configuration creation for consistency

###  📣  2. Observer Pattern
**Purpose**: Implement a notification system where customers and staff receive updates about order status changes.

**Implementation**:
```java
// Subject interface
public interface OrderSubject {
    void registerObserver(OrderObserver observer);
    void removeObserver(OrderObserver observer);
    void notifyObservers();
}

// Observer interface
public interface OrderObserver {
    void update(String orderStatus, int orderId);
}

// Concrete subject
public class Order implements OrderSubject {
    private List<OrderObserver> observers = new ArrayList<>();
    private String orderStatus;
    private int orderId;
    
    @Override
    public void registerObserver(OrderObserver observer) {
        observers.add(observer);
    }
    
    @Override
    public void removeObserver(OrderObserver observer) {
        observers.remove(observer);
    }
    
    @Override
    public void notifyObservers() {
        for (OrderObserver observer : observers) {
            observer.update(orderStatus, orderId);
        }
    }
    
    public void setOrderStatus(String orderStatus) {
        this.orderStatus = orderStatus;
        notifyObservers();
    }
}

// Concrete observer
public class Customer implements OrderObserver {
    private int customerId;
    private String name;
    
    @Override
    public void update(String orderStatus, int orderId) {
        // Handle notification about order status change
        System.out.println("Notification to " + name + ": Order #" + 
                           orderId + " status changed to " + orderStatus);
    }
}
```

**Benefits**:
- Decouples order processing from notification mechanisms
- Allows multiple notification types (email, SMS, in-app) without changing order logic
- Makes it easy to add new notification recipients

###  📊  3. Strategy Pattern
**Purpose**: Implement different pricing strategies based on book specifications, volume, and customer type.

**Implementation**:
```java
// Strategy interface
public interface PricingStrategy {
    double calculatePrice(BookConfig bookConfig, int quantity);
}

// Concrete strategies
public class StandardPricingStrategy implements PricingStrategy {
    @Override
    public double calculatePrice(BookConfig bookConfig, int quantity) {
        double basePrice = calculateBasePrice(bookConfig);
        return basePrice * quantity;
    }
    
    private double calculateBasePrice(BookConfig bookConfig) {
        // Standard pricing calculation logic
        return 0.0; // Placeholder
    }
}

public class BulkPricingStrategy implements PricingStrategy {
    @Override
    public double calculatePrice(BookConfig bookConfig, int quantity) {
        double basePrice = calculateBasePrice(bookConfig);
        double discount = calculateVolumeDiscount(quantity);
        return basePrice * quantity * (1 - discount);
    }
    
    private double calculateBasePrice(BookConfig bookConfig) {
        // Bulk pricing calculation logic
        return 0.0; // Placeholder
    }
    
    private double calculateVolumeDiscount(int quantity) {
        // Volume discount logic
        return 0.0; // Placeholder
    }
}

// Context
public class PricingCalculator {
    private PricingStrategy strategy;
    
    public void setStrategy(PricingStrategy strategy) {
        this.strategy = strategy;
    }
    
    public double calculatePrice(BookConfig bookConfig, int quantity) {
        return strategy.calculatePrice(bookConfig, quantity);
    }
}

// Usage:
PricingCalculator calculator = new PricingCalculator();
if (quantity > 100) {
    calculator.setStrategy(new BulkPricingStrategy());
} else {
    calculator.setStrategy(new StandardPricingStrategy());
}
double price = calculator.calculatePrice(bookConfig, quantity);
```

**Benefits**:
- Allows switching between pricing algorithms at runtime
- Makes it easy to add new pricing strategies without changing existing code
- Isolates pricing calculation logic from order processing

### 🧍‍♂️ 4. Singleton Pattern
**Purpose**: Ensure only one instance of the notification manager exists in the system.

**Implementation**:
```java
public class NotificationManager {
    private static NotificationManager instance;
    private List<Notification> pendingNotifications;
    
    private NotificationManager() {
        pendingNotifications = new ArrayList<>();
    }
    
    public static synchronized NotificationManager getInstance() {
        if (instance == null) {
            instance = new NotificationManager();
        }
        return instance;
    }
    
    public void addNotification(Notification notification) {
        pendingNotifications.add(notification);
    }
    
    public void processNotifications() {
        for (Notification notification : pendingNotifications) {
            // Process and send notifications
        }
        pendingNotifications.clear();
    }
}

// Usage:
NotificationManager.getInstance().addNotification(new Notification(user, "Order processed"));
```

**Benefits**:
- Ensures system-wide access to the notification subsystem
- Prevents multiple instances from sending duplicate notifications
- Centralizes notification handling logic

### 🧱 5. MVC Architecture
**Purpose**: Separate the application into Model, View, and Controller components to improve maintainability and testability.

**Implementation**:
```java
// Model
public class OrderModel {
    private int orderId;
    private Customer customer;
    private List<OrderItem> items;
    private String status;
    
    // Getters and setters
    
    public double calculateTotal() {
        // Calculate order total
        return 0.0; // Placeholder
    }
}

// View
public class OrderView {
    public void displayOrderDetails(int orderId, Customer customer, 
                                    List<OrderItem> items, double total) {
        // Display order information to user
    }
    
    public void showError(String message) {
        // Display error message
    }
}

// Controller
public class OrderController {
    private OrderModel model;
    private OrderView view;
    
    public OrderController(OrderModel model, OrderView view) {
        this.model = model;
        this.view = view;
    }
    
    public void setOrderCustomer(Customer customer) {
        model.setCustomer(customer);
    }
    
    public void addOrderItem(OrderItem item) {
        model.getItems().add(item);
    }
    
    public void updateView() {
        view.displayOrderDetails(
            model.getOrderId(),
            model.getCustomer(),
            model.getItems(),
            model.calculateTotal()
        );
    }
}
```

**Benefits**:
- Separates concerns for better maintainability
- Allows independent development of UI and business logic
- Improves testability through separation
- Enables multiple views of the same data

## Implementation Strategy

To effectively implement these design patterns in the PrintingHouseMS system:

1. **Identify Pattern Application Points**:
   - Factory Pattern: Book configuration creation
   - Observer Pattern: Notification system
   - Strategy Pattern: Pricing calculations
   - Singleton Pattern: System-wide services
   - MVC: Overall application architecture

2. **Phased Implementation**:
   - Phase 1: Implement core patterns (MVC, Factory)
   - Phase 2: Add behavioral patterns (Observer, Strategy)
   - Phase 3: Optimize with Singleton where appropriate

3. **Documentation and Review**:
   - Document pattern usage in code
   - Review pattern implementations for correctness
   - Refactor as needed based on usage patterns

## 🧩  Conclusion

These design patterns provide a solid foundation for the PrintingHouseMS system, promoting code reuse, flexibility, and maintainability. They address specific challenges in the system while following established software engineering best practices.

The patterns work together to create a cohesive architecture:
- Factory Pattern creates diverse book configurations
- Observer Pattern keeps stakeholders informed
- Strategy Pattern provides flexible pricing
- Singleton Pattern manages global services
- MVC Architecture organizes the overall system

This approach ensures that the PrintingHouseMS system can evolve to meet changing business requirements while maintaining a clean, maintainable codebase.
