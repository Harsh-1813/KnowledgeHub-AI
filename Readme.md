# KnowledgeHub AI — Enterprise Knowledge Assistant

An AI-powered enterprise knowledge assistant built with Java and Spring Boot. The goal is to allow users to upload company documents, ask natural-language questions, and receive AI-generated answers grounded in document content with source citations.

**Status:** 🚧 Under active development

## Project Overview

KnowledgeHub AI is designed to solve the problem of searching and understanding large collections of enterprise documents.

The application will use Retrieval-Augmented Generation (RAG) to retrieve relevant document passages and provide contextual answers using a Large Language Model (LLM).

### Planned workflow

1. Users upload PDF or TXT documents.
2. The backend extracts document text.
3. Extracted text is divided into smaller chunks.
4. An embedding model converts chunks into numerical vectors.
5. Embeddings are stored in PostgreSQL using pgvector.
6. Users ask questions in natural language.
7. Relevant document chunks are retrieved using semantic similarity.
8. An AI model generates an answer grounded in the retrieved content.
9. Answers include source citations and relevant excerpts.

## Technology Stack

| Technology | Purpose |
|---|---|
| Java 21 | Programming language |
| Spring Boot 4.1.2 | Backend framework |
| Spring MVC | REST APIs |
| Spring Data JPA | Database persistence |
| Spring AI | AI and LLM integration |
| PostgreSQL | Relational database |
| pgvector | Vector storage and similarity search |
| Flyway | Database migrations |
| Spring Security | Authentication and authorization |
| JWT | Token-based authentication |
| Apache PDFBox | PDF text extraction |
| Maven | Build and dependency management |
| Docker | Containerization |
| JUnit 5 and Mockito | Automated testing |
| React + Vite | Planned frontend |

## Architecture

The project follows a modular monolithic architecture with layered responsibilities.

```text
knowledgehub-ai/
│
├── auth/             # Authentication and authorization
├── users/            # User management
├── documents/        # Document management
├── processing/       # Document extraction and chunking
├── search/           # Semantic search
├── rag/              # Retrieval-augmented generation
├── conversations/    # Chat and conversation history
├── common/           # Shared exceptions and responses
└── config/           # Application configuration
```

### Request flow

```text
Client
  |
  v
Spring Boot REST API
  |
  v
Controller Layer
  |
  v
Service Layer
  |
  +------> PostgreSQL
  |
  +------> Spring AI
                |
                v
          LLM Provider
                |
                v
         Generated Answer
```

## Current Implementation Status

### Milestone 1 — Project Initialization

- [x] Spring Boot Maven project initialization
- [x] Java 21 configuration
- [x] Docker Desktop and WSL 2 setup
- [x] PostgreSQL container using Docker Compose
- [x] Persistent database volume
- [x] pgvector extension enabled
- [x] Flyway database migrations
- [x] Spring Boot PostgreSQL integration
- [x] Actuator health endpoint
- [x] Initial application test
- [x] Maven build verification
- [x] GitHub repository initialization

### Upcoming milestones

- [ ] Milestone 2: Authentication and JWT
- [ ] Milestone 3: Document upload and management
- [ ] Milestone 4: Document processing and embeddings
- [ ] Milestone 5: RAG question answering and citations
- [ ] Milestone 6: Conversations and chat history
- [ ] Milestone 7: Security hardening and integration testing
- [ ] Milestone 8: Docker packaging, CI/CD and documentation
- [ ] Optional React frontend

## Prerequisites

Make sure you have installed:

- Java JDK 21
- Docker Desktop with WSL 2
- IntelliJ IDEA
- Git
- Postman (optional)

Maven is available through the included Maven Wrapper.

## Local Setup

### 1. Clone the repository

```bash
git clone https://github.com/Harsh-1813/KnowledgeHub-AI.git
cd KnowledgeHub-AI
```

### 2. Configure environment variables

Copy `.env.example` to `.env` in the project root.

Configure your local PostgreSQL database name, username and password.

Never commit `.env` or real credentials.

### 3. Start PostgreSQL

```bash
docker compose up -d
```

Check the container:

```bash
docker compose ps
```

### 4. Run the application

On Windows PowerShell:

```powershell
.\mvnw.cmd spring-boot:run
```

### 5. Run tests

```powershell
.\mvnw.cmd clean test
```

To run the complete Maven verification lifecycle:

```powershell
.\mvnw.cmd clean verify
```

## Application Health

Once the application is running, access:

```text
http://localhost:8080/actuator/health
```

Expected response:

```json
{
  "status": "UP"
}
```

## Database Migrations

Flyway manages database schema changes.

Migration files are stored in:

```text
src/main/resources/db/migration/
```

Current migration:

```text
V1__enable_pgvector.sql
```

Future schema changes will be introduced through versioned SQL migration files.

Hibernate is configured to validate the schema rather than automatically modify it.

## Security

Security is a core design consideration.

Planned security features include:

- Password hashing.
- JWT authentication.
- Role-based access control.
- User-level document ownership.
- Protected document retrieval.
- Secure handling of environment variables.
- Protection against unauthorized access to conversations.

## Engineering Principles

The project follows these principles:

- Modular monolithic architecture.
- Separation of controllers, services and repositories.
- DTO-based API contracts.
- Constructor-based dependency injection.
- Centralized exception handling.
- Database migrations through Flyway.
- Automated unit and integration testing.
- Environment-based configuration.
- Secure document processing and retrieval.

## Future Enhancements

- Asynchronous document processing.
- Improved retrieval evaluation.
- Conversation-aware question answering.
- Document-level access controls.
- AI provider abstraction.
- React-based user interface.
- CI/CD with GitHub Actions.
- Production deployment and monitoring.

---

**Author:** Harsh Gupta

**Repository:** [KnowledgeHub AI](https://github.com/Harsh-1813/KnowledgeHub-AI)

*This project is being developed incrementally as a hands-on Java backend engineering portfolio project.*