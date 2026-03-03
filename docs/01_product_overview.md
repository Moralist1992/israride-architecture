# 01_Product_Overview

Project: Israride  
Document Type: Product Overview  
Status: Draft v0.1  
Author: Ilia Volosov  

---

## 1. Problem Statement

The taxi and private transportation market in Israel is undergoing regulatory changes. Existing ride-hailing platforms often suffer from:

- Non-transparent pricing models  
- High commission fees for drivers  
- Limited flexibility for independent drivers  
- Lack of localized multi-language support  

There is a market opportunity to introduce a transparent, fair, and locally adapted ride service platform.

---

## 2. Product Vision

Israride aims to become a transparent, commission-efficient ride service platform focused on:

- Fair pricing model  
- Clear cost calculation  
- Multi-language accessibility  
- Independent driver empowerment  

The long-term vision includes web and mobile (iOS/Android) applications.

---

## 3. Target Users

### 3.1 Passengers
- Residents of Israel
- Tourists
- Users requiring multilingual interface
- Price-sensitive riders

### 3.2 Drivers
- Licensed taxi drivers
- Independent private drivers
- Drivers seeking reduced platform commissions

---

## 4. Value Proposition

For passengers:
- Transparent pricing
- Clear ride estimation
- Multi-language interface (RU, EN, HE, AR)

For drivers:
- Fair revenue model
- Reduced intermediary commissions
- Direct client engagement

---

## 5. Current Stage

Current implementation status:

- Interactive frontend prototype
- Static deployment via Firebase Hosting
- Branch-based CI/CD workflow (dev / main)
- No backend or API implemented yet

Infrastructure maturity: Early MVP with structured CI/CD.

---

## 6. Target MVP Scope (Phase 1)

The minimum viable product must include:

- Passenger ride request creation
- Driver availability toggle
- Basic ride status lifecycle (requested → accepted → completed)
- Backend API layer
- Persistent ride storage
- Authentication (Passenger / Driver roles)

---

## 7. Technical Direction

Planned technical evolution:

Frontend:
- Refactored modular JavaScript structure
- Separation of components
- API integration layer

Backend (Planned):
- REST API
- Authentication system
- Database integration
- Role-based access control

Infrastructure:
- Maintain branch-based deployment strategy
- Consider environment isolation in future phases

---

## 8. Documentation Strategy

All product development will be accompanied by:

- Architecture documentation
- API documentation (OpenAPI/Swagger)
- Change logs
- Release notes
- User documentation
- Deployment documentation

Documentation and development will evolve in parallel.
