# Agent Security Decision Chain

**Version:** v0.1 — Experimental
**Author:** Gustavo O. / Okamoto Security Labs

The **Agent Security Decision Chain (ASDC)** is an open security model for reasoning about whether an autonomous AI agent action should be allowed to execute.

The model is intentionally simple:

**Origin → Context → Authority → Action → Decision**

AI security is becoming increasingly good at observing what agents do.

The harder problem is determining whether an action **should be allowed to happen at all**.

ASDC attempts to provide a common mental model for that decision.

## The Chain

### 1. Origin

**Who initiated the action?**

Examples:

* Human
* AI agent
* External content
* Another service or agent

Origin establishes the initial source of intent.

---

### 2. Context

**Why is the action happening?**

Context may include:

* Session state
* User instructions
* Agent memory
* External content
* Prompt or tool provenance
* Previous decisions

The same action can have completely different security implications depending on what influenced it.

---

### 3. Authority

**What is this agent actually allowed to do?**

Authority includes:

* Identity
* Permissions
* Delegated authority
* Scope
* Credentials
* Runtime policy

Possessing a capability does not automatically mean the agent should be permitted to exercise it in every context.

---

### 4. Action

**What is about to execute?**

Examples:

* Tool call
* Process execution
* File access
* Network request
* API call
* Credential use
* Infrastructure change

This is the boundary where reasoning becomes real-world execution.

---

### 5. Decision

**Should this action be allowed now?**

Possible outcomes include:

**ALLOW · DENY · CONSTRAIN · ESCALATE**

The decision should be informed by the entire chain rather than the action alone.

---

## Core Principle

> Detection tells us what happened.
> Agent security must decide what is allowed to happen next.

ASDC separates **observability** from **governability**.

Telemetry may explain an agent's behavior.

Runtime security determines whether that behavior should be permitted to continue.

## Runtime Evidence

Evidence supporting a decision may come from:

* Agent/session telemetry
* Identity systems
* Endpoint or kernel telemetry
* Tool-call traces
* Policy engines
* Network telemetry
* Provenance metadata

The framework does not prescribe a specific telemetry implementation.

## What ASDC Is Not

ASDC is not:

* an AI safety benchmark;
* a replacement for IAM;
* a detection framework;
* an agent protocol;
* a specific policy engine;
* a claim that every decision can be deterministic.

It is a model for reasoning about the security boundary between **agent intent and runtime execution**.

## Vortex DFS

[Vortex DFS](https://github.com/) is an independent experimental project exploring deterministic runtime security concepts related to parts of this decision chain.

ASDC does **not** depend on Vortex DFS.

The framework is intended to remain implementation-independent.

## Current Status

This is **v0.1**.

The model is being published early intentionally.

Rather than designing it in isolation, the goal is to let security engineers, researchers, platform engineers and AI practitioners challenge its assumptions.

Questions currently being explored include:

* Where should provenance live in the chain?
* How should delegated authority be represented?
* What evidence should invalidate trust?
* Can previous agent decisions change the authority of future actions?
* Which decisions should never depend on probabilistic reasoning?
* How should multi-agent delegation be represented?

## Feedback

If you think the model is wrong, incomplete or badly abstracted, open an issue.

Especially if you can break one of its assumptions.

That is the point.

---

**Agent Security Decision Chain — v0.1**
Okamoto Security Labs
