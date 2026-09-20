# Project work

Roughly a sixth of the course's total time (2 of 12 weeks) is dedicated project work, but the
group project itself is meant to run in parallel with the content weeks: every module's ideas get
applied to the same running project as soon as they're covered, starting in Sprint A (Week 6).

The project serves as the basis for the course's final grading. Groups are free to choose their
own system to design; the point is not to build the most feature-complete application but to
demonstrate that the group can apply the principles and patterns taught in this course to a real
(if modest) system, and can justify the architectural decisions they made.

## Group size

*TBD, see [course information](../README.md#course-information).*

## Assessment

*TBD, see [course information](../README.md#course-information).*

## Getting started

1. **Pick a domain and scope it small.** A small system with a clearly justified architecture
   beats an ambitious one with none. Something with at least two or three distinct responsibilities
   (so there's something to actually decompose) works well: a small e-commerce backend, a booking
   system, a content platform.
2. **Write a short design brief** (the problem, the main use cases, and a first guess at the
   quality attributes that matter most for this system) and commit it to the project repository's
   `README.md`.
3. **Scaffold the repository** using Module 1's project conventions and Module 2's SOLID-aligned
   package structure (see Sprint A).

## Project checklist

This checklist is *exhaustive*: it lists everything that could be done across the whole
curriculum. Nobody is expected to check every box. The module tag in parentheses shows which
module the item ties to.

### Weeks 1-6 (Modules 1-5, Sprint A)

* [ ] Repository scaffolded with a clear package structure (M1)
* [ ] At least one deliberate SOLID refactor, documented (before/after) (M2)
* [ ] At least two creational or structural patterns applied where they genuinely fit (M3)
* [ ] At least one behavioral pattern applied where it genuinely fits (M4)
* [ ] An explicit architectural style chosen and justified in writing (M5)

### Weeks 7-11 (Modules 6-10)

* [ ] Domain model with at least one bounded context identified (M6)
* [ ] The system decomposed into at least two independently deployable services, or a documented
      reason why it stays a single service (M7)
* [ ] At least one resilience pattern (retry, circuit breaker, timeout) applied to an
      inter-service or external call (M8)
* [ ] At least one Architecture Decision Record (ADR) written for a real decision the group made (M9)
* [ ] A quality attribute scenario defined and evaluated against the current design, with at
      least one resulting refactor (M10)

### Extra

* [ ] Write documentation for the application and publish it
* [ ] Revisit the initial design brief: did the architecture turn out as planned?
* [ ] Create a C4-style diagram of the overall system
* [ ] Make sure all group members understand every part of the architecture

## Submission

The report template lives at `reports/README.md` in this repository (excluded from the built docs
site since it's a template to copy, not a page to publish). Copy it into the group project's own
repository and fill it out. *Deadline TBD once the semester dates are fixed.*
