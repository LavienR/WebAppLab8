# Customer API Documentation

## Base URL
`http://localhost:8080/api/customers`

## Endpoints

### 1. Get All Customers
**GET** `/api/customers`

**Response:** 200 OK
```json
[
    {
       {
  "totalItems": 5,
  "totalPages": 1,
  "customers": [
    {
      "id": 1,
      "customerCode": "C001",
      "fullName": "John Removed Updated",
      "email": "newJohnmail@gmail.com",
      "phone": "+0957321284",
      "address": "New Address",
      "status": "ACTIVE",
      "createdAt": "2025-12-02T15:46:25"
    },
    {
      "id": 2,
      "customerCode": "C002",
      "fullName": "Jane Smith",
      "email": "jane.smith@example.com",
      "phone": "+1-555-0102",
      "address": "456 Oak Ave, Los Angeles, CA 90001",
      "status": "ACTIVE",
      "createdAt": "2025-12-02T15:46:25"
    },
    {
      "id": 3,
      "customerCode": "C003",
      "fullName": "Bob Johnson",
      "email": "bob.johnson@example.com",
      "phone": "+1-555-0103",
      "address": "789 Pine Rd, Chicago, IL 60601",
      "status": "ACTIVE",
      "createdAt": "2025-12-02T15:46:25"
    },
    {
      "id": 4,
      "customerCode": "C004",
      "fullName": "Alice Brown",
      "email": "alice.brown@example.com",
      "phone": "+1-555-0104",
      "address": "321 Elm St, Houston, TX 77001",
      "status": "INACTIVE",
      "createdAt": "2025-12-02T15:46:25"
    },
    {
      "id": 5,
      "customerCode": "C005",
      "fullName": "Charlie Wilson",
      "email": "charlie.wilson@example.com",
      "phone": "+1-555-0105",
      "address": "654 Maple Dr, Phoenix, AZ 85001",
      "status": "ACTIVE",
      "createdAt": "2025-12-02T15:46:25"
    }
  ],
  "currentPage": 0
}
    }
]


###2. Get Customer by ID
**GET** `/api/customers/{id}`
http://localhost:8080/api/customers/5
**Response:** 200 OK
```json
[
    {
        {
  "id": 5,
  "customerCode": "C005",
  "fullName": "Charlie Wilson",
  "email": "charlie.wilson@example.com",
  "phone": "+1-555-0105",
  "address": "654 Maple Dr, Phoenix, AZ 85001",
  "status": "ACTIVE",
  "createdAt": "2025-12-02T15:46:25"
}
    }
]
http://localhost:8080/api/customers/64
**Response** 404 Not Found
[{{
  "timestamp": "2025-12-07T14:38:28.13214",
  "status": 404,
  "error": "Not Found",
  "message": "Customer not found with id: 64",
  "path": "/api/customers/64",
  "details": null
}}]

3. Create Customer 
**POST**/api/customers
**Response:**  201 Created
[{
    {
  "id": 8,
  "customerCode": "C006",
  "fullName": "M Quan",
  "email": "mquan@example.com",
  "phone": "+0957321284",
  "address": "New Address",
  "status": "ACTIVE",
  "createdAt": "2025-12-07T14:39:25.8584395"
}
}]

**Response**: 400 Bad Request
```json
{
  "id" : 8,
  "customerCode": "C006",
    "fullName": "M Quan",
    "email": "mquan.com",
    "phone": "+0957321284",
    "address": "New Address"
}

[{{
  "timestamp": "2025-12-07T14:40:21.0364813",
  "status": 400,
  "error": "Validation Failed",
  "message": "Invalid input data",
  "path": "/api/customers",
  "details": [
    "email: Invalid email format"
  ]
}}]

**Response**: 409 Conflict
```json
{
  "id" : 6,
  "customerCode": "C006",
    "fullName": "M Quan",
    "email": "charlie.wilson@example.com",
    "phone": "+0957321284",
    "address": "New Address"
}
[{{
  "timestamp": "2025-12-07T14:41:43.3923568",
  "status": 409,
  "error": "Conflict",
  "message": "Customer code already exists: C006",
  "path": "/api/customers",
  "details": null
}}]

**Response**: 500 Internal Server Error
```json
{
  "id" : 8,
  "customerCode": "C016"
    "fullName": "Minh Quan"
    "email": "yui@example.com",
    "phone": "+0957321284",
    "address": "New Address"
}

[{
    {
  "timestamp": "2025-12-07T14:56:36.431854",
  "status": 500,
  "error": "Internal Server Error",
  "message": "JSON parse error: Unexpected character ('\"' (code 34)): was expecting comma to separate Object entries",
  "path": "/api/customers",
  "details": null
}
}]


4. Update Customer
**PUT** `/api/customers/{id}`
**Response:** 200 OK
```json
{
  "id" : 8,
  "customerCode": "C006",
    "fullName": "M Quan",
    "email": "yui@example.com",
    "phone": "+0957321284",
    "address": "New Address"
}
[{
    {
  "id": 8,
  "customerCode": "C006",
  "fullName": "M Quan",
  "email": "yui@example.com",
  "phone": "+0957321284",
  "address": "New Address",
  "status": "ACTIVE",
  "createdAt": "2025-12-07T14:39:26"
}
}]

4. Update Customer
**PUT** `/api/customers/{id}`
**Response:** 200 OK
```json
{
  "id" : 8,
  "customerCode": "C016",
    "fullName": "Minh Quan",
    "email": "yui@example.com",
    "phone": "+0957321284",
    "address": "New Address"
}
[{
    {
  "id": 8,
  "customerCode": "C006",
  "fullName": "Minh Quan",
  "email": "yui@example.com",
  "phone": "+0957321284",
  "address": "New Address",
  "status": "ACTIVE",
  "createdAt": "2025-12-07T14:39:26"
}
}]

5. Search
**GET** /api/customers/search?keyword=Quan
**Response:** 200 OK
```json
[
  {
    "id": 8,
    "customerCode": "C006",
    "fullName": "Minh Quan",
    "email": "yui@example.com",
    "phone": "+0957321284",
    "address": "New Address",
    "status": "ACTIVE",
    "createdAt": "2025-12-07T14:39:26"
  }
]

6. Delete
**DELETE** /api/customers/{id}
http://localhost:8080/api/customers/8
Status: 200 OK
{
  "message": "Customer deleted successfully"
}