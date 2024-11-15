
# PostgreSQL and DataGrip SQL Tutorial Part 03

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