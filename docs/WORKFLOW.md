# RANYOR - Application Workflow

This document outlines the end-to-end workflows of the RANYOR rental marketplace application, covering user lifecycle, item management, and the secure rental process.

---

## 📸 Workflow Diagrams
<!-- [ADD IMAGE: Full Application Workflow Diagram] -->

---

## 1. User Authentication Workflow

The authentication flow ensures secure access via JWT and OTP verification.

*   **Registration**:
    1.  User enters Name, Email, Phone, and Password.
    2.  Selects Account Type (Individual or Business).
    3.  Backend sends OTP to Email/SMS.
    4.  User enters OTP to verify and activate account.
*   **Login**:
    1.  **Email/Phone Login**: User enters credentials and backend validates via JWT.
    2.  **Google Login**: Single-tap social authentication via Firebase/Google Sign-In.
    3.  App stores token securely and navigates to Main Stack.
*   **Forgot Password**:
    1.  User initiates "Forgot Password" with Email/Phone.
    2.  OTP is sent for verification.
    3.  User enters OTP and provides a new password.
*   **Account Management**:
    1.  **Update Profile**: Change Name, Avatar, Location, and Business specific details.
    2.  **Security**: Change password or manage notification preferences.
    3.  **Delete Account**: Users can request account deletion (Soft delete by default, Hard delete by admin).

---

## 2. Lender (Owner) Workflow

Lenders can list items, manage availability, and handle booking requests.

### ➕ Add Item Workflow
<!-- [ADD IMAGE: Add Item Screen Sequence] -->
1.  **Basic Info**: Select Category, Sub-category, Brand, and Model.
2.  **Listing Details**: Title, Description, Quantity, and Pricing (Hourly/Daily).
3.  **Photos**: Upload high-quality images (compressed locally before upload).
4.  **Location**: Set pickup and drop-off locations (Map integration).
5.  **Availability**: Set patterns (Weekdays/Weekends) and manual date exclusions.

### 🗓️ Set Availability
1.  Owners can define "Patterns" (e.g., Only available on Weekends).
2.  Manual "Excluded Dates" can be added for specific days the item is unavailable.
3.  Manual "Included Dates" can override patterns for specific days.

### 📝 Edit Listing
1.  Access from My Listings -> Edit.
2.  Update any field, status (Active/Inactive), or availability rules.

### ✅ Accept/Reject Booking
1.  Notification received for a new booking request.
2.  Lender views requester profile and booking dates.
3.  Clicks **Accept** (moves to Confirmation) or **Reject** (notifies Renter).

---

## 3. Renter Workflow

Renters discover items and manage their rentals.

### 🔍 Discovery
1.  **Browse**: Explore categories on the Home screen.
2.  **Search**: Use keywords or location-based filtering to find items nearby.
3.  **Item Details**: View full info, images, owner ratings, and dynamic price calculation based on selected dates.

### 📅 Create Booking
1.  **Select Dates**: Use the interactive calendar (checks owner availability).
2.  **Checkout**: Review total price, security deposit (if any), and notes.
3.  **Payment/Confirm**: Confirm the booking request.
4.  **Wait for Approval**: Booking status is "Pending" until Lender accepts.

### 📋 See Listing / My Rentals
1.  View all ongoing, upcoming, and past rentals in "My Rentals".
2.  Access the **Booking Detail** screen for specific rental actions.

---

## 4. Rental Security & Handover Workflow (CRITICAL)

This flow ensures the safety of assets and builds trust between users.

<!-- [ADD IMAGE: Security Checklist Flow] -->

### 🛡️ Security Checklist Steps:
1.  **Identity Verification**: Renter uploads ID proof (verified by Owner or System).
2.  **Rental Agreement**: Digital agreement displayed and "Signed" by the user.
3.  **Handover (Item Pickup)**:
    -   Renter & Owner meet at the Pickup Location.
    -   Owner inspects the item and takes "Condition Photos" within the app.
    -   **Handover OTP**: Owner provides a unique OTP to the Renter. Renter enters it in the app to confirm receipt.
    -   Status moves to "Ongoing".
4.  **Return (Item Drop-off)**:
    -   Users meet at the Drop-off Location.
    -   Owner verifies the item condition.
    -   **Return OTP**: Renter provides a unique OTP to the Owner. Owner enters it to confirm the item is returned safely.
    -   Status moves to "Completed".

---

## 5. Other Features

*   **Real-time Chat**: Bi-directional communication with item-specific context.
*   **Blocking/Reporting**: Users can block problematic profiles or report suspicious listings.
*   **Reviews & Ratings**: Both parties leave feedback after a successful rental.
*   **Favorites**: Save items for later reference.
*   **Push Notifications**: Instant updates for chat, booking status, and handover reminders.

---
*Created on: 2026-01-19* | *Updated on: 2026-01-25*
