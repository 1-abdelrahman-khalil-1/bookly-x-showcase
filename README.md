# BooklyX — Mobile Ecosystem

> A production-grade, multi-role SaaS booking platform built as a graduation project.  
> Designed for service businesses such as clinics, spas, salons, and barbershops.

---

## 🎬 Demo Videos

See the app in action — both roles, full flows, real data:

### 📱 Client App

https://github.com/user-attachments/assets/9d4a05d0-22b0-4a32-b121-1c5ef795f2ea

### 💼 Staff App

https://github.com/user-attachments/assets/db9cb7f3-e0d9-4948-886d-bc9425459c96

---

## 🧠 What Is BooklyX?

BooklyX is a **full-stack mobile platform** that allows service businesses to manage their bookings, staff, and operations — all from a mobile app.

The platform has **two distinct mobile apps** built within the same Flutter codebase:

| App | Who Uses It | Purpose |
|---|---|---|
| **Client App** | Customers | Discover services, book appointments, track history, earn loyalty points |
| **Staff App** | Employees & Managers | Manage schedules, handle bookings, track earnings, view analytics |

Both apps connect to the same **Node.js + MySQL backend**, secured behind a **Web Application Firewall (WAF)**.

---

## 🏆 What I Built

This is a **graduation project** where I was solely responsible for the entire Flutter mobile ecosystem — both apps, from scratch.

### My Responsibilities

- ✅ Designed and implemented the **full Flutter architecture** (feature-first, layered)
- ✅ Built the complete **Client App** — 20+ screens end-to-end
- ✅ Built the complete **Staff App** — 15+ screens end-to-end
- ✅ Created a shared **design system** (colors, typography, spacing, components)
- ✅ Integrated all features with the **REST API** (100+ endpoints)
- ✅ Implemented **multi-language support** (English & Arabic, RTL)
- ✅ Contributed to **backend database schema design** and API contract definition
- ✅ Wrote reusable **core widgets** used across both apps

> The web frontend was handled by other team members. The backend was a collaborative effort.

---

## ✨ Key Features

### Client App
- 🔍 **Service & Business Discovery** — browse and filter providers by category, location, and rating
- 📅 **Smart Booking Flow** — pick service → select staff → choose time slot → confirm
- 🗓️ **Appointment Management** — view, reschedule, and cancel bookings
- 💳 **Payment Integration** — integrated payment handling in the booking flow
- ⭐ **Reviews & Ratings** — leave feedback after completed appointments
- 🎁 **Loyalty System** — earn and redeem points across bookings
- 🔔 **Notifications** — real-time booking status updates
- 🌐 **Bilingual UI** — full English / Arabic support with RTL layout switching

### Staff App
- 📆 **Schedule Management** — visual calendar-based daily/weekly agenda
- 📋 **Booking Operations** — confirm, reschedule, complete, or cancel bookings
- ⚙️ **Availability Configuration** — set working hours, days off, and service limits
- 💰 **Earnings Dashboard** — track revenue, completed sessions, and performance metrics
- 📊 **Analytics** — charts and summaries powered by FL Chart
- 🗺️ **Location & Map Integration** — set and view business locations via Google Maps

---

## 🛠️ Tech Stack

### Mobile — Flutter / Dart

| Layer | Technology | Purpose |
|---|---|---|
| **State Management** | Riverpod (FutureProvider + StateNotifier) | Reactive, scalable state |
| **Navigation** | AutoRoute | Type-safe, code-generated routing |
| **HTTP Client** | Dio | REST API communication, interceptors |
| **Localization** | Slang | Type-safe i18n with code generation |
| **Local Storage** | Shared Preferences | Session persistence |
| **Image Loading** | Cached Network Image | Efficient remote image rendering |
| **Charts** | FL Chart | Earnings and analytics visualizations |
| **Calendar** | Table Calendar | Schedule and booking date picker |
| **Animations** | Lottie | Micro-animations for key interactions |
| **Maps** | Google Maps Flutter | Location display and selection |
| **Pagination** | Infinite Scroll Pagination | Paged list views for large data |

### Backend — Node.js

| Technology | Purpose |
|---|---|
| **Express.js** | REST API server |
| **MySQL** | Relational database |
| **JWT** | Authentication & authorization tokens |
| **Layered Architecture** | Controller → Service → Repository → Database |
| **OpenAPI Spec** | Documented and typed API contracts |
| **WAF** | Web Application Firewall for request protection |

### Tooling & Design

| Tool | Use |
|---|---|
| **Figma** | UI/UX design and prototyping |
| **GitHub Actions** | Version control and collaboration |
| **GitHub Copilot / Claude / ChatGPT** | AI-assisted development acceleration |

---

## 📐 Architecture

### Why Feature-First?

The project uses a **feature-first architecture** rather than a layer-first one. This means each feature (e.g. `bookings`, `profile`, `schedule`) owns all its layers — data, domain, and presentation — in one place. This makes features independently navigable, testable, and scalable.

```
lib/
 ├── app/
 │    ├── core/                   # Shared design system & infrastructure
 │    │    ├── api_helper/        # DioClient, error handling, interceptors
 │    │    ├── constants/         # App-wide constants
 │    │    ├── enums/             # Typed enum sets
 │    │    ├── extensions/        # Context, spacing, style extensions
 │    │    ├── models/            # Shared data models
 │    │    ├── services/          # Cross-feature services
 │    │    ├── styles/            # Typography atoms
 │    │    ├── themes/            # Light/dark theme tokens
 │    │    ├── utils/             # Formatters, validators, helpers
 │    │    └── widgets/           # Reusable core UI components
 │    │
 │    └── features/
 │         ├── client/            # All client-facing features
 │         │    ├── auth/
 │         │    ├── home/
 │         │    ├── bookings/
 │         │    ├── booking_service/
 │         │    ├── profile/
 │         │    └── ...
 │         │
 │         ├── staff/             # All staff-facing features
 │         │    ├── auth/
 │         │    ├── schedule/
 │         │    ├── bookings/
 │         │    ├── earnings/
 │         │    └── ...
 │         │
 │         └── common/            # Features shared across both roles
 │
 ├── generated/                   # Code-generated files (icons, i18n)
 ├── router/                      # AutoRoute configuration
 └── main.dart
```

### System Architecture

```
┌──────────────────────────┐      ┌──────────────────────────┐
│    Flutter Client App    │      │     Flutter Staff App    │
└────────────┬─────────────┘      └────────────┬─────────────┘
             │                                 │
             └────────────────┬────────────────┘
                              │  HTTPS / REST API
                              ▼
              ┌──────────────────────────────┐
              │   WAF (Web App Firewall)     │
              │   Rate limiting • Filtering  │
              └──────────────────┬───────────┘
                                 │
                                 ▼
              ┌──────────────────────────────┐
              │        Express.js API        │
              │  JWT Auth • Layered Backend  │
              └──────────────────┬───────────┘
                                 ▼
              ┌──────────────────────────────┐
              │         MySQL Database       │
              └──────────────────────────────┘
```

### State Management Pattern

Every feature follows a consistent three-layer state pattern:

```
UI (Widget)
  └── ref.watchWhen(provider)         ← reactive UI binding
        ├── loading → Shimmer Widget  ← never a spinner
        ├── error   → Error Widget
        └── data    → Feature Widget

StateNotifier (Controller)
  └── executeVoid / execute           ← via InternetErrorHandlerMixin
        ├── handles loading state
        ├── handles error state
        └── sets specific success message

Service
  └── DioClient → REST API
```

---

## 🎨 Design System

A fully custom design system was built from scratch and enforced project-wide:

- **Colors** — Centralized `AppColors` palette, no hardcoded hex values anywhere
- **Typography** — Context extension atoms (`context.bold20Primary`, `context.regular14TextSub`) — no raw `TextStyle`
- **Spacing** — Extension-based spacing (`16.h`, `8.w`) for consistent density
- **Icons** — Custom icon font (`MyIcons`) generated from Iconsax, no `Icons.*`
- **Core Widgets** — `CustomAppBar`, `CustomButton`, `CustomTextFormField`, `CustomCachedNetworkImage`, `CustomDropList`, `CustomDatePickerField`
- **Loading States** — All async states use Shimmer skeletons, never `CircularProgressIndicator`

---

## 🌐 Backend Repository

**Backend Repository:** [BooklyX Backend](https://github.com/1-abdelrahman-khalil-1/booklyX_backend)

---

## 📝 Notes

- This repository contains only the **Flutter mobile ecosystem**
- The web frontend exists in a separate repository, maintained by other team members
- All architecture decisions, code review, and integration logic were personally designed and maintained
