
# Wishlist API Documentation

This documentation describes the API endpoints available for managing user wishlists in the ATF (Around The Food) application.

## Base URL
```
http://localhost:8000
```

## Authentication
All API endpoints require authentication using JWT (JSON Web Token). Include the token in the request header:

```json
{
  "Authorization": "Bearer <your_token>"
}
```

## API Endpoints

### 1. Get User's Wishlist
Get all restaurants in the user's wishlist.

**Endpoint:** `GET /wishlist/api/wishlist/`

**Headers:**
```
Authorization: Bearer <your_token>
```

**Success Response:**
```json
[
  {
    "id": "1",
    "name": "Restaurant Name",
    "category": "Italian",
    "image_url": "http://localhost:8000/media/restaurant_image.jpg",
    "rating": 5
  }
]
```

---

### 2. Add Restaurant to Wishlist
Add a restaurant to the user's wishlist.

**Endpoint:** `POST /wishlist/api/add-to-wishlist/{restaurant_id}/`

**Headers:**
```
Authorization: Bearer <your_token>
```

**Success Response:**
```json
{
  "success": true,
  "message": "Restaurant has been added to your wishlist",
  "wishlist": [
    {
      "id": "1",
      "name": "Restaurant Name",
      "category": "Italian",
      "image_url": "http://localhost:8000/media/restaurant_image.jpg",
      "rating": 5
    }
  ]
}
```

---

### 3. Remove Restaurant from Wishlist
Remove a restaurant from the user's wishlist.

**Endpoint:** `DELETE /wishlist/api/remove-from-wishlist/{restaurant_id}/`

**Headers:**
```
Authorization: Bearer <your_token>
```

**Success Response:**
```json
{
  "success": true,
  "message": "Restaurant removed from your wishlist!",
  "wishlist": [
    {
      "id": "1",
      "name": "Restaurant Name",
      "category": "Italian",
      "image_url": "http://localhost:8000/media/restaurant_image.jpg",
      "rating": 5
    }
  ]
}
```

---

## Error Responses

**401 Unauthorized:**
```json
{
  "error": "User is not authenticated."
}
```

**404 Not Found:**
```json
{
  "success": false,
  "message": "Restaurant is not in your wishlist!"
}
```

**500 Internal Server Error:**
```json
{
  "success": false,
  "error": "Error message details"
}
```

---

## Response Status Codes
- **200** - Success
- **401** - Unauthorized
- **404** - Not Found
- **500** - Internal Server Error

---

## Notes
- All requests must include a valid JWT token in the Authorization header.
- The wishlist data is returned in the response after successful add/remove operations.
- Rating value is currently fixed at 5 (placeholder for future implementation).
- For local development, use `http://localhost:8000` as the base URL.
- For production deployment, the base URL will be updated accordingly.
