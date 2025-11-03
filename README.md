# Inventory Tracking System

Compact README for the Inventory Tracking System SQL project.

## Project summary
Relational inventory database (MySQL) for tracking products, suppliers, warehouses, stock levels and inventory transactions (IN, OUT, TRANSFER, ADJUST). Designed with proper PK/FK constraints and InnoDB transactional safety.

## Files
- c:\Users\Kioko\Untitled-1.sql — main SQL script: CREATE DATABASE, CREATE TABLE, relationship constraints.
- c:\workspace\answers.sql — (optional) additional examples / queries used earlier.

## Schema (tables)
- users (employees)
- suppliers
- categories
- warehouses
- products (FK → categories, suppliers)
- stock_levels (product × warehouse, composite PK)
- transactions (inventory movements)
- transaction_items (transaction × product)

## Prerequisites
- MySQL Server 5.7 or 8.0 (InnoDB)
- MySQL client (mysql CLI) or MySQL Workbench / phpMyAdmin
- Windows machine (commands below use Windows paths)

## Install / Execute
From Command Prompt or PowerShell:
1. Run script directly:
   mysql -u root -p < "C:\Users\Kioko\Untitled-1.sql"
2. Or connect then SOURCE:
   mysql -u root -p
   mysql> SOURCE C:/Users/Kioko/Untitled-1.sql;

Use a user with CREATE/ALTER privileges.

## Quick verification
After running:
mysql -u root -p -e "USE inventory_system; SHOW TABLES;"
mysql -u root -p -e "USE inventory_system; SHOW CREATE TABLE products\G"

Example query to view total stock per product:
SELECT p.product_id, p.sku, p.name, COALESCE(SUM(s.quantity),0) AS total_quantity
FROM products p
LEFT JOIN stock_levels s ON s.product_id = p.product_id
GROUP BY p.product_id, p.sku, p.name
ORDER BY total_quantity ASC;

## Notes & recommendations
- Wrap inventory changes (INSERT into transactions + transaction_items and UPDATE stock_levels) inside a DB transaction to maintain consistency.
- Add indexes for high-read columns (e.g., products.sku).
- Consider stored procedures for common operations (receive, ship, transfer) to encapsulate logic and locking.

## Contact
Project author: (student) — include your name/email here before submission.

```// filepath: c:\Users\Kioko\README.md

# Inventory Tracking System

Compact README for the Inventory Tracking System SQL project.

## Project summary
Relational inventory database (MySQL) for tracking products, suppliers, warehouses, stock levels and inventory transactions (IN, OUT, TRANSFER, ADJUST). Designed with proper PK/FK constraints and InnoDB transactional safety.

## Files
- c:\Users\Kioko\Untitled-1.sql — main SQL script: CREATE DATABASE, CREATE TABLE, relationship constraints.
- c:\workspace\answers.sql — (optional) additional examples / queries used earlier.

## Schema (tables)
- users (employees)
- suppliers
- categories
- warehouses
- products (FK → categories, suppliers)
- stock_levels (product × warehouse, composite PK)
- transactions (inventory movements)
- transaction_items (transaction × product)

## Prerequisites
- MySQL Server 5.7 or 8.0 (InnoDB)
- MySQL client (mysql CLI) or MySQL Workbench / phpMyAdmin
- Windows machine (commands below use Windows paths)

## Install / Execute
From Command Prompt or PowerShell:
1. Run script directly:
   mysql -u root -p < "C:\Users\Kioko\Untitled-1.sql"
2. Or connect then SOURCE:
   mysql -u root -p
   mysql> SOURCE C:/Users/Kioko/Untitled-1.sql;

Use a user with CREATE/ALTER privileges.

## Quick verification
After running:
mysql -u root -p -e "USE inventory_system; SHOW TABLES;"
mysql -u root -p -e "USE inventory_system; SHOW CREATE TABLE products\G"

Example query to view total stock per product:
SELECT p.product_id, p.sku, p.name, COALESCE(SUM(s.quantity),0) AS total_quantity
FROM products p
LEFT JOIN stock_levels s ON s.product_id = p.product_id
GROUP BY p.product_id, p.sku, p.name
ORDER BY total_quantity ASC;

## Notes & recommendations
- Wrap inventory changes (INSERT into transactions + transaction_items and UPDATE stock_levels) inside a DB transaction to maintain consistency.
- Add indexes for high-read columns (e.g., products.sku).
- Consider stored procedures for common operations (receive, ship, transfer) to encapsulate logic and locking.

## Contact
Project author: (student) — KIOKO
