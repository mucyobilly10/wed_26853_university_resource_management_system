# University Resource Management System

## 📚 Project Overview
The **University Resource Management System** is a full-stack web application integrated with an Oracle database. It enables the efficient management and booking of university resources such as labs, classrooms, books, and equipment. The system ensures transparency, security, and automation across departments.

---

## 🧩 Features

- Role-based access: Admin, Faculty, Manager, Student
- Manage departments, resources, and users
- Booking system with conflict validation and approval workflow
- Resource maintenance reporting and tracking
- Feedback and rating system
- Notification system for bookings and maintenance
- Implements PL/SQL procedures, functions, cursors, and exception handling

---

## ⚙️ Technology Stack

| Layer       | Technology Used                |
|------------|---------------------------------|
| Frontend   | HTML, CSS, JavaScript           |
| Backend    | PHP                             |
| Database   | Oracle SQL, PL/SQL              |

---

## 🗃️ Database Schema

### Main Tables:
- `Department`: Stores department details
- `AppUser`: Stores user information with roles
- `Resource`: University resources linked to departments
- `Booking`: Booking requests with status and schedule
- `Maintenance`: Tracks reported issues on resources
- `Feedback`: User-submitted ratings and comments
- `Notification`: Message system for status updates

---

## 💻 Setup Instructions

### 1. Oracle Database
- Run the `CREATE TABLE` scripts located in the SQL folder.
- Populate tables using the sample `INSERT` statements.
- Create necessary **indexes**, **procedures**, **functions**, and **packages**.

### 2. Web Server (PHP)
- Deploy the frontend files to a PHP-supported server (e.g., XAMPP, WAMP).
- Configure `config.php` with Oracle DB credentials.
- Use the application via the login page based on user roles.

---

## 🧪 Testing & Validation

- Test cases implemented for:
  - Booking conflict resolution
  - Maintenance status transitions
  - Resource availability checks
- PL/SQL used for exception handling and logic encapsulation

---

## 📦 Directory Structure

 ### 1. ERD DIAGRAM

![image](https://github.com/user-attachments/assets/75f9fa51-9f33-417c-ab60-b66cc3087c05)


### 2. BPMN DIAGRAM

![image](https://github.com/user-attachments/assets/429975c2-db56-46b5-9c0f-44cba8cd241c)

### 3. CREATING A PLUGGABLE DATABASE
```sql

CREATE PLUGGABLE DATABASE wed_26853_BILLY_university_resource_management_system_db
  2    ADMIN USER billy IDENTIFIED BY billy
  3    FILE_NAME_CONVERT = (
  4      'C:\app\oradata\XE\pdbseed',
  5      'C:\app\oradata\XE\WED26853_BILLY_DB'
  6    );

```
![image](https://github.com/user-attachments/assets/cc40d6ee-9305-45cb-92ad-5800e12d5d02)

### OEM
![image](https://github.com/user-attachments/assets/8ef8f84f-6d35-4885-861b-fa9f683c5fa4)


### 3. CREATING TABLE CODES





![image](https://github.com/user-attachments/assets/9d254d42-f525-4d35-a330-442fd502eecd)
![image](https://github.com/user-attachments/assets/2b9e87fa-0ec3-402f-8699-60faf7bb05f3)
![image](https://github.com/user-attachments/assets/0d1e9f85-a193-46ab-985c-4b1b4343c45b)
![image](https://github.com/user-attachments/assets/ed6b3a9d-c943-4348-91f7-c0035c79d733)
![image](https://github.com/user-attachments/assets/4c0f4ae4-0a34-4002-966a-3e3a996cf72f)
![image](https://github.com/user-attachments/assets/055d542b-219e-4e02-9e6c-9fc9bae5c9c7)



### 4. INSERT TABLE VALUES
<br>
<br>

```sql

INSERT INTO Resources (Name, Type, Location, Status, Description, DepartmentID) VALUES
('Comp Lab A', 'Lab', 'Block B - Room 105', 'Available', 'Advanced computing lab with 40 PCs', 1);

INSERT INTO Resources (Name, Type, Location, Status, Description, DepartmentID) VALUES
('Lecture Room 3', 'Classroom', 'Block C - Room 203', 'Available', 'Seating for 60 students', 1);

INSERT INTO Resources (Name, Type, Location, Status, Description, DepartmentID) VALUES
('Oscilloscope', 'Equipment', 'Lab 2, EE Block', 'Available', 'Digital oscilloscope, 50MHz', 2);

INSERT INTO Resources (Name, Type, Location, Status, Description, DepartmentID) VALUES
('Database Systems Book', 'Book', 'Library Shelf 2A', 'Available', 'Core DBMS textbook', 3);
<br>
<br>
```
<br>
<br>


```sql

INSERT INTO Booking (UserID, ResourceID, StartTime, EndTime, Status, Purpose) VALUES
(1, 1, TO_TIMESTAMP('2025-05-25 09:00:00', 'YYYY-MM-DD HH24:MI:SS'), TO_TIMESTAMP('2025-05-25 11:00:00', 'YYYY-MM-DD HH24:MI:SINSERT INTO Booking (UserID, ResourceID, StartTime, EndTime, Status, Purpose) VALUES
(1, 1, TO_TIMESTAMP('2025-05-25 09:00:00', 'YYYY-MM-DD HH24:MI:SS'), TO_TIMESTAMP('2025-05-25 11:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'Approved', 'Group project work');

INSERT INTO Booking (UserID, ResourceID, StartTime, EndTime, Status, Purpose) VALUES
(2, 2, TO_TIMESTAMP('2025-05-26 14:00:00', 'YYYY-MM-DD HH24:MI:SS'), TO_TIMESTAMP('2025-05-26 16:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'Pending', 'Lecture session');

INSERT INTO Booking (UserID, ResourceID, StartTime, EndTime, Status, Purpose) VALUES
(1, 4, TO_TIMESTAMP('2025-05-27 10:00:00', 'YYYY-MM-DD HH24:MI:SS'), TO_TIMESTAMP('2025-05-27 12:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'Approved', 'Research reading');
S'), 'Approved', 'Group project work');

INSERT INTO Booking (UserID, ResourceID, StartTime, EndTime, Status, Purpose) VALUES
(2, 2, TO_TIMESTAMP('2025-05-26 14:00:00', 'YYYY-MM-DD HH24:MI:SS'), TO_TIMESTAMP('2025-05-26 16:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'Pending', 'Lecture session');

INSERT INTO Booking (UserID, ResourceID, StartTime, EndTime, Status, Purpose) VALUES
~(1, 4, TO_TIMESTAMP('2025-05-27 10:00:00', 'YYYY-MM-DD HH24:MI:SS'), TO_TIMESTAMP('2025-05-27 12:00:00', 'YYYY-MM-DD HH24:MI:SS'), 'Approved', 'Research reading');
<br>
<br>
```
<br>
<br>



```sql
INSERT INTO AppUser (Name, Email, Password, Role, DepartmentID) VALUES 
('John Doe', 'john.doe@university.edu', 'password123', 'Student', 1);

INSERT INTO AppUser (Name, Email, Password, Role, DepartmentID) VALUES 
('Dr. Emily Smith', 'emily.smith@university.edu', 'securepass', 'Faculty', 1);

INSERT INTO AppUser (Name, Email, Password, Role, DepartmentID) VALUES 
('Mark Taylor', 'mark.taylor@university.edu', 'adminpass', 'Admin', 2);

INSERT INTO AppUser (Name, Email, Password, Role, DepartmentID) VALUES 
('Sarah Lane', 'sarah.lane@university.edu', 'managerpass', 'Manager', 3);
<br>
<br>
INSERT INTO Department (Name, Head) VALUES ('Computer Science', 'Dr. Alice Johnson');
INSERT INTO Department (Name, Head) VALUES ('Electrical Engineering', 'Dr. Mark Benson');
INSERT INTO Department (Name, Head) VALUES ('Library Services', 'Mrs. Janet Cole');
<br>
<br>
```

![image](https://github.com/user-attachments/assets/f4b350dc-59b6-4dc5-8e90-393d65c146a0)
![image](https://github.com/user-attachments/assets/0349e8ab-bb14-4eae-ad75-7c7781c10fe5)
![image](https://github.com/user-attachments/assets/70d593f5-eeaa-4435-83ea-548c87aee255)
![image](https://github.com/user-attachments/assets/f144fc90-f6ff-4135-bb77-e1da545b8010)

### 5. DML MANIPULATION 
<br>
<br>


```sql
INSERT INTO Booking (UserID, ResourceID, StartTime, EndTime, Status, Purpose)
VALUES (2, 1, TO_TIMESTAMP('2025-05-25 10:00:00', 'YYYY-MM-DD HH24:MI:SS'), 
             TO_TIMESTAMP('2025-05-25 12:00:00', 'YYYY-MM-DD HH24:MI:SS'),
        'Pending', 'Test conflict');
        <br>
        <br>

```


![image](https://github.com/user-attachments/assets/46363dba-9fe8-45ed-a1ec-feb7e02f631b)

 






###6 DDL MANIPULATION

![image](https://github.com/user-attachments/assets/2f914e4d-7944-495d-88a8-cb951810a56b)


### 7.CREATE FUNCTION RESOURCE
<br>
<br>


```sql

CREATE OR REPLACE FUNCTION Get_Resource_Bookings_Count(p_resource_id IN NUMBER)
RETURN NUMBER IS
    v_count NUMBER;
BEGIN
    SELECT COUNT(*) INTO v_count 
    FROM Booking 
    WHERE ResourceID = p_resource_id;

    RETURN v_count;
EXCEPTION
    WHEN OTHERS THEN
        RETURN -1;
END;
/
```

![image](https://github.com/user-attachments/assets/d54eb464-e70e-4e74-8e92-5ed9bcb56fc0)





<br>
<br>

### 8. create function booking
<br>
<br>

```sql
CREATE OR REPLACE PROCEDURE Get_User_Bookings(p_user_id IN NUMBER) IS
    CURSOR c_bookings IS
        SELECT BookingID, ResourceID, StartTime, Status
        FROM Booking
        WHERE UserID = p_user_id;

    v_rec c_bookings%ROWTYPE;
BEGIN
    OPEN c_bookings;
    LOOP
        FETCH c_bookings INTO v_rec;
        EXIT WHEN c_bookings%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE('BookingID: ' || v_rec.BookingID || ', Resource: ' || v_rec.ResourceID ||
                             ', Time: ' || v_rec.StartTime || ', Status: ' || v_rec.Status);
    END LOOP;
    CLOSE c_bookings;
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/
```

<br>
<br>

![image](https://github.com/user-attachments/assets/ae38450c-1423-4171-bd8b-555ac601734f)

### package creation
![image](https://github.com/user-attachments/assets/c1f7a719-5048-430c-a7dc-5177ca890331)






















 
