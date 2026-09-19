A comprehensive API test automation and manual validation suite built for the Restful Booker service using Postman. This project showcases end-to-end test coverage, dynamic environment management, negative scenario validations, edge-case analysis, and formal bug reporting.
🚀 Project Overview
Target API: Restful Booker Heroku App


Testing Tool: Postman & Newman CLI
Scripting Language: JavaScript (Chai assertions for Postman tests)
Test Scope: Happy Paths, CRUD Operations, Negative Scenarios, and Edge Cases
📂 Repository Structure
restful-booker-api-testing/
│
├── collections/
│   └── Restful_Booker_API.postman_collection.json
│
├── environments/
│   └── Restful_Booker.postman_environment.json
│
├── bug-reports/
│   ├── bug_report_invalid_dates.md
│   └── bug_report_negative_price.md
│
└── README.md

🛠️ Endpoints & Test Coverage

The collection covers the complete API lifecycle using dynamic environment variables (baseURL, token, and bookingid) to prevent hardcoded values:

GET /ping – Health check to verify API availability.
POST /auth – Dynamic authentication to generate and persist the admin token.
GET /booking – Retrieve all booking IDs.
POST /booking – Create a new booking (Happy path & Edge cases).
GET /booking/:id – Retrieve specific booking details.
PUT /booking/:id – Full update of an existing booking.
PATCH /booking/:id – Partial update of an existing booking.
DELETE /booking/:id – Remove a booking record.

🧪 Test Scenarios Included

Positive / Happy Path Tests: Validates standard CRUD workflows with proper authentication and assertion checkpoints.
Negative Scenarios:
Accessing or modifying records using invalid/expired tokens (Expects 403 Forbidden).
Accessing deleted records (Expects 404 Not Found).
Submitting incomplete payloads.
Edge Cases:
Boundary value analysis for pricing (submitting negative values).
Date logic validation (check-out date prior to check-in date).

🐛 Discovered Bugs

During exploratory and edge-case testing, two logical validation issues were identified in the API backend:
Invalid Booking Dates Accepted: The API accepts and stores bookings where the check-out date is earlier than the check-in date (200 OK instead of 400 Bad Request). (Detailed report available in bug-reports/).
Negative Total Price Accepted: The API permits negative values for the totalprice field without throwing a validation error. (Detailed report available in bug-reports/).
