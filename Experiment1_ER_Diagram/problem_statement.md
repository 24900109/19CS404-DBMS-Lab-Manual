# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1392" height="677" alt="City Fitness Club Management drawio" src="https://github.com/user-attachments/assets/318983fc-a3b3-4bb6-badc-e8d00a20938a" />


### Entities and Attributes

| Entity     | Attributes (PK, FK)                                   | Notes                                   |
| ---------- | ----------------------------------------------------- | --------------------------------------- |
| Member     | Member_ID (PK), Name, Membership_Type, Start_Date     | Gym members                             |
| Program    | Program_ID (PK), Program_Name, Duration, Fee          | Fitness programs offered                |
| Trainer    | Trainer_ID (PK), Trainer_Name, Specialization         | Trainers conducting programs            |
| Session    | Session_ID (PK), Date, Time, Trainer_ID (FK)          | Training sessions conducted by trainers |
| Payment    | Payment_ID (PK), Member_ID (FK), Amount, Payment_Date | Membership payment details              |
| Attendance | Attendance_ID (PK), Session_ID (FK), Status           | Attendance records for sessions         |


### Relationships and Constraints

| Relationship                    | Cardinality | Participation       | Notes                                                                                       |
| ------------------------------- | ----------- | ------------------- | ------------------------------------------------------------------------------------------- |
| Member – Program (Joins)        | M : N       | Partial             | A member can join multiple programs, and a program can have many members.                   |
| Program – Trainer (Assigned To) | M : N       | Partial             | A program can be assigned to multiple trainers, and a trainer can handle multiple programs. |
| Trainer – Session (Conducts)    | 1 : M       | Total on Session    | Every session is conducted by exactly one trainer. A trainer may conduct many sessions.     |
| Member – Session (Books)        | 1 : M       | Partial             | A member may book multiple sessions. A session can be booked by many members.               |
| Member – Payment (Makes)        | 1 : M       | Total on Payment    | Every payment is made by one member. A member can make multiple payments.                   |
| Session – Attendance (Has)      | 1 : M       | Total on Attendance | Each attendance record belongs to one session. A session can have many attendance records.  |


### Assumptions
- A member can enroll in multiple fitness programs.
- A fitness program can have multiple members.
- Trainers may conduct more than one training session.
- Every training session is conducted by exactly one trainer.
- A member may book multiple sessions.
- Attendance is recorded separately for every session.
- A member can make multiple payments for memberships or programs.
- Each payment belongs to only one member.
- Attendance records are maintained per session.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1022" height="662" alt="City Library Event   Book Lending System drawio" src="https://github.com/user-attachments/assets/c2fa48bc-091d-4f21-b2c8-cb4fcd34e51c" />


### Entities and Attributes
| Entity  | Attributes (PK, FK)                                | Notes                            |
| ------- | -------------------------------------------------- | -------------------------------- |
| Member  | Member_ID (PK), Name, Phone                        | Library members                  |
| Book    | Book_ID (PK), Title, Category                      | Books available in the library   |
| Loan    | Loan_ID (PK), Book_ID (FK), Loan_Date, Return_Date | Book lending records             |
| Fine    | Fine_ID (PK), Loan_ID (FK), Amount                 | Fine for overdue book returns    |
| Event   | Event_ID (PK), Event_Name                          | Library events conducted         |
| Room    | Room_ID (PK), Room_Name                            | Rooms used for library events    |
| Speaker | Speaker_ID (PK), Speaker_Name                      | Speakers participating in events |


### Relationships and Constraints

| Relationship               | Cardinality | Participation  | Notes                                                                                         |
| -------------------------- | ----------- | -------------- | --------------------------------------------------------------------------------------------- |
| Member – Book (Borrows)    | M : N       | Partial        | A member can borrow multiple books, and a book can be borrowed by multiple members over time. |
| Book – Loan                | 1 : M       | Total on Loan  | Each loan is associated with exactly one book. A book can have many loan records.             |
| Loan – Fine (Generates)    | 1 : 0..1    | Partial        | A loan may or may not generate a fine. A fine belongs to only one loan.                       |
| Member – Event (Registers) | M : N       | Partial        | A member can register for multiple events, and an event can have many members.                |
| Room – Event (Hosts)       | 1 : M       | Total on Event | One room can host many events. Each event is hosted in one room.                              |
| Event – Speaker (Has)      | 1 : M       | Partial        | An event can have multiple speakers. Each speaker is assigned to one event.                   |


### Assumptions
- A library member can borrow multiple books.
- A book can be borrowed multiple times by different members over time.
- Every loan record is created for exactly one book.
- A fine is generated only if a borrowed book is returned late.
- A member may register for multiple library events.
- An event can have many registered members.
- Every event is hosted in one room, while a room can host multiple events.
- An event may have one or more speakers.
- Fine details are maintained separately from loan records.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1162" height="812" alt="Restaurant Table Reservation   Ordering drawio" src="https://github.com/user-attachments/assets/5d6e32a4-bc46-4cc3-8cf0-53e19880459f" />


### Entities and Attributes
| Entity      | Attributes (PK, FK)                                                                | Notes                                |
| ----------- | ---------------------------------------------------------------------------------- | ------------------------------------ |
| Customer    | Customer_ID (PK), Name                                                             | Customer details                     |
| Reservation | Reservation_ID (PK), Date, Guests, Customer_ID (FK), Table_ID (FK), Waiter_ID (FK) | Table reservations made by customers |
| Table       | Table_ID (PK), Capacity                                                            | Restaurant tables                    |
| Waiter      | Waiter_ID (PK), Name                                                               | Waiters serving customers            |
| Order       | Order_ID (PK), Order_Date, Reservation_ID (FK)                                     | Orders placed during a reservation   |
| Dish        | Dish_ID (PK), Dish_Name, Price, Category_ID (FK)                                   | Menu items served                    |
| Category    | Category_ID (PK), Category_Name                                                    | Dish categories                      |
| Bill        | Bill_ID (PK), Reservation_ID (FK), Total_Amount                                    | Final bill for a reservation         |

### Relationships and Constraints
| Relationship                     | Cardinality | Participation        | Notes                                                                                                        |
| -------------------------------- | ----------- | -------------------- | ------------------------------------------------------------------------------------------------------------ |
| Customer – Reservation (Makes)   | 1 : M       | Total on Reservation | A customer can make multiple reservations, and every reservation belongs to one customer.                    |
| Reservation – Table (Assigned)   | M : 1       | Total on Reservation | Every reservation is assigned to one table. A table can be assigned to many reservations at different times. |
| Waiter – Reservation (Served By) | 1 : M       | Total on Reservation | One waiter can serve multiple reservations. Each reservation is served by one waiter.                        |
| Reservation – Order (Has)        | 1 : M       | Partial              | A reservation can have multiple orders. Some reservations may not place any orders.                          |
| Order – Dish (Contains)          | 1 : M       | Total on Order       | An order contains one or more dishes. A dish can appear in multiple orders.                                  |
| Dish – Category (Belongs)        | M : 1       | Total on Dish        | Every dish belongs to one category. A category can contain many dishes.                                      |
| Reservation – Bill (Generates)   | 1 : 1       | Total on Bill        | Every reservation generates exactly one bill.                                                                |

### Assumptions
- A customer can make multiple table reservations.
- Every reservation is assigned to exactly one table.
- A table can be reserved multiple times on different dates or time slots.
- Each reservation is served by one waiter, while a waiter can serve many reservations.
- A reservation may include multiple food orders.
- Each order contains one or more dishes.
- Every dish belongs to one food category.
- A reservation generates exactly one final bill.
- Billing is done per reservation, not per individual order.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
