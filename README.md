# ⚖️ Advocate Case Management System

A full-stack web application designed for legal professionals to manage cases, clients, hearings, expenses, and payments — all in one place.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 19, Vite, React Router DOM v7 |
| Backend | Java 21, Spring Boot 3.5.6 |
| Database | MySQL 8 |
| Auth | JWT (JSON Web Tokens) |
| Styling | Custom CSS modules |
| HTTP Client | Axios |
| Calendar | React Big Calendar |
| PDF Export | jsPDF |
| ORM | Spring Data JPA / Hibernate |

---

## 📁 Project Structure

```
advocate-case-management/
├── Advocate-app-BE-main/          # Spring Boot Backend
│   ├── src/main/java/advocate/com/advocate_app/
│   │   ├── controller/            # REST API Controllers
│   │   ├── entity/                # JPA Entity classes
│   │   ├── repository/            # Spring Data Repositories
│   │   ├── service/               # Business Logic
│   │   └── security/              # JWT Utility
│   └── src/main/resources/
│       ├── application.properties
│       └── static/                # Built frontend (for deployment)
│
└── Advocate-app-FE-main/          # React Frontend
    ├── src/
    │   ├── pages/                 # Page components (Dashboard, Cases, Calendar…)
    │   ├── assets/styles/         # CSS per page
    │   └── utils/                 # Auth helpers (JWT decode, logout)
    └── public/
```

---

## ✨ Features

- 🔐 **Authentication** — Secure signup / login with JWT; auto-logout on token expiry
- 📋 **Case Management** — Create, update, and track legal cases with status and court details
- 👥 **Client Management** — Add and manage clients linked to their cases
- 📅 **Calendar & Events** — Schedule hearings and case events on an interactive calendar
- 💰 **Expense Tracking** — Log and categorize case-related expenses
- 💳 **Payment Management** — Track client payments against cases
- 🔔 **Notifications** — Automated notification scheduler for upcoming events
- 📄 **PDF Export** — Export case or expense data as PDF using jsPDF

---

## ⚙️ Backend Setup

### Prerequisites
- Java 21+
- Maven 3.8+
- MySQL 8+

### 1. Configure the Database

Create a MySQL database:
```sql
CREATE DATABASE advocate_db;
```

### 2. Update `application.properties`

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/advocate_db
spring.datasource.username=YOUR_DB_USERNAME
spring.datasource.password=YOUR_DB_PASSWORD

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
```

> ⚠️ **Never commit real credentials to GitHub.** Use environment variables or a `.env` file.

### 3. Run the Backend

```bash
cd Advocate-app-BE-main
./mvnw spring-boot:run
```

Backend runs at: `http://localhost:8080`

---

## 🖥️ Frontend Setup

### Prerequisites
- Node.js 18+
- npm

### 1. Install Dependencies

```bash
cd Advocate-app-FE-main
npm install
```

### 2. Run Development Server

```bash
npm run dev
```

Frontend runs at: `http://localhost:5173`

### 3. Build for Production

```bash
npm run build
```

Copy the generated `dist/` folder into `Advocate-app-BE-main/src/main/resources/static/` to serve the full app from Spring Boot alone.

---

## 🔗 API Overview

| Module | Base Endpoint |
|---|---|
| Advocate (Auth) | `/api/advocate` |
| Cases | `/api/cases` |
| Case Events | `/api/case-events` |
| Clients | `/api/clients` |
| Payments | `/api/payments` |
| Expenses | `/api/expenses` |
| Notifications | `/api/notifications` |

---

## 🔒 Security

- JWT tokens are stored in `localStorage` and sent via `Authorization: Bearer <token>` headers
- Protected routes on the frontend automatically redirect unauthenticated users to `/login`
- Token expiry is checked client-side on every protected route access

---

## 🚀 Deployment (Single JAR)

1. Build the React frontend: `npm run build`
2. Copy `dist/` → `src/main/resources/static/`
3. Build the Spring Boot JAR: `./mvnw clean package`
4. Run: `java -jar target/advocate-app-0.0.1-SNAPSHOT.jar`

The entire app (frontend + backend) is served from a single JAR on port `8080`.

---

## 🤝 Contributing

1. Fork this repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 👨‍💻 Developer

Built by **CHILL-CODING**  
Full-Stack Developer | Java · Spring Boot · React · MySQL

---

## 📄 License

This project is for educational and portfolio purposes.
