# **IT Support Ticket System**

## **Table of Contents**

1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Tech Stack](#tech-stack)
4. [Folder Structure](#folder-structure)
5. [Database Schema](#database-schema)
6. [Installation & Setup](#installation--setup)
7. [Usage](#usage)
8. [Testing](#testing)
9. [Future Enhancements](#future-enhancements)

---

## **Project Overview**

The **IT Support Ticket System** is a web-based application that allows users to submit technical problems or issues to IT support or system administrators.
Users receive a **ticket number** for tracking their requests, and IT admins can confirm receipt, provide estimated resolution time, and add instructions.

The system includes:

* **User registration and login**
* **Admin login and dashboard**
* **Real-time admin online/offline status**
* **Ticket submission, tracking, and updates**
* **Color-coded ticket statuses**

---

## **Features**

### **User Features**

* Register and login securely
* Submit technical problems with title and description
* Receive unique ticket number after submission
* Track ticket status, estimated time, and instructions
* See admin online/offline status

### **Admin Features**

* Admin login with secure credentials
* Dashboard to view all tickets
* Confirm tickets and update status (Pending / Confirmed / Resolved)
* Add estimated resolution time and instructions for each ticket
* Logout sets admin status offline

---

## **Tech Stack**

* **Frontend:** HTML, CSS (animations), JavaScript
* **Backend:** PHP
* **Database:** MySQL
* **Server:** Apache (XAMPP recommended)
* **Fonts:** Garamond / EB Garamond

---

## **Folder Structure**

```
it-support-system/
│
├── db.php                 # Database connection
├── submit_ticket.php      # User ticket submission
├── track_ticket.php       # Ticket tracking by ticket number
├── admin_status.php       # Check admin online/offline
│
├── auth/                  # User authentication
│   ├── register.php
│   ├── login.php
│   ├── logout.php
│
├── admin/                 # Admin files
│   ├── admin_login.php
│   ├── admin_logout.php
│   ├── dashboard.php
│   ├── fetch_tickets.php
│   ├── update_ticket.php
│
├── index.html             # User dashboard
├── login.html             # User login page
├── register.html          # User registration page
└── assets/
    └── style.css          # Styles & animations
```

---

## **Database Schema**

**Database Name:** `it_support_ticket_system`

### **users**

| Column    | Type               | Description                 |
| --------- | ------------------ | --------------------------- |
| id        | INT AUTO_INCREMENT | Primary key                 |
| full_name | VARCHAR(100)       | Full name of user/admin     |
| email     | VARCHAR(100)       | Unique email                |
| password  | VARCHAR(255)       | Hashed password             |
| is_admin  | TINYINT(1)         | 1 = admin, 0 = regular user |

### **tickets**

| Column         | Type               | Description                    |
| -------------- | ------------------ | ------------------------------ |
| id             | INT AUTO_INCREMENT | Primary key                    |
| user_id        | INT                | Foreign key → users.id         |
| title          | VARCHAR(255)       | Ticket title                   |
| description    | TEXT               | Problem description            |
| status         | ENUM               | Pending / Confirmed / Resolved |
| ticket_number  | VARCHAR(20)        | Unique ticket number           |
| estimated_time | VARCHAR(50)        | ETA provided by admin          |
| instructions   | TEXT               | Instructions provided by admin |
| created_at     | TIMESTAMP          | Auto-generated                 |
| updated_at     | TIMESTAMP          | Auto-updated                   |

### **admin_status**

| Column      | Type               | Description             |
| ----------- | ------------------ | ----------------------- |
| id          | INT AUTO_INCREMENT | Primary key             |
| admin_id    | INT                | Foreign key → users.id  |
| is_online   | TINYINT(1)         | 1 = online, 0 = offline |
| last_active | TIMESTAMP          | Last activity timestamp |

---

## **Installation & Setup**

### **1. Requirements**

* XAMPP or WAMP (Apache + MySQL)
* PHP >= 7.4
* MySQL

### **2. Steps**

1. Download or clone the repository:

   ```
   git clone <repo-url>
   ```
2. Move the project folder to `htdocs` (for XAMPP).
3. Start **Apache** and **MySQL**.
4. Create database `it_support_ticket_system` in **phpMyAdmin**.
5. Import the SQL schema included in the project.
6. Create an admin manually (optional):

   ```sql
   INSERT INTO users (full_name,email,password,is_admin)
   VALUES ('System Admin','admin@itsupport.com','<hashed_password>',1);
   ```
7. Update database credentials in `db.php`.

---

## **Usage**

### **User**

1. Register: `register.html`
2. Login: `login.html`
3. Submit Ticket: `index.html`
4. Track Ticket: enter ticket number in user dashboard

### **Admin**

1. Login: `admin/admin_login.php`
2. View tickets in `dashboard.php`
3. Confirm tickets, set ETA, and instructions
4. Logout sets status offline

---

## **Testing**

1. Open browser: `http://localhost/it-support-system/register.html`
2. Register a new user
3. Login and submit a ticket
4. Copy ticket number and track it
5. Admin login: `http://localhost/it-support-system/admin/admin_login.php`
6. Confirm ticket → user sees updated status
7. Logout admin → user sees **Offline**

---

## **Future Enhancements**

* Email notifications for ticket updates
* Real-time ticket updates (WebSockets)
* Multiple admin support
* Analytics dashboard for admins
* Mobile-responsive design



Do you want me to do that?
