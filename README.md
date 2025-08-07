# ✈️ Jet-Set-Go – Travel Itinerary Backend App

**Jet-Set-Go** is a Spring Boot-powered backend application that enables seamless travel itinerary management with secure user authentication, itinerary history tracking, and full support for AI-generated travel plans.

---

## 🌟 Key Features

- 🔐 **JWT-based User Authentication**
- 📅 **Create, View, and Delete Travel Itineraries**
- 🧠 **Store Full AI-Generated Itineraries**
- 📜 **User Itinerary History**
- 🔎 **Search Itineraries by Keyword**
- 🌐 **RESTful API Design**

---

## 🧰 Tech Stack

| Layer       | Technology             |
|-------------|------------------------|
| Backend     | Spring Boot (Java)     |
| Security    | Spring Security + JWT  |
| Database    | MySQL                  |
| Build Tool  | Maven                  |
| API Format  | JSON (Wrapped in `ApiResponse<T>`) |

---

## 🗂️ Database Schema

### 🧑 User Table

| Field          | Type        |
|----------------|-------------|
| id             | Primary Key |
| username       | String      |
| email          | String      |
| password       | String      |
| firstName      | String      |
| lastName       | String      |
| phoneNumber    | String      |
| role           | String      |
| enabled        | Boolean     |
| createdAt      | Timestamp   |
| updatedAt      | Timestamp   |

### 📍 Itinerary Table

| Field           | Type        |
|------------------|-------------|
| id               | Primary Key |
| user_id          | Foreign Key |
| destination      | String      |
| title            | String      |
| description      | String      |
| fullItinerary    | TEXT        |
| startDate        | Date        |
| endDate          | Date        |
| numberOfDays     | Integer     |
| budgetRange      | String      |
| travelStyle      | String      |
| createdAt        | Timestamp   |
| updatedAt        | Timestamp   |

---

## 📡 API Endpoints

### 🔐 Authentication

| Method | Endpoint             | Description         |
|--------|----------------------|---------------------|
| POST   | `/api/auth/signup`   | Register a user     |
| POST   | `/api/auth/login`    | Login and get token |

### 🧳 Itineraries

| Method | Endpoint                                                                 | Description                 |
|--------|--------------------------------------------------------------------------|-----------------------------|
| POST   | `/api/itineraries?userId={userId}`                                       | Save a new itinerary        |
| GET    | `/api/itineraries?userId={userId}`                                       | Get all itineraries for user|
| GET    | `/api/itineraries/{itineraryId}?userId={userId}`                        | Get specific itinerary      |
| GET    | `/api/itineraries/search?userId={userId}&searchTerm={term}`             | Search itineraries          |
| DELETE | `/api/itineraries/{itineraryId}?userId={userId}`                        | Delete an itinerary         |

---

## ⚙️ Setup Instructions

### 🔧 Database Setup

1. Install MySQL and create a database.
2. Update `application.properties` with your DB credentials:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/jetsetgo
   spring.datasource.username=yourUsername
   spring.datasource.password=yourPassword

{
  "destination": "Paris, France",
  "title": "Weekend in Paris",
  "description": "A romantic weekend getaway",
  "fullItinerary": "Complete AI-generated itinerary details...",
  "startDate": "2024-06-15",
  "endDate": "2024-06-17",
  "numberOfDays": 3,
  "budgetRange": "1000-2000",
  "travelStyle": "Luxury"
}


{
  "success": true,
  "data": {
    "id": 1,
    "destination": "Paris, France",
    "title": "Weekend in Paris",
    "description": "A romantic weekend getaway",
    "fullItinerary": "Complete AI-generated itinerary details...",
    "startDate": "2024-06-15",
    "endDate": "2024-06-17",
    "numberOfDays": 3,
    "budgetRange": "1000-2000",
    "travelStyle": "Luxury",
    "createdAt": "2024-01-15T10:30:00",
    "updatedAt": "2024-01-15T10:30:00"
  },
  "message": null
}
