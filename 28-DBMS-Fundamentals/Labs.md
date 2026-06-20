# Day 28 - Lab: DBMS Design Practice

## Objective
Design a normalized database schema and implement it in a real RDBMS (MySQL or PostgreSQL).

## Prerequisites
```bash
sudo apt install mysql-server -y
# OR
sudo apt install postgresql -y
```

## Task 1: Design an ER Diagram (on paper or any diagram tool)
Design a simple "Library Management System" with these entities:
- Books (BookID, Title, Author, ISBN)
- Members (MemberID, Name, Email)
- Loans (LoanID, BookID, MemberID, LoanDate, ReturnDate)

Identify relationships: Members borrow Books (via Loans - a many-to-many resolved through a junction table).

## Task 2: Create the Normalized Schema
```sql
CREATE DATABASE library;
USE library;

CREATE TABLE Books (
    BookID INT PRIMARY KEY AUTO_INCREMENT,
    Title VARCHAR(255) NOT NULL,
    Author VARCHAR(255),
    ISBN VARCHAR(20) UNIQUE
);

CREATE TABLE Members (
    MemberID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(255) NOT NULL,
    Email VARCHAR(255) UNIQUE
);

CREATE TABLE Loans (
    LoanID INT PRIMARY KEY AUTO_INCREMENT,
    BookID INT,
    MemberID INT,
    LoanDate DATE,
    ReturnDate DATE,
    FOREIGN KEY (BookID) REFERENCES Books(BookID),
    FOREIGN KEY (MemberID) REFERENCES Members(MemberID)
);
```

## Task 3: Insert Sample Data
```sql
INSERT INTO Books (Title, Author, ISBN) VALUES ('Clean Code', 'Robert Martin', '9780132350884');
INSERT INTO Members (Name, Email) VALUES ('Tharsan', 'tharsan@example.com');
INSERT INTO Loans (BookID, MemberID, LoanDate) VALUES (1, 1, CURDATE());
```

## Task 4: Verify Relationships
```sql
SELECT Books.Title, Members.Name, Loans.LoanDate
FROM Loans
JOIN Books ON Loans.BookID = Books.BookID
JOIN Members ON Loans.MemberID = Members.MemberID;
```

## Results
| Item | Value |
|---|---|
| Database created (Y/N) | |
| Tables created | |
| Foreign keys working (Y/N) | |
| Join query result | |

## Screenshots
```
![ER Diagram](Screenshots/er-diagram.png)
![Schema Created](Screenshots/schema-created.png)
![Join Query Result](Screenshots/join-result.png)
```

## Lab Summary
Note any errors hit while creating foreign key constraints and how normalization made the schema cleaner than a single flat table would be.
