# 🏥 MediCore — Hospital Management System

A full-stack hospital management application built with **Spring Boot 3.2**, **React 18**, and **PostgreSQL**.

---

## 📋 Tech Stack

| Layer     | Technology                          |
|-----------|-------------------------------------|
| Backend   | Spring Boot 3.2, JDK 21             |
| Database  | PostgreSQL                          |
| ORM       | Spring Data JPA / Hibernate         |
| Frontend  | React 18, React Router v6           |
| HTTP      | Axios                               |
| UI        | Custom CSS (no component library)   |

---

## 🗂️ Project Structure

```
hospital-management/
├── backend/                      # Spring Boot application
│   ├── src/main/java/com/hospital/
│   │   ├── entity/               # JPA entities
│   │   ├── repository/           # Spring Data repositories
│   │   ├── service/              # Business logic
│   │   ├── controller/           # REST controllers
│   │   ├── dto/                  # Data Transfer Objects
│   │   └── config/               # CORS configuration
│   └── src/main/resources/
│       └── application.properties
└── frontend/                     # React application
    └── src/
        ├── pages/                # Dashboard, Patients, Doctors, etc.
        ├── components/           # Modal, ConfirmDialog
        └── services/             # API (axios)
```

---

## ⚙️ Prerequisites

- **JDK 21** (IntelliJ IDEA bundled or download from [Adoptium](https://adoptium.net))
- **PostgreSQL** running on `localhost:5432`
- **Node.js 18+** and **npm**
- **IntelliJ IDEA** (Community or Ultimate)

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/hospital-management.git
cd hospital-management
```

### 2. Set up PostgreSQL

Make sure PostgreSQL is running and the `postgres` database exists (it does by default).

The app uses:
```
URL:      jdbc:postgresql://localhost:5432/postgres
Username: postgres
Password: root
```

Tables are **auto-created** by Hibernate on first run (`ddl-auto=update`).

### 3. Run the Backend

**Option A — IntelliJ IDEA:**
1. Open IntelliJ → **File → Open** → select the `backend/` folder
2. Wait for Maven to sync dependencies
3. Run `HospitalManagementApplication.java`
4. Backend starts on **http://localhost:8080**

**Option B — Maven CLI:**
```bash
cd backend
./mvnw spring-boot:run
```

### 4. Run the Frontend

```bash
cd frontend
npm install
npm start
```

Frontend starts on **http://localhost:3000** and proxies API calls to `localhost:8080`.

---

## 📡 REST API Endpoints

| Resource     | Method | URL                              | Description          |
|--------------|--------|----------------------------------|----------------------|
| Dashboard    | GET    | `/api/dashboard`                 | Stats overview       |
| Patients     | GET    | `/api/patients`                  | List all             |
| Patients     | GET    | `/api/patients?search=name`      | Search by name       |
| Patients     | POST   | `/api/patients`                  | Create               |
| Patients     | PUT    | `/api/patients/{id}`             | Update               |
| Patients     | DELETE | `/api/patients/{id}`             | Delete               |
| Doctors      | GET    | `/api/doctors`                   | List all             |
| Doctors      | POST   | `/api/doctors`                   | Create               |
| Doctors      | PUT    | `/api/doctors/{id}`              | Update               |
| Doctors      | DELETE | `/api/doctors/{id}`              | Delete               |
| Departments  | GET    | `/api/departments`               | List all             |
| Departments  | POST   | `/api/departments`               | Create               |
| Departments  | PUT    | `/api/departments/{id}`          | Update               |
| Departments  | DELETE | `/api/departments/{id}`          | Delete               |
| Appointments | GET    | `/api/appointments`              | List all             |
| Appointments | POST   | `/api/appointments`              | Book                 |
| Appointments | PUT    | `/api/appointments/{id}`         | Update               |
| Appointments | PATCH  | `/api/appointments/{id}/status`  | Update status only   |
| Appointments | DELETE | `/api/appointments/{id}`         | Delete               |
| Insurance    | GET    | `/api/insurances`                | List all             |
| Insurance    | POST   | `/api/insurances`                | Create               |
| Insurance    | PUT    | `/api/insurances/{id}`           | Update               |
| Insurance    | DELETE | `/api/insurances/{id}`           | Delete               |

---

## 🗄️ Database Schema

Matches the ER diagram exactly:

- **PATIENT** — id, name, gender, birthDate, email, bloodGroup, createdAt, insurance_id (FK)
- **DOCTOR** — id, name, specialization, email, createdAt
- **DEPARTMENT** — id, name, createdAt, head_doctor_id (FK)
- **APPOINTMENT** — id, appointmentTime, reason, status, doctor_id (FK), patient_id (FK)
- **INSURANCE** — id, policyNumber, provider, validUntil, createdAt
- **DOCTOR_DEPARTMENT** — doctor_id (PK,FK), department_id (PK,FK)

---

## 🌐 Deploying to GitHub

```bash
cd hospital-management
git init
git add .
git commit -m "Initial commit: MediCore Hospital Management System"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/hospital-management.git
git push -u origin main
```

---

## ✅ Features

- 📊 **Dashboard** — live counts for all entities
- 🧑‍⚕️ **Patients** — register, edit, delete, search; link to insurance
- 👨‍⚕️ **Doctors** — CRUD; assign to multiple departments
- 🏥 **Departments** — CRUD; assign head doctor; shows doctor count
- 📅 **Appointments** — book, filter by status, mark complete/cancelled
- 🛡️ **Insurance** — manage policies; expiry detection

---

## 📝 License

MIT
