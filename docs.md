# REQUIREMENTS TABLE

| ID | Requirement type | Description | Priority (High/Medium/Low) |
|----|------------------|-------------|----------------------------|
| FR1 | Functional | Customers shall be able to create accounts and place book printing orders online. | High |
| FR2 | Functional | The system shall allow customers to upload book files in various formats (PDF, DOCX, InDesign). | High |
| FR3 | Functional | The system shall provide various binding options (hardcover, paperback, spiral, etc.) with visual examples. | High |
| FR4 | Functional | The system shall allow customers to select paper quality, weight, finish, and color. | High |
| FR5 | Functional | The system shall offer standard book dimensions with option for custom sizes. | Medium |
| FR6 | Functional | The system shall generate dynamic pricing based on selected options and quantity. | High |
| FR7 | Functional | The system shall provide a 3D preview of book cover with selected options. | Medium |
| FR8 | Functional | The system shall allow customers to track order status in real-time. | High |
| FR9 | Functional | Customers shall be able to communicate with printing house staff through an integrated messaging system. | Medium |
| FR10 | Functional | Staff shall be able to view all incoming orders with detailed specifications. | High |
| FR11 | Functional | Production workers shall update order status as items move through production workflow. | High |
| FR12 | Functional | The system shall generate printable job tickets with QR codes for production floor tracking. | Medium |
| FR13 | Functional | Staff shall be able to upload mockups and samples for customer approval. | Medium |
| FR14 | Functional | The system shall generate financial reports (daily, weekly, and monthly). | High |
| FR15 | Functional | The system shall track inventory levels and notify managers when stock is low. | High |
| NFR1 | Non-Functional | The system shall have a response time of less than 3 seconds for most operations. | High |
| NFR2 | Non-Functional | The system shall ensure secure file storage and data transmission. | High |
| NFR3 | Non-Functional | The system shall be accessible on both mobile and desktop devices. | Medium |
| NFR4 | Non-Functional | The system shall provide automatic data backups at regular intervals. | Medium |
| NFR5 | Non-Functional | The system shall support multiple concurrent users (at least 100). | High |
| NFR6 | Non-Functional | The staff interface shall be intuitive for users with limited technical experience. | High |

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 600">
  <!-- Background -->
  <rect width="800" height="600" fill="white"/>
  
  <!-- Onion Diagram Circles -->
  <circle cx="350" cy="300" r="200" fill="#9b59b6" opacity="0.8"/>
  <circle cx="350" cy="300" r="150" fill="#1abc9c" opacity="0.8"/>
  <circle cx="350" cy="300" r="100" fill="#e67e22" opacity="0.8"/>
  <circle cx="350" cy="300" r="50" fill="#f9f9f9" stroke="#333" stroke-width="1"/>
  
  <!-- Center Text -->
  <text x="350" y="295" font-family="Arial" font-size="20" text-anchor="middle" font-weight="bold">Printing</text>
  <text x="350" y="320" font-family="Arial" font-size="20" text-anchor="middle" font-weight="bold">House MS</text>
  
  <!-- Layer Labels and Lines -->
  <!-- External Layer (Purple) -->
  <line x1="550" y1="300" x2="580" y2="300" stroke="#9b59b6" stroke-width="2"/>
  <text x="585" y="305" font-family="Arial" font-size="16" font-weight="bold">External Factors</text>
  <text x="585" y="325" font-family="Arial" font-size="14">(Customers, Suppliers,</text>
  <text x="585" y="345" font-family="Arial" font-size="14">Shipping Providers,</text>
  <text x="585" y="365" font-family="Arial" font-size="14">Competitors)</text>
  
  <!-- Middle Layer (Green) -->
  <line x1="500" y1="220" x2="580" y2="220" stroke="#1abc9c" stroke-width="2"/>
  <text x="585" y="225" font-family="Arial" font-size="16" font-weight="bold">Internal Users</text>
  <text x="585" y="245" font-family="Arial" font-size="14">(Production Workers,</text>
  <text x="585" y="265" font-family="Arial" font-size="14">Managers, Designers,</text>
  <text x="585" y="285" font-family="Arial" font-size="14">Sales Staff)</text>
  
  <!-- Inner Layer (Orange) -->
  <line x1="450" y1="400" x2="580" y2="400" stroke="#e67e22" stroke-width="2"/>
  <text x="585" y="405" font-family="Arial" font-size="16" font-weight="bold">System Modules</text>
  <text x="585" y="425" font-family="Arial" font-size="14">(Order Management,</text>
  <text x="585" y="445" font-family="Arial" font-size="14">File Processing,</text>
  <text x="585" y="465" font-family="Arial" font-size="14">Production Tracking,</text>
  <text x="585" y="485" font-family="Arial" font-size="14">Inventory, Finance)</text>
  
  <!-- Title -->
  <text x="400" y="550" font-family="Arial" font-size="24" text-anchor="middle" font-weight="bold">ONION DIAGRAM</text>
</svg>
