# Data Models

## User
- `id` (Primary Key, Auto-increment)
- `username` (String, Unique)
- `password` (String, Hashed)
- `email` (String, Unique)
- `phone_number` (String, Unique, Nullable)
- `first_name` (String)
- `last_name` (String)
- `role` (String, Enum: 'customer', 'store_staff', 'delivery_personnel', 'admin')
- `is_active` (Boolean, Default: True)
- `date_joined` (DateTime, Auto now add)
- `last_login` (DateTime, Nullable)

## Address
- `id` (Primary Key, Auto-increment)
- `user_id` (Foreign Key to User)
- `street_address` (String)
- `city` (String)
- `state_province` (String)
- `postal_code` (String)
- `country` (String)
- `address_type` (String, Enum: 'home', 'work', Default: 'home')
- `is_default_delivery` (Boolean, Default: False)

## Store
- `id` (Primary Key, Auto-increment)
- `name` (String)
- `address` (String) # Could be a ForeignKey to a new Address model specific to stores, or just a text field
- `phone_number` (String, Nullable)
- `operating_hours` (String, e.g., "Mon-Fri 9am-5pm")
- `is_active` (Boolean, Default: True)
- `created_at` (DateTime, Auto now add)
- `updated_at` (DateTime, Auto now)

## ProductCategory
- `id` (Primary Key, Auto-increment)
- `name` (String, Unique)
- `description` (Text, Nullable)
- `parent_category_id` (Foreign Key to ProductCategory, Nullable, for subcategories)
- `created_at` (DateTime, Auto now add)
- `updated_at` (DateTime, Auto now)

## Product
- `id` (Primary Key, Auto-increment)
- `store_id` (Foreign Key to Store)
- `category_id` (Foreign Key to ProductCategory)
- `name` (String)
- `description` (Text, Nullable)
- `price` (Decimal, e.g., 10.99)
- `sku` (String, Unique, Nullable) # Stock Keeping Unit
- `image_url` (String, Nullable)
- `stock_quantity` (Integer, Default: 0)
- `is_available` (Boolean, Default: True)
- `created_at` (DateTime, Auto now add)
- `updated_at` (DateTime, Auto now)

## Order
- `id` (Primary Key, Auto-increment)
- `user_id` (Foreign Key to User) # Customer who placed the order
- `store_id` (Foreign Key to Store) # Store from which the order is placed
- `delivery_address_id` (Foreign Key to Address)
- `delivery_personnel_id` (Foreign Key to User where role is 'delivery_personnel', Nullable)
- `total_amount` (Decimal)
- `status` (String, Enum: 'pending_payment', 'paid', 'preparing', 'ready_for_delivery', 'out_for_delivery', 'delivered', 'cancelled', 'refunded')
- `payment_method` (String, Nullable, e.g., 'credit_card', 'paypal')
- `payment_status` (String, Enum: 'pending', 'completed', 'failed', 'refunded')
- `notes` (Text, Nullable) # Customer notes
- `created_at` (DateTime, Auto now add)
- `updated_at` (DateTime, Auto now)

## OrderItem
- `id` (Primary Key, Auto-increment)
- `order_id` (Foreign Key to Order)
- `product_id` (Foreign Key to Product)
- `quantity` (Integer)
- `price_at_purchase` (Decimal) # Price of the product when the order was placed
- `created_at` (DateTime, Auto now add)

## DeliveryPersonnel
- `id` (Primary Key, Auto-increment) # This could simply be the User.id
- `user_id` (Foreign Key to User, Unique, where role is 'delivery_personnel')
- `vehicle_details` (String, Nullable, e.g., "Bike - XYZ 123")
- `current_location_lat` (Decimal, Nullable)
- `current_location_long` (Decimal, Nullable)
- `availability_status` (String, Enum: 'available', 'on_delivery', 'offline', Default: 'offline')
- `rating` (Decimal, Nullable, e.g., 4.5)
- `created_at` (DateTime, Auto now add)
- `updated_at` (DateTime, Auto now)
