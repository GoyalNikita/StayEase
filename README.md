
## StayEase : Room Booking Application

### Author
Nikita Goyal

### Overview

StayEase is a RESTful API service designed to streamline the room booking process for a hotel management aggregator application. This application is built using Spring Boot and MySQL to manage and persist data. The service includes authentication and authorization using JWT tokens and supports three roles: CUSTOMER, MANAGER, and ADMIN.


 
## Key Features :

- Simplified room booking system.
-   Assumptions:
    - Single type of room, bookings for two guests.
    - Any hotel manager can update any hotel details.
    - Check-in and check-out are handled by another service.
- JWT tokens for session management.
- Public and private API endpoints.
- User roles: CUSTOMER, HOTEL MANAGER, ADMIN.

## API Features :

### 1. User Registration and Login

- Users can register with an email address and password.
- Passwords are encrypted using BCrypt.
- Fields: Email, Password, First Name, Last Name, Role.
- Default role is "Customer" if not specified.
- JWT token generation upon successful login.

### 2. Hotel Management

- Store and manage hotel details.
- Fields: Hotel Name, Location, Description, Number of Available Rooms.
- Anyone can browse available hotels (public endpoint).
- Only the admin can create and delete hotels.
- Hotel managers can update hotel details.

### 3. Booking Management

- Customers can book rooms.
- Single room booking per request.
- Only hotel managers can cancel bookings.

## Requirements :

### 1. Logging
- Log information and errors using SLF4J.

### 2. Error Handling
- Graceful handling of common errors with appropriate HTTP codes.

### 3. Testing
- Basic unit tests with MockMvc and Mockito 

### 4. Deployment
- Generate a JAR file for the application.
- Instructions on how to run the application.

### 5. Documentation
- Descriptive README.md.
- Public Postman Collection.

## Project Structure

The project follows a layered architecture approach:

- `entities` : Contains the entity classes.
- `controllers`: Handles incoming HTTP requests and responses.
- `services`: Contains the logic for managing users books and rentals.
- `repositories`: Interacts with the MySQL Database.
- `exceptions` : Contains the custom exceptions and exception handler classes. 



## Setup Instructions :

### Prerequisites

- Java 11 or higher
- Gradle 6.0.8 or higher
- MySQL 8.0 or higher
- Git
- Postman


To run the application follow the following steps :

### Local Environment Setup :
#### 1. Clone the repository :

    git clone https://github.com/GoyalNikita/StayEase.git


### 2. Set up the MySQL database :

- Update the application.properties file with your MySQL database details:

        spring.datasource.url = jdbc:mysql://localhost:{port ex. 3300, 3306}/{databse name}
        spring.datasource.username={username}
        spring.datasource.password={password}
        spring.jpa.hibernate.ddl-auto=update

#### 2. Navigate to the project directory :

    cd StayEase

#### 3. Build the project :

    gradle build 

#### 4. Run the application :

To run the application use following command.

    java -jar build/libs/StayEase-0.0.1-SNAPSHOT.jar


#### 5. Access the APIs:

Once the application is running, you can access the API at

    http://localhost:8080


## Running Tests :

Use the following command to run the unit tests :

    gradle test
## Endpoints :

### 1. Public Endpoints 
#### i. Accessible to everyone 
- User Registration : POST /register
- User Login  : POST /login
- Browse Hotel : GET /hotels
- Browse Hotel : GET /hotels/{hotelId}


### 2. Private Endpoints

#### i. Accessible to Authenticated USERS
- User Update : PUT /users/{userId}
- User Book Room : POST /hotels/{hotelId}/book

#### ii. ADMIN only 
- Create Hotel : POST /hotels
- Delete Hotel : Delete /hotels/{hotelId}

#### iii. MANAGER only
- Update Hotel : PUT /hotels/{hotelId}
- Cancel Booking : DELETE /bookings/{bookingId}

#### iv. Both ADMIN and MANAGER
- Read USER : GET /users
- Read USER : GET /users/{userId}
- Read USER : GET /users/emailId
- Delete USER : DELETE /users/{userId}
- Update Hotel : PUT /hotels/{hotelId}
- Read Booking  : GET /bookings/{bookingId}
- Read Bookings : GET /bookings 

#### NOTE : Use the following link to read all the API Documentation only after running the application.

[API Documentation using OpenAPI](http://localhost:8080/swagger-ui/index.html)
## Postman Collection

You can use the following Postman Collection to test the API:
[StayEase Postman Collection](https://new666-9823.postman.co/workspace/New-Workspace~446ac2dc-32b8-4882-b3de-4aba165c8ad5/collection/36335262-6130515d-78bc-4988-b8eb-64c317aad9dd?action=share&creator=36335262)
