Software Requirements Specification (SRS)
1. Introduction

● Project Title: WanderWheel Car Rental System

● Purpose: This project aims to provide a car rental service where users can sign up,
log in, view available cars, book a car, and manage their bookings. The system is
database-driven, utilizing MySQL for data storage and management.

● Scope: The system covers basic user management, car availability, booking
functionality, and booking history, with added automation through SQL functions,
stored procedures, triggers, and events.

3. System Overview
Actors
● User: A registered user who can log in, view available cars, and make bookings.

● System: The database and application interface that handles user requests, car
availability, and booking management.

Main Functions
1. User Registration and Login:

○ Signup: Allows users to create an account by providing details like
username, password, and contact information.

○ Login: Enables existing users to log in using their username and password.

2. Car Viewing:

○ Displays a list of all cars that are currently available for booking.

3. Car Booking:

○ Allows users to book a car by selecting an available car, specifying the start
and end dates for the booking, and viewing the total cost.

4. Booking History:

○ Moves completed bookings to a separate history table for reference and
display completed bookings.

5. Account Information:

○ Users can view their ongoing bookings, past bookings, total spending, and
high-cost bookings.

3. Functional Requirements
3.1 User Registration

● Input: Username, password, full name, phone number, and email.

● Process: Stores user details in the Users table.

● Output: Confirms successful signup.

3.2 User Login

● Input: Username and password.

● Process: Validates credentials against the Users table.

● Output: Confirms successful login or notifies of incorrect credentials.

3.3 Display Available Cars

● Input: None.

● Process: Queries the Cars table for cars with status available.

● Output: List of available cars with car ID, model, seating capacity, rate per day, and
car number.

3.4 Car Booking

● Input: Car ID, start date, end date.

● Process:

○ Calculates the total cost based on the daily rental rate and duration ,using
function CalculateTotalCost.

○ Stores booking details in the Bookings table.

○ Updates car status to booked in the Cars table.

● Output: Confirms booking and displays the total cost and assigned driver details.
Shows ongoing

3.5 Booking History and Status Management

● Input: User ID.

● Process:

○ Moves completed bookings to BookingHistory when the end date has
passed.

○ Updates the car status to available.

● Output: completed bookings for the user.

3.6 Account Information

● Total Spending:

○ Retrieves the total amount spent by the user on bookings from
TotalSpendingView.

● High-Cost Bookings:

○ Shows bookings where the cost is above the average booking cost
AverageBookingCost.

4. Non-Functional Requirements

● Performance: Ensures fast response times for login, booking, and data retrieval.

● Security: User passwords should be securely stored (e.g., hashed).

● Reliability: Ensures consistent data across tables with triggers and stored
procedures for data integrity.

● Usability: Provides a simple, user-friendly console interface for easy interaction.

5. Database Requirements

5.1 Database Tables

● Users: Stores user account information.

● Cars: Contains details on each car and its status.

● Bookings: Stores ongoing booking information.

● BookingHistory: Archives completed bookings.

● TotalSpending and highCostBooking View: View that calculates the total
spending for each user and spendings above average.

5.2 SQL Components

1. Views:

○ TotalSpendingView: Aggregates total spending by each user from
BookingHistory to provide a summary of their expenditure.

○ AverageBookingCost View: Calculates the average booking cost across all
bookings, allowing the system to identify high-cost bookings for a specific
user.

2. Functions:

○ CalculateTotalCost: Calculates the total cost for a booking based on car
rental rates and booking duration, returning the total cost to the application.

3. Stored Procedures:

○ GetActiveBookings: A stored procedure that retrieves ongoing bookings for
a specific user, simplifying the retrieval of current bookings and keeping the
SQL logic within the database.

4. Triggers:

○ after_booking_move: After a booking is transferred to BookingHistory,
this trigger updates the car’s status to available in the Cars table,
ensuring that cars are automatically freed up once a booking ends.

5. Events:

○ move_expired_bookings: An event that runs daily to move expired
bookings (where the end date is before today) from the Bookings table to
BookingHistory. This keeps the system up-to-date with completed rentals.

6. System Requirements

● Software: MySQL database, Java (JDBC),java Swing.

● Hardware: Server with sufficient processing power for database operations.
