# SQL_Database_Project.sql

# 🍋 Little Lemon Restaurant - MySQL Database Project

A MySQL-based relational database project for **Little Lemon**, a family-owned Mediterranean restaurant in Chicago. This project models customers, bookings, and menu courses, supporting efficient data management and potential business analytics.

---

## 📖 About Little Lemon

**Little Lemon** is a rustic Mediterranean restaurant owned by Italian brothers Mario and Adrian. Inspired by family recipes and Mediterranean cultures (Italian, Greek, Turkish), the restaurant serves a seasonal menu of 12–15 dishes in a relaxed setting with moderate prices.

---

## 🧰 Prerequisites

To run this project, ensure you have:
- MySQL installed on your system
- MySQL Workbench or any MySQL client
- A user account with privileges to create databases and tables

---

## 🗄️ Database & Tables Setup

### 🔹 1. Create the Database

```sql
CREATE DATABASE IF NOT EXISTS Little_Lemon;
USE Little_Lemon;

-- The code to create the Customers table is as follows:
CREATE TABLE Customers(
CustomerID INT NOT NULL PRIMARY KEY,
 FullName VARCHAR(100) NOT NULL,
 PhoneNumber INT NOT NULL UNIQUE
 );

-- The code to populate the Customers table is as follows:
INSERT INTO 
Customers(CustomerID, FullName, PhoneNumber) 
VALUES 
(1, "Vanessa McCarthy", 0757536378), 
(2, "Marcos Romero", 0757536379), 
(3, "Hiroki Yamane", 0757536376), 
(4, "Anna Iversen", 0757536375), 
(5, "Diana Pinto", 0757536374),     
(6, "Altay Ayhan", 0757636378),      
(7, "Jane Murphy", 0753536379),      
(8, "Laurina Delgado", 0754536376),      
(9, "Mike Edwards", 0757236375),     
(10, "Karl Pederson", 0757936374);

-- The code to see Customers table : 1
SELECT * FROM Customers;


---



   ```bash
   git clone https://github.com/your-username/little-lemon-db.git
   cd little-lemon-db

