# shree
library management 

CREATE DATABASE LibraryManagement;

USE LibraryManagement;

-- Create Students Table
CREATE TABLE Students (
    student_id INT PRIMARY KEY AUTO_INCREMENT,
    student_name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(15)
);

-- Create Books Table
CREATE TABLE Books (
    book_id INT PRIMARY KEY AUTO_INCREMENT,
    book_name VARCHAR(150),
    author VARCHAR(100),
    category VARCHAR(50),
    quantity INT
);

-- Create Issue Table
CREATE TABLE Book_Issue (
    issue_id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    book_id INT,
    issue_date DATE,
    return_date DATE,
    status VARCHAR(20),
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id)
);

-- Insert Student Details
INSERT INTO Students
(student_name, email, phone)
VALUES
('Rahul', 'rahul@gmail.com', '9876543210'),
('Priya', 'priya@gmail.com', '9876543211');

-- Insert Book Details
INSERT INTO Books
(book_name, author, category, quantity)
VALUES
('Python Programming', 'Guido van Rossum', 'Programming', 5),
('Data Science', 'John Smith', 'Education', 3),
('Artificial Intelligence', 'Stuart Russell', 'Technology', 4);

-- Display Students
SELECT * FROM Students;

-- Display Books
SELECT * FROM Books;

-- Issue a Book
INSERT INTO Book_Issue
(student_id, book_id, issue_date, return_date, status)
VALUES
(1, 1, CURDATE(), NULL, 'Issued');

-- Search Books
SELECT * FROM Books
WHERE book_name LIKE '%Python%';

-- Return a Book
UPDATE Book_Issue
SET return_date = CURDATE(),
    status = 'Returned'
WHERE issue_id = 1;

-- Check Issued Books
SELECT * FROM Book_Issue;

-- Check Available Books
SELECT * FROM Books
WHERE quantity > 0;

