# Panchayat App Architecture

Panchayat App is designed as a scalable multi-PG SaaS mobile platform with separate owner and tenant workflows, real-time data synchronization, and isolated PG-based data handling.

---

## Architecture Overview

The application follows a role-based and PG-isolated architecture. Each PG has its own unique `pgId`, and all major data operations are filtered using the active PG context.

This ensures that owners and tenants only access data related to their assigned PG.

---

## Core Architecture Principles

- Multi-PG SaaS structure
- Role-based owner and tenant access
- PG-wise data isolation using `pgId`
- Real-time synchronization using Firestore listeners
- Persistent login using AsyncStorage
- Cloud-based media upload handling
- Mobile-first UI with dark mode support
- Modular screen and component structure

---

## User Roles

### Owner

Owners can manage PG operations such as:

- Tenant records
- Rent collections
- Payment history
- Complaints
- Notices
- Service requests
- Dashboard analytics

### Tenant

Tenants can access:

- PG dashboard
- Payment requests
- Complaint tracking
- Notices
- Services
- Profile management
- Community-related features

---

## Data Flow

```text
User Login
   ↓
Firebase Authentication
   ↓
Role Detection
   ↓
Fetch User Profile from Firestore
   ↓
Set Active PG Context
   ↓
Load Owner or Tenant Workflow
   ↓
Real-time Firestore Updates
