---
layout: page
title: Project 1
permalink: /projects/project-1
parent: Projects
nav_order: 1
---

# CS6.401 Software Engineering

## Spring 2026

## Project - 1

Welcome to the first project! Your objective is to reverse engineer, analyze, and refactor Apache Roller. This system is significantly more complex than a simple RSS reader; it is a mature Apache project used by major organizations (like Oracle and IBM) for enterprise-level blogging.

### Target System

**Apache Roller** is an open-source, Java-based blog platform. It supports multi-user blogging, group blogs, comment moderation, and content indexing via Lucene. You can find the repository here: https://github.com/apache/roller.

> Note on LLM Usage: If you use LLMs (ChatGPT, Claude, Gemini, etc.), you must include screenshots of your prompts and the generated responses in your report. Provide a qualitative analysis of the LLM outputs and highlight your own manual contributions or modifications.

## Task 1: Architectural Mapping and Design Recovery (30 Marks)

Apache Roller is a large system. To manage its complexity, focus on these three major functional areas:

1. **Weblog and Content Subsystem:** This manages the creation of blogs, entries, and comments. It includes the rendering engine and content fetching.
2. **User and Role Management Subsystem:** Handles user registration, permissions (Owner, Editor, Drafter), and administrative controls.
3. **Search and Indexing Subsystem:** Centered around the Lucene-based search functionality that allows users to comb through blog content.

### Task Description:

- **Identify Relevant Classes:** Discern the key Java classes and interfaces responsible for the three subsystems mentioned above.
- **Document Functionality:** Create detailed documentation for each identified class, explaining its role and how it interacts with the rest of the subsystem.
- **Create UML Diagrams:** Use PlantUML or StarUML to model the relationships (inheritance, association, composition, etc.).
  - _Requirement:_ Hand-drawn or general drawing tools (draw.io, etc.) will not be considered for final submission.
- **Observations and Comments:** Highlight strengths and weaknesses of the current design.
- **Assumptions:** Explicitly state any simplifications you made while modeling.
- **LLM vs Manual Analysis:** Perform the above steps once without LLM assistance and once with LLM assistance on a small, clearly defined part of any one subsystem. Provide a brief comparative analysis highlighting differences in completeness, correctness, and effort.

## Task 2: Smells and Metrics Analysis (30 Marks)

### Task 2A: Design Smells

Design smells are indicators of deeper architectural problems. While SonarQube detects _code_ smells (fine-grained), you must use these as clues to identify _design_ smells (system-level violations).

- **Task:** Detect 5-7 design smells \*\*\*\*using the tools already mentioned.
- **Tools:** SonarQube is **mandatory**. You are encouraged to supplement this with Designite Java or IDE plugins.
- **Deliverable:** A list of smells with supporting evidence from your tool reports and UML analysis.

> Note: Sonarqube or any automated tool is not perfect, so use your own judgment. The best way to identify design smells is to first make the UML class diagram for the project and try to justify design choices or identify if better ones could have been made.

### Task 2B: Code Metrics Analysis

The goal of this task is to conduct a comprehensive code metrics analysis for the initial state of the project, utilizing appropriate tools such as CodeMR, Checkstyle, PMD, or any other tools deemed suitable. The analysis should provide insights into up to 6 key code metrics, and the implications of these metrics should be discussed. Additionally, consider how these metrics might guide decision-making processes for potential refactoring. Ensure that the metrics you select are diverse and also include OOPs specific metrics (like those of Chidamber and Kemerer).

### Task Description:

- **Code Metrics Analysis**: Employ code analysis tools (e.g., CodeMR, Checkstyle, PMD) to extract up to 6 relevant code metrics for the project.
- **Tools Used**: Clearly state the tools used for the code metrics analysis and ensure that the selected tools provide a reliable and accurate representation of the project’s codebase.
- **Implications Discussion**: For each identified metric, discuss its implications in the context of software quality, maintainability, and potential performance issues. Provide insights into how each metric reflects on the project’s current state.

## Task 3: Refactoring (40 Marks)

> Note: All refactorings must preserve the original behavior of the system. After applying any refactoring, you must ensure that all existing (in-built) test cases in the Apache Roller repository pass successfully. In addition to tests, the core functionality of the affected components should be manually verified to ensure no behavioral regressions are introduced. Refactorings that break tests or system functionality will be considered incorrect, even if they improve code structure or design.

### Task 3A: Manual Refactoring

You previously identified 5-7 design smells in task 2A. Now, the goal is to rectify these issues through code refactoring without fundamentally altering the existing codebase. It’s crucial to emphasize that we’re not discarding the previous code but rather enhancing its design. The goal is for your refactoring to address the design smell you’ve identified.

- **Constraint:** Refactorings must be significant (class-level changes). The refactoring should go beyond trivial changes, and your evaluation will be based on the correctness and significance of the improvements made.

> Note: Trivial changes refer to changes more fine-grained than the class level, like defining variables for repeated constants, wrapping something around a try-catch block, repeatedly extracting methods and so on.

- **Workflow:** For every design issue you intend to fix, you must open a GitHub Issue in your team's repository first. Your grade depends on this documented roadmap.

### Task 3B: Post-Refactoring Metrics

Re-run your metrics analysis. Discuss whether the metrics improved or deteriorated. Is it possible for one metric to improve while another gets worse?

### Task 3C: Automating the Refactoring Pipeline using LLMs

> Note: Keep in mind, you only have to document the changes in the code suggested by LLMs and not apply it in your actual code base. The code base should only contain changes made by you.

Design and implement a script/pipeline (using OpenAI/Gemini APIs) that:

1. **Detects:** Develop a script or tool that periodically scans the GitHub repository for potential design smells.
2. **Refactors:** Implement an automated refactoring module that takes the identified design smells and generates refactored code using LLMs. Ensure that the refactoring process is robust, preserving the functionality of the code while enhancing its design.
3. **PR Generation:** Automatically creates a Pull Request on your repository with the suggested changes. Include detailed information in the pull request, such as the detected design smells, the applied refactoring techniques, and any relevant metrics.

Also provide a flowchart explaining your pipeline better and how it handles the context of large files.

## **Task 4: Agentic Refactoring on a Single File (10 Marks)**

> Note: You only need to document the refactorings suggested by an agentic setup.
>
> The actual codebase should include **only the changes implemented manually by you**.

In this task, you will use an existing agentic refactoring tool/system to generate refactoring suggestions for a single source file from Apache Roller. The focus is on agentic reasoning and suggestions, not on building the agent system.

You may use any agentic environment (e.g., Claude Code, Cursor, Antigravity, etc.). Due to API/cost constraints, you may apply the agentic approach to only a subset of files/modules (use at least 3 or 4 files).

### **Task Description**

Use an agentic refactoring workflow on a single Java source file. **You are not required to implement agents yourself.**

The tool/system should demonstrate (explicitly or implicitly) the following stages:

1. **Smell Identification**
   - Takes a single Java file
   - Optionally uses static analysis output
   - Identifies and selects _design-level_ smells to address
2. **Refactoring Planning**
   - Proposes refactoring strategies for selected smells
   - Briefly explains why the refactoring is appropriate
   - Identifies affected methods/classes
3. **Refactoring Execution**
   - Produces refactored code snippets
   - Ensures syntactic correctness/compilability
   - Clearly distinguishes original vs refactored code

### **Deliverables**

- Name of the agentic tool/system used (brief)
- Prompts/commands used (brief)
- Documentation of suggested refactorings (snippets/diff allowed; **not applied to the entire repo**)

## **Task 5: Comparative Refactoring Analysis (Manual vs LLM vs Agentic) (10 Marks)**

This task provides a unified empirical analysis of refactoring outcomes produced by manual, LLM-assisted, and agentic approaches.

### Task Description

Select 2–3 design smells from your identified list and refactor the same code using all three approaches:

1. **Manual Refactoring (Task 3A)**
   - Performed entirely by the team without LLM assistance
2. **LLM-Assisted Refactoring**
   - Uses exactly one prompt per smell
   - No iterative prompting, memory, tools, or agents
   - The LLM acts as a _single-shot refactoring assistant_
3. **Agentic Refactoring (Task 4)**
   - Uses the agent-based setup designed in Task 4

### Analysis Requirements (Qualitative / Empirical)

For each refactoring, compare the three approaches using the following dimensions:

- **Clarity:** Readability and understandability of the refactored code
- **Conciseness:** Reduction of unnecessary complexity or duplication
- **Design Quality:** Adherence to DRY and SOLID principles
- **Faithfulness:** Preservation of original behavior and intent
- **Architectural Impact:** Whether the refactoring improves or harms the broader design
- **Human vs Automation Judgment:**
  - Where human refactoring was superior
  - Where LLM or agentic refactoring was advantageous
  - Where automation failed or required correction

## Bonus: Benchmarking (5 Marks)

> Note: This bonus will only recoup marks lost in this project. It will not add to your course total, i.e. your project 1 marks will be `min(120, project marks + bonus)`.

Compare two different LLMs (e.g., GPT-4o vs. Claude 3.5 Sonnet) in both non-agentic and agentic settings on:

- Their ability to identify the _same_ design smells you found manually.
- The quality and "compliability" of their refactored code.

## Submission Instructions

The submission for this phase will be through the GitHub classroom. The codebase will be automatically downloaded at the deadline, so ensure that everything is up in time. No extensions will be granted.

In addition to the code changes required, you also need to submit a report containing your responses for each task. The report should be present in the `docs/` directory, titled `project1_<team_number>.pdf`. If you are attempting the bonus, submit a separate document titled `project1_bonus_<team_number>.pdf` containing the corresponding responses. Add these reports and other documents in the `docs/` folder of your repository.

Accurately report the contribution of each team member at the end of the report. This will be considered when evaluating the project.

**Deadlines:**

- **Soft Deadline:** 10th February, 2026, 11:59 PM IST
- **Hard Deadline:** 17th February, 2026, 11:59 PM IST

> Note: Bonus can be submitted till the hard deadline without any penalty. Late days are not applicable for bonus components

To encourage consistency, at least 50% of your total commits must be made before the last week of the soft deadline, i.e., before 3rd February, 2026. Repositories showing most of the work being done close to the deadline may be penalized.

The course policy mentioned on this website will be followed for late submissions and associated penalties/late days.

**Best of luck (start early)!**
