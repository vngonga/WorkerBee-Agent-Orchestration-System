# 🐝 WorkerBee Agent Orchestration System

## Project Overview

WorkerBee is a layered, parallel multi-agent AI orchestration system
developed as part of the University of Utah MSIS Capstone Project.

The system is designed to break complex work into smaller tasks,
assign those tasks to specialized AI agents, coordinate their execution,
evaluate the quality of their outputs, and maintain human oversight
throughout the workflow.

WorkerBee was explored through Apiary by HIVE Labs as a way to demonstrate
how multiple specialized AI agents can collaborate on complex knowledge-work
tasks.

---

## Problem Statement

Complex AI-assisted work often involves multiple activities such as
research, analysis, content creation, quality assurance, and coordination.

A single AI agent may be asked to perform all of these responsibilities at
once. WorkerBee explores a different approach by decomposing complex work
into specialized tasks and assigning those tasks to agents with specific
roles.

The goal is to create a structured workflow in which AI agents collaborate
while a human operator remains involved in important decisions.

---

## How WorkerBee Works

A human operator, called the **Keeper**, submits a work request.

**HIVEMIND**, the strategic orchestrator, interprets the request and creates
a Directed Acyclic Graph (DAG) of tasks.

The tasks are assigned to specialized Bee agents. Tasks within the same
layer can run in parallel, while layers execute sequentially.

After each layer, **CORA**, the Coordinator Bee, synthesizes the results and
provides instructions for the next layer.

Quality review, self-critique, revision, escalation, and human decision
points are incorporated throughout the workflow.

The Keeper can also provide instructions while the workflow is running.

---

## Specialized AI Agents

| Agent | Role | Primary Responsibility |
|---|---|---|
| **HIVEMIND** | Strategic Orchestrator | Plans tasks and synthesizes the final deliverable |
| **CORA** | Coordinator | Coordinates layers and manages handoffs |
| **RYE** | Research | Gathers and validates sources |
| **AXEL** | Analysis | Structures information and develops frameworks |
| **CLOVER** | Content | Creates written deliverables |
| **QUINN** | Quality | Reviews and evaluates output quality |
| **NOVA** | Innovation | Develops creative alternatives |

## WorkerBee Architecture


                     KEEPER
                Human Operator
                      |
                      v
                  HIVEMIND
              Strategic Planner
                      |
                      v
                   DAG Plan
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
         RYE         AXEL       CLOVER
       Research     Analysis     Content
          |           |           |
          +-----------+-----------+
                      |
                      v
                    CORA
                 Coordinator
                      |
                      v
                   QUINN
               Quality Review
                      |
                Pass / Revise
                      |
                      v
                  HIVEMIND
                   Synthesis
                      |
                      v
              FINAL DELIVERABLE

---

## Core Features

- Multi-agent AI orchestration
- DAG-based task planning
- Specialized AI agent roles
- Parallel task execution
- Sequential workflow layers
- Human-in-the-loop decision making
- Self-critique and revision cycles
- Quality assurance and quality gates
- Agent-to-agent communication
- Mid-flight human steering
- Artifact lineage and revision history
- Automated deliverable compilation


## Technology Stack

The documented WorkerBee implementation uses:

- TypeScript
- React
- TanStack Start
- Supabase
- Lovable AI Gateway
- Large Language Models
- Multi-Agent AI Orchestration

## My Contributions

As a member of the MSIS Capstone team, my contributions included:

- Researched multi-agent AI workflows and specialized agent roles.
- Contributed to AI agent persona and prompt development.
- Contributed to Quality, Innovation, and Coordination agent concepts.
- Researched AI self-critique and quality evaluation approaches.
- Researched curriculum alignment involving PLOs, CLOs, and MLOs.
- Studied human annotation and gold-standard evaluation approaches.
- Supported human-in-the-loop AI workflow documentation.
- Participated in project discovery and requirements discussions.
- Contributed to project documentation and presentation development.
- Helped connect WorkerBee research to institutional use cases.


## What I Learned

This project strengthened my understanding of:

- Multi-agent AI systems
- AI orchestration
- Prompt engineering
- Human-in-the-loop AI
- AI quality evaluation
- Workflow design
- Requirements analysis
- Technical documentation
- Research and analysis
- Team collaboration

## Documentation

Additional project documentation is organized in this repository:

- `docs/architecture.md` - WorkerBee system architecture
- `docs/agents.md` - Specialized Bee agents and responsibilities
- `docs/workflow.md` - End-to-end execution workflow
- `docs/evaluation.md` - Quality assurance and evaluation approach
- `diagrams/` - Architecture and workflow diagrams
- `examples/` - Example WorkerBee workflows
- `research/` - Research findings and lessons learned

## Future Work

Potential areas for continued exploration include:

- Evaluating AI agent output against human-created benchmarks
- Improving quality-assurance reliability
- Studying self-critique and revision effectiveness
- Improving routing and orchestration strategies
- Expanding human-in-the-loop governance
- Evaluating specialized models for different agent roles

## Project Context

**Program:** Master of Science in Information Systems (MSIS)  
**Institution:** University of Utah  
**Project:** MSIS Capstone Project  
**System:** WorkerBee Agent Orchestration System  
**Prototype:** Apiary  
**Project Environment:** HIVE Labs

