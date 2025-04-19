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

```
![output]( https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/select%20from%20database.png
)

```sql
-- The code to create the Bookings table is as follows:
CREATE TABLE Bookings(
BookingID INT, 
BookingDate DATE,
TableNumber INT, 
NumberOfGuests INT,
CustomerID INT
);
 
-- The code to populate the Bookings table with data is as follows:
INSERT INTO Bookings 
(BookingID, BookingDate, TableNumber, NumberOfGuests, CustomerID) 
VALUES
(10, '2021-11-10', 7, 5, 1),  
(11, '2021-11-10', 5, 2, 2),  
(12, '2021-11-10', 3, 2, 4), 
(13, '2021-11-11', 2, 5, 5),  
(14, '2021-11-11', 5, 2, 6),  
(15, '2021-11-11', 3, 2, 7), 
(16, '2021-11-11', 3, 5, 1),  
(17, '2021-11-12', 5, 2, 2),  
(18, '2021-11-12', 3, 2, 4), 
(19, '2021-11-13', 7, 5, 6),  
(20, '2021-11-14', 5, 2, 3),  
(21, '2021-11-14', 3, 2, 4);

-- The code to see Bookings table:- 2
SELECT * FROM Bookings;

```
![output]( https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/select%20from%20database2.png
)

```sql
-- The code to create the restaurant Courses table is as follows:-
CREATE TABLE Courses(
CourseName VARCHAR(255) PRIMARY KEY,
 Cost Decimal(4,2)
 );

-- The code to populate the restaurant's Courses table with data is as follows:
INSERT INTO
 Courses (CourseName, Cost)
 VALUES 
("Greek salad", 15.50), 
("Bean soup", 12.25), 
("Pizza", 15.00), 
("Carbonara", 12.50), 
("Kabasa", 17.00), 
("Shwarma", 11.30);

-- The code to see Courses table :- 3
SELECT * FROM Courses;
```

![output](https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/courses%20table.png
)


```sql
-- Filter data using the WHERE clause and logical operators.4
SELECT * 
FROM Bookings 
WHERE BookingDate BETWEEN '2021-11-11' AND '2021-11-13';
```
![output](  https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/image%204.png
)

-- Task 2: Create a JOIN Query.

Create an JOIN SQL statement on the Customers and Bookings tables. statement must print  customers full names and related bookings iDs from the date 2021/11/11.

The expected output result should be the same as that shown in the following screenshot :

```sql
-- Create a JOIN Query. 5
SELECT Customers.FullName, Bookings.BookingID 
FROM Customers RIGHT JOIN Bookings 
ON Customers.CustomerID = Bookings.CustomerID 
WHERE BookingDate = '2021-11-11';
```
![output](  https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/image%205.png
)

🗂️ Task 3: Group Bookings by Date
Write a SQL query to display each booking date along with the total number of bookings made on that date. Use the GROUP BY BookingDate clause.

✅ Expected Output:
A list of dates with corresponding booking counts, matching the provided screenshot
```sql
-- Create a GROUP BY Query:-6
SELECT BookingDate, COUNT(BookingDate) 
FROM Bookings 
GROUP BY BookingDate;
```
![output](  https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/image%206.png
)


💾 Task 4: Update Course Cost Using REPLACE
Write a SQL REPLACE statement to update the cost of the Kabsa course .

✅ Expected Output:
The course "Kabsa" should now reflect the updated cost in the table, matching the screenshot provided.

```sql

-- Create a REPLACE Statement and then see the changes made:-7
REPLACE INTO Courses (CourseName, Cost) VALUES ("Kabasa", 20.00);
SELECT * FROM Courses;
```

![output](  https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/image%207.png
)


🛠️ Task 5: Alter Table to Add Ingredients Column
Write a SQL ALTER TABLE statement to add a new column named Ingredients to the Courses table.

Column Name: Ingredients

Data Type: VARCHAR(255)

✅ Expected Output:
The Courses table should now include the Ingredients column, as shown in the screenshot.

```sql
-- Alter Table Structure and then see the columns from Courses.
ALTER TABLE Courses
 ADD COLUMN Ingredients VARCHAR(255);
 
SHOW COLUMNS FROM Courses;  -- 8
```
![output](https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/8.png
)

Task 6: Find Customers Using a Subquery
Write a SQL statement using a subquery to display the full names of customers who made bookings on 2021-11-11.

Target Table: Customers

Condition: Booking date equals 2021-11-11

Hint: Use a subquery to filter customers based on CustomerID from the Bookings table.

✅ Expected Output:
A list of customer full names who booked on that date, matching the screenshot provided.

```sql
-- Create a Subquery: new
SELECT FullName 
FROM Customers 
WHERE (SELECT CustomerID 
       FROM Bookings
       WHERE Customers.CustomerID = Bookings.CustomerID and BookingDate = "2021-11-11");
```
![output]()

🧾 Task 7: Create a Virtual Table (View)
Create a SQL VIEW named BookingsView that shows:

BookingID

BookingDate

NumberOfGuests

Only include bookings that:

Were made before 2021-11-13

Have more than 3 guests

Then, select all data from BookingsView.

✅ Expected Output:
A filtered list of bookings matching the conditions, just like the screenshot.

```sql
-- Create a Virtual Table and then see the Virtual Table.
CREATE VIEW BookingsView AS
 SELECT BookingID, BookingDate, NumberOfGuests
 FROM Bookings
 WHERE NumberOfGuests > 3 AND BookingDate < "2021-11-13";
 
SELECT * FROM BookingsView;  -- 9

```
![output]( https://github.com/imSaurav06/MYSQL/blob/f2b30b7d2b08ceab084978946fd6606dfbd59fe2/image_resources/9.png
)



🧩 Task 8: Create a Stored Procedure
Create a stored procedure named GetBookingsData that:

Accepts one parameter: InputDate (date format)

Returns all records from the Bookings table where the BookingDate equals InputDate

Then, execute the procedure with:

sql
Copy
Edit GetBookingsData('2021-11-13');
✅ Expected Output:
All bookings from the date 2021-11-13, matching the screenshot.

```sql
-- Create a Stored Procedure and then call the Stored Procedure.10
CREATE PROCEDURE GetBookingsData (InputDate DATE) 
SELECT * 
FROM Bookings 
WHERE BookingDate = InputDate;
CALL GetBookingsData ("2021-11-13");

-- Use the String Function.
SELECT CONCAT( "ID: ", BookingID, ' ,Date: ', BookingDate, ', Number of guests: ', NumberOfGuests) AS "Booking Details" FROM Bookings;
```

![output](https://github.com/imSaurav06/MYSQL/blob/51513dba0f6b747ca1e00431e01a133172707bc3/image_resources/10.png)







 





