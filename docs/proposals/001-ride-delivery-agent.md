---
status: "proposed"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
---

# Ride Delivery Agent

## Context and Problem Statement

RideDelivery is a stretch goal for us here at MobilityCorp. The desire is, have an optimized delivery of cars to renters (either on demand or planned) and return‑to‑hub post rental. For delivery, the vehicle is autonomously driven to the renter or meet point. For returns, it autonomously selects and drives to the best hub using the dispatch/demand forecaster plus hub capacity/charger state.

Current Realities/constraints: City vs suburb ODDs; mixed traffic and vulnerable road users; adverse weather; changing local laws and permitting; reliance on high‑integrity localization and HD maps; stringent safety requirements; continuous human oversight; full auditability.

### Why in the future:

These capabilities are not fully fleshed out yet or even eligible depending on where you reside. This is for when we plan on getting new cars or when automated vehicles in general become more prominent and stable.

## Decision Drivers

- User trust, safety, and satisfaction
- Operational resilience
- Customers need cars in the right places at the right times

## Considered Options

- O1: Human Valet + Teleoperation Assist
- O2: Renter Pickup and Dropoff
- O3: Full City and Suburb scaled Autonomy (Minimal‑HITL only in extreme cases, Basically pure Automation)

## Decision Outcome

Chosen option: "Full City and Suburb scaled Autonomy (Minimal‑HITL only in extreme cases, Basically pure Automation)"

### What it is:

A fully automated capability where the car plans, perceives, and drives end‑to‑end without human intervention inside a clearly defined city or suburb scaled ODD. ODD refers to where/when autonomy is allowed (roads, speeds, weather/time). If outside ODD or other extreme issues occur, the vehicle enters MRC (Minimal Risk Condition = safe, predictable stop), self‑reassesses, and either self‑recovers (re‑plan around the issue) or aborts the mission (no remote driving)

### Why this option (future stretch):

Addresses the product issue of customers complaining that the right vehicles arent in the right places via instant delivery/planned delivery/return at scale. It maximizes utilization and customer convenience, and removes per‑mile human costs. Choosing O3 now sets technical and governance north‑stars (fail‑operational architecture, certification‑grade logs, privacy‑by‑design) even while near‑term deployments may remain manual or limited‑ODD.

## Confirmation

- Automated gates: policy-as-code checks for each tool call; reservation “dry-run” diffs; tool vs LLM consistency checks (LLM output must match tool reality).
- Audits: monthly logs review of agent/tool traces; privacy retention and tokenization tests in CI.
- User feedback: Ratings, number of users re-renting, number of users using for daily/recurring commutes, satisfaction scores.

## Pros and Cons of the Options

### O1: Human Valet + Teleoperation Assist

- Good, because reliable.
- Bad, because slow.
- Bad, because hard to anticipate user needs.
- Bad, because doesn't address current product issues
- Bad, because needs person along for the ride after car is delivered

### O2: Renter Pickup and Dropoff

- Good, because no need for valet
- Good, because no potential delays in delivery (since there is no delivery)
- Bad, because onis is on user, inconvenient comparatively to automated delivery
- Bad, because can't anticipate where cars will be needed or will be stocked
- Bad, because have to think about consequences if cars aren't returned

### O3: Agentic Autonomy (auto-execute)

- Good, because most hands-off and smooth experience.
- Good, because autonomy is only done when user/renter is not in the vehicle.
- Good because maximizes availability/utilization, faster pickups/returns, lower long‑run cost/ride.
- Good because consistent user experience (no waiting for staff); hub selection optimizes balance/charging.
- Bad, because not currently feasible.
- Bad, because no human override means stricter proof obligations; recovery requires robust self‑rescue or post‑hoc field assist (not driving, human interaction in these cases), increasing design complexity
