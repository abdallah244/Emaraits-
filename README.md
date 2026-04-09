<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%20%7C%20iOS-blue?style=for-the-badge" alt="Platform" />
  <img src="https://img.shields.io/badge/Status-In%20Development-orange?style=for-the-badge" alt="Status" />
  <img src="https://img.shields.io/badge/Duration-2%20Months-green?style=for-the-badge" alt="Duration" />
  <img src="https://img.shields.io/badge/Language-AR%20%7C%20EN-purple?style=for-the-badge" alt="Language" />
</p>

<h1 align="center">🏙️ Emaraits — دليل الخدمات</h1>
<h3 align="center">Your All-in-One Local Services Directory App</h3>

<p align="center">
  تطبيق دليل خدمات شامل للهاتف المحمول (Android & iOS) يتيح للمستخدمين استكشاف المطاعم والخدمات المحلية والمزيد، مع لوحة تحكم قوية لإدارة المحتوى والإشعارات.
</p>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Dashboard (Admin Panel)](#-dashboard-admin-panel)
- [Mobile App (User Interface)](#-mobile-app-user-interface)
- [Tech Stack](#-tech-stack)
- [Project Roadmap](#-project-roadmap)
- [Timeline — 2 Months](#-timeline--2-months)
- [API Endpoints](#-api-endpoints)
- [Database Schema](#-database-schema)
- [Getting Started](#-getting-started)
- [Folder Structure](#-folder-structure)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌟 Overview

**Emaraits** is a bilingual (Arabic / English) mobile application that serves as a comprehensive **local services directory**. Users can browse businesses across multiple categories — restaurants, beauty salons, maintenance services, rentals, and more — all from a beautifully designed mobile interface.

The app is backed by a powerful **admin dashboard** for managing clients, categories, users, and push notifications.

### 🎯 Project Goals

| Goal                   | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| 🔍 **Discoverability** | Help users easily find local businesses and services |
| 🌐 **Bilingual**       | Full Arabic & English support throughout the app     |
| 📊 **Admin Control**   | Complete dashboard for managing all content          |
| 🔔 **Engagement**      | Push notifications with deep linking to businesses   |
| 📱 **Cross-Platform**  | Native experience on both Android & iOS              |

---

## 🚀 Key Features

### For Users (Mobile App)

- 🔍 **Smart Search** — Find businesses by name, category, or keyword
- 📂 **Categorized Browsing** — Organized sections with subcategories
- 🏪 **Business Profiles** — Photos, social media, location, contact info
- 🎠 **Auto-Sliding Showcase** — Featured businesses carousel on homepage
- 🔔 **Push Notifications** — Stay updated with new businesses and offers
- 💬 **WhatsApp Integration** — Direct communication channel
- 📍 **Google Maps** — Navigate to business locations
- 🌙 **Dark Mode Support** — Comfortable viewing experience

### For Admins (Dashboard)

- 👤 **Client Management** — Full CRUD with auto-generated QR codes
- 📁 **Dynamic Categories** — Create and manage unlimited categories & subcategories
- 👥 **User Management** — Monitor and manage app users
- 📢 **Push Notifications** — Send targeted notifications with deep links
- 🖼️ **Media Management** — Upload and manage business photos & logos
- 📊 **Analytics Dashboard** — Track app usage and engagement metrics
- 🎨 **Banner Management** — Control ad banners displayed in the app

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────┐
│                   MOBILE APP                         │
│              (Android & iOS)                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐            │
│  │  Home    │ │ Browse   │ │ Profile  │            │
│  │  Screen  │ │ Screen   │ │ Screen   │            │
│  └────┬─────┘ └────┬─────┘ └────┬─────┘            │
│       └─────────────┼───────────┘                   │
│                     │                                │
└─────────────────────┼────────────────────────────────┘
                      │ REST API / WebSocket
┌─────────────────────┼────────────────────────────────┐
│              BACKEND SERVER                           │
│  ┌──────────────────┼──────────────────────┐         │
│  │          API Gateway / Auth             │         │
│  ├─────────┬────────┼────────┬─────────────┤         │
│  │ Clients │ Categories │ Users │ Notifications│     │
│  │ Module  │  Module    │Module│   Module      │     │
│  └────┬────┴─────┬──────┴──┬──┴──────┬────────┘     │
│       └──────────┴─────────┴─────────┘               │
│                     │                                │
│              ┌──────┴──────┐                         │
│              │  Database   │                         │
│              │ (PostgreSQL)│                         │
│              └──────┬──────┘                         │
│              ┌──────┴──────┐                         │
│              │File Storage │                         │
│              │  (S3/Local) │                         │
│              └─────────────┘                         │
└──────────────────────────────────────────────────────┘
                      │
┌─────────────────────┼────────────────────────────────┐
│            ADMIN DASHBOARD                            │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │ Clients  │ │Categories│ │  Users   │ │Notif.  │ │
│  │ Panel    │ │ Panel    │ │  Panel   │ │ Panel  │ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┘ │
└──────────────────────────────────────────────────────┘
```

---

## 🖥️ Dashboard (Admin Panel)

### Part 1: Client Management (إدارة العملاء)

| Feature                       | Description                                                                   |
| ----------------------------- | ----------------------------------------------------------------------------- |
| 🔢 **Auto Serial Number**     | Unique auto-generated serial number linked to a QR code for each client       |
| 📛 **Client Name**            | Bilingual name fields (Arabic & English)                                      |
| 📞 **Phone Number**           | Client contact number                                                         |
| 🖼️ **Profile & Cover Photos** | Facebook-style layout — profile picture for logo + cover photo                |
| 📍 **Google Maps Location**   | Integrated map location for the business                                      |
| 🔗 **Social Media Links**     | Separate clickable icons for: Facebook, Instagram, Snapchat, TikTok, WhatsApp |
| 📸 **Profile Gallery**        | Ability to add multiple photos to client profile                              |
| 👁️ **Visibility Toggle**      | Checkbox to show/hide the client's name                                       |

### Part 2: Categories & Sections (الأقسام والتصنيفات)

```
📁 Main Category (e.g., Restaurants / مطاعم)
 ├── 📂 Subcategory (e.g., Asian / آسيوي)
 │    ├── 🏪 Business 1
 │    ├── 🏪 Business 2
 │    └── 🏪 Business 3
 ├── 📂 Subcategory (e.g., Fast Food / وجبات سريعة)
 │    ├── 🏪 Business 1
 │    └── 🏪 Business 2
 └── 📂 Subcategory (e.g., Seafood / مأكولات بحرية)
      └── 🏪 Business 1
```

**Category Examples:**
| Category | Icon | Subcategories |
|----------|------|---------------|
| 🍽️ Restaurants / مطاعم | 🍴 | Eastern, Asian, Fast Food, Seafood |
| 🔧 Services / خدمات | ⚙️ | Plumbing, Electrical, Cleaning |
| 🏠 Rental / إيجار | 🏘️ | Apartments, Villas, Offices |
| 💇 Beauty / تجميل | 💄 | Salons, Spa, Barber |
| 🔨 Maintenance / صيانة | 🛠️ | AC, Appliances, Cars |

- Each category and subcategory has **Arabic & English names** with a **descriptive thumbnail image**
- Admin can create **unlimited** categories and subcategories

### Part 3: User Management (إدارة المستخدمين)

| Field    | Type         |
| -------- | ------------ |
| 📛 Name  | Text         |
| 📧 Email | Email        |
| 📱 Phone | Phone Number |

### Part 4: Push Notifications (الإشعارات)

- 📢 Send push notifications to all app users
- 🔗 Attach a **deep link** to a specific business/restaurant
- 💬 Custom notification message
- 📲 When user taps the notification → **navigates directly to the business profile**

---

## 📱 Mobile App (User Interface)

### Home Screen Layout

```
┌────────────────────────────────┐
│  🔔          LOGO         💬  │  ← Header (Notifications + WhatsApp)
├────────────────────────────────┤
│  🔍 Search businesses...      │  ← Search Bar
├────────────────────────────────┤
│  ┌────────────────────────┐   │
│  │   🎯 AD BANNER AREA   │   │  ← Rotating Ad Banners
│  │   (Auto-sliding)       │   │
│  └────────────────────────┘   │
├────────────────────────────────┤
│                                │
│  🍽️      🔧      🏠      💇  │  ← Category Icons Grid
│  Food   Services Rental Beauty│
│                                │
│  🔨      📦      🚗      ➕  │
│  Maint. Shopping Auto    More │
│                                │
├────────────────────────────────┤
│  ┌──────┐ ┌──────┐ ┌──────┐  │
│  │  📸  │ │  📸  │ │  📸  │  │  ← Featured Businesses
│  │Shop 1│ │Shop 2│ │Shop 3│  │    (Auto-sliding Carousel)
│  └──────┘ └──────┘ └──────┘  │
│       ◀ ● ● ● ● ● ▶         │
├────────────────────────────────┤
│  🏠 Home    📂 Browse   👤   │  ← Bottom Navigation
└────────────────────────────────┘
```

### App Features

- 💬 **WhatsApp Button** — Direct link to business WhatsApp
- 🖼️ **Ad Banners** — Promotional banners at the top
- 🔍 **Search** — Full-text search across all businesses
- 🎠 **Auto-Sliding Carousel** — Featured businesses showcase
- ⬅️ **Navigation** — Back button + Home button on every screen
- 🌐 **Language Toggle** — Switch between Arabic and English
- 📍 **Map Integration** — View business location on Google Maps
- 📱 **QR Code Scanner** — Scan QR code to view business profile

---

## 🛠️ Tech Stack

| Layer                  | Technology                     | Purpose                           |
| ---------------------- | ------------------------------ | --------------------------------- |
| **Mobile App**         | Flutter / React Native         | Cross-platform mobile development |
| **Admin Dashboard**    | React.js + Tailwind CSS        | Web-based admin panel             |
| **Backend API**        | Node.js + Express / NestJS     | RESTful API server                |
| **Database**           | PostgreSQL                     | Primary data storage              |
| **File Storage**       | AWS S3 / Firebase Storage      | Image & media storage             |
| **Push Notifications** | Firebase Cloud Messaging (FCM) | Push notification service         |
| **Maps**               | Google Maps API                | Location services                 |
| **Authentication**     | JWT + OAuth 2.0                | Secure authentication             |
| **QR Code**            | ZXing / qr_flutter             | QR code generation & scanning     |
| **Caching**            | Redis                          | API response caching              |
| **CI/CD**              | GitHub Actions                 | Automated testing & deployment    |

---

## 🗺️ Project Roadmap

```mermaid
gantt
    title Emaraits Project Roadmap — 2 Months
    dateFormat  YYYY-MM-DD
    axisFormat  %b %d

    section Phase 1 — Foundation
    Project Setup & Architecture       :done, p1_1, 2026-04-10, 3d
    Database Design & Schema           :done, p1_2, after p1_1, 3d
    Authentication & Authorization     :active, p1_3, after p1_2, 4d

    section Phase 2 — Dashboard Core
    Client Management Module           :p2_1, after p1_3, 5d
    QR Code Generation System          :p2_2, after p2_1, 2d
    Categories & Subcategories Module  :p2_3, after p2_2, 5d
    Media Upload System                :p2_4, after p2_3, 3d

    section Phase 3 — Dashboard Extended
    User Management Module             :p3_1, after p2_4, 3d
    Push Notification System           :p3_2, after p3_1, 4d
    Banner Management                  :p3_3, after p3_2, 2d
    Analytics Dashboard                :p3_4, after p3_3, 2d

    section Phase 4 — Mobile App
    App UI/UX Design                   :p4_1, after p1_3, 5d
    Home Screen & Navigation           :p4_2, after p4_1, 4d
    Category Browsing & Search         :p4_3, after p4_2, 5d
    Business Profile Screen            :p4_4, after p4_3, 4d
    Social Media & Maps Integration    :p4_5, after p4_4, 3d

    section Phase 5 — Integration & Polish
    Push Notifications Integration     :p5_1, after p4_5, 3d
    QR Code Scanner                    :p5_2, after p5_1, 2d
    Arabic/English Localization        :p5_3, after p5_2, 3d
    Dark Mode & Theming                :p5_4, after p5_3, 2d

    section Phase 6 — Testing & Launch
    Unit & Integration Testing         :p6_1, after p5_4, 4d
    UAT & Bug Fixes                    :p6_2, after p6_1, 3d
    App Store Submission               :p6_3, after p6_2, 2d
    Launch & Monitoring                :p6_4, after p6_3, 2d
```

---

## 📅 Timeline — 2 Months

### 🔵 Week 1–2: Foundation & Setup

| Day   | Task                                   | Deliverable              |
| ----- | -------------------------------------- | ------------------------ |
| 1-3   | Project scaffolding, repo setup, CI/CD | Monorepo structure ready |
| 4-6   | Database schema design & migrations    | All tables created       |
| 7-10  | Auth system (JWT, roles, permissions)  | Login/Register APIs      |
| 11-14 | Client management CRUD + QR code       | Client module complete   |

### 🟢 Week 3–4: Dashboard Development

| Day   | Task                              | Deliverable               |
| ----- | --------------------------------- | ------------------------- |
| 15-17 | Categories & subcategories module | Category tree CRUD        |
| 18-20 | Media upload system (S3/local)    | Image upload pipeline     |
| 21-23 | Social media links integration    | Profile with social icons |
| 24-26 | User management module            | User list & details       |
| 27-28 | Push notification backend (FCM)   | Notification sender ready |

### 🟡 Week 5–6: Mobile App Development

| Day   | Task                                        | Deliverable              |
| ----- | ------------------------------------------- | ------------------------ |
| 29-31 | UI/UX wireframes & app shell                | Navigation & theme ready |
| 32-34 | Home screen (banners, carousel, categories) | Home screen complete     |
| 35-37 | Category browsing + subcategories           | Browse flow complete     |
| 38-40 | Business profile screen                     | Profile with all details |
| 41-42 | Search functionality                        | Full-text search working |

### 🟠 Week 7: Integration & Polishing

| Day   | Task                                  | Deliverable                   |
| ----- | ------------------------------------- | ----------------------------- |
| 43-44 | Google Maps + social media deep links | Maps & socials working        |
| 45-46 | Push notifications integration        | Notifications with deep links |
| 47-48 | QR code scanner + generator           | QR flow complete              |
| 49    | Arabic/English localization           | i18n complete                 |

### 🔴 Week 8: Testing & Launch

| Day   | Task                                        | Deliverable      |
| ----- | ------------------------------------------- | ---------------- |
| 50-52 | Unit tests + integration tests              | 80%+ coverage    |
| 53-55 | UAT, bug fixes, performance optimization    | Stable release   |
| 56-58 | App store submissions (Google Play + Apple) | Apps submitted   |
| 59-60 | Launch monitoring + hotfixes                | 🚀 **App Live!** |

---

## 📡 API Endpoints

### Authentication

```
POST   /api/auth/login              # Admin login
POST   /api/auth/register           # Register new admin
POST   /api/auth/refresh-token      # Refresh JWT token
```

### Clients (العملاء)

```
GET    /api/clients                  # List all clients (paginated)
GET    /api/clients/:id              # Get client details
POST   /api/clients                  # Create new client
PUT    /api/clients/:id              # Update client
DELETE /api/clients/:id              # Delete client
GET    /api/clients/:id/qrcode       # Generate QR code for client
POST   /api/clients/:id/photos       # Upload client photos
PUT    /api/clients/:id/visibility   # Toggle name visibility
```

### Categories (الأقسام)

```
GET    /api/categories               # List all categories
GET    /api/categories/:id           # Get category with subcategories
POST   /api/categories               # Create category
PUT    /api/categories/:id           # Update category
DELETE /api/categories/:id           # Delete category
POST   /api/categories/:id/subcategories  # Add subcategory
```

### Users (المستخدمين)

```
GET    /api/users                    # List all users
GET    /api/users/:id                # Get user details
POST   /api/users                    # Create user
PUT    /api/users/:id                # Update user
DELETE /api/users/:id                # Delete user
```

### Notifications (الإشعارات)

```
POST   /api/notifications            # Send push notification
GET    /api/notifications            # List sent notifications
GET    /api/notifications/:id        # Get notification details
```

### Banners (الإعلانات)

```
GET    /api/banners                  # List active banners
POST   /api/banners                  # Create banner
PUT    /api/banners/:id              # Update banner
DELETE /api/banners/:id              # Delete banner
```

### Search

```
GET    /api/search?q={query}&lang={ar|en}  # Search businesses
```

---

## 🗄️ Database Schema

```sql
-- Core Tables

CREATE TABLE clients (
    id              SERIAL PRIMARY KEY,
    serial_number   VARCHAR(20) UNIQUE NOT NULL,  -- Auto-generated
    qr_code         TEXT,                          -- QR code data
    name_ar         VARCHAR(255) NOT NULL,
    name_en         VARCHAR(255) NOT NULL,
    phone           VARCHAR(20),
    profile_image   TEXT,                          -- Logo/profile pic
    cover_image     TEXT,                          -- Cover photo
    google_maps_url TEXT,
    facebook_url    TEXT,
    instagram_url   TEXT,
    snapchat_url    TEXT,
    tiktok_url      TEXT,
    whatsapp_url    TEXT,
    is_name_visible BOOLEAN DEFAULT TRUE,
    is_active       BOOLEAN DEFAULT TRUE,
    category_id     INTEGER REFERENCES subcategories(id),
    created_at      TIMESTAMP DEFAULT NOW(),
    updated_at      TIMESTAMP DEFAULT NOW()
);

CREATE TABLE categories (
    id          SERIAL PRIMARY KEY,
    name_ar     VARCHAR(255) NOT NULL,
    name_en     VARCHAR(255) NOT NULL,
    image       TEXT,
    sort_order  INTEGER DEFAULT 0,
    created_at  TIMESTAMP DEFAULT NOW()
);

CREATE TABLE subcategories (
    id          SERIAL PRIMARY KEY,
    category_id INTEGER REFERENCES categories(id) ON DELETE CASCADE,
    name_ar     VARCHAR(255) NOT NULL,
    name_en     VARCHAR(255) NOT NULL,
    image       TEXT,
    sort_order  INTEGER DEFAULT 0,
    created_at  TIMESTAMP DEFAULT NOW()
);

CREATE TABLE client_photos (
    id         SERIAL PRIMARY KEY,
    client_id  INTEGER REFERENCES clients(id) ON DELETE CASCADE,
    image_url  TEXT NOT NULL,
    sort_order INTEGER DEFAULT 0,
    created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE users (
    id         SERIAL PRIMARY KEY,
    name       VARCHAR(255) NOT NULL,
    email      VARCHAR(255) UNIQUE NOT NULL,
    phone      VARCHAR(20),
    created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE notifications (
    id          SERIAL PRIMARY KEY,
    title       VARCHAR(255) NOT NULL,
    message     TEXT NOT NULL,
    deep_link   TEXT,              -- Link to client profile
    sent_at     TIMESTAMP DEFAULT NOW(),
    sent_by     INTEGER REFERENCES admins(id)
);

CREATE TABLE banners (
    id          SERIAL PRIMARY KEY,
    image_url   TEXT NOT NULL,
    link_url    TEXT,
    is_active   BOOLEAN DEFAULT TRUE,
    sort_order  INTEGER DEFAULT 0,
    created_at  TIMESTAMP DEFAULT NOW()
);

CREATE TABLE admins (
    id            SERIAL PRIMARY KEY,
    username      VARCHAR(100) UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    role          VARCHAR(20) DEFAULT 'admin',
    created_at    TIMESTAMP DEFAULT NOW()
);
```

---

## ⚡ Getting Started

### Prerequisites

- Node.js >= 18.x
- PostgreSQL >= 14
- Flutter SDK >= 3.x (for mobile app)
- Firebase project (for push notifications)
- Google Maps API key

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/emaraits.git
cd emaraits
```

### 2. Backend Setup

```bash
cd backend
cp .env.example .env          # Configure environment variables
npm install                    # Install dependencies
npm run db:migrate             # Run database migrations
npm run db:seed                # Seed initial data
npm run dev                    # Start development server
```

### 3. Dashboard Setup

```bash
cd dashboard
cp .env.example .env          # Configure API URL
npm install
npm run dev                    # Start at http://localhost:3000
```

### 4. Mobile App Setup

```bash
cd mobile
cp .env.example .env          # Configure API URL & keys
flutter pub get               # Install dependencies
flutter run                   # Run on connected device/emulator
```

### Environment Variables

```env
# Backend
DATABASE_URL=postgresql://user:password@localhost:5432/emaraits
JWT_SECRET=your-secret-key
AWS_S3_BUCKET=emaraits-media
FIREBASE_PROJECT_ID=your-firebase-project
GOOGLE_MAPS_API_KEY=your-maps-key

# Dashboard
REACT_APP_API_URL=http://localhost:4000/api

# Mobile
API_BASE_URL=http://localhost:4000/api
GOOGLE_MAPS_KEY=your-maps-key
```

---

## 📁 Folder Structure

```
emaraits/
├── 📂 backend/                    # API Server
│   ├── src/
│   │   ├── auth/                  # Authentication module
│   │   ├── clients/               # Client management
│   │   ├── categories/            # Categories & subcategories
│   │   ├── users/                 # User management
│   │   ├── notifications/         # Push notifications
│   │   ├── banners/               # Banner management
│   │   ├── upload/                # File upload service
│   │   ├── search/                # Search engine
│   │   └── common/                # Shared utilities
│   ├── migrations/                # Database migrations
│   ├── seeds/                     # Seed data
│   ├── tests/                     # Unit & integration tests
│   └── package.json
│
├── 📂 dashboard/                  # Admin Dashboard (React)
│   ├── src/
│   │   ├── components/            # Reusable UI components
│   │   ├── pages/
│   │   │   ├── Clients/           # Client management pages
│   │   │   ├── Categories/        # Category management pages
│   │   │   ├── Users/             # User management pages
│   │   │   ├── Notifications/     # Notification management
│   │   │   └── Banners/           # Banner management
│   │   ├── services/              # API service layer
│   │   ├── hooks/                 # Custom React hooks
│   │   ├── i18n/                  # Internationalization (AR/EN)
│   │   └── utils/                 # Utility functions
│   └── package.json
│
├── 📂 mobile/                     # Mobile App (Flutter)
│   ├── lib/
│   │   ├── screens/               # App screens
│   │   │   ├── home/              # Home screen
│   │   │   ├── browse/            # Category browsing
│   │   │   ├── profile/           # Business profile
│   │   │   └── search/            # Search screen
│   │   ├── widgets/               # Reusable widgets
│   │   ├── models/                # Data models
│   │   ├── services/              # API & notification services
│   │   ├── providers/             # State management
│   │   └── l10n/                  # Localization (AR/EN)
│   ├── assets/                    # Images, fonts, icons
│   └── pubspec.yaml
│
├── 📂 docs/                       # Documentation
│   ├── api-docs.md                # API documentation
│   ├── wireframes/                # UI/UX wireframes
│   └── architecture.md            # System architecture
│
├── .github/
│   └── workflows/                 # CI/CD pipelines
├── docker-compose.yml             # Docker setup
├── README.md                      # This file
└── LICENSE
```

---

## 🧪 Testing Strategy

| Type              | Tool                | Coverage Target       |
| ----------------- | ------------------- | --------------------- |
| Unit Tests        | Jest / Flutter Test | 80%+                  |
| Integration Tests | Supertest           | All API endpoints     |
| E2E Tests         | Cypress / Detox     | Critical user flows   |
| Load Testing      | Artillery           | 1000 concurrent users |

```bash
# Run backend tests
cd backend && npm test

# Run dashboard tests
cd dashboard && npm test

# Run mobile tests
cd mobile && flutter test
```

---

## 🔒 Security Measures

- 🔐 JWT-based authentication with refresh tokens
- 🛡️ Role-based access control (RBAC)
- 🔒 Password hashing with bcrypt (salt rounds: 12)
- 🚫 Rate limiting on all API endpoints
- 📝 Input validation & sanitization (XSS/SQL Injection prevention)
- 🔑 Environment variables for sensitive data
- 📋 CORS configuration for allowed origins
- 🔍 Request logging & audit trail

---

## 📊 Performance Targets

| Metric                     | Target                |
| -------------------------- | --------------------- |
| API Response Time          | < 200ms               |
| App Launch Time            | < 2 seconds           |
| Image Load Time            | < 1 second (with CDN) |
| Push Notification Delivery | < 5 seconds           |
| Search Results             | < 500ms               |
| Uptime                     | 99.9%                 |

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Commit Convention

```
feat:     New feature
fix:      Bug fix
docs:     Documentation changes
style:    Code style changes (formatting, etc.)
refactor: Code refactoring
test:     Adding or updating tests
chore:    Build process or auxiliary tool changes
```

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <b>Built with abdallah</b>
  <br/>
  <sub>© 2026 abdallah — All Rights Reserved</sub>
</p>
