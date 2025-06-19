# Overview

Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts.

## Airbnb clone project goals

- User Management - Implement a secure system for user registration, authentication, and profile management.
- Property Management - Develop features for property listing creation, updates, and retrieval.
- Booking System - Create a booking mechanism for users to reserve properties and manage booking details.
- Payment Processing - Integrate a payment system to handle transactions and record payment details.
- Review System - Allow users to leave reviews and ratings for properties.
- Data Optimization - Ensure efficient data retrieval and storage through database optimizations.

## Technology Stack

- Django - a web framework for building the RESTful API.
- Django REST Framework - Will be used to Provides tools for creating and managing RESTful APIs.
- PostgreSQL - A relational database used for data storage.
- GraphQL - Will allows for flexible and efficient querying of data.
- Celery - For handling asynchronous tasks such as sending notifications or processing payments.
- Redis - Used for caching and session management.
- Docker - Containerization tool for consistent development and deployment environments.
- CI/CD Pipelines - Automated pipelines for testing and deploying code changes.

## Team Roles

- **Backend Developer** - Responsible for implementing API endpoints, database schema, and business logic.
- **Database Administrator** - Manages database design, indexing and optimizations.
- **DevOps Engineer** - Handles deployment, monitoring and scaling of the backend service
- **QA Engineer** - Ensures the backend functionalities are thoroughly tested and meet quality standards.

## Database Design

### Key entities

1. **Users**: Represents individuals using the platform, either as hosts or guests.
   - **Important Fields**
     - id: Unique identifier for each user.
     - name: Full name of the user.
     - email: Used for login and communication.
     - password: Hashed password for authentication.
     - role: Defines the user's role, such as host or guest.
   - **Relationships**
     - A user can list multiple properties (if host).
     - A user can make multiple bookings (if guest).
     - A user can write multiple reviews.
     - A user can make multiple payments.
2. **Properties**: Represents properties listed by hosts for booking.
   - **Important Fields**
     - id: Unique identifier for each property.
     - title: The name or headline of the property listing.
     - description: Detailed description of the property.
     - price_per_night: Cost of booking the property per night.
     - owner_id: Foreign key linking to the user who owns the property.
   - **Relationships**
     - A property belongs to one user (host).
     - A property can have many bookings.
     - A property can have many reviews.
3. **Bookings**: Represents reservations made by guests to stay at properties.
   - **Important Fields**
     - id: Unique identifier for each booking.
     - user_id: Foreign key referencing the guest who made the booking.
     - property_id: Foreign key referencing the booked property.
     - check_in: Date of check-in.
     - check_out: Date of check-out.
   - **Relationships**
     - A booking belongs to a user (guest).
     - A booking belongs to a property.
     - A booking can have one associated payment.
4. **Reviews**: Represents user feedback and ratings for properties after a stay.
   - **Important Fields**
     - id: Unique identifier for each review.
     - user_id: Foreign key referencing the reviewer (guest).
     - property_id: Foreign key referencing the reviewed property.
     - rating: Numeric rating (e.g., 1 to 5).
     - comment: Textual feedback about the stay.
   - **Relationships**
     - A review belongs to a user (guest).
     - A review belongs to a property.
5. **Payments**: Represents financial transactions made for bookings.
   - **Important Fields**
     - id: Unique identifier for each payment.
     - user_id: Foreign key referencing the user who made the payment.
     - booking_id: Foreign key referencing the related booking.
     - amount: Total payment amount.
     - status: Status of the transaction (e.g., pending, completed).
   - **Relationships**
     - A payment belongs to a user.
     - A payment is linked to one booking.

## Feature Breakdown

This project includes several core features that work together to replicate the functionality of the Airbnb platform. Each feature is designed to enhance the user experience for both guests and hosts.

1. ### User Management
   Enables users to register, authenticate, and manage their profiles. This system ensures secure access to the platform and allows users to interact with other features such as property listings and bookings.
2. ### Property Management
   Allows hosts to create, update, and manage property listings. Each listing includes details like description, pricing, and availability, helping guests find suitable accommodations.
3. ### Booking System
   Provides functionality for guests to reserve properties based on availability. Bookings include check-in and check-out dates, ensuring accurate scheduling and avoiding conflicts.
4. ### Payment Processing
   Handles secure financial transactions for property bookings. This feature ensures that all payments are recorded, validated, and linked to the appropriate users and bookings.
5. ### Review System
   Allows guests to leave feedback and ratings for properties after their stay. Reviews help build trust and transparency between users by showcasing previous guest experiences.
6. ### API Integration
   Offers both RESTful and GraphQL APIs for seamless data access and integration. These APIs ensure flexibility and scalability for front-end and third-party service integration.
7. ### Asynchronous Task Handling
   Utilizes Celery and Redis to handle background tasks such as sending notifications or processing payments. This ensures responsiveness and efficiency across the platform.
