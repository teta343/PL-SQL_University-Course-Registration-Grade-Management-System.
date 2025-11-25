NAME: TETA KEVINE
ID: 27973

# PL-SQL_University-Course-Registration-Grade-Management-System.
University Course Registration & Grade Management System

📌 Project Overview

This project implements a University Course Registration & Grade Management System using Oracle PL/SQL.
It demonstrates:

Table creation, constraints, and schema design

Sample data insertion

Use of %ROWTYPE, VARRAY collections, and records

PL/SQL loops with GOTO statements

Basic academic processing logic (students, courses, grades)

The system simulates a simplified student-course-grade workflow used in higher education institutions.

🏗️ Database Structure

1️⃣ Students Table

Stores student personal and program details.

CREATE TABLE students (
    student_id NUMBER PRIMARY KEY,
    first_name VARCHAR2(50),
    last_name VARCHAR2(50),
    program VARCHAR2(50)
);

2️⃣ Courses Table

Stores course information.

CREATE TABLE courses (
    course_id NUMBER PRIMARY KEY,
    course_name VARCHAR2(100),
    credit_hours NUMBER
);

3️⃣ Grade History Table

Tracks all grade records per student and course.

CREATE TABLE grade_history (
    history_id NUMBER PRIMARY KEY,
    student_id NUMBER,
    course_id NUMBER,
    grade VARCHAR2(5),
    grade_year NUMBER,
    grade_semester VARCHAR2(10),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);


✔️ All tables successfully created
✔️ Includes PKs, FKs, and valid data types

📊 Sample Data (Inserted)

Students
INSERT INTO students VALUES (1, 'Alice', 'Johnson', 'Computer Science');
INSERT INTO students VALUES (2, 'Bob', 'Smith', 'Information Technology');
INSERT INTO students VALUES (3, 'Charlie', 'Brown', 'Software Engineering');

Courses
INSERT INTO courses VALUES (101, 'Database Systems', 3);
INSERT INTO courses VALUES (102, 'Computer Networks', 4);
INSERT INTO courses VALUES (103, 'Operating Systems', 3);

Grade History
INSERT INTO grade_history VALUES (1, 1, 101, 'A', 2024, 'Fall');
INSERT INTO grade_history VALUES (2, 1, 102, 'B', 2024, 'Fall');
INSERT INTO grade_history VALUES (3, 2, 101, 'B+', 2024, 'Fall');
INSERT INTO grade_history VALUES (4, 2, 103, 'A-', 2024, 'Fall');


✔️ Sample data provides realistic scenarios
✔️ Enables testing of queries, %ROWTYPE, lookups, etc


1️⃣ VARRAY Declaration & Initialization

TYPE course_array IS VARRAY(5) OF NUMBER;
v_course_list course_array := course_array(101, 102, 103);


Stores up to 5 course IDs

Used for representing a student’s registered course list

Supports .COUNT and index-based access

🔁 Processing Logic Using GOTO

Loop Demonstration

This loop processes three students and classifies the first student as Honor Student using GOTO.

FOR id IN 1..3 LOOP
    total_students := total_students + 1;

    IF id = 1 THEN
        GOTO HONOR_PROCESS;
    END IF;

    <<REGULAR_PROCESS>>
    DBMS_OUTPUT.PUT_LINE('Regular Student: ' || v_students(id));
    CONTINUE;

    <<HONOR_PROCESS>>
    IF id = 1 THEN
        DBMS_OUTPUT.PUT_LINE('Honor Student: ' || v_students(id) || ' (Dean''s List)');
        honor_students := honor_students + 1;
    END IF;
END LOOP;

❗ Purpose of GOTO in This Project

Demonstrates low-level branching

Used to jump out of normal flow for special-case handling

Helps show PL/SQL’s support for labeled blocks and alternate logic paths

 Tested Outputs

During execution you will see:

“Tables created successfully!”

“Sample data inserted!”

List of Regular and Honor students

VARRAY iteration output

Grade history processing

🎯 Key Learning Outcomes

By completing this project, you demonstrated:

✔ Database schema creation
✔ Inserting and validating sample data
✔ Using VARRAYs in PL/SQL
✔ Using GOTO and labels
✔ Working with loops & processing logic
✔ Understanding student-course-grade relationships

📂 Files Included in Your Project
File	Purpose
DATABASE/TABLE_CREATION.sql	Creates all required tables
DATABASE/SAMPLE_DATA.sql	Inserts realistic sample data
plsql_processing_block.sql	Contains VARRAY, GOTO logic, loops
README.md	Full project explanation
✅ Final Notes

This PL/SQL project demonstrates essential database programming skills required in real academic information systems.
You have implemented all required components:

✔ Tables
✔ Sample data
✔ VARRAY
✔ GOTO logic
✔ Loops & processing
