## Phase 1: Algorithm Foundation

**Goal:** Deliver early, tangible operational improvements through optimized fleet movement

### Deliverables:

- Google OR-Tools vehicle routing optimizer
- Basic data collection infrastructure (GPS, battery levels, reservation data)
- Simulation/testing environment using historical data

### Success Metrics:

- Vehicle Utilization Rate: +30% improvement
- Average Repositioning Time: -40% reduction
- Operational Cost per Trip: -30% reduction

### Cost Estimate:

**Timeline:** 3 months

**Team Composition:**

- 1 Senior ML/Optimization Engineer
- 1 Senior Data Engineer
- 1 Mid-level Backend Engineer
- 1 Engineering Manager (20% allocation)

**Total Team:** 3.2 FTE

**Engineering Cost:** €72,000

- Calculation: 3.2 FTE × €7,500/month average blended rate × 3 months

## Phase 2: Simple Demand Forecasting Model

**Goal:** Add predictive capability to inform where/when to position vehicles

### Deliverables:

- LightGBM demand forecasting model (basic version)
- Medallion data lake (Bronze → Silver → Gold)
- Integration: Model predictions feed into OR-Tools optimizer
- Databricks setup for experimentation

### Success Metrics:

- Demand Forecast Accuracy: >80% accuracy, MAE <15%
- Vehicle Availability Rate: >95%
- Vehicle Utilization Rate: +30% improvement (building on Phase 1)

### Cost Estimate:

**Timeline:** 3 months

**Team Composition:**

- 2 Senior ML Engineers
- 2 Senior Data Engineers
- 1 Mid-level Backend Engineer
- 1 Engineering Manager (25% allocation)

**Total Team:** 5.25 FTE

**Engineering Cost:** €118,125

- Calculation: 5.25 FTE × €7,500/month average blended rate × 3 months

## Phase 3a: Travel Assistant MVP

**Goal:** Customer-facing AI that improves booking experience and builds reliance

### Deliverables:

- Travel Agent Orchestrator with Route Planner Agent + Reservation Agent
- Reservation Context Tool + basic Mapping Tool
- Customer Reservation System frontend (web + mobile)
- Pydantic AI framework deployment
- WebSocket chat interface with confirm-before-act validation

### Success Metrics:

- Conversation Completion Rate: >60%
- Booking Conversion Lift: +15% vs. control
- Customer Satisfaction (NPS): >50

### Cost Estimate:

**Timeline:** 4 months

**Team Composition:**

- 2 Senior AI/ML Engineers (Agentic AI development)
- 2 Senior Frontend Engineers (React/React Native)
- 2 Senior Backend Engineers
- 1 Mid-level QA Engineer
- 1 Product Manager (50% allocation)
- 1 Engineering Manager (30% allocation)

**Total Team:** 7.8 FTE

**Engineering Cost:** €234,000

- Calculation: 7.8 FTE × €7,500/month average blended rate × 4 months

## Phase 3b: Operations Dispatch Agent

**Goal:** AI-assisted dispatch for field technicians and fleet redistributors

### Deliverables:

- Dispatch Agent: Recommender, Feedback (human-in-the-loop), Manager
- Operations System frontend (web admin + mobile for field techs)
- Integration with Phase 2 forecasting + Phase 1 optimizer

### Success Metrics:

- Dispatch Recommendation Approval Rate: >70%
- Battery Swap Efficiency: -25% downtime reduction
- Mid-trip Battery Failures: <1%

### Cost Estimate:

**Timeline:** 3 months

**Team Composition:**

- 1 Senior AI/ML Engineer
- 2 Senior Frontend Engineers (React/React Native)
- 2 Mid-level Backend Engineers
- 1 Mid-level QA Engineer
- 1 Engineering Manager (30% allocation)

**Total Team:** 6.3 FTE

**Engineering Cost:** €141,750

- Calculation: 6.3 FTE × €7,500/month average blended rate × 3 months

## Phase 4: Optimization & Scale

**Goal:** Prepare for 10x customer growth, enhance customer experience, and enable continuous improvement

### Deliverables:

- Performance optimization and load testing
- Route Optimizer Agent + Route Judge Agent for advanced travel planning
- Enhanced Mapping Tool with real-time traffic, weather, and incident data
- Dynamic re-routing capabilities and user correction workflows
- Advanced analytics dashboards
- Automated model retraining pipelines
- Cost optimization (LLM usage, infrastructure)

### Success Metrics:

- System Response Time: <2s average under load
- Revenue per Vehicle: +50% increase
- Daily Active Users: +200% growth (recurring commuters)

### Cost Estimate:

**Timeline:** 4 months

**Team Composition:**

- 1 Senior AI/ML Engineer
- 2 Senior Backend Engineers
- 1 Senior Frontend Engineer
- 1 Senior DevOps/Platform Engineer
- 1 Mid-level Data Engineer
- 1 Mid-level QA Engineer
- 1 Engineering Manager (30% allocation)

**Total Team:** 7.3 FTE

**Engineering Cost:** €219,000

- Calculation: 7.3 FTE × €7,500/month average blended rate × 4 months

## Total Program Cost Summary

**Total Timeline:** 17 months (with some phases running in parallel)

**Peak Team Size:** ~8 FTE (during Phase 3a)

**Total Engineering Investment:** €784,875

**Cost Breakdown by Phase:**

- Phase 1: €72,000 (9%)
- Phase 2: €118,125 (15%)
- Phase 3a: €234,000 (30%)
- Phase 3b: €141,750 (18%)
- Phase 4: €219,000 (28%)

**Key Assumptions:**

- Cost estimates calculated with AI assistance based on typical EU market rates
- Excludes infrastructure costs, third-party services, and corporate overhead
- Assumes co-located or hybrid team structure
- Phases 3a and 3b can run in parallel, reducing overall timeline from 17 to 13 months
