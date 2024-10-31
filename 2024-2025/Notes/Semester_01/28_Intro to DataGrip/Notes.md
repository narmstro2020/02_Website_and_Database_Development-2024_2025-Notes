
# PostgreSQL Tutorial Using DataGrip

This tutorial covers creating a PostgreSQL database, creating a table, and adding fields and records using DataGrip.

## Step 1: Setting Up DataGrip and Connecting to PostgreSQL
1. **Open DataGrip** and select **New Database Connection** from the welcome screen.
2. Choose **PostgreSQL** from the list.
3. **Configure Connection**:
   - Enter your **host** (usually `localhost` for local PostgreSQL setups).
   - Enter the **port** (default is `5432`).
   - Add your **database name**, **username**, and **password**.
4. **Test the Connection** to ensure it's configured correctly, then click **Apply** and **OK**.

## Step 2: Creating a Database
1. In DataGrip, right-click the **server** connection and select **New | Database**.
2. In the dialog box, **name your database** (e.g., `test_db`), and select **OK** to create it.

## Step 3: Creating a Table
1. Expand your new database under the **Database Explorer**.
2. Right-click on the **Tables** section and select **New | Table**.
3. **Define Table Name**:
   - In the editor, name your table (e.g., `employees`).
4. **Add Columns**:
   - Right-click in the `Columns` area or select **Add New Column** to define each field.
   - Define each column's **name**, **data type** (e.g., `VARCHAR`, `INTEGER`), and **constraints** (e.g., `NOT NULL` or `PRIMARY KEY`).
   - Example columns for `employees`:
     - `id` (INTEGER, PRIMARY KEY)
     - `first_name` (VARCHAR(50), NOT NULL)
     - `last_name` (VARCHAR(50), NOT NULL)
     - `position` (VARCHAR(50), NOT NULL)

5. **Apply** changes to create the table in the database.

## Step 4: Adding Records
1. Right-click on the table (`employees`) and select **Jump to Data**.
2. In the Data tab, click **Add Row**.
3. **Input Data**:
   - Enter values in each field according to the table schema you defined.
   - For example:
     - `id`: 1
     - `first_name`: "Alice"
     - `last_name`: "Johnson"
     - `position`: "Software Engineer"
4. Press **Enter** to save each row.

## Step 5: Saving Changes
If your records don't save automatically, ensure you're in the **Commit** tab and select **Apply** or **Commit** to finalize the entries.

This tutorial provides a basic PostgreSQL database setup and a functional table with records using DataGrip.
