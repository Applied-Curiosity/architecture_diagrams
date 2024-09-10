Here's a concise guide based on the C4 Architecture model:

### C4 Model for Visualizing Software Architecture

The C4 model breaks down software architecture into four hierarchical diagrams:
#### 1. System Context Diagram
- **Purpose**: Provides a high-level view of the system and its interactions.
- **Components**: Shows the system (as a central box), users, and other interacting systems.
- **Focus**: People (actors, roles, personas) and software systems, not technologies or protocols.

#### 2. Container Diagram
- **Purpose**: Illustrates high-level technology choices and the overall architecture.
- **Components**: Displays containers (e.g., web applications, databases) and their communication.
- **Focus**: Separately deployable units executing code or storing data, and their interactions.

#### 3. Component Diagram
- **Purpose**: Zooms into each container to show major building blocks and their interactions.
- **Components**: Details components, their responsibilities, and implementation details.
- **Focus**: Structural details within a container; multiple diagrams may be needed for complex containers.

#### 4. (Optional) Code/Class Diagram
- **Purpose**: Further detail components by showing class structures and code-level elements.
- **Components**: Classes, methods, properties, etc.
- **Focus**: Detailed implementation specifics.

### Additional Notes
- **Hierarchy**: The C4 model moves from high-level (System Context) to detailed (Code/Class).
- **Consistency**: Ensure consistent notation and a shared set of abstractions within the team.
- **Supplementary Diagrams**: Use additional diagrams to show runtime behavior and deployment.

### Example Usage in Obsidian
You can create sections in your Obsidian notes for each diagram level, adding diagrams and descriptions as needed. Here’s a structure you might follow:

```markdown
# C4 Architecture Model

## System Context Diagram
- Description: High-level view of the system and interactions.
- Diagram: ![System Context](path/to/system-context-diagram.png)

## Container Diagram
- Description: High-level technology choices and architecture.
- Diagram: ![Container](path/to/container-diagram.png)

## Component Diagram
- Description: Detailed view of components within containers.
- Diagram: ![Component](path/to/component-diagram.png)

## Code/Class Diagram (Optional)
- Description: Code-level details of components.
- Diagram: ![Code/Class](path/to/code-class-diagram.png)
```

### C4 Diagrams
Here’s an expanded guide on using Mermaid to create C4 Architecture diagrams, based on the official Mermaid C4 syntax documentation:

### C4 Model with Mermaid

#### System Context Diagram
```mermaid
    C4Context
      title System Context diagram for Internet Banking System
      Enterprise_Boundary(b0, "BankBoundary0") {
        Person(customerA, "Banking Customer A", "A customer of the bank, with personal bank accounts.")
        Person(customerB, "Banking Customer B")
        Person_Ext(customerC, "Banking Customer C", "desc")

        Person(customerD, "Banking Customer D", "A customer of the bank, <br/> with personal bank accounts.")

        System(SystemAA, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")

        Enterprise_Boundary(b1, "BankBoundary") {

          SystemDb_Ext(SystemE, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

          System_Boundary(b2, "BankBoundary2") {
            System(SystemA, "Banking System A")
            System(SystemB, "Banking System B", "A system of the bank, with personal bank accounts. next line.")
          }

          System_Ext(SystemC, "E-mail system", "The internal Microsoft Exchange e-mail system.")
          SystemDb(SystemD, "Banking System D Database", "A system of the bank, with personal bank accounts.")

          Boundary(b3, "BankBoundary3", "boundary") {
            SystemQueue(SystemF, "Banking System F Queue", "A system of the bank.")
            SystemQueue_Ext(SystemG, "Banking System G Queue", "A system of the bank, with personal bank accounts.")
          }
        }
      }

      BiRel(customerA, SystemAA, "Uses")
      BiRel(SystemAA, SystemE, "Uses")
      Rel(SystemAA, SystemC, "Sends e-mails", "SMTP")
      Rel(SystemC, customerA, "Sends e-mails to")

      UpdateElementStyle(customerA, $fontColor="red", $bgColor="grey", $borderColor="red")
      UpdateRelStyle(customerA, SystemAA, $textColor="blue", $lineColor="blue", $offsetX="5")
      UpdateRelStyle(SystemAA, SystemE, $textColor="blue", $lineColor="blue", $offsetY="-10")
      UpdateRelStyle(SystemAA, SystemC, $textColor="blue", $lineColor="blue", $offsetY="-40", $offsetX="-50")
      UpdateRelStyle(SystemC, customerA, $textColor="red", $lineColor="red", $offsetX="-50", $offsetY="20")

      UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")


```
- **C4Context**: Defines a system context diagram.
- **Boundary**: Groups elements within a boundary.
- **Person/System**: Defines actors and systems.
- **->**: Defines interactions.

#### Container Diagram
```mermaid
    C4Container
    title Container diagram for Internet Banking System

    System_Ext(email_system, "E-Mail System", "The internal Microsoft Exchange system", $tags="v1.0")
    Person(customer, Customer, "A customer of the bank, with personal bank accounts", $tags="v1.0")

    Container_Boundary(c1, "Internet Banking") {
        Container(spa, "Single-Page App", "JavaScript, Angular", "Provides all the Internet banking functionality to customers via their web browser")
        Container_Ext(mobile_app, "Mobile App", "C#, Xamarin", "Provides a limited subset of the Internet banking functionality to customers via their mobile device")
        Container(web_app, "Web Application", "Java, Spring MVC", "Delivers the static content and the Internet banking SPA")
        ContainerDb(database, "Database", "SQL Database", "Stores user registration information, hashed auth credentials, access logs, etc.")
        ContainerDb_Ext(backend_api, "API Application", "Java, Docker Container", "Provides Internet banking functionality via API")

    }

    System_Ext(banking_system, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

    Rel(customer, web_app, "Uses", "HTTPS")
    UpdateRelStyle(customer, web_app, $offsetY="60", $offsetX="90")
    Rel(customer, spa, "Uses", "HTTPS")
    UpdateRelStyle(customer, spa, $offsetY="-40")
    Rel(customer, mobile_app, "Uses")
    UpdateRelStyle(customer, mobile_app, $offsetY="-30")

    Rel(web_app, spa, "Delivers")
    UpdateRelStyle(web_app, spa, $offsetX="130")
    Rel(spa, backend_api, "Uses", "async, JSON/HTTPS")
    Rel(mobile_app, backend_api, "Uses", "async, JSON/HTTPS")
    Rel_Back(database, backend_api, "Reads from and writes to", "sync, JDBC")

    Rel(email_system, customer, "Sends e-mails to")
    UpdateRelStyle(email_system, customer, $offsetX="-45")
    Rel(backend_api, email_system, "Sends e-mails using", "sync, SMTP")
    UpdateRelStyle(backend_api, email_system, $offsetY="-60")
    Rel(backend_api, banking_system, "Uses", "sync/async, XML/HTTPS")
    UpdateRelStyle(backend_api, banking_system, $offsetY="-50", $offsetX="-140")
```
- **C4Container**: Defines a container diagram.
- **Container/ContainerDb**: Defines containers and databases.
- **System_Boundary**: Defines system boundaries.

#### Component Diagram
```mermaid
    C4Component
    title Component diagram for Internet Banking System - API Application

    Container(spa, "Single Page Application", "javascript and angular", "Provides all the internet banking functionality to customers via their web browser.")
    Container(ma, "Mobile App", "Xamarin", "Provides a limited subset to the internet banking functionality to customers via their mobile mobile device.")
    ContainerDb(db, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
    System_Ext(mbs, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

    Container_Boundary(api, "API Application") {
        Component(sign, "Sign In Controller", "MVC Rest Controller", "Allows users to sign in to the internet banking system")
        Component(accounts, "Accounts Summary Controller", "MVC Rest Controller", "Provides customers with a summary of their bank accounts")
        Component(security, "Security Component", "Spring Bean", "Provides functionality related to singing in, changing passwords, etc.")
        Component(mbsfacade, "Mainframe Banking System Facade", "Spring Bean", "A facade onto the mainframe banking system.")

        Rel(sign, security, "Uses")
        Rel(accounts, mbsfacade, "Uses")
        Rel(security, db, "Read & write to", "JDBC")
        Rel(mbsfacade, mbs, "Uses", "XML/HTTPS")
    }

    Rel_Back(spa, sign, "Uses", "JSON/HTTPS")
    Rel(spa, accounts, "Uses", "JSON/HTTPS")

    Rel(ma, sign, "Uses", "JSON/HTTPS")
    Rel(ma, accounts, "Uses", "JSON/HTTPS")

    UpdateRelStyle(spa, sign, $offsetY="-40")
    UpdateRelStyle(spa, accounts, $offsetX="40", $offsetY="40")

    UpdateRelStyle(ma, sign, $offsetX="-90", $offsetY="40")
    UpdateRelStyle(ma, accounts, $offsetY="-40")

        UpdateRelStyle(sign, security, $offsetX="-160", $offsetY="10")
        UpdateRelStyle(accounts, mbsfacade, $offsetX="140", $offsetY="10")
        UpdateRelStyle(security, db, $offsetY="-40")
        UpdateRelStyle(mbsfacade, mbs, $offsetY="-40")
```
- **C4Component**: Defines a component diagram.
- **Component/ComponentDb**: Defines components and databases.
- **Container_Boundary**: Defines container boundaries.

#### Code/Class Diagram (Optional)
```mermaid
classDiagram
    class User {
        +String name
        +String email
    }
    class UserService {
        +User getUser(int id)
    }
    UserService --> User : Uses
```
- **classDiagram**: Defines a class diagram.
- **class**: Defines classes and their attributes/methods.

 [Mermaid C4 syntax documentation](https://mermaid.js.org/syntax/c4.html).
### Tags
#diagram #C4 #architecture 