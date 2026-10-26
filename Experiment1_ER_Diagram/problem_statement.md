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
<img width="1186" height="827" alt="0e924954-dbbf-449e-9162-a10e923e2806" src="https://github.com/user-attachments/assets/0ac5ecca-b605-4eda-a949-2ddf09bdf23c" />

<img width="960" height="1280" alt="WhatsApp Image 2026-10-26 at 3 53 27 PM" src="https://github.com/user-attachments/assets/bac7f522-9e17-44c7-865c-85b8b3a84da7" />



### Entities and Attributes

| Entity                       | Attributes (PK, FK)                                      | Notes                         |
|------------------------------|---------------------------------------------------------|-------------------------------|
| MEMBER                       | MEMBER_ID (PK), MEM_NAME, MEM_ADDRESS, MEM_START_DATE   | Stores member details         |
| PROGRAMS                     | PROGRAM_ID (PK), PROGRAM_NAME                           | Stores gym program details    |
| TRAINER                      | TRAINER_ID (PK), TRAINER_NAME, SPECIALIZED, TRAINER_NO  | Stores trainer details        |
| PERSONAL_TRAINING_SESSIONS   | SESSION_ID (PK), MEMBER_ID (FK), TRAINER_ID (FK), SESSION_DATE | Stores training sessions |
| ATTENDANCE                   | ATTENDANCE_ID (PK), SESSION_ID (FK), MEMBER_ID (FK)    | Records member attendance    |
| PAYMENT                      | PAYMENT_ID (PK), MEMBER_ID (FK), AMOUNT, METHOD        | Stores payment details        |


### Relationships and Constraints
| Relationship                                  | Cardinality | Participation        | Notes                              |
|-----------------------------------------------|-------------|----------------------|------------------------------------|
| MEMBER — HAS — PROGRAMS                       | M:N         | Partial, Partial     | Members join gym programs          |
| MEMBER — BOOKS — PERSONAL_TRAINING_SESSIONS   | 1:M         | Partial, Total       | Members book training sessions     |
| PROGRAMS — HAS — TRAINER                      | M:N         | Partial, Partial     | Trainers handle gym programs       |
| MEMBER — HAS — ATTENDANCE                     | 1:M         | Partial, Total       | Records member attendance          |
| PERSONAL_TRAINING_SESSIONS — TRACKED — PAYMENT| 1:1         | Partial, Partial     | Tracks training session payments   |


### Assumptions
1)Each member has a unique member ID, even though it is not shown as an attribute in the diagram.

2)Each trainer has a unique trainer ID, and each training session records the member, trainer, and session date.

3)Each payment stores the amount and payment method and is associated with a member or training session as represented in the diagram.

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
<img width="1232" height="822" alt="74a22a21-1103-45a8-b0ff-c8200d577ac3" src="https://github.com/user-attachments/assets/66ce0fbf-c58e-4b03-a677-74df5824515c" />

<img width="960" height="1280" alt="WhatsApp Image 2026-10-26 at 3 53 27 PM (1)" src="https://github.com/user-attachments/assets/38967780-d376-495e-8ca0-e368123123d1" />


### Entities and Attributes
| Entity | Attributes (PK, FK)                                      | Notes                         |
|--------|-----------------------------------------------------------|-------------------------------|
| MEMBER | MEMBER_ID (PK), NAME, EMAIL, PHONE                        | Stores member details         |
| EVENT  | ID (PK), NAME, DEPT                                       | Stores event details          |
| SPEAKER| SPEAKER_ID (PK), NAME, BIO, CONTACT                       | Stores speaker details        |
| BOOKS  | BOOK_ID (PK), TITLE, AUTHOR, PUB_YEAR                      | Stores library book details   |
| ROOM   | ROOM_ID (PK), ROOM_NAME, CAPACITY, TYPE                   | Stores room details           |
| FINE   | FINE_ID (PK), AMOUNT, FINE_DATE, STATUS                   | Stores fine details           |

### Relationships and Constraints
| Relationship       | Cardinality | Participation    | Notes                                  |
|--------------------|-------------|------------------|----------------------------------------|
| MEMBER — REGISTER — EVENT | M:N   | Partial, Partial | Members can register for multiple events |
| MEMBER — BORROWS — BOOKS | M:N   | Partial, Partial | Members can borrow multiple books       |
| EVENT — HAS — SPEAKER    | 1:M   | Partial, Total   | An event can have multiple speakers     |
| MEMBER — BOOKED IN — ROOM| M:N   | Partial, Partial | Members book rooms for events           |
| BOOKS — OVERDUE — FINE   | 1:1   | Partial, Partial | An overdue book may generate a fine     |

### Assumptions
 1)Each member is identified by a unique MEMBER_ID.
 
 2)Each event has a unique ID and can have multiple speakers.
 
 3)Members can borrow books and register for events.
 
 4)Rooms have a name, capacity, and type for booking purposes.

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
<img width="1204" height="827" alt="86bdc144-d3aa-4836-9c24-979b075d965a" src="https://github.com/user-attachments/assets/cc4e3785-4867-45d2-9949-bc2ad741fabc" />

<img width="960" height="1280" alt="WhatsApp Image 2026-10-26 at 3 53 27 PM (2)" src="https://github.com/user-attachments/assets/39badff9-c182-4f05-aaaf-2b1fcb773353" />


### Entities and Attributes
| Entity       | Attributes (PK, FK)                                              | Notes                          |
|--------------|------------------------------------------------------------------|--------------------------------|
| CUSTOMER     | CUSTOMER_ID (PK), NAME, PHONE, EMAIL                             | Stores customer details        |
| RESERVATION  | RESERVATION_ID (PK), CUSTOMER_ID (FK), DATE, TIME, NUM_GUESTS    | Stores reservation details     |
| ORDER        | ORDER_ID (PK), RESERVATION_ID (FK), ORDER_DATE, STATUS           | Stores order details           |
| ORDER_ITEM   | ORDER_ITEM_ID (PK), ORDER_ID (FK), QUANTITY, PRICE               | Stores ordered item details    |
| BILL         | BILL_ID (PK), RESERVATION_ID (FK), TOTAL_AMOUNT, PAYMENT_METHOD, BILL_DATE | Stores billing details |
| WAITERS      | WAITER_ID (PK), NAME, PHONE                                      | Stores waiter details          |


### Relationships and Constraints

| Relationship                  | Cardinality | Participation    | Notes                                  |
|-------------------------------|-------------|------------------|----------------------------------------|
| CUSTOMER — MAKES — RESERVATION| 1:M         | Partial, Total   | A customer can make multiple reservations |
| RESERVATION — PLACES — ORDER  | 1:M         | Partial, Total   | A reservation can have multiple orders |
| ORDER — CONTAINS — ORDER_ITEM | 1:M         | Partial, Total   | An order contains multiple order items |
| RESERVATION — HAS — BILL      | 1:1         | Partial, Total   | Each reservation has a bill            |
| WAITERS — SERVERS — RESERVATION| M:N        | Partial, Partial | Waiters serve reservations             |
| ORDER — CONNECTED TO — BILL   | M:1         | Partial, Partial | Orders are included in a bill          |

### Assumptions
  1)Each customer has a unique CUSTOMER_ID.
  
  2)Each reservation has a unique RESERVATION_ID and belongs to one customer.
  
  3)A reservation can contain multiple orders, and each order contains multiple order items.
  
  4)Each order item records its quantity and price.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
