# Module 10: Quality Attributes, Evaluation & Refactoring

Week 11

## Learning objectives

* Be able to write a concrete quality attribute scenario, not just name the attribute
* Understand sensitivity points and trade-off points well enough to spot one in a real design
* Be able to measure code-level quality with complexity and coupling metrics
* Recognize common code smells and refactor toward a cleaner design under test

---

## 1. From naming a quality attribute to evaluating one

Module 1, §1 introduced quality attributes (performance, security, maintainability, and the
rest) as the things an architecture trades off against each other. Naming them is easy: everyone
agrees a system should be "scalable" and "maintainable." Evaluating whether a specific design
actually delivers on that is the harder, more useful skill, and it is what separates architecture
as an opinion from architecture as an engineering discipline.

## 2. Quality attribute scenarios

A quality attribute is not evaluable until it is written as a **scenario** with four parts:
stimulus, environment, response, and response measure.

| Part | Question it answers |
|---|---|
| **Stimulus** | What event triggers the concern? |
| **Environment** | Under what conditions? (normal load, peak load, partial outage) |
| **Response** | What should the system do? |
| **Response measure** | How do you know it worked, in a measurable, testable way? |

Compare a vague goal against a real scenario:

* Vague: "The system should be scalable."
* Scenario: "When traffic increases to 10x normal load during a flash sale (stimulus,
  environment), the Ordering service should continue processing new orders (response) with 95th
  percentile latency under 500ms and zero dropped requests (response measure)."

The second version is something you can actually test, and something a design review can say yes
or no to, rather than nod along with.

## 3. Sensitivity points and trade-off points

Two ideas from the **Architecture Tradeoff Analysis Method (ATAM)** help you locate where a
design decision matters most. A **sensitivity point** is a place where one architectural decision
significantly affects a quality attribute: choosing synchronous versus asynchronous
communication between services is highly sensitive to both latency and availability. A
**trade-off point** is a sensitivity point that affects *more than one* attribute in opposite
directions: that same synchronous-versus-asynchronous choice improves consistency (you know
immediately if a downstream call failed) while it worsens availability (a downstream outage now
blocks the caller too, exactly the problem Module 8, §3's circuit breaker pattern exists to
contain).

Walking through the scenario from §2: the Ordering service's synchronous call to the Payment
service is a trade-off point. Making it synchronous makes the order-confirmation flow simpler to
reason about and keeps order and payment state consistent, but it means a slow or down Payment
service directly threatens the 500ms response measure above. That single observation, made
explicit rather than left implicit, is the entire value ATAM adds: it does not choose the trade-off
for you, it makes sure the trade-off is a decision instead of an accident.

## 4. Code-level quality metrics

Architecture-level evaluation is qualitative; code-level evaluation can be measured directly.
**Cyclomatic complexity** counts the number of independent paths through a function (each `if`,
`for`, `while`, or `and`/`or` adds one); a function above roughly 10 is a candidate for splitting.
**Coupling** metrics count how many other modules a given module depends on, or is depended on
by; high coupling in both directions is exactly what Module 2's SOLID principles are trying to
prevent.

`radon`, a Python static analysis tool, computes cyclomatic complexity directly:

```bash
uv add --dev radon
radon cc order_service.py -s
```

```text
order_service.py
    F 12:0 process_order - C (14)
    F 45:0 validate_address - A (2)
```

The letter grade (A through F) and number are radon's complexity score per function; `process_order`
at 14 is well past the point where splitting it into smaller functions, or applying one of the
behavioral patterns from Module 4 (a Strategy for the different validation rules it likely
branches on), would make it independently testable and easier to reason about.

## 5. Code smells and safe refactoring

A **code smell** is a surface symptom that usually points at a deeper design problem underneath.
Four common ones:

| Smell | What it looks like | Usually points at |
|---|---|---|
| **Long Method** | A function that keeps growing, doing several unrelated things | A missing abstraction, or a single responsibility violation (Module 2, §2) |
| **God Class** | One class that knows and does too much | Missing decomposition, often fixable with the patterns from Modules 3-4 |
| **Shotgun Surgery** | One conceptual change requires editing many unrelated files | Low cohesion, the same concern scattered across the codebase |
| **Feature Envy** | A method that uses another class's data more than its own | The method (or the data) is in the wrong place |

Refactoring, in Martin Fowler's original sense, means changing the internal structure of code
*without changing its observable behavior*. That "without changing behavior" clause is why a test
suite is not optional here: a refactor you cannot verify against passing tests is just a rewrite
with extra risk. This connects directly back to Module 2's SOLID work: a refactor toward the
Single Responsibility or Dependency Inversion principle is usually the concrete fix for a Long
Method or God Class smell, done safely because tests catch a behavior change the moment it
happens.

## 6. Project: evaluate and refactor (required)

For your own group project: write one quality attribute scenario in the stimulus/environment/
response/response-measure format from §2, using a concern that is actually real for your system.
Identify at least one sensitivity or trade-off point in your current design relative to that
scenario, the way §3 did for the Ordering example. Then make at least one refactor as a direct
result, whether that means splitting a God Class, applying a pattern from Module 3 or 4, or
restructuring a dependency to satisfy SOLID. Show the before and after, and run `radon` on the
affected file both times to report whether the complexity number actually moved.

---

## Summary

A quality attribute is not evaluated until it is written as a testable scenario (§2); a
sensitivity or trade-off point (§3) is where a specific design decision earns or costs you that
attribute, made visible instead of assumed. Code-level metrics (§4) give the same discipline a
concrete, measurable form at the function level, and refactoring under test (§5) is how you act
on what the evaluation found without regressing the behavior that already worked. This is the
last content module before Sprint B, and its project deliverable, an evaluated and refactored
design, is exactly what the final report in Sprint B asks you to have already done.

## Further reading

* See the [Course books](../README.md#course-books) for deeper dives.

## References

* Bass, Len, Clements, Paul, and Kazman, Rick. *Software Architecture in Practice*. Addison-Wesley.
  Source for ATAM, sensitivity points, and trade-off points in §3.
* Fowler, Martin. *Refactoring: Improving the Design of Existing Code*. Addison-Wesley. Source for
  the code smells and the definition of refactoring in §5.
* [radon documentation](https://radon.readthedocs.io/). Source for the cyclomatic complexity
  example in §4.
