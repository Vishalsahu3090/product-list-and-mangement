# product-list-and-mangement
1. Login (Authentication)
Endpoint: POST /auth/login
Description: Generate a JWT token for admin access.

URL: http://localhost:5000/auth/login
Method: POST
Headers:
Content-Type: application/json
Body (JSON):
json
Copy code
{
  "username": "admin",
  "password": "adminpassword"
}
Expected Response:

json
Copy code
{
  "token": "your_jwt_token_here"
}
2. Create a Product
Endpoint: POST /products
Description: Add a new product. Requires authentication.

URL: http://localhost:5000/products
Method: POST
Headers:
Authorization: Bearer your_jwt_token_here
Content-Type: multipart/form-data
Body:
Use form-data in Postman:
name (Text): "Product Name"
price (Number): 100
category (Text): "Electronics"
inStock (Boolean): true
image (File): Upload an image file (optional).
Expected Response:

json
Copy code
{
  "_id": "unique_id_here",
  "name": "Product Name",
  "price": 100,
  "category": "Electronics",
  "inStock": true,
  "image": "uploads/filename_here",
  "__v": 0
}
3. Get All Products
Endpoint: GET /products
Description: Retrieve all products. Public route.

URL: http://localhost:5000/products
Method: GET
Expected Response:

json
Copy code
[
  {
    "_id": "unique_id_here",
    "name": "Product Name",
    "price": 100,
    "category": "Electronics",
    "inStock": true,
    "image": "uploads/filename_here",
    "__v": 0
  }
]
4. Get Product by ID
Endpoint: GET /products/:id
Description: Retrieve a product by its ID. Public route.

URL: http://localhost:5000/products/unique_id_here
Method: GET
Expected Response:

json
Copy code
{
  "_id": "unique_id_here",
  "name": "Product Name",
  "price": 100,
  "category": "Electronics",
  "inStock": true,
  "image": "uploads/filename_here",
  "__v": 0
}
5. Update a Product
Endpoint: PUT /products/:id
Description: Update a product by ID. Requires authentication.

URL: http://localhost:5000/products/unique_id_here
Method: PUT
Headers:
Authorization: Bearer your_jwt_token_here
Content-Type: application/json
Body (JSON):
json
Copy code
{
  "name": "Updated Product Name",
  "price": 150,
  "category": "Home Appliances",
  "inStock": false
}
Expected Response:

json
Copy code
{
  "_id": "unique_id_here",
  "name": "Updated Product Name",
  "price": 150,
  "category": "Home Appliances",
  "inStock": false,
  "image": "uploads/filename_here",
  "__v": 0
}
6. Delete a Product
Endpoint: DELETE /products/:id
Description: Delete a product by ID. Requires authentication.

URL: http://localhost:5000/products/unique_id_here
Method: DELETE
Headers:
Authorization: Bearer your_jwt_token_here
Expected Response:

json
Copy code
{
  "message": "Product deleted successfully"
}
Common Notes for Postman Testing
Replace your_jwt_token_here with the token received from the login response.
Use the Authorization header in all requests that require authentication.
For testing image uploads, ensure you use multipart/form-data and attach a valid image file in Postman.
This setup will help you verify all backend endpoints.
