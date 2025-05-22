# Vehicle Parking Management System

## Introduction
This document outlines the Low-Level Design (LLD) for a **Vehicle Parking Management System** that facilitates efficient parking slot management, vehicle entry/exit logging, reservations, and billing operations. The system aims to streamline both visitor and subscriber parking operations in real time. It supports backend development using **Java (Spring Boot)** and **.NET (ASP.NET Core)** frameworks.

---

## Module Overview

### 1. User Management
**Features:**
- User registration and login.
- Role-based access for admins, staff, and customers.

**Entities:**
- **User**:  
    - `UserID`, `Name`, `Email`, `Phone`, `Role`, `Password (hashed)`.

---

### 2. Parking Slot Management
**Features:**
- Add, remove, and update parking slots.
- Real-time availability tracking.

**Entities:**
- **ParkingSlot**:  
    - `SlotID`, `Type (2W/4W)`, `IsOccupied`, `Location`.

---

### 3. Vehicle Entry & Exit Logging
**Features:**
- Log vehicle entry and exit.
- Calculate parking duration and update slot occupancy.

**Entities:**
- **VehicleLog**:  
    - `LogID`, `VehicleNumber`, `EntryTime`, `ExitTime`, `SlotID`, `UserID`.

---

### 4. Reservation System
**Features:**
- View slot availability and reserve slots.
- Modify or cancel reservations.

**Entities:**
- **Reservation**:  
    - `ReservationID`, `UserID`, `SlotID`, `VehicleNumber`, `StartTime`, `EndTime`, `Status`.

---

### 5. Billing and Payments
**Features:**
- Generate bills dynamically based on parking duration and vehicle type.
- Support multiple payment methods.

**Entities:**
- **Invoice**:  
    - `InvoiceID`, `UserID`, `Amount`, `PaymentMethod`, `Status`, `Timestamp`.

---

## Architecture Overview

### 1. Architectural Style
- **Frontend**: Angular or React.
- **Backend**: REST API-based.
- **Database**: Relational (MySQL/SQL Server).

### 2. Component Interaction
- Frontend communicates with backend APIs.
- Backend handles business logic and data operations.
- Database stores persistent data like user information, reservations, and invoices.

---

## Deployment Strategy

### 1. Local Development
- Frontend served via Angular CLI or React dev server.
- Backend run with Spring Boot or .NET CLI.
- Database setup using local MySQL/PostgreSQL/SQL Server instance.

---

## Database Design

| Table Name     | Primary Key   | Foreign Keys          |
|----------------|---------------|-----------------------|
| **User**       | `UserID`      | –                     |
| **ParkingSlot**| `SlotID`      | –                     |
| **VehicleLog** | `LogID`       | `UserID`, `SlotID`    |
| **Reservation**| `ReservationID`| `UserID`, `SlotID`   |
| **Invoice**    | `InvoiceID`   | `UserID`             |

---

## User Interface Design

### Wireframe Elements:
- Login/Signup Page.
- Dashboard for Admin/Staff/User.
- Slot Availability Map.
- Reservation Page.
- Vehicle Entry/Exit Management.
- Billing Summary and Payment Page.

---

## Non-Functional Requirements

### 1. Performance
- Support 200+ concurrent users in development/test setups.

### 2. Scalability
- Horizontal scalability using containerization (optional in future).

### 3. Security
- Role-based access control.
- Encrypted password storage.
- HTTPS for all data exchange.

### 4. Usability
- Responsive and mobile-friendly UI.
- WCAG-compliant design.

---

## Assumptions and Constraints

### Assumptions:
- Each slot accommodates only one vehicle.
- Entry/exit operations are manual or via scanner.

### Constraints:
- SMS/Email notifications are out of scope.
- Third-party integrations are not included in this phase.

---

## Conclusion
The **Vehicle Parking Management System** is designed to provide a robust and scalable solution for managing parking operations efficiently. It ensures seamless integration of core modules like user management, parking slot management, vehicle logging, reservations, and billing.
