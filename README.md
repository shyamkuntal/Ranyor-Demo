# RANYOR - Premium Rental Marketplace

Welcome to the official repository for **RANYOR**, a high-end peer-to-peer rental marketplace built with React Native and Go.

---

- 🔄 **[Application Workflow](./docs/WORKFLOW.md)** - Detailed end-to-end user and system workflows.

---

## 🎯 What is RANYOR?

RANYOR is a **high-end rental marketplace** mobile application that facilitates:
- **Listing items for rent** (Electronics, Vehicles, Equipment, Furniture, etc.)
- **Flexible renting** on a daily or hourly basis with dynamic availability rules
- **Real-time communication** via an integrated WebSocket chat system
- **Secure rental lifecycle** with a mandatory security checklist (Agreement, ID Proof, OTP verification)
- **Geospatial discovery** for finding items available near the user

---

## 📊 Project Statistics

| Category | Count | Details |
|----------|-------|---------|
| **Screens** | 36 | Auth (6), Home (6), List (6), Profile (11), Chat (2), Rent (5) |
| **Components** | 22+ | GlassView, BookingSecurityManager, SecurityChecklist, ItemCard, etc. |
| **Services** | 13 | Auth, Item, Booking, Chat, Socket, Block, Image, Push, etc. |
| **Context Providers** | 3 | AuthContext, LocationContext, NotificationContext |
| **Backend Handlers** | 14 | Auth, Item, Booking, Chat, User, Block, Review, OTP, etc. |
| **Data Models** | 14 | User, Item, Booking, Chat, Message, Review, BlockedUser, etc. |
| **REST APIs** | 50+ | Full CRUD and specialized features (blocking, availability) |
| **WebSocket Endpoints** | 1 | Production-ready real-time chat messaging |
| **Total Lines of Code** | ~18,000+ | Frontend + Backend |

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    MOBILE CLIENT (RANYOR)                   │
│                 (React Native 0.83.1)                       │
├─────────────────────────────────────────────────────────────┤
│  Screens  │  Components  │  Services  │  Context  │  Utils  │
└─────────────────────────────────────────────────────────────┘
                            │
               HTTP REST API │ WebSocket (Real-time)
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                    BACKEND SERVER (Go)                      │
│                      (Go 1.24)                              │
├─────────────────────────────────────────────────────────────┤
│  Handlers  │  Middleware  │  WebSocket  │  FCM  │  OTP      │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    DATA LAYER                               │
├─────────────────────────────────────────────────────────────┤
│  MongoDB (Database)  │  Firebase Storage  │  Twilio/SMTP     │
└─────────────────────────────────────────────────────────────┘
```

---

## 📱 Frontend Tech Stack

| Category | Technology | Version | Purpose |
|----------|------------|---------|---------|
| **Framework** | React Native | 0.83.1 | Cross-platform mobile development |
| **Design System** | Glassmorphism | Custom | Premium, modern UI aesthetics |
| **Navigation** | React Navigation | 7.x | Stack, Tab, and Native navigation |
| **State Management** | React Context | - | Global auth, location, notification state |
| **Real-time** | Socket.IO Client | 4.8.3 | WebSocket chat messaging |
| **Maps** | React Native Maps | 1.26.20 | Location display and picker |
| **Image Handling** | Image Picker + Resizer | 8.2.1 | Camera/gallery access, compression |
| **Local Storage** | AsyncStorage | 2.2.0 | Token and user data persistence |

---

## ⚙️ Backend Tech Stack

| Category | Technology | Purpose |
|----------|------------|---------|
| **Language** | Go 1.24 | High-performance, concurrent backend |
| **Database** | MongoDB | NoSQL with GeoJSON/Geospatial support |
| **Authentication** | JWT | Stateless security with expiration |
| **Real-time** | Gorilla WebSocket | Bi-directional communication |
| **Push Notifications** | Firebase Admin | FCM delivery for booking updates |
| **Security** | bcrypt & Middleware | Password hashing, rate limiting, CORS |
| **Cloud Storage** | Firebase Storage | Image hosting for items and profiles |

---

## 📊 Key Data Models

| Model | Purpose | Key Fields |
|-------|---------|------------|
| **User** | Identity | accountType (Individual/Business), rating, GeoLocation |
| **Item** | Listing | availabilityRules (Patterns/Exclusions), GeoLocation, pricingUnit |
| **Booking** | Transaction | trackingId, status, Security (Agreement, OTPs, Photos) |
| **Chat** | Interaction | participants, itemId, unreadCount |
| **Review** | Feedback | rating (1-5), targetType (User/Item) |
| **BlockedUser** | Safety | userId, blockedId |

---

## 🚀 Specialized Features

### 1. Advanced Availability Engine
Owners can set complex availability patterns:
- Weekdays/Weekends/All days
- Manual exclusion of specific dates
- Manual inclusion of specific overrides
- Integrated with business hours and holidays

### 2. Rental Security Lifecycle
A multi-step handover and return process:
- **Agreement**: Digital signing before rental starts.
- **Verification**: ID proof upload and verification.
- **Handover**: Mutual OTP exchange and condition photos.
- **Return**: Verified return OTP to close the loop.

### 3. User Safety & Moderation
- **Blocking**: Block users from messaging or seeing your listings.
- **Reporting**: Report items or users for review.
- **Rate Limiting**: Protection against brute-force and spam.

### 4. Business Accounts
- Dedicated profiles for rental shops.
- Business naming, logos, and descriptions.
- Enhanced credibility and tracking.

---

## Demo Account

```javascript
- User:          test@test.com
- Password:      @@Abc123
```

```javascript
- User:          1@1.com
- Password:      @@Abc123
```

```javascript
- User:          b@1.com
- Password:      @@Abc123
```
---
*Developed by Shyam Kuntal*
