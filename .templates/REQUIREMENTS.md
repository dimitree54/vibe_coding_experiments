# Requirements Specification

> Fill this template to formalize the development task.

# Goals and Background Context

## Goals

> Bullet list of 1 line desired outcomes if implementation is successful. Who will benefit from it? Developer or user?

-

## Background Context

> 1-2 short paragraphs summarizing the background context, such as what we learned in the brief without being redundant with the goals, what and why this solves a problem, what the current landscape or need is.

## Change Log

> Track document versions and changes.

| Date | Version | Description | Author |
| --- | --- | --- | --- |
| | | | |

# Requirements

> Draft the list of functional and non functional requirements under the two child sections.

## Functional

> Each Requirement will be a bullet markdown and an identifier sequence starting with FR.
>
> Example:
> - "FR6: The Todo List uses AI to detect and warn against potentially duplicate todo items that are worded differently."

- FR1:

## Non Functional

> Each Requirement will be a bullet markdown and an identifier sequence starting with NFR.
>
> Example:
> - "NFR1: AWS service usage must aim to stay within free-tier limits where feasible."

- NFR1:

# User Interface Design Goals

> Note: This section is applicable if the PRD has UX/UI requirements.
>
> **Instructions to follow:**
> 1.  Pre-fill all subsections with educated guesses based on project context
> 2.  Present the complete rendered section to user
> 3.  Clearly let the user know where assumptions were made
> 4.  Ask targeted questions for unclear/missing elements or areas needing more specification
> 5.  This is NOT detailed UI spec - focus on product vision and user goals

## Overall UX Vision

## Key Interaction Paradigms

## Core Screens and Views

> From a product perspective, what are the most critical screens or views necessary to deliver the the PRD values and goals? This is meant to be Conceptual High Level to Drive Rough Epic or User Stories.
>
> Examples:
> - "Login Screen"
> - "Main Dashboard"
> - "Item Detail Page"
> - "Settings Page"

-

## Accessibility: {None|WCAG AA|WCAG AAA|Custom Requirements}

## Branding

> Any known branding elements or style guides that must be incorporated?
>
> Examples:
> - "Replicate the look and feel of early 1900s black and white cinema, including animated effects replicating film damage or projector glitches during page or state transitions."
> - "Attached is the full color pallet and tokens for our corporate branding."

## Target Device and Platforms: {Web Responsive|Mobile Only|Desktop Only|Cross-Platform}

> Examples:
> - "Web Responsive, and all mobile platforms"
> - "iPhone Only"
> - "ASCII Windows Desktop"

# Technical Assumptions

> **Instructions to follow:**
> 1. Check if `{root}/data/technical-preferences.yaml` or an attached `technical-preferences` file exists - use it to pre-populate choices
> 2. Ask user about: languages, frameworks, starter templates, libraries, APIs, deployment targets
> 3. For unknowns, offer guidance based on project goals and MVP scope
> 4. Document ALL technical choices with rationale (why this choice fits the project)
> 5. These become constraints for the Architect - be specific and complete

## Repository Structure: {Monorepo|Polyrepo|Multi-repo}

## Service Architecture

> CRITICAL DECISION - Document the high-level service architecture (e.g., Monolith, Microservices, Serverless functions within a Monorepo).

## Testing Requirements

> CRITICAL DECISION - Document the testing requirements, unit only, integration, e2e, manual, need for manual testing convenience methods).

## Additional Technical Assumptions and Requests

> Throughout the entire process of drafting this document, if any other technical assumptions are raised or discovered appropriate for the architect, add them here as additional bulleted items.

-

# Epic List

> Present a high-level list of all epics for user approval. Each epic should have a title and a short (1 sentence) goal statement. This allows the user to review the overall structure before diving into details.
>
> CRITICAL: Epics MUST be logically sequential following agile best practices:
>
> - Each epic should deliver a significant, end-to-end, fully deployable increment of testable functionality
> - Epic 1 must establish foundational project infrastructure (app setup, Git, CI/CD, core services) unless we are adding new functionality to an existing app, while also delivering an initial piece of functionality, even as simple as a health-check route or display of a simple canary page - remember this when we produce the stories for the first epic!
> - Each subsequent epic builds upon previous epics' functionality delivering major blocks of functionality that provide tangible value to users or business when deployed
> - Not every project needs multiple epics, an epic needs to deliver value. For example, an API completed can deliver value even if a UI is not complete and planned for a separate epic.
> - Err on the side of less epics, but let the user know your rationale and offer options for splitting them if it seems some are too large or focused on disparate things.
> - Cross Cutting Concerns should flow through epics and stories and not be final stories. For example, adding a logging framework as a last story of an epic, or at the end of a project as a final epic or story would be terrible as we would not have logging from the beginning.
>
> Examples:
> - "Epic 1: Foundation & Core Infrastructure: Establish project setup, authentication, and basic user management"
> - "Epic 2: Core Business Entities: Create and manage primary domain objects with CRUD operations"
> - "Epic 3: User Workflows & Interactions: Enable key user journeys and business processes"
> - "Epic 4: Reporting & Analytics: Provide insights and data visualization for users"

-

# Epic {{epic_number}} {{epic_title}}

> This section is repeatable for each epic.
>
> **Instructions to follow:**
> After the epic list is approved, present each epic with all its stories and acceptance criteria as a complete review unit.
>
> For each epic provide expanded goal (2-3 sentences describing the objective and value all the stories will achieve).
>
> **Epic Goal:** {{epic_goal}}
>
> CRITICAL STORY SEQUENCING REQUIREMENTS:
>
> - Stories within each epic MUST be logically sequential
> - Each story should be a "vertical slice" delivering complete functionality aside from early enabler stories for project foundation
> - No story should depend on work from a later story or epic
> - Identify and note any direct prerequisite stories
> - Focus on "what" and "why" not "how" (leave technical implementation to Architect) yet be precise enough to support a logical sequential order of operations from story to story.
> - Ensure each story delivers clear user or business value, try to avoid enablers and build them into stories that deliver value.
> - Size stories for AI agent execution: Each story must be completable by a single AI agent in one focused session without context overflow
> - Think "junior developer working for 2-4 hours" - stories must be small, focused, and self-contained
> - If a story seems complex, break it down further as long as it can deliver a vertical slice

## Story {{epic_number}}.{{story_number}} {{story_title}}

> This section is repeatable for each story in an epic.
>
> As a {{user_type}},
> I want {{action}},
> so that {{benefit}}.

### Acceptance Criteria

> This section is repeatable for each acceptance criterion.
>
> Define clear, comprehensive, and testable acceptance criteria that:
>
> - Precisely define what "done" means from a functional perspective
> - Are unambiguous and serve as basis for verification
> - Include any critical non-functional requirements from the PRD
> - Consider local testability for backend/data components
> - Specify UI/UX requirements and framework adherence where applicable
> - Avoid cross-cutting concerns that should be in other stories or PRD sections

1. {{criterion_number}}: {{criteria}}

# Checklist Results Report

> Before running the checklist and drafting the prompts, offer to output the full updated PRD. If outputting it, confirm with the user that you will be proceeding to run the checklist and produce the report. Once the user confirms, execute the pm-checklist and populate the results in this section.

# Next Steps

## UX Expert Prompt

> This section will contain the prompt for the UX Expert, keep it short and to the point to initiate create architecture mode using this document as input.

## Architect Prompt

> This section will contain the prompt for the Architect, keep it short and to the point to initiate create architecture mode using this document as input.

