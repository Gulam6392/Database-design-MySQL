
#  Hospital Database Creation and Data Migration (MySQL)

A complete Hospital Management System Database developed using MySQL to migrate hospital records from an Excel-based system into a normalized relational database. The project focuses on database design, data migration, data integrity, automation using triggers, role-based access control, and department-wise revenue reporting.

---

#  Project Background

The hospital was maintaining all operational records—including patient information, doctor details, appointments, prescriptions, laboratory reports, and billing—using Excel spreadsheets.

As the hospital expanded, the Excel-based system became:

* Difficult to maintain
* Error-prone
* Inefficient for large datasets
* Unable to enforce relationships between data
* Inadequate for reporting and security

To overcome these challenges, a fully normalized relational database was designed using MySQL. Existing data from the Excel file (`hospital_data`) was migrated into structured database tables while maintaining data consistency and integrity.

---

#  Problem Statement

The project addresses the following real-world business problems:

### 1. Lack of Unique Identifiers

The Excel system did not guarantee unique identifiers for departments, doctors, patients, appointments, prescriptions, bills, or lab reports.

**Solution**

* Introduced Primary Keys with `AUTO_INCREMENT`.
* Ensured uniqueness across all entities.

---

### 2. Disconnected Relationships

Appointments in Excel were not linked to valid patients or doctors, resulting in inconsistent data.

**Solution**

Implemented Foreign Key constraints between:

* Departments → Doctors
* Doctors → Appointments
* Patients → Appointments
* Appointments → Prescriptions
* Appointments → Bills
* Appointments → Lab Reports

This maintains complete referential integrity.

---

### 3. Invalid or Ambiguous Data

The Excel data contained inconsistent values such as invalid gender codes, incorrect appointment statuses, and mixed date formats.

**Solution**

Implemented:

* CHECK Constraints
* Standardized gender values (`M`, `F`, `O`)
* Standardized appointment statuses (`Scheduled`, `Completed`, `Cancelled`)
* Date conversion using `STR_TO_DATE()`

---

### 4. Unregulated Appointment Scheduling

Doctors could be double-booked, and appointments could be scheduled in the past.

**Solution**

Created a MySQL Trigger that automatically:

* Prevents appointments in the past.
* Prevents double booking of doctors for the same appointment time.

---

### 5. Unrestricted Access to Patient Information

Every doctor had unrestricted access to all patient records.

**Solution**

Implemented a role-based Stored Procedure.

* Senior doctors can access all patients within their department.
* Other doctors can only access their own patients' appointment details, prescriptions, and lab reports.

---

### 6. Lack of Departmental Reporting

The Excel system could not generate revenue reports by department.

**Solution**

Developed a Stored Procedure that generates:

* Monthly revenue
* Department-wise revenue summary

using billing information.

---

#  Features

* Normalized Relational Database
* Excel to MySQL Data Migration
* Primary Keys
* Foreign Keys
* CHECK Constraints
* AUTO_INCREMENT IDs
* Default Values
* Trigger for Appointment Validation
* Role-Based Access Control
* Monthly Revenue Reporting
* Aggregate Reporting using SQL

---

#  Database Tables

* Department
* Doctors
* Patients
* Appointment
* Prescriptions
* Bills
* LabReport

---

#  Database Design

Department

↓

Doctors

↓

Appointments

├── Patients

├── Prescriptions

├── Bills

└── LabReport

---

#  Technologies Used

* MySQL
* SQL
* Relational Database Design
* Data Migration
* Stored Procedures
* Triggers
* Constraints

---

#  SQL Concepts Used

* CREATE DATABASE
* CREATE TABLE
* Primary Key
* Foreign Key
* CHECK Constraint
* DEFAULT Constraint
* AUTO_INCREMENT
* INSERT INTO...SELECT
* STR_TO_DATE()
* INNER JOIN
* Aggregate Functions
* GROUP BY
* Stored Procedures
* Triggers

---

#  Project Structure

```
Hospital_Management_System/
│
├── Hospital_Database.sql
├── README.md
└── Dataset (hospital_data)
```

---

#  How to Run

1. Create the database in MySQL.
2. Import the provided SQL script.
3. Create all tables.
4. Import the Excel dataset into the `hospital_data` table.
5. Execute the data migration queries.
6. Create triggers and stored procedures.
7. Run the sample procedure calls.

---

# Future Enhancements

* User Authentication System
* Pharmacy Module
* Inventory Management
* Nurse Management
* Medical History Tracking
* Appointment Dashboard
* Payment Gateway Integration
* Backup & Recovery Automation




**Gulam Mohammad**




