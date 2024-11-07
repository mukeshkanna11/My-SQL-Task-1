//Ecommerce Task SQL Project//

This project demonstrates a basic eCommerce database setup using SQL. The database includes tables for customers, orders, products, and order items, with sample data and various queries.

//Project Overview//

The database, named ecommercetask, is designed to store information about customers, their orders, the products they purchase, and the details of each order item.


//Project Overview//

The database, named ecommercetask, is designed to store information about customers, their orders, the products they purchase, and the details of each order item.

//Database Structure//

Customers Table//

Stores customer details such as name, email, and address.

Orders Table//

Stores order information, including the customer ID, order date, and total amount.

Products Table//

Contains information about each product, including name, price, and description.

Order Items Table//

(Used to normalize the database) Stores each order’s products, including order ID, product ID, and quantity.

CREATE DATABASE ecommercetask;
USE ecommercetask;

-- Create Customers Table --
CREATE TABLE customers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    address VARCHAR(255)
);

-- Create Orders Table --

CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10, 2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- Create Products Table --

CREATE TABLE products (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2),
    description TEXT
);

-- Create Order Items Table --

CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT DEFAULT 1,
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
