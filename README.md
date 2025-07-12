# Domain Model

```mermaid
classDiagram
direction BT

class User {
  UUID id
  String email
  String password
  String googleId
  String fullName
  String phone
  String avatar
  String role
  Boolean isActive
  Date dateOfBirth
  String gender
}

class Cart {
  UUID id
}

class CartItem {
  UUID id
  Integer quantity
}

class Order {
  UUID id
  String orderNumber
  String status
  Decimal discount
  Decimal totalAmount
  String notes
}

class OrderItem {
  UUID id
  Integer quantity
  Decimal price
}

class Category {
  UUID id
  JSONB name
  JSONB description
  String image
  Boolean isActive
  Integer sortOrder
}

class Product {
  UUID id
  JSONB name
  JSONB shortDescription
  JSONB description
  Decimal price
  Integer stock
  Integer minStock
  Boolean isActive
  Array<String> images
}

class ProductImage {
  UUID id
  String url
  String alt
  Integer order
}

' === RELATIONS ===

User --> "1" Cart
Cart --> "*" CartItem
CartItem --> "1" Product

User --> "*" Order
Order --> "*" OrderItem
OrderItem --> "1" Product

Product --> "*" ProductImage

Product --> "1" Category
Category --> "*" Product

```
