# Delivery Logistics Features - UI/UX Design V1

This document outlines the UI elements and UX flow for key delivery logistics features of the Supermarket Grocery Delivery Platform, covering interfaces for delivery personnel and administrative/store staff.

## 1. Delivery Personnel - Mobile App/Interface

This interface is envisioned primarily as a mobile application for users with the 'delivery_personnel' role.

*   **A. Login:**
    *   **UI Elements:**
        *   App Logo/Name
        *   Fields: Email/Username, Password
        *   "Login" button
        *   "Forgot Password?" link
    *   **UX Flow:**
        1.  Delivery personnel opens the app.
        2.  Enters their credentials.
        3.  Taps "Login".
        4.  System validates credentials and role ('delivery_personnel').
        5.  On success, redirects to the Dashboard/Task List. On error, shows an error message.

*   **B. Dashboard/Task List:**
    *   **UI Elements:**
        *   Header: "Your Deliveries" or "Tasks", User Name.
        *   Availability Toggle: "Go Online/Available", "Go Busy/Offline".
        *   Task List:
            *   Each task item (card or list item):
                *   Order ID
                *   Store Name & Pickup Address
                *   Customer Name & Delivery Address
                *   Estimated Pickup/Delivery Time Window
                *   Order Status (e.g., "Assigned", "At Store", "Picked Up")
                *   Indication of urgency or proximity (e.g., color-coding, icons).
        *   Sorting/Filtering options (Optional): Sort by time, distance.
    *   **UX Flow:**
        1.  After login, personnel sees this screen.
        2.  Personnel sets their status using the availability toggle. Only 'Online/Available' personnel can be assigned new tasks (typically).
        3.  New tasks assigned by admin/store appear in the list (potentially with a notification).
        4.  Tasks are sorted, often by urgency or optimal routing.
        5.  Personnel taps on a task to view its details and begin the process.

*   **C. Task Detail View:**
    *   **UI Elements:**
        *   Header: "Order #[Order ID]"
        *   **Pickup Information:**
            *   Store Name, Full Address, Contact Number.
            *   Button: "Navigate to Store" (integrates with device's map app).
            *   List of items/bags to pick up (brief summary, e.g., "3 bags, 1 frozen item").
        *   **Delivery Information:**
            *   Customer Name, Full Address, Contact Number.
            *   Button: "Navigate to Customer" (integrates with device's map app).
            *   Delivery Notes (from customer or store).
        *   **Action Buttons (state-dependent, only relevant buttons shown):**
            *   "Accept Task" / "Reject Task" (if assignments are provisional)
            *   "Arrived at Store" (optional, for more granular tracking)
            *   "Confirm Pickup" (after collecting items from the store)
            *   "Confirm Delivery" (after handing over items to the customer)
                *   May trigger: Signature capture screen, Photo capture (e.g., of items at doorstep).
            *   "Report Issue" / "Unable to Deliver"
    *   **UX Flow:**
        1.  Personnel views task details.
        2.  **Pickup Process:**
            *   Taps "Navigate to Store" to get directions.
            *   Upon arrival/collection, taps "Confirm Pickup".
                *   System updates order status (e.g., to 'Out for Delivery').
                *   Customer and store might be notified.
        3.  **Delivery Process:**
            *   Taps "Navigate to Customer" to get directions.
            *   Upon arrival, attempts delivery.
            *   Taps "Confirm Delivery".
                *   If required, captures signature or photo proof.
                *   System updates order status to 'Delivered'.
                *   Customer and store are notified. Task is removed from active list or moved to a completed section.
        4.  **Issue Reporting:**
            *   If an issue occurs (e.g., customer not available, wrong address, item damaged), personnel taps "Report Issue".
            *   A form appears to select issue type and add notes.
            *   This flags the order for admin/store attention.

*   **D. Profile/Settings:**
    *   **UI Elements:**
        *   User's Name, Photo (optional).
        *   Editable Fields (if allowed):
            *   Phone Number
            *   Vehicle Details (Make, Model, License Plate)
        *   Read-only Information:
            *   Email/Username
        *   Links:
            *   "Delivery History" (list of completed deliveries)
            *   "Earnings Summary" (if applicable, showing payments per delivery/period)
            *   "Help/Support"
            *   "Logout"
    *   **UX Flow:**
        1.  Personnel accesses this section from a menu.
        2.  Can view and update their profile information as permitted.
        3.  Can view past deliveries and earnings.

## 2. Admin/Store Staff - Order Assignment Interface

This interface would typically be part of the existing Admin Panel or Store Management Panel.

*   **A. View 'Ready for Delivery' Orders:**
    *   **UI Elements (within Order Management section):**
        *   A dedicated tab or filter: "Ready for Delivery".
        *   Table/List of Orders:
            *   Order ID
            *   Store Name (if admin views multiple stores)
            *   Customer Name & Full Delivery Address (Map snippet preview optional)
            *   Order Placed Time
            *   Promised Delivery Window (if any)
            *   Order Value/Size (to help assess vehicle needs)
            *   Current Status (should be 'Ready for Delivery' or similar)
            *   "Assign Delivery" button/dropdown for each unassigned order.
            *   Column showing "Assigned To" (empty or shows delivery person name).
    *   **UX Flow:**
        1.  Admin or store staff navigates to this view.
        2.  They see a list of orders that have been prepared by the store and are awaiting delivery assignment.

*   **B. Assign to Delivery Personnel:**
    *   **UI Elements (Modal or slide-in panel triggered by "Assign Delivery" button):**
        *   Title: "Assign Order #[Order ID] to Delivery Personnel"
        *   List of Available Delivery Personnel:
            *   Personnel Name
            *   Current Status ('Online/Available')
            *   Current Location/Zone (if available via GPS, or last known)
            *   Current Load/Number of Active Deliveries (to avoid overloading)
            *   Vehicle Type (if relevant for order size)
            *   Rating (optional)
        *   Search/Filter for delivery personnel (if list is long).
        *   "Assign" button next to each available person OR radio buttons and a main "Confirm Assignment" button.
    *   **UX Flow:**
        1.  Admin/staff clicks "Assign Delivery" for an order.
        2.  The assignment modal appears, showing suitable and available delivery personnel.
        3.  Admin/staff reviews the list, considering factors like proximity, current load, etc.
        4.  Admin/staff selects a delivery person and confirms the assignment.
        5.  **System Action:**
            *   The order is associated with the chosen delivery person.
            *   The order status might update (e.g., to 'Waiting for Pickup by Delivery').
            *   The assigned order appears in the delivery person's mobile app task list.
            *   The "Assigned To" column in the order list updates.

## 3. (Conceptual) Real-time Tracking View (Admin Panel)

This is a more advanced feature, typically found in an Admin or Logistics Management Panel.

*   **UI Elements:**
    *   Page Title: "Live Delivery Map" or "Driver Tracking"
    *   Main Area:
        *   Interactive Map (e.g., Google Maps, Mapbox integration).
        *   Markers representing active delivery personnel.
            *   Marker color might indicate status (e.g., green for available, blue for on delivery, red for issue).
            *   Clicking a marker shows: Personnel Name, Current Task (Order ID), Phone.
    *   Sidebar/Filters:
        *   List of all active delivery personnel. Clicking a name centers map on them.
        *   Filter by status (Available, On Delivery, Offline with recent activity).
        *   Search for a specific delivery person.
        *   Option to view routes taken (if history is logged).
    *   Event Log (Optional): Real-time feed of delivery events (pickup confirmations, delivery confirmations, reported issues).
*   **UX Flow:**
    1.  Admin/Logistics Manager opens this page.
    2.  The map displays the current (or last known) locations of all active delivery personnel who have their availability status set to 'Online' or are actively on a task.
    3.  Admin can click on personnel markers to get more details about their current assignment.
    4.  Admin can use filters to focus on specific personnel or groups.
    5.  This view provides an operational overview for monitoring efficiency, resolving issues, and managing the delivery fleet.

These descriptions should provide a solid basis for designing the necessary interfaces and backend logic to support the platform's delivery operations.Okay, I have created the `delivery_logistics_features_design_v1.md` file in the `docs/` directory and populated it with the UI/UX flow descriptions for the delivery logistics features.
