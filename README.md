# Task S2.03 - MongoDB data structure

## 📌 Level 1

This repository contains two projects focused on **NoSQL database modeling** and **system design** using **MongoDB**, **Docker**, and **Moon Modeler**:

1. **“Cul d’Ampolla” Optics** – Management of clients and eyeglasses sales.  
2. **Online Food Delivery Web** – Management of clients, orders, products, and stores.

Both projects are designed to practice **document-based database design**, entity relationships, and business logic in real-world management systems.

### Exercise 1 y 2 - “Cul d’Ampolla” Optics

### Objective
Digitize the management of clients, suppliers, and eyeglass sales, including detailed information about products, clients, and employees using **MongoDB collections**.

### Collections and Fields

**Suppliers**
- `name`
- `address`: street, number, floor, door, city, postal code, country
- `phone`
- `fax`
- `taxId` (NIF)

**Eyeglasses**
- `brand`
- `lensPrescription`: left and right
- `frameType`: floating, plastic, or metal
- `frameColor`
- `lensColor`: left and right
- `price`
- `supplierId` (reference)

**Clients**
- `name`
- `postalAddress`
- `phone`
- `email`
- `registrationDate`
- `referredByClientId` (optional)

**Employees**
- `name`
- `employeeId`
- `sales` (array of sale references)

**Sales**
- `eyeglassesId` (reference)
- `clientId` (reference)
- `employeeId` (reference)
- `saleDateTime`

### Design Notes
- A supplier can provide multiple eyeglasses (one-to-many relationship).  
- A client can make multiple purchases; each purchase is linked to an employee and a timestamp.  
- A client may have been referred by another client.  

## 📌 Level 2

### Exercise 1 - Online Food Delivery

### Objective
Model a home delivery platform that manages orders, products (pizzas, hamburgers, drinks) and store staff.

### Design Principles

* Embedded Pattern: To avoid relational behavior (Joins) and improve performance, customer and product data (including price and category at the time of purchase) are stored directly within the Order document.

* Historical Accuracy: By embedding the pizza category and price, the order remains unchanged even if category names change seasonally or prices increase.

* Dynamic Delivery Info: The delivery information object only exists in "delivery" orders, optimizing space usage.

### Collections Summary

* Orders: Central document containing the customer (embedded), the product list (embedded with historical pricing), and delivery info (conditional).

* Products: Pizzas (with categories), hamburgers, and drinks.

* Stores & Employees: Store and staff management (cooks/delivery drivers). 

## 🛠️ Technologies
- **Database:** MongoDB (NoSQL, document-oriented)  
- **Containerization:** Docker  
- **Modeling tool:** Moon Modeler (ER diagrams and JSON schema design)  

## 🚀 Installation and Execution
1. Clone the repository:
`git clone https://github.com/Karel-Patricia/Task.S2.03.-MongoDB_data_structure.git`   
cd Task.S2.03.-MongoDB_data_structure

2. Start the environment (Docker):
docker run -d -p 27017:27017 --name mongodb mongo

3. Import data:
docker cp Level2/Exercise1/orders.js mongodb:/tmp/orders.js
docker exec -it mongodb mongosh "delivery_db" /tmp/orders.js
