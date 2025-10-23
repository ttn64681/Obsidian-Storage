```table-of-contents
```

### 1. Client-Server
*   **Key Idea:** Client initiates requests, server processes and responds. Client knows server, but server doesn't inherently know the client.
*   **Example:** Web browsing (browser is client, website server is server), Email (email client, mail server).

### 2. Peer-to-Peer (P2P)
*   **Key Idea:** All participants (peers) can act as both clients and servers, communicating directly with each other.
*   **Example:** BitTorrent for file sharing, blockchain networks.

### 3. N-Tier (e.g., 3-Tier)
*   **Key Idea:** Divides an application into logical and physical layers (e.g., Presentation, Business Logic, Data) for separation of concerns and scalability.
*   **Example:** Most modern web applications, where the web browser is the presentation tier, an application server is the business logic tier, and a database server is the data tier.

### 4. Closed Multi-layer (Opaque Layering)
*   **Key Idea:** Layers can only interact with the layer immediately below them, enforcing strict separation and enhancing maintainability, flexibility, and security.
*   **Example:** Operating systems, where applications interact with system calls, which then interact with the kernel.

### 5. Repository
*   **Key Idea:** Components share data through a central, common data structure (repository); primarily aims for good overall system response time.
*   **Example:** Integrated Development Environments (IDEs) where various tools (compiler, debugger, editor) interact with a central project repository.

### 6. Pipe & Filter
*   **Key Idea:** Data flows sequentially through a series of independent processing steps (filters), each performing a specific transformation; aims for good overall system throughput.
*   **Example:** Unix command-line pipelines (`cat file.txt | grep "error" | sort`), compilers (lexer, parser, code generator).

### 7. Model-View-Controller (MVC)
*   **Key Idea:** Separates an application into three interconnected components: Model (data/business logic), View (user interface), and Controller (handles input and updates model/view).
*   **Example:** Web frameworks like Ruby on Rails, Spring MVC, or desktop applications.

### 8. Monolithic
*   **Key Idea:** All components of an application are tightly coupled and deployed as a single, indivisible unit.
*   **Example:** Many traditional enterprise applications or smaller web applications (e.g., a simple e-commerce site deployed as one WAR file).

### 9. Microservices
*   **Key Idea:** An application is built as a collection of small, independent, loosely coupled services, each running in its own process and communicating via lightweight mechanisms.
*   **Example:** Netflix, Amazon (each function like user authentication, payment processing, or recommendation engine is a separate service).

### 10. Event-Driven
*   **Key Idea:** Components communicate asynchronously by producing and consuming events, allowing for loose coupling and scalability.
*   **Example:** E-commerce order processing (order placed event, payment processed event, shipping initiated event), real-time dashboards.

### 11. Service-Oriented Architecture (SOA)
*   **Key Idea:** A collection of loosely coupled, interoperable services that communicate via standardized protocols (e.g., SOAP, REST), often with a central enterprise service bus (ESB).
*   **Example:** Large enterprise systems integrating various business functions like ERP, CRM, and supply chain management.