
# PostgreSQL and DataGrip SQL Tutorial Part 02

This tutorial will guide you through setting up PostgreSQL with DataGrip, creating databases and tables, and performing SQL operations such as CRUD (Create, Read, Update, Delete), as well as advanced operations like joins, views, and transactions.

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
