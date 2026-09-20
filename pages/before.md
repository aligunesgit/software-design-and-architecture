# Introduction

Welcome to **Software Design and Architecture**! This repository holds everything for the course:
lecture notes, exercises, and further reading. I won't pretend you'll walk out a senior architect
twelve weeks from now, but I will promise something more useful: you'll leave knowing the
vocabulary, the principles, and the classic patterns well enough to recognize them in a real
codebase, and to make a deliberate architectural decision instead of an accidental one.

## What is software architecture?

*Software architecture* is the set of decisions about a system's structure that are expensive to
change later: how it's decomposed into components, how those components communicate, and which
quality attributes (performance, security, maintainability, and the rest) that structure trades
off against each other. *Software design*, by contrast, usually refers to the smaller-scale
decisions inside one component: which classes exist, how they collaborate, which pattern fits a
specific problem. This course covers both, moving from the small scale (Modules 1-4) to the large
scale (Modules 5-9), because a good architecture built from badly designed components still fails,
and well-designed components with no coherent architecture around them still don't add up to a
working system.

A useful way to think about the relationship: design decisions are the ones you can usually change
in an afternoon by editing a class. Architectural decisions are the ones you'd need a migration
plan for. This course is largely about learning to tell the two apart *before* a decision becomes
expensive.

## How this course is organized

The course runs across 12 weeks: 10 content modules (one per week) covering the principles,
patterns, and practices of software design and architecture, plus two dedicated project sprints
(Week 6 and Week 12) for applying everything to your own group project. See the
[time plan](timeplan.md) for the full week-by-week breakdown and the [projects page](projects.md)
for how the group project and grading work.

Think of this course as a toolbox, not a certification. You will not leave as an expert in every
single pattern or style covered. The goal is that you leave knowing *what exists* and *when to
reach for it*, so that when a real project calls for one of these tools you know where to start,
and just as importantly, when a pattern is the wrong tool and adding it would only add complexity.

## Prerequisites

To get the most out of this course, you should have prior experience with:

* At least 1 year of general programming experience, comfortable reading and writing
  object-oriented code
* Basic data structures and algorithms
* Some exposure to a statically-typed or strongly-typed language is helpful but not required;
  every code example in this course is in Python, chosen for readability, not because production
  architecture work is Python-specific

## Setup

### Languages used in this course

* **Python 3.11+**, the language every code example is written in. The patterns and principles
  themselves are language-agnostic; Python is chosen for readability in a lecture setting.
* **Java 17+** (optional), for anyone who would rather work in a statically-typed, class-based
  language for their exercises and project. Every pattern and principle in this course maps
  directly onto Java; only the lecture code examples are Python. Use [Maven](https://maven.apache.org/)
  or [Gradle](https://gradle.org/) for dependency management, whichever you already know.
* **Mermaid**, for every architecture and sequence diagram in this course, following the [C4
  model](https://c4model.com/)'s levels of abstraction where relevant.
* **Markdown**, for Architecture Decision Records (Module 9) and every module's own notes.

### Tools to install locally

| Tool | Needed from | Install |
|---|---|---|
| **Python 3.11+** | Module 1 | [python.org/downloads](https://www.python.org/downloads/) or a version manager like `pyenv` |
| **uv** | Module 1 | [docs.astral.sh/uv](https://docs.astral.sh/uv/getting-started/installation/): this repo's dependency manager |
| **JDK 17+** (optional, Java track) | Module 1 | [adoptium.net](https://adoptium.net/): only needed if you choose to work in Java instead of Python |
| **Git** | Module 1 | [git-scm.com/downloads](https://git-scm.com/downloads/) |
| **A code editor** | Module 1 | [VS Code](https://code.visualstudio.com/) is recommended; this repo ships a `.devcontainer/` |
| **Docker Desktop** (or OrbStack on macOS) | Module 7 | [docs.docker.com/get-docker](https://docs.docker.com/get-docker/), for the microservices exercises |

Once Python, `uv`, and Git are installed, clone the course repository and run:

```bash
git clone https://github.com/aligunesgit/software-design-and-architecture.git
cd software-design-and-architecture
uv sync
```

This installs every dependency listed in `pyproject.toml`, including the per-module exercise
dependencies tracked under `[dependency-groups.exercises]`.

## Prescribed books

The following books are suggested reading for the course:

* Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides, *Design Patterns: Elements of
  Reusable Object-Oriented Software* (Addison-Wesley)
* Robert C. Martin, *Clean Architecture: A Craftsman's Guide to Software Structure and Design*
  (Prentice Hall)
* Len Bass, Paul Clements, and Rick Kazman, *Software Architecture in Practice* (Addison-Wesley)
* Eric Evans, *Domain-Driven Design: Tackling Complexity in the Heart of Software*
  (Addison-Wesley)
* Sam Newman, *Building Microservices: Designing Fine-Grained Systems* (O'Reilly)

None are required to follow the course, but each is a good deeper dive on a theme that recurs
across several modules.
