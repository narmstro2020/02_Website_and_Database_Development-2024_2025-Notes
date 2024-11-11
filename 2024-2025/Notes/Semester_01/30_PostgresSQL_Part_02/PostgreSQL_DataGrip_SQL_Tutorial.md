
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