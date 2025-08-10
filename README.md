# airbnb-clone-project

Team Roles:
1. Backend Developer
What they do: Create and manage the server-side logic powering user features such as listing search, bookings, messaging, and authentication.

Airbnb-clone focus:
* Design RESTful APIs for functionality like search, reservations, and user registration.
* Implement business rules like availability checks or payment logic.
* Ensure robust security and maintain optimum performance.
* Provide clear documentation for other contributors.


2. Database Administrator (DBA)
What they do: Ensure the stability, security, and performance of the database systems supporting the app.

Airbnb-clone focus:
* Set up and maintain a production-grade database (e.g., PostgreSQL).
* Tune performance via indexing and monitoring.
* Implement backup strategies and manage disaster recovery.
* Enforce access controls and ensure high availability of data.


3. DevOps Engineer
What they do: Bridge development and operations to automate infrastructure, streamline deployments, and enforce reliability.

Airbnb-clone focus:
* Implement CI/CD pipelines for smooth delivery of features.
* Use Infrastructure as Code (e.g., Terraform, Docker) to provision environments.
* Monitor app performance and enable rapid rollback capabilities.
* Support scaling in real time (e.g., container orchestration, cloud infrastructure).


4. QA Engineer
What they do: Validate software quality to ensure the app functions correctly and reliably.

Airbnb-clone focus:
* Design and execute test plans across features like search, booking, messaging, and payments.
* Perform both manual and automated testing, including unit, integration, and end-to-end tests.
* Identify, report, and verify bug fixes.
* Integrate testing into CI/CD pipelines to catch regressions early.


Technology Stack:
1. Django serves as the core backend framework, managing essential features like user authentication, listings, bookings, and admin functionality.

2. Django REST Framework (DRF) builds on Django to provide RESTful APIs, allowing the frontend or mobile apps to interact with the backend through endpoints for listings, bookings, and user data.

3. GraphQL can be used as an alternative to REST to enable more flexible and efficient data querying, allowing clients to request only the data they need—such as fetching a listing, its reviews, and host details in a single query.

4. Celery handles background tasks asynchronously, ensuring that operations like sending emails, processing bookings, or updating calendars do not block user interactions.

5. Redis functions as a fast in-memory data store, typically used as a message broker for Celery and for caching frequently accessed data like search results or user sessions.

6. Docker containerizes the entire application stack—including Django, Celery, Redis, and databases—making development, testing, and deployment consistent across different environments.


Database Design:
1. Users
user_id
name
email
password
role (e.g., guest, host)

2. Properties (Listings)
property_id
host_id (references Users)
title
location
price_per_night

3. Bookings
booking_id
property_id (references Properties)
guest_id (references Users)
start_date
end_date

4. Reviews
review_id
property_id (references Properties)
user_id (references Users)
rating
comment

5. Payments
payment_id
booking_id (references Bookings)
user_id (payer)
amount
payment_status

Entity Relationship
* A User can be a host who owns multiple Properties.
* A User can also be a guest who makes multiple Bookings.
* Each Property belongs to one host (User) but can have many Bookings from different guests.
* Each Booking is linked to one Property and one guest (User).
* Users (guests) can write multiple Reviews, each tied to a specific Property they stayed in.
* Each Booking has one associated Payment, made by the guest who booked it.

