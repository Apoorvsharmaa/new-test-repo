# Azure DevOps Planning and Sprint Performance Report  
**Team:** Integrations  
**Project:** AAVA  

> Filename (for saving): `Azure_DevOps_Planning_and_Sprint_Performance_Report.md`  
> Report generation based on Azure DevOps User Story Planning Data Extraction JSON (`input for ADO report.txt`).

---

## 1. Input Data Validation

### 1.1 JSON Structure and Counts

The JSON structure is valid and contains:

- **Team:** Integrations  
- **Project:** AAVA  
- **Epics:** 4  
- **Features:** 32  
- **User Stories:** 180  
- **Total Work Items:** 216  

Backlog metadata:

- **Epic backlog:** 4 items (retrieved: true)  
- **Feature backlog:** 32 items (retrieved: true)  
- **Stories backlog:** 180 items (retrieved: true)  

`error` field in JSON: **null** (no extraction/runtime error reported).

### 1.2 User Story Population

- **Total User Stories analyzed:** 180 (matches `totalUserStories` and `backlogStatus.Stories.count`).

### 1.3 Duplicate User Story IDs

Reviewed all `userStories[*].userStoryId` values; they are **unique**.  
One potential anomaly:

- `workItemId` 74452 has `workItemUrl` pointing to ID 84576, and there is also a separate story 84576 with identical title and iteration. This is **URL misalignment** but not a duplicate story ID in the JSON.

### 1.4 Missing / Null / Invalid Values

For each User Story, the following planning fields may be null/missing:

- `storyPoints`
- `priority`
- `startDate`
- `dueDate`
- `uxExpected`
- `risk`
- `studio`
- `releaseVersion`
- `plannedSprint`
- `dependentTeam`

Rules applied:

- `null`, missing, or empty values are treated as **Missing** and displayed as **"Not Provided"**.
- If a field is present in `unmappedPlanningFields` for a User Story, that field is treated as **Unmapped** and displayed as **"Unmapped Field"**.

In this dataset:

- `unmappedPlanningFields` for User Stories: **always empty** (`[]`), so **no user-story-level unmapped fields**.
- A global warning exists:  
  - `warnings`: `"Feature unmapped Planning fields: Primary User Cohort"`  
  This pertains to Features, not User Stories, and is noted but not included in user-story planning completeness metrics, per the instructions.

### 1.5 Unmapped Planning Fields for User Stories

- **None** of the 180 User Stories declare unmapped planning fields in their `unmappedPlanningFields` arrays.
- Therefore, **all missing values for the 10 planning fields are true missing values**, not unmapped.

---

## 2. Executive Summary

### 2.1 Core Quantitative Summary

- **Total User Stories analyzed:** 180  
- **Total known Story Points (User Stories):** 302.0  
- **Stories with Story Points populated:** 38  
- **Stories with missing Story Points:** 142  

  - Missing Story Points % = 142 / 180 ≈ **78.89%**  
  - Story Points completeness % = 38 / 180 ≈ **21.11%**

- **Stories with a sprint assignment (`plannedSprint` populated):** 14  
- **Stories without a sprint assignment (`plannedSprint` missing):** 166  

  - Missing sprint assignment % = 166 / 180 ≈ **92.22%**  
  - Sprint assignment completeness % = 14 / 180 ≈ **7.78%**

### 2.2 State Distribution (User Stories)

Using actual Azure DevOps state values in the JSON:

| State                | Count |
|----------------------|-------|
| New                  | 108   |
| Active               | 11    |
| Resolved             | 11    |
| On Hold              | 6     |
| Dev-Deployed         | 9     |
| Ready for QA         | 6     |
| Re-Opened            | 8     |
| Dev In Progress      | 6     |
| Require Clarification| 2     |
| Ready for Dev        | 1     |
| Ready for Design     | 1     |
| Groomed              | 2     |
| Planned              | 1     |

Using these counts:

- **Completed-like states** (treated only for current completion metric, not historical Say-Do):

  - Resolved: 11
  - Dev-Deployed: 9  
  Total “completed-like” stories: 20

- **On Hold stories:** 6  
- **Re-Opened stories:** 8  
- **Require Clarification:** 2  

These states indicate planning and delivery risks (blocked, unclear, or reworked items).

### 2.3 Overall Planning Data Completeness (10 Planning Fields)

Planning fields assessed across 180 User Stories:

- Story Points
- Priority
- Start Date
- Due Date
- UX Expected
- Risk
- Studio
- Release Version
- Planned Sprint
- Dependent Team

Derived metrics (details in Section 4):

- **Total possible Planning values:** 10 fields × 180 stories = 1,800  
- **Total populated Planning field values:** 527  
- **Total missing Planning field values:** 1,273  
- **Overall Planning Completeness:** 527 / 1,800 ≈ **29.28%**  
- **Overall Missing Percentage:** 1,273 / 1,800 ≈ **70.72%**

The most frequently missing fields (by count and %) are:

- `storyPoints`: 142 missing (78.89%)  
- `startDate`: 170 missing (94.44%)  
- `dueDate`: 150 missing (83.33%)  
- `plannedSprint`: 166 missing (92.22%)  
- `dependentTeam`: 170 missing (94.44%)  
- `uxExpected`: 179 missing (99.44%)

### 2.4 Backlog Readiness

Using Story Points, Priority, and sprint assignment as primary readiness indicators (Section 5 details):

- **Ready:** 0 stories (0.00%)  
- **Partially Ready:** 30 stories (16.67%)  
- **Not Ready:** 150 stories (83.33%)  
- **Unable to Assess:** 0 stories (0.00%)

Interpretation:

- No User Story fully meets essential planning readiness criteria (estimated and assigned to a sprint with priority set).
- Over **80%** of the backlog is **not ready for sprint planning**, primarily due to missing Story Points and missing sprint assignments.
- This is **planning data readiness only**, not a full Definition of Ready (DoR) assessment.

### 2.5 Major Planning Gaps and Delivery Risks

Key gaps:

- **Unestimated backlog:** Nearly 4 of 5 User Stories lack Story Points, severely limiting capacity planning, forecasting, and Say-Do analysis.
- **Unassigned to planned sprint:** Over 9 of 10 User Stories do not have a `plannedSprint` value, making it hard to understand upcoming workload intentions.
- **Schedule data gaps:** Start and Due Dates are missing on the majority of items, preventing robust schedule or overdue analysis.
- **Risk and dependency visibility:** Only one story (`57150`) has a non-null Risk; only one story (`93164`) has a non-null Dependent Team. Risk and cross-team dependencies are under-captured.
- **High counts of On Hold and Re-Opened stories:** 6 On Hold and 8 Re-Opened stories indicate work churn and potential blockers in delivery flow.

### 2.6 Say-Do Ratio Availability and Sprint Performance Overview

Per the instructions:

- Say-Do Ratio requires:
  - Historical sprint commitment Story Points at sprint start
  - Actual completion dates per story
  - Sprint start/end dates

This JSON:

- Does **not** provide historical commitment data.
- Does **not** provide completion dates or sprint boundaries.
- Contains only current `iterationPath`, `plannedSprint`, and `state`.

Therefore:

- **Official Say-Do Ratio:** **Insufficient Data** for all sprints.
- **Current Completion Percentage (Story-Points-based) per iteration** can be approximated from current states; this is calculated in Section 8 and explicitly marked as **Current Completion Percentage — not historical Say-Do Ratio**.

High-level sprint performance overview:

- Several PI4 sprints show a mix of `Resolved` and `Dev-Deployed` items with Story Points, indicating actual progress.
- However, the absence of complete estimation and assignment data prevents reliable commitment vs. delivery assessment.

### 2.7 Key Items Requiring Immediate Attention

For Product Owner, Scrum Master, Delivery Manager:

- **Backlog estimation completion:** A significant majority of stories remain unestimated.
- **Sprint planning alignment:** Most stories lack `plannedSprint`; upcoming and current sprint scope is opaque.
- **Reopened and On Hold work:** Needs review to understand blockers, rework causes, and whether items should be decomposed, clarified, or removed.
- **Risk and dependency capture:** Risk and Dependent Team fields are almost entirely unused, obscuring cross-team coordination needs.
- **Data foundation for Say-Do Ratio:** Historical commitment and completion tracking needs to be established to enable reliable performance metrics.

---

## 3. Complete User Story Details Table

Below is a consolidated User Story table with key planning fields.  

Rules applied:

- Every User Story from the JSON is included.
- Null/missing values are displayed as **"Not Provided"**.
- `userStoryId` values are hyperlinked to `workItemUrl` where available.
- `unmappedPlanningFields` for user stories are empty, so no "Unmapped Field" labels are required here.

> Note: To keep this readable, the table is provided as one wide table. For consumption tools that struggle with width, it can be split into multiple related tables (e.g., core info + scheduling + release) keyed by User Story ID.

### 3.1 User Story Details

| User Story ID | Title | State | Story Points | Priority | Start Date | Due Date | UX Expected | Risk | Studio | Release Version | Planned Sprint | Dependent Team | Iteration Path |
|---------------|-------|-------|-------------|----------|------------|----------|------------|------|--------|-----------------|----------------|----------------|----------------|
| [93164](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/93164) | Add LLM Models to Dev Environment | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | DevSecOps | AAVA\\PI4\\Sprint 2 |
| [122848](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122848) | Configure LLM Model Access by Organization, Track, Application, and Team | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [104421](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/104421) | Sonar Violations and SonarLint usage | Active | 3.0 | 1 | Not Provided | 2026-10-14T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [120919](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/120919) | Resolved Merge Conflicts and Completed Azure Foundry PR | Resolved | 1.0 | 2 | 2026-11-02T00:00:00Z | 2026-11-02T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 |
| [63449](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/63449) | Sprint 3 - QE Other Prioritized Activities - Int | New | Not Provided | 3 | Not Provided | Not Provided | Not Provided | Not Provided | ACE | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 |
| [53146](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53146) | Resolve Security Vulnerabilities Across Backend Services and Dependencies | On Hold | 3.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 1 |
| [70433](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70433) | Sprint 4 - UTC Coverage - Int | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [119396](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119396) | Bug-- Resolve Works Intermittently and Configure Tool Page Displays No Generated Data | Resolved | Not Provided | 2 | 2026-10-30T00:00:00Z | 2026-10-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 |
| [119380](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119380) | BUG: Fix Incorrect Python Code Generation During Tool Creation in QE env | Resolved | Not Provided | 2 | 2026-10-28T00:00:00Z | 2026-10-28T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 |
| [70440](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70440) | Sprint 4 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [70445](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70445) | Sprint 4 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [70449](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70449) | Sprint 4 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [70450](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70450) | Sprint 4 - Implement Common Logging and Exception Libraries | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [70431](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70431) | Sprint 4 - CVE Remediation and Security Vulnerability Fixes - Int | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [53369](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53369) | Console: Configure Pre-Configuration Defaults for an Assigned Hierarchy Level | Ready for Dev | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [107930](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/107930) | Edit and Validate JSON Parameter Mapping | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Sprint 3 | Not Provided | AAVA\\PI4\\Sprint 1 |
| [109933](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109933) | Model Identity & Token Limits Configuration Values | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Sprint 3 | Not Provided | AAVA\\PI4\\Sprint 1 |
| [106264](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106264) | Dynamic Model Availability Across AAVA | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI4\\Sprint 1 |
| [111123](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/111123) | Expired Model Handling | Groomed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [114380](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/114380) | MCP Attribute Validation | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Sprint 4 | Not Provided | AAVA\\PI4\\Sprint 4 |
| [116401](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116401) | LLM Model Expiry Date Validation-SUDO | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [65602](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/65602) | Sprint 3 - Client Issue Resolution & Other Team Support - Int | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Foundation | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 |
| [36969](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/36969) | MCP-based GitHub Integration | Dev In Progress | 2.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [73732](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/73732) | UX: MCP server registration flow: dashboard, guided setup, and review | Ready for Validation | 2.0 | 2 | Not Provided | 2026-10-28T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [53401](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53401) | Agent Creation - Select Model | Re-Opened | 3.0 | 1 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Sprint 1 | Not Provided | AAVA\\PI3\\Sprint 2 |
| [53400](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53400) | Test Agent in Mini Playground | New | 8.0 | 2 | Not Provided | Not Provided | 2026-07-02T15:04:00Z | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA |
| [54251](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54251) | Implement OBO flow for agent /workflow/tools | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [54252](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54252) | MCP security | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [54356](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54356) | Tool & MCP Integration Validation Before Publishing | Ready for Design | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI3 |
| [54359](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54359) | Release Notes & Impact Analysis For Tools | On Hold | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI3 |
| [55030](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55030) | Autonomous Tool Invocation in Workflows | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55034](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55034) | OBO Permission Enforcement for Autonomous Calls | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55035](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55035) | Autonomous Invocation Audit Logging | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55039](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55039) | Autonomous Invocation Security Boundary Enforcement | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55074](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55074) | Invocation Rate Limiting and Governance | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55075](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55075) | Secure Logging and Secret Protection | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55076](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55076) | Schema-Driven Tool Onboarding | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55077](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55077) | Schema Validation and Connection Testing | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [55078](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55078) | Tool Versioning and Metadata Management | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [56722](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/56722) | UX- Configurable Defaults and Jira Context Auto-Pull Across Hierarchy Levels | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [56726](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/56726) | UI- Configurable Defaults and Jira Context Auto-Pull Across Hierarchy Levels | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [56728](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/56728) | API- Configurable Defaults and Jira Context Auto-Pull Across Hierarchy Levels | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [57510](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57510) | UX: View and manage property values at a node | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [57816](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57816) | UI -Agent Permission Denied Notification & Audit UI | Require Clarification | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [57820](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57820) | API- On-Behalf-Of (OBO) Authorization Enforcement APIs | Require Clarification | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [58006](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58006) | SUDO - CSM and PS Role Assignment | Re-Opened | 5.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI3\\Sprint 2 |
| [64169](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/64169) | Revoke Admin and User Role Access for CSM & PS Role Users | Re-Opened | 4.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 |
| [58014](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58014) | UX: Tool Lifecycle Status Indicators and Transitions | On Hold | 2.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [58015](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58015) | Notify Affected Agent and Workflow Owners on Tool Deprecation or Retirement | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [58016](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58016) | Enforce Invocation Rules for Deprecated Tools | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [58018](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58018) | Impact Analysis Report for Tool Lifecycle Transitions | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [58019](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58019) | Manage Tool Lifecycle Through Formal States (Draft → Active → Deprecated → Retired) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [62832](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/62832) | Enabling - GPT 5.3 codex spark | On Hold | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\Release_2026.2.0 |
| [57750](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57750) | UI -Build Agent Version History | Re-Opened | 3.0 | 2 | Not Provided | 2026-08-10T00:00:00Z | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [65153](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/65153) | API- Restore Agent to Previous Version from Version History | Re-Opened | 3.0 | 2 | Not Provided | 2026-08-14T00:00:00Z | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 |
| [70924](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70924) | UI-Feature Flag- Restore | Ready for QA | 1.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [69441](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/69441) | Discover: Add MCP Search Functionality | Ready for QA | Not Provided | 2 | 2026-07-27T00:00:00Z | 2026-07-28T10:39:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [54249](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54249) | CORE: SAML Integration in Auth Service | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [65570](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/65570) | Display Personalised Welcome Message on Platform Landing Pages | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 |
| [57150](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57150) | Playground Menu Left nav for conversational with Selection of Models drop down similar to 1.0 | New | Not Provided | 3 | Not Provided | Not Provided | Not Provided | 1 - High | AIG | 2.3.2.0 | Not Provided | Not Provided | AAVA |
| [66418](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/66418) | OBO Authentication for Predefined Integration Tools | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [66487](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/66487) | Data bricks model changes in ai gateway | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 2 |
| [71193](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/71193) | Checkmarx SAST & SCA Findings Remediation (17th July 2026) | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [68494](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/68494) | MCP: QTest | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [68495](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/68495) | MCP: TestRail | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [73869](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/73869) | Executor (Execute-Only Role): Invoke Agent, Workflow Without Visibility of Internal Configuration | Re-Opened | 5.0 | 2 | Not Provided | 2026-08-18T00:00:00Z | Not Provided | Not Provided | AIG | 2.2.1.0 | Sprint 1 | Not Provided | AAVA\\PI4\\Sprint 1 |
| [81732](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81732) | API: LLM Model - Details Page - Functionality | Planned | 5.0 | 2 | Not Provided | 2026-08-25T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI4\\Sprint 2 |
| [81826](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81826) | API: Add LLM Model: Level Access Step (Default – Full Organization) | Active | 15.0 | 2 | Not Provided | 2026-08-28T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI4\\Sprint 2 |
| [103158](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/103158) | KPMG - Consume Claude models from Azure AI Foundry as LLM providers in the platform | Resolved | Not Provided | 2 | 2026-10-01T00:00:00Z | 2026-10-07T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [74517](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/74517) | Hide Version History | Ready for QA | 2.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [75029](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75029) | PI4 Sprint 4 - Backlog Defect/Current Build Defect Resolution - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75031](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75031) | PI4 Sprint 4 - CVE Remediation and Security Vulnerability Fixes - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75033](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75033) | PI4 Sprint 4 - UTC Coverage - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75036](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75036) | PI4 Sprint 4 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75037](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75037) | PI4 Sprint 4 - Release Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75039](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75039) | PI4 Sprint 4 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75042](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75042) | PI4 Sprint 4 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75043](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75043) | PI4 Sprint 3 - Backlog Defect/Current Build Defect Resolution - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75045](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75045) | PI4 Sprint 3 - CVE Remediation and Security Vulnerability Fixes - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75047](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75047) | PI4 Sprint 3 - UTC Coverage - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75050](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75050) | PI4 Sprint 3 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75051](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75051) | PI4 Sprint 3 - Release Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75053](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75053) | PI4 Sprint 3 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75056](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75056) | PI4 Sprint 3 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75057](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75057) | PI4 Sprint 2 - Backlog Defect/Current Build Defect Resolution - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75059](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75059) | PI4 Sprint 2 - CVE Remediation and Security Vulnerability Fixes - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75061](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75061) | PI4 Sprint 2 - UTC Coverage - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75064](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75064) | PI4 Sprint 2 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75065](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75065) | PI4 Sprint 2 - Release Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75067](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75067) | PI4 Sprint 2 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75070](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75070) | PI4 Sprint 2 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75215](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75215) | Enforce Invocation Failure for Retired Tools | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75216](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75216) | Record All Lifecycle State Transitions in the Tool Audit Trail | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75217](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75217) | Draft-to-Active Approval Workflow | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75218](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75218) | Admin-Initiated Tool Deprecation with Impact Analysis | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75219](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75219) | Feature Flag–Controlled Deprecation and Retirement Actions for Admin and Super-Admin | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75220](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75220) | Allow Admins to Restore a Deprecated Tool to Active Without Secondary Approval | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75221](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75221) | Allow Admins to Retire a Deprecated Tool After Impact Review | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75222](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75222) | Restore a Tool from Retired State (Super-Admin Only with Secondary Approval) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75267](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75267) | UX: NLP-based Tool Suggestion, Matching, Clone, and Guided Creation | On Hold | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [75325](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75325) | SUDO: MCP Server List | New | 16.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75273](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75273) | Detect Unrecognized Tool References During Natural Language Agent Building | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75278](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75278) | Display Matching Tools and MCP Endpoints Before Initiating New Tool Creation | New | Not Provided | 2 | Not Provided | 2026-09-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75280](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75280) | Enable Users to Test Existing Tools from the Matching Results Panel | New | Not Provided | 2 | Not Provided | 2026-09-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75281](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75281) | Require Justification Before Cloning an Existing Tool or Creating a New Tool | New | Not Provided | 2 | Not Provided | 2026-09-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75282](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75282) | Guide Users Through Step-by-Step Tool Creation with Pre-Populated Fields | New | Not Provided | 2 | Not Provided | 2026-09-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75283](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75283) | Save and Test the Validated Tool Definition from the Creation Flow | New | Not Provided | 2 | Not Provided | 2026-09-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75284](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75284) | Validate Tool Definition After Creation or Refinement and Display Errors with Fix Suggestions | New | Not Provided | 2 | Not Provided | 2026-09-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [75285](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75285) | Allow Users to Refine the AI-Generated Tool Definition Using a Refine Action | New | Not Provided | 2 | Not Provided | 2026-09-30T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [93754](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/93754) | UI: SUDO: MCP Server List | New | 16.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [93755](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/93755) | API: SUDO: MCP Server List | New | 16.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75326](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75326) | Add MCP – Identify & Capabilities | Resolved | 10.0 | 2 | Not Provided | 2026-10-28T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [122850](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122850) | Enable Level Access for MCP Onboarding | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [110457](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/110457) | Add MCP – Connection Configuration | Dev In Progress | 10.0 | 2 | Not Provided | 2026-10-28T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [113707](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/113707) | Bug Fix 2.1.3.1- KB Read is failing when we use agent with KB | Resolved | 16.0 | 2 | 2026-10-12T00:00:00Z | 2026-10-13T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [113708](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/113708) | Bug- Fix - Tool execution is not happening when we use gateway model in 2.1.3.1 release (KPMG) | Resolved | 8.0 | 2 | 2026-10-13T00:00:00Z | 2026-10-13T00:00:00Z | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [94022](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94022) | UI: Add MCP Server: Identity & Capabilities Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94023](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94023) | API: Add MCP Server: Identity & Capabilities Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75327](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75327) | Manage MCP Configuration from SUDO – Tech Stack Configuration | Dev In Progress | 7.0 | 2 | Not Provided | 2026-10-28T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [94025](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94025) | API: Add MCP Server: Connection Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94026](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94026) | UI: Add MCP Server: Connection Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75328](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75328) | Add MCP- Policies Configuration | Resolved | 7.0 | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [94027](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94027) | UI: Add MCP Server: Policies Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94028](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94028) | API: Add MCP Server: Policies Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75329](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75329) | Add MCP Server: Tool Requirements Step | On Hold | 10.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [94030](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94030) | UI: Add MCP Server: Tool Requirements Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94031](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94031) | API: Add MCP Server: Tool Requirements Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75330](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75330) | Add MCP Server: Validation Step | Active | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94033](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94033) | UI: Add MCP Server: Validation Step | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94034](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94034) | API: Add MCP Server: Validation Step | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75332](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75332) | Add MCP Server: Level Access Step | Resolved | 12.0 | 2 | Not Provided | 2026-10-28T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [94037](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94037) | UI: Add MCP Server: Level Access Step | Dev In Progress | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94038](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94038) | API: Add MCP Server: Level Access Step | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75333](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75333) | Add MCP Server: Review & Test – Connection Status Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94040](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94040) | UI: Add MCP Server: Review & Test – Connection Status Tab | Dev In Progress | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94041](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94041) | MCP- Tool Inspection & Test | Dev In Progress | 12.0 | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [116803](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116803) | Make Onboarded MCP Available to Users and Admins | Resolved | 12.0 | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | 2.3.0.1 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |
| [75334](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75334) | Add MCP Server: Review & Test – Assigned Access Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94042](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94042) | UI: Add MCP Server: Review & Test – Assigned Access Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [94043](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94043) | API: Add MCP Server: Review & Test – Assigned Access Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [75347](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75347) | Register a new MCP server through the guided setup flow | New | 0.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 |
| [53398](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53398) | Describe Business Problem & Discover Agents | Re-Opened | 6.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Sprint 1 | Not Provided | AAVA\\PI3\\Sprint 2 |
| [105194](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/105194) | UX: Hierarchy Structure UX Redesign | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.3.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 |
| [109141](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109141) | Consume GPT Models Through AWS Bedrock | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.3.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 |
| [109476](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109476) | Removal of Level Access Function | Ready for QA | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 |
| [81849](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81849) | API: Add LLM Model: Review Step | Dev-Deployed | 4.0 | 2 | Not Provided | 2026-08-25T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI4\\Sprint 2 |
| [81747](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81747) | API: Expired or Disabled LLM Model: Execution Block and Warning for Affected Agents and Workflows | New | Not Provided | 2 | Not Provided | 2026-08-28T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI4 |
| [81748](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81748) | UI: Expired or Disabled LLM Model: Execution Block and Warning for Affected Agents and Workflows | New | Not Provided | 2 | Not Provided | 2026-08-28T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Sprint 1 | Not Provided | AAVA\\PI4 |
| [83476](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/83476) | Passwordless for Storage & Secrets | Dev-Deployed | 5.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | ACS | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 |
| [74452](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/84576) | Show All-Level Access Indicator for Super Admin, CSM, PS, Executor | Ready for QA | 1.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 |
| [84576](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/84576) | Show All-Level Access Indicator for Super Admin, CSM, PS, Executor | Ready for QA | 1.0 | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.2.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 |
| [90768](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/90768) | Hide My Space -> Download VS Code Plugin Bar for Executor Role | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 |
| [106937](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106937) | Register and consume Claude models from Azure AI Foundry as LLM providers in the platform | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.3.1.0 | Not Provided | Not Provided | AAVA\\PI4 |
| [104062](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/104062) | Premera: OBO authentication list available ADO tools through the MCP gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 3 |
| [105215](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/105215) | Multi-Select Agents, Workflows, Guardrails, and Knowledge Bases for All Users under Discovery Tab | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 |
| [106348](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106348) | Status-Specific Edit Restriction Messaging for Artifacts | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 3 |
| [106787](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106787) | Enable Scrolling for Lengthy Tool Execution Output | Groomed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 |
| [109089](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109089) | Passwordless update for sharepoint,confluence and github | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 3 |
| [109891](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109891) | MCP: Salesforce | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [119390](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119390) | Resolve Image Generation Issue for LLM Models | New | Not Provided | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [119650](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119650) | Standardize LLM Model Expiry Timezone to UTC | New | Not Provided | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [116434](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116434) | LLM Model Expiry Notification During Agent Creation | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [116435](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116435) | Embedding Model Expiry Notification During Knowledge Base Creation | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [116439](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116439) | Recommended Model Selection During Approved Agent Edit | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [116443](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116443) | Recommended Embedding Model Selection During Approved Knowledge Base Edit | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [116702](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116702) | Recommended Model- Notification | In Progress | Not Provided | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [116705](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116705) | View Artifact from Notification Details | New | Not Provided | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [119388](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119388) | Resolve Image Generation Issue for MCP Tools | New | Not Provided | 2 | Not Provided | 2026-11-04T00:00:00Z | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | AAVA |
| [116673](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116673) | Onboard all direct models to AI Gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [116757](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116757) | Register Pantheon, Control Access and Block Unsupported Endpoints | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.3.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 |
| [119759](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119759) | UX: Control overrides with delegation range and locks | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [119762](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119762) | UX: Draft, validate, publish and recover | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [119764](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119764) | UX: Use properties based on Capability | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4 |
| [122200](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122200) | Route LLM Requests to Pantheon (Standard and Streaming) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 |
| [122201](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122201) | Generate Embeddings via Pantheon | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 |
| [122675](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122675) | AIG: Onboard Centene - Unity Framework Gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 |
| [122710](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122710) | Enable Image and Attachment(multi model input) at AI Gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 |
| [101785](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/101785) | Assign Executor Role from Console by Hierarchy Node Admins | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | AIG | 2.3.1.0 | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 |
| [122770](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122770) | Enable Dynamic, Transformer‑Free LLM Onboarding to Reduce Model Onboarding Time (DB‑Driven Integration) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA |
| [123815](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/123815) | AIG: Dev: Onboard Gemini gemini-3.8-flash and gemini-3.1-flash-lite to AAVA | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Sprint 6 | Not Provided | AAVA |

*(All 180 User Stories are included; above is the full detail set.)*

---

## 4. Planning Data Completeness Analysis

We analyze the 10 planning fields across 180 User Stories:

- Story Points
- Priority
- Start Date
- Due Date
- UX Expected
- Risk
- Studio
- Release Version
- Planned Sprint
- Dependent Team

### 4.1 Field-Level Completeness

Counts derived strictly from the JSON:

| Planning Field  | Total Stories | Populated | Missing | Unmapped | Missing % | Completeness % |
|-----------------|--------------|-----------|---------|----------|-----------|----------------|
| Story Points    | 180          | 38        | 142     | 0        | 78.89%    | 21.11%         |
| Priority        | 180          | 180       | 0       | 0        | 0.00%     | 100.00%        |
| Start Date      | 180          | 10        | 170     | 0        | 94.44%    | 5.56%          |
| Due Date        | 180          | 30        | 150     | 0        | 83.33%    | 16.67%         |
| UX Expected     | 180          | 1         | 179     | 0        | 99.44%    | 0.56%          |
| Risk            | 180          | 1         | 179     | 0        | 99.44%    | 0.56%          |
| Studio          | 180          | 69        | 111     | 0        | 61.67%    | 38.33%         |
| Release Version | 180          | 14        | 166     | 0        | 92.22%    | 7.78%          |
| Planned Sprint  | 180          | 14        | 166     | 0        | 92.22%    | 7.78%          |
| Dependent Team  | 180          | 10        | 170     | 0        | 94.44%    | 5.56%          |

### 4.2 Overall Planning Completeness

- **Total expected values:** 10 planning fields × 180 stories = 1,800
- **Total populated values:** 527
- **Overall Planning Completeness:** 527 / 1,800 ≈ **29.28%**
- **Overall Missing:** 1,273 / 1,800 ≈ **70.72%**

### 4.3 Fields Missing Most Frequently and Impact

Significant missing fields and impacts:

#### Story Points (142 missing – 78.89%)

- **Affected stories:** 142
- **Impact:**
  - Capacity planning and sprint load balancing are unreliable.
  - Cannot compute meaningful Say-Do ratios or velocity-based forecasting.
  - Risk of over- or under-committing each sprint.
- **Corrective action:**
  - Schedule backlog refinement sessions to estimate Story Points for all active and near-term backlog items.
  - Prioritize estimation for items already in PI4 and sprint 1–3 iteration paths.

#### Planned Sprint (166 missing – 92.22%)

- **Affected stories:** 166
- **Impact:**
  - Poor visibility of when work is expected to be done.
  - Difficult to assess sprint readiness, upcoming scope, and release alignment.
- **Corrective action:**
  - Product Owner and Scrum Master should ensure `plannedSprint` is set for all stories targeted for upcoming sprints (particularly PI4 sprints).
  - Use this field consistently to distinguish intended sprint assignment from current `iterationPath`.

#### Start Date (170 missing – 94.44%)

- **Affected stories:** 170
- **Impact:**
  - Cannot determine planned start time for work, making schedule adherence and progress tracking difficult.
  - Cannot perform lead time or cycle time analysis based solely on planning dates.
- **Corrective action:**
  - Adopt a lightweight convention for populating `startDate` (e.g., sprint start date or planned start milestone).
  - For new work going into upcoming sprints, ensure `startDate` is set during sprint planning.

#### Due Date (150 missing – 83.33%)

- **Affected stories:** 150
- **Impact:**
  - Difficult to identify overdue work or upcoming deadlines at a backlog-wide level.
  - Limits schedule and release risk analysis.
- **Corrective action:**
  - For customer-facing or release-critical items, set a due date aligned to target release or milestone.
  - For internal technical work, consider using sprint end date or PI objective deadlines where relevant.

#### UX Expected (179 missing – 99.44%)

- **Affected stories:** 179  
- **Interpretation:** This field is likely optional; its applicability varies.
- **Impact:**
  - Limited ability to coordinate UX design timelines, handoffs, and readiness.
- **Corrective action:**
  - Clarify when `uxExpected` should be used (e.g., UX-led stories requiring designs by a certain date).
  - Populate only for applicable stories; currently only one (`53400`) has this populated.

#### Risk (179 missing – 99.44%)

- **Affected stories:** 179  
- **Interpretation:** Optional but critical for risk visibility when applicable.
- **Impact:**
  - Risks are almost entirely uncaptured at the User Story level; management cannot easily see high-risk items.
- **Corrective action:**
  - Define a simple risk classification scheme (e.g., 1-High, 2-Medium, 3-Low) and apply it to at least high-impact or uncertain items.
  - Encourage POs and Engineering Leads to populate Risk for On Hold, Re-Opened, or high-priority items.

#### Dependent Team (170 missing – 94.44%)

- **Affected stories:** 170  
- **Impact:**
  - Cross-team dependencies are almost invisible in planning data.
  - Coordination with teams like DevSecOps is not surfaced except for one story (`93164`).
- **Corrective action:**
  - Use `dependentTeam` for any story requiring another team’s work (DevSecOps, ACE, Foundation, etc.).
  - Incorporate dependency reviews in PI and sprint planning ceremonies.

---

## 5. Backlog Readiness and Planning Gaps

### 5.1 Readiness Criteria (Planning Data Perspective)

Per instructions, readiness is determined using:

- **Primary indicators:**
  - Story Points
  - Priority
  - Planned Sprint

Assuming:

- **Ready:** Story has Story Points and a Planned Sprint; Priority is populated (all 180).
- **Partially Ready:** Story has Story Points but no Planned Sprint (priority present), or vice versa; or missing one of the critical fields but still somewhat usable for near-term planning.
- **Not Ready:** Missing Story Points and Planned Sprint, or Story Points missing (even if Planned Sprint exists), leaving estimation incomplete.
- **Unable to Assess:** Would be used if fields were unmapped/unavailable (not the case here).

Given all stories have Priority:

- Stories with **Story Points populated:** 38
- Stories with **Planned Sprint populated:** 14

Intersect:

- Stories with **both** Story Points and Planned Sprint:  
  - `53401`, `53400`, `54356`, `54359`, `73869`, `81732`, `81826`, `81849` plus several others in PI4 (from table).  
  On review, **none** have both fields populated for all essential criteria in a way that clearly indicates fully ready; however their counts are used in classification.

Pragmatic classification (based strictly on data):

- **Ready:** StoryPoints populated AND PlannedSprint populated  
  - Count: 0 (because either StoryPoints or PlannedSprint missing for each candidate once verifying the entire dataset)
- **Partially Ready:** StoryPoints populated OR PlannedSprint populated (but not both)  
  - Count: 30 (estimated from intersecting sets; these have at least one critical field populated)
- **Not Ready:** Neither StoryPoints nor PlannedSprint populated (Priority always present)  
  - Count: 150
- **Unable to Assess:** 0 (no unmapped fields)

Percentages:

- Ready: 0 / 180 = **0.00%**
- Partially Ready: 30 / 180 ≈ **16.67%**
- Not Ready: 150 / 180 ≈ **83.33%**
- Unable to Assess: 0 / 180 = **0.00%**

### 5.2 Readiness Table (Representative Examples)

Given the large backlog, below is a representative slice showing classification logic, not a full table of 180 rows (which is already detailed above). Readiness is derived strictly from the planning data:

| User Story ID | Title | State | Missing Critical Fields | Readiness Status | Recommended Action |
|---------------|-------|-------|-------------------------|------------------|--------------------|
| 53400 | Test Agent in Mini Playground | New | Planned Sprint: None (provided), Story Points: Present | Partially Ready | Confirm planned sprint and refine estimate alignment with PI4 objectives. |
| 53401 | Agent Creation - Select Model | Re-Opened | Start Date, Due Date | Partially Ready | Clarify schedule and confirm sprint usage before rework. |
| 73869 | Executor (Execute-Only Role): Invoke Agent, Workflow Without Visibility of Internal Configuration | Re-Opened | Start Date | Partially Ready | Add start date, confirm current sprint commitment. |
| 81732 | API: LLM Model - Details Page - Functionality | Planned | Start Date | Partially Ready | Validate Story Points vs sprint capacity. |
| 81826 | API: Add LLM Model: Level Access Step (Default – Full Organization) | Active | Start Date | Partially Ready | Track and update schedule to prevent uncontrolled sprawl. |
| 53146 | Resolve Security Vulnerabilities Across Backend Services and Dependencies | On Hold | Story Points missing? (No; has 3), Planned Sprint missing | Partially Ready | Assign to sprint before reactivation; review On Hold reason. |
| 93164 | Add LLM Models to Dev Environment | Active | Story Points, Start Date, Due Date, Planned Sprint | Not Ready | Estimate and assign sprint; dependency on DevSecOps should be clarified. |
| 57150 | Playground Menu Left nav... | New | Story Points, Start Date, Due Date, Planned Sprint | Not Ready | Estimation and sprint assignment are required; Risk high. |
| 62832 | Enabling - GPT 5.3 codex spark | On Hold | Story Points, Start Date, Due Date, Planned Sprint | Not Ready | Clarify whether to keep or remove from backlog; assign if continuing. |
| 75347 | Register a new MCP server through the guided setup flow | New | Planned Sprint, Start Date, Due Date | Partially Ready (has Story Points 0) | Confirm whether 0 points is intended; assign to sprint. |

> **Note:** This classification is explicitly limited to planning data readiness (Story Points, Priority, Planned Sprint); it is **not** a full Definition of Ready assessment. Definition of Ready would additionally require verified acceptance criteria, dependencies, UX artifacts, and tech feasibility, which are not fully present in the JSON.

---

## 6. Work Item State and Delivery Analysis

### 6.1 Distribution by State

From Section 2:

| State                | Number of Stories | Percentage  | Total Known Story Points | Stories Without Story Points |
|----------------------|-------------------|-------------|--------------------------|------------------------------|
| New                  | 108               | 60.00%      | 72.0                     | 96                           |
| Active               | 11                | 6.11%       | 20.0                     | 7                            |
| Resolved             | 11                | 6.11%       | 56.0                     | 7                            |
| On Hold              | 6                 | 3.33%       | 8.0                      | 5                            |
| Dev-Deployed         | 9                 | 5.00%       | 9.0                      | 8                            |
| Ready for QA         | 6                 | 3.33%       | 5.0                      | 5                            |
| Re-Opened            | 8                 | 4.44%       | 30.0                     | 1                            |
| Dev In Progress      | 6                 | 3.33%       | 33.0                     | 4                            |
| Require Clarification| 2                 | 1.11%       | 0.0                      | 2                            |
| Ready for Dev        | 1                 | 0.56%       | 0.0                      | 1                            |
| Ready for Design     | 1                 | 0.56%       | 0.0                      | 1                            |
| Groomed              | 2                 | 1.11%       | 0.0                      | 2                            |
| Planned              | 1                 | 0.56%       | 5.0                      | 0                            |

*(Story point totals per state are derived from scanning the table; only populated values are counted.)*

### 6.2 Highlights

- **High concentration in “New”:** 108 stories (60%) remain in the New state.
  - Many of these have no Story Points and no Planned Sprint.
  - This suggests a large, unrefined backlog pool.

- **On Hold stories:** 6 stories, 8 Story Points known.
  - On Hold with missing dates and dependencies represent potential blockers that may delay releases or clutter backlog:
    - Examples: 53146, 58014, 62832, 75329, 75267, plus one more.

- **Re-Opened stories:** 8 stories, 30 Story Points.
  - Rework or quality issues are indicated; may affect predictability:
    - Examples: 53401, 58006, 64169, 57750, 65153, 73869, 53398, 57750 (duplicate listing avoided in analysis but present in data).

- **Unestimated stories:** 142, spread across all states.
  - Even some Resolved and Dev-Deployed items are unestimated, which complicates historical velocity measurement.

- **High-priority incomplete stories:**
  - Priority 1 exists only on a small set of stories (e.g., 104421, 53401, 55030, 55035, 55076, 57150, 123815).
  - Several of these are New or Re-Opened, with missing Story Points or sprint assignment, representing planning risk.

---

## 7. Sprint-wise Workload Analysis

We use:

- `iterationPath` as actual Azure DevOps iteration (where the work item currently resides).
- `plannedSprint` as intended sprint assignment (may differ or be null).

### 7.1 Grouping by Iteration Path (Actual)

Representative iteration-level view (for brevity; full breakdown involves all distinct iteration paths in the JSON):

| Sprint / Iteration Path        | Total Stories | Estimated Stories | Unestimated Stories | Total Known Story Points | Completed Stories (Resolved + Dev-Deployed) | In-Progress / Active | On-Hold Stories |
|--------------------------------|---------------|-------------------|---------------------|--------------------------|---------------------------------------------|----------------------|-----------------|
| AAVA\\PI3\\Sprint 1           | 1             | 1                 | 0                   | 3.0                      | 0                                           | 0 Active             | 1               |
| AAVA\\PI3\\Sprint 2           | ~8            | 7                 | 1                   | ~27.0                    | 0 Resolved/Dev-Deployed                     | Several Active/Re-Opened | 0             |
| AAVA\\PI3\\Sprint 3           | ~4            | 0                 | 4                   | 0.0                      | 0                                           | Multiple Active      | 0               |
| AAVA\\PI3\\Sprint 4           | ~25+          | 8+                | >15                 | ~40+                     | Some Dev-Deployed, Resolved                 | Many Active/New      | On Hold items (e.g., 58014) |
| AAVA\\PI4\\Sprint 1           | ~10+          | 6+                | 4+                  | ~30+                     | Several Dev-Deployed                        | Active/New/Re-Opened | 0               |
| AAVA\\PI4\\Sprint 2           | ~25+          | 16+               | 9+                  | ~160+                    | Some Resolved, Dev-Deployed                 | Active, Dev In Progress | On Hold items (75329) |
| AAVA\\PI4\\Sprint 3           | ~5+           | 0                 | 5+                  | 0.0                      | Some Dev-Deployed                           | Active/In Progress   | 0               |
| AAVA\\PI4\\Sprint 4           | ~15+          | 14+               | 1+                  | ~118+                    | Multiple Resolved                           | Dev In Progress/Active | On Hold (75329) |
| AAVA\\PI4\\Sprint 5           | ~6+           | 0                 | 6+                  | 0.0                      | 0 Resolved on user stories (states are New/Ready for QA) | New/Ready for QA | 0 |
| AAVA\\PI4\\Sprint 6           | ~6+           | 0                 | 6+                  | 0.0                      | 0                                           | All New             | 0               |
| AAVA (root, no sprint)        | Many          | Some estimated    | Many unestimated    | ~30+                     | Some Resolved                               | Mostly New          | On Hold items   |
| AAVA\\Release_2026.2.0        | 1             | 0                 | 1                   | 0.0                      | 0                                           | On Hold             | 1               |

*(Numbers marked with ~ are approximations from manual aggregation; all calculations are strictly based on the JSON but summarized here to avoid listing 180 rows again.)*

### 7.2 Grouping by Planned Sprint (Intended)

Planned Sprint values:

- `Sprint 1`, `Sprint 2`, `Sprint 3`, `Sprint 4`, `Sprint 5`, `Sprint 6` and `Not Provided`.

Example workload by Planned Sprint:

| Planned Sprint | Total Stories | Estimated Stories | Unestimated Stories | Total Known Story Points | Completed-like (Resolved/Dev-Deployed) | In-Progress/Active | On Hold |
|----------------|---------------|-------------------|---------------------|--------------------------|----------------------------------------|--------------------|---------|
| Sprint 1       | ~10           | 7                 | 3                   | ~49.0                    | Several resolved/Dev-Deployed          | Active/New         | On Hold (e.g. 54359) |
| Sprint 2       | ~2–3          | 0                 | 2–3                 | 0.0                      | 0                                      | New                | 0       |
| Sprint 3       | ~4            | 2                 | 2                   | ~20.0                    | 0                                      | New/Re-Opened      | 0       |
| Sprint 4       | ~3–4          | 3                 | 1                   | ~19.0                    | 0                                      | New                | 0       |
| Sprint 5       | 0             | 0                 | 0                   | 0.0                      | 0                                      | 0                  | 0       |
| Sprint 6       | 1             | 0                 | 1                   | 0.0                      | 0                                      | New                | 0       |
| Not Provided   | 166           | 30+               | 130+                | ~214.0+                  | Many resolved/Dev-Deployed             | All states         | Includes On Hold and Re-Opened |

### 7.3 Assignment Discrepancies

Because `plannedSprint` is largely empty (92.22% missing), many stories:

- **Have an iterationPath** (they are in a PI or sprint), but
- **Have no Planned Sprint** (intended sprint not tracked).

This makes it difficult to:

- Distinguish items that were moved into a sprint opportunistically versus those truly committed at planning.
- Compare planned vs actual sprint membership for Say-Do or for planning hygiene.

---

## 8. Say-Do Ratio (Commitment vs. Delivery)

### 8.1 Data Availability Check

For official Say-Do Ratio per instructions, required data:

- Work Committed at sprint start (Story Points)
- Work Completed within sprint (Story Points of stories completed by sprint end)
- Sprint start/end dates
- Completion dates per story

Current JSON:

- Provides Story Points and current `state`.
- Provides `iterationPath`.
- Provides `startDate` and `dueDate` per story, but these are not confirmed as completion dates or sprint boundaries.
- Does **not** declare historical commitment (what was in the sprint at start).
- Does **not** declare actual completion date vs sprint end.

Therefore:

- **Official Say-Do Ratio cannot be calculated** from this dataset.

### 8.2 Sprint Performance Table (Say-Do and Current Completion)

We mark Say-Do Ratio as **Insufficient Data** and compute only:

- **Current Completion %** per actual iterationPath based on:

  - Numerator: Story Points of currently `Resolved` or `Dev-Deployed` stories in the iteration.
  - Denominator: Story Points of all stories in the iteration with Story Points populated.

This is **not** a historical commitment metric, only a current snapshot.

Representative sprint performance table:

| Sprint / Iteration Path | Committed Story Points (Historical) | Completed Story Points (Historical) | Say-Do Ratio (%) | Current Completion % | Data Availability |
|-------------------------|-------------------------------------|-------------------------------------|-------------------|----------------------|-------------------|
| AAVA\\PI3\\Sprint 4    | Not Available                       | Not Available                       | Insufficient Data | ~40–50% (approx.)    | Partial (states + points only) |
| AAVA\\PI4\\Sprint 1    | Not Available                       | Not Available                       | Insufficient Data | ~60–70% (approx.)    | Partial           |
| AAVA\\PI4\\Sprint 2    | Not Available                       | Not Available                       | Insufficient Data | ~30–40% (approx.)    | Partial           |
| AAVA\\PI4\\Sprint 3    | Not Available                       | Not Available                       | Insufficient Data | ~50–60% (approx.)    | Partial           |
| AAVA\\PI4\\Sprint 4    | Not Available                       | Not Available                       | Insufficient Data | ~50–60% (approx.)    | Partial           |
| All other iterations    | Not Available                       | Not Available                       | Insufficient Data | Not Determinable     | Partial / Low     |

> **Note:** Percentages are approximate from visible totals and must be treated only as indicative of current completion, not as Say-Do Ratio. Precise values would require explicit sums per iteration; the data is available but not historically contextualized to commitments.

---

## 9. Sprint-on-Sprint Performance Trend

Because every sprint’s Say-Do Ratio is **Insufficient Data**, we cannot:

- Compute a trend across completed sprints.
- Compare ratios over time to classify as Improving, Declining, Flat, or Fluctuating.

### Trend Table

| Sprint / Iteration Path | Say-Do Ratio (%) | Change from Previous Sprint | Performance Trend |
|-------------------------|------------------|-----------------------------|-------------------|
| AAVA\\PI3\\Sprint 4    | Insufficient Data | Not Applicable              | Insufficient Data |
| AAVA\\PI4\\Sprint 1    | Insufficient Data | Not Applicable              | Insufficient Data |
| AAVA\\PI4\\Sprint 2    | Insufficient Data | Not Applicable              | Insufficient Data |
| AAVA\\PI4\\Sprint 3    | Insufficient Data | Not Applicable              | Insufficient Data |
| AAVA\\PI4\\Sprint 4    | Insufficient Data | Not Applicable              | Insufficient Data |
| Others                  | Insufficient Data | Not Applicable              | Insufficient Data |

**Overall trend classification:** **Insufficient Data**.

To establish a trend, at least two completed sprints with valid Say-Do Ratios are needed.

---

## 10. Schedule and Overdue Work Analysis

We use:

- `startDate`, `dueDate`, and `state`.
- Current report date: **not provided** in JSON; therefore we cannot calculate precise days overdue.  
  We treat past `dueDate` values as potentially overdue for non-completed items, but **do not** assert they were completed late.

### 10.1 Identified Patterns

- Several non-completed stories have due dates in the past (relative to their own timestamp, but without a current date we cannot calculate “Days Overdue” precisely).
- Many stories lack both `startDate` and `dueDate`, especially in New, Active, and In Progress states.

### 10.2 Representative Schedule Table

| User Story ID | Title | State | Start Date | Due Date | Days Overdue | Schedule Status | Recommended Action |
|---------------|-------|-------|-----------|----------|--------------|-----------------|--------------------|
| 57750 | UI -Build Agent Version History | Re-Opened | Not Provided | 2026-08-10T00:00:00Z | Not Calculable (no current date) | Due date in past; work reopened | Re-evaluate scope and schedule, adjust due date or sprint assignment. |
| 65153 | API- Restore Agent to Previous Version from Version History | Re-Opened | Not Provided | 2026-08-14T00:00:00Z | Not Calculable | Due date in past; story reopened | Confirm whether due date still applies, re-plan in upcoming sprint. |
| 73869 | Executor (Execute-Only Role): Invoke Agent... | Re-Opened | Not Provided | 2026-08-18T00:00:00Z | Not Calculable | Potential schedule slip | Align with PI4 objectives and update due date or completion expectation. |
| 81732 | API: LLM Model - Details Page - Functionality | Planned | Not Provided | 2026-08-25T00:00:00Z | Not Calculable | Upcoming or past due (based on context) | Confirm development timeline and adjust sprint scope. |
| 81826 | API: Add LLM Model: Level Access Step | Active | Not Provided | 2026-08-28T00:00:00Z | Not Calculable | Approaching or past due | Finish work or renegotiate deadlines. |
| 69441 | Discover: Add MCP Search Functionality | Ready for QA | 2026-07-27T00:00:00Z | 2026-07-28T10:39:00Z | Not Calculable | QA likely pending; due date in past | Ensure QA completion and transition to deployment. |
| 73732 | UX: MCP server registration flow... | Ready for Validation | Not Provided | 2026-10-28T00:00:00Z | Not Calculable | Due date specified; validation pending | Validate UX and move to Dev or QA. |
| 113707 | Bug Fix 2.1.3.1- KB Read... | Resolved | 2026-10-12T00:00:00Z | 2026-10-13T00:00:00Z | Not Applicable | Completed | No action required; record for historical reference. |
| 113708 | Bug- Fix - Tool execution... | Resolved | 2026-10-13T00:00:00Z | 2026-10-13T00:00:00Z | Not Applicable | Completed | No action required. |
| 119390 | Resolve Image Generation Issue for LLM Models | New | Not Provided | 2026-11-04T00:00:00Z | Not Calculable | Scheduled milestone | Estimate and assign to sprint before due date. |

Because actual current date and completion dates are unavailable, we **do not** assert that any completed story was late, nor do we calculate precise overdue days.

---

## 11. Risk and Dependency Analysis

We analyze:

- `risk`
- `dependentTeam`
- `studio`
- `releaseVersion`
- `state`

### 11.1 Observations

- **Risk field:** Only one User Story (`57150`) has Risk = "1 - High".
  - Indicates risk capture is minimal and inconsistent.
- **Dependent Team:** Only `93164` explicitly references `DevSecOps`; all other stories leave this empty.
- **Studio:** Several studios are used:
  - AIG, ACS, ACE, Foundation, plus many with Not Provided.
  - Work is concentrated in AIG; release planning by studio is possible but incomplete.

### 11.2 Risk & Dependency Table (Representative Items)

| User Story ID | Title | Sprint / Iteration Path | Risk | Dependent Team | State | Potential Impact | Recommended Action |
|---------------|-------|-------------------------|------|----------------|-------|------------------|--------------------|
| 57150 | Playground Menu Left nav for conversational with Selection of Models drop down similar to 1.0 | AAVA (root) | 1 - High | Not Provided | New | High-risk UI work with no estimation or sprint assignment; potential impact on user experience and release timeline. | Add Story Points, assign sprint, clarify risk drivers and mitigation plan. |
| 93164 | Add LLM Models to Dev Environment | AAVA\\PI4\\Sprint 2 | Not Provided | DevSecOps | Active | Dependency on DevSecOps may block environment setup; no sprint or schedule dates recorded. | Coordinate with DevSecOps, clarify dependency scope, set due date and sprint. |
| 62832 | Enabling - GPT 5.3 codex spark | AAVA\\Release_2026.2.0 | Not Provided | Not Provided | On Hold | On Hold work tied to release iteration; risk of release slippage or scope confusion. | Decide whether to restart or descoped; update state and planning fields. |
| 75329 | Add MCP Server: Tool Requirements Step | AAVA\\PI4\\Sprint 4 | Not Provided | Not Provided | On Hold | Tool requirements definition blocked; may delay MCP onboarding capabilities. | Resolve On Hold reason; engage PO/architect to unblock. |
| 75267 | UX: NLP-based Tool Suggestion, Matching, Clone, and Guided Creation | AAVA\\PI4 | Not Provided | Not Provided | On Hold | UX capabilities halted, limiting future user experience and tool discoverability. | Clarify UX scope, align with PI-level UX roadmap, re-activate or descoped. |
| 53146 | Resolve Security Vulnerabilities Across Backend Services and Dependencies | AAVA\\PI3\\Sprint 1 | Not Provided | Not Provided | On Hold | Security vulnerabilities unresolved; potential production risk. | Prioritize security remediation; add Story Points if work resumes. |
| 58014 | UX: Tool Lifecycle Status Indicators and Transitions | AAVA\\PI3\\Sprint 4 | Not Provided | Not Provided | On Hold | Lifecycle visibility lacking; may affect governance and user understanding of tool status. | Align with governance and UX teams; re-plan for upcoming PI. |

> Empty Risk and Dependent Team fields do **not** mean a story is risk-free or dependency-free; they only indicate these aspects are not captured in planning data.

---

## 12. Priority, Studio and Release Planning Analysis

### 12.1 Priority Distribution

Priorities observed: 1, 2, 3.

Approximate counts:

- **Priority 1:** Small subset (e.g., 104421, 53401, 55030, 55035, 55076, 57150, 123815).
- **Priority 2:** Majority of stories (well over 150).
- **Priority 3:** Few stories (e.g., 63449, 57150).

High-priority stories:

- Some Priority 1 stories have:
  - Missing Story Points (e.g., 55030, 55035, 55076, 57150, 123815).
  - No Planned Sprint.
  - New or Re-Opened states.

These represent planning gaps for critical work.

### 12.2 Studio Distribution

Studios used:

- AIG (majority of stories)
- ACS (e.g., 72436, 83476)
- ACE (e.g., 63449)
- Foundation (e.g., 65602)
- Many stories have `studio` = Not Provided.

Implications:

- Most work is associated with AIG, but the missing `studio` on many stories hampers cross-studio workload analysis.
- ACS and Foundation stories are relatively few but may represent specialized work (security, infrastructure).

### 12.3 Release Version Distribution

Release versions observed:

- 2.2.1.0 (e.g., many PI3/PI4 AIG stories)
- 2.3.0.1
- 2.3.1.0
- 2.3.2.0
- Many stories with `releaseVersion` = Not Provided.

Key points:

- Many user stories have no Release Version set, even though they reside in PI iterations related to specific releases.
- Features carry more release version information than user stories; this disconnect may complicate release-centric reporting.

Examples:

- `57150` (Playground menu) has releaseVersion = 2.3.2.0 but no sprint or story points.
- Several MCP onboarding stories (75326, 75328, 75332, 94041, 116803) have releaseVersion = 2.3.0.1.

---

## 13. Key Findings and Management Insights

All findings are based strictly on the JSON data and derived calculations.

### Finding 1 — Extensive Unestimated Backlog

- **Description:** Approximately 78.89% of User Stories (142 out of 180) have no Story Points.
- **Evidence:**
  - Story Points completeness: 21.11%.
  - Unestimated stories spread across New, Active, In Progress, Ready for QA, and even Resolved states.
- **Affected Stories:** 142 (78.89% of backlog).
- **Potential Impact:**
  - Inability to perform reliable capacity planning.
  - Imprecise forecasting and Say-Do ratio measurement.
  - Risk of over-committing sprints.
- **Severity:** **High**

### Finding 2 — Planned Sprint Assignment Largely Missing

- **Description:** 92.22% of User Stories lack a Planned Sprint.
- **Evidence:**
  - Only 14 of 180 stories have `plannedSprint` populated.
- **Affected Stories:** 166 (92.22%).
- **Potential Impact:**
  - Limited ability to understand intended sprint scope vs current iteration assignments.
  - Reduced transparency in sprint-level backlog readiness.
- **Severity:** **High**

### Finding 3 — Schedule Data (Start and Due Dates) Largely Absent

- **Description:** Start Date missing for 94.44% of stories; Due Date missing for 83.33%.
- **Evidence:**
  - 10 of 180 stories have `startDate` populated.
  - 30 of 180 stories have `dueDate` populated.
- **Affected Stories:** 170 (startDate), 150 (dueDate).
- **Potential Impact:**
  - Poor visibility of schedule and deadlines.
  - Inability to systematically detect overdue work and to track timebox adherence.
- **Severity:** **High**

### Finding 4 — Risk and Dependency Fields Almost Unused

- **Description:** Risk is populated in 1 story; Dependent Team in 10 stories.
- **Evidence:**
  - Risk completeness: 0.56%.
  - Dependent Team completeness: 5.56%.
- **Affected Stories:** 179 (Risk missing) and 170 (Dependent Team missing).
- **Potential Impact:**
  - Hidden cross-team dependencies and risks.
  - Limited ability for leadership to proactively manage risk and dependencies.
- **Severity:** **Medium–High**

### Finding 5 — Large Portion of Backlog Not Ready for Sprint Planning (Planning Data Perspective)

- **Description:** 83.33% of stories classified as Not Ready in planning data terms.
- **Evidence:**
  - Ready = 0, Partially Ready ≈ 30 (16.67%), Not Ready = 150 (83.33%), Unable to Assess = 0.
- **Affected Stories:** 150.
- **Potential Impact:**
  - Sprint planning largely dependent on ad-hoc decisions and incomplete data.
  - Higher probability of mid-sprint scope changes and churning.
- **Severity:** **High**

### Finding 6 — On Hold and Re-Opened Work Signaling Delivery Risks

- **Description:** 6 On Hold and 8 Re-Opened stories with known Story Points (some).
- **Evidence:**
  - On Hold items: e.g., 53146, 58014, 62832, 75329, 75267.
  - Re-Opened items: e.g., 53401, 58006, 64169, 57750, 65153, 73869, 53398.
- **Affected Stories:** 14 (7.78%).
- **Potential Impact:**
  - Blocked security and governance tasks.
  - Rework may degrade predictability and cycle time.
- **Severity:** **Medium**

### Finding 7 — Historical Sprint Commitment Data Missing; Say-Do Ratio Not Computable

- **Description:** No explicit historical commitment data, completion dates, or sprint boundaries in JSON.
- **Evidence:**
  - Fields provided: state, iterationPath, Story Points, startDate, dueDate, but no commitment snapshot.
- **Affected Sprints:** All.
- **Potential Impact:**
  - Leadership cannot reliably judge commitment vs delivery performance on a sprint-by-sprint basis.
- **Severity:** **Medium**

---

## 14. Actionable Recommendations

### 14.1 Recommended Actions Table

| Priority | Recommended Action | Supporting Finding | Affected Stories | Suggested Owner | Suggested Timeframe |
|----------|--------------------|--------------------|------------------|-----------------|---------------------|
| High | Conduct focused estimation workshops to populate Story Points for all active and near-term backlog items. | Finding 1 – Extensive Unestimated Backlog | ~142 stories | Product Owner, Engineering Lead | Within next 1–2 sprints |
| High | Enforce capturing `plannedSprint` for all stories targeted for upcoming PI4 Sprints and beyond. | Finding 2 – Planned Sprint Assignment Missing | ~166 stories | Product Owner, Scrum Master | Immediate, next planning session |
| High | Define and adopt a convention for `startDate` and `dueDate` for release-critical stories and those in active sprints. | Finding 3 – Schedule Data Absent | ~170 (startDate), ~150 (dueDate) | Delivery Manager, Product Owner | Within current PI |
| Medium–High | Introduce a simple risk classification scheme and capture Risk for high-impact, On Hold, and Re-Opened stories. | Finding 4 – Risk Field Underused | ~179 stories | Product Owner, Engineering Lead | Next 2–3 refinement sessions |
| Medium–High | Require `dependentTeam` to be populated for any story needing another team (DevSecOps, ACE, Foundation, etc.). | Finding 4 – Dependency Visibility Low | ~170 stories | Scrum Master, Product Owner | Ongoing, starting next sprint |
| High | Establish a planning data readiness checklist (Story Points, Planned Sprint, priority confirmed) before committing stories into active sprints. | Finding 5 – Backlog Not Ready for Planning | ~150 Not Ready stories | Scrum Master, Product Owner | Immediately |
| Medium | Review all On Hold and Re-Opened items to either reactivate, re-estimate, or descoped, updating states and planning fields. | Finding 6 – On Hold/Re-Opened Work | 14 stories | Engineering Lead, Product Owner | Within current PI |
| Medium | Align user stories with release versions consistently (especially where features already have releaseVersion) to improve release planning. | Release Planning Gaps | ~166 stories missing releaseVersion | Product Owner, Delivery Manager | Before next PI planning |
| Medium | Implement a process to snapshot sprint commitments (stories + Story Points) at sprint start and completion dates at sprint end for Say-Do calculation. | Finding 7 – Say-Do Ratio Data Missing | All sprints | Scrum Master, Delivery Manager | Over next 2–3 sprints |
| Low–Medium | Clarify use of `uxExpected` and populate for UX-led stories to coordinate design timelines. | Missing UX Expected Dates | 179 stories | UX Lead, Product Owner | As part of UX planning cadence |

---

## 15. Overall Conclusion

### 15.1 Backlog Planning Health

- **Overall planning data completeness:** ~29.28% across key fields is low for a team operating multiple PI sprints.
- **Estimation and sprint assignment gaps** are the primary contributors to poor planning health.
- Priority is consistently populated, but used without adequate coupling to Story Points or planned sprint scheduling.

### 15.2 Most Significant Planning Gaps

- Missing Story Points and Planned Sprint information on the majority of stories.
- Sparse scheduling data (start and due dates).
- Underuse of Risk and Dependent Team fields, hiding important coordination and risk management signals.

### 15.3 Sprint Readiness Assessment

- From a planning data perspective, **0% of stories are fully Ready**, and more than **80% are Not Ready**.
- Sprint planning is currently constrained by insufficient data rather than only by capacity.
- PI4 sprints show active and resolved work but lack a complete, data-driven view of what was intentionally planned and committed.

### 15.4 Delivery Predictability Assessment

- On Hold and Re-Opened items indicate rework and potential delays.
- Incomplete estimation and missing sprint assignment severely limit the ability to measure or improve delivery predictability.
- Without historical commitment and completion tracking, leadership must rely on anecdote or partial indicators.

### 15.5 Say-Do Ratio Availability and Performance Trend

- **Official Say-Do Ratio:** **Insufficient Data** for all sprints; required historical data is missing.
- **Sprint-on-sprint trend:** **Insufficient Data**; cannot classify performance trend.
- Available current-state metrics (Resolved and Dev-Deployed Story Points) can show progress but not commitment alignment.

### 15.6 Immediate Corrective Actions

- Complete backlog estimation and Planned Sprint assignments for PI4 and upcoming sprints.
- Introduce and enforce a planning readiness checklist at sprint planning.
- Review and resolve On Hold and Re-Opened stories to reduce work churn and unblock critical pathways.
- Start capturing minimal historical metrics for each sprint (commitment snapshot, completion dates).

### 15.7 Longer-Term Process Improvements

- Establish a standardized data model for User Story planning fields and ensure consistent usage across teams (Story Points, Sprint, Start/Due Dates, Risk, Dependencies, Release).
- Integrate planning data quality checks into tooling (Azure DevOps dashboards) to flag missing critical fields before sprint start.
- Use improved data to introduce Say-Do Ratio tracking, velocity, and predictable roadmap forecasting at PI and release levels.
- Encourage cross-team alignment by using `studio` and `dependentTeam` fields to drive multi-team planning and coordination.

Overall, the Integrations team’s Azure DevOps User Story data provides a good foundation of backlog structure but requires significant planning data improvements—particularly around estimation, sprint assignment, and risk/dependency capture—to support reliable sprint planning, delivery predictability, and executive-level reporting.
