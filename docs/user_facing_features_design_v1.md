# User Facing Features - UI/UX Design V1

This document outlines the UI elements and UX flow for key customer-facing features of the Supermarket Grocery Delivery Platform.

## 1. User Registration Page

*   **UI Elements:**
    *   Page Title: "Create Your Account"
    *   Form Fields:
        *   Username (Text input, required)
        *   Email (Email input, required)
        *   Password (Password input, required)
        *   Confirm Password (Password input, required)
        *   First Name (Text input, required)
        *   Last Name (Text input, required)
        *   Phone Number (Text input, optional)
    *   Buttons:
        *   "Register" or "Sign Up" (Submit button)
    *   Links:
        *   "Already have an account? Login" (Link to Login Page)
*   **UX Flow:**
    1.  User navigates to the registration page.
    2.  User fills in the required (and optional) fields.
    3.  User clicks the "Register" button.
    4.  **System Validation:**
        *   All required fields are filled.
        *   Email format is valid.
        *   Username is unique.
        *   Email is unique.
        *   Password meets complexity requirements (e.g., min 8 characters).
        *   Password and Confirm Password fields match.
    5.  **On Success:**
        *   User account is created in the system (role defaults to 'customer').
        *   User is redirected to the Login Page or directly to the main Dashboard/Store Listing Page (and automatically logged in).
        *   A success message might be displayed (e.g., "Registration successful! Please login.").
    6.  **On Error:**
        *   Error messages are displayed next to the respective fields or as a summary at the top of the form (e.g., "Username already taken", "Passwords do not match").

## 2. User Login Page

*   **UI Elements:**
    *   Page Title: "Login to Your Account"
    *   Form Fields:
        *   Email or Username (Text input, required)
        *   Password (Password input, required)
    *   Buttons:
        *   "Login" (Submit button)
    *   Links:
        *   "Don't have an account? Register" (Link to Registration Page)
        *   "Forgot Password?" (Link to a password reset flow - to be detailed later)
*   **UX Flow:**
    1.  User navigates to the login page.
    2.  User enters their email/username and password.
    3.  User clicks the "Login" button.
    4.  **System Validation:**
        *   Credentials are checked against the database.
    5.  **On Success:**
        *   User session is created.
        *   User is redirected to the main Dashboard or Store Listing Page.
    6.  **On Error:**
        *   An error message is displayed (e.g., "Invalid email/username or password.").

## 3. Store Listing/Selection Page

*   **UI Elements:**
    *   Page Title: "Available Stores" or "Choose a Supermarket"
    *   Search Bar: "Search for stores by name or location"
    *   Filter Options (Optional, could be a dropdown or sidebar):
        *   Filter by location/area (if multiple service areas are supported)
        *   Filter by cuisine/type (if applicable, e.g. "Organic", "International")
    *   Store Display:
        *   Grid or List view.
        *   Each store item:
            *   Store Logo/Image
            *   Store Name
            *   Brief description (e.g., "Fresh groceries and household essentials")
            *   Location/Address snippet
            *   Operating Hours / Open/Closed status indicator
            *   Delivery estimate (optional)
*   **UX Flow:**
    1.  User lands on this page after login or by navigating from another part of the app.
    2.  A list of available stores is displayed.
    3.  User can scroll through the list.
    4.  User can use the search bar to find specific stores by name.
    5.  User can use filter options to narrow down the list (if implemented).
    6.  User clicks on a store card/listing to view its products.
    7.  Redirected to the Product Listing Page for the selected store.

## 4. Product Listing Page (within a store)

*   **UI Elements:**
    *   Header: Store Name, Store Logo
    *   Navigation: Breadcrumbs (e.g., Home > Stores > [Store Name])
    *   Sidebar/Top Bar (for categories):
        *   List of Product Categories (e.g., "Fruits & Vegetables", "Dairy & Eggs", "Bakery")
        *   Sub-categories might be expandable.
    *   Main Content Area:
        *   Search Bar: "Search for products in [Store Name]"
        *   Filter Options (Optional):
            *   Sort by: Price (low to high, high to low), Popularity, Name
            *   Filter by price range
        *   Product Display:
            *   Grid or List view.
            *   Each product item:
                *   Product Image
                *   Product Name
                *   Price (e.g., $2.99)
                *   Unit (e.g., /lb, /each) - if applicable
                *   "Add to Cart" button (possibly with a quick quantity +/-)
                *   Short description (optional)
*   **UX Flow:**
    1.  User arrives after selecting a store.
    2.  Products from the selected store are displayed, possibly showing a default category or all products.
    3.  User can click on a category in the sidebar/top bar to filter products by that category.
    4.  User can use the search bar to find specific products within the current store.
    5.  User can use filter/sort options to refine the product list.
    6.  User can click on a product image or name to navigate to the Product Detail Page.
    7.  User can click the "Add to Cart" button directly from the listing.
        *   Feedback is provided (e.g., item added to cart, cart icon updates with item count).

## 5. Product Detail Page

*   **UI Elements:**
    *   Header: Store Name, Link back to Product Listing / Store
    *   Navigation: Breadcrumbs (e.g., Home > Stores > [Store Name] > [Category] > [Product Name])
    *   Product Information:
        *   Product Name (Large heading)
        *   Image Gallery/Carousel (Multiple product images if available)
        *   Full Description (Detailed text about the product)
        *   Price (Clearly displayed, e.g., "$2.99 /lb")
        *   Unit of Measure (e.g., per item, per kg, per liter)
        *   Stock Status (e.g., "In Stock", "Out of Stock", "Limited Stock")
        *   Quantity Selector (Input field with +/- buttons, default to 1)
    *   Actions:
        *   "Add to Cart" button
    *   Related Products / Customers Also Bought (Optional section)
*   **UX Flow:**
    1.  User navigates from the Product Listing Page by clicking on a product.
    2.  All details of the selected product are displayed.
    3.  User can view different images in the carousel.
    4.  User can adjust the desired quantity using the quantity selector.
    5.  User clicks the "Add to Cart" button.
        *   The selected quantity of the product is added to the shopping cart.
        *   Visual feedback is provided (e.g., button changes to "Added ✓", cart icon updates).
        *   User might be shown a mini-cart dropdown or a notification.

## 6. Shopping Cart Page

*   **UI Elements:**
    *   Page Title: "Your Shopping Cart" or "Review Your Order"
    *   Cart Items List:
        *   For each item:
            *   Product Image
            *   Product Name (Link to Product Detail Page)
            *   Unit Price
            *   Quantity (Editable input field or +/- buttons)
            *   Subtotal (Price * Quantity)
            *   "Remove" button/icon
    *   Order Summary Section:
        *   Subtotal (sum of all item subtotals)
        *   Estimated Taxes (if applicable)
        *   Delivery Fee (if applicable, clearly stated)
        *   Discount/Promo Code field (Optional)
        *   Total Amount
    *   Actions:
        *   "Proceed to Checkout" button
        *   "Continue Shopping" link (navigates back to the last viewed store or store listing)
        *   "Clear Cart" button (Optional)
*   **UX Flow:**
    1.  User navigates to the cart by clicking a cart icon (usually in the header) or after adding an item.
    2.  All items added to the cart are displayed with their details.
    3.  User can change the quantity of any item. The item subtotal and overall cart total update automatically.
    4.  User can remove an item from the cart. The item is removed, and totals are updated.
    5.  User can apply a promo code (if feature exists).
    6.  User clicks "Proceed to Checkout" to move to the next step.
    7.  User clicks "Continue Shopping" to go back to browsing products.

## 7. Checkout Process

This could be a single scrollable page or a multi-step wizard.

*   **Step 1: Delivery Address**
    *   **UI Elements:**
        *   Section Title: "Delivery Address"
        *   Option to select from saved addresses (if user is logged in and has addresses).
            *   Display saved addresses as cards or a list with radio buttons.
            *   Each address shows: Street, City, Postal Code.
            *   "Edit" or "Delete" option for saved addresses.
        *   Button/Link: "Add New Address"
        *   New Address Form (appears if "Add New Address" is clicked or no addresses are saved):
            *   Street Address (Text input, required)
            *   Apartment, Suite, etc. (Text input, optional)
            *   City (Text input, required)
            *   State/Province (Text input or Dropdown, required)
            *   Postal Code (Text input, required)
            *   Country (Text input or Dropdown, required)
            *   Save this address for future use (Checkbox)
        *   Button: "Continue to Delivery Time" or "Continue to Payment"
    *   **UX Flow:**
        *   User selects an existing address or fills out the new address form.
        *   If adding a new address, system validates the input.
        *   User clicks "Continue".

*   **Step 2: Delivery Time Slot Selection (Optional)**
    *   **UI Elements:**
        *   Section Title: "Choose Delivery Time"
        *   Display available dates and time slots (e.g., "Today, 2 PM - 4 PM", "Tomorrow, 10 AM - 12 PM").
        *   Radio buttons or selectable cards for time slots.
        *   Button: "Continue to Payment"
    *   **UX Flow:**
        *   User selects a preferred delivery time slot from the available options.
        *   User clicks "Continue".

*   **Step 3: Payment Method Selection**
    *   **UI Elements:**
        *   Section Title: "Payment Method"
        *   List of available payment options (e.g., "Credit/Debit Card", "PayPal", "Cash on Delivery" - if supported).
            *   Radio buttons to select an option.
        *   If "Credit/Debit Card" is selected:
            *   Card Number (Input)
            *   Expiry Date (MM/YY) (Input)
            *   CVV/CVC (Input)
            *   Name on Card (Input)
            *   "Save this card for future payments" (Checkbox, if PCI compliance is handled)
        *   Button: "Review Order" or "Continue to Summary"
    *   **UX Flow:**
        *   User selects a payment method.
        *   If applicable, user enters payment details.
        *   System validates card details (format, not actual payment yet).

*   **Step 4: Order Summary & Confirmation**
    *   **UI Elements:**
        *   Section Title: "Review Your Order"
        *   Selected Delivery Address
        *   Selected Delivery Time (if applicable)
        *   Selected Payment Method (e.g., "Visa **** 1234")
        *   List of items in cart (Product Name, Quantity, Price, Subtotal for each)
        *   Order Totals: Subtotal, Delivery Fee, Taxes, Total Amount.
        *   Notes/Instructions for store/delivery (Text area, optional)
    *   **Actions:**
        *   "Confirm & Pay" or "Place Order" button
        *   Link/Button: "Back to Cart" or "Edit Order"
*   **UX Flow:**
    1.  User reviews all order details: items, address, payment, totals.
    2.  User can add any special instructions.
    3.  User clicks "Confirm & Pay".
    4.  **System Processing:**
        *   Payment is processed via the selected payment gateway.
        *   Order is created in the system with 'pending_payment' or 'paid' status.
        *   Inventory is updated (ideally).
    5.  **On Payment Success:**
        *   User is redirected to the Order Confirmation Page.
    6.  **On Payment Failure:**
        *   An error message is displayed (e.g., "Payment failed. Please try again or use a different card.").
        *   User remains on the checkout page to correct details or try again.

## 8. Order Confirmation Page

*   **UI Elements:**
    *   Page Title: "Thank You for Your Order!" or "Order Placed Successfully!"
    *   Order Confirmation Message: e.g., "Your order #[Order ID] has been placed."
    *   Order ID: Clearly displayed.
    *   Summary of the Order:
        *   Items ordered (brief list)
        *   Total amount paid
        *   Delivery address
        *   Estimated delivery date/time slot.
    *   Next Steps Information (optional): e.g., "You will receive an email confirmation shortly."
    *   Actions:
        *   "Track Your Order" (if real-time tracking is a feature, link to Order Details in Order History)
        *   "View Order History" (Link to Order History Page)
        *   "Continue Shopping" (Link back to Store Listing or homepage)
*   **UX Flow:**
    1.  User is redirected here after successful payment and order creation.
    2.  User sees the confirmation details and order ID.
    3.  User can choose to view their order history or continue shopping.

## 9. Order History Page

*   **UI Elements:**
    *   Page Title: "My Orders"
    *   List/Table of Past Orders:
        *   Each order item:
            *   Order ID (Link to Order Detail Page)
            *   Date Placed
            *   Store Name (if orders can be from multiple stores)
            *   Total Amount
            *   Status (e.g., "Delivered", "Processing", "Cancelled", "Out for Delivery")
            *   "View Details" button/link
            *   "Reorder" button (Optional, adds items from that order to cart)
    *   Filters (Optional): Filter by status, date range.
    *   Pagination if the list is long.
*   **UX Flow:**
    1.  User navigates to this page from their account menu or order confirmation.
    2.  A list of their past and current orders is displayed.
    3.  User can click on an Order ID or "View Details" to see the full details of a specific order (navigates to an Order Detail page, similar to confirmation but with more details like individual item breakdown if not immediately visible).

## 10. User Profile Page

*   **UI Elements:**
    *   Page Title: "My Profile" or "Account Settings"
    *   Tabs or Sections for different settings:
        *   **Personal Information:**
            *   Fields (editable): First Name, Last Name, Phone Number, Email (display only or link to change email process)
            *   Username (display only)
            *   Button: "Save Changes"
        *   **Manage Addresses:**
            *   List of saved delivery addresses (similar to checkout address selection).
            *   Option to Add New Address.
            *   Option to Edit/Delete existing addresses.
            *   Option to set a default address.
        *   **Change Password:**
            *   Field: Current Password
            *   Field: New Password
            *   Field: Confirm New Password
            *   Button: "Update Password"
        *   **(Optional) Payment Methods:**
            *   List saved payment methods (e.g., last 4 digits of card).
            *   Option to delete saved methods.
            *   Option to add new (securely).
*   **UX Flow:**
    *   **Personal Information:**
        1.  User navigates to the profile page.
        2.  User modifies their first name, last name, or phone number.
        3.  User clicks "Save Changes".
        4.  System validates and updates the information. Success/error message shown.
    *   **Manage Addresses:**
        1.  User views their list of saved addresses.
        2.  User can add a new address (form similar to checkout).
        3.  User can edit or delete an existing address.
        4.  User can set one address as their default.
    *   **Change Password:**
        1.  User fills in current password, new password, and confirms new password.
        2.  User clicks "Update Password".
        3.  System validates:
            *   Current password is correct.
            *   New password meets complexity requirements.
            *   New password and confirmation match.
        4.  On success, password is updated. User might be logged out and asked to log in again.
        5.  On error, messages are displayed.
