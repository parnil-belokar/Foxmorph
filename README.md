# FoxMorph

FoxMorph is a desktop application designed to automate the migration of legacy **Visual FoxPro databases** to **MySQL**.

The tool extracts schema and data from FoxPro database files and generates corresponding SQL queries, enabling seamless migration to modern relational database systems.

FoxMorph simplifies the process of modernizing legacy database systems by automatically handling schema extraction, datatype mapping, and SQL generation.

---

## Motivation

Visual FoxPro databases use proprietary file formats such as:

- **.DBC** – database container (stores metadata about tables and relationships)
- **.DBF** – table files containing records
- **.CDX** – index files used to speed up queries
- **.FPT** – memo files storing large text or binary data

These legacy formats are difficult to maintain in modern environments. FoxMorph helps migrate this data into **MySQL**, ensuring better scalability, maintainability, and integration with modern software systems.

---

## Features

- Automated migration from **Visual FoxPro to MySQL**
- Reads **DBC and DBF database structures**
- Converts **FoxPro datatypes to MySQL datatypes**
- Generates SQL scripts including:
  - `CREATE DATABASE`
  - `CREATE TABLE`
  - `INSERT INTO`
- Preserves **primary keys, foreign keys, and indexes**
- Built-in **data cleaning and sanitization**
- Simple **GUI-based migration interface**

---

## Tech Stack

- **Java**
- **JavaDBF**
- **JDBC**
- **Java Swing**
- **MySQL**

---

## How It Works

1. Select the directory containing the FoxPro database files.
2. FoxMorph reads `.DBC` and `.DBF` files.
3. Schema information is extracted and mapped to MySQL equivalents.
4. SQL queries are generated automatically.
5. The resulting SQL script can be executed in MySQL to recreate the database.

---
## Project Structure

FoxMorph/
│
├── src/
│   ├── foxql/
│   │   ├── FoxMorph.java        # Main GUI application
│   │   ├── Converter.java       # Core migration logic
│   │
│   └── com/foxdbf/
│       ├── foxdbf.java          # DBF file reader
│       ├── field.java           # Field metadata representation
│       ├── idx.java             # Index handling
│       ├── cdx.java             # CDX index parsing
│       ├── datestr.java         # Date parsing utilities
│       └── base.java            # Core DBF parsing functionality
│
└── README.md

## Future Improvements

- Support for stored procedure migration
- Trigger migration
- PostgreSQL support
- Handling larger datasets
- Cloud database integration

---

## Author

**Parnil**  
Computer Science Undergraduate
