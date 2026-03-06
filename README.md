# SQL Query Generator – Natural Language to SQL

##  Project Overview

SQL Query Generator is an intelligent system that converts **natural language questions into SQLite SQL queries**.
Users can simply type queries in plain English, and the system automatically generates safe and optimized SQL statements.

The project is designed to make database querying **easy for non-technical users** who do not know SQL.

---

##  Features

* Natural Language → SQL conversion
* Automatic **table detection**
* Intelligent **column detection**
* **Condition extraction** (date filters, amount filters)
* SQL injection **security validation**
* **Query history** tracking
* **Gradio chat interface**
* Public deployment using **Google Colab**
* SQL query preview for users

---

##  Technologies Used

| Technology   | Purpose                         |
| ------------ | ------------------------------- |
| Python       | Core programming language       |
| Gradio       | Interactive web interface       |
| SQLite       | SQL query format                |
| Transformers | NLP support (optional AI model) |
| ReportLab    | PDF report generation           |
| Regex        | Condition detection             |

---

##  Database Schema

### Users Table

| Column      | Type    |
| ----------- | ------- |
| id          | INTEGER |
| name        | TEXT    |
| email       | TEXT    |
| signup_date | DATE    |
| age         | INTEGER |
| country     | TEXT    |
| status      | TEXT    |

### Orders Table

| Column       | Type    |
| ------------ | ------- |
| id           | INTEGER |
| user_id      | INTEGER |
| product_name | TEXT    |
| amount       | REAL    |
| order_date   | DATE    |
| status       | TEXT    |

### Products Table

| Column   | Type    |
| -------- | ------- |
| id       | INTEGER |
| name     | TEXT    |
| price    | REAL    |
| category | TEXT    |
| stock    | INTEGER |

### Transactions Table

| Column  | Type    |
| ------- | ------- |
| id      | INTEGER |
| user_id | INTEGER |
| amount  | REAL    |
| date    | DATE    |
| type    | TEXT    |

---

##  Installation

Install required libraries:

```
pip install gradio reportlab transformers torch
```

---

##  Running the Project

Run the notebook in **Google Colab**.

Steps:

1. Open Google Colab
2. Upload `sql_query_generator.ipynb`
3. Run all cells
4. A **Gradio public link** will be generated

---

## 💬 Example Queries

### Example 1

Input

```
Show users who signed up last month
```

Output

```sql
SELECT * FROM users
WHERE DATE(signup_date) >= DATE('now','-1 month')
LIMIT 10
```

---

### Example 2

Input

```
Find transactions greater than 500 from last week
```

Output

```sql
SELECT * FROM transactions
WHERE amount > 500
AND DATE(date) >= DATE('now','-7 days')
LIMIT 10
```

---

### Example 3

Input

```
Show users and their orders
```

Output

```sql
SELECT users.name, orders.product_name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id
LIMIT 10
```

---

##  Project Workflow

1. User enters natural language query
2. System checks for **security risks**
3. Detects **table name**
4. Detects **columns**
5. Extracts conditions
6. Generates SQL query
7. Displays results in chat interface

---

##  Security

The system blocks dangerous SQL commands including:

* DROP
* DELETE
* ALTER
* INSERT
* UPDATE

It also prevents common **SQL injection patterns**.

---

##  Project Structure

```
SQL-Query-Generator
│
├── sql_query_generator.ipynb
├── README.md
├── requirements.txt
└── exports
```

---

##  Future Improvements

* Support for MySQL and PostgreSQL
* Query visualization dashboards
* AI-powered SQL optimization
* Automatic database schema detection

---

##  Author

Developed as part of an **AI/NLP database project** for natural language database interaction.

---

##  License

This project is for **educational and research purposes**.
