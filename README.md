# Chinook SQL + R Data Pipeline

## Project Overview

This project demonstrates an end-to-end **SQL and R data analytics pipeline** using the Chinook sample database, a relational database representing a digital music store.

The analysis uses **raw SQL** to perform JOINs, Common Table Expressions (CTEs), and window functions, and then implements equivalent analyses using **dplyr/dbplyr**. The results are compared and visualised in a reproducible **Quarto report**.

The project demonstrates the ability to work directly with relational databases while also using R for data manipulation, analysis, visualisation, and reporting.

## Objectives

- Query and analyse relational data using SQL.
- Demonstrate practical use of SQL JOINs.
- Use CTEs to structure multi-step queries.
- Apply SQL window functions for ranking and analytical calculations.
- Reproduce SQL analyses using `dplyr`.
- Use `dbplyr` to translate R data manipulation into SQL.
- Compare raw SQL and R-based database workflows.
- Visualise analytical results using R.
- Produce a reproducible Quarto report.

## Dataset

The project uses the **Chinook sample database**, which represents a digital music store.

The database contains related tables covering areas such as:

- Customers
- Invoices
- Invoice Items
- Tracks
- Albums
- Artists
- Genres
- Employees
- Playlists

The relational structure provides a realistic environment for practising multi-table SQL analysis.

## Methodology

### 1. Database Exploration

The database structure is explored to understand the relationships between tables and identify appropriate keys for joining datasets.

The analysis considers relationships such as:

```text
Customer
   ↓
Invoice
   ↓
InvoiceLine
   ↓
Track
   ↓
Album
   ↓
Artist
```

This allows customer purchasing behaviour and product-level performance to be analysed across multiple related tables.

### 2. SQL JOINs

Multiple SQL JOIN types are used to combine information across related tables.

For example, customer information can be joined with invoice data to determine customer spending, while invoice-line data can be connected to tracks and artists to analyse purchasing behaviour.

The project demonstrates the practical use of:

- `INNER JOIN`
- Multi-table JOINs
- Key-based relationships

### 3. Common Table Expressions

**CTEs** are used to divide complex analytical queries into logical stages.

Instead of constructing one large query, intermediate results are created using `WITH` statements and then used by subsequent queries.

This improves query organisation and makes more complex analytical workflows easier to understand and maintain.

### 4. Window Functions

SQL window functions are used for analytical calculations while retaining row-level detail.

Examples include:

- Customer ranking
- Running totals
- Partition-level calculations
- Comparative performance analysis

Functions such as `RANK()`, `ROW_NUMBER()`, and `SUM() OVER()` demonstrate more advanced SQL querying skills.

### 5. dplyr/dbplyr Implementation

The same analytical questions are implemented using **dplyr** and **dbplyr**.

`dplyr` provides a consistent R syntax for data manipulation, while `dbplyr` translates supported dplyr operations into SQL that can be executed against the database.

This creates an opportunity to compare:

**Raw SQL**

```sql
SELECT ...
FROM Customer
JOIN Invoice ...
```

with:

**dplyr/dbplyr**

```r
Customer %>%
  inner_join(Invoice, by = "CustomerId") %>%
  group_by(CustomerId)
```

The comparison demonstrates how database analysis can be performed using both direct SQL and R-based workflows.

## Analytical Workflow

```text
Chinook Database
       ↓
Database Exploration
       ↓
Raw SQL Analysis
 ┌─────┼──────────┐
 JOINs  CTEs  Window Functions
       ↓
dplyr/dbplyr Reimplementation
       ↓
SQL vs R Comparison
       ↓
Data Visualisation
       ↓
Quarto Report
```

## Technologies Used

- **SQL**
- **R**
- `dplyr`
- `dbplyr`
- `DBI`
- `RSQLite`
- `ggplot2`
- **Quarto**

## Analysis Examples

The project can answer business questions such as:

- Which customers generate the most revenue?
- Which artists or genres generate the highest sales?
- How does customer spending rank within the customer base?
- What are the cumulative sales trends?
- Which products contribute most to revenue?
- How do SQL and dplyr/dbplyr produce equivalent analytical results?

## Visualisation

The analysis is presented using R visualisation tools to communicate key findings.

Potential outputs include:

- Customer revenue rankings
- Sales by genre
- Revenue by artist
- Cumulative revenue trends
- Product performance comparisons

## Project Structure

```text
chinook-sql-r-pipeline/
│
├── data/
│   └── chinook.sqlite
│
├── sql/
│   ├── 01_joins.sql
│   ├── 02_ctes.sql
│   └── 03_window_functions.sql
│
├── R/
│   ├── 01_database_connection.R
│   ├── 02_dplyr_analysis.R
│   ├── 03_dbplyr_analysis.R
│   └── 04_visualisation.R
│
├── figures/
│   ├── customer_revenue.png
│   ├── genre_sales.png
│   └── revenue_trends.png
│
├── report/
│   └── chinook_analysis.qmd
│
└── README.md
```

## SQL vs dplyr/dbplyr

A key objective of the project is to demonstrate that the same analytical logic can be expressed through different tools.

| Analysis | Raw SQL | R |
|---|---|---|
| Filtering | `WHERE` | `filter()` |
| Selecting columns | `SELECT` | `select()` |
| Joining tables | `JOIN` | `*_join()` |
| Grouping | `GROUP BY` | `group_by()` |
| Aggregation | `SUM()`, `AVG()` | `summarise()` |
| Ranking | Window functions | `mutate()`/database translation |
| Database execution | SQL engine | `dbplyr` → SQL |

This comparison highlights both **SQL fluency** and the ability to work with databases through R.

## Quarto Report

The final analysis is delivered as a **Quarto report**, combining:

- Analytical narrative
- SQL queries
- R code
- Tables
- Visualisations
- Results
- Business interpretation

The report provides a reproducible record of the complete analytical workflow.

## Key Skills Demonstrated

This project demonstrates practical skills in:

- Relational database analysis
- SQL querying
- JOINs
- Common Table Expressions
- Window functions
- R programming
- `dplyr`
- `dbplyr`
- Database connectivity
- Data transformation
- Data visualisation
- Analytical reasoning
- Reproducible reporting with Quarto

## Business Value

Although Chinook is a sample database, the workflow reflects techniques that can be applied to real-world business data.

The same approach can be used to analyse:

- Customer purchasing behaviour
- Sales performance
- Product performance
- Revenue trends
- Customer segmentation
- Business performance indicators

The project therefore demonstrates not only technical SQL and R skills but also the ability to translate relational data into **actionable business insights**.

## How to Run

1. Install R and the required packages.
2. Install Quarto.
3. Open the project in RStudio.
4. Connect to the Chinook SQLite database.
5. Run the SQL scripts.
6. Run the R analysis scripts.
7. Render the Quarto report.
8. Review the generated tables, visualisations, and findings.

## Conclusion

This project demonstrates an end-to-end SQL and R workflow for analysing relational data. By implementing analytical questions in both raw SQL and dplyr/dbplyr, it demonstrates an understanding of the underlying SQL as well as modern R-based database workflows.

The final Quarto report combines technical analysis with visualisation and business interpretation, making the project suitable as a portfolio example of **intermediate-to-advanced SQL and R data analytics**.
