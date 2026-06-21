---
layout: Article
title: "2026-06-21: Vibe Coding to Agentic Engineering :  Collected lessons and reflections"
date: 2026-06-21
---
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']]
    }
  };
</script>

<script async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>





# Vibe Coding to Agentic Engineering :  Collected lessons and reflections

19 June, 2026 


Over the past week, I have been deeply engaged in learning, practicing, and experimenting with vibe coding and agentic engineering through a Google 5-day intensive program. This included live streams, hands-on codelabs, podcasts, and the study of relevant white papers.
It has been a valuable investment of time, especially given that this is not a retrospective topic from years past, but something actively unfolding in real time. We are witnessing, almost moment by moment, how these paradigms are reshaping the structure of software development, the broader technological landscape, and increasingly, our role within it as a society.
These reflections feel like personal notes and mental snapshots collected while navigating a rapidly expanding field—almost like observing the early waves of a much larger transformation still forming ahead of us.
In many ways, this feels like a leap into a new technological era, one that is unfolding faster than traditional development cycles can fully capture.
This article reflects my own simplified understanding of core concepts and techniques behind vibe coding and agentic engineering frameworks. It is intended as an accessible introduction for those interested in how these systems work. I will continue refining and expanding it over time with more detailed explanations.
At a high level, this is a brief summary of the key ideas and components that form the foundation of vibe coding and agentic engineering frameworks.

## A New Paradigm: From Code Writing to Intent Expression

A new paradigm in software development has emerged in which developers increasingly express what they want to build rather than how to build it. The system is responsible for implementation, while the human provides intent, architectural direction, and judgment.
This is no longer a future concept—it is already becoming the daily reality for a growing number of professional developers.
As of early 2026, approximately 85% of professional developers regularly use AI coding agents, with 51% using them daily, and an estimated 41% of newly written code being AI-generated (The New SDLC With Vibe Coding, white paper).

## Role Shift From Developer to Conductor / Orchestrator

Within modern software development, a structural shift is underway. The role of the developer is gradually moving away from directly producing syntax-level code and toward designing, supervising, and orchestrating systems that generate and manage that code.
This emerging discipline is often referred to as Agentic Engineering.
In this model, software is no longer purely written—it is co-produced through collaboration between humans and autonomous or semi-autonomous agents.
The “80% Problem”
A key challenge in agentic software development is commonly referred to as the 80% problem.
AI systems are often capable of generating approximately 80% of the code required to implement a feature described in natural language. However, the remaining 20%—which includes:

- edge cases
- error handling
- integration boundaries
- subtle correctness requirements
- long-term architectural consistency

requires deep contextual understanding that current systems still struggle to reliably capture.

Importantly, the nature of AI-generated errors has shifted. Instead of syntax-level mistakes, failures are now more often:

- incorrect assumptions
- missing edge cases
- failure to request clarification
- weak architectural decisions
- hidden maintainability issues
  
These issues are particularly challenging because the output often appears correct and may even pass basic tests, while still being structurally or conceptually flawed.
As a result, the developer’s role increasingly focuses on identifying and correcting what AI systems systematically miss.
As AI agents take on a larger share of implementation work, the role of the developer is evolving.
Rather than acting primarily as a code author, the developer increasingly functions as a conductor or orchestrator—guiding multiple systems, shaping intent, validating outputs, and ensuring alignment with broader architectural and product goals.
In this model, the developer is less concerned with writing every line of code and more focused on:

- defining system boundaries
- supervising agent behavior
- ensuring correctness under constraints
- integrating outputs into coherent systems
- 
This represents a shift from implementation work to system orchestration work.



                 Source: (The New SDLC With Vibe Coding, white paper)

## Vibe Coding to Agentic Engineering 

In vibe coding, developers primarily express intent in natural language—“what they want to build”—and rely on AI tools to generate working code quickly. The emphasis is on flow, experimentation, and rapid prototyping, often with minimal concern for strict structure or long-term system design.
Agentic engineering, however, takes this further. It moves from code generation to autonomous system execution, where AI agents not only write code but also:

- plan multi-step development tasks
- modify and coordinate across multiple files
- run tests in controlled environments
- debug and iterate on failures
- and even propose or submit pull requests
  
This transition marks a fundamental shift from prompting for code → to orchestrating agents that build and maintain systems
In essence, vibe coding is about expressing intent, while agentic engineering is about designing and supervising intelligent workflows that execute that intent end-to-end.

                    Source: (The New SDLC With Vibe Coding, white paper)

Agentic engineering is an emerging software development approach where AI agents are used not just as coding assistants, but as active participants in building, modifying, testing, and maintaining software systems.
Instead of a human writing most of the code line-by-line, the human defines intent, goals, constraints, and architecture, while AI agents handle much of the execution.

## Agent Development: Tools and Interoperability

Modern AI agent development has shifted toward terminal-native, composition-driven workflows where natural language interfaces are increasingly coupled with automated coding agents. This represents a departure from traditional SDK-heavy and console-based paradigms, replacing them with modular, runtime-adaptive systems.

## Key Concepts in Agent Systems

- Progressive Disclosure: hierarchical activation of context to reduce attention dilution.
- Context Window: bounded token capacity for model inference.
- Context Rot: degradation of reasoning performance due to accumulated irrelevant context.
- Shift-Left Agent Engineering: early-stage enforcement of validation, constraints, and structure prior to reasoning and tool execution.
- Trajectory Scoring: evaluation of agent performance across full execution traces rather than terminal outcomes. “Did it succeed efficiently and correctly step-by-step?”
     A trajectory = steps the agent takes:
         - thought → tool call → observation → next step → result
  
## Agent Skills

Agent Skills are modular execution units that inject task-specific behavioral policies into general-purpose agents at runtime. They function as lightweight representations of procedural memory, defining:
- reasoning patterns
- tool usage constraints
- context activation rules
  
In essence, Skills enable agents to dynamically adopt specialized behaviors without requiring separate architectures.

## Skill Anatomy and Progressive Disclosure

A Skill is a self-contained unit typically organized as a directory. The only mandatory component is:

        - SKILL.md
        
Additional files (scripts, tools, configurations) are optional and depend on implementation needs.
A canonical structure, as defined by the open standard at agentskills.io, illustrates how Skills can be packaged for portability and reuse. For example, a Skill may encapsulate workflows such as daily operational tasks (e.g., cafe preparation routines), combining instructions and tooling within a single modular boundary.



## Skill vs MCP

Skills and the Model Context Protocol (MCP) operate at orthogonal abstraction layers:

- MCP defines external system connectivity (data access, APIs, tools).
- Skills define internal execution logic and reasoning structure.
  
In execution flows, Skills act as policy layers that invoke MCP-connected tools when external state or computation is required.

## Skill vs AGENTS.md

AGENTS.md defines persistent system-level constraints and project conventions that remain globally active during execution.
Skills are dynamically activated modules triggered via contextual relevance detection.
A robust architecture combines both:

- AGENTS.md → static constraints and project invariants
- Skills → dynamic, task-specific execution policies

Skills are designed to mitigate key systemic limitations in LLM-based agent architectures:
 #### 1. Context Window Saturation and Context Rot
    Overloading system prompts with static instructions results in degraded attention allocation and reduced task fidelity. Skills address this by enabling on-demand context injection, minimizing persistent token overhead and reducing context interference.
#### 2.  Lack of Procedural Memory in LLMs
    While transformer-based models exhibit emergent episodic and semantic recall, they lack explicit procedural memory representation. Skills introduce a structured abstraction for encoding step-wise operational policies, effectively approximating reusable execution graphs.
#### 3. Multi-Agent System Overhead
    Conventional multi-agent architectures introduce coordination complexity, non-deterministic communication overhead, and maintenance challenges. Skills enable single-agent role multiplexing, allowing dynamic specialization without distributed system complexity.
#### 4. Cross-Platform Portability
    Skills are implemented as filesystem-native artifacts (e.g., Markdown + scripts), enabling deterministic portability across heterogeneous execution environments without vendor lock-in or runtime coupling.


## Open Interoperability Protocols

Agent systems increasingly rely on standardized protocols to enable composable multi-system interaction:
- MCP (Model Context Protocol): standardized tool and data connectivity layer.
- A2A (Agent-to-Agent): inter-agent communication and delegation protocol.
- A2UI (Agent-to-User Interface): structured rendering layer for safe UI generation.
- AP2 / UCP: transactional and commercial execution layers for autonomous systems.
- OpenResponses API: long-running inference interface bridging stateless and stateful execution.
  
Together, these protocols define a modular agent architecture where 

- Skills operate as execution logic, 
- MCP as connectivity, and 
- A2A/A2UI as coordination and presentation layers.
  
## Agent CLI Skills vs ADK

Agent development workflows involve repetitive lifecycle tasks such as:
- scaffolding project structures
- configuring runtime environments
- running prompt-based tests
- initializing evaluation loops
  
Instead of relying on unconstrained LLM generation for these tasks, Agent CLI Skills package encapsulate them as deterministic, reusable execution modules.
The Agent CLI layer provides operational primitives for local execution—enabling fast scaffolding, testing, and deployment with minimal overhead.
In contrast, the Agent Development Kit (ADK) defines the structural foundation of agent systems, providing:
- SDKs
- APIs
- orchestration primitives
  
Together, they form a two-layer architecture:

- CLI = execution runtime
- ADK = system design framework

