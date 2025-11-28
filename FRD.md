# Functional Requirements Document (FRD)
## Project: Checkout Redesign

---

# 1. Feature Overview
The new checkout will be a **React single-page application** backed by the existing order service and the new payment orchestration layer.

---

# 2. Functional Requirements

## 2.1 Guest Checkout
### FR-001
System must allow order placement without requiring an account.

### FR-002
If user provides email, system stores it for order confirmation.

---

## 2.2 Payment Methods
### FR-010 — Apple Pay integration  
System must display Apple Pay button when device supports it.

### FR-011 — Google Pay integration  
Google Pay must be offered for all Android Chrome users.

### FR-012 — Credit card validation
Luhn algorithm, expiry, CVV rules.

---

## 2.3 Address Validation
### FR-020
ZIP code auto-fills State & City using LocationAPI.

### FR-021
Invalid ZIP triggers an inline error.

---

## 2.4 Order Summary
### FR-030
Taxes & shipping recalculate dynamically upon address update.

---

## 2.5 Error Handling
### FR-040
All errors must follow standardized format:
