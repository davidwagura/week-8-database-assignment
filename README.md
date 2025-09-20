
# E-commerce Database Schema

## Overview
This project provides a **relational database schema** for an e-commerce platform using **MySQL**.  
The schema supports user management, product catalog, orders, payments, reviews, inventory tracking, and more.

## Features
- **Users & Roles**: Customers, Admins, and Sellers.
- **Addresses**: Multiple addresses per user (shipping, billing).
- **Products & Categories**: Products can belong to multiple categories (many-to-many).
- **Suppliers**: Vendor/supplier management.
- **Inventory**: Stock tracking per product.
- **Orders & Order Items**: Order processing with discounts and shipping details.
- **Payments**: Linked to orders with status tracking.
- **Coupons/Discounts**: Supports fixed and percentage discounts.
- **Reviews**: Verified purchase product reviews.
- **Cart & Wishlist**: Shopping cart and wishlist per user.
- **Audit Logs**: Tracks important changes (insert/update/delete).

## Schema Highlights
- **Primary Keys**: Auto-increment IDs for all main tables.
- **Foreign Keys**: Enforced referential integrity with cascading rules.
- **Constraints**: 
  - `NOT NULL` for required fields  
  - `UNIQUE` for emails, SKU, coupon codes  
  - `CHECK` constraint for review ratings (1–5)  
- **Relationships**:
  - One-to-Many: `users -> addresses`, `orders -> order_items`
  - Many-to-Many: `products <-> categories`, `users <-> products (wishlists)`
  - One-to-One/Many: `orders -> payments`

## Installation
1. Open MySQL client or phpMyAdmin.
2. Run the SQL script:

   ```bash
   mysql -u your_user -p < ecommerce_schema.sql
   ```

3. The database `ecommerce_db` will be created.

## Usage
- Use the provided tables to manage an e-commerce application backend.
- Query example: List all orders with user details:

   ```sql
   SELECT o.id, o.order_number, u.email, o.status, o.total_amount
   FROM orders o
   JOIN users u ON u.id = o.user_id;
   ```

- Stored procedure example: Get product stock availability

   ```sql
   CALL sp_get_product_stock(1);
   ```

## Files
- `ecommerce_schema.sql` → Complete schema with tables, relationships, views, and procedures.
- `README.md` → Documentation of schema structure and usage.

## Author
Database schema generated for academic and practical use.  
Can be extended for production with indexes, triggers, and data seeding.
