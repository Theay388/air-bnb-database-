Database Structure Overview
The system is built upon a normalized relational architecture consisting of 21 specialized
tables . It is structured to handle three primary user roles: Guests, Hosts, and Admins, each
with distinct permissions and actions . The core of the database centers on the relationship
between users, the properties they list or book, and the subsequent financial and feedback
loops. Key structural components include:
• Core Entities: Central tables such as User, Property, and Booking store foundational
data.
• Relational Logic: The design utilizes one-to-many and many-to-many relationships,
the latter managed through junction tables like Property_Amenity.
• Integrity Constraints: Primary and foreign keys are strictly defined to maintain data
consistency across all 21 entities.
2. Tools and Technology
The platform is developed using the following technological stack:
• Database Management System: MySQL is the primary RDBMS used for its reliability
in handling relational data and foreign key constraints.
• Language: SQL (Structured Query Language) is employed for schema definition,
data manipulation, and complex analytical querying.
• Data Accuracy: The system utilizes specific data types like DECIMAL(10,2) for
financial precision and TIMESTAMP for real-time tracking.
3. Installation Requirements
To successfully deploy the database, the following environment specifications must be met:
• Administrative Access: The user must have privileges to create schemas and grant
permissions within a MySQL instance.
• Resource Allocation: Sufficient storage for the 21-table schema and initial test data .
• Sequential Logic: An understanding of data dependencies is required, as tables must
be populated in a specific order to satisfy foreign key requirements.
4. Installation Manual
4.1 Required Software
• MySQL Server (v8.0 or higher): The core database engine.
• MySQL Workbench or Command-Line Client: For executing the SQL scripts and
managing the schema.
4.2 Database Setup Instructions
The installation must follow a tiered approach to ensure relational integrity:
1. Schema Initialization: Create and select the database environment.
SQL
CREATE DATABASE Airbnb_Platform;
USE Airbnb_Platform;
2. Tier 1 (Independent Tables): Create the User table first, followed by utility tables like
Amenity and ServiceProvider.
3. Tier 2 (Dependent Tables): Create tables that rely on Tier 1, such as Guest, Host,
Admin, and Property.
4. Tier 3 (Relational Tables): Create the Booking and Message tables, which link
multiple users and properties.
5. Tier 4 (Junction & Detail Tables): Finalize the setup with tables like Payment, Review,
Property_Amenity, and HostPaymentRecord.
5. Verify Database Creation
Verification is conducted by executing analytical queries that require cross-table joins.
Success is confirmed if the system returns accurate aggregate data.
Example Verification Query (Host Earnings): This query joins HostPaymentRecord, Host,
and User to calculate total revenue per host :
SQL
SELECT u.Name AS HostName, SUM(h.Amount) AS TotalEarnings
FROM HostPaymentRecord h
JOIN Host ho ON h.HostID = ho.HostID
JOIN User u ON ho.UserID = u.UserID
GROUP BY h.HostID
ORDER BY TotalEarnings DESC;
6. Final Deliverables Checklist
The installation is considered complete once all 21 tables are established, foreign keys are
validated, and the initial dataset of 423 entries is successfully inserted without constraint
violations. The system is then ready to support real-world simulations of property listings,
bookings, and user interactions.
7. Summary
This structured approach ensures the development of a high-quality, professional database
system. By adhering to normalization principles and strict relational mapping, the platform
provides an organized, consistent, and efficient environment for managing the complex data
needs of a modern accommodation service.
