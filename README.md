# Liara OpenAPI Specification

[![OpenAPI Specification](https://img.shields.io/badge/OpenAPI-3.0-brightgreen)](https://swagger.io/specification/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Welcome to the official Liara Cloud Platform OpenAPI Specification repository. This repository contains comprehensive [OpenAPI specifications](https://openapi.liara.ir/) for all Liara API services, enabling developers to integrate with Liara's cloud platform seamlessly.

## 📖 Overview

Liara provides a comprehensive suite of cloud services designed to help developers build, deploy, and scale their applications. This repository serves as the single source of truth for all Liara API specifications, including:

| Service | Description | Specification |
|---------|-------------|---------------|
| **PaaS** | Platform as a Service for deploying and managing applications | [`spec/paas.yaml`](spec/paas.yaml) |
| **DBaaS** | Database as a Service for managed databases | [`spec/dbaas.yaml`](spec/dbaas.yaml) |
| **Object Storage** | Scalable object storage for any amount of data | [`spec/object-storage.yaml`](spec/object-storage.yaml) |
| **DNS** | DNS zone and record management | [`spec/dns.yaml`](spec/dns.yaml) |
| **Mail** | Email delivery and management platform | [`spec/mail.yaml`](spec/mail.yaml) |
| **File Browser** | Web-based file management for disks | [`spec/file-browser.yaml`](spec/file-browser.yaml) |
| **IaaS** | Infrastructure as a Service for virtual machines | [`spec/Iaas.yaml`](spec/Iaas.yaml) |
<!-- | **Database Inspector** | Database inspection and analysis tools | [`spec/database-inspector.yaml`](spec/database-inspector.yaml) | -->

## 🚀 Quick Start

### Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/) (version 20.10 or higher)
- [Docker Compose](https://docs.docker.com/compose/install/) (version 2.0 or higher)
- [Node.js](https://nodejs.org/) (version 20.17.0 or higher) - for Mintlify development
- A code editor (we recommend [VS Code](https://code.visualstudio.com/))

### Running Locally

Choose your preferred development environment:

#### Option 1: Swagger UI (Docker)

Preview and interact with API specifications using Swagger UI:

1. **Clone the repository**

   ```bash
   git clone https://github.com/liara-cloud/openapi.git
   cd openapi
   ```

2. **Start the Swagger UI container**

   ```bash
   docker compose up -d
   ```

3. **Access the documentation**

   Open your browser and navigate to: [http://localhost:8080](http://localhost:8080)


#### Option 2: Mintlify (Documentation Preview)

Preview the full documentation site with Mintlify:

1. **Clone the repository**

   ```bash
   git clone https://github.com/liara-cloud/openapi.git
   cd openapi
   ```

2. **Install Mintlify CLI**

   ```bash
   npm i -g mint
   ```

3. **Start the development server**

   ```bash
   mint dev
   ```

4. **Access the documentation**

   The documentation will automatically open in your browser, or navigate to the URL shown in your terminal (typically [http://localhost:3000](http://localhost:3000)).

## 📁 Project Structure

```
openapi/
├── .github/                    # GitHub workflows and configurations
├── pages/                      # Documentation pages for Mintlify (MDX format)
│   ├── dbaas.mdx              # DBaaS introduction
│   ├── dns.mdx                # DNS introduction
│   ├── file-browser.mdx       # File Browser introduction
│   ├── iaas.mdx               # IaaS introduction
│   ├── mail.mdx               # Mail service introduction
│   ├── object-storage.mdx     # Object Storage introduction
│   └── paas.mdx               # PaaS introduction
├── spec/                       # OpenAPI specification files
│   ├── database-inspector.yaml
│   ├── dbaas.yaml
│   ├── dns.yaml
│   ├── file-browser.yaml
│   ├── Iaas.yaml
│   ├── mail.yaml
│   ├── object-storage.yaml
│   └── paas.yaml
├── docs.json                   # Mintlify documentation configuration
├── index.mdx                   # Documentation landing page
├── docker-compose.yml          # Docker Compose configuration
├── Dockerfile                  # Container build instructions
├── logo.png                    # Liara logo
└── README.md                   # README
```

## 🤝 Contributing

We welcome contributions from the community! Whether you're fixing a typo, improving documentation, or adding new API endpoints, your help is appreciated.

### How to Contribute

#### Step 1: Fork the Repository

Click the "Fork" button at the top right of this page to create a copy of this repository in your GitHub account.

#### Step 2: Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/openapi.git
cd openapi
```

#### Step 3: Create a Branch

Create a descriptive branch name that reflects your changes:

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-bug-fix
# or
git checkout -b docs/your-documentation-update
```

#### Step 4: Make Your Changes

1. **Start the local development environment**

   Choose your preferred environment:

   **For Swagger UI (API specification preview):**
   ```bash
   docker compose up -d
   ```
   Then open [http://localhost:8080](http://localhost:8080) in your browser.

   **For Mintlify (Full documentation preview):**
   ```bash
   npm i -g mint
   mint dev
   ```
   The documentation will open automatically in your browser.

2. **Edit the relevant files**

   - For API specification changes, edit files in the `spec/` directory
   - For documentation changes, edit files in the `pages/` directory or `index.mdx`

3. **Validate your changes**

   - **Swagger UI**: Verify that your changes render correctly and there are no validation errors
   - **Mintlify**: Check that the documentation site builds without errors

4. **Test API endpoints** (if applicable)

   Use the "Try it out" feature in Swagger UI to test API endpoints with your changes.

#### Step 5: Commit Your Changes

```bash
git add .
git commit -m "feat: add new endpoint for listing databases"
# or
git commit -m "fix: correct response schema for DNS records"
# or
git commit -m "docs: update authentication instructions"
```

#### Step 6: Push to Your Fork

```bash
git push origin feature/your-feature-name
```

#### Step 7: Open a Pull Request

1. Navigate to your fork on GitHub
2. Click "Compare & pull request"
3. Fill in the PR template:
   - **Title**: A clear, descriptive title
   - **Description**: Explain what changes you made and why
   - **Related Issues**: Link any related issues (e.g., "Fixes #123")
4. Click "Create pull request"

### Contribution Guidelines

#### OpenAPI Specification Standards

When modifying API specifications, please follow these guidelines:

1. **Use OpenAPI 3.0+ syntax**

   Ensure your specification is compatible with OpenAPI 3.0 or later.

2. **Include complete endpoint documentation**

   ```yaml
   /endpoint:
     get:
       summary: Brief description
       description: Detailed description
       operationId: getEndpoint
       tags:
         - Category
       responses:
         '200':
           description: Successful response
           content:
             application/json:
               schema:
                 $ref: '#/components/schemas/SomeModel'
   ```

3. **Define reusable components**

   Use the `components` section for reusable schemas, parameters, and responses:

   ```yaml
   components:
     schemas:
       Error:
         type: object
         properties:
           code:
             type: integer
           message:
             type: string
   ```

4. **Include examples**

   Provide examples for request bodies and responses:

   ```yaml
   examples:
     ExampleName:
       value:
         id: "123"
         name: "Example"
   ```

### Pull Request Process

1. **Ensure all checks pass** before requesting review
2. **Update documentation** if you change functionality
3. **Request review** from maintainers

## 📚 Resources

- [OpenAPI Specification](https://swagger.io/specification/)
- [Swagger UI Documentation](https://swagger.io/tools/swagger-ui/)
- [Liara Documentation](https://docs.liara.ir)
- [Liara Blog](https://liara.ir/blog)

## 🛠️ Tools We Use

- [Swagger UI](https://swagger.io/docs/specification/v3_0/about/) - API documentation visualization
- [Mintlify](https://www.mintlify.com/docs/) - Documentation platform
- [Docker](https://docs.docker.com/) - Containerization

## 📞 Support

Need help? We're here for you!

- **Documentation**: [https://docs.liara.ir](https://docs.liara.ir)
- **Email**: [info@liara.ir](mailto:info@liara.ir)
- **Website**: [https://liara.ir](https://liara.ir)
- **GitHub Issues**: [Open an issue](https://github.com/liara-cloud/openapi/issues)

---

<p align="center">
  Made with ❤️ by the <a href="https://liara.ir">Liara Team</a>
</p>

<p align="center">
  <a href="https://liara.ir">Website</a> •
  <a href="https://github.com/liara-cloud">GitHub</a> •
  <a href="https://linkedin.com/company/liara-cloud">LinkedIn</a> •
  <a href="https://x.com/liara_cloud">Twitter</a>
</p>
