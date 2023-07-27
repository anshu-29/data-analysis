

# Personal Details Database - README

This repository contains the SQL script to create and populate the "Personal_Details" database. The database is designed to store information related to clients, products, employees, orders, and other related activities.

## Database Schema

The database consists of the following tables:

1. **Clients:** Stores client information such as ClientID, FullName, ContactNumber, and AddressID.

2. **Products:** Contains product details including ProductID, ProductName, BuyPrice, SellPrice, and NumberOfItems.

3. **Addresses:** Stores address information with AddressID, Street, and County.

4. **Employees:** Contains employee details like EmployeeID, FullName, JobTitle, Department, and AddressID.

5. **Activity:** Holds activity data with ActivityID and Properties (stored as JSON format).

6. **Audit:** Records auditing data with AuditID, OrderDateTime (timestamp).

7. **Orders:** Stores order information with OrderID, ClientID, ProductID, Quantity, Cost, and Date. It has foreign key constraints on ClientID and ProductID referencing the Clients and Products tables, respectively.

8. **Notifications:** Keeps track of notifications with NotificationID, Notification, and DateTime.

## Functions and Procedures

1. **FindAverageCost(YearInput INT):** A function that calculates and returns the average cost of orders placed in a given year (YearInput). Call this function using `SELECT FindAverageCost(2022);` to get the average cost for the year 2022.

2. **EvaluateProduct(IN product_id VARCHAR(10), OUT SoldItemsIn2020 INT, OUT SoldItemsIn2021 INT, OUT SoldItemsIn2022 INT):** A stored procedure that retrieves the total quantity of a specific product (product_id) sold in the years 2020, 2021, and 2022. Call this procedure using the `CALL EvaluateProduct('P1', @sold_items_2020, @sold_items_2021, @sold_items_2022);` statement and then fetch the results using `SELECT @sold_items_2020, @sold_items_2021, @sold_items_2022;`.

## Triggers

1. **UpdateAudit Trigger:** A trigger that automatically inserts a new record into the "Audit" table after every new entry in the "Orders" table. The "Audit" table contains the OrderDateTime (timestamp) of the order insertion.

## Views

1. **DataSummary View:** A view that provides a summary of data for the year 2022. It includes client information (FullName, ContactNumber), address county, product name, product ID, order cost, and order date. To access the view, use `SELECT * FROM DataSummary;`.

## Data Population

The database is populated with sample data for clients, products, employees, orders, and activities. The sample data provides a foundation for testing and analysis.

Please feel free to explore the database and use the provided functions, procedures, and views to gather relevant information.

If you encounter any issues or have suggestions for improvement, please feel free to create an issue or reach out to the repository maintainer.

Thank you for using the Personal_Details database! Happy coding!
