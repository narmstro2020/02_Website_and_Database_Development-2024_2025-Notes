
# PostgreSQL and DataGrip SQL Tutorial Part 04

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