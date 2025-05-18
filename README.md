# Food Order API Testing using JSON-server and Postman

## Project Overview
This project simulates an Online Food Delivery Order Placement API using JSON-server as a mock backend and Postman for API testing. It demonstrates how to create, retrieve, and validate food orders with nested JSON arrays and required fields.

---

## Project Structure
- `db.json` — Mock database file containing orders data
- `README.md` — Project documentation

---

## Getting Started

### Prerequisites
- Node.js and npm installed
- JSON-server installed globally
  ```bash
  npm install -g json-server

Postman installed (for API testing)

Setup Instructions
Start the JSON-server:

npx json-server db.json
Use Postman to interact with the API at http://localhost:8000/orders

API Endpoints Tested

| Method | Endpoint  | Description                     |
| ------ | --------- | ------------------------------- |
| GET    | `/orders` | Retrieve all orders             |
| POST   | `/orders` | Place a new food delivery order |

Order JSON Format

{
  "id": 1,
  "customer_name": "John Doe",
  "items": [
    {
      "name": "Burger",
      "price": 100,
      "quantity": 2
    },
    {
      "name": "Fries",
      "price": 50,
      "quantity": 1
    }
  ],
  "restaurant_id": 101,
  "delivery_address": "123 Main St",
  "total_price": 250
}


Testing and Validation

1. Successful Order Creation (POST)
Sent valid POST requests with correctly structured JSON.
Received Status Code 201 Created confirming resource creation.

2. Retrieve Orders (GET)
Sent GET requests to fetch orders.
Received Status Code 200 OK confirming successful data retrieval.

3. Validation of Payload Structure
Verified items is an array of objects with name, price, and quantity.
Confirmed all required fields (customer_name, restaurant_id, delivery_address, total_price) are included.
Tested invalid payloads with missing fields or incorrect items format.
JSON-server accepted invalid payloads because it doesn’t enforce validation; in real APIs, such requests should be rejected.

How to Test Invalid Payloads
Example of invalid POST request body:

{

  "id": 3,
  
  "customer_name": "Riya",
  
  "items": "Burger, Fries",   // Incorrect: items should be an array
  
  "restaurant_id": 104,
  
  "total_price": 300
  
}

Expected behavior in real-world API:
Return 400 Bad Request with validation error.

Actual behavior with JSON-server:
Returns 201 Created (no validation enforcement).

Notes:

JSON-server is used as a mock API; it does not validate payloads strictly.
This project is focused on API request structure, response status validation, and understanding typical backend API behaviors.

Video Demo:

The full execution and testing process is recorded and uploaded on YouTube:
https://youtu.be/M3-B3kjW5Bk 
