CREATE DATABASE TinyHub;

USE TinyHub;

CREATE TABLE Student (
	StudentId Int NOT NULL,
	StudentName Char(50) NOT NULL,
	Email Char(30) NOT NULL UNIQUE,
	DispName Char(20) UNIQUE,
	Password Char(20) NOT NULL,
	Primary Key (Email)
);

CREATE TABLE Professor (
	ProfId Int NOT NULL,
	ProfName Char(50) NOT NULL,
	Email Char(30) NOT NULL UNIQUE,
	DispName Char(20) UNIQUE,
	Password Char(20) NOT NULL,
	Primary Key (Email)
);

CREATE TABLE Staff (
	StaffId Int NOT NULL,
	StaffName Char(50) NOT NULL,
	Email Char(30) NOT NULL UNIQUE,
	DispName Char(20) UNIQUE,
	Password Char(20) NOT NULL,
	Primary Key (Email)
);

CREATE TABLE Department (
	DeptId Char(10) NOT NULL UNIQUE,
	DeptName Char(30) NOT NULL UNIQUE,
	Primary Key (DeptId)
);

CREATE TABLE Programs (
	ProgId Char(10) NOT NULL UNIQUE,
	DeptId Char(10) NOT NULL UNIQUE,
	ProgName Char(30) NOT NULL UNIQUE,
	Primary Key (ProgId),
	Constraint Prog
		Foreign Key (DeptId) References Department(DeptId)
		ON DELETE CASCADE
);

CREATE TABLE ProfHire (
	ProfEmail Char(30) NOT NULL UNIQUE,
	DeptId Char(10) NOT NULL,
	Primary Key (ProfEmail, DeptId),
	Foreign Key (DeptId) References Department(DeptId),
	Foreign Key (ProfEmail) References Professor(Email)
);

CREATE TABLE StaffHire (
	StaffEmail Char(30) NOT NULL UNIQUE,
	DeptId Char(10) NOT NULL,
	Primary Key (StaffEmail, DeptId),
	Foreign Key (DeptId) References Department(DeptId),
	Foreign Key (StaffEmail) References Staff(Email)
);

CREATE TABLE Courses (
	CourseId Char(10) NOT NULL,
	DeptId Char(10) NOT NULL,
	TaEmail Char(30) NOT NULL,
	CourseName Char(30) NOT NULL,
	InstructorEmail Char(30) NOT NULL,
	Enrolled Int NOT NUll,
	MaxEnrolled Int NOT NULL,
	Primary Key (CourseId),
	Constraint Enrolled
		Check (Enrolled <= MaxEnrolled AND Enrolled >= 0),
	Constraint Instructor
		Foreign Key (InstructorEmail) References Professor(Email)
		ON UPDATE CASCADE,
	Constraint Crs
		Foreign Key (DeptId) References Department(DeptId)
		ON DELETE CASCADE, 
	Constraint TA
		Foreign Key (TaEmail) References Student(Email)
		ON UPDATE CASCADE
);

CREATE TABLE Majors (
	ProgId Char(10) NOT NULL,
	StudentEmail Char(30) NOT NULL,
	DeptId Char(10) NOT NULL,
	Primary Key (ProgId, DeptId, StudentEmail),
	Foreign Key (DeptId) References Department(DeptId),
	Foreign Key (StudentEmail) References Student(Email)
);

CREATE TABLE Prerequisites (
	CourseId Char(10) NOT NULL,
	PrerequisiteID Char(10) NOT NULL,
	Primary Key (CourseId, PrerequisiteID),
	Foreign Key (CourseId) References Courses(CourseId),
	Foreign Key (PrerequisiteID) References Courses(CourseId)	
);

CREATE TABLE Semester(
	Year Int NOT NULL,
	Season Char(10) NOT NULL,
	Primary Key (Year, Season)
);

CREATE TABLE StudentRegister (
	StudentEmail Char(30) NOT NULL,
	RegYear Int NOT NULL,
	RegSeason Char(10) NOT NULL,
	Primary Key (StudentEmail, RegYear, RegSeason),
	Foreign Key (RegYear, RegSeason) References Semester(Year, Season),
	Foreign Key (StudentEmail) References Student(Email)
);

CREATE TABLE CoursesOpen (
	CourseId Char(10) NOT NULL,
	RegYear Int NOT NULL,
	RegSeason Char(10) NOT NULL,
	Primary Key (CourseId, RegYear, RegSeason),
	Foreign Key (RegYear, RegSeason) References Semester(Year, Season),
	Foreign Key (CourseId) References Courses(CourseId)
);

CREATE TABLE Enrolls (
	StudentEmail Char(30) NOT NULL,
	CourseId Char(10) NOT NULL,
	Grade Char(1) NOT NULL,
	Feedback Char(150),
	Primary Key(StudentEmail, CourseId),
	Foreign Key (CourseId) References Courses(CourseId),
	Foreign Key (StudentEmail) References Student(Email),
	Check (Grade IN ('A','B','C','D','F'))
);

CREATE TABLE Exams (
	CourseId Char(10) NOT NULL,
	ExamId Char(10) NOT NULL,
	Primary Key (CourseId, ExamId),
	Constraint Course_Exam
		Foreign Key (CourseId) References Courses(CourseId)
		ON DELETE CASCADE
);

CREATE TABLE Problems (
	ProblemId Char(10) NOT NULL,
	ExamId Char(10) NOT NULL,
	CourseId Char(10) NOT NULL,
	Primary Key (CourseId, ExamId, ProblemId),
	Constraint Course_Problem
		Foreign Key (CourseId) References Courses(CourseId)
		ON DELETE CASCADE,
	Constraint Exam_Problem
		Foreign Key (ExamId) References Exams(ExamId)
		ON DELETE CASCADE	
);