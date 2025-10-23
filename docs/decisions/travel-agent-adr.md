---
# These are optional metadata elements. Feel free to remove any of them.
status: "proposed"
date: {2025-10-22}
decision-makers: {Jon Manahan, Kelsey Roy, Eric Olson}
---

# Travel Agent

## Context and Problem Statement

MobilityCorp needs a rider-facing assistant that improves trip quality before and during a ride without sacrificing safety or privacy. Riders want: 
* (1) pre-ride/in-ride queries (e.g., “best pizza/cheapest tacos/grocery store with a niche ingredient on my route”)
* (2) dynamic re-routing by preference (avoid tolls vs faster; scenic; add a grocery stop with all list items)
* (3) live incident awareness (flooding, downed trees, crashes) with clear alternatives
* (4) leave/arrival time optimization within a window 
* (5) the ability to correct stale/fabricated data and force a re-plan.

### Why now: 
These capabilities increase potential customer satisfaction, the likelihood of a user adopting this ride share service for their daily commute, as well as reduce abandonment when conditions change, and differentiate MobilityCorp in cities and expanding suburbs while preserving reliability and availability.

## Decision Drivers

* User trust, safety, and satisfaction
* Operational resilience
* Intuitive, conversational, low-friction  UX
* Users ability to correct information
* Niche user prompt fulfillment

## Considered Options

* O1: Thin Orchestrator + External Intelligence
* O2: Hybrid Planner with Agent Ensemble
* O3: Agentic Autonomy (end-to-end auto-execute)

## Decision Outcome

### Chosen option: 
O2: Hybrid Planner with Agent Ensemble, because it satisfies the requested agent architecture and preserves safety by verifying all LLM outputs with deterministic tools and policy gates.

### What it is: 
A multi-agent conversational layer that orchestrates user requests, with LLM agents for planning, optimization, judging, and reservation backed by tool calls that do the safety-critical work (routes, availability, reservations). All actions require confirm-before-act and pass policy-as-code (machine-checked rules).

## Confirmation
* Automated gates: policy-as-code checks for each tool call; reservation “dry-run” diffs; tool vs LLM consistency checks (LLM output must match tool reality).
* Audits: monthly logs review of agent/tool traces; privacy retention and tokenization tests in CI.
* User feedback: Ratings, number of users re-renting, number of users using for daily/recurring commutes, satisfaction scores.

## Pros and Cons of the Options
### O1: Thin Orchestrator + External Intelligence 
* Good, because fastest to pilot.
* Bad, because weaker verification; higher hallucination risk.
* Bad, because vendor lock-in and limited flexibility and expensive to change.

### O2: Hybrid Planner with Agent Ensemble
* Good, because critical steps are verified before executed, not executed automatically.
* Good, because modular (swap mapping/POI/reservation providers).
* Bad, because increased integration/observability needs across agents/tools.

### O3: Agentic Autonomy (auto-execute)
* Good, because most “hands-off” UX.
* Bad, because verification/safety/compliance risks and unpredictable latency.
* Bad, because lower user trust without confirm-before-act; higher privacy exposure.