# Football Ticket Booking System

A comprehensive database design project for a Football Ticket Booking System, featuring ERD modeling, relational database schema design, and advanced SQL queries.

## Live Links

| Resource | Link |
|----------|------|
| **ERD Diagram** | [View ERD](https://shorturl.at/4Fj8M) |
| **GitHub Repository** | [Football_Ticket_Booking_DB_Design](https://github.com/Ahammad204/Football_Ticket_Booking_DB_Design) |

## Project Overview

This project implements a simplified **Football Ticket Booking System** database that manages football fans purchasing tickets, upcoming tournament matches, and individual ticket booking receipts. The system demonstrates relational database design principles with proper entity relationships and constraint implementations.

## Database Schema

### Tables

| Table | Description |
|-------|-------------|
| **Users** | Stores administrative staff and customer information |
| **Matches** | Catalogs tournament events, stadium logistics, and ticket pricing |
| **Bookings** | Records individual ticket purchases linking users to matches |

### Entity Relationships

```
┌─────────────┐       ┌─────────────┐       ┌─────────────┐
│    Users    │       │   Bookings  │       │   Matches   │
├─────────────┤       ├─────────────┤       ├─────────────┤
│ user_id (PK)│◄──────│ user_id (FK)│       │ match_id(PK)│
│ full_name   │  1:M  │ match_id(FK)│──────►│ fixture     │
│ email       │       │ booking_id  │  M:1  │ tournament  │
│ role        │       │ seat_number │       │ base_price  │
│ phone_number│       │ payment_stat│       │ match_stat  │
└─────────────┘       │ total_cost  │       └─────────────┘
                      └─────────────┘
```

### Relationship Types

- **One-to-Many:** One User → Many Bookings
- **Many-to-One:** Many Bookings → One Match
- **One-to-One (Logical):** Each booking maps one user to one match

## SQL Queries

The project includes 7 comprehensive SQL queries demonstrating various database concepts:

| Query | Description | Concepts Used |
|-------|-------------|---------------|
| **Query 1** | Retrieve Champions League matches with 'Available' status | `WHERE`, `AND` |
| **Query 2** | Search users by name pattern (case-insensitive) | `LIKE`, `ILIKE` |
| **Query 3** | Find bookings with missing payment status | `IS NULL`, `COALESCE` |
| **Query 4** | Retrieve booking details with user and match info | `INNER JOIN` |
| **Query 5** | List all users including those without bookings | `LEFT JOIN` |
| **Query 6** | Find bookings above average cost | Subquery, `AVG()` |
| **Query 7** | Get top 2 most expensive matches (skip first) | `ORDER BY`, `LIMIT`, `OFFSET` |

## Technology Stack

- **Database:** PostgreSQL
- **Schema Design:** Draw.io / Lucidchart
- **Query Language:** SQL (DDL + DML)

## Project Structure

```
Football_Ticket_Booking_DB_Design/
├── QUERY.sql                              # Database schema and SQL queries
├── FootballTicketBookingSystem.drawio     # ERD diagram source file
├── README.md                              # Project documentation
└── task.md                                # Assignment requirements
```

## Getting Started

### Prerequisites

- PostgreSQL 12+ installed
- SQL client (pgAdmin, DBeaver, or similar)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Ahammad204/Football_Ticket_Booking_DB_Design.git
   cd Football_Ticket_Booking_DB_Design
   ```

2. **Create the database**
   ```sql
   CREATE DATABASE football_ticket_booking;
   ```

3. **Run the schema and queries**
   ```bash
   psql -d football_ticket_booking -f QUERY.sql
   ```

## Sample Data

### Users Table
| user_id | full_name | email | role | phone_number |
|---------|-----------|-------|------|--------------|
| 1 | Tanvir Rahman | tanvir@mail.com | Football Fan | +8801711111111 |
| 2 | Asif Haque | asif@mail.com | Football Fan | +8801722222222 |
| 3 | Sajjad Rahman | sajjad@mail.com | Ticket Manager | +8801733333333 |
| 4 | Jannat Ara | jannat@mail.com | Football Fan | NULL |

### Matches Table
| match_id | fixture | tournament_category | base_ticket_price | match_status |
|----------|---------|---------------------|-------------------|--------------|
| 101 | Real Madrid vs Barcelona | Champions League | 150 | Available |
| 102 | Man City vs Liverpool | Premier League | 120 | Selling Fast |
| 103 | Bayern Munich vs PSG | Champions League | 130 | Available |
| 104 | AC Milan vs Inter Milan | Serie A | 90 | Sold Out |
| 105 | Juventus vs Roma | Serie A | 80 | Available |

## Database Constraints

| Constraint Type | Implementation |
|-----------------|----------------|
| **Primary Keys** | `user_id`, `match_id`, `booking_id` |
| **Foreign Keys** | `Bookings.user_id` → `Users.user_id`, `Bookings.match_id` → `Matches.match_id` |
| **Unique** | `Users.email` |
| **Check** | Role validation, non-negative prices, status enums |
| **Not Null** | Essential fields enforced |

## Key Learnings

- Entity Relationship Diagram (ERD) design with Crow's Foot notation
- Primary Key and Foreign Key implementations
- Referential integrity and cascade rules
- Complex SQL joins (INNER, LEFT)
- Aggregate functions and subqueries
- NULL handling with COALESCE
- Pattern matching with LIKE/ILIKE
- Pagination with LIMIT and OFFSET

## Author

**Ahammad** - [GitHub Profile](https://github.com/Ahammad204)

## License

This project is for educational purposes as part of ALevel-2 Mission-03 assignment.

---

<p align="center">Built with PostgreSQL and structured SQL queries</p>
