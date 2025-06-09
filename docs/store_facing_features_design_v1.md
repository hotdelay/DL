# Store Facing Features - UI/UX Design V1

This document outlines the UI elements and UX flow for key store-facing features of the Supermarket Grocery Delivery Platform, intended for use by store staff.

## 1. Store Staff Login Page

*   **UI Elements:**
    *   Page Title: "Store Management Portal" or "[Store Name] Staff Login"
    *   Form Fields:
        *   Email or Username (Text input, required)
        *   Password (Password input, required)
    *   Buttons:
        *   "Login" (Submit button)
    *   Links:
        *   "Forgot Password?" (Link to a password reset flow specific to staff)
*   **UX Flow:**
    1.  Store staff navigates to the dedicated store portal login page.
    2.  Staff enters their assigned email/username and password.
    3.  Staff clicks the "Login" button.
    4.  **System Validation:**
        *   Credentials are checked against the database.
        *   System verifies the user has a 'store_staff' (or similar) role and is associated with a specific store.
    5.  **On Success:**
        *   User session is created.
        *   User is redirected to the Store Dashboard.
    6.  **On Error:**
        *   An error message is displayed (e.g., "Invalid credentials or access denied.").

## 2. Store Dashboard/Homepage

*   **UI Elements:**
    *   Header: Store Name, Logged-in Staff Member Name, Logout Button.
    *   Main Navigation Menu (Sidebar or Top Bar):
        *   Dashboard
        *   Product Management
        *   Order Management
        *   Store Settings (Optional)
        *   Reports (Optional)
    *   Dashboard Content:
        *   **Overview/Summary Cards:**
            *   "New/Pending Orders": Count of orders needing attention.
            *   "Orders in Progress": Count of orders being prepared.
            *   "Ready for Pickup/Delivery": Count of orders ready.
            *   "Today's Sales": Total revenue for the current day (optional).
            *   "Low Stock Alerts": Notifications for products running low (optional).
        *   **Quick Links:**
            *   "View New Orders"
            *   "Add New Product"
            *   "Manage Inventory"
        *   **Recent Activity Feed (Optional):**
            *   List of recent important events (e.g., "New order #12345 received", "Product XYZ updated").
*   **UX Flow:**
    1.  Staff lands on this page after successful login.
    2.  Staff gets a quick overview of the store's current status and key metrics.
    3.  Staff can use the main navigation menu to access different management sections.
    4.  Staff can click on quick links or summary cards to jump to specific tasks (e.g., clicking "New/Pending Orders" card takes to Order Management filtered by new orders).

## 3. Product Management Page

*   **UI Elements:**
    *   Page Title: "Manage Products"
    *   Actions Bar:
        *   "Add New Product" button
        *   Search Bar: "Search by product name, SKU, category"
        *   Filter Options (Dropdowns):
            *   Filter by Category
            *   Filter by Status (e.g., Available, Unavailable/Archived)
    *   Product Table/List:
        *   Columns:
            *   Image Thumbnail
            *   Product Name
            *   SKU
            *   Category
            *   Price
            *   Stock Quantity
            *   Status (e.g., "Available", "Unavailable")
            *   Actions (Buttons/Icons for each product):
                *   "Edit"
                *   "Toggle Availability" (changes status between Available/Unavailable)
                *   "Delete" (with confirmation, potentially soft delete)
    *   Pagination if the product list is long.

*   **Add/Edit Product Form (Modal or Separate Page)**
    *   **UI Elements:**
        *   Form Title: "Add New Product" or "Edit [Product Name]"
        *   Fields:
            *   Product Name (Text input, required)
            *   Description (Text area/Rich text editor, optional)
            *   SKU (Stock Keeping Unit) (Text input, unique within store, optional)
            *   Category (Dropdown, populated from ProductCategory model, required)
            *   Price (Decimal input, required)
            *   Stock Quantity (Integer input, required, default 0)
            *   Unit of Measure (e.g., "each", "kg", "pack of 6") (Text input or dropdown, optional)
            *   Image Uploads (Allow multiple images, primary image selection)
            *   Is Available (Checkbox, default True)
    *   **Actions:**
        *   "Save Product" / "Update Product" button
        *   "Cancel" button

*   **UX Flow:**
    *   **Viewing Products:**
        1.  Staff navigates to the Product Management page.
        2.  A list/table of all products for their store is displayed.
        3.  Staff can search, filter, and sort the product list.
    *   **Adding a New Product:**
        1.  Staff clicks the "Add New Product" button.
        2.  The Add Product form (modal or new page) appears.
        3.  Staff fills in the product details and uploads images.
        4.  Staff clicks "Save Product".
        5.  **System Validation:** Required fields, valid price/stock, unique SKU (if provided).
        6.  On success, the product is created, and the list is updated. A success message is shown.
        7.  On error, validation messages are displayed on the form.
    *   **Editing an Existing Product:**
        1.  Staff clicks the "Edit" button for a specific product in the list.
        2.  The Edit Product form appears, pre-filled with the product's current details.
        3.  Staff modifies the details as needed.
        4.  Staff clicks "Update Product".
        5.  On success, changes are saved, and the list is updated. A success message is shown.
    *   **Toggling Availability:**
        1.  Staff clicks the "Toggle Availability" button for a product.
        2.  The product's status (e.g., from "Available" to "Unavailable" or vice-versa) is updated in the system and visually in the list. This directly affects customer visibility.
    *   **Deleting a Product:**
        1.  Staff clicks the "Delete" button for a product.
        2.  A confirmation dialog appears ("Are you sure you want to delete [Product Name]?").
        3.  On confirmation, the product is deleted (or marked as archived). The list updates.

## 4. Order Management Page

*   **UI Elements:**
    *   Page Title: "Manage Orders"
    *   Actions Bar:
        *   Filter Options (Dropdowns/Date Pickers):
            *   Filter by Status (e.g., "All", "Pending", "Preparing", "Ready for Delivery", "Out for Delivery", "Delivered", "Cancelled")
            *   Filter by Date Range (Order date)
            *   Search Bar: "Search by Order ID, Customer Name/ID"
    *   Order Table/List:
        *   Columns:
            *   Order ID
            *   Customer Name / User ID
            *   Order Date & Time
            *   Total Amount
            *   Payment Status (e.g. "Paid", "Pending")
            *   Current Order Status
            *   Actions (Buttons/Icons for each order):
                *   "View Details"
    *   Pagination if the order list is long.
    *   Real-time refresh or notification for new orders (desirable).

*   **Order Detail View (Modal or Separate Page)**
    *   **UI Elements:**
        *   View Title: "Order Details - #[Order ID]"
        *   Customer Information:
            *   Name, Contact (Phone/Email)
        *   Delivery Information:
            *   Delivery Address
            *   Delivery Time Slot (if applicable)
            *   Customer Notes
        *   Order Items:
            *   Table: Product Name, SKU, Quantity, Price at Purchase, Item Subtotal
        *   Order Summary:
            *   Subtotal, Delivery Fee, Taxes, Total Amount
        *   Payment Information:
            *   Payment Method, Payment Status
        *   Order History/Log (Optional): Timestamped list of status changes.
    *   **Actions:**
        *   "Update Order Status" (Dropdown or set of buttons):
            *   Options: "Acknowledge Order", "Start Preparing", "Mark as Ready for Delivery/Pickup", "Assign to Delivery Personnel" (if applicable), "Mark as Out for Delivery", "Mark as Delivered", "Cancel Order" (with reason, if applicable).
        *   "Print Order / Packing Slip" button
        *   "Contact Customer" button (Optional, might integrate with an internal messaging system or reveal contact info)

*   **UX Flow:**
    1.  Staff navigates to the Order Management page. New orders might be highlighted.
    2.  A list/table of orders is displayed, typically sorted by newest first.
    3.  Staff can filter orders by status, date, or search for specific orders.
    4.  Staff clicks "View Details" for an order to see the full information.
    5.  **Processing an Order:**
        *   On the Order Detail view, staff reviews the order items and customer details.
        *   Staff uses the "Update Order Status" action to reflect the order's progression (e.g., from "Pending" to "Preparing").
        *   The system records the status change and timestamp.
        *   Customer might receive notifications based on status updates (e.g., "Your order is now being prepared").
        *   Staff can print a packing slip or order summary.
    6.  This process continues until the order is "Delivered" or "Cancelled".

## 5. (Optional) Store Settings Page

*   **UI Elements:**
    *   Page Title: "Store Settings"
    *   Form Fields (depending on what's configurable by store staff vs. platform admin):
        *   Store Name (Text input, may be read-only or require admin approval for changes)
        *   Store Address (Text area, may be read-only)
        *   Contact Phone Number (Text input)
        *   Contact Email (Text input)
        *   Operating Hours (Series of inputs for each day, e.g., Mon: 9:00 AM - 7:00 PM, Tue: ...)
        *   Delivery Radius/Zones (If configurable by store, might be a map interface or zip code list)
        *   Minimum Order Amount (Decimal input)
        *   Estimated Delivery Time (e.g., "30-45 minutes") (Text input or dropdown)
    *   Actions:
        *   "Save Settings" button
*   **UX Flow:**
    1.  Staff (likely a store manager or admin staff) navigates to the Store Settings page.
    2.  Staff views current store operational details.
    3.  Staff modifies editable fields as needed (e.g., updates operating hours for a holiday, changes contact phone).
    4.  Staff clicks "Save Settings".
    5.  **System Validation:** Ensure data formats are correct (e.g., valid times, phone numbers).
    6.  On success, settings are updated. These changes would reflect on the customer-facing side (e.g., updated store hours).
    7.  On error, validation messages are displayed.

This design provides a foundational structure for store staff to manage their operations on the platform effectively. Each action taken by staff should trigger appropriate backend API calls and database updates.
