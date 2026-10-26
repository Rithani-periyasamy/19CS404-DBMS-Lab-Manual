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
![ER Diagram](er_diagram_fitness.png)
<img width="1077" height="741" alt="image" src="https://github.com/user-attachments/assets/89ace934-f400-490e-8525-a3585a469fdc" />


### Entities and Attributes

1.Members: Member_ID (Primary Key), Name, Contact_Number, Address.

2.Program: Program_ID (Primary Key), Type, Duration.

3.Trainers: Trainer_ID (Primary Key), Name, Specialization, Contact_Number.

4.Payment: Payment_ID (Primary Key), Amount, Mode, Due_Date.

### Relationships and Constraints

1.Members — Joins → Program: A member can join multiple programs, and each program can have multiple members.

2.Program — Pays → Payment: Payments are made by members for program fees. Each payment is associated with the member making the payment and the relevant program.

3.Trainers — Choose → Payment: This relationship in the diagram should be corrected. Trainers are assigned to programs, and members make payments for memberships or training sessions. Payment should not be directly associated with trainers unless it represents trainer salary payments.

### Assumptions
1.Every user must register as a member before accessing gym services.

2.Each member has a unique Member_ID and contact number.

3.Each program has a unique Program_ID.

4.Each trainer has a unique Trainer_ID.

5.A member can join multiple programs, and a program can have multiple members.

6.A program can be conducted by multiple trainers, and a trainer can conduct multiple programs.

7.Every payment has a unique Payment_ID.

8.Payments record the amount, payment mode, and due date.

9.Payments are associated with the member and program for which the payment is made.

10.All primary keys must be unique, and foreign keys must refer to valid records.

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
![ER Diagram](er_diagram_library.png)
<img width="1292" height="637" alt="image" src="https://github.com/user-attachments/assets/93168248-84a0-46bd-9d65-4ac237eaf8ac" />


### Entities and Attributes

1.MEMBER : memb_id(PK), memb_name, contact no, date
2.LOAN : loan_date ,due_date, return_date ,fine memb_id(FK) ,book_id(FK), loan_id(PK)
3.BOOK : Title Author , Category ,book_id(PK)
4.Event : event_id(PK), event_name ,event_date ,room_id(FK) 
5.Speaker : speaker_id(PK), name 
6.Room : room_id(PK) ,room_name ,capacity ,purpose

### Relationships and Constraints
1.Member — Loan — Book: A member can borrow many books.

2.Member — Event: A member can register for many events, and an event can have many members.

3.Event — Speaker: An event can have multiple speakers.

4.Room — Event: A room can host many events at different times; each event uses one room.

5.Category — Book: Each book belongs to one category.

6.Loan — Fine: A late return may generate a fine.


### Assumptions
1.A member must be registered before borrowing books or registering for events.
2.Member contact number is unique.
3.Each loan refers to a single book and a single member.
4.Loan must have both a loan date and due date.
5.Every book belongs to exactly one category

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
![ER Diagram](er_diagram_restaurant.png)
<img width="1267" height="642" alt="image" src="https://github.com/user-attachments/assets/0bf7cc81-ed78-42fd-8095-289a9aa798ba" />


### Entities and Attributes

1. Customer
- customerID (PK)
- Name
- Phone no
2. Reservation
- reservationID (PK)
- Reservation date and time
- customerID (FK)
3. Table
- tableID (PK)
- Table number
- Capacity
- categoryID (FK)
4. Category
- categoryID (PK)
- Category Name
5. Dish
- dishID (PK)
- Name
- Price
- categoryID (FK)
6. Order
- orderID (PK)
- Order time
- reservationID (FK)
- waiterID (FK)
7. Bill
- billID (PK)
- Total amount
- orderID (FK)
8. Waiter
- waiterID (PK)
- Name
- Phone no

### Relationships and Constraints

1.Customer ↔ Reservation: One customer books many reservations. Each reservation belongs to one customer. (1:N)

2.Reservation ↔ Table: One reservation is assigned to one table. A table can be assigned to many reservations (over time). (1:N)

3.Reservation ↔ Order: One reservation generates one or many orders. Each order belongs to exactly one reservation. (1:N)

4.Waiter ↔ Order: One waiter serves many orders. Each order is served by exactly one waiter. (1:N)

5.Order ↔ Bill: Each order produces one bill. Each bill is linked to only one order. (1:1)

6.Bill ↔ Dish: A bill contains many dishes. Each dish can appear in many bills. (M:N)

### Assumptions
1.A customer must register before making a reservation.

2.Every reservation requires a valid and unique customerID.

3.A table may serve multiple reservations, but not simultaneously.

4.Each order must be served by exactly one waiter.

5.A customer can have multiple reservations.

6.There is no double-booking of the same table at the same date and time.

7.Contact details like phone number are assumed unique.

8.Order time is recorded.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
