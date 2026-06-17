# Fundamentals of BDD with Python
## Complete Training Presentation & Course Content

---

# SLIDE 1 — TITLE

# Fundamentals of BDD with Python
### From Requirements to Executable Specifications

**Duration:** 2 Days  
**Level:** Beginner  
**Audience:** Developers, Testers, QA Engineers, Beginners to BDD

---

# SLIDE 2 — TRAINING OBJECTIVES

## By the end of this training participants will:

- Understand the purpose and principles of BDD
- Know the differences between BDD and TDD
- Write readable and maintainable Gherkin scenarios
- Use Given/When/Then correctly
- Understand Scenario Outline and Examples tables
- Recognize common BDD anti-patterns
- Learn when BDD should and should not be used
- Implement BDD scenarios using Python and pytest-bdd
- Build a basic maintainable BDD test structure

---

# SLIDE 3 — AGENDA

# Day 1
- Why BDD?
- BDD principles
- BDD vs TDD
- Gherkin basics
- Good vs bad scenarios
- Scenario Outline & Examples
- Anti-patterns
- Where BDD fits in testing

# Day 2
- Python BDD tooling
- pytest-bdd basics
- Step definitions
- Test architecture
- Hands-on implementation
- Review and refactoring
- Best practices

---

# DAY 1 — UNDERSTANDING BDD

---

# SLIDE 4 — THE CHALLENGES OF TRADITIONAL REQUIREMENTS

## Common Problems

- Ambiguous requirements
- Different understanding between teams
- Tests focus on implementation details
- Documentation becomes outdated
- Communication gaps between business, development, and testing

## Result

- Rework
- Misunderstandings
- Defects
- Slow feedback

---

# SLIDE 5 — WHAT IS BDD?

# Behavior Driven Development (BDD)

BDD is a collaborative development approach where:

- Requirements are described as behaviors
- Teams use shared language
- Examples become executable specifications
- Business and technical teams collaborate more effectively

## Main Goal

> Build the right thing before building the thing right.

---

# SLIDE 6 — CORE IDEAS OF BDD

## BDD focuses on:

- Shared understanding
- Observable behavior
- Real examples
- Collaboration
- Living documentation

## BDD is NOT:

- Just writing tests in Gherkin
- A replacement for unit testing
- Only for testers

---

# SLIDE 7 — BDD FLOW

## Typical BDD Workflow

1. Discuss requirements
2. Define examples
3. Write scenarios
4. Automate scenarios
5. Implement functionality
6. Run automated checks continuously

---

# SLIDE 8 — BDD vs TDD

| TDD | BDD |
|------|------|
| Developer focused | Team focused |
| Unit-level validation | Behavior-level validation |
| Technical language | Business language |
| Tests implementation | Tests behavior |
| Focus on correctness | Focus on understanding |

## Important

BDD and TDD complement each other.

---

# SLIDE 9 — WHAT IS GHERKIN?

## Gherkin

A readable language used to describe behavior.

### Main Keywords

- Feature
- Scenario
- Given
- When
- Then
- And
- But

---

# SLIDE 10 — BASIC GHERKIN EXAMPLE

```gherkin
Feature: Login

  Scenario: Successful login
    Given a registered user
    When the user logs in with valid credentials
    Then the user should access the dashboard
```

---

# SLIDE 11 — GIVEN / WHEN / THEN

| Keyword | Purpose |
|----------|----------|
| Given | Initial context |
| When | User/system action |
| Then | Observable outcome |

## Rule of Thumb

- Given = setup
- When = action
- Then = verification

---

# SLIDE 12 — GOOD SCENARIO CHARACTERISTICS

## Good Scenarios Are:

- Easy to read
- Business-focused
- Short and meaningful
- Independent
- Focused on one behavior
- Understandable by non-technical people

---

# SLIDE 13 — BAD SCENARIO EXAMPLE

## ❌ Bad Example

```gherkin
Scenario: Login test
  Given I open Chrome browser
  And I navigate to login page
  And I type username
  And I type password
  And I click login button
  Then I see dashboard page
```

## Problems

- Too UI-focused
- Too technical
- Difficult to maintain
- Focuses on implementation

---

# SLIDE 14 — IMPROVED SCENARIO

## ✅ Better Example

```gherkin
Scenario: Registered user logs in successfully
  Given a registered user
  When the user logs in with valid credentials
  Then the user should access the dashboard
```

## Why Better?

- Business-focused
- Clear intent
- Stable wording
- Easier maintenance

---

# SLIDE 15 — SCENARIO OUTLINE

## Scenario Outline

Used when behavior stays the same but data changes.

```gherkin
Scenario Outline: Discount calculation
  Given a "<type>" customer
  When the cart total is "<amount>"
  Then the discount should be "<discount>"
```

---

# SLIDE 16 — EXAMPLES TABLE

```gherkin
Examples:
  | type    | amount | discount |
  | Regular | 100    | 0%       |
  | Premium | 100    | 10%      |
```

## Benefits

- Avoid duplication
- Improves readability
- Supports data-driven behavior

---

# SLIDE 17 — WHEN TO USE EXAMPLES TABLES

## Use When:

- Same behavior with different data
- Boundary conditions
- Equivalence partitions
- Input/output variations

## Avoid When:

- Huge combinations
- Technical permutations
- Unreadable tables

---

# SLIDE 18 — BDD ANTI-PATTERNS

## Common Anti-Patterns

- Scenarios read like scripts
- Too much UI detail
- Huge Examples tables
- Multiple behaviors in one scenario
- Generic steps
- Duplicate wording
- Logic hidden in step definitions

---

# SLIDE 19 — ANTI-PATTERN EXAMPLE

## ❌ Too Many Behaviors

```gherkin
Scenario: Shopping flow
  Given the user logs in
  When the user adds product to cart
  And applies discount
  And enters address
  And makes payment
  Then the order should be completed
```

## Problem

Too many behaviors in one scenario.

---

# SLIDE 20 — BETTER APPROACH

## ✅ Split Behaviors

- Scenario: User adds product to cart
- Scenario: User applies discount code
- Scenario: User completes payment

---

# SLIDE 21 — WHERE BDD FITS IN TESTING

## Test Pyramid

- Unit Tests
- Integration Tests
- API/Service Tests
- UI Tests

## BDD Works Best At:

- API level
- Service level
- Critical business flows

---

# SLIDE 22 — WHEN NOT TO USE BDD

## Avoid BDD For:

- Pure algorithm validation
- Complex technical permutations
- Highly unstable UI details
- Low-level unit logic
- Scenarios with no collaboration value

---

# DAY 2 — AUTOMATION WITH PYTHON

---

# SLIDE 23 — INTRODUCTION TO PYTEST-BDD

## What is pytest-bdd?

A Python framework combining:

- pytest
- Gherkin syntax
- BDD workflow

## Benefits

- Simple integration
- pytest ecosystem support
- Readable scenarios
- Easy automation

---

# SLIDE 24 — PROJECT STRUCTURE

```text
bdd-project/
├── features/
│   ├── login.feature
│   └── steps/
│       └── test_login_steps.py
├── tests/
│   ├── domain/
│   └── helpers/
├── requirements.txt
└── pytest.ini
```

---

# SLIDE 25 — INSTALLATION

```bash
pip install pytest
pip install pytest-bdd
```

---

# SLIDE 26 — FEATURE FILE EXAMPLE

```gherkin
Feature: Login

  Scenario: Successful login
    Given a registered user
    When the user logs in with valid credentials
    Then the user should access the dashboard
```

---

# SLIDE 27 — STEP DEFINITIONS

```python
from pytest_bdd import scenarios, given, when, then

scenarios('../login.feature')
```

---

# SLIDE 28 — GIVEN STEP

```python
@given("a registered user")
def registered_user(context):
    context["user"] = {
        "username": "test_user",
        "password": "secret123"
    }
```

---

# SLIDE 29 — WHEN STEP

```python
@when("the user logs in with valid credentials")
def login(context):
    response = login_service(
        context["user"]
    )

    context["response"] = response
```

---

# SLIDE 30 — THEN STEP

```python
@then("the user should access the dashboard")
def dashboard_access(context):
    assert context["response"] == "success"
```

---

# SLIDE 31 — THIN STEPS, RICH DOMAIN LAYER

## Recommended Architecture

### Step Definitions
- Glue code
- Readability
- Simple orchestration

### Domain Layer
- Business logic
- API calls
- Reusable workflows
- Validation helpers

---

# SLIDE 32 — TAGGING STRATEGY

## Example Tags

```gherkin
@smoke
@regression
@api
@ui
@negative
```

## Why Use Tags?

- Organize tests
- Select executions
- CI filtering
- Reporting

---

# SLIDE 33 — REUSABLE STEPS

## ❌ Bad

```gherkin
Given the user is logged in
Given the customer is authenticated
Given active session exists
```

## ✅ Better

```gherkin
Given an authenticated user
```

---

# SLIDE 34 — TEST DATA MANAGEMENT

## Recommendations

- Keep test data simple
- Use builders/helpers
- Avoid hardcoded values everywhere
- Make scenarios independent
- Avoid shared mutable state

---

# SLIDE 35 — MAINTAINABILITY GUIDELINES

## Best Practices

- Keep scenarios short
- Avoid implementation details
- Use stable domain language
- Review feature files collaboratively
- Refactor duplicate steps
- Prefer readability over technical cleverness

---

# SLIDE 36 — HANDS-ON LAB

## Exercise

### Goal

Implement BDD scenarios for:

- Login validation
- Discount calculation
- Account lock after failed attempts

### Tasks

- Write scenarios
- Create Examples tables
- Implement step definitions
- Run pytest-bdd tests

---

# SLIDE 37 — LAB EXPECTED OUTCOME

## Participants Should Be Able To:

- Create feature files
- Implement Given/When/Then steps
- Run automated scenarios
- Organize a small BDD project
- Recognize anti-patterns

---

# SLIDE 38 — REVIEW & REFACTORING

## Questions

- Is the scenario readable?
- Is behavior clear?
- Is there duplicated wording?
- Is the scenario too technical?
- Can a non-technical person understand it?

---

# SLIDE 39 — KEY TAKEAWAYS

## Remember

- BDD is about collaboration
- Focus on behavior, not implementation
- Scenarios should be readable
- Examples should add value
- BDD complements other testing levels
- Good architecture improves maintainability

---

# SLIDE 40 — FINAL Q&A

# Questions?

Thank you!

---

# DETAILED COURSE CONTENT

## DAY 1 SCHEDULE

### 10:00 – 10:30
## Welcome & Introduction

Topics:
- Course overview
- Objectives
- Expectations
- Agenda walkthrough

Activity:
- Icebreaker discussion

---

### 10:30 – 11:15
## The Challenges of Traditional Requirements & Testing

Topics:
- Requirement misunderstandings
- Communication gaps
- Traditional test limitations
- Why behavior matters

Activity:
- Group discussion using real examples

---

### 11:15 – 12:00
## What is BDD?

Topics:
- BDD definition
- Core principles
- Shared understanding
- Living documentation
- Examples as specifications

Activity:
- Q&A discussion

---

### 12:00 – 13:00
# Lunch Break

---

### 13:00 – 13:45
## BDD vs TDD

Topics:
- Key differences
- Complementary usage
- Appropriate usage areas

Activity:
- Comparison exercise

---

### 13:45 – 14:30
## Writing Behavior-Focused Scenarios

Topics:
- Feature/Scenario structure
- Given/When/Then
- Good wording practices
- Readability principles

Activity:
- Improve bad scenarios exercise

---

### 14:30 – 15:15
## Scenario Outline & Examples Tables

Topics:
- Data-driven scenarios
- Designing useful examples
- Boundary examples
- Avoiding giant tables

Activity:
- Create Scenario Outline together

---

### 15:15 – 16:00
## BDD Anti-Patterns & Test Pyramid

Topics:
- Common mistakes
- Where BDD fits
- When not to use BDD

Activity:
- Anti-pattern review workshop

---

# DAY 2 SCHEDULE

### 10:00 – 10:30
## Recap & Q&A

Topics:
- Key takeaways from Day 1
- Clarifications

---

### 10:30 – 11:15
## Introduction to pytest-bdd

Topics:
- Framework overview
- Installation
- Project structure
- Running tests

Activity:
- Live demo

---

### 11:15 – 12:00
## Step Definitions & Architecture

Topics:
- Given/When/Then implementation
- Context management
- Fixtures
- Thin steps approach
- Domain layer

Activity:
- Live coding

---

### 12:00 – 13:00
# Lunch Break

---

### 13:00 – 14:30
## Hands-on Lab — Part 1

Topics:
- Writing feature files
- Implementing step definitions
- Using Examples tables
- Running tests

Activity:
- Guided hands-on implementation

---

### 14:30 – 15:15
## Hands-on Lab — Part 2

Topics:
- Completing scenarios
- Debugging failures
- Improving readability
- Refactoring duplicate steps

Activity:
- Team implementation

---

### 15:15 – 15:45
## Review & Refactoring

Topics:
- Reviewing implementations
- Common mistakes
- Better architecture
- Readability improvements

Activity:
- Group review

---

### 15:45 – 16:00
## Wrap-up

Topics:
- Final recommendations
- Next steps
- Useful resources
- Feedback

---

# RECOMMENDED RESOURCES

## Books
- The Cucumber Book
- Specification by Example
- BDD in Action

## Tools
- pytest-bdd
- behave
- pytest

## Suggested Practice Areas
- Login workflows
- API validation
- Discount calculations
- Account management

---

# TEAM PLAYBOOK SUMMARY

## Writing Rules

- Focus on behavior
- Avoid UI-heavy wording
- Keep scenarios short
- Use consistent vocabulary
- One behavior per scenario

## Automation Rules

- Keep step definitions thin
- Move logic to helper/domain layers
- Reuse meaningful steps
- Avoid duplicate wording

## Review Checklist

- Is behavior clear?
- Is wording readable?
- Is the scenario maintainable?
- Does the Examples table add value?
- Is BDD appropriate here?

