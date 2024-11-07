
# PostgreSQL and DataGrip SQL Tutorial Part 01

This tutorial will guide you through setting up PostgreSQL with DataGrip, creating databases and tables, and performing SQL operations such as CRUD (Create, Read, Update, Delete), as well as advanced operations like joins, views, and transactions.

---

## 1. Setting Up PostgreSQL and DataGrip

- **Install PostgreSQL**: Download and install PostgreSQL from the [official PostgreSQL website](https://www.postgresql.org/).
- **Install DataGrip**: Get DataGrip from [JetBrains](https://www.jetbrains.com/datagrip/).
- **Connect DataGrip to PostgreSQL**:
  - Open DataGrip and create a new PostgreSQL connection.
  - Enter your PostgreSQL host, port, username, and password.
  - Test the connection and click **OK** to finalize.

---

## 2. Creating a Database

Run this command in the Query Console to create a new database:

```sql
CREATE DATABASE my_database;
```

> **Note**: PostgreSQL doesn’t allow switching databases within the same connection. After creating the database, connect to it by opening a new Query Console.

---

## 3. Creating Tables

With the Query Console connected to your database, create a new table using the following syntax:

```sql
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Explanation
- `user_id SERIAL PRIMARY KEY`: Auto-incrementing integer serving as the primary key.
- `username VARCHAR(50) UNIQUE NOT NULL`: Stores unique usernames up to 50 characters, cannot be `NULL`.
- `created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP`: Automatically sets to the current timestamp upon record creation.

---

## 4. Inserting Data into Tables

Use `INSERT INTO` to add data to the table:

```sql
INSERT INTO users (username, email) 
VALUES ('john_doe', 'john.doe@example.com');
```

Add multiple records in one query:

```sql
INSERT INTO users (username, email) 
VALUES 
    ('jane_smith', 'jane.smith@example.com'),
    ('bob_jones', 'bob.jones@example.com');
```

