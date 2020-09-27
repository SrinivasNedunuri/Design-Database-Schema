# Design-Database-Schema
Design and Implement database schema for TinyHub, which is a course enrollment system 
 It provides simple functions, main functions for TinyHub are the following:
• User management
• Department management
• Course management
• Student Course management

# Requirements of functions
The specific requirements for each function of TinyHub are given in this section.
Note that you need to analyze and design the entity types, attributes
and relationship types, while this project description only gives some of them
for clarifying the system requirements.
# 1 User management
1. Users can be of three types: Students, Professors, or Staff.
2. Users sign up their accounts with their email addresses.
3. Users need to set their passwords.
4. Account, password, and display names are strings.
5. One account has an optional unique display name. Users are allowed to
change their display name as long as it is unique.
6. One email address can be used to register only one account.
# 2 Department management
1. Each department has an identifier department number.
2. Every professor is hired by one department.
3. Every staff is hired by one department.
4. Departments offer different programs, which a program can only belong
to one department.
5. Students are allowed to major in different departments.
6. Students can pursue different programs, but they must major in the department which is offering that program. e.g. Given a program "Data
Science" which is offered by CSE department, then only students major
in CSE are allowed to
# 3 Course management
1. Each department offers different courses.
2. A course can be opened in different semesters.
3. A semester is identified by a year and a season, e.g. 2020 Spring.
4. A course does NOT have to be opened every semester.
5. Every course has TAs, and one instructor. However, it is possible to
change TAs or the instructor even during the semester.
6. An instructor must be a professor.
7. A TA must be a student.
8. A course may contain prerequisite courses.
9. A student may register in different semesters.
# 4 Student-Course management
1. A student can enroll different courses. But that student can enroll a course
only if
• That student has registered in the semester and the course is offered
in that semester. i.e. A student need to register 2020 Spring before
enrolling any course in 2020 Spring.
• That student passes all the prerequisite courses
• It is being offered by a department they are majoring in
• The capacity of the course is not full
2. Students will have a grade (F/D/C/B/A) with the course, which will be
given after the student finishes the course.
3. Students can post feedback for the instructor of the course in which they
enrolled.
4. Each course has one or more exams. Students who take that course have
letter grades on those exams.
5. Each exam has a number of problems. Students have scores on those
problems.
