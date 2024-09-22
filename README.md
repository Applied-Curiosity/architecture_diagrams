# Architecture Diagrams Repository

This repository contains generic starting templates for architectural diagrams used in our projects. These diagrams are meant to be used as a foundation for client-specific architectural designs.

It also contains a library of reference libraries for AWS and Databricks. For Azure diagrams, the most reliable and up-to-date diagrams and diagram tools are located at [[Azure Diagrams](https://azurediagrams.com/)].

## Contents

- C4 Model Diagrams
- Cloud Architecture Diagrams
- Network Topology Diagrams

## Usage

1. Clone this repository to your local machine.
2. Copy the relevant diagram templates to your client-specific project repository.
3. Customize and refine the diagrams to meet the specific needs of your client.

## Diagram Types

### C4 Model Diagrams

We use the C4 model for visualizing software architecture. Our repository includes templates for:

- Context Diagrams (C1)
- Container Diagrams (C2)
- Component Diagrams (C3)

For detailed instructions on creating C4 diagrams, please refer to the C4 instruction documents in this repository.

### Cloud Architecture Diagrams

Our cloud architecture diagrams are designed to capture detailed solution architectures. We use a layered approach:

1. Abstract Layer: High-level overview of the system (this could be the C4 diagram)
2. Networking Layer: Network topology and connections
3. Storage Layer: Major storage resources
4. Compute Layer: Compute resources where needed

### Network Topology Diagrams

Network topology diagrams follow a similar layered approach to the cloud architecture diagrams.

## Tools

We primarily use Draw.io for creating and editing our diagrams. Please ensure you have Draw.io installed or use the online version when working with these templates.

## Important Guidelines

1. **Do not check in client-specific files to this repository.** This is a public repository for generic templates only.
2. When creating client-specific diagrams, always work in the client's private repository.
3. Keep the generic templates in this repository up-to-date with best practices and common patterns.
4. When adding new templates, ensure they are generic and do not contain any client-specific information.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

