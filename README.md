# Warehouse Inventory Tracker (Event-based)

## Overview
This Java project simulates a warehouse inventory management system with real-time stock monitoring. The system updates stock when shipments arrive or customer orders are fulfilled and automatically triggers alerts when quantities drop below a predefined threshold.

---

## Features
- Maintain a list of products with unique ID, name, quantity, and reorder threshold.
- Add new products dynamically.
- Update stock on shipment arrival.
- Fulfill customer orders and update inventory.
- Event-driven alerts using the Observer pattern for low stock.
- Multithreaded operations for simultaneous stock updates.
- Console-based interface for easy interaction.

---

## Classes

### **Product**
- Stores product information: ID, name, quantity, reorder threshold.

### **Warehouse**
- Manages inventory operations:
  - `addPro(Product pro)` – Add a new product.
  - `shipmentsArrive(Product pro, int qnty)` – Update stock on shipment.
  - `fullFillOrders(Product pro, int order)` – Process customer orders.
  - `showPro()` – Display all products.
- Synchronized methods for thread-safe operations.
- Supports deep-copy of products for safe access by observers.

### **Observer**
- Monitors product stock in real-time.
- Runs as a **daemon thread** checking inventory every 3 seconds.
- Alerts when stock falls below reorder threshold.
- Implements `Runnable` and `StockAlert` interface.

### **WarehouseOwner**
- Main console-based interface for interacting with the warehouse.
- Supports:
  - Adding products
  - Restocking
  - Ordering
  - Viewing inventory
  - Exiting application

---

## Usage
1. Clone or download the repository.
2. Compile the Java files:

   ```bash
   javac -d bin src/koo/war/*.java src/koo/pro/*.java src/koo/obs/*.java
3. Run the Application

   ```bash
   java -cp bin koo.war.WarehouseOwner
4. Use the console menu to add products, update stock, fulfill orders, and view inventory.

## Notes
- Observer runs in the background as a daemon thread, automatically alerting low stock.

- All operations are thread-safe using synchronized methods.

- Product IDs are managed internally; customers interact using product names.