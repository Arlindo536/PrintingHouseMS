%% Level 1 - Detailed Processes
flowchart TD
    %% Title
    classDef titleClass fill:#fff,stroke:none
    title[Level 1 - Detailed System Processes: PrintingHouseMS]
    class title titleClass
    
    %% External entities with distinct shapes
    Customer([Customer])
    PaymentGateway([Payment Gateway])
    ShippingPartner([Shipping Partner])
    Staff([Staff])
    
    %% Main Processes with clear numbering
    P1((1.0\nOrder\nManagement))
    P2((2.0\nBook\nConfiguration))
    P3((3.0\nProduction\nTracking))
    P4((4.0\nNotification\nSystem))
    
    %% Data Stores with clear numbering
    DS1[(D1: Customer\nData)]
    DS2[(D2: Order\nDetails)]
    DS3[(D3: Book\nConfigurations)]
    DS4[(D4: Production\nStatus)]
    
    %% Customer interactions
    Customer -->|1. Submit order| P1
    Customer -->|2. Provide book specs| P2
    P4 -->|3. Status notifications| Customer
    
    %% Payment Gateway interactions
    PaymentGateway -->|4. Payment confirmation| P1
    P1 -->|5. Process payment| PaymentGateway
    
    %% Shipping Partner interactions
    P1 -->|6. Shipping request| ShippingPartner
    ShippingPartner -->|7. Delivery updates| P3
    
    %% Staff interactions
    Staff -->|8. Process orders| P1
    Staff -->|9. Configure books| P2
    Staff -->|10. Manage production| P3
    P4 -->|11. Work notifications| Staff
    
    %% Process interactions
    P1 -->|12. New order| P2
    P2 -->|13. Book specs| P3
    P3 -->|14. Status update| P4
    P4 -->|15. Order update| P1
    
    %% Data store interactions
    P1 <-->|16. Store/retrieve| DS1
    P1 <-->|17. Record orders| DS2
    P2 <-->|18. Store configs| DS3
    P3 <-->|19. Update status| DS4
    
    %% Visual styling
    classDef process fill:#f9f,stroke:#333,stroke-width:2px
    classDef datastore fill:#bbf,stroke:#33f,stroke-width:1px
    classDef external fill:#ffc,stroke:#333,stroke-width:1px
    
    class P1,P2,P3,P4 process
    class DS1,DS2,DS3,DS4 datastore
    class Customer,PaymentGateway,ShippingPartner,Staff external
