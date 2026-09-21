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

## WorkerBee Architecture

```text
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
