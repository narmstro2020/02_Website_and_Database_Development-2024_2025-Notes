
# Relational Database Concepts Tutorial (Without SQL)

## 1. Introduction to Relational Databases

A **relational database** is a type of database that stores and provides access to data points that are related to each other. In this model, data is organized into tables, known as relations. These tables are composed of rows and columns, where each row represents a single record, and each column represents an attribute of the record.

### Key Terms:
- **Table**: A structured set of data, similar to a spreadsheet, where rows represent individual entries and columns represent attributes of these entries.
- **Row (Record/Tuple)**: A single, structured data entry in a table.
- **Column (Field/Attribute)**: Defines a specific type of data to be stored in each record. For example, "Name" or "Email" in a "Customers" table.
- **Primary Key**: A column or set of columns that uniquely identifies each record in a table.
- **Foreign Key**: A column in one table that creates a link between the data in two tables by referring to the primary key of another table.

## 2. Relational Database Structure

In a relational database, data is structured in tables that can be related to each other. For example:

### Customers Table

| CustomerID (PK) | Name       | Email            |
|-----------------|------------|------------------|
| 1               | John Doe   | john@example.com |
| 2               | Jane Smith | jane@example.com |

### Orders Table

| OrderID (PK) | CustomerID (FK) | OrderDate   |
|--------------|------------------|-------------|
| 101          | 1                | 2024-01-15  |
| 102          | 2                | 2024-01-16  |

## 3. Relationships in Relational Databases

There are three main types of relationships:

### 1. One-to-One (1:1)
A single record in one table is related to a single record in another table. 

### 2. One-to-Many (1:N)
A single record in one table is associated with multiple records in another table.

### 3. Many-to-Many (N:M)
Records in one table are associated with multiple records in another table, and vice versa.


## 4. Normalization in Relational Databases

**Normalization** is the process of organizing data within a database to reduce redundancy and ensure data integrity.

### First Normal Form (1NF)
Each table cell should contain only atomic values, and each record must be unique.

### Second Normal Form (2NF)
All non-primary key attributes must be fully dependent on the primary key.

### Third Normal Form (3NF)
All columns must be dependent on the primary key and nothing else.

## 5. Example of Normalizing a Database

### Unnormalized Table

| StudentID | StudentName  | CourseName   | InstructorName | InstructorPhone |
|-----------|--------------|--------------|----------------|-----------------|
| 1         | Alice Smith  | Math 101     | Dr. Johnson    | 555-1234        |
| 2         | Bob Jones    | Math 101     | Dr. Johnson    | 555-1234        |
| 3         | Alice Smith  | Physics 101  | Dr. Lee        | 555-5678        |

### Step 1: First Normal Form (1NF)
Ensure that each column contains atomic values and each record is unique.

### Step 2: Second Normal Form (2NF)
Eliminate partial dependencies by creating separate tables.

### Step 3: Third Normal Form (3NF)
Remove transitive dependencies.

### Final Normalized Structure (3NF)

#### Students Table

| StudentID | StudentName  |
|-----------|--------------|
| 1         | Alice Smith  |
| 2         | Bob Jones    |
| 3         | Alice Smith  |

#### Courses Table

| CourseName   | InstructorName |
|--------------|----------------|
| Math 101     | Dr. Johnson    |
| Physics 101  | Dr. Lee        |

#### Instructors Table

| InstructorName | InstructorPhone |
|----------------|-----------------|
| Dr. Johnson    | 555-1234        |
| Dr. Lee        | 555-5678        |

#### Students and Courses Table

| StudentID | CourseName   |
|-----------|--------------|
| 1         | Math 101     |
| 2         | Physics 101  |

## 6. Entity-Relationship (ER) Diagrams

An **Entity-Relationship Diagram (ERD)** is a graphical representation of the entities (tables) in a database and their relationships.

### Components of an ER Diagram:
- **Entity**: Represents a table in the database.
- **Attribute**: Attributes are the columns of a table.
- **Relationship**: Relationships between entities.
- **Primary Key (PK)**: The unique identifier for each entity.
- **Foreign Key (FK)**: A reference to a primary key in another entity.

### Example of an ER Diagram:
```
    +------------+         +------------+
    | Customers  |         |   Orders   |
    +------------+         +------------+
    | CustomerID | <------ | OrderID    |
    | Name       |         | OrderDate  |
    | Email      |         | CustomerID |
    +------------+         +------------+
          |                       |
          |-----------------------|
            One-to-Many Relationship
```

### Steps to Create an ER Diagram:
1. **Identify Entities**: Determine the main entities in your database.
2. **Identify Attributes**: List the key attributes for each entity.
3. **Identify Relationships**: Define how the entities relate to each other.
4. **Draw the ER Diagram**: Use rectangles for entities, ovals for attributes, and diamonds for relationships.

### Types of Relationships in ER Diagrams:
- **One-to-One (1:1)**: Example: A person and their passport.
- **One-to-Many (1:N)**: Example: A customer and their orders.
- **Many-to-Many (N:M)**: Example: Students and courses.

