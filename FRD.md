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
{ code: “ERR-###”, message: “User-friendly error” }

---

# 3. Non-Functional Requirements

- Load time <2.5s  
- 99.5% uptime  
- PCI DSS compliance  
- Must support 10k concurrent checkouts  

---

# 4. Data Model
### Entities:
- CheckoutSession  
- UserProfile  
- PaymentMethod  
- Address  
- Order  

---

# 5. API Endpoints

POST /api/checkout/start
POST /api/checkout/submit
POST /api/payment/applepay
POST /api/payment/googlepay


---

# 6. Sequence Diagrams
(Description for draw.io)

### “Payment Authorization Sequence”
1. User submits form  
2. Frontend → Payment Orchestrator  
3. Orchestrator → Gateway  
4. Gateway → Approval/Decline  
5. Orchestrator → Order Service  
6. Order Service → Frontend  

---

# 7. Acceptance Criteria
See AcceptanceCriteria.md
