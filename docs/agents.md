# WorkerBee Agents

This document describes the specialized AI agents used
within the WorkerBee orchestration system.


## Agent Overview

WorkerBee uses a collection of specialized AI agents, called **Bees**,
to perform different types of work within a coordinated workflow.

Rather than assigning every responsibility to a single AI agent,
WorkerBee separates work across agents with specialized roles.

The primary agent families are:

- HIVEMIND - Strategic orchestration
- CORA - Coordination
- RYE - Research
- AXEL - Analysis
- CLOVER - Content
- QUINN - Quality
- NOVA - Innovation

Each Bee receives a specific task, role, context, and instructions
based on the project plan created by HIVEMIND.

## Agent Summary

| Agent | Call Sign Family | Primary Role |
|---|---|---|
| **HIVEMIND** | HIVEMIND | Strategic orchestration and final synthesis |
| **Coordinator Bee** | CORA | Layer coordination and handoffs |
| **Research Bee** | RYE | Research and source gathering |
| **Analysis Bee** | AXEL | Analysis, structure, and frameworks |
| **Content Bee** | CLOVER | Content and deliverable creation |
| **Quality Bee** | QUINN | Quality review and auditing |
| **Innovation Bee** | NOVA | Creative alternatives and innovation |

## HIVEMIND - Strategic Orchestrator

### Purpose

HIVEMIND serves as the strategic meta-agent within WorkerBee.

It interprets the Keeper's request, determines how the work should
be structured, creates the project plan, and synthesizes the final
deliverable.

### Key Responsibilities

- Read and interpret the Keeper's request
- Identify project goals and constraints
- Identify open questions and risks
- Generate clarification questions when needed
- Create the task DAG
- Organize tasks into layers
- Assign tasks to specialized Bee roles
- Frame decision gates for the Keeper
- Synthesize completed work
- Support final deliverable generation

### Position in the Workflow

Keeper
   |
   v
HIVEMIND
   |
   v
Project Plan / DAG
   |
   v
Specialized Bees
   |
   v
HIVEMIND
   |
   v
Final Synthesis

---

## CORA - Coordinator Bee

### Purpose

CORA coordinates work between execution layers.

After a layer of tasks is completed, CORA reviews the outputs and
creates handoff instructions for the next layer.

### Key Responsibilities

- Review completed layer outputs
- Synthesize important findings
- Coordinate transitions between layers
- Create handoff directives
- Support workflow continuity
- Interpret Keeper steering instructions
- Help determine how active work should be redirected

### Example

Research Layer Completed
        |
        v
       CORA
        |
        v
Synthesizes Findings
        |
        v
Creates Handoff
        |
        v
Next Layer Begins

---

## RYE - Research Bee

### Purpose

RYE is the Research Bee.

It is responsible for research-oriented tasks within the WorkerBee
workflow.

### Key Responsibilities

- Gather relevant information
- Identify useful sources
- Support evidence-based outputs
- Collect research needed by downstream agents
- Organize research findings for later analysis or content development

### Typical Workflow

Research Task
     |
     v
    RYE
     |
     v
Research Artifact
     |
     v
Analysis / Content / Quality

---

## AXEL - Analysis Bee

### Purpose

AXEL is the Analysis Bee.

It focuses on analytical tasks that require information to be
organized, compared, structured, or evaluated.

### Key Responsibilities

- Analyze research findings
- Structure complex information
- Develop analytical frameworks
- Create matrices and comparisons
- Identify patterns and relationships
- Prepare structured findings for downstream agents

### Typical Workflow

Research Artifacts
       |
       v
      AXEL
       |
       v
Structured Analysis
       |
       v
Content / Quality / Synthesis

---

## CLOVER - Content Bee

### Purpose

CLOVER is the Content Bee.

It transforms project requirements, research, analysis, and other
upstream artifacts into written deliverables.

### Key Responsibilities

- Draft content
- Transform research into readable material
- Follow project requirements and constraints
- Incorporate upstream findings
- Produce content artifacts for review
- Revise content when quality issues are identified

### Typical Workflow

Research + Analysis
        |
        v
      CLOVER
        |
        v
Content Artifact
        |
        v
Quality Review

---

## QUINN - Quality Bee

### Purpose

QUINN is the Quality Bee.

It evaluates artifacts created by other agents and identifies
issues that may require revision.

### Key Responsibilities

- Review upstream artifacts
- Evaluate output quality
- Identify material issues
- Produce structured QA findings
- Provide revision directives
- Support quality gates
- Escalate unresolved quality concerns when necessary

### Quality Review Flow

Artifact
   |
   v
 QUINN
   |
   v
Quality Review
   |
   +----------+
   |          |
 PASS       REVISE
   |          |
   v          v
Continue    Redo Task
              |
              v
          Review Again


---

## NOVA - Innovation Bee

### Purpose

NOVA is the Innovation Bee.

It supports tasks that benefit from creative alternatives,
new approaches, or innovative variants.

### Key Responsibilities

- Explore alternative approaches
- Generate creative options
- Develop innovative variants
- Support ideation
- Contribute alternatives for consideration by other agents

## Bee Call Signs

Each Bee instance receives a unique call sign during a project run.

The call sign identifies both the agent family and the specific
instance of that agent.

Examples:

RYE-01
AXEL-01
CLOVER-01
QUINN-01
NOVA-01

---

## Agent Collaboration

WorkerBee agents are designed to operate as part of a coordinated
workflow rather than as isolated AI assistants.

A simplified collaboration pattern is:

                 HIVEMIND
                     |
                     v
              Creates DAG Plan
                     |
        +------------+------------+
        |            |            |
        v            v            v
       RYE          AXEL        NOVA
    Research      Analysis    Innovation
        |            |            |
        +------------+------------+
                     |
                     v
                   CORA
               Coordination
                     |
                     v
                  CLOVER
                  Content
                     |
                     v
                   QUINN
                   Quality
                     |
                     v
                 HIVEMIND
                  Synthesis


---

## Agent-to-Agent Communication

WorkerBee supports peer communication between agents.

During execution, a Bee can request information from another Bee
when additional context or expertise is needed.

Messages can be routed using:

- Exact Bee call sign
- Agent role or family
- General broadcast

Responses can then be incorporated into the requesting agent's work.

This allows specialized agents to exchange information without
requiring every interaction to pass directly through the Keeper.

## Agent Self-Critique

WorkerBee includes a self-critique process for non-Quality Bees.

After creating a draft artifact, the Bee can evaluate its own work
and determine whether the output should:

- **Ship** - The artifact is ready to continue through the workflow.
- **Revise** - Specific improvements should be made.
- **Escalate** - Human input is needed to resolve an important decision.

Self-critique creates an additional review step before artifacts
move further through the workflow.

## Human and Agent Relationship

WorkerBee is designed as a human-in-the-loop system.

The AI agents perform specialized work, but the Keeper remains
responsible for important human decisions.

             HUMAN KEEPER
                  |
          Direction / Review
                  |
                  v
              HIVEMIND
                  |
            Coordination
                  |
                  v
        SPECIALIZED AI BEES
                  |
             Artifacts
                  |
                  v
         Quality / Escalation
                  |
                  v
             HUMAN KEEPER

---

## Quick Reference

| Need | WorkerBee Agent |
|---|---|
| Strategic planning | HIVEMIND |
| Layer coordination | CORA |
| Research | RYE |
| Analysis | AXEL |
| Content creation | CLOVER |
| Quality review | QUINN |
| Innovation | NOVA |
| Human direction and approval | Keeper |


