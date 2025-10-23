---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Platform Team, Customer Team, Operations Team, Data Science Team]
informed: [Leadership and Product Teams]
---

# Pydantic AI for our Agentic Framework Foundation

## Context and Problem Statement

MobilityCorp needs a GenAI agentic framework to build production level AI workflows that for operations work dispatch and customer travel support. These applications will interact with external APIs, databases, and other services to accomplish multi-step tasks. We require a framework that supports rigorous testing and evaluation, provides comprehensive monitoring and observability, allows easy switching between different LLM providers, and enables type-safe development to catch errors early. How should we select an agentic framework that balances development velocity, production reliability, and maintainability?

Key requirements:
- Eval support: Systematic testing of agent behavior with deterministic and LLM-based evaluators
- Observability: Real-time debugging, performance tracking, cost monitoring, and tracing
- Model pluggability: Easy switching between LLM providers like Claude, Gemini, and OpenAI models without code rewrites

## Considered Options

* Option 1: Pydantic AI
* Option 2: LangGraph
* Option 3: CrewAI

## Decision Outcome

Chosen option: "Option 1: Pydantic AI", because it provides the most comprehensive evaluation framework with built in Pydantic Evals, seamless observability through Pydantic Logfire with OpenTelemetry integration, true model-agnostic architecture supporting all major LLM providers, and industry-leading type safety leveraging Pydantic's validation. While LangGraph offers powerful graph-based workflows and CrewAI simplifies role-based collaboration, Pydantic AI's focus on testing, monitoring, and type safety makes it the best choice for building reliable production systems.

## Consequences

### Option 1: Pydantic AI

* Good, because it comes with a built-in evaluation framework that makes testing agents straightforward
* Good, because monitoring is baked in through Logfire integration
* Good, because switching between LLMs is easy
* Good, because it catches bugs before runtime with strong type checking

* Bad, because it's relatively newer with less examples
* Bad, because it doesn't have as many pre-built patterns for complex multiagent configs
* Bad, because fewer third-party integrations 

### Option 2: LangGraph

* Good, because you get graph-based workflows that handle complex agent patterns
* Good, because it has the biggest ecosystem thanks to LangChain
* Good, because LangGraph Platform offers managed deployment
* Good, because you get fine-grained control
* Good, because memory and state management is robust with session tracking

* Bad, because testing and evaluation aren't built in and you need to wire up separate tools or pay for LangSmith
* Bad, because monitoring requires either external platforms or the paid LangSmith service instead of being included
* Bad, because the graph approach is overkill for simple agents and has a steep learning curve
* Bad, because type safety is weaker so you'll catch fewer errors during development
* Bad, because switching models means navigating LangChain's abstraction layer

### Option 3: CrewAI

* Good, because the role based approach is intuitive and you define agents like team members with specific jobs
* Good, because you can build collaborative agents really quickly with minimal boilerplate code
* Good, because the API is clean and readable, making it easy for new developers to understand what's happening
* Good, because memory management for agents coordinating together works well out of the box
* Good, because it makes the common patterns easy by being opinionated about how multi-agent systems should work

* Bad, because there's basically no built-in evaluation framework for systematically testing your agents
* Bad, because lack monitoring and logging support makes debugging painful
* Bad, because its harder to switch models
* Bad, because there's minimal type safety 
* Bad, because it's optimized for simple team workflows and struggles when you need complex control flow or edge case handling

## Related Documentation

* [Pydantic AI Documentation](https://ai.pydantic.dev/)
* [Pydantic Evals Framework](https://ai.pydantic.dev/evals/)
* [Pydantic Logfire](https://pydantic.dev/logfire)
* [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
* [CrewAI Documentation](https://docs.crewai.com/)