# Israride — Monetization & Pricing Strategy

**Status:** Draft  
**Last updated:** 2026-02-21  
**Scope:** Web MVP → Mobile platforms  
**Audience:** Founders, investors, regulators, developers

---

## 🎯 Core Principle

Israride is a **subscription-first mobility platform** designed for driver fairness, regulatory compatibility, and long-term sustainability.

The platform does **not** take commissions from rides.  
Revenue is generated through driver subscriptions and potential regulatory fees if required by law.

This model differentiates Israride from traditional ride-hailing platforms like Uber.

---

## 💰 Monetization Model Overview

Israride monetization is built on:

1. Driver subscriptions (primary revenue)
2. Regulatory fees (if mandated by law)
3. Policy-driven monetization modes (admin configurable)
4. Dormant platform fee support (disabled by default)

### Platform Fee Fallback

If regulation prohibits subscription-based monetization or requires alternative revenue mechanisms, the platform can enable a **platform fee** via the admin policy.

- Disabled by default
- Activated only if required by law
- Fully configurable via admin panel
- Transparent to drivers and passengers

This ensures regulatory compliance without architectural changes.

---

## 📌 Canonical Monetization Model

### 1️⃣ Driver Subscription (Primary Revenue)

**Model**
- First month: free trial
- After trial: monthly subscription required
- Platform access depends on subscription status

**Goals**
- Predictable recurring revenue
- Minimal financial burden on drivers
- Strong differentiation from commission-based platforms

**Planned driver fields**

```js
driver = {
  subscriptionStatus: "trial" | "active" | "expired",
  subscriptionExpiresAt: Date
}