# Airbnb Clone Project

The **Airbnb Clone Project** is a comprehensive application designed to simulate a booking platform similar to Airbnb.  
It focuses on **backend systems, database design, API development, security, and CI/CD pipelines**, giving learners real-world experience in building scalable web applications.

---

## 📌 Team Roles & Responsibilities

### Business Analyst (BA)
- Understands customer processes and workflows.  
- Translates abstract business needs into clear requirements.  
- Acts as a bridge between stakeholders and the development team.  

### Product Owner (PO)
- Owns product vision and strategy.  
- Prioritizes backlog to maximize business value.  
- Balances customer needs with business goals.  

### Project Manager (PM)
- Ensures delivery within scope, time, and budget.  
- Manages risks and motivates the team.  
- Maintains communication across teams.  

### UI/UX Designer
- Designs user-friendly and visually appealing interfaces.  
- Crafts seamless user journeys.  
- Builds wireframes, prototypes, and conducts user research.  

### Software Architect
- Defines high-level architecture and technical design.  
- Chooses platforms, frameworks, and integrations.  
- Establishes coding standards and performs reviews.  

### Software Developer
- Implements features and fixes issues.  
- Frontend: builds user interfaces.  
- Backend: builds APIs and core logic.  
- Full-stack: manages both ends.  

### QA Engineer
- Ensures software quality through testing.  
- Performs functional, usability, security, and performance testing.  
- Documents defects and testing coverage.  

### Test Automation Engineer
- Builds automation frameworks.  
- Creates scripts for fast, reliable testing.  
- Identifies test cases for automation.  

### DevOps Engineer
- Builds CI/CD pipelines.  
- Automates deployments and ensures system reliability.  
- Bridges development and operations teams.  

---

## ⚙️ Technology Stack

### Backend
- **Django**: High-level Python framework for authentication, ORM, and APIs.  
- **FastAPI** (alternative): Async-first Python framework for REST APIs.  

### Database
- **PostgreSQL**: Relational DBMS for storing users, properties, bookings, payments, and reviews.  

### API Layer
- **GraphQL**: Query language allowing clients to fetch only required data in flexible queries.  

### CI/CD & Deployment
- **GitHub Actions**: Automated workflows (tests, linting, deployment).  
- **Docker**: Containerized application environments.  
- **NGINX**: Reverse proxy and static file server.  
- **pytest/Django Test Framework**: Automated testing.  

---

## 🗄️ Database Design

### Entities & Attributes

#### User
- **PK**: `user_id` (UUID)  
- `first_name`, `last_name` (NOT NULL)  
- `email` (UNIQUE, NOT NULL)  
- `password_hash` (NOT NULL)  
- `phone_number` (optional)  
- `role` (ENUM: guest, host, admin)  
- `created_at` (timestamp)  

#### Property
- **PK**: `property_id` (UUID)  
- **FK**: `host_id` → User(user_id)  
- `name`, `description`, `location` (NOT NULL)  
- `pricepernight` (DECIMAL, NOT NULL)  
- `created_at`, `updated_at`  

#### Booking
- **PK**: `booking_id` (UUID)  
- **FK**: `property_id` → Property(property_id)  
- **FK**: `user_id` → User(user_id)  
- `start_date`, `end_date` (DATE, NOT NULL)  
- `total_price` (DECIMAL)  
- `status` (ENUM: pending, confirmed, canceled)  
- `created_at`  

#### Payment
- **PK**: `payment_id` (UUID)  
- **FK**: `booking_id` → Booking(booking_id)  
- `amount`, `payment_method`  
- `payment_date`  

#### Review
- **PK**: `review_id` (UUID)  
- **FK**: `property_id` → Property(property_id)  
- **FK**: `user_id` → User(user_id)  
- `rating` (1–5), `comment`  
- `created_at`  

#### Message
- **PK**: `message_id` (UUID)  
- **FK**: `sender_id` → User(user_id)  
- **FK**: `recipient_id` → User(user_id)  
- `message_body`  
- `sent_at`  

---

## 🔗 Relationships

- **User (host) 1—N Property**  
- **User (guest) 1—N Booking**  
- **Property 1—N Booking**  
- **Booking 1—N Payment**  
- **User 1—N Review**  
- **Property 1—N Review**  
- **User 1—N Message (sender & recipient)**  

---

## 🚀 Feature Breakdown

### 👤 User Management
- Signup/login with role-based access.  
- Manage personal profiles.  

### 🏠 Property Management
- Hosts can create and update property listings.  
- Manage pricing, description, and availability.  

### 📅 Booking System
- Guests book properties with start and end dates.  
- Supports booking statuses.  

### 💳 Payment Processing
- Secure transactions with providers (Stripe, PayPal, etc.).  
- Manages payment statuses (paid, refunded, failed).  

### ⭐ Reviews & Ratings
- Guests leave reviews for properties they booked.  
- Builds trust and feedback loop.  

### ❤️ Favorites / Wishlists
- Guests save properties for later.  

### 🔍 Search & Filtering
- Search by location, price, and availability.  

---

## 🔒 API Security

- **Least Privilege**: Minimal access tokens.  
- **Defense in Depth**: Security at app, API, DB, infra levels.  
- **Secure Defaults**: Strong defaults for cookies, headers, and timeouts.  

---

## ⚡ CI/CD Pipeline

### What is CI/CD?
- **Continuous Integration (CI)**: Auto builds & tests for every change.  
- **Continuous Deployment (CD)**: Auto deploys to staging/production.  

### Benefits
- Faster development cycles.  
- Higher code quality.  
- Reliable, automated deployments.  
- Reduced human error.  

### Tools
- GitHub Actions → Automated testing & deployment.  
- Docker → Consistent app environments.  
- NGINX → Reverse proxy.  
- pytest/Django Test Framework → Automated testing.  

---

## 📖 About
A full-stack **Airbnb clone** project with focus on:  
- Realistic **database design**  
- Clean **architecture & APIs**  
- Secure **payments & bookings**  
- Modern **DevOps practices**