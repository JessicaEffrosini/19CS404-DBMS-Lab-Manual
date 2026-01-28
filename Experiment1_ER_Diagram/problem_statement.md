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

<img width="1145" height="745" alt="508790396-6caa47f0-dfbd-4a8b-8b77-96da233bfea7" src="https://github.com/user-attachments/assets/5ff9e808-7a37-48f5-9ddf-72d7f95cb493" />


### Entities and Attributes
| **Entity**   | **Attributes (PK, FK)**                             | **Notes**                          |
| ------------ | --------------------------------------------------- | ---------------------------------- |
| **Members**  | MemberID (PK), Name, ContactNumber, Address         | Stores details of gym members      |
| **Programs** | ProgramID (PK), Type, Duration, Fees                | Stores fitness program information |
| **Trainers** | TrainerID (PK), Name, Specialization, ContactNumber | Stores trainer details             |
| **Payments** | PaymentID (PK), Amount, PaymentType, DueDate        | Stores payment details             |


### Relationships and Constraints

| **Relationship** | **Cardinality** | **Participation** | **Notes**                                                                                    |
| ---------------- | --------------- | ----------------- | -------------------------------------------------------------------------------------------- |
| **Joins**        | M : N           | Partial – Partial | A member can join multiple programs and a program can have many members                      |
| **Conducts**     | M : N           | Partial – Partial | A trainer can conduct multiple programs and a program may have multiple trainers             |
| **Duty**         | 1 : M           | Partial – Total   | A trainer can be responsible for multiple payments; each payment must be linked to a trainer |


### Assumptions
A member can enroll in more than one program

A program can have multiple members and trainers

Trainers handle payment-related duties

Payments include membership or program fees

Each payment record belongs to only one trainer

Contact numbers are assumed to be single-valued attributes


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
<img width="1148" height="694" alt="508790573-7c4cbc21-e7ab-45d1-bc6e-c300c8a7cc73" src="https://github.com/user-attachments/assets/7614e8d8-7cf3-43ce-a9a8-8d7e2f1493a4" />

### Entities and Attributes

| **Entity**  | **Attributes (PK, FK)**                                                                   | **Notes**                            |
| ----------- | ----------------------------------------------------------------------------------------- | ------------------------------------ |
| **Member**  | memb_id (PK), memb_name, contact_no, date                                                 | Stores library member details        |
| **Loan**    | loan_id (PK), loan_date, return_date, due_date, fine, purpose, memb_id (FK), book_id (FK) | Stores book loan transaction details |
| **Book**    | book_id (PK), title, author, category                                                     | Stores book information              |
| **Event**   | event_id (PK), event_name, event_date                                                     | Stores details of events conducted   |
| **Room**    | room_id (PK), room_name, capacity                                                         | Stores room details for events       |
| **Speaker** | speaker_id (PK), name                                                                     | Stores speaker details for events    |


### Relationships and Constraints

| **Relationship** | **Cardinality** | **Participation** | **Notes**                                                                     |
| ---------------- | --------------- | ----------------- | ----------------------------------------------------------------------------- |
| **Can Have**     | 1 : M           | Partial – Total   | A member can have multiple loans; every loan must belong to a member          |
| **Have**         | M : 1           | Total – Partial   | Each loan is for one book; a book may or may not be loaned                    |
| **Can Register** | M : N           | Partial – Partial | A member may register for multiple events; an event may have multiple members |
| **Occurs**       | 1 : 1           | Total – Total     | Each event occurs in exactly one room and each room hosts one event at a time |
| **Have**         | 1 : M           | Partial – Partial | A room can have multiple speakers; a speaker may speak in multiple rooms      |


### Assumptions
Each member is uniquely identified by a Member ID.

A member can have multiple loans, but each loan belongs to only one member.

Each loan is issued for only one book at a time.

A book may or may not be loaned at a given time.

Fine is applicable only if the book is returned after the due date.

A member can register for multiple events, and an event can have multiple members.

Each event occurs in exactly one room.
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
<img width="1219" height="703" alt="508790743-dafe9e85-23e8-4e68-bf22-4efd8818f37c" src="https://github.com/user-attachments/assets/a0c6fb59-b012-4a43-9e6b-7b21953fcc88" />


### Entities and Attributes
| **Entity**      | **Attributes (PK, FK)**                                                | **Notes**                        |
| --------------- | ---------------------------------------------------------------------- | -------------------------------- |
| **Customer**    | customerID (PK), Name, PhoneNo                                         | Stores customer details          |
| **Reservation** | reservationID (PK), ReservationDateTime, customerID (FK), tableID (FK) | Stores table reservation details |
| **Table**       | tableID (PK), TableNumber, Capacity, categoryID (FK)                   | Stores restaurant table details  |
| **Category**    | categoryID (PK), CategoryName                                          | Stores table categories          |
| **Waiter**      | waiterID (PK), Name, PhoneNo                                           | Stores waiter information        |
| **Order**       | orderID (PK), OrderTime, reservationID (FK), waiterID (FK)             | Stores order details             |
| **Bill**        | billID (PK), TotalAmount, orderID (FK)                                 | Stores billing information       |
| **Dish**        | dishID (PK), Name, Price, categoryID (FK)                              | Stores dish details              |


### Relationships and Constraints

| **Relationship**   | **Cardinality** | **Participation** | **Notes**                                                                       |
| ------------------ | --------------- | ----------------- | ------------------------------------------------------------------------------- |
| **Books**          | 1 : M           | Partial – Total   | A customer can book many reservations; each reservation belongs to one customer |
| **Is Assigned To** | M : 1           | Total – Partial   | Each reservation is assigned one table; a table may have no reservation         |
| **Belongs To**     | M : 1           | Total – Partial   | Each table belongs to one category                                              |
| **Serves**         | 1 : M           | Partial – Total   | A waiter can serve multiple orders                                              |
| **Generates**      | 1 : M           | Partial – Total   | One reservation can generate multiple orders                                    |
| **Produces**       | 1 : 1           | Total – Total     | Each order generates exactly one bill                                           |
| **Contains**       | M : N           | Total – Partial   | A bill contains multiple dishes                                                 |


### Assumptions
Each customer is uniquely identified by a customerID.

A customer can make multiple reservations, but each reservation belongs to only one customer.

Each reservation is assigned to exactly one table.

A table may or may not be reserved at a given time.

Tables and dishes are classified using categories.

A waiter can serve multiple orders, but each order is served by only one waiter.

A reservation may generate one or more orders.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
