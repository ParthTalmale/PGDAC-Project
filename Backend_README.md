# MediConnect Backend Documentation

**Original Organization:** [https://github.com/mediconnect-team](https://github.com/mediconnect-team)  
*Note: This is the official codebase for the MediConnect project. All development history and collaboration took place in the main organization repository linked above. This represents the final consolidated backend state.*

---

## 📅 Development Timeline (Backend Phase)

The backend development was executed over a dedicated 20-day sprint, focusing on security, database integrity, and API robustness.

### Week 1: Foundation & Architecture (Days 11-15)
*   **Day 11:** Initialized Spring Boot Project with Maven. Configured `application.properties` for MySQL connectivity.
*   **Day 12:** Designed Database Schema (ER Diagram implementation). Created Entity classes (`User`, `Doctor`, `Patient`, `Appointment`).
*   **Day 13:** Implemented Validation Layer using `@Valid` and global `GlobalExceptionHandler`.
*   **Day 14:** Developed `UserRepository` and basic CRUD operations for Patient Registration.
*   **Day 15:** Set up Swagger/OpenAPI 3.0 configuration for API documentation.

### Week 2: Core Logic & Security (Days 16-22)
*   **Day 16:** Integrated **Spring Security**. Implemented `UserDetailsService` for DB-based authentication.
*   **Day 17:** Implemented **JWT (JSON Web Token)** filter. Added `JwtUtils` for token generation and validation.
*   **Day 18:** Secured endpoints with Role-Based Access Control (`@PreAuthorize("hasRole('ADMIN')")`).
*   **Day 19:** Developed Doctor Module: `DoctorService` for schedule management and profile updates.
*   **Day 20:** Developed Patient Module: Search functionality and Slot booking logic (`AppointmentService`).
*   **Day 21:** Implemented Email Notification Service using JavaMailSender (Async execution).
*   **Day 22:** Performance optimization: Added Indexing to commonly queried columns.

### Week 3: Payment & Integration (Days 23-28)
*   **Day 23:** Researched Payment Gateway options. Selected **Razorpay**.
*   **Day 24:** Implemented `BillingService`. Created order generation logic.
*   **Day 25:** Implemented Signature Verification logic (HMAC SHA256) to prevent payment tampering.
*   **Day 26:** Dockerization: Created `Dockerfile` and initial `docker-compose.yml`.
*   **Day 27:** Integration Testing using Postman. Verified full flow: Auth -> Search -> Book -> Pay.
*   **Day 28:** Bug Fixing: Resolved CORS issues and Date Format inconsistencies.

### Week 4: Finalization (Days 29-30)
*   **Day 29:** Admin Dashboard APIs: Aggregated statistics calculations.
*   **Day 30:** Final Code Review, Refactoring, and polished Logic comments.

---

## 🧪 Testing & Validation

All endpoints were rigorously tested using JUnit and Postman.

| Component | Test Scenario | Outcome |
| :--- | :--- | :--- |
| **Auth** | Login with invalid credentials | ✅ Returns 401 Unauthorized |
| **Auth** | Login with valid credentials | ✅ Returns JWT Token |
| **Security** | Access Admin Routes as Patient | ✅ Returns 403 Forbidden |
| **Booking** | Book an already occupied slot | ✅ Returns 409 Conflict |
| **Payment** | Verify tampered signature | ✅ Payment Rejected |
| **Payment** | Verify valid signature | ✅ Payment Success & Appointment Confirmed |
| **Data** | Register with duplicate Email | ✅ Returns 400 Bad Request |

---

## 🛠️ Tech Stack
*   **Framework:** Spring Boot 3
*   **Language:** Java 21
*   **Database:** MySQL 8.0
*   **Security:** Spring Security 6 + JWT
*   **Build Tool:** Maven

---
*Developed by MediConnect Team*
