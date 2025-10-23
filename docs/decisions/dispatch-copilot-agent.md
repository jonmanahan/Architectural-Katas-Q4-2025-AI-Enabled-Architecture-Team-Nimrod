---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Operations Team, Data Science Team]
informed: [Engineering Team, Product Team]
---

# Agentic Dispatch Workflow Using GenAI

## Context and Problem Statement

MobilityCorp has an opportunity to improve it's operational efficiency by addressing two critical business needs:

1. Anticipating customer demand to position the right vehicles in the right locations at the right times
2. Intelligently prioritizing battery swaps based on charge levels and demand patterns

To support these objectives, the company requires an operations platform that enables field operators to make real-time dispatch decisions based on dynamic conditions--such as weather, traffic, and demand fluctuations. We need to determine a workflow that will enable real-time, explainable dispatch decisions while supporting operator collaboration and maintaining human oversight for safety and compliance.

## Decision Drivers

MobilityCorp's priorities for the system include:

- Demand anticipation and vehicle positioning optimization
- Intelligent battery management prioritization
- Real-time adaptability
- Human-in-the-loop collaboration
- Comprehensive automated testing
- Auditability and compliance
- Use of modern, prevalent tools

## Considered Options

- GenAI Based Agentic Workflow
- ML/Forecasting with Dynamic Route Planning (No GenAI)
- Rule Based Dispatch System

## Decision Outcome

Chosen option: "GenAI Based Agentic Workflow", because it uniquely enables conversational, explainable dispatch recommendations that anticipate customer demand and optimize service availability and reliability while maintaining human oversight through natural language negotiation between operators and AI agents.

### Confirmation

- Dispatch recommendation requires operator approval via the Feedback Agent before execution
- All agent decisions, tool calls, and reasoning chains are logged for compliance review
- Performance metrics monitored: approval rates, decision latency, route efficiency, satisfaction scores

## Pros and Cons of the Options

### GenAI Based Agentic Workflow

Builds upon dynamic ML forecasting and route optimization by adding a GenAI orchestration layer. LLMs coordinate specialized agents and tools to provide conversational interaction, natural language explainability, and intelligent synthesis of optimization outputs that traditional approaches cannot deliver.

- Good, because Feedback Agent enables operators to review, question, and negotiate recommendations with agent
- Good, because combines proven optimization algorithms with intelligent LLM orchestration
- Good, because business logic adjustments require prompt engineering rather than code redeployment
- Bad, because LLM outputs are non-deterministic, requiring validation and careful prompt engineering
- Bad, because per-request LLM API costs are higher than traditional compute
- Bad, because requires sophisticated observability infrastructure

### ML/Forecasting with Dynamic Route Planning (No GenAI)

System uses ML forecasting and vehicle routing optimization to generate dispatch recommendations in real-time when operators request their next assignment. Incorporates current vehicle locations, battery levels, and demand forecasts, but uses traditional UI rather than a conversational interface.

- Good, because adapts to real-time conditions throughout the day
- Good, because leverages proven optimization algorithms for route efficiency
- Good, because lower per-request costs than LLM inference
- Neutral, because uses the same optimization algorithms as GenAI approach, but lacks intelligent orchestration and conversational layer
- Bad, because cannot explain reasoning in natural language
- Bad, because operators cannot negotiate or provide contextual feedback conversationally
- Bad, because adjusting decision priorities and criteria requires algorithm changes and redeployment

### Rule Based Dispatch System

Hardcoded business logic that dispatches based on prioritization rules.

- Good, because fast execution with minimal computational overhead
- Good, because business stakeholders understand and can explictly influence rules and logic
- Bad, because complexity grows exponentially with number of variables
- Bad, because workflow cannot learn from operator feedback over time
- Bad, because no conversational interface for operator negotiation or natural language explanation

### Related Documentation

- [Architecture Diagram](images/c3-dispatch-agent.png)
