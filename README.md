# 📊 FinSight-Engine-AI-Finance-Intelligence-Backend
 (Backend – Microservices)

A **microservice-based finance tracker backend** designed for **mobile applications**, focused on **automatic expense tracking** using **AI-driven SMS parsing**.

The system securely authenticates users, processes raw bank SMS messages using a **Large Language Model (LLM)**, extracts structured transaction data, and stores it using an **event-driven architecture powered by Kafka**.

> ⚠️ **Frontend / Android application** is intentionally not included due to hardware limitations.  
> This repository focuses purely on **backend architecture, scalability, and real-world system design**.

---

## 🎯 Project Objectives

- Eliminate manual expense entry  
- Automatically track transactions from bank SMS  
- Handle unstructured SMS formats reliably using AI  
- Build a scalable, decoupled microservice architecture  
- Provide a strong backend foundation for a mobile finance app  

---

## 🚀 Core Features

### 🔐 Authentication Service
- JWT-based authentication  
- Refresh token mechanism  
- Secure token rotation  
- Stateless access token validation  
- Publishes authentication events to Kafka  

---

### 👤 User Service
- Maintains user profile and preferences  
- Listens to authentication events  
- Decoupled from Auth Service using Kafka  
- Stores user-specific metadata  

---

### 🤖 AI-Based SMS Transaction Parsing Service
- Accepts raw SMS messages from the client  
- Uses **LLM (Grok API)** to:
  - Identify whether SMS represents a valid transaction  
  - Extract amount, currency, merchant, and transaction type  
- Handles inconsistent and multi-bank SMS formats  
- Publishes parsed transaction events to Kafka  

---

### 💰 Transaction Service
- Consumes parsed transaction events  
- Stores structured financial data  
- Maintains user expense history  
- Designed for future analytics and reporting  

---

### 🔄 Event-Driven Architecture
- Apache Kafka for asynchronous communication  
- Loose coupling between services  
- Improved scalability and fault isolation  
- Event replay capability  

---

### 🐳 Containerized Setup
- Fully Dockerized using Docker Compose  
- One-command local startup  
- Environment-agnostic deployment  

---

## 🏗️ System Architecture


Each service owns its database and communicates asynchronously via Kafka.

---

## 🔄 End-to-End Data Flow

1. User logs in and receives JWT + Refresh token  
2. Auth Service publishes authentication event  
3. User Service consumes event and manages user profile  
4. Raw SMS message is sent to LLM Parsing Service  
5. LLM validates and extracts transaction details  
6. Parsed transaction event is published to Kafka  
7. Transaction Service stores data in database  

---

## 🧠 LLM Integration

- **LLM Provider:** Grok  
- **Integration Method:** API Key  

### Responsibilities
- Natural language understanding of bank SMS  
- Transaction validation  
- Entity extraction (amount, merchant, currency)  

### Why LLM instead of Regex?
- Bank SMS formats are inconsistent  
- Regex is brittle and unscalable  
- LLM provides semantic understanding and adaptability  

---

## 🛠️ Tech Stack

- **Backend Framework:** Spring Boot (Microservices)  
- **Authentication:** JWT + Refresh Tokens  
- **Messaging:** Apache Kafka  
- **AI / NLP:** Grok LLM API  
- **Databases:** Service-specific databases  
- **Containerization:** Docker, Docker Compose  
- **Communication:** REST APIs + Kafka Events  

---

## 📂 Project Structure

=======
📊 AI-Powered Finance Tracker (Backend – Microservices)
A microservice-based finance tracker backend designed for mobile applications, focused on automatic expense tracking using AI-driven SMS parsing.

The system securely authenticates users, processes raw bank SMS messages using a Large Language Model (LLM), extracts structured transaction data, and stores it using an event-driven architecture powered by Kafka.

⚠️ Frontend / Android application is intentionally not included due to hardware limitations.
This repository focuses purely on backend architecture, scalability, and real-world system design.

🎯 Project Objectives
Eliminate manual expense entry

Automatically track transactions from bank SMS

Handle unstructured SMS formats reliably using AI

Build a scalable, decoupled microservice architecture

Provide a strong backend foundation for a mobile finance app

🚀 Core Features
🔐 Authentication Service
JWT-based authentication

Refresh token mechanism

Secure token rotation

Stateless access token validation

Publishes authentication events to Kafka

👤 User Service
Maintains user profile and preferences

Listens to authentication events

Decoupled from Auth Service using Kafka

Stores user-specific metadata

🤖 AI-Based SMS Transaction Parsing Service
Accepts raw SMS messages from the client

Uses LLM (Grok API) to:

Identify whether SMS represents a valid transaction

Extract amount, currency, merchant, and transaction type

Handles inconsistent and multi-bank SMS formats

Publishes parsed transaction events to Kafka

💰 Transaction Service
Consumes parsed transaction events

Stores structured financial data

Maintains user expense history

Designed for future analytics and reporting

🔄 Event-Driven Architecture
Apache Kafka for asynchronous communication

Loose coupling between services

Improved scalability and fault isolation

Event replay capability

🐳 Containerized Setup
Fully Dockerized using Docker Compose

One-command local startup

Environment-agnostic deployment

🏗️ System Architecture
Mobile Client (Future)
↓
Auth Service → Kafka → User Service

Raw SMS Input
↓
LLM Parsing Service → Kafka → Transaction Service

Each service owns its database and communicates asynchronously via Kafka.

🔄 End-to-End Data Flow
User logs in and receives JWT + Refresh token

Auth Service publishes authentication event

User Service consumes event and manages user profile

Raw SMS message is sent to LLM Parsing Service

LLM validates and extracts transaction details

Parsed transaction event is published to Kafka

Transaction Service stores data in database

🧠 LLM Integration
LLM Provider: Grok

Integration Method: API Key

Responsibilities:

Natural language understanding of bank SMS

Transaction validation

Entity extraction (amount, merchant, currency)

Why LLM instead of Regex?

Bank SMS formats are inconsistent

Regex is brittle and unscalable

LLM provides semantic understanding and adaptability

🛠️ Tech Stack
Backend Framework: Spring Boot (Microservices)
Authentication: JWT + Refresh Tokens
Messaging: Apache Kafka
AI / NLP: Grok LLM API
Databases: Service-specific databases
Containerization: Docker, Docker Compose
Communication: REST APIs + Kafka Events

📂 Project Structure
>>>>>>> e718c72 (Add dsService as normal service module)
finance-tracker
├── auth-service
├── user-service
├── llm-service
├── transaction-service
├── docker-compose.yml
└── README.md

<<<<<<< HEAD

---

## ▶️ Running the Project Locally

### Prerequisites
- Docker  
- Docker Compose  
- Java 17+  

### Start All Services
```bash
docker-compose up --build
=======
▶️ Running the Project Locally
Prerequisites
Docker

Docker Compose

Java 17+

Start All Services
docker-compose up --build

All services will start and communicate internally via Kafka.

🔐 Environment Configuration
Each service uses environment variables for sensitive configuration:

JWT secrets

Refresh token expiry

Grok API key

Database credentials

Do not commit .env files or secrets to version control.

📈 Future Enhancements
Monthly and yearly expense analytics

Category-wise expense classification

Budget alerts and spending insights

Mobile app integration

Export transactions (PDF / CSV)

Rate limiting and circuit breakers

Fraud detection using AI

🧑‍💻 Author
Varun Patil
Backend Engineer
Java | Spring Boot | Microservices | Kafka | AI Integration

⭐ Project Significance
Solves a real-world financial tracking problem

Demonstrates production-grade microservice architecture

Uses event-driven design with Kafka

Integrates AI in a practical, non-gimmicky way

Built with scalability and maintainability in mind

This project reflects industry-level backend engineering, not a tutorial implementation.
>>>>>>> e718c72 (Add dsService as normal service module)
