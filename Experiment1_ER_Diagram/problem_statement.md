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
*Paste or attach your diagram here*  

<img width="989" height="659" alt="image" src="https://github.com/user-attachments/assets/e6fc10a7-ea1d-4bea-aa09-f58a2c49a16a" />


### Entities and Attributes

| Entity          | Attributes (PK, FK)                                                                 | Notes                                  |
| --------------- | ----------------------------------------------------------------------------------- | -------------------------------------- |
| Member          | **MemberID (PK)**, Name, Phone, Email, MembershipType, StartDate                    | Gym member details                     |
| Program         | **ProgramID (PK)**, ProgramName, Duration, Fee                                      | Fitness programs (Yoga, Zumba, etc.)   |
| Trainer         | **TrainerID (PK)**, TrainerName, Phone, Specialization                              | Gym trainers                           |
| MemberProgram   | **MemberID (FK)**, **ProgramID (FK)**, JoinDate                                     | Records member enrollment in programs  |
| TrainerProgram  | **TrainerID (FK)**, **ProgramID (FK)**                                              | Records trainer assignment to programs |
| PersonalSession | **SessionID (PK)**, SessionDate, SessionTime, MemberID (FK), TrainerID (FK)         | Personal training bookings             |
| Attendance      | **AttendanceID (PK)**, AttendanceDate, Status, SessionID (FK), MemberID (FK)        | Attendance for training sessions       |
| Payment         | **PaymentID (PK)**, PaymentDate, Amount, PaymentType, MemberID (FK), SessionID (FK) | Membership and session payments        |


### Relationships and Constraints

| Relationship                       | Cardinality | Participation | Notes                                  |
| ---------------------------------- | ----------- | ------------- | -------------------------------------- |
| Member joins Program               | M:N         | Partial       | Implemented through **MemberProgram**  |
| Trainer conducts Program           | M:N         | Total         | Implemented through **TrainerProgram** |
| Member books Personal Session      | 1:M         | Partial       | A member can book multiple sessions    |
| Trainer conducts Personal Session  | 1:M         | Total         | A trainer can conduct many sessions    |
| Session has Attendance             | 1:M         | Total         | Attendance recorded for every session  |
| Member makes Payment               | 1:M         | Total         | Members make multiple payments         |
| Personal Session generates Payment | 1:0..1      | Partial       | Session payment only if applicable     |


### Assumptions
A member can enroll in multiple fitness programs.

A fitness program can have many members.

A trainer can teach multiple programs.

A program may have multiple trainers.

A member can book multiple personal training sessions.

Each personal training session is conducted by one trainer for one member.

Attendance is recorded for every personal training session.

Members pay for memberships and personal training sessions separately.

A session payment is optional if it is included in the membership plan.
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
*Paste or attach your diagram here*  
<img width="989" height="658" alt="image" src="https://github.com/user-attachments/assets/7cdccf50-78fa-45f9-94ce-a3f10ef0c356" />


### Entities and Attributes

| Entity           | Attributes (PK, FK)                                               | Notes                                         |
| ---------------- | ----------------------------------------------------------------- | --------------------------------------------- |
| **Member**       | **MemberID (PK)**, Name, Phone, Email                             | Library member details                        |
| **Book**         | **BookID (PK)**, Title, Author, Category                          | Books available in the library                |
| **Loan**         | **LoanID (PK)**, LoanDate, ReturnDate, MemberID (FK), BookID (FK) | Records borrowing and returning of books      |
| **Event**        | **EventID (PK)**, EventName, EventDate, RoomID (FK)               | Library cultural events                       |
| **Speaker**      | **SpeakerID (PK)**, SpeakerName                                   | Event speakers/authors                        |
| **Room**         | **RoomID (PK)**, RoomName, Capacity                               | Rooms used for events and study               |
| **Fine**         | **FineID (PK)**, Amount, LoanID (FK), MemberID (FK)               | Overdue fine details                          |
| **MemberEvent**  | **MemberID (FK)**, **EventID (FK)**                               | Junction entity for member event registration |
| **EventSpeaker** | **EventID (FK)**, **SpeakerID (FK)**                              | Junction entity for event speakers            |


### Relationships and Constraints

| Relationship               | Cardinality                  | Participation | Notes                                                                                |
| -------------------------- | ---------------------------- | ------------- | ------------------------------------------------------------------------------------ |
| **Member borrows Book**    | **M : N (via Loan)**         | Total         | Implemented through **Loan**, which stores loan and return dates.                    |
| **Member registers Event** | **M : N (via MemberEvent)**  | Partial       | Members may register for multiple events.                                            |
| **Event has Speaker**      | **M : N (via EventSpeaker)** | Total         | Each event has one or more speakers; a speaker may attend multiple events.           |
| **Event uses Room**        | **M : 1**                    | Total         | Each event is conducted in one room; a room may host many events at different times. |
| **Loan generates Fine**    | **1 : 0..1**                 | Partial       | A fine is generated only if the loan is overdue.                                     |
| **Member pays Fine**       | **1 : M**                    | Partial       | A member may have multiple fines.                                                    |

### Assumptions

A member can borrow multiple books.

A book can be borrowed multiple times but only by one member at a time.

Each loan records both loan date and return date.

A fine is generated only for overdue book returns.

Members can register for multiple library events.

An event may have one or more speakers.

A speaker can participate in multiple events.

One room is allocated to one event at a given time, but it can be reused for different events at different times.

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
*Paste or attach your diagram here*  

<img width="984" height="656" alt="image" src="https://github.com/user-attachments/assets/940bb68a-161b-40c8-9a72-9622812380f1" />

### Entities and Attributes

| Entity          | Attributes (PK, FK)                                                                      | Notes                                                                 |
| --------------- | ---------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Customer**    | **CustomerID (PK)**, Name, Phone                                                         | Restaurant customer details                                           |
| **Reservation** | **ReservationID (PK)**, Date, Time, Guests, CustomerID (FK), TableID (FK), WaiterID (FK) | Stores reservation information                                        |
| **Table**       | **TableID (PK)**, TableNo, Capacity                                                      | Dining tables in the restaurant                                       |
| **Order**       | **OrderID (PK)**, ReservationID (FK), OrderDate, OrderTime                               | Food order placed for a reservation                                   |
| **Dish**        | **DishID (PK)**, DishName, Price, CategoryID (FK)                                        | Menu items available                                                  |
| **Category**    | **CategoryID (PK)**, CategoryName                                                        | Dish categories such as Starter, Main Course, Dessert                 |
| **Bill**        | **BillID (PK)**, FoodCharge, ServiceCharge, TotalAmount, ReservationID (FK)              | Bill generated for a reservation                                      |
| **Waiter**      | **WaiterID (PK)**, WaiterName                                                            | Restaurant staff serving customers                                    |
| **OrderDish**   | **OrderID (FK)**, **DishID (FK)**, Quantity                                              | Junction entity to handle the M:N relationship between Order and Dish |

### Relationships and Constraints

| Relationship                      | Cardinality | Participation | Notes                                                                                                         |
| --------------------------------- | ----------- | ------------- | ------------------------------------------------------------------------------------------------------------- |
| **Customer reserves Reservation** | **1 : M**   | Total         | One customer can make multiple reservations.                                                                  |
| **Reservation assigned Table**    | **M : 1**   | Total         | Each reservation is assigned exactly one table.                                                               |
| **Reservation places Order**      | **1 : M**   | Total         | One reservation can include multiple food orders.                                                             |
| **Order contains Dish**           | **M : N**   | Total         | Implemented using **OrderDish**; each order contains multiple dishes and each dish can appear in many orders. |
| **Dish belongs Category**         | **M : 1**   | Total         | Every dish belongs to one category.                                                                           |
| **Reservation generates Bill**    | **1 : 1**   | Total         | Exactly one bill is generated for each reservation.                                                           |
| **Waiter serves Reservation**     | **1 : M**   | Total         | One waiter can serve multiple reservations, but each reservation is served by one waiter.                     |

### Assumptions

Customers can reserve a table in advance or walk in directly.

Each reservation is allocated to one dining table.

A customer can have multiple reservations on different dates.

A reservation may include multiple food orders.

Each order can contain multiple dishes.

A dish belongs to only one category (Starter, Main Course, Dessert, etc.).

One bill is generated for each reservation.

Food charge, service charge, and total amount are included in the bill.

One waiter can serve many reservations, but each reservation is handled by only one waiter.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
