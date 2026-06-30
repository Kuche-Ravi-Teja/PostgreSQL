# <u> -------------------- PostgreSQL -------------------- <u/>

## <u> What is PostgreSQL? <u/>

PostgreSQL is a free open-source database system that supports both relational (SQL) and non-relational (JSON) queries.

PostgreSQL is a back-end database for dynamic websites and web applications.

PostgreSQL supports the most important programming languages:

  - Python
  - Java
  - C/C++
  - C#
  - Node.js
  - Go
  - Ruby
  - Perl
  - Tcl

#### Note : PostgreSQL supports basically all features that other database management systems support.

## <u> PostgreSQL History <u/>

PostgreSQL was invented at the Berkeley Computer Science Department, University of California.

It started as a project in 1986 with the goal of creating a database system with the minimal features needed to support multiple data types.

In the beginning, PostgreSQL ran on UNIX platforms, but now it can run on various platforms, including Windows and MacOS.

## <u> Why Choose PostgreSQL over Other SQL Databases <u/>

  - Open Source and Free : PostgreSQL is completely free to use and has a strong developer community.
  - Advanced SQL Support : Supports complex queries, joins, subqueries, views, stored procedures and triggers.
  - ACID Compliance : Ensures reliable and secure transactions with data integrity.
  - JSON Support : Can store and query JSON data efficiently, making it suitable for modern applications.
  - Extensible : Users can create custom functions, data types and extensions.
  - High Performance : Optimized for handling large datasets and complex workloads.
  - Multi-Language Support : Works with popular programming languages such as Python, Java, C/C++, C#, Node.js, Go, Ruby, Perl and Tcl.

## <u> Applications <u/>

  - Enterprise Applications : Used in large business systems requiring reliability and data integrity.
  - Data Analytics and Warehousing : Stores and processes large volumes of data for analysis.
  - Financial Systems : Supports banking and financial applications with strong transaction management.
  - Geographic Information Systems (GIS) : Handles spatial and location-based data using PostGIS.
  - Web Applications : Powers dynamic websites and web services.

## <u> Datatypes of PostgreSQL <u/>

PostgreSQL has one of the richest sets of native data types available in the database world. 

Here is a breakdown of the most common data types you'll actually use, explained simply.

### 1. Text Data Types (For Words and Strings)

  - VARCHAR(n) : Variable-length character string with a limit of n characters. Perfect when you have an upper limit but lengths vary.

  - TEXT : Unlimited length string. Use this when you don't want to arbitrary cap how much someone can type (like blog posts or comments). In PostgreSQL, TEXT is   just as fast as VARCHAR.

  - Example :

        username VARCHAR(50),  -- e.g., 'johndoe123'
        bio TEXT               -- e.g., 'A long paragraph about my life...'

    
### 2. Numeric Data Types (For Numbers)

  - INT or INTEGER : For whole numbers (no decimals). Ranges from -2 billion to +2 billion.

  - BIGINT : For massive whole numbers (like global IDs or system timestamps).

  - NUMERIC(precision, scale) : For exact math, like money. You tell it the total number of digits (precision) and how many go after the decimal (scale).

  - REAL / DOUBLE PRECISION : For floating-point numbers (decimals where minor rounding errors are fine, like scientific data or GPS coordinates).

  - Example :

        age INT,                      -- e.g., 29
        account_balance NUMERIC(10,2) -- e.g., 1250.50 (Max 10 digits total, 2 after decimal)

    
### 3. Date and Time Data Types

  - DATE : Just the calendar date (no time).

  - TIMESTAMP : Date and time combined.

  - TIMESTAMPTZ : Date, time, and time zone.

Pro tip: Always use this for global apps so your servers don't get confused about when something happened.

  - Example :

        birth_date DATE,           -- e.g., '1995-05-15'
        created_at TIMESTAMPTZ     -- e.g., '2026-06-30 10:00:00+00'

    
### 4. Boolean Data Type (True/False)

  - BOOLEAN : Holds exactly three states: TRUE, FALSE, or NULL (unknown).

  - Example :

        is_active BOOLEAN          -- e.g., TRUE

    
### 5. Advanced Data Types

PostgreSQL stands out because it easily handles complex data without needing a separate NoSQL database.

  - JSONB : Stores JSON data in a decomposed, binary format. It allows you to index and query inside raw JSON data fast.

  - UUID : Universally Unique Identifier. Great for IDs instead of sequential numbers (1, 2, 3...) so hackers can't guess your data size.

  - ARRAY : Allows a column to hold a list of values.

  - Example :

        user_id UUID,              -- e.g., 'a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11'
        preferences JSONB,         -- e.g., '{"theme": "dark", "notifications": true}'
        tags TEXT[]                -- e.g., '{"coding", "databases", "sql"}'
