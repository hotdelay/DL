# Admin Panel Features - UI/UX Design V1

This document outlines the UI elements and UX flow for key features of the Administrator Panel for the Supermarket Grocery Delivery Platform. This panel is intended for users with the 'admin' role.

## 1. Admin Login Page

*   **UI Elements:**
    *   Page Title: "Platform Administration" or "Admin Login"
    *   Form Fields:
        *   Email or Username (Text input, required)
        *   Password (Password input, required)
    *   Buttons:
        *   "Login" (Submit button)
*   **UX Flow:**
    1.  Admin navigates to the dedicated admin portal URL.
    2.  Admin enters their credentials.
    3.  Admin clicks the "Login" button.
    4.  **System Validation:**
        *   Credentials are checked against the database.
        *   System verifies the user has the 'admin' role.
    5.  **On Success:**
        *   Admin session is created.
        *   Admin is redirected to the Admin Dashboard.
    6.  **On Error:**
        *   An error message is displayed (e.g., "Invalid credentials or access denied.").

## 2. Admin Dashboard

*   **UI Elements:**
    *   Header: Platform Name/Logo, Logged-in Admin Name, Logout Button.
    *   Main Navigation Sidebar:
        *   Dashboard
        *   User Management
        *   Store Management
        *   Product Category Management
        *   Order Management
        *   Delivery Personnel Management
        *   Platform Settings
        *   Reports & Analytics
        *   Notifications/Alerts
    *   Dashboard Content:
        *   **Key Metric Cards/Widgets:**
            *   Total Registered Users
            *   Total Active Stores
            *   Total Orders (e.g., last 30 days, all time)
            *   Total Revenue (e.g., last 30 days, all time)
            *   Pending Store Applications
            *   Open Support Tickets/Issues
        *   **Charts/Graphs:**
            *   User registration trends (line chart)
            *   Order volume trends (bar chart)
            *   Revenue trends (line chart)
        *   **Quick Access Lists:**
            *   List of recent pending store applications (with links to review).
            *   List of recently reported issues or high-priority orders.
*   **UX Flow:**
    1.  Admin lands on this page after successful login.
    2.  Admin gets a high-level overview of platform activity and key performance indicators.
    3.  Admin can use the sidebar to navigate to specific management sections.
    4.  Admin can click on items in quick access lists to directly address them.

## 3. User Management Section

*   **A. User List View:**
    *   **UI Elements:**
        *   Page Title: "Manage Users"
        *   Actions Bar:
            *   "Add New User" button (optional, admins might not create users directly, or only specific types)
            *   Search Bar: "Search by User ID, Name, Email"
            *   Filter Options (Dropdowns):
                *   Filter by Role (Customer, Store Staff, Delivery Personnel, Admin)
                *   Filter by Status (Active, Inactive, Suspended)
        *   User Table:
            *   Columns: User ID, Full Name, Email, Phone Number, Role, Status (e.g., Active, Suspended), Date Joined, Last Login.
            *   Actions per row: "View Details", "Edit", "Suspend/Activate".
        *   Pagination.
    *   **UX Flow:**
        1.  Admin navigates to User Management.
        2.  Views a paginated list of all users. Can search and filter.
        3.  Clicks "View Details" or "Edit" to manage a specific user.

*   **B. User Detail View / Edit Form:**
    *   **UI Elements:**
        *   Page Title: "User Details - [User Name]" or "Edit User - [User Name]"
        *   Display of all user information (from User model and related data).
        *   Editable Fields (depending on context):
            *   First Name, Last Name, Phone Number
            *   Role (Dropdown: Customer, Store Staff, Delivery Personnel, Admin) - Changing role has significant implications.
            *   Status (Dropdown: Active, Inactive, Suspended)
        *   Associated Data (Read-only or links):
            *   List of Orders (if customer)
            *   Associated Store (if store staff)
            *   Delivery History (if delivery personnel)
            *   Address book
        *   Actions:
            *   "Save Changes" button
            *   "Reset Password" button (sends a password reset link or allows admin to set a temporary password)
            *   "View Activity Log" (audit trail for this user)
    *   **UX Flow:**
        1.  Admin views all details of a selected user.
        2.  Admin can modify user information, role, or status.
        3.  Admin clicks "Save Changes". System validates and updates.
        4.  Admin can trigger a password reset for the user.

## 4. Store Management Section

*   **A. Store List View:**
    *   **UI Elements:**
        *   Page Title: "Manage Stores"
        *   Actions Bar:
            *   Search Bar: "Search by Store ID, Name, Owner Name/Email"
            *   Filter Options (Dropdowns):
                *   Filter by Status (Pending Approval, Approved/Active, Rejected, Suspended)
                *   Filter by Location/Region (if applicable)
        *   Store Table:
            *   Columns: Store ID, Store Name, Owner Name (User who registered store), Contact Email, Status, Date Registered, City/Location.
            *   Actions per row: "View Details", "Approve/Reject" (if pending), "Suspend/Activate".
        *   Pagination.
    *   **UX Flow:**
        1.  Admin navigates to Store Management.
        2.  Views a list of all stores. Can search and filter, especially for "Pending Approval" stores.
        3.  Clicks "View Details" or an action button for a specific store.

*   **B. Store Detail View / Edit Form:**
    *   **UI Elements:**
        *   Page Title: "Store Details - [Store Name]" or "Edit Store - [Store Name]"
        *   Display of all store information (from Store model and related data like owner User).
        *   Editable Fields: Store Name, Address, Phone Number, Operating Hours.
        *   Status Management: Dropdown/Buttons for "Approve Application", "Reject Application" (with reason), "Suspend Store", "Activate Store".
        *   Associated Data (Links or summaries):
            *   Store Staff list (Users with 'store_staff' role linked to this store)
            *   Product list for this store
            *   Order history for this store
        *   Actions:
            *   "Save Changes" button
            *   "Manage Store Staff" button (links to user management filtered for this store, or a dedicated staff assignment UI)
    *   **UX Flow:**
        1.  Admin views all details of a selected store.
        2.  **Approval Process:** If store is "Pending Approval", admin reviews details, verifies documents (if applicable, not covered in this UI design), and then "Approve" or "Reject" (providing a reason for rejection).
        3.  Admin can edit store operational details.
        4.  Admin can suspend a store for policy violations or activate a suspended store.
        5.  Changes are saved with audit logs.

## 5. Product Category Management (Global)

*   **UI Elements:**
    *   Page Title: "Manage Product Categories"
    *   Category Display:
        *   Tree view (preferred for hierarchical data) or nested list.
        *   Each category shows: Name, Number of Products (optional).
    *   Actions:
        *   "Add New Root Category" button
        *   For each category: "Add Subcategory", "Edit", "Delete" (with confirmation).
    *   **Add/Edit Category Form (Modal or inline):**
        *   Fields: Category Name (String), Parent Category (Dropdown, shows existing categories, null for root), Description (Text, optional).
        *   Actions: "Save Category", "Cancel".
*   **UX Flow:**
    1.  Admin navigates to Product Category Management.
    2.  Views the existing category structure.
    3.  **Adding Category:** Admin clicks "Add New Root Category" or "Add Subcategory" on an existing category. Fills form and saves.
    4.  **Editing Category:** Admin clicks "Edit" for a category. Modifies details and saves.
    5.  **Deleting Category:** Admin clicks "Delete". System checks if any products are associated. If not (or if a soft delete/re-categorization mechanism exists), deletion proceeds after confirmation.

## 6. Order Management Section (Global View & Escalations)

*   **UI Elements:**
    *   Page Title: "Manage Orders"
    *   Actions Bar:
        *   Search Bar: "Search by Order ID, Customer ID/Name, Store ID/Name, Product Name"
        *   Advanced Filter Options: By Status (all defined statuses), Date Range, Payment Status, Delivery Personnel.
    *   Order Table:
        *   Columns: Order ID, Customer Name, Store Name, Delivery Personnel Name (if assigned), Order Date, Total Amount, Payment Status, Order Status.
        *   Actions per row: "View Details".
        *   Pagination.
    *   Batch Actions (Optional): e.g., "Mark selected as Cancelled".
*   **UX Flow:**
    1.  Admin navigates to Order Management.
    2.  Views a comprehensive list of all orders on the platform. Uses advanced search/filters to find specific orders, especially those requiring intervention (e.g., "Payment Failed", "Delivery Issue").
    3.  Clicks "View Details" for an order.

*   **Order Detail View (Admin Perspective):**
    *   **UI Elements:**
        *   All information from customer and store order detail views.
        *   Additional Info: Payment Transaction ID/Details, Fraud Score (if applicable), Customer IP.
        *   Order Event Log/Audit Trail: Detailed history of all status changes, payments, refunds, assignments.
    *   **Actions:**
        *   "View Payment Transaction" (link to payment gateway details if available)
        *   "Initiate Refund" (full or partial, with reason; connects to payment gateway API)
        *   "Manually Update Status" (dropdown with all order statuses; requires reason/note for audit)
        *   "Re-assign Delivery" (if issue with current delivery person)
        *   "Contact Customer" / "Contact Store" / "Contact Delivery Person" (internal notes or direct contact info)
    *   **UX Flow:**
        1.  Admin views complete details of an order.
        2.  Investigates issues, fraud, or customer complaints.
        3.  Can perform high-level actions like initiating refunds or manually overriding order status if necessary, with all actions logged.

## 7. Delivery Personnel Management

*   **A. Personnel List View:**
    *   **UI Elements:**
        *   Page Title: "Manage Delivery Personnel"
        *   Actions Bar:
            *   "Review New Applications" button (filters list to pending approvals)
            *   Search Bar: "Search by Name, User ID, Phone"
            *   Filter Options: By Status (Pending Approval, Approved/Active, Suspended), Availability Status (Online, Offline, Busy).
        *   Personnel Table:
            *   Columns: User ID (linked to User Management), Name, Phone, Vehicle Details, Availability Status, Current Task ID (if any), Rating, Date Joined.
            *   Actions per row: "View Details", "Approve/Reject Application", "Suspend/Activate Account".
        *   Pagination.
    *   **UX Flow:**
        1.  Admin navigates to Delivery Personnel Management.
        2.  Views list of personnel. Can filter for new applications.

*   **B. Personnel Detail View / Edit Form:**
    *   **UI Elements:**
        *   Page Title: "Delivery Personnel Details - [Name]"
        *   All information from `User` and `DeliveryPersonnel` models.
        *   Editable Fields: Vehicle Details, potentially some user profile fields if not self-service.
        *   Status Management: "Approve Application", "Reject Application" (with reason), "Suspend Account", "Activate Account".
        *   Associated Data: Delivery History, Earnings Log, Current Assigned Tasks.
    *   **Actions:**
        *   "Save Changes"
        *   "View Performance Report"
    *   **UX Flow:**
        1.  Admin reviews applications, verifying documents/background checks (external process).
        2.  Approves or rejects applications.
        3.  Manages existing personnel accounts, including suspension for misconduct.

## 8. System Settings (Example)

*   **UI Elements:**
    *   Page Title: "Platform Settings"
    *   Forms organized into sections/tabs:
        *   **General:** Platform Name, Support Email, Default Currency (Dropdown), Timezone.
        *   **Financial:** Default Tax Rates (%), Delivery Fee Structure (e.g., flat rate, distance-based parameters, free delivery threshold).
        *   **Operational:** Business hours (if there are global cutoffs), Order auto-cancellation rules (e.g., for unpaid orders).
        *   **Notifications:** Admin email for critical alerts.
    *   Actions: "Save Settings" button for each section or a global save.
*   **UX Flow:**
    1.  Admin navigates to System Settings.
    2.  Modifies platform-wide configurations as needed.
    3.  Saves changes. These settings will affect various parts of the platform's operation. Changes should be audited.

This comprehensive Admin Panel design provides administrators with the tools to oversee and manage all aspects of the supermarket grocery delivery platform. Development should include robust permission checks and audit trails for all administrative actions.
