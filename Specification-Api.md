# Specification of Online Loan API

## Description
This API provides services for managing users, loans, payments, and transaction management for online loan fintech platforms.

## Endpoint
- Base URL: `https://fintechpinjaman.com/api`


### User

#### Registratioin User
Used to register a new user into the system.
- `POST /users/register`

##### Input Parameter
| Field     | Tipe   | Deskripsi             |
|-----------|--------|-----------------------|
| name      | string | user's name         |
| email     | string | user's email address|
| password  | string | user's password  |

##### Response

| Field     | Tipe   | Deskripsi             |
|-----------|--------|-----------------------|
| id        | integer| user ID           |
| name      | string | user's name         |
| email     | string | user's email address|

##### Sample :
- Request Body
```json
{
    "name": "Nama Pengguna",
    "email": "email@example.com",
    "password": "password123"
}
```
- Response Body (Success) :
```json
{
    "id": 1,
    "name": "Nama Pengguna",
    "email": "email@example.com"
}
```

#### Login
Used to log in to the system.

- `POST /users/login`

##### Input Parameter
| Param     | Type   | Length  | Meaning             |
|-----------|--------|---------|-----------------------|
| email     | string | 75      | user's email address        |
| password  | string | 225     | user's password  |

##### Output Parameter
| Param     | Type   | Length  | Meaning             |
|-----------|--------|---------|----------------------|
| token     | string | 600     | token from system : Bearer (Token JWT)  |

##### Sample :

- Request Body
```json
{
    "email": "email@example.com",
    "password": "password123"
}
```
- Response Body (Success) :
```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJlbWFpbEBleGFtcGxlLmNvbSIsImlhdCI6MTY0OTYxNDU1OH0.YVW9BYIzBgswQ65Joxqz7e2kX8nEnbJJmtr_NtP3lDo"
}
```

### Loans

#### List of Loans
Used to retrieve the list of available loans.

- `GET /loans`

#### Request Header :

| Attribute     | Type   | Length             | Meaning             |
|-----------|--------|-----------------------|-----------------------|
| Content-Type      | string | 16         |"application/json"
| token     | string | 600|Bearer (Token JWT)|


##### Output Parameter
| Param     | Type   | Length  | Meaning             |
|-----------|--------|---------|----------------------|
| id     | string | 600     | token from system    |
| amount     | Integer | 11     | total amount in rupiah    |
| interest_rate     | Integer | 3     | interest in percentage    |
| term     | Integer | 3     | termins of months   |
| status     | string | 25     | status of loans   |

##### Sample :
- Header:
```code
Content-Type : application/json
token :    47b54594063957de22fce0aeddd51a6adf4a80aa
```

- Response Body (Success) :
```json
[
    {
        "id": 1,
        "amount": 1000000,
        "interest_rate": 10,
        "term": 12,
        "status": "available"
    },
    {
        "id": 2,
        "amount": 500000,
        "interest_rate": 8,
        "term": 6,
        "status": "available"
    }
]
```

#### Apply for a Loan
Used to apply for a new loan.

- `POST /loans/apply`

#### Request Header :

| Attribute     | Type   | Length             | Meaning             |
|-----------|--------|-----------------------|-----------------------|
| Content-Type      | string | 16         |"application/json"
| token     | string | 600|Bearer (Token JWT)|


##### Output Parameter
| Param     | Type   | Length  | Meaning             |
|-----------|--------|---------|----------------------|
| id     | string | 600     | token from system    |
| amount     | Integer | 11     | total amount in rupiah    |
| interest_rate     | Integer | 3     | interest in percentage    |
| term     | Integer | 3     | termins of months   |
| status     | string | 25     | status of loans   |

##### Sample :
- Header:
```code
Content-Type : application/json
token :    47b54594063957de22fce0aeddd51a6adf4a80aa
```
- Request Body :
```json
{
    "amount": 1000000,
    "term": 12
}
```
- Response Body (Success) :
```json
{
    "id": 3,
    "amount": 1000000,
    "interest_rate": 10,
    "term": 12,
    "status": "pending"
}
```

### Payment

#### Installment Payment
Used to make installment payments.

- `POST /payments`

#### Request Header :

| Attribute     | Type   | Length             | Meaning             |
|-----------|--------|-----------------------|-----------------------|
| Content-Type      | string | 16         |"application/json"
| token     | string | 600|Bearer (Token JWT)|

##### Input Parameter
| Param     | Type   | Length  | Meaning             |
|-----------|--------|---------|-----------------------|
| loan_id     | string | 100      | id of the loan        |
| amount  | int | 11     | total amount to be paid (rupiah)|

##### Output Parameter
| Param     | Type   | Length  | Meaning             |
|-----------|--------|---------|----------------------|
| id     | string | 600     | id from system    |
| loan_id     | Integer | 11     | id of the loan     |
| amount     | Integer | 3     | Total amount paid (rupiah)   |
| status     | string | 25     | status of the payment   |

##### Sample :
- Header:
```code
Content-Type : application/json
token :    47b54594063957de22fce0aeddd51a6adf4a80aa
```
- Request Body :
```json
{
    "loan_id": 3,
    "amount": 100000
}
```
- Response Body (Success) :
```json
{
    "id": 1,
    "loan_id": 3,
    "amount": 100000,
    "status": "success"
}
```

## Errors
- 400 Bad Request: Invalid request.
- 401 Unauthorized: Access denied due to authentication failure or invalid token.
- 404 Not Found: Data not found.
- 500 Internal Server Error: Internal server error.
