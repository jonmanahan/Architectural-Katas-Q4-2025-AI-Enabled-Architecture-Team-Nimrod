---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Data Science Team]
informed: [Engineering and Product Teams]
---

# Google OR-Tools for Vehicle Redistribution Optimization

## Context and Problem Statement

Our operations team needs to efficiently redistribute electric bikes and scooters from low-demand zones to high-demand zones throughout the day. Operations staff with cargo vans must decide which vehicles to pick up from which locations and where to drop them off to maximize fleet utilization and minimize customer wait times. The redistribution problem has multiple constraints including vehicle capacity limits, travel time between zones, time windows for operations, and varying demand patterns by location. How should we determine the optimal redistribution routes and assignments for our operations team?

Key optimization requirements:
- Determine which bikes and scooters to move from low to high demand zones
- Minimize total travel distance and time for operations staff
- Respect cargo van capacity constraints
- Complete redistribution within operational time windows
- Balance fleet across zones to meet forecasted demand
- Provide actionable routes for operations staff to follow
- Update recommendations in near real-time as conditions change

## Considered Options

* Option 1: Machine Learning Approach Reinforcement Learning
* Option 2: Algorithmic Solver with Open Source Tool: Google OR-Tools
* Option 3: Algorithmic Solver with Commercial Tool: Gurobi

## Decision Outcome

Chosen option: "Option 2: Algorithmic Solver with Open Source Tool: Google OR-Tools", because it provides mathematically great solutions for vehicle routing problems, is specifically designed for logistics optimization, offers free and open-source licensing, and includes proven algorithms for capacitated vehicle routing with time windows. While commercial solvers like Gurobi may be faster for very large instances, OR-Tools provides excellent performance for typical fleet sizes and is easier to deploy without licensing costs.

## Consequences

### Option 1: Machine Learning Approach with RL

* Good, because it can potentially learn complex decision patterns and adapt to changing operational constraints without explicit programming
* Good, because it can handle objectives that are difficult to formalize mathematically
* Good, because it can potentially generalize across different cities and fleet configurations with transfer learning
* Good, because it can incorporate real-time feedback and improve performance over time through continuous learning

* Bad, because it requires extensive training data covering diverse scenarios and may take weeks or months to train effectively
* Bad, because solutions are not guaranteed to be optimal or even near-optimal
* Bad, because it's a black box making it difficult to debug poor decisions or explain routing choices to operations staff
* Bad, because it requires significant ML infrastructure, expertise, and computational resources for training and inference
* Bad, because convergence is uncertain and model may produce inconsistent or unpredictable recommendations that operations teams won't trust

### Option 2: Algorithmic Solver with Google OR-Tools

* Good, because it provides provably optimal or near-optimal solutions using established vehicle routing algorithms 
* Good, because it's free and open source
* Good, because it's specifically designed for routing and scheduling problems with excellent documentation
* Good, because solutions are explainable and deterministic
* Good, because it handles complex constraints naturally including capacity, time windows, distance limits, and multiple locations

* Bad, because it may have slower solve times than commercial solvers like Gurobi for very large instances
* Bad, because it requires operations research expertise to properly formulate the problem and tune solver parameters
* Bad, because finding optimal solutions can be computationally expensive for large problems, may need to accept good-enough solutions with time limits
* Bad, because it's less flexible than ML for incorporating fuzzy or learned preferences that are hard to express as constraints
* Bad, because model updates require code changes rather than simply retraining with new data

### Option 3: Algorithmic Solver with Gurobi (commercial solver)

* Good, because it provides best in class solving speed and can handle very large routing problems efficiently
* Good, because it offers comprehensive support, documentation, and proven performance in enterprise logistics applications
* Good, because it can find optimal solutions faster than open-source alternatives, reducing computational costs for complex problems

* Bad, because it requires expensive commercial licenses
* Bad, because licensing restrictions may limit deployment options, number of users, or computational resources
* Bad, because it has a steeper learning curve compared to OR-Tools
* Bad, because vendor lock-in creates dependency on single commercial provider with potential price increases or discontinuation


## Related Documentation

* [Google OR-Tools Routing Library](https://developers.google.com/optimization/routing)
* [Vehicle Routing Problem with Time Windows](https://en.wikipedia.org/wiki/Vehicle_routing_problem)
* [OR-Tools CVRPTW Examples](https://github.com/google/or-tools/tree/stable/examples/python)
* [Gurobi Vehicle Routing](https://www.gurobi.com/resource/vehicle-routing-problem/)