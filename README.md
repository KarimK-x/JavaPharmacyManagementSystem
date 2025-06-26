# Pharmacy Management System

## Overview
The **Pharmacy Management System** is a Java-based application designed to streamline pharmacy operations, including inventory management, order processing, payment handling, and financial reporting. Developed using Maven and JavaFX for a user-friendly graphical interface, the system supports both console-based and GUI interactions. The project includes unit tests with JUnit to ensure reliability of key functionalities.

## Team Members
- Marina Bebawy Nasr (ID: 2200826)
- Karim Mohamed Elsayed (ID: 2200746)
- Menna Ayman Hassan (ID: 2200236)
- Karim Khaled Gamaleldin (ID: 2201356)

## Features
- **User Management**:
  - Admin registration with secure password setup and login validation.
  - Customer registration with order history tracking.
- **Inventory Management**:
  - Supports multiple item categories: Medicines, Supplements, Baby Care, Personal Care, and Devices.
  - Real-time stock tracking with add, remove, and availability checks.
- **Order Processing**:
  - Create and validate orders with inventory checks.
  - Add/remove items from orders and calculate totals.
- **Payment System**:
  - Supports cash and card payments with balance validation.
  - Generates receipts for finalized orders.
- **Financial Reporting**:
  - Tracks sales, expenses, and profits for specific dates.
  - Summarizes financial data for the pharmacy branch.
- **Graphical User Interface**:
  - JavaFX-based GUI for browsing products, adding to cart, and processing payments.
  - Includes login page, product selection, and receipt display.

## Project Structure
```
karimk-x-javapharmacymanagementsystem/
├── README.md                    # Project documentation
└── PharmacyManagementSystem/
    ├── pom.xml                  # Maven configuration file
    └── src/
        ├── main/
        │   └── java/
        │       └── com/mycompany/pharmacymanagementsystem/
        │           ├── Admin.java
        │           ├── BabyCare.java
        │           ├── Branch.java
        │           ├── Customer.java
        │           ├── Devices.java
        │           ├── Expenses.java
        │           ├── Financials.java
        │           ├── Inventory.java
        │           ├── Item.java
        │           ├── Main.java
        │           ├── MainFX.java
        │           ├── Medicine.java
        │           ├── Order.java
        │           ├── Payments.java
        │           ├── PersonalCare.java
        │           ├── Pharmacy.java
        │           ├── Receipt.java
        │           ├── Sales.java
        │           ├── Supplements.java
        │           └── User.java
        └── test/
            └── java/
                └── com/mycompany/pharmacymanagementsystem/
                    └── InventoryTest.java
```

- **`src/main/java`**: Contains the core application logic, including classes for users, items, inventory, orders, payments, and financials.
- **`src/test/java`**: Includes JUnit tests for the `Inventory` class.
- **`src/main/resources/images`**: Stores image assets for the JavaFX GUI (e.g., `Logo.png`, product images).
- **`pom.xml`**: Defines Maven dependencies (JavaFX, JUnit) and build configurations.

## Prerequisites
- **Java**: Version 23 or higher.
- **Maven**: For building and managing dependencies.
- **JavaFX**: Version 21.0.2 (included via Maven dependencies).
- **JUnit**: Version 5.10.0+ for running unit tests.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/karimk-x/javapharmacymanagementsystem.git
   cd karimk-x-javapharmacymanagementsystem/PharmacyManagementSystem
   ```

2. **Install Dependencies**:
   Run the following command to download dependencies specified in `pom.xml`:
   ```bash
   mvn clean install
   ```

3. **Set Up Image Assets**:
   - Ensure the `src/main/resources/images` directory contains required images (e.g., `Logo.png`, `Strepsils.jpg`, `Panadol.jpg`, `Fucicort.png`, `Zithromax.jpg`).
   - Update image paths in `MainFX.java` to use relative paths (e.g., `getClass().getResource("/images/Logo.png")`) for portability.

## Running the Application
### Console Application
To run the console-based version and test core functionalities:
```bash
mvn exec:java -Dexec.mainClass="com.mycompany.pharmacymanagementsystem.Main"
```
This executes `Main.java`, which demonstrates user management, order processing, and financial reporting via console output.

### GUI Application
To run the JavaFX GUI:
```bash
mvn javafx:run
```
This executes `MainFX.java`, launching the graphical interface with login, product browsing, and checkout features.

### Running Tests
To execute the JUnit tests for the `Inventory` class:
```bash
mvn test
```
This runs the tests in `InventoryTest.java`, covering the `isAvailable()` method for null, available, and unavailable items.

## Usage
### Console Application (`Main.java`)
- Creates a pharmacy branch in "New Cairo".
- Demonstrates admin/customer creation, inventory setup, order placement, payment processing, and financial reporting.
- Outputs results to the console, including stock levels and financial summaries.

### GUI Application (`MainFX.java`)
1. **Login Page**:
   - Enter email and password to access the system (currently a placeholder; password validation is console-based in `Admin.java`).
   - Click "Login" to proceed to the product page.
2. **Product Page**:
   - Browse available medicines (e.g., Strepsils, Panadol Extra).
   - Enter quantity and click "ADD" to add items to the cart.
   - Use navigation buttons (Home, Cart, Logout, About Us, Check Out).
3. **Checkout**:
   - Click "Check Out" to view the receipt with purchased items and total.
   - Select payment method (Cash or Card) and enter the amount/balance.
   - Confirm payment to finalize the order and clear the cart.

### Example Workflow
1. Run the GUI application (`mvn javafx:run`).
2. Log in to access the product page.
3. Add 2 units of Panadol Extra ($8 each) to the cart.
4. Proceed to checkout, select "Cash", and enter $16.
5. View the receipt and confirm payment to complete the transaction.

## Testing
The project includes JUnit tests in `InventoryTest.java` for the `Inventory.isAvailable()` method:
- **Null Pointer Test**: Verifies that a `NullPointerException` is thrown for a null item.
- **True Test**: Confirms `isAvailable()` returns `true` for an item in stock.
- **False Test**: Confirms `isAvailable()` returns `false` for an item not in stock.


## Known Issues
- **Hardcoded Image Paths**: `MainFX.java` uses absolute paths for images, reducing portability. Update to relative paths using `getResource`.
- **Static Variables**: Classes like `Sales` and `Expenses` use static histories, which may cause issues in multi-branch scenarios. Consider moving to instance-based storage or a database.
- **Incomplete Device Integration**: `Devices` does not extend `Item`, leading to inconsistent inventory handling. Integrate `Devices` into the `Item` hierarchy.
- **Order Removal**: The `Order.removeItem` method does not restore inventory quantities. Implement reverse deduction logic.
- **Console-Based Passwords**: `Admin` class uses console input for passwords, incompatible with the GUI. Replace with JavaFX-based input.

## Future Improvements
- **Database Integration**: Replace static `ArrayList`s with a database (e.g., MySQL, SQLite) for persistent storage of users, orders, and financials.
- **Enhanced GUI**: Add features like user registration forms, order history views, and admin dashboards.
- **Authentication System**: Implement proper user authentication with encrypted passwords.
- **Receipt Formatting**: Generate formatted receipts (e.g., as PDFs) with timestamps and branch details.
- **Expanded Testing**: Increase test coverage for critical methods and edge cases.

## Presentation
For a detailed overview of the project, refer to the PowerPoint presentation (`Team19PharmacyPresentation.pptx`) included in the repository.
