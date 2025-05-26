# 🧍‍♂️ Singleton Pattern Implementation

## Overview
The Singleton Pattern restricts the instantiation of a class to a single instance and provides global access to that instance. In PrintingHouseMS, this pattern ensures only one instance of critical system managers exists, providing centralized control over printing operations, authentication, and configuration.

## Problem Solved
- **Resource Control**: Prevents multiple instances of components that should only exist once
- **Global Access**: Provides a single access point to critical system services
- **State Consistency**: Ensures consistent state across the printing house application
- **System Coordination**: Centralizes management of shared resources like print queues and configurations
- **Print Job Coordination**: Prevents conflicts in printer assignments and job scheduling

## Implementation in PrintingHouseMS

### Structure

#### ConfigurationManager
ConfigurationManager ├─ -instance: ConfigurationManager (static) ├─ -printerSettings: Map ├─ -paperTypes: List ├─ -bindingOptions: List ├─ -pricingRules: Map ├─ -ConfigurationManager() (private constructor) └─ +getInstance(): ConfigurationManager (static)


#### PrintQueueManager
PrintQueueManager ├─ -instance: PrintQueueManager (static) ├─ -activeJobs: Queue ├─ -printerRegistry: Map ├─ -queueStatus: Status ├─ -PrintQueueManager() (private constructor) └─ +getInstance(): PrintQueueManager (static)


#### AuthenticationService
AuthenticationService ├─ -instance: AuthenticationService (static) ├─ -userSession: Session ├─ -tokenManager: TokenManager ├─ -securityPolicies: Map ├─ -AuthenticationService() (private constructor) └─ +getInstance(): AuthenticationService (static)


### Key Components

1. **Private Constructor**: Prevents external instantiation of critical system managers
2. **Static Instance**: Single shared instance stored as a private static field
3. **Static Access Method**: Public method to access the instance (`getInstance()`)
4. **Thread-Safety Mechanism**: Ensures thread-safe instantiation in multi-user printing environment
5. **State Management**: Maintains consistent state for printing configurations, queues, and user sessions
6. **Resource Coordination**: Centralizes management of shared printing house resources

## Benefits in Our PrintingHouseMS System

- **Centralized Print Queue Management**: All print jobs are managed through a single queue manager
- **Unified Configuration Control**: System-wide printing settings managed consistently
- **Secure Authentication**: Single authentication service ensures consistent security policies
- **Resource Optimization**: Prevents redundant instances of resource-intensive printing managers
- **Consistent Pricing**: Single configuration manager ensures uniform pricing across all orders
- **Print Job Coordination**: Prevents conflicts in printer assignments and job scheduling
- **Operational Efficiency**: Single point of control for all printing operations

## Usage Example Scenario - Print Order Processing Flow

### Multi-Step Process:
1. **Authentication**: User login calls `AuthenticationService.getInstance()` for credential validation
2. **Configuration Access**: Order processing calls `ConfigurationManager.getInstance()` to get pricing rules and paper types
3. **Queue Management**: New print job calls `PrintQueueManager.getInstance()` to add job to the printing queue
4. **Printer Assignment**: Queue manager uses the same instance to assign jobs to available printers
5. **Status Updates**: All system components use the same queue manager instance to track job progress
6. **Billing Calculation**: Pricing calculations use the same configuration manager instance for consistent rates
7. **Multi-User Coordination**: Multiple staff members access shared instances simultaneously for coordinated operations
8. **Security Enforcement**: All authentication requests go through the same AuthenticationService instance
9. **Configuration Changes**: Updates affect all users immediately through the shared ConfigurationManager

### Real-World Scenario:
When a customer places a printing order:
- Different parts of the system call their respective singleton instances
- All calls receive the same instance of each manager
- The managers track job specifications, user preferences, and delivery status
- System-wide policies are consistently applied
- Resource allocation and job scheduling are managed centrally to prevent conflicts

## Singleton Applied To

### 1. ConfigurationManager
- **Purpose**: Manages printer settings, paper types, binding options, and pricing rules
- **Benefits**: Ensures consistent configuration across all printing operations
- **Features**: Validates system settings and maintains printing standards

### 2. PrintQueueManager
- **Purpose**: Controls print job queue and printer registry
- **Benefits**: Manages job scheduling and printer assignments
- **Features**: Tracks queue status and job progress in real-time

### 3. AuthenticationService
- **Purpose**: Handles user authentication and session management
- **Benefits**: Manages security tokens and policies consistently
- **Features**: Ensures secure access across the printing house system

### 4. Additional Singletons (Future Implementation)
- **LoggingService**: Centralized logging for all printing operations
- **DatabaseConnectionPool**: Manages database connections for order data
- **NotificationManager**: Handles customer and staff notifications
- **ReportingEngine**: Generates system-wide reports and analytics

## Thread Safety Considerations

In a multi-user printing environment, thread safety is crucial:
- **Lazy Initialization**: Instance created only when first requested
- **Double-Checked Locking**: Prevents multiple instances in concurrent scenarios
- **Synchronized Access**: Critical sections protected for queue and configuration updates

<svg width="1200" height="800" xmlns="http://www.w3.org/2000/svg">
<defs>
  <style>
    .class-box { fill: #ffffff; stroke: #000000; stroke-width: 2; }
    .class-header { fill: #e6f3ff; stroke: #000000; stroke-width: 1; }
    .text { fill: #000000; font-family: Arial, sans-serif; font-size: 10px; }
    .class-name { fill: #000000; font-family: Arial, sans-serif; font-size: 14px; font-weight: bold; }
    .title { fill: #000000; font-family: Arial, sans-serif; font-size: 18px; font-weight: bold; }
    .client-box { fill: #e6f7ff; stroke: #000000; stroke-width: 1; }
    .legend-box { fill: #fff9e6; stroke: #000000; stroke-width: 1; }
    .flow-box { fill: #f0f0f0; stroke: #000000; stroke-width: 1; }
    .step-box { fill: #ffffff; stroke: #0066cc; stroke-width: 1; }
    .completion-box { fill: #ffffff; stroke: #009900; stroke-width: 2; }
    .singleton-arrow { stroke: #cc0000; stroke-width: 2; fill: none; marker-end: url(#red-arrow); }
    .client-arrow { stroke: #0066cc; stroke-width: 2; fill: none; marker-end: url(#blue-arrow); }
    .collab-arrow { stroke: #009900; stroke-width: 2; fill: none; stroke-dasharray: 5,5; marker-end: url(#green-arrow); }
    .flow-arrow { stroke: #ff6600; stroke-width: 2; fill: none; marker-end: url(#orange-arrow); }
  </style>
  <marker id="red-arrow" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
    <polygon points="0 0, 10 3.5, 0 7" fill="#cc0000" />
  </marker>
  <marker id="blue-arrow" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
    <polygon points="0 0, 10 3.5, 0 7" fill="#0066cc" />
  </marker>
  <marker id="green-arrow" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
    <polygon points="0 0, 10 3.5, 0 7" fill="#009900" />
  </marker>
  <marker id="orange-arrow" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
    <polygon points="0 0, 10 3.5, 0 7" fill="#ff6600" />
  </marker>
</defs>

&lt;!-- Background -->
<rect width="1200" height="800" fill="#f8f9fa"/>

&lt;!-- Title -->
<text x="600" y="30" text-anchor="middle" class="title">Singleton Pattern - PrintingHouseMS System</text>

&lt;!-- ConfigurationManager -->
<rect x="50" y="80" width="320" height="180" class="class-box"/>
<rect x="50" y="80" width="320" height="30" class="class-header"/>
<text x="210" y="100" text-anchor="middle" class="class-name">ConfigurationManager</text>
<line x1="50" y1="110" x2="370" y2="110" stroke="#000000" stroke-width="1"/>
<text x="60" y="125" class="text">-static instance: ConfigurationManager</text>
<text x="60" y="140" class="text">-printerSettings: Map</text>
<text x="60" y="155" class="text">-paperTypes: List</text>
<text x="60" y="170" class="text">-bindingOptions: List</text>
<text x="60" y="185" class="text">-pricingRules: Map</text>
<line x1="50" y1="195" x2="370" y2="195" stroke="#000000" stroke-width="1"/>
<text x="60" y="210" class="text">+static getInstance(): ConfigurationManager</text>
<text x="60" y="225" class="text">+getPrinterSettings(): Map</text>
<text x="60" y="240" class="text">+updatePricingRules(): void</text>
<text x="60" y="255" class="text">+validateConfiguration(): boolean</text>

&lt;!-- PrintQueueManager -->
<rect x="440" y="80" width="320" height="180" class="class-box"/>
<rect x="440" y="80" width="320" height="30" class="class-header"/>
<text x="600" y="100" text-anchor="middle" class="class-name">PrintQueueManager</text>
<line x1="440" y1="110" x2="760" y2="110" stroke="#000000" stroke-width="1"/>
<text x="450" y="125" class="text">-static instance: PrintQueueManager</text>
<text x="450" y="140" class="text">-activeJobs: Queue</text>
<text x="450" y="155" class="text">-printerRegistry: Map</text>
<text x="450" y="170" class="text">-queueStatus: Status</text>
<line x1="440" y1="185" x2="760" y2="185" stroke="#000000" stroke-width="1"/>
<text x="450" y="200" class="text">+static getInstance(): PrintQueueManager</text>
<text x="450" y="215" class="text">+addJobToQueue(job): void</text>
<text x="450" y="230" class="text">+getNextJob(): PrintJob</text>
<text x="450" y="245" class="text">+registerPrinter(printer): void</text>
<text x="450" y="260" class="text">+getQueueStatus(): Status</text>

&lt;!-- AuthenticationService -->
<rect x="830" y="80" width="320" height="180" class="class-box"/>
<rect x="830" y="80" width="320" height="30" class="class-header"/>
<text x="990" y="100" text-anchor="middle" class="class-name">AuthenticationService</text>
<line x1="830" y1="110" x2="1150" y2="110" stroke="#000000" stroke-width="1"/>
<text x="840" y="125" class="text">-static instance: AuthenticationService</text>
<text x="840" y="140" class="text">-userSession: Session</text>
<text x="840" y="155" class="text">-tokenManager: TokenManager</text>
<text x="840" y="170" class="text">-securityPolicies: Map</text>
<line x1="830" y1="180" x2="1150" y2="180" stroke="#000000" stroke-width="1"/>
<text x="840" y="195" class="text">+static getInstance(): AuthenticationService</text>
<text x="840" y="210" class="text">+authenticateUser(credentials): boolean</text>
<text x="840" y="225" class="text">+validateToken(token): boolean</text>
<text x="840" y="240" class="text">+generateNewToken(userID): String</text>
<text x="840" y="255" class="text">+logout(): void</text>

&lt;!-- Client Classes -->
<rect x="50" y="320" width="150" height="80" class="client-box"/>
<text x="125" y="340" text-anchor="middle" class="class-name" font-size="12">OrderProcessor</text>
<line x1="50" y1="350" x2="200" y2="350" stroke="#000000" stroke-width="1"/>
<text x="60" y="365" class="text">+processOrder(): void</text>
<text x="60" y="380" class="text">+calculatePricing(): double</text>
<text x="60" y="395" class="text">+validateSpecs(): boolean</text>

<rect x="250" y="320" width="150" height="80" class="client-box"/>
<text x="325" y="340" text-anchor="middle" class="class-name" font-size="12">PrintingController</text>
<line x1="250" y1="350" x2="400" y2="350" stroke="#000000" stroke-width="1"/>
<text x="260" y="365" class="text">+managePrintJobs(): void</text>
<text x="260" y="380" class="text">+assignPrinters(): void</text>
<text x="260" y="395" class="text">+trackProgress(): void</text>

<rect x="450" y="320" width="150" height="80" class="client-box"/>
<text x="525" y="340" text-anchor="middle" class="class-name" font-size="12">UserInterface</text>
<line x1="450" y1="350" x2="600" y2="350" stroke="#000000" stroke-width="1"/>
<text x="460" y="365" class="text">+handleLogin(): void</text>
<text x="460" y="380" class="text">+displayOrders(): void</text>
<text x="460" y="395" class="text">+showStatus(): void</text>

<rect x="650" y="320" width="150" height="80" class="client-box"/>
<text x="725" y="340" text-anchor="middle" class="class-name" font-size="12">ReportGenerator</text>
<line x1="650" y1="350" x2="800" y2="350" stroke="#000000" stroke-width="1"/>
<text x="660" y="365" class="text">+generateReports(): void</text>
<text x="660" y="380" class="text">+analyzeData(): void</text>
<text x="660" y="395" class="text">+exportResults(): void</text>

&lt;!-- Self-reference arrows for singletons -->
<path d="M 370 140 Q 400 140 400 170 Q 400 200 370 200" class="singleton-arrow"/>
<path d="M 760 140 Q 790 140 790 170 Q 790 200 760 200" class="singleton-arrow"/>
<path d="M 1150 140 Q 1180 140 1180 170 Q 1180 200 1150 200" class="singleton-arrow"/>

&lt;!-- Client to Singleton arrows -->
<line x1="125" y1="320" x2="210" y2="260" class="client-arrow"/>
<line x1="325" y1="320" x2="600" y2="260" class="client-arrow"/>
<line x1="525" y1="320" x2="990" y2="260" class="client-arrow"/>
<line x1="725" y1="320" x2="210" y2="260" class="client-arrow"/>

&lt;!-- Cross-singleton dependencies -->
<line x1="370" y1="180" x2="440" y2="180" class="collab-arrow"/>
<line x1="760" y1="180" x2="830" y2="180" class="collab-arrow"/>

&lt;!-- Labels -->
<text x="405" y="175" fill="#cc0000" class="text" font-size="9">instance</text>
<text x="795" y="175" fill="#cc0000" class="text" font-size="9">instance</text>
<text x="1185" y="175" fill="#cc0000" class="text" font-size="9">instance</text>

<text x="270" y="290" fill="#0066cc" class="text" font-size="9">uses</text>
<text x="470" y="290" fill="#0066cc" class="text" font-size="9">uses</text>
<text x="720" y="290" fill="#0066cc" class="text" font-size="9">uses</text>
<text x="470" y="290" fill="#0066cc" class="text" font-size="9">uses</text>

<text x="405" y="195" fill="#009900" class="text" font-size="9">collaborates</text>
<text x="795" y="195" fill="#009900" class="text" font-size="9">collaborates</text>

&lt;!-- Legend -->
<rect x="50" y="450" width="400" height="120" class="legend-box"/>
<text x="250" y="470" text-anchor="middle" class="class-name">PrintingHouseMS Singleton Pattern</text>
<text x="60" y="490" class="text" font-weight="bold">Key Benefits:</text>
<text x="60" y="505" class="text">• Centralized configuration management</text>
<text x="60" y="520" class="text">• Unified print queue coordination</text>
<text x="60" y="535" class="text">• Consistent authentication across system</text>
<text x="60" y="550" class="text">• Thread-safe resource management</text>

&lt;!-- Usage Flow -->
<rect x="500" y="450" width="650" height="300" class="flow-box"/>
<text x="825" y="470" text-anchor="middle" class="class-name">PrintingHouseMS Usage Flow</text>

&lt;!-- Flow steps -->
<rect x="520" y="490" width="280" height="40" class="step-box"/>
<text x="660" y="505" text-anchor="middle" class="text" font-weight="bold">1. User Authentication</text>
<text x="660" y="520" text-anchor="middle" class="text" font-size="9">AuthenticationService.getInstance()</text>

<rect x="850" y="490" width="280" height="40" class="step-box"/>
<text x="990" y="505" text-anchor="middle" class="text" font-weight="bold">2. Order Configuration</text>
<text x="990" y="520" text-anchor="middle" class="text" font-size="9">ConfigurationManager.getInstance()</text>

<rect x="520" y="550" width="280" height="40" class="step-box"/>
<text x="660" y="565" text-anchor="middle" class="text" font-weight="bold">3. Print Job Creation</text>
<text x="660" y="580" text-anchor="middle" class="text" font-size="9">PrintQueueManager.getInstance()</text>

<rect x="850" y="550" width="280" height="40" class="step-box"/>
<text x="990" y="565" text-anchor="middle" class="text" font-weight="bold">4. Queue Management</text>
<text x="990" y="580" text-anchor="middle" class="text" font-size="9">Centralized job coordination</text>

<rect x="520" y="610" width="280" height="40" class="step-box"/>
<text x="660" y="625" text-anchor="middle" class="text" font-weight="bold">5. Printer Assignment</text>
<text x="660" y="640" text-anchor="middle" class="text" font-size="9">Automatic printer selection</text>

<rect x="850" y="610" width="280" height="40" class="step-box"/>
<text x="990" y="625" text-anchor="middle" class="text" font-weight="bold">6. Status Tracking</text>
<text x="990" y="640" text-anchor="middle" class="text" font-size="9">Real-time progress monitoring</text>

<rect x="685" y="670" width="280" height="40" class="completion-box"/>
<text x="825" y="685" text-anchor="middle" class="text" font-weight="bold">7. Order Completion</text>
<text x="825" y="700" text-anchor="middle" class="text" font-size="9">Unified system coordination</text>

&lt;!-- Flow arrows -->
<line x1="800" y1="510" x2="850" y2="510" class="flow-arrow"/>
<line x1="990" y1="530" x2="660" y2="550" class="flow-arrow"/>
<line x1="800" y1="570" x2="850" y2="570" class="flow-arrow"/>
<line x1="990" y1="590" x2="660" y2="610" class="flow-arrow"/>
<line x1="800" y1="630" x2="850" y2="630" class="flow-arrow"/>
<line x1="990" y1="650" x2="825" y2="670" class="flow-arrow"/>
</svg>
## Real-World Benefits

- **Operational Efficiency**: Single point of control for all printing operations
- **Data Consistency**: Unified configuration prevents conflicting settings
- **Resource Management**: Optimal use of printers and materials through centralized queue
- **Security**: Consistent authentication and authorization across all system access points
- **Scalability**: Easy to extend with additional singleton services as the printing house grows
- **Maintenance**: Simplified system maintenance with centralized component management
- **Performance**: Reduced memory footprint and improved resource utilization
