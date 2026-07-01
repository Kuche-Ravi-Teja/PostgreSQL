# <u> -------------------- PostgreSQL Database -------------------- <u/>

  - A PostgreSQL database is a secure, digital container used to store and organize an application's data. 
  - It keeps all your tables, lists, and records completely isolated from other databases on the same server.
    
## <u> Connect to the Database <u/>

To create a new database table using the SQL Shell, make sure you are connected to the database. Once you are connected, you are ready to write SQL statements!

## Steps to install, setup, and connect to the database (windows) <u/>

  - Step 1 : Download the Installer

        Go to the official PostgreSQL Downloads Page.
        Click the link for the EDB Windows Installer.
        Download the latest stable version for Windows x86-64.

  - Step 2 : Install PostgreSQL
  
        Run the downloaded .exe file.
        The setup wizard will walk you through the process:
          Components to Select : Keep the default options checked.
          This includes : PostgreSQL Server (the actual database)
                          pgAdmin4 (the visual interface you will use)
                          Command Line Tools (for using psql if needed)
                          Stack Builder (Optional, you can uncheck this to save time)
                          Data Directory: Leave it at the default path and click Next.
                          Password: Choose a master password for the database superuser (postgres).
          ⚠️ Crucial: Write this password down! You will need it every time you connect.
                          Port: Leave it as the default 5432 unless you know another app is using it.
                          Locale: Leave it as [Default locale] and finish the installation.

  - Step 3 : Connect Using pgAdmin (The Visual Way) Once the installation is complete, pgAdmin is your easiest gateway to managing your data.
  
           Open the Windows Start menu, search for pgAdmin 4, and open it. (It opens in a neat browser window or a standalone desktop app dashboard).
           In the left sidebar, click on Servers to expand the list.
           Click on PostgreSQL [Your Version].
           A prompt will pop up asking for a password.
           Type the password you created in Step 2.
           Optional: Check the "Save Password" box so you don't have to type it every time.You are now connected! You can expand the Databases tab to see the default postgres database, or right-click Databases ➔ Create ➔ Database to create your own.
  
  -   Step 4 : Connect via Command Line (Alternative Way) if you prefer using the Command Prompt or terminal:
  
           Search for SQL Shell (psql) in your Windows Start menu and open it.
           It will prompt you with a few defaults.
           Just hit Enter to accept them for : Server [localhost]
                                               Database [postgres]
                                               Port [5432]
                                               Username [postgres]
           When it asks for Password for user postgres, type your master password. (Note: The cursor won't move or show dots while typing the password for security—just type it out and hit Enter).
           If successful, your prompt will change to postgres=#, meaning you are directly inside the database shell. You can type \q and hit Enter to exit at any time.

## <u> Learning Database <u/>

### 01. Create Table

  - The following SQL statement will create a table named cars in your PostgreSQL database :

        CREATE TABLE cars (
          brand VARCHAR(255),
          model VARCHAR(255),
          year INT
        );

  - When you execute the above statement, an empty table named cars will be created, and the SQL Shell application will return the following :

        CREATE TABLE

#### SQL Statement Explained

  - The above SQL statement created an empty table with three fields: brand, model, and year.

  - When creating fields in a table we have to specify the data type of each field.

  - For brand and model we are expecting string values, and string values are specified with the VARCHAR keyword.

  - We also have to specify the number of characters allowed in a string field, and since we do not know exactly, we just set it to 255.

  - For year we are expecting integer values (numbers without decimals), and integer values are specified with the INT keyword.

### 02. Display Table

  - You can "display" the empty table you just created with another SQL statement :

        SELECT * FROM cars;
    
  - Which will give you this result:

         brand | model | year
        -------+-------+------
        (0 rows)

### 03. Insert Into

  - To insert data into a table in PostgreSQL, we use the INSERT INTO statement.

  - The following SQL statement will insert one row of data into the cars table you created in the previous chapter.

        INSERT INTO cars (brand, model, year)
        VALUES ('Ford', 'Mustang', 1964);
    
  - The SQL Shell application will return the following:

        INSERT 0 1
    
  - Which means that 1 row was inserted. Don't think about the 0, for now, just accept that it represents something else and will always be 0.

#### SQL Statement Explained

  - As you can see in the SQL statement above, string values must be written with apostrophes.

  - Numeric values can be written without apostrophes, but you can include them if you want.

#### Insert Multiple Rows

  - To insert multiple rows of data, we use the same INSERT INTO statement, but with multiple values :

        INSERT INTO cars (brand, model, year)
        VALUES
          ('Volvo', 'p1800', 1968),
          ('BMW', 'M1', 1978),
          ('Toyota', 'Celica', 1975);
    
  - The SQL Shell application will return the following:

        INSERT 0 3

  - Which means 3 rows were successfully inserted.

## 04. Select Data (Fetch data)

  - To retrieve data from a data base, we use the SELECT statement.

#### Specify Columns

  - By specifying the column names, we can choose which columns to select:

        SELECT brand, year FROM cars;

#### Return ALL Columns

  - Specify a * instead of the column names to select all columns:

        SELECT * FROM cars;

### 05. The ALTER TABLE Statement

  - To add a column to an existing table, we have to use the ALTER TABLE statement.

  - The ALTER TABLE statement is used to add, delete, or modify columns in an existing table.

  - The ALTER TABLE statement is also used to add and drop various constraints on an existing table.

#### ADD COLUMN

  - We want to add a column named color to our cars table.

  - When adding columns we must also specify the data type of the column. Our color column will be a string, and we specify string types with the VARCHAR keyword. we also want to restrict the number of characters to 255:

  - Add a column named color :

        ALTER TABLE cars
        ADD color VARCHAR(255);

  - Result

        ALTER TABLE

#### ALTER COLUMN

  - We want to change the data type of the year column of the cars table from INT to VARCHAR(4).

  - To modify a column, use the ALTER COLUMN statement and the TYPE keyword followed by the new data type:

  - Change the year column from INT to VARCHAR(4):

        ALTER TABLE cars
        ALTER COLUMN year TYPE VARCHAR(4);
    
  - Result

        ALTER TABLE
    
  - Note : Some data types cannot be converted if the column has value. E.g. numbers can always be converted to text, but text cannot always be converted to numbers.

#### Change Maximum Allowed Characters

  - We also want to change the maximum number of characters allowed in the color column of the cars table.

  - Use the same syntax as above, use the ALTER COLUMN statement and the TYPE keyword followed by the new data type:

  - Change the color column from VARCHAR(255) to VARCHAR(30):

        ALTER TABLE cars
        ALTER COLUMN color TYPE VARCHAR(30);

  - Result

        ALTER TABLE

#### DROP COLUMN

  - We want to remove the column named color from the cars table.

  - To remove a column, use the DROP COLUMN statement:

  - Remove the color column:

        ALTER TABLE cars
        DROP COLUMN color;

  - Result

        ALTER TABLE

### 06. The UPDATE Statement

  - The UPDATE statement is used to modify the value(s) in existing records in a table.

  - Set the color of the Volvo to 'red':

        UPDATE cars
        SET color = 'red'
        WHERE brand = 'Volvo';

  - Result
    
        UPDATE 1
    
  - Which means that 1 row was affected by the UPDATE statement.

  - Note : Be careful with the WHERE clause, in the example above ALL rows where brand = 'Volvo' gets updated.

#### Update Multiple Columns

  - To update more than one column, separate the name/value pairs with a comma ,:

  - Update color and year for the Toyota:

        UPDATE cars
        SET color = 'white', year = 1970
        WHERE brand = 'Toyota';

  - Result

        UPDATE 1
    
  - Which means that 1 row was affected by the UPDATE statement.

### 07. The DELETE Statement

  - The DELETE statement is used to delete existing records in a table.

  - Note : Be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement. The WHERE clause specifies which record(s) should be deleted.

  - If you omit the WHERE clause, all records in the table will be deleted!.

  - To delete the record(s) where brand is 'Volvo', use this statement:

  - Delete all records where brand is 'Volvo':

        DELETE FROM cars
        WHERE brand = 'Volvo';

  - Result

        DELETE 1

  - Which means that 1 row was deleted.

#### Delete All Records

  - It is possible to delete all rows in a table without deleting the table. This means that the table structure, attributes, and indexes will be intact.

  - The following SQL statement deletes all rows in the cars table, without deleting the table:

  - Delete all records in the cars table:

        DELETE FROM cars;

  - Result
    
        DELETE 3
    
  - Which means that all 3 rows were deleted.

#### TRUNCATE TABLE

  - Because we omit the WHERE clause in the DELETE statement above, all records will be deleted from the cars table.

  - The same would have been achieved by using the TRUNCATE TABLE statement:

  - Delete all records in the cars table:

        TRUNCATE TABLE cars;

  - Result

        TRUNCATE TABLE

### 08. The DROP TABLE Statement

  - The DROP TABLE statement is used to drop an existing table in a database.

  - Note : Be careful before dropping a table. Deleting a table will result in loss of all information stored in the table!

  - The following SQL statement drops the existing table cars:

  - Delete the cars table:

        DROP TABLE cars;

  - Result

        DROP TABLE

    
