
# PostgreSQL and DataGrip SQL Tutorial

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

---

## 5. Reading Data from Tables

- **Select all records**:

  ```sql
  SELECT * FROM users;
  ```

- **Select specific columns**:

  ```sql
  SELECT username, email FROM users;
  ```

- **Filtering records** with `WHERE`:

  ```sql
  SELECT * FROM users 
  WHERE username = 'john_doe';
  ```

- **Ordering results**:

  ```sql
  SELECT * FROM users 
  ORDER BY created_at DESC;
  ```

---

## 6. Updating Data in Tables

- Update a record’s data:

  ```sql
  UPDATE users 
  SET email = 'john.updated@example.com' 
  WHERE username = 'john_doe';
  ```

- Update multiple fields:

  ```sql
  UPDATE users 
  SET email = 'jane.updated@example.com', username = 'jane_updated' 
  WHERE user_id = 2;
  ```

---

## 7. Deleting Data from Tables

- **Delete specific records**:

  ```sql
  DELETE FROM users 
  WHERE username = 'bob_jones';
  ```

- **Delete all records** (use with caution!):

  ```sql
  DELETE FROM users;
  ```

---

## 8. Adding Constraints and Modifying Table Structure

- **Adding a new column**:

  ```sql
  ALTER TABLE users 
  ADD COLUMN phone_number VARCHAR(15);
  ```

- **Removing a column**:

  ```sql
  ALTER TABLE users 
  DROP COLUMN phone_number;
  ```

- **Adding a Foreign Key**:

  ```sql
  CREATE TABLE orders (
      order_id SERIAL PRIMARY KEY,
      user_id INTEGER REFERENCES users(user_id),
      order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

---

## 9. Using Joins to Combine Tables

- **Inner Join**: Retrieve related records from two tables.

  ```sql
  SELECT users.username, orders.order_date 
  FROM users 
  INNER JOIN orders ON users.user_id = orders.user_id;
  ```

- **Left Join**: Retrieves all records from the left table and matched records from the right table.

  ```sql
  SELECT users.username, orders.order_date 
  FROM users 
  LEFT JOIN orders ON users.user_id = orders.user_id;
  ```

---

## 10. Aggregate Functions and Grouping Data

- **Count total users**:

  ```sql
  SELECT COUNT(*) AS total_users FROM users;
  ```

- **Group by and aggregate**:

  ```sql
  SELECT user_id, COUNT(order_id) AS total_orders 
  FROM orders 
  GROUP BY user_id;
  ```

---

## 11. Views and Indexes

- **Creating a View**:

  ```sql
  CREATE VIEW user_orders AS 
  SELECT users.username, orders.order_date 
  FROM users 
  JOIN orders ON users.user_id = orders.user_id;
  ```

- **Creating an Index**:

  ```sql
  CREATE INDEX idx_username ON users(username);
  ```

---

## 12. Using Transactions

- **Begin a transaction**:

  ```sql
  BEGIN;
  ```

- **Rollback if something goes wrong**:

  ```sql
  ROLLBACK;
  ```

- **Commit the transaction**:

  ```sql
  COMMIT;
  ```

---

This guide covers essential SQL operations, making the Query Console in DataGrip a powerful tool for interacting directly with PostgreSQL.
