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
Design a **NoSQL database in MongoDB** to manage clients, products, orders, and stores for an online food delivery platform.

### Collections and Fields

**Clients**
- `_id` (unique identifier)
- `firstName`, `lastName`
- `address`
- `postalCode`, `city`, `province`
- `phoneNumber`

**Orders**
- `_id` (unique identifier)
- `dateTime`
- `orderType`: delivery or pickup
- `products`: array with quantity and product references
- `totalPrice`
- `note` (optional)
- `clientId` (reference)
- `deliveryEmployeeId` (optional reference)
- `deliveryDateTime` (optional)

**Products**
- `_id` (unique identifier)
- `name`
- `description`
- `imageURL`
- `price`
- `category` (for pizzas, may change seasonally)

**Stores**
- `_id` (unique identifier)
- `address`
- `postalCode`, `city`, `province`
- `employees` (array of employee references)

**Employees**
- `_id` (unique identifier)
- `name`, `lastName`
- `taxId` (NIF)
- `phone`
- `role`: cook or delivery person
- `storeId` (reference)

### Design Notes
- A client can place multiple orders, each order belongs to a single client.  
- Each order can include multiple products.  
- A store can manage many orders and have multiple employees.  
- Each delivery order is assigned to a single delivery person.  

## 🛠️ Technologies
- **Database:** MongoDB (NoSQL, document-oriented)  
- **Containerization:** Docker  
- **Modeling tool:** Moon Modeler (ER diagrams and JSON schema design)  

## 🚀 Instalación y Ejecución
1. Clonar el repositorio: `git clone https://github.com/Karel-Patricia/Task.S2.03.-MongoDB_data_structure.git`   
cd Task.S2.03.-MongoDB_data_structure
