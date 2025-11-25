# PL-SQL_University-Course-Registration-Grade-Management-System.
 PROJECT :  University Course Registration & Grade Management System

Below is the FULL PROJECT, including:

✅ Tables creation script
✅ Sample data script
✅ Full PL/SQL main program

1. DATABASE/TABLES_CREATION.sql

What tables_creation.sql does — step-by-step

Creates students table with columns: student_id, first_name, last_name, program.

Creates courses table: course_id, course_name, credit_hours.

Creates grade_history table to store grades (with foreign keys to students and courses).

Commits changes and prints a confirmation message.

Purpose: schema foundation so PL/SQL code can query and demonstrate %ROWTYPE records and sample data.

-- Create Students table
CREATE TABLE students (
    student_id NUMBER PRIMARY KEY,
    first_name VARCHAR2(50),
    last_name VARCHAR2(50),
    program VARCHAR2(50)
);

-- Create Courses table
CREATE TABLE courses (
    course_id NUMBER PRIMARY KEY,
    course_name VARCHAR2(100),
    credit_hours NUMBER
);

-- Create Grade History table
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

COMMIT;

SELECT 'Tables created successfully!' AS message FROM dual

2 DATABASE /SAMPLE_DATA.sql

What sample_data.sql does — step-by-step

Inserts a few student rows (Alice, Bob, Charlie).

Inserts a few course rows (Database Systems, Computer Networks, Operating Systems).

Inserts grade history rows for testing (grade_history).

Commits the inserts and prints confirmation.

Purpose: provides realistic data so the PL/SQL demo can SELECT ... INTO and show record examples and logic outputs.

-- Insert students
INSERT INTO students VALUES (1, 'Alice', 'Johnson', 'Computer Science');
INSERT INTO students VALUES (2, 'Bob', 'Smith', 'Information Technology');
INSERT INTO students VALUES (3, 'Charlie', 'Brown', 'Software Engineering');

-- Insert courses
INSERT INTO courses VALUES (101, 'Database Systems', 3);
INSERT INTO courses VALUES (102, 'Computer Networks', 4);
INSERT INTO courses VALUES (103, 'Operating Systems', 3);

-- Insert grade history
INSERT INTO grade_history VALUES (1, 1, 101, 'A', 2024, 'Fall');
INSERT INTO grade_history VALUES (2, 1, 102, 'B', 2024, 'Fall');
INSERT INTO grade_history VALUES (3, 2, 101, 'B+', 2024, 'Fall');
INSERT INTO grade_history VALUES (4, 2, 103, 'A-', 2024, 'Fall');

COMMIT;

SELECT 'Sample data inserted!' AS message FROM dual;

