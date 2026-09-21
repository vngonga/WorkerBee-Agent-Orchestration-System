# WorkerBee Workflow

This document describes the end-to-end execution workflow of the
WorkerBee multi-agent orchestration system, from the Keeper's initial
request through planning, execution, quality review, human oversight,
and final delivery.


## Workflow Overview

WorkerBee follows a structured multi-agent workflow.

A human operator, called the **Keeper**, submits a request. The request
is analyzed by **HIVEMIND**, which determines the project requirements,
identifies questions or constraints, and creates a structured task plan.

The plan is divided into layers containing tasks assigned to specialized
Bee agents.

Tasks within a layer can execute in parallel, while layers execute
sequentially.

Throughout execution, WorkerBee supports self-critique, quality review,
revision, coordination, human decision gates, and mid-flight steering.

When the workflow is complete, HIVEMIND synthesizes the project artifacts
and WorkerBee compiles the final deliverable.

## End-to-End Workflow

```text
KEEPER REQUEST
      |
      v
HIVEMIND READ
      |
      v
CLARIFICATION
(if required)
      |
      v
HIVEMIND PLAN
      |
      v
DAG CREATED
      |
      v
PLAN DISPATCHED
      |
      v
TASK EXECUTION
      |
      v
SELF-CRITIQUE
      |
      v
QUALITY REVIEW
      |
      +---- Revision Required ----+
      |                           |
      |                           v
      |                       REDO TASK
      |                           |
      +---------------------------+
      |
      v
LAYER COORDINATION
      |
      v
NEXT LAYER
      |
      v
HUMAN GATE
(if required)
      |
      v
HIVEMIND SYNTHESIS
      |
      v
DELIVERABLE COMPILATION
      |
      v
FINAL DELIVERABLE
      |
      v
POST-DELIVERY CHANGES
(if requested)
```

## 1. Keeper Intake

The workflow begins when the **Keeper** submits a project request.

The intake provides the initial context that WorkerBee needs to
understand the requested work.

The Keeper serves as the human operator throughout the workflow and
can continue providing direction as the project progresses.
```text
Keeper
   |
   | Project Request
   v
WorkerBee
```
---

## 2. HIVEMIND Read

After intake, HIVEMIND analyzes the Keeper's request.

During this phase, HIVEMIND identifies important information such as:

- Project goal
- Constraints
- Open questions
- Risks
- Out-of-scope items
- Estimated execution considerations

The purpose of this phase is to understand the request before
creating the execution plan.

```text
Keeper Request
      |
      v
   HIVEMIND
      |
      v
Request Analysis
```
---

## 3. Clarification

If important information is missing or ambiguous, WorkerBee can
request clarification from the Keeper before execution continues.

The Keeper answers the clarification questions, and those answers
become additional project context or constraints.
```text
HIVEMIND
    |
    v
Clarification Question
    |
    v
  Keeper
    |
    v
Answer / Constraint
    |
    v
HIVEMIND
```
---

## 4. HIVEMIND Planning

After the request has been understood, HIVEMIND creates the project plan.

The plan organizes the project into:

- Layers
- Tasks
- Dependencies
- Assigned Bee roles
- Expected outputs

WorkerBee uses a Directed Acyclic Graph (DAG) to represent the
execution structure.

                HIVEMIND
                    |
                    v
               PROJECT PLAN
                    |
         +----------+----------+
         |          |          |
         v          v          v
       Task 1     Task 2     Task 3


---

## 5. Plan Dispatch

After HIVEMIND creates the plan, WorkerBee dispatches the plan for
execution.

The planned layers and tasks are materialized, and work is assigned
to the appropriate specialized Bee roles.

Bee instances receive call signs that help identify them during the run.

Examples include:
```text
RYE-01
AXEL-01
CLOVER-01
QUINN-01
NOVA-01
```
---

## 6. Layer and Task Execution

WorkerBee executes the project one layer at a time.

Within the active layer, multiple tasks can run in parallel.

For example:

                 ACTIVE LAYER
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
        RYE-01      AXEL-01     NOVA-01
       Research     Analysis   Innovation
          |           |           |
          v           v           v
      Artifact A   Artifact B   Artifact C

    
---

## 7. Individual Task Workflow

A task can pass through several internal stages during execution.

A simplified task flow is:
```text
Task Assigned
     |
     v
Control Check
     |
     v
Thinking / Planning
     |
     v
Optional Research or Tool Use
     |
     v
Step Planning
     |
     v
Drafting
     |
     v
Artifact Created
     |
     v
Post-Draft Review
```

Your documentation identifies control checks, thinking, optional web research, deterministic step planning, drafting, artifact creation, and post-draft QA/self-critique as parts of task execution. :contentReference[oaicite:5]{index=5}

---

## 8. Self-Critique

After producing a draft artifact, non-Quality Bees can evaluate
their own work.

The self-critique process can result in three outcomes:

| Outcome | Meaning |
|---|---|
| **Ship** | The artifact is ready to continue through the workflow |
| **Revise** | The artifact needs specific improvements |
| **Escalate** | Human input is needed to resolve an important issue |

A revision can return the task for another attempt.

WorkerBee limits automatic revision cycles to prevent endless
self-revision loops.

## 9. Quality Review

Quality review provides an additional evaluation layer.

The **Quality Bee (QUINN)** can review artifacts produced by upstream
agents and identify issues that require correction.

A simplified QA flow is:
```text
Artifact
   |
   v
 QUINN
   |
   v
QA Review
   |
   +------------------+
   |                  |
   v                  v
 PASS              REVISE
   |                  |
   v                  v
Continue          Redo Task
                      |
                      v
                  Re-evaluate

```
---

## 10. Layer Coordination

After a layer completes, **CORA**, the Coordinator Bee, helps
prepare the workflow for the next layer.

CORA can:

- Review completed layer outputs
- Synthesize important findings
- Identify information needed downstream
- Create handoff directives
- Support continuity between layers

```text
Completed Layer
      |
      v
     CORA
      |
      v
Layer Synthesis
      |
      v
Handoff Instructions
      |
      v
Next Layer
```
---

## 11. Human Decision Gates

Some decisions should not be made automatically by the AI agents.

WorkerBee can create a **Gate** when human judgment is required.
```text
WorkerBee
    |
    v
Decision Gate
    |
    v
  Keeper
    |
    +------ Approve
    |
    +------ Reject
    |
    +------ Provide Direction
```
---

## 12. Mid-Flight Steering

The Keeper does not have to wait until the workflow finishes to
provide new instructions.

During execution, the Keeper can send a natural-language directive.

The Coordinator can interpret the instruction and translate it into
an action such as:

- Requeue a task
- Skip a task
- Raise a decision gate
- Record a note
- Add a new project constraint
```text
        WORKFLOW RUNNING
              |
              v
        Keeper Directive
              |
              v
             CORA
              |
       Interpret Request
              |
      +-------+-------+
      |       |       |
      v       v       v
   Requeue   Skip    Gate
      |
      v
Updated Workflow
```
---

## 13. Agent-to-Agent Messaging

WorkerBee allows agents to communicate during execution.

A Bee can request information from another Bee when additional
context is needed.

Messages can be routed by:

- Exact call sign
- Agent role or family
- General broadcast
```text
RYE-01
   |
   | Message
   v
AXEL-01
   |
   | Response
   v
RYE-01
```
---

## 14. Task and Project Control

WorkerBee provides controls for managing execution while a project
is running.

Supported controls include:

- Pause project
- Resume project
- Pause task
- Resume task
- Skip task
- Cancel task
- Abort in-flight AI work

These controls give the Keeper additional oversight of active execution.

## 15. Stall Recovery

WorkerBee includes mechanisms for handling situations where execution
cannot continue normally.

When progress stalls, the system can identify the blocked state and
support recovery actions rather than allowing the workflow to remain
indefinitely unresolved.

This contributes to the reliability of long-running multi-agent workflows.

## 16. HIVEMIND Final Synthesis

After the required execution layers are completed, HIVEMIND performs
final synthesis.

HIVEMIND uses the completed project artifacts and workflow context
to organize the results into a coherent final output.
```text
Research Artifacts
        +
Analysis Artifacts
        +
Content Artifacts
        +
Quality Findings
        |
        v
     HIVEMIND
        |
        v
Final Synthesis
```
---

## 17. Deliverable Compilation

After synthesis, WorkerBee compiles the final deliverable.

The final output represents the result of the coordinated work performed
across the project's agents, layers, reviews, revisions, and human
decision points.
```text
HIVEMIND Synthesis
        |
        v
Deliverable Compilation
        |
        v
FINAL DELIVERABLE
        |
        v
      Keeper
```
---

## 18. Post-Delivery Change Requests

After receiving the final deliverable, the Keeper can request
additional changes.

This allows the workflow to continue when revisions or additional
work are needed after delivery.
```text
Final Deliverable
       |
       v
     Keeper
       |
       v
Change Request
       |
       v
WorkerBee
       |
       v
Updated Deliverable
```
---

## Operating Modes

WorkerBee supports multiple operating modes that influence how
the workflow is structured.

### Content Mode

Designed for general knowledge-work deliverables.

A typical pattern may include:
```text
Research
   |
Analysis
   |
Content
   |
Quality
   |
Synthesis
```
---

## Complete Workflow Summary
```text
1.  Keeper submits request
             |
             v
2.  HIVEMIND reads request
             |
             v
3.  Clarification if needed
             |
             v
4.  HIVEMIND creates DAG
             |
             v
5.  Plan is dispatched
             |
             v
6.  Specialized Bees execute tasks
             |
             v
7.  Artifacts are created
             |
             v
8.  Agents perform self-critique
             |
             v
9.  Quality review is performed
             |
             v
10. Revisions occur when necessary
             |
             v
11. CORA coordinates layer handoff
             |
             v
12. Next layer executes
             |
             v
13. Keeper handles gates when required
             |
             v
14. HIVEMIND performs final synthesis
             |
             v
15. Deliverable is compiled
             |
             v
16. Keeper receives final deliverable
             |
             v
17. Post-delivery changes can be requested
```
---

