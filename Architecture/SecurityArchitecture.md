# Security Architecture Diagram

```mermaid
graph LR

    %% Nodes
    Customer["Customer Device"]
    Staff["Staff Device"]
    WebServer["Web Server (Frontend)"]
    AppServer["Application Server (Backend)"]
    Database["Relational Database"]
    FileStorage["Secure File Storage"]
    Firewall["Firewall"]
    AuthServer["Authentication Server"]
    EncryptionModule["Encryption Module"]
    IDS["Intrusion Detection System"]
    SecurityTeam["Security Operations Team"]

    %% Connections
    Customer -->|"HTTPS (TLS)"| Firewall
    Staff -->|"HTTPS (TLS)"| Firewall
    Firewall --> WebServer
    WebServer -->|"REST API Calls (HTTPS)"| AppServer
    AppServer --> Database
    AppServer --> FileStorage
    AppServer --> AuthServer
    AppServer --> EncryptionModule
    Firewall --> IDS
    IDS --> SecurityTeam

    %% Style definitions
    classDef whiteBox fill:#ffffff,stroke:#000000,color:#007acc,font-weight:bold;
    classDef redText fill:#ffffff,stroke:#000000,color:#d32f2f,font-weight:bold;

    class Customer,Staff,WebServer,AppServer,Database,FileStorage,Firewall,AuthServer,EncryptionModule,IDS whiteBox;
    class SecurityTeam redText;
