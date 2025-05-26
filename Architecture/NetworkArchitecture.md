# Network Architecture Diagram

```mermaid
graph LR

    %% Nodes with white background, black border, and colored text
    Customer[Customer Device]
    Staff[Staff Device]
    PaymentGateway[Payment Gateway]
    ShippingPartner[Shipping Partner]
    Internet[(Internet)]
    WebServer["Web Server (Frontend)"]
    AppServer["Application Server (Backend)"]
    Database["Relational Database"]
    FileStorage["Secure File Storage"]

    %% Connections
    Customer -->|HTTPS Request| Internet
    Staff -->|HTTPS Request| Internet
    Internet -->|HTTPS Request| WebServer
    WebServer -->|REST API Calls| AppServer
    AppServer -->|SQL Queries| Database
    AppServer -->|Read/Write Files| FileStorage
    AppServer -->|Payment API Calls| PaymentGateway
    AppServer -->|Shipping API Calls| ShippingPartner

    %% Style definitions
    classDef whiteBox fill:#ffffff,stroke:#000000,color:#007acc,font-weight:bold;
    classDef redText fill:#ffffff,stroke:#000000,color:#d32f2f,font-weight:bold;

    class Customer,Staff,Internet,WebServer,AppServer,Database,FileStorage whiteBox;
    class PaymentGateway,ShippingPartner redText;
