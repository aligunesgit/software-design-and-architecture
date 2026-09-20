<p align="center">
    <h1 align="center">Software Design and Architecture</h1>
    <p align="center">Course material.</p>
</p>

## Quick Links

| Resource | Link |
|---|---|
| Course materials | *TBD* |
| Documentation | *TBD* |
| Course platform (deadlines, homework) | *TBD* |
| Communication channel | *TBD* |
| Announcements | *TBD* |
| FAQ | [FAQ page](pages/faq.md) |

## Course information

* Course responsible
    * Assistant Professor <a href="https://www.atlas.edu.tr/akademik-kadro/ali-gunes" target="_blank" rel="noopener noreferrer">Ali Gunes</a>, ali.gunes@atlas.edu.tr
* Credit weight: *TBD*
* 12 week period
* Grade: *TBD*
* Type of assessment: *TBD*
* Project Group Size: *TBD*
* Recommended prerequisites:
    * At least 1 year of general programming experience, comfortable reading and writing
      object-oriented code
    * Basic data structures and algorithms
    * Some exposure to a statically-typed or strongly-typed language is helpful but not required

## ❔ Learning objectives

**General course objective**

This course exists to take a student who can already *write* working code and teach them to
*structure* it: organizing a codebase so it stays changeable as it grows, recognizing which design
pattern actually fits a problem instead of reaching for the first one that comes to mind, and
making architectural trade-offs deliberately instead of by accident. The emphasis throughout is
applied: every module pairs a principle or pattern with real code, not just a diagram.

This includes:

* Apply the SOLID principles to keep a codebase's coupling and cohesion under control as it grows
* Recognize and implement the classic creational, structural, and behavioral design patterns
* Compare architectural styles (layered, event-driven, microservices, and more) and justify which
  one fits a given system's actual constraints
* Apply domain-driven design to carve a large system into coherent, independently evolvable modules
* Design and reason about distributed systems: service boundaries, consistency trade-offs, and
  resilience patterns like retries and circuit breakers
* Document an architecture so someone else, including future you, can understand why it looks the
  way it does
* Evaluate a design against its quality attributes, and refactor deliberately when it falls short
* Conduct a project in collaboration with fellow students, applying every framework taught in the
  course end to end
* Have fun along the way. Good architecture is usually invisible until it's missing

## 🔥 Where to start

We recommend going through the material on this repository's GitHub Pages site rather than
reading raw markdown here, since it renders the same content through Material for MkDocs, with
proper navigation, search, and diagram rendering.

Specifically, start at the [Introduction page](pages/before.md) for a soft introduction to the
course and how it is organized, then follow the [Time plan](pages/timeplan.md) week by week.

## 📂 Course organization

Every module below is required. The course is organized into 10 content modules (M1-M10) and 2
project sprint weeks (Sprint A, Sprint B). Each module has its own folder with a `README.md` and
`exercise_files/`.

| Week | Module | Topic |
|------|--------|-------|
| 1  | [M1](m1_introduction/README.md) | Introduction to Software Design & Architecture |
| 2  | [M2](m2_oo_design_principles/README.md) | Object-Oriented Design Principles |
| 3  | [M3](m3_design_patterns_creational_structural/README.md) | Design Patterns I (Creational & Structural) |
| 4  | [M4](m4_design_patterns_behavioral/README.md) | Design Patterns II (Behavioral) |
| 5  | [M5](m5_architectural_styles/README.md) | Architectural Styles & Patterns |
| 6  | [Sprint A](sprint_a_project/README.md) | Project Sprint A |
| 7  | [M6](m6_domain_driven_design/README.md) | Domain-Driven Design & Modular Design |
| 8  | [M7](m7_microservices/README.md) | Microservices Architecture |
| 9  | [M8](m8_distributed_systems/README.md) | Distributed Systems & Resilience Patterns |
| 10 | [M9](m9_architecture_documentation/README.md) | Architecture Documentation & Decision Making |
| 11 | [M10](m10_quality_evaluation/README.md) | Quality Attributes, Evaluation & Refactoring |
| 12 | [Sprint B](sprint_b_final_project/README.md) | Project Sprint B (final) |

## 🏗️ Recommended folder structure

Keeping this repository and your own group project in separate folders, each with its own virtual
environment, avoids dependency conflicts between the two.

```
software-design-course/            # call this whatever you like
    ├── SoftwareDesignAndArchitecture/   # this repository
    │   ├── .git/
    │   ├── .venv/
    │   ├── uv.lock
    │   ├── pyproject.toml
    │   ├── m1_introduction/exercise_files/
    │   ├── m2_oo_design_principles/exercise_files/
    │   └── ...                      # one exercise_files/ per module
    ├── group-project/                # your own repo, created in Sprint A (Week 6)
    │   ├── .git/
    │   ├── .venv/
    │   ├── uv.lock
    │   ├── pyproject.toml
    │   └── ...                      # carried through to submission in Sprint B (Week 12)
    └── ...                           # any other personal notes
```

## Course books

The following books are suggested reading for the course:

* Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides, *Design Patterns: Elements of
  Reusable Object-Oriented Software* (Addison-Wesley): the original "Gang of Four" book
* Robert C. Martin, *Clean Architecture: A Craftsman's Guide to Software Structure and Design*
  (Prentice Hall)
* Len Bass, Paul Clements, and Rick Kazman, *Software Architecture in Practice* (Addison-Wesley)
* Eric Evans, *Domain-Driven Design: Tackling Complexity in the Heart of Software*
  (Addison-Wesley)
* Sam Newman, *Building Microservices: Designing Fine-Grained Systems* (O'Reilly)

## 📓 References

Additional reading resources (in no particular order):

* [Refactoring Guru: Design Patterns](https://refactoring.guru/design-patterns). A visual,
  language-agnostic introduction to the Gang of Four patterns.
* [Martin Fowler's blog](https://martinfowler.com/). A large body of writing on software
  architecture, patterns, and refactoring, referenced throughout this course.
* [The Twelve-Factor App](https://12factor.net/). A widely cited methodology for building
  service-based applications, relevant to the microservices module.
* [C4 model](https://c4model.com/). The notation this course uses for architecture diagrams.
* [Architecture Decision Records](https://adr.github.io/). The lightweight documentation format
  this course uses for recording architectural decisions.
