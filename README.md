# OnlineShopping



SQL code to create the required databases:


```sql

-- 1️⃣ Create Database

CREATE DATABASE OnlineShopping;

GO



USE OnlineShopping;

GO



-- 2️⃣ Create Category Table

CREATE TABLE Category (

&nbsp;   Id INT IDENTITY(1,1) PRIMARY KEY,

&nbsp;   Name NVARCHAR(255) NOT NULL

);



-- 3️⃣ Create Product Table

CREATE TABLE Product (

&nbsp;   Id INT IDENTITY(1,1) PRIMARY KEY,

&nbsp;   Title NVARCHAR(255) NOT NULL,

&nbsp;   Description NVARCHAR(MAX) NOT NULL,

&nbsp;   Price INT NOT NULL,

&nbsp;   ProductPhoto NVARCHAR(500) NULL,

&nbsp;   CategoryId INT NOT NULL,

&nbsp;   CONSTRAINT FK\_Product\_Category FOREIGN KEY (CategoryId) REFERENCES Category(Id) ON DELETE CASCADE

);



-- 4️⃣ Create User Table

CREATE TABLE \[User] (

&nbsp;   Id INT IDENTITY(1,1) PRIMARY KEY,

&nbsp;   UserName NVARCHAR(255) NOT NULL UNIQUE,

&nbsp;   Password NVARCHAR(255) NOT NULL,

&nbsp;   UserType NVARCHAR(50) NOT NULL CHECK (UserType IN ('Admin', 'Customer'))

);



-- 5️⃣ Optional: Insert Sample Data

INSERT INTO Category (Name) VALUES ('Electronics'), ('Clothing'), ('Books');



INSERT INTO Product (Title, Description, Price, ProductPhoto, CategoryId) VALUES

('Laptop', 'High performance laptop', 1200, NULL, 1),

('T-Shirt', 'Cotton t-shirt', 20, NULL, 2),

('Novel', 'Best-selling book', 15, NULL, 3);



INSERT INTO \[User] (UserName, Password, UserType) VALUES

('admin@example.com', 'admin123', 'Admin'),

('customer@example.com', 'customer123', 'Customer');



```



You can create a file named: `init.sql` and run `sqlcmd -S [SERVER_NAME] -E -i init.sql`
to setup your database.

SERVER_NAME can be something like `DESKTOP\SQLEXPRESS` or others.



