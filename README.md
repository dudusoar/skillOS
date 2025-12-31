# SkillOS

**SkillOS** is a personal operating system for AI skills.

It explores how *skills*—as introduced by Anthropic—can be created, contextualized, evolved, and governed across projects, rather than treated as static, one-off artifacts.

This repository is an experiment, not a framework.

---

## Motivation

Anthropic skills provide a powerful abstraction:  
they package procedural knowledge, domain expertise, and reusable resources into modular units that extend an AI agent’s capabilities.

However, in practice, skills are:

- **Static**: designed once, manually updated, and reused as-is  
- **Isolated**: selected and invoked individually, without explicit coordination  
- **Project-blind**: lacking mechanisms to absorb project-specific experience and feed it back into general knowledge  

For individual researchers and engineers who work across many projects, this raises a question:

> What if skills were treated not as frozen artifacts, but as *living units* that evolve through use?

SkillOS is a concrete attempt to explore that question.

---

## Core Idea

SkillOS treats skills as first-class entities in a personal system with:

- **Lifecycle**: creation → use → adaptation → abstraction → reuse  
- **Context-awareness**: separation between general skill knowledge and project-specific context  
- **Governance**: explicit rules for how skills are updated, composed, and refined  
- **Meta-skills**: skills that operate *on other skills* (e.g., context generation, extraction, updating)

In other words:

> Skills become *capabilities*, and SkillOS becomes the system that manages them.

---

## Design Principles

### 1. Build *on top of* existing skill abstractions

SkillOS is inspired by Anthropic’s official skill format and design philosophy:

- `SKILL.md` as the canonical interface  
- Progressive disclosure to respect the context window  
- Scripts, references, and assets as bundled resources  

SkillOS does **not** replace this model—it extends it with additional structure and process.

---

### 2. Separate **general knowledge** from **project context**

Every skill conceptually consists of two layers:

- **General layer**  
  Reusable workflows, scripts, references, and heuristics that are stable across projects.
- **Project layer**  
  Injected context such as repo structure, schemas, constraints, naming conventions, and goals.

SkillOS makes this separation explicit and operational.

---

### 3. Make evolution explicit and governed

Instead of ad-hoc edits, SkillOS favors:

- Declared **contracts** inside each skill (what may change, what must remain stable)  
- **Meta-skills** that handle updating, extraction, and refinement  
- Controlled feedback from project experience into general skill knowledge  

The goal is not automation for its own sake, but *cognitive leverage* over time.

---

### 4. Prefer small, composable steps over monolithic intelligence

SkillOS assumes:

- The model is already intelligent  
- The bottleneck is not reasoning, but **structure**  
- Good systems reduce ambiguity and cognitive load  

Skills should be concise, opinionated where necessary, and composable where possible.

---

## What This Repository Is (and Is Not)

**This repo is:**

- A personal knowledge and capability system  
- A design space exploration  
- A discussion artifact meant to invite feedback and alternative viewpoints  

**This repo is not:**

- An official Anthropic extension  
- A production-ready framework  
- A general-purpose SaaS or agent platform  

---

## Current Status

SkillOS is at an early, exploratory stage.

The initial focus is on:

- Defining minimal conventions for skills and meta-skills  
- Designing a clean separation between general skills and project context  
- Using real projects to stress-test the ideas  

Expect incomplete pieces, iteration, and changes.

---

## Why Share This Publicly

This repository is shared to:

- Think more clearly by making assumptions explicit  
- Invite critique from others working with AI skills, agents, and tooling  
- Explore whether this way of organizing AI capabilities resonates beyond a single workflow  

If you find the ideas interesting—or flawed—I would welcome discussion.

---

## License & Use

This repository is primarily a research and exploration artifact.

Use, adapt, or ignore any part of it as you see fit.

---

*SkillOS is an ongoing experiment. The most important part is the thinking, not the code.*
