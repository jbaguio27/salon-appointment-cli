# Salon 💇‍♀️✨🧴 Appointment Scheduler CLI

A simple command line application that allows users to book salon appointments.  
Built with Bash and PostgreSQL. The script interacts with a database to manage customers, services, and appointments.

This project demonstrates basic database design, Bash scripting, and SQL queries working together in a small CLI system.

---

## Features

- Display available salon services
- Validate service selection
- Register new customers using phone number
- Store customer data in a PostgreSQL database
- Schedule appointments with selected service and time
- Retrieve existing customers automatically
- Simple CLI workflow

---

## Technologies Used

- Bash
- PostgreSQL
- SQL
- Linux Terminal

---

## Database Schema

### customers
Stores customer information.

| Column | Type | Description |
|------|------|-------------|
| customer_id | SERIAL | Primary key |
| phone | VARCHAR | Unique phone number |
| name | VARCHAR | Customer name |

### services
Stores salon services.

| Column | Type | Description |
|------|------|-------------|
| service_id | SERIAL | Primary key |
| name | VARCHAR | Service name |

### appointments
Stores appointment records.

| Column | Type | Description |
|------|------|-------------|
| appointment_id | SERIAL | Primary key |
| customer_id | INT | Foreign key to customers |
| service_id | INT | Foreign key to services |
| time | VARCHAR | Appointment time |

---

## Project Structure

```
salon-appointment-cli
│
├── salon.sh
├── README.md
```

---

## Setup Instructions

### 1. Clone the repository

```
git clone https://github.com/yourusername/salon-appointment-cli.git
cd salon-appointment-cli
```

### 2. Create the PostgreSQL database

```
createdb salon
```

### 3. Create tables

```
CREATE TABLE customers (
customer_id SERIAL PRIMARY KEY,
phone VARCHAR UNIQUE NOT NULL,
name VARCHAR NOT NULL
);

CREATE TABLE services (
service_id SERIAL PRIMARY KEY,
name VARCHAR NOT NULL
);

CREATE TABLE appointments (
appointment_id SERIAL PRIMARY KEY,
customer_id INT REFERENCES customers(customer_id),
service_id INT REFERENCES services(service_id),
time VARCHAR NOT NULL
);
```

### 4. Insert services

```
INSERT INTO services(service_id, name) VALUES (1, 'cut');
INSERT INTO services(service_id, name) VALUES (2, 'color');
INSERT INTO services(service_id, name) VALUES (3, 'perm');
INSERT INTO services(service_id, name) VALUES (4, 'style');
INSERT INTO services(service_id, name) VALUES (5, 'trim');
```

### 5. Give execution permission

```
chmod +x salon.sh
```

### 6. Run the program

```
./salon.sh
```

---

## Example Output

```
~~~~~ MY SALON ~~~~~

Welcome to My Salon, how can I help you?

1) cut
2) color
3) perm
4) style
5) trim
1

What's your phone number?
555-555-5555

I don't have a record for that phone number, what's your name?
Fabio

What time would you like your cut, Fabio?
10:30

I have put you down for a cut at 10:30, Fabio.
```

---

## What This Project Demonstrates

- Bash scripting with functions and conditionals
- CLI input handling using `read`
- SQL queries executed inside Bash
- Database relationships with foreign keys
- Simple CRUD operations

---

## Future Improvements

- Add service management
- Validate appointment time format
- Prevent duplicate bookings
- Convert CLI to a web interface
- Add logging and error handling

---

## License

This project is open source and available for learning purposes.
