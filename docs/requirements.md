# MobilityCorp System Requirements

## Functional Requirements
1. User Account Management
    * Registration
    * Authentication
    * Authorization
1. Vehicle booking
    * Cars and vans can be booked up to 7 days in advance with specific duration. 
    * Bikes and scooters can be booked up to 30 minutes in advance with open-ended duration (max 12 hours).
1. Payment Processing
    * Per-minute rental pricing
    * Fine system for late returns or wrong location returns
    * Payment processing integration
1. Vehicle Access
    * NFC-capable smartphone app to lock/unlock vehicles
    * Remote unlock capability by MobilityCorp
1. Vehicle Return Process
    *  Photo submission of returned vehicle for proof
    * GPS verification of return location
    * Confirmation that Cars/Vans are plugged into EV chargers
    * Customer feedback submission (including vehicle faults)
1. Vehicle Location Services
    * Real-time GPS tracking of all vehicles
    * Display available vehicles to customers
    * Show designated parking spots
1. Operations
    * Battery swap scheduling for bikes/scooters
    * Staff routing system for maintenance visits
    * Vehicle redistribution to popular locations
    * Fault tracking and maintenance scheduling
1. Data Collection
    * GPS tracking data
    * Battery levels/charge status
    * Usage patterns and history
    * Customer feedback collection
    * Vehicle condition monitoring
    * Photo evidence storage

## Non-Functional Requirements

1. Availability
    * System must be available 24/7 for bookings
    * Real-time vehicle access required
    * GPS tracking must be continuous
1. Scalability
    * Multiple city locations, multiple countries, supporting many languages across the EU
    * Current fleet size, no plans to expand. (200 cars, 200 vans, 2,000 scooters, and 2,000 bikes per metro)
    * Increasing customer base, 10x
1. Reliability
    * Accurate GPS tracking
    * Reliable payment processing
    * Accurate billing calculations
    * Data storage and retrieval
    * Booking history accuracy
1. Performance
    * Near real-time location updates
    * Fast booking response times
    * Efficient route optimization for staff
1. Security
    * Secure payment processing
    * Protected customer data
    * Authentication and authorization
1. Usability
    * Intuitive mobile app interface
    * Easy booking process
    * Clear return instructions