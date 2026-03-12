# FoxMorph

FoxMorph is a desktop application designed to automate the migration of legacy **Visual FoxPro databases** to **MySQL**.

Many legacy systems still rely on FoxPro database files (`.DBF`, `.DBC`, `.CDX`, `.FPT`).  
FoxMorph reads these files, extracts the schema and records, and generates equivalent **MySQL SQL scripts** that recreate the database structure and data in a modern relational database.

The goal of FoxMorph is to simplify the modernization of legacy data systems while preserving **schema structure and data integrity**.

---

# Motivation

Visual FoxPro was once widely used for database-driven applications. However, the platform has been discontinued and many organizations still maintain critical data in FoxPro databases.

Challenges with FoxPro systems include:

- Limited compatibility with modern operating systems
- File-based database structure
- Difficult integration with modern technology stacks
- Limited scalability

FoxMorph helps address these issues by enabling a **structured and automated migration process** from FoxPro to MySQL.

---

# Features

## Automated Schema Migration

FoxMorph extracts schema information from FoxPro databases and generates equivalent **MySQL table definitions**.

## Data Extraction

Reads records directly from FoxPro `.DBF` tables and converts them into SQL **INSERT queries**.

## Data Type Mapping

Automatically maps FoxPro data types to MySQL equivalents.

| FoxPro Type | MySQL Type |
|-------------|-----------|
| Integer | INT |
| Character | VARCHAR |
| Float | DECIMAL |
| Date | DATE |
| Memo / Text | TEXT |
| Double | DOUBLE |

## Key Preservation

Maintains important database constraints including:

- Primary keys
- Foreign keys
- Indexes

## Data Cleaning and Sanitization

Handles common issues in legacy systems such as:

- Null values
- Invalid characters
- Control characters
- Missing metadata

## GUI-Based Workflow

FoxMorph includes a desktop interface built using **Java Swing**, allowing users to select FoxPro database directories and generate migration scripts easily.

---

# Technology Stack

| Component | Technology |
|----------|-----------|
| Programming Language | Java |
| GUI Framework | Java Swing |
| FoxPro File Parsing | JavaDBF Library |
| Database Connectivity | JDBC |
| Target Database | MySQL |

---

# Architecture Overview

FoxMorph follows a **data migration pipeline architecture**.

```
Visual FoxPro Database Files
│
├── DBC (Database Container - metadata)
├── DBF (Table data)
├── CDX (Index files)
└── FPT (Memo data)
│
▼
Schema Extraction
│
▼
Data Cleaning & Validation
│
▼
Schema Mapping
(FoxPro → MySQL conversion)
│
▼
SQL Query Generation
(DDL + DML scripts)
│
▼
MySQL Database
```

---

# Installation

## Prerequisites

Make sure the following tools are installed:

- Java JDK (8 or higher)
- MySQL Server
- Git
- Java IDE (IntelliJ IDEA / Eclipse / VS Code)

---

# Clone the Repository

```bash
git clone https://github.com/yourusername/FoxMorph.git
cd FoxMorph
```

---

# Running the Application

## Step 1 — Compile the Project

Using your preferred IDE:

- Open the project
- Build the project

Or compile using Java:

```bash
javac *.java
```

---

## Step 2 — Launch the Application

Run the main application:

```bash
java FoxMorph
```

The FoxMorph GUI will open.

---

# Using FoxMorph

1. Open the FoxMorph application  
2. Select the directory containing FoxPro database files (`.DBC`, `.DBF`)  
3. Choose an output directory for generated SQL scripts  
4. Click **Convert**

FoxMorph will generate SQL scripts containing:

- `CREATE TABLE` statements
- `INSERT INTO` queries

---

# Example Workflow

```
FoxPro Database
│
├── customers.dbf
├── orders.dbf
├── database.dbc
└── indexes.cdx
│
▼
FoxMorph Processing
│
▼
Generated SQL Script
│
▼
MySQL Database
```

---

# Project Structure

```
FoxMorph
│
├── src
│   ├── foxql
│   │   ├── FoxMorph.java
│   │   └── Converter.java
│   │
│   └── com/foxdbf
│       ├── foxdbf.java
│       ├── field.java
│       ├── idx.java
│       ├── cdx.java
│       ├── datestr.java
│       └── base.java
│
├── README.md
└── .gitignore
```

---

# Example Output

FoxMorph generates SQL scripts such as:

```sql
CREATE TABLE Customers (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    created_date DATE
);

INSERT INTO Customers VALUES (1, 'John Doe', '2023-01-01');
```

These scripts can be directly executed in **MySQL**.

---

# Future Improvements

Planned enhancements include:

- Stored procedure migration
- Trigger migration
- Support for additional databases (PostgreSQL, SQL Server)
- Optimization for large datasets
- Cloud database migration support

---
