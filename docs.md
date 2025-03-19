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
  <circle cx="400" cy="250" r="200" fill="#8e44ad" opacity="0.8"/>
  <circle cx="400" cy="250" r="150" fill="#16a085" opacity="0.8"/>
  <circle cx="400" cy="250" r="100" fill="#e67e22" opacity="0.8"/>
  <circle cx="400" cy="250" r="50" fill="#f9f9f9" stroke="#333" stroke-width="1"/>
  
  <!-- Center Text -->
  <text x="400" y="245" font-family="Arial" font-size="20" text-anchor="middle" font-weight="bold">Printing</text>
  <text x="400" y="270" font-family="Arial" font-size="20" text-anchor="middle" font-weight="bold">House MS</text>
  
  <!-- Layer Labels and Lines -->
  <!-- External Layer -->
  <line x1="600" y1="250" x2="650" y2="250" stroke="#8e44ad" stroke-width="2"/>
  <text x="655" y="240" font-family="Arial" font-size="14" font-weight="bold">External Factors</text>
  <text x="655" y="260" font-family="Arial" font-size="12">(Customers, Suppliers,</text>
  <text x="655" y="275" font-family="Arial" font-size="12">Shipping Providers,</text>
  <text x="655" y="290" font-family="Arial" font-size="12">Competitors)</text>
  
  <!-- Middle Layer -->
  <line x1="550" y1="200" x2="650" y2="200" stroke="#16a085" stroke-width="2"/>
  <text x="655" y="190" font-family="Arial" font-size="14" font-weight="bold">Internal Users</text>
  <text x="655" y="210" font-family="Arial" font-size="12">(Production Workers,</text>
  <text x="655" y="225" font-family="Arial" font-size="12">Managers, Designers,</text>
  <text x="655" y="240" font-family="Arial" font-size="12">Sales Staff)</text>
  
  <!-- Inner Layer -->
  <line x1="500" y1="320" x2="650" y2="320" stroke="#e67e22" stroke-width="2"/>
  <text x="655" y="310" font-family="Arial" font-size="14" font-weight="bold">System Modules</text>
  <text x="655" y="330" font-family="Arial" font-size="12">(Order Management,</text>
  <text x="655" y="345" font-family="Arial" font-size="12">File Processing,</text>
  <text x="655" y="360" font-family="Arial" font-size="12">Production Tracking,</text>
  <text x="655" y="375" font-family="Arial" font-size="12">Inventory, Finance)</text>
  
  <!-- Title -->
  <text x="400" y="500" font-family="Arial" font-size="24" text-anchor="middle" font-weight="bold">ONION DIAGRAM</text>
</svg>
