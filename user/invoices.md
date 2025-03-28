
Here is a sample `README.md` documentation for your PHP API controller:

---

# API Documentation - User Items Controller

This document provides the API documentation for interacting with the `Items` controller of the User API. It describes how to perform CRUD operations for items and invoices, along with pagination and validation details.

## API Base URL

All API endpoints are under the following base URL:

```
http://yourdomain.com/api/user/items
```

## Endpoints

### 1. **GET /items**

Retrieve a paginated list of items associated with the authenticated user.

#### Query Parameters:
- `page` (optional) - The page number (default: 1).
- `limit` (optional) - The number of items per page (default: 10).
- `orderby` (optional) - The field to order results by (e.g., 'created_at').
  
#### Response:
```json
{
  "pagination": {
    "prev": 1,
    "next": 3,
    "list_prev": [1, 2],
    "list_next": [3, 4]
  },
  "current_page": 1,
  "total_pages": 10,
  "item_found": 100,
  "curent_item": 10,
  "limit": 10,
  "data": [
    {
      "id": 1,
      "product_id": 123,
      "created_at": "2025-03-01T10:00:00Z",
      "detail": {
        "id": 123,
        "name": "Product Name",
        "price": 100
      }
    },
    ...
  ]
}
```

### 2. **GET /invoices**

Retrieve a paginated list of invoices for the authenticated user.

#### Query Parameters:
- `page` (optional) - The page number (default: 1).
- `limit` (optional) - The number of invoices per page (default: 10).

#### Response:
```json
{
  "pagination": {
    "prev": 1,
    "next": 3,
    "list_prev": [1, 2],
    "list_next": [3, 4]
  },
  "current_page": 1,
  "total_pages": 10,
  "item_found": 100,
  "curent_item": 10,
  "limit": 10,
  "data": [
    {
      "id": 1,
      "product_id": 123,
      "created_at": "2025-03-01T10:00:00Z",
      "detail": {
        "id": 123,
        "name": "Product Name"
      }
    },
    ...
  ]
}
```

### 3. **POST /create_invoice**

Create a new invoice for a product.

#### Request Body:
```json
{
  "product_id": 123,
  "price": 100
}
```

#### Validation:
- `product_id` (required, integer): The product ID.
- `price` (required, integer): The price for the product.

#### Response:
```json
{
  "status": 201,
  "message": "Berhasil Membuat Invoices",
  "invoice_id": 123
}
```

### 4. **DELETE /items/{id}**

Delete an item by its ID.

#### Parameters:
- `id` (required, integer): The ID of the item to delete.

#### Response:
```json
{
  "status": 200,
  "message": "Data berhasil dihapus"
}
```

## Authentication

The API relies on user authentication. The `auth_user` is stored in the session and is used to validate the user's access to their items and invoices.

- **Session-based Authentication**: The API uses session variables to check the authenticated user's `user_id`.

## Error Handling

The following error responses are used:

- **400 Bad Request**: When required fields are missing or invalid data is sent.
- **401 Unauthorized**: When the user is not authenticated.
- **403 Forbidden**: When the user tries to access or modify resources that they don't own.
- **404 Not Found**: When the requested item or invoice is not found.
- **500 Internal Server Error**: When something goes wrong on the server-side.

## Example Request

To create an invoice:

```bash
POST /api/user/items/create_invoice
{
  "product_id": 123,
  "price": 100
}
```

To retrieve a list of items:

```bash
GET /api/user/items?page=1&limit=10
```

---

### License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

---

Feel free to update any placeholder values (like URLs or product details) based on your actual environment and requirements.
