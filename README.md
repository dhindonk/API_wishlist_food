
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

## Endpoints

### 1. **Get Wishlist**

**URL**: `/api/wishlist/`  
**Method**: `GET`  
**Headers**:  
```json
{
    "Authorization": "Bearer <your_token>"
}
```
**Response**:
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

### 2. **Add to Wishlist**

**URL**: `/api/wishlist/`  
**Method**: `POST`  
**Headers**:  
```json
{
    "Authorization": "Bearer <your_token>"
}
```
**Request Body**:
```json
{
    "restaurant_id": "1"
}
```
**Response**:
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

### 3. **Remove from Wishlist**

**URL**: `/api/wishlist/<id>/`  
**Method**: `DELETE`  
**Headers**:  
```json
{
    "Authorization": "Bearer <your_token>"
}
```
**Response**:
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

### 1. **Unauthorized Access**
**Response**:
```json
{
    "error": "User is not authenticated."
}
```

### 2. **Restaurant Not in Wishlist**
**Response**:
```json
{
    "success": false,
    "message": "Restaurant is not in your wishlist!"
}
```

### 3. **General Error**
**Response**:
```json
{
    "success": false,
    "error": "Error message details"
}
```
