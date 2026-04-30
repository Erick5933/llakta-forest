# Llakta Forest 🌱

> Reforestation management platform born from the 2024 wildfires at Parque Nacional El Cajas, Cuenca, Ecuador. Volunteers register planted trees with GPS coordinates, admins manage affected zones, and the system tracks recovery progress in real time — designed to eventually integrate drone-mapped burn areas for precision reforestation.

---

## The problem it solves

In 2024, wildfires devastated large areas of Parque Nacional El Cajas in the Azuay region of Ecuador. The response required coordinating dozens of volunteers across multiple affected zones — but there was no system to track which areas had been replanted, which species were used, or how recovery was progressing over time.

Llakta Forest was built to solve exactly that. Volunteers can mark each tree they plant with GPS coordinates directly from their phone. Administrators manage the affected zones, set reforestation goals, and monitor real-time recovery progress per area. Sponsors and institutions can track the impact of their contributions.

**Future vision:** integrate drone flight data to automatically map newly burned or deforested areas, feed those coordinates into the system, and generate prioritized replanting task lists for ground volunteers — closing the loop from aerial detection to physical reforestation.

---

## Tech stack

| Layer | Technology |
|---|---|
| Backend | Spring Boot 3.4.1 (Java 17) |
| Web layer | Spring MVC + Thymeleaf |
| REST API | Spring Web + Jackson |
| Database | MySQL + Spring Data JPA / Hibernate |
| Validation | Spring Boot Validation |
| Reports | OpenPDF (PDF generation) |
| Image handling | imgscalr |
| API docs | SpringDoc OpenAPI / Swagger UI |
| Build | Maven |

---

## Architecture

```
src/main/java/com/example/demo/
├── controllers/           # MVC controllers — web views (Thymeleaf)
├── restcontroller/        # REST API endpoints — JSON responses
├── controladorReportes/   # PDF report generation
├── service/               # Business logic layer
├── serviceMovil/          # Mobile-optimized service endpoints
├── dao/                   # Data Access Objects
├── repository/            # Spring Data JPA repositories
├── entity/                # JPA entities — database models
├── dto/                   # Data Transfer Objects
└── util/                  # Utilities and helpers
```

The system exposes both MVC web views (Thymeleaf) and REST endpoints — the REST layer (`restcontroller/` + `serviceMovil/`) was built specifically to support mobile clients alongside the web app.

---

## Key features

**Affected zone management**
- Administrators register fire-affected or deforested areas with geographic coordinates
- Each zone tracks: location, area size, target tree species, planting goal, start/end dates, and recovery status (active / completed / cancelled)

**Tree registration with geolocation**
- Volunteers log each planted tree: species, date, exact GPS coordinates
- Real-time statistics: total trees planted per zone, % progress toward recovery goal

**Interactive maps**
- Visual map of active reforestation zones
- Distribution of planted trees across affected areas

**Volunteer coordination**
- Sign up for reforestation activities
- View scheduled events, locations, and attendance
- Confirm participation

**Reports & export**
- Auto-generated PDF progress reports per zone
- Volunteer participation summaries
- Exportable data for institutions and sponsors

**Role-based access**
- Administrator: full project and user management
- Volunteer: tree logging, activity enrollment, attendance confirmation
- Sponsor: read-only dashboard with impact statistics

**API documentation**
- Swagger UI available at `/swagger-ui.html` when running locally

---

## Getting started

### Prerequisites
- Java 17+
- Maven 3.8+
- MySQL running locally

### Run locally

```bash
git clone https://github.com/Erick5933/llakta-forest
cd llakta-forest

# Configure your database
# Edit src/main/resources/application.properties:
# spring.datasource.url=jdbc:mysql://localhost:3306/llakta_forest
# spring.datasource.username=your_user
# spring.datasource.password=your_password
# spring.jpa.hibernate.ddl-auto=update

mvn spring-boot:run
```

App runs at `http://localhost:8080`  
API docs at `http://localhost:8080/swagger-ui.html`

---

## Non-functional requirements

- REST API responses average < 1 second
- Supports 100+ concurrent users
- Android-compatible REST endpoints (serviceMovil layer)
- Compatible with Chrome, Firefox, Edge
- Role-based permissions enforced at service and controller layers
- Sensitive data storage with encryption

---

## Project context

This project was developed in response to the 2024 wildfires at Parque Nacional El Cajas in Cuenca, Ecuador — one of the most biodiverse high-altitude wetland ecosystems in South America. The goal was to build a real tool that local conservation organizations and volunteer groups could use to coordinate and track reforestation efforts across affected areas.

The project was built using Scrum methodology, with one Scrum Master (Erick Chacón) coordinating multiple development teams across an entire student cohort at Instituto Tecnológico del Azuay. The system was designed from 14 user stories across 2 development iterations.

The long-term vision includes integrating autonomous drone surveys to automatically detect and map newly burned zones, feeding those coordinates directly into the platform so ground teams can receive prioritized, GPS-guided replanting assignments — connecting aerial intelligence with on-the-ground action.

---

## Authors

Built in response to the 2024 El Cajas wildfires — Cuenca, Ecuador (2024)  
Scrum Master & Lead Developer: Erick Chacón
