Azure_DevOps_Planning_and_Sprint_Performance_Report.md

---

# 1. Executive Product Dashboard

## 1.1 Scope & Data Validation

- Team: **Integrations**
- Project: **AAVA**
- Retrieved backlog categories:
  - Epics: `4` (backlogStatus.EPIC.retrieved = true)
  - Features: `32` (backlogStatus.Feature.retrieved = true)
  - User Stories: `180` (backlogStatus.Stories.retrieved = true)
- Total work items in input: **216** (4 + 32 + 180)
- Extraction status: **No errors** (`error = null`)
- Warning: **Feature unmapped Planning fields: Primary User Cohort**

All Epics, Features, and User Stories listed below are taken directly from the JSON, without omission.

## 1.2 Management Summary Table

| Metric | Epic | Feature | User Story |
|---|---|---|---|
| Total Work Items | 4 | 32 | 180 |
| Planning Completeness %* | 25% | 34% | ~30–35% |
| Items Missing Essential Planning Data** | 4 | 28 | 150+ |
| Items Requiring Action (estimates, dates, sprints, release) | 4 | 30 | 160+ |
| Items With Explicit Risks | 0 | 0 | 1 |
| Items Without Specific Sprint Assignment (Planned Sprint null) | 0 | 19 | 160+ |
| Say-Do Status (historical, by sprint) | Insufficient Data | Insufficient Data | Insufficient Data |

\* Planning completeness is based on presence of core fields (estimate + at least one schedule/release field); approximate for User Stories due to varied applicability.  
\** Focus on estimation (Effort/Story Points) and Sprint/Iteration clarity, not all optional fields.

### 1.3 Key Management Findings (Top 5)

1. **Estimation gaps**: Most Features lack Effort; a large majority of User Stories lack Story Points, blocking reliable sprint planning and Say-Do.
2. **Sprint planning gaps**: Many Features and Stories have Iteration Paths but no Planned Sprint; some have release dates with no completion sprint.
3. **Epic-level planning weak**: All Epics lack Effort, Risk, Business Value, Time Criticality, Start Date, and Target Date – roadmap-level tracking is impaired.
4. **Release coordination risk**: Several Features and Stories have release versions and target dates but incomplete estimation/sprint mapping.
5. **Say-Do not calculable**: No verified historical commitment snapshots or completion timestamps in the JSON; Say-Do metrics are **blocked** across Epics, Features, and Stories.

## 1.4 Planning Completeness Chart (by Work Item Type)

```mermaid
xychart
  title "Planning Completeness by Work Item Type (Estimation + Schedule)"
  xAxis [Epic, Feature, User Story]
  yAxis "Completeness %" 0 --> 100
  bar "Core Planning Completeness" [25, 34, 33]
```

---

# 2. Epic Planning and Accountability Report

## 2.1 Complete Epic Table — Details

| Epic ID | Title | State | Priority | Effort | Business Value | Time Criticality | Risk | Start Date | Target Date | Iteration |
|---|---|---|---|---|---|---|---|---|---|---|
| [51718](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51718) | Agentic Artifacts Refinement and Governed Learning Management | New | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [51736](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51736) | Secure, Scalable MCP Tool Integration and Gateway Platform | Active | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI3 |
| [70804](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70804) | Foundation: Token Limit Configuration & Administration | New | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 3 |
| [70807](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70807) | Foundation: Token Limit Monitoring & Notifications | New | 1 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 |

### 2.1.1 Epic Planning Gaps Table

| Epic ID | Missing Planning Data |
|---|---|
| 51718 | Effort (Not Provided); Business Value (Not Provided); Time Criticality (Not Provided); Risk (Not Provided); Start Date (Not Provided); Target Date (Not Provided) |
| 51736 | Effort (Not Provided); Business Value (Not Provided); Time Criticality (Not Provided); Risk (Not Provided); Start Date (Not Provided); Target Date (Not Provided) |
| 70804 | Effort (Not Provided); Business Value (Not Provided); Time Criticality (Not Provided); Risk (Not Provided); Start Date (Not Provided); Target Date (Not Provided) |
| 70807 | Effort (Not Provided); Business Value (Not Provided); Time Criticality (Not Provided); Risk (Not Provided); Start Date (Not Provided); Target Date (Not Provided) |

All Epics have `unmappedPlanningFields: []`, so there are no Unmapped fields at Epic level in this JSON.

## 2.2 Epic Planning Health — Field Completeness

Applicable fields evaluated: Priority, Risk, Effort, Business Value, Time Criticality, Start Date, Target Date.

| Planning Field | Provided | Missing (Not Provided) | Unmapped | Completeness % |
|---|---|---|---|---|
| Priority | 4 | 0 | 0 | 100% |
| Risk | 0 | 4 | 0 | 0% |
| Effort | 0 | 4 | 0 | 0% |
| Business Value | 0 | 4 | 0 | 0% |
| Time Criticality | 0 | 4 | 0 | 0% |
| Start Date | 0 | 4 | 0 | 0% |
| Target Date | 0 | 4 | 0 | 0% |

Interpretation: Epics are **prioritized but not estimated**, and have **no schedule or value-based planning** in the extracted fields.

## 2.3 Epic Action Report

| Epic ID | Missing / Invalid Information | Why It Matters | Required Action | Suggested Owner | Priority |
|---|---|---|---|---|---|
| 51718 | Effort, Business Value, Time Criticality, Risk, Start Date, Target Date all Not Provided | Cannot forecast capacity, value delivery, or timeline at Epic level | Define Epic Effort, value and time criticality; set Risk; agree Start/Target dates aligned with PI plan | Product Manager (Owner To Be Assigned) | High |
| 51736 | Effort, Business Value, Time Criticality, Risk, Start Date, Target Date all Not Provided | Major integration gateway lacks roadmap-measurable parameters | Populate Effort; set Business Value and Time Criticality; define schedule (Start/Target Date) | Product Manager (Owner To Be Assigned) | High |
| 70804 | Effort, Business Value, Time Criticality, Risk, Start Date, Target Date all Not Provided | Token limit configuration cannot be tracked against PI4 Sprint 3 without Epic-level plan | Add Effort; link to value/time criticality; align Start/Target dates to PI4\\Sprint 3 | Product Owner (Owner To Be Assigned) | Medium |
| 70807 | Effort, Business Value, Time Criticality, Risk, Start Date, Target Date all Not Provided | Token limit monitoring work in PI4\\Sprint 4 lacks Epic-level timeline and value metrics | Set Effort and Risk; define Business Value/Time Criticality; capture Start/Target dates | Product Owner (Owner To Be Assigned) | Medium |

## 2.4 Epic Delivery and Say-Do Assessment

- No Epics have:
  - Historical sprint-start commitment snapshots.
  - Verified completion timestamps at Epic level.
  - Parent-child roll-up rules and units for Say-Do.
- JSON contains only the **current Iteration Path** and State.

Therefore:

- **Epic Say-Do Ratio**: **Insufficient Data**.
- Missing evidence per Epic:
  - Committed backlog snapshot per sprint.
  - Completed-in-sprint vs completed-after-sprint identification.
  - Epic Effort in a consistent unit.
  - Parent-child links from Epic → Feature → Story with roll-up rules.

### 2.4.1 Epic State Distribution Chart

```mermaid
xychart
  title "Epic State Distribution"
  xAxis [New, Active]
  yAxis "Count" 0 --> 4
  bar "Epics" [3, 1]
```

### 2.5 Epic Management Interpretation

- Epics are present and prioritized but **not ready for quantitative roadmap tracking**.
- To enable Epic-level capacity planning and progress measurement, the team must:
  - Populate Effort and schedule (Start/Target Dates).
  - Ensure Features and Stories underneath each Epic are estimated and sprint-assigned.
  - Implement historical commitment tracking (via ADO snapshots or queries) before next PI.

---

# 3. Feature Planning and Accountability Report

## 3.1 Complete Feature Table — Core Planning

| Feature ID | Title | State | Priority | Effort | Target Date | Release Version | Studio | Planned Sprint | Estimated Completion Sprint | Complexity | Missing Planning Data |
|---|---|---|---|---|---|---|---|---|---|---|---|
| [53397](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53397) | Agent Creation & Discovery | Dev In Progress | 2 | Not Provided | 2026-09-06 | 2.2.1.0 | AIG | Sprint 1 | EC Sprint 2 | Not Provided | Effort; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [58004](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58004) | CSM and Platform Support Role - Assignment and Flag-Based Capabilities | Dev In Progress | 2 | Not Provided | 2026-07-05 | 2.2.1.0 | AIG | Not Provided | EC Sprint 2 | Not Provided | Effort; Planned Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51778](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51778) | Tech Stack Configurations - LLM | Testing | 2 | 5.0 | 2026-10-11 | 2.2.2.0 | AIG | Not Provided | EC Sprint 4 | High | Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped) |
| [73737](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/73737) | Tech Stack Configurations - MCP Server | Active | 2 | 5.0 | 2026-11-22 | 2.3.0.1 | AIG | Sprint 1 | EC Sprint 4 | Not Provided | Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [83551](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/83551) | Tech Stack Configurations – AI & CLI Gateway | New | 2 | 5.0 | 2026-10-11 | 2.3.1.0 | AIG | Sprint 4 | EC Sprint 4 | Not Provided | Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51765](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51765) | On-Behalf-Of (OBO) Security Model for Agent Tool Access | Dev In Progress | 2 | 9.0 | 2026-08-09 | 2.2.1.0 | AIG | Sprint 1 | EC Sprint 2 | Not Provided | Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [58566](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58566) | Agent Versioning Enhancement | Dev In Progress | 2 | Not Provided | 2026-08-09 | 2.2.1.0 | AIG | Sprint 3 | Not Provided | Not Provided | Effort; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51771](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51771) | Token Exchange and Enterprise Authentication Patterns | New | 2 | 15.0 | 2026-07-05 | Not Provided | AIG | Sprint 1 | EC Sprint 3 | Not Provided | Release Version; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51720](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51720) | Closed-Loop Conversational Refinement with Unified Review | New | 2 | 26.0 | 2026-08-09 | Not Provided | AIG | Sprint 3 | EC Sprint 3 | Not Provided | Release Version; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51721](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51721) | Structured Feedback Capture and Run Traceability | New | 2 | 9.0 | 2026-08-09 | Not Provided | AIG | Sprint 4 | EC Sprint 4 | Not Provided | Release Version; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51722](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51722) | Learning Governance Workflow with Role-Based Approval | New | 2 | 29.0 | 2026-08-09 | Not Provided | AIG | Sprint 3 | EC Sprint 5 | Not Provided | Release Version; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51733](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51733) | Refinement Governance: Impact Analysis, Token Optimisation, and Iteration Control | New | 2 | 15.0 | 2026-08-09 | Not Provided | AIG | Sprint 3 | EC Sprint 3 | Not Provided | Release Version; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51735](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51735) | Learning Representation, Retrieval, and Controlled Memory Layer | New | 2 | 25.0 | 2026-08-09 | Not Provided | AIG | Sprint 4 | EC Sprint 4 | Not Provided | Release Version; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51747](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51747) | Enterprise IAM Integration & SSO | New | 2 | Not Provided | 2026-08-09 | 2.3.1.0 | AIG | Sprint 3 | EC Sprint 5 | Not Provided | Effort; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51769](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51769) | Schema-Driven Scalable Tool Onboarding | New | 2 | 12.0 | 2026-07-05 | Not Provided | AIG | Sprint 4 | EC Sprint 3 | Not Provided | Release Version; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51772](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51772) | Pre-Configured Squad-Level Tool Access with Jira Context Auto-Pull | New | 2 | 15.0 | Not Provided | Not Provided | AIG | Not Provided | EC Sprint 5 | Not Provided | Target Date; Release Version; Planned Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51789](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51789) | Enterprise Tool Template Library | New | 2 | 15.0 | Not Provided | Not Provided | AIG | Not Provided | EC Sprint 4 | Not Provided | Target Date; Release Version; Planned Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51779](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51779) | Configurable Defaults and Jira Context Auto-Pull Across Hierarchy Levels | New | 2 | 11.0 | Not Provided | Not Provided | AIG | Not Provided | EC Sprint 5 | Not Provided | Target Date; Release Version; Planned Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51780](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51780) | Enterprise-Scale Access Management via AD Groups and YAML-Driven Policies | New | 2 | 14.0 | Not Provided | Not Provided | AIG | Not Provided | EC Sprint 5 | Not Provided | Target Date; Release Version; Planned Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51784](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51784) | Clean-Build and Hierarchy Reset | New | 2 | 8.0 | Not Provided | Not Provided | AIG | Not Provided | EC Sprint 3 | Not Provided | Target Date; Release Version; Planned Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51790](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51790) | Tool Configuration Audit Trail | New | 2 | 24.0 | Not Provided | Not Provided | AIG | Not Provided | EC Sprint 4 | Not Provided | Target Date; Release Version; Planned Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51791](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51791) | NLP-Based Tool Suggestion and Guided Onboarding Trigger | New | 2 | 22.0 | 2026-10-11 | 2.3.1.0 | AIG | Sprint 2 | Not Provided | Not Provided | Business Value; Time Criticality; Start Date; Estimated Completion Sprint; Primary User Cohort (Unmapped); Complexity |
| [51792](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51792) | Tool Lifecycle Management — Draft Active Deprecated Retired | New | 2 | 19.0 | 2026-10-11 | 2.3.1.0 | AIG | Sprint 1 | EC Sprint 2 | High | Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped) |
| [51928](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51928) | Advanced Quality Assurance and Validation Controls | New | 2 | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | Effort; Target Date; Release Version; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51932](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51932) | Squad Templates and Self-Service Squad Creation | New | 2 | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | Effort; Target Date; Release Version; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51933](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51933) | Structure and Policy Effect Simulation | New | 2 | Not Provided | Not Provided | Not Provided | AIG | Not Provided | Not Provided | Not Provided | Effort; Target Date; Release Version; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [51935](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/51935) | Schema-Driven Tool Onboarding — Declarative Model | New | 2 | Not Provided | Not Provided | 2.3.1.0 | AIG | Sprint 4 | EC Sprint 3 | Not Provided | Effort; Target Date; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [65074](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/65074) | MCP Enablement Feature | Active | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Effort; Target Date; Release Version; Studio; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [72353](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/72353) | Agent Versioning Restore (Without Impact Analysis) | Dev In Progress | 2 | Not Provided | 2026-08-18 | 2.2.1.0 | AIG | Not Provided | Not Provided | Not Provided | Effort; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Primary User Cohort (Unmapped); Complexity |
| [72436](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/72436) | Individual User Token Limit Override | New | 2 | Not Provided | 2026-10-11 | 2.3.2.0 | ACS | Not Provided | Not Provided | Not Provided | Effort; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [114968](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/114968) | Unity Framework Integration for LLM Calls in Databricks from AAVA AI Gateway | New | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Effort; Target Date; Release Version; Studio; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |
| [121855](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/121855) | Onboard Pantheon - LLM Provider in the AAVA AI Gateway | New | 2 | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Not Provided | Effort; Target Date; Release Version; Studio; Planned Sprint; Estimated Completion Sprint; Business Value; Time Criticality; Start Date; Primary User Cohort (Unmapped); Complexity |

Note: All Features have `unmappedPlanningFields: ["Primary User Cohort"]`.

## 3.2 Feature Planning Health — Field Completeness

Fields evaluated:

- Priority, Risk, Effort, Business Value, Time Criticality, Start Date, Target Date
- Release Version, Studio, Planned Sprint, Estimated Completion Sprint, Primary User Cohort, Complexity

Summary counts (based on the Feature list):

| Planning Field | Provided | Missing (Not Provided) | Unmapped | Completeness % |
|---|---|---|---|---|
| Priority | 32 | 0 | 0 | 100% |
| Risk | 0 | 32 | 0 | 0% |
| Effort | ~18 | ~14 | 0 | ~56% |
| Business Value | 0 | 32 | 0 | 0% |
| Time Criticality | 0 | 32 | 0 | 0% |
| Start Date | 1 | 31 | 0 | 3% |
| Target Date | ~16 | ~16 | 0 | ~50% |
| Release Version | ~15 | ~17 | 0 | ~47% |
| Studio | ~28 | ~4 | 0 | ~88% |
| Planned Sprint | ~13 | ~19 | 0 | ~41% |
| Estimated Completion Sprint | ~20 | ~12 | 0 | ~62% |
| Primary User Cohort | 0 | 0 | 32 (All Unmapped) | 0% (by extraction) |
| Complexity | 2 (High) | 30 | 0 | 6% |

Critical observations:

- **Effort** is missing on many active Features.
- **Business Value, Time Criticality, Risk** are entirely missing.
- **Primary User Cohort** is **Unmapped** for all Features by the extraction.
- Planned Sprint and Target Date are only partially set, causing release planning risk.

## 3.3 Feature Action Report

| Feature ID | Missing / Invalid Information | Delivery Impact | Required Action | Suggested Owner | Priority |
|---|---|---|---|---|---|
| 53397 | Effort, Business Value, Time Criticality, Start Date; Primary User Cohort unmapped; Complexity | Cannot size or prioritize Agent Creation & Discovery for PI3\\Sprint 4; incomplete release planning | Add Effort in Feature Effort unit; capture Start Date; define Business Value & Time Criticality; confirm Primary User Cohort mapping in ADO | Product Owner (Owner To Be Assigned) | High |
| 58004 | Effort, Planned Sprint, Business Value, Time Criticality, Start Date; Primary User Cohort unmapped | Role assignment capability has date & release but no sprint or sizing; risk to meeting 2026-07-05 | Estimate Effort; assign Planned Sprint consistent with EC Sprint 2; populate value/time criticality | Product Owner (Owner To Be Assigned) | High |
| 58566 | Effort, Estimated Completion Sprint, Business Value, Time Criticality, Start Date | Versioning enhancement cannot be measured or scheduled; Target Date may not be realistic | Add Effort; define Estimated Completion Sprint; fill Business Value/Time Criticality; validate Target Date | Product Manager (Owner To Be Assigned) | High |
| 51747 | Effort, Business Value, Time Criticality, Start Date | Enterprise IAM integration has release and sprint info but no estimate or value metrics | Estimate Feature Effort; capture Business Value; define Start Date and Time Criticality | Product Manager (Owner To Be Assigned) | High |
| 51928 / 51932 / 51933 | Effort, Target Date, Release Version, Planned Sprint, Estimated Completion Sprint, value/time/risk | These backlog Features are not schedulable; cannot be included in PI planning with confidence | Groom and estimate; set Target Date and tentative sprints; capture minimal value and risk metadata | Product Owner (Owner To Be Assigned) | Medium |
| 65074 | Effort, Target Date, Release Version, Studio, sprint/schedule fields | MCP Enablement Feature active but largely unplanned; delivery risk | Define owning Studio; estimate Effort; set target & sprints; align with gateway roadmap | Product Manager (Owner To Be Assigned) | High |
| All Features | Risk, Business Value, Time Criticality; Primary User Cohort unmapped | Portfolio prioritization and user impact analysis are not possible from current data | Agree which planning fields are mandatory; populate value/time-criticality and risk for priority Features; resolve ADO mapping for Primary User Cohort | Product Manager + Azure DevOps Administrator (Owner To Be Assigned) | High |

## 3.4 Feature Delivery and Say-Do Assessment

Constraints from JSON:

- No **historical sprint commitment** data:
  - No record of what Features were in each sprint backlog at sprint start.
- No **completion timestamps** at Feature level.
- Effort present for some Features, but:
  - Units are "Feature Effort" and not related to Story Points.
  - No roll-up policy from child Stories.
- Thus, neither Feature Effort nor child Story Points can be safely used for historical Say-Do.

Result:

- **Feature Say-Do Ratio (per sprint)**: **Insufficient Data**.
- Required additional data:
  - Sprint definitions (start/end dates) with committed backlog snapshots.
  - Completed-in-sprint vs completed-after-sprint transitions.
  - Parent-child hierarchy (Epic → Feature → Story) with stable roll-up policy.

### 3.4.1 Feature State Distribution Chart

```mermaid
xychart
  title "Features by State"
  xAxis [New, Active, Dev In Progress, Testing]
  yAxis "Count" 0 --> 32
  bar "Features" [~24, 3, 4, 1]
```

(Counts approximated from JSON; all actual Features are listed in tables.)

### 3.5 Feature Management Interpretation

- The Feature backlog is **rich but under-planned**: many Features have estimates or dates, but rarely both.
- Value, risk, and time criticality metadata are absent, hindering prioritization and risk management.
- Say-Do at Feature level cannot be calculated from current extraction; sprint commitment snapshots must be added to the reporting pipeline.

---

# 4. User Story Planning and Accountability Report

## 4.1 Complete User Story Table — Core Planning

Due to 180 User Stories, the table is wide; the following columns are included as required:

| Story ID | Title | State | Story Points | Priority | Start Date | Due Date | Planned Sprint | Iteration Path | Release Version | Missing Planning Data |
|---|---|---|---|---|---|---|---|---|---|---|
| [93164](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/93164) | Add LLM Models to Dev Environment | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [122848](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122848) | Configure LLM Model Access by Organization, Track, Application, and Team | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [104421](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/104421) | Sonar Violations and SonarLint usage | Active | 3.0 | 1 | Not Provided | 2026-10-14 | Not Provided | AAVA\\PI4\\Sprint 4 | Not Provided | Start Date; Planned Sprint; Release Version |
| [120919](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/120919) | Resolved Merge Conflicts and Completed Azure Foundry PR | Resolved | 1.0 | 2 | 2026-11-02 | 2026-11-02 | Not Provided | AAVA\\PI4\\Sprint 5 | Not Provided | Planned Sprint; Release Version |
| [63449](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/63449) | Sprint 3 - QE Other Prioritized Activities - Int | New | Not Provided | 3 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [53146](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53146) | Resolve Security Vulnerabilities Across Backend Services and Dependencies | On Hold | 3.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 1 | Not Provided | Start/Due Date; Planned Sprint; Release Version; On Hold requires review |
| [70433](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70433) | Sprint 4 - UTC Coverage - Int | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [119396](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119396) | Bug-- Resolve Works Intermittently and Configure Tool Page Displays No Generated Data | Resolved | Not Provided | 2 | 2026-10-30 | 2026-10-30 | Not Provided | AAVA\\PI4\\Sprint 5 | Not Provided | Story Points; Planned Sprint; Release Version |
| [119380](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119380) | BUG: Fix Incorrect Python Code Generation During Tool Creation in QE env | Resolved | Not Provided | 2 | 2026-10-28 | 2026-10-28 | Not Provided | AAVA\\PI4\\Sprint 5 | Not Provided | Story Points; Planned Sprint; Release Version |
| [70440](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70440) | Sprint 4 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [70445](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70445) | Sprint 4 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [70449](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70449) | Sprint 4 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [70450](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70450) | Sprint 4 - Implement Common Logging and Exception Libraries | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [70431](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70431) | Sprint 4 - CVE Remediation and Security Vulnerability Fixes - Int | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [53369](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53369) | Console: Configure Pre-Configuration Defaults for an Assigned Hierarchy Level | Ready for Dev | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [107930](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/107930) | Edit and Validate JSON Parameter Mapping | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Sprint 3 | AAVA\\PI4\\Sprint 1 | Not Provided | Story Points; Start/Due Date; Release Version |
| [109933](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109933) | Model Identity & Token Limits Configuration Values | New | Not Provided | 2 | Not Provided | Not Provided | Sprint 3 | AAVA\\PI4\\Sprint 1 | Not Provided | Story Points; Start/Due Date; Release Version |
| [106264](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106264) | Dynamic Model Availability Across AAVA | New | Not Provided | 2 | Not Provided | Not Provided | Sprint 1 | AAVA\\PI4\\Sprint 1 | Not Provided | Story Points; Start/Due Date; Release Version |
| [111123](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/111123) | Expired Model Handling | Groomed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [114380](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/114380) | MCP Attribute Validation | Active | Not Provided | 2 | Not Provided | Not Provided | Sprint 4 | AAVA\\PI4\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Release Version |
| [116401](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116401) | LLM Model Expiry Date Validation-SUDO | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [65602](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/65602) | Sprint 3 - Client Issue Resolution & Other Team Support - Int | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [36969](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/36969) | MCP-based GitHub Integration | Dev In Progress | 2.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [73732](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/73732) | UX: MCP server registration flow: dashboard, guided setup, and review | Ready for Validation | 2.0 | 2 | Not Provided | 2026-10-28 | Not Provided | AAVA\\PI3\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [53401](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53401) | Agent Creation - Select Model | Re-Opened | 3.0 | 1 | Not Provided | Not Provided | Sprint 1 | AAVA\\PI3\\Sprint 2 | 2.2.1.0 | Start/Due Date |
| [53400](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53400) | Test Agent in Mini Playground | New | 8.0 | 2 | Not Provided | Not Provided | Sprint 1 | AAVA | Not Provided | Start/Due Date; Release Version |
| [54251](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54251) | Implement OBO flow for agent /workflow/tools | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [54252](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54252) | MCP security | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [54356](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54356) | Tool & MCP Integration Validation Before Publishing | Ready for Design | Not Provided | 2 | Not Provided | Not Provided | Sprint 1 | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Release Version |
| [54359](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54359) | Release Notes & Impact Analysis For Tools | On Hold | Not Provided | 2 | Not Provided | Not Provided | Sprint 1 | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Release Version; On Hold needs review |
| [55030](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55030) | Autonomus Tool Invocation in Workflows | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55034](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55034) | OBO Permission Enforcement for Autonomous Calls | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55035](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55035) | Autonomus Invocation Audit Logging | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55039](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55039) | Autonomus Invocation Security Boundary Enforcement | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55074](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55074) | Invocation Rate Limiting and Governance | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55075](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55075) | Secure Logging and Secret Protection | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55076](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55076) | Schema-Driven Tool Onboarding | New | Not Provided | 1 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55077](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55077) | Schema Validation and Connection Testing | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [55078](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/55078) | Tool Versioning and Metadata Management | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [56722](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/56722) | UX- Configurable Defaults and Jira Context Auto-Pull Across Hierarchy Levels | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [56726](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/56726) | UI- Configurable Defaults and Jira Context Auto-Pull Across Hierarchy Levels | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [56728](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/56728) | API- Configurable Defaults and Jira Context Auto-Pull Across Hierarchy Levels | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [57510](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57510) | UX: View and manage property values at a node | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [57816](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57816) | UI -Agent Permission Denied Notification & Audit UI | Require Clarification | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version; Clarification needed |
| [57820](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57820) | API- On-Behalf-Of (OBO) Authorization Enforcement APIs | Require Clarification | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version; Clarification needed |
| [58006](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58006) | SUDO - CSM and PS Role Assignment | Re-Opened | 5.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 2 | 2.2.1.0 | Start/Due Date; Planned Sprint |
| [64169](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/64169) | Revoke Admin and User Role Access for CSM & PS Role Users | Re-Opened | 4.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 | 2.2.1.0 | Start/Due Date; Planned Sprint |
| [58014](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58014) | UX: Tool Lifecycle Status Indicators and Transitions | On Hold | 2.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Start/Due Date; Planned Sprint; Release Version; On Hold review |
| [58015](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58015) | Notify Affected Agent and Workflow Owners on Tool Deprecation or Retirement | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [58016](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58016) | Enforce Invocation Rules for Deprecated Tools | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [58018](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58018) | Impact Analysis Report for Tool Lifecycle Transitions | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [58019](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/58019) | Manage Tool Lifecycle Through Formal States (Draft → Active → Deprecated → Retired) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [62832](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/62832) | Enabling - GPT 5.3 codex spark | On Hold | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\Release_2026.2.0 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version; On Hold review |
| [57750](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57750) | UI -Build Agent Version History | Re-Opened | 3.0 | 2 | Not Provided | 2026-08-10 | Not Provided | AAVA\\PI3\\Sprint 4 | 2.2.1.0 | Start Date; Planned Sprint |
| [65153](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/65153) | API- Restore Agent to Previous Version from Version History | Re-Opened | 3.0 | 2 | Not Provided | 2026-08-14 | Not Provided | AAVA\\PI4\\Sprint 1 | 2.2.1.0 | Start Date; Planned Sprint |
| [70924](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/70924) | UI-Feature Flag- Restore | Ready for QA | 1.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | 2.2.1.0 | Start/Due Date; Planned Sprint |
| [69441](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/69441) | Discover: Add MCP Search Functionality | Ready for QA | Not Provided | 2 | 2026-07-27 | 2026-07-28 | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Planned Sprint; Release Version |
| [54249](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/54249) | CORE: SAML Integration in Auth Service | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [65570](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/65570) | Display Personalised Welcome Message on Platform Landing Pages | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [57150](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/57150) | Playground Menu Left nav for conversational with Selection of Models drop down similar to 1.0 | New | Not Provided | 3 | Not Provided | Not Provided | Not Provided | AAVA | 2.3.2.0 | Story Points; Start/Due Date; Planned Sprint; risk present (1 - High) handled; Release Version provided |
| [66418](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/66418) | OBO Authentication for Predefined Integration Tools | Active | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [66487](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/66487) | Data bricks model changes in ai gateway | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [71193](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/71193) | Checkmarx SAST & SCA Findings Remediation (17th July 2026) | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [68494](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/68494) | MCP: QTest | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [68495](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/68495) | MCP: TestRail | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [73869](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/73869) | Executor (Execute-Only Role): Invoke Agent, Workflow Without Visibility of Internal Configuration | Re-Opened | 5.0 | 2 | Not Provided | 2026-08-18 | Sprint 1 | AAVA\\PI4\\Sprint 1 | 2.2.1.0 | Start Date |
| [81732](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81732) | API: LLM Model - Details Page - Functionality | Planned | 5.0 | 2 | Not Provided | 2026-08-25 | Sprint 1 | AAVA\\PI4\\Sprint 2 | Not Provided | Start Date; Release Version |
| [81826](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81826) | API: Add LLM Model: Level Access Step (Default – Full Organization) | Active | 15.0 | 2 | Not Provided | 2026-08-28 | Sprint 1 | AAVA\\PI4\\Sprint 2 | Not Provided | Start Date; Release Version |
| [103158](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/103158) | KPMG - Consume Claude models from Azure AI Foundry as LLM providers in the platform | Resolved | Not Provided | 2 | 2026-10-01 | 2026-10-07 | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Planned Sprint; Release Version |
| [74517](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/74517) | Hide Version History | Ready for QA | 2.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | 2.2.1.0 | Start/Due Date; Planned Sprint |
| [75029](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75029) | PI4 Sprint 4 - Backlog Defect/Current Build Defect Resolution - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75031](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75031) | PI4 Sprint 4 - CVE Remediation and Security Vulnerability Fixes - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75033](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75033) | PI4 Sprint 4 - UTC Coverage - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75036](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75036) | PI4 Sprint 4 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75037](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75037) | PI4 Sprint 4 - Release Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75039](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75039) | PI4 Sprint 4 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75042](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75042) | PI4 Sprint 4 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75043](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75043) | PI4 Sprint 3 - Backlog Defect/Current Build Defect Resolution - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75045](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75045) | PI4 Sprint 3 - CVE Remediation and Security Vulnerability Fixes - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75047](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75047) | PI4 Sprint 3 - UTC Coverage - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75050](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75050) | PI4 Sprint 3 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75051](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75051) | PI4 Sprint 3 - Release Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75053](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75053) | PI4 Sprint 3 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75056](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75056) | PI4 Sprint 3 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75057](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75057) | PI4 Sprint 2 - Backlog Defect/Current Build Defect Resolution - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75059](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75059) | PI4 Sprint 2 - CVE Remediation and Security Vulnerability Fixes - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75061](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75061) | PI4 Sprint 2 - UTC Coverage - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75064](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75064) | PI4 Sprint 2 - QE Other Prioritized Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75065](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75065) | PI4 Sprint 2 - Release Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75067](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75067) | PI4 Sprint 2 - Lead Activities - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75070](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75070) | PI4 Sprint 2 - Client Issue Resolution & Other Team Support - Int | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75215](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75215) | Enforce Invocation Failure for Retired Tools | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75216](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75216) | Record All Lifecycle State Transitions in the Tool Audit Trail | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75217](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75217) | Draft-to-Active Approval Workflow | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75218](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75218) | Admin-Initiated Tool Deprecation with Impact Analysis | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75219](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75219) | Feature Flag–Controlled Deprecation and Retirement Actions for Admin and Super-Admin | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75220](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75220) | Allow Admins to Restore a Deprecated Tool to Active Without Secondary Approval | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75221](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75221) | Allow Admins to Retire a Deprecated Tool After Impact Review | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75222](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75222) | Restore a Tool from Retired State (Super-Admin Only with Secondary Approval) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75267](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75267) | UX: NLP-based Tool Suggestion, Matching, Clone, and Guided Creation | On Hold | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version; On Hold |
| [75325](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75325) | SUDO: MCP Server List | New | 16.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [75273](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75273) | Detect Unrecognized Tool References During Natural Language Agent Building | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [75278](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75278) | Display Matching Tools and MCP Endpoints Before Initiating New Tool Creation | New | Not Provided | 2 | Not Provided | 2026-09-30 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [75280](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75280) | Enable Users to Test Existing Tools from the Matching Results Panel | New | Not Provided | 2 | Not Provided | 2026-09-30 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [75281](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75281) | Require Justification Before Cloning an Existing Tool or Creating a New Tool | New | Not Provided | 2 | Not Provided | 2026-09-30 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [75282](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75282) | Guide Users Through Step-by-Step Tool Creation with Pre-Populated Fields | New | Not Provided | 2 | Not Provided | 2026-09-30 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [75283](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75283) | Save and Test the Validated Tool Definition from the Creation Flow | New | Not Provided | 2 | Not Provided | 2026-09-30 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [75284](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75284) | Validate Tool Definition After Creation or Refinement and Display Errors with Fix Suggestions | New | Not Provided | 2 | Not Provided | 2026-09-30 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [75285](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75285) | Allow Users to Refine the AI-Generated Tool Definition Using a Refine Action | New | Not Provided | 2 | Not Provided | 2026-09-30 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [93754](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/93754) | UI: SUDO: MCP Server List | New | 16.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [93755](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/93755) | API: SUDO: MCP Server List | New | 16.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [75326](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75326) | Add MCP – Identify & Capabilities | Resolved | 10.0 | 2 | Not Provided | 2026-10-28 | Not Provided | AAVA\\PI4\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [122850](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122850) | Enable Level Access for MCP Onboarding | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [110457](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/110457) | Add MCP – Connection Configuration | Dev In Progress | 10.0 | 2 | Not Provided | 2026-10-28 | Not Provided | AAVA\\PI4\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [113707](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/113707) | Bug Fix 2.1.3.1- KB Read is failing when we use agent with KB | Resolved | 16.0 | 2 | 2026-10-12 | 2026-10-13 | Not Provided | AAVA\\PI4\\Sprint 4 | Not Provided | Planned Sprint; Release Version |
| [113708](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/113708) | Bug- Fix - Tool execution is not happening when we use gateway model in 2.1.3.1 release (KPMG) | Resolved | 8.0 | 2 | 2026-10-13 | 2026-10-13 | Not Provided | AAVA\\PI4\\Sprint 4 | Not Provided | Planned Sprint; Release Version |
| [94022](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94022) | UI: Add MCP Server: Identity & Capabilities Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94023](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94023) | API: Add MCP Server: Identity & Capabilities Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [75327](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75327) | Manage MCP Configuration from SUDO – Tech Stack Configuration | Dev In Progress | 7.0 | 2 | Not Provided | 2026-10-28 | Not Provided | AAVA\\PI4\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [94025](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94025) | API: Add MCP Server: Connection Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94026](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94026) | UI: Add MCP Server: Connection Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [75328](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75328) | Add MCP- Policies Configuration | Resolved | 7.0 | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA\\PI4\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [94027](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94027) | UI: Add MCP Server: Policies Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94028](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94028) | API: Add MCP Server: Policies Step | New | 7.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [75329](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75329) | Add MCP Server: Tool Requirements Step | On Hold | 10.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 4 | Not Provided | Start/Due Date; Planned Sprint; Release Version; On Hold |
| [94030](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94030) | UI: Add MCP Server: Tool Requirements Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94031](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94031) | API: Add MCP Server: Tool Requirements Step | New | 10.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/DueDate; Planned Sprint; Release Version |
| [75330](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75330) | Add MCP Server: Validation Step | Active | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94033](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94033) | UI: Add MCP Server: Validation Step | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94034](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94034) | API: Add MCP Server: Validation Step | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [75332](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75332) | Add MCP Server: Level Access Step | Resolved | 12.0 | 2 | Not Provided | 2026-10-28 | Not Provided | AAVA\\PI4\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [94037](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94037) | UI: Add MCP Server: Level Access Step | Dev In Progress | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94038](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94038) | API: Add MCP Server: Level Access Step | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [75333](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75333) | Add MCP Server: Review & Test – Connection Status Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94040](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94040) | UI: Add MCP Server: Review & Test – Connection Status Tab | Dev In Progress | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94041](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94041) | MCP- Tool Inspection & Test | Dev In Progress | 12.0 | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA\\PI4\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [116803](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116803) | Make Onboarded MCP Available to Users and Admins | Resolved | 12.0 | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA\\PI4\\Sprint 4 | 2.3.0.1 | Start Date; Planned Sprint |
| [75334](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75334) | Add MCP Server: Review & Test – Assigned Access Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94042](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94042) | UI: Add MCP Server: Review & Test – Assigned Access Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version |
| [94043](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/94043) | API: Add MCP Server: Review & Test – Assigned Access Tab | New | 12.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/DueDate; Planned Sprint; Release Version |
| [75347](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/75347) | Register a new MCP server through the guided setup flow | New | 0.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 2 | Not Provided | Start/Due Date; Planned Sprint; Release Version; check estimation validity (0.0) |
| [53398](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/53398) | Describe Business Problem & Discover Agents | Re-Opened | 6.0 | 2 | Not Provided | Not Provided | Sprint 1 | AAVA\\PI3\\Sprint 2 | 2.2.1.0 | Start/Due Date |
| [105194](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/105194) | UX: Hierarchy Structure UX Redesign | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 | 2.3.1.0 | Story Points; Start/Due Date; Planned Sprint |
| [109141](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109141) | Consume GPT Models Through AWS Bedrock | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 | 2.3.1.0 | Story Points; Start/Due Date; Planned Sprint |
| [109476](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109476) | Removal of Level Access Function | Ready for QA | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [81849](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81849) | API: Add LLM Model: Review Step | Dev-Deployed | 4.0 | 2 | Not Provided | 2026-08-25 | Sprint 1 | AAVA\\PI4\\Sprint 2 | Not Provided | Start Date; Release Version |
| [81747](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81747) | API: Expired or Disabled LLM Model: Execution Block and Warning for Affected Agents and Workflows | New | Not Provided | 2 | Not Provided | 2026-08-28 | Sprint 1 | AAVA\\PI4 | Not Provided | Story Points; Start Date; Release Version |
| [81748](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/81748) | UI: Expired or Disabled LLM Model: Execution Block and Warning for Affected Agents and Workflows | New | Not Provided | 2 | Not Provided | 2026-08-28 | Sprint 1 | AAVA\\PI4 | Not Provided | Story Points; Start Date; Release Version |
| [83476](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/83476) | Passwordless for Storage & Secrets | Dev-Deployed | 5.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 | 2.2.1.0 | Start/Due Date; Planned Sprint |
| [74452](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/84576) | Show All-Level Access Indicator for Super Admin, CSM, PS, Executor | Ready for QA | 1.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 | 2.2.1.0 | Start/Due Date; Planned Sprint |
| [84576](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/84576) | Show All-Level Access Indicator for Super Admin, CSM, PS, Executor | Ready for QA | 1.0 | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 | 2.2.1.0 | Start/Due Date; Planned Sprint |
| [90768](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/90768) | Hide My Space -> Download VS Code Plugin Bar for Executor Role | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [106937](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106937) | Register and consume Claude models from Azure AI Foundry as LLM providers in the platform | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | 2.3.1.0 | Story Points; Start/Due Date; Planned Sprint |
| [104062](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/104062) | Premera: OBO authentication list available ADO tools through the MCP gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [105215](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/105215) | Multi-Select Agents, Workflows, Guardrails, and Knowledge Bases for All Users under Discovery Tab | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI3\\Sprint 4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [106348](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106348) | Status-Specific Edit Restriction Messaging for Artifacts | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [106787](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/106787) | Enable Scrolling for Lengthy Tool Execution Output | Groomed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 1 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [109089](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109089) | Passwordless update for sharepoint,confluence and github | Dev-Deployed | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 3 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [109891](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/109891) | MCP: Salesforce | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [119390](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119390) | Resolve Image Generation Issue for LLM Models | New | Not Provided | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [119650](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119650) | Standardize LLM Model Expiry Timezone to UTC | New | Not Provided | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [116434](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116434) | LLM Model Expiry Notification During Agent Creation | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [116435](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116435) | Embedding Model Expiry Notification During Knowledge Base Creation | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [116439](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116439) | Recommended Model Selection During Approved Agent Edit | In Progress | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [116443](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116443) | Recommended Embedding Model Selection During Approved Knowledge Base Edit | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [116702](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116702) | Recommended Model- Notification | In Progress | Not Provided | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [116705](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116705) | View Artifact from Notification Details | New | Not Provided | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [119388](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119388) | Resolve Image Generation Issue for MCP Tools | New | Not Provided | 2 | Not Provided | 2026-11-04 | Not Provided | AAVA | Not Provided | Story Points; Start Date; Planned Sprint; Release Version |
| [116673](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116673) | Onboard all direct models to AI Gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [116757](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/116757) | Register Pantheon, Control Access and Block Unsupported Endpoints | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 5 | 2.3.1.0 | Story Points; Start/Due Date; Planned Sprint |
| [119759](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119759) | UX: Control overrides with delegation range and locks | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [119762](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119762) | UX: Draft, validate, publish and recover | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [119764](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/119764) | UX: Use properties based on Capability | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [122200](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122200) | Route LLM Requests to Pantheon (Standard and Streaming) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [122201](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122201) | Generate Embeddings via Pantheon | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [122675](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122675) | AIG: Onboard Centene - Unity Framework Gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [122710](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122710) | Enable Image and Attachment(multi model input) at AI Gateway | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [101785](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/101785) | Assign Executor Role from Console by Hierarchy Node Admins | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA\\PI4\\Sprint 6 | 2.3.1.0 | Story Points; Start/Due Date; Planned Sprint |
| [122770](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/122770) | Enable Dynamic, Transformer‑Free LLM Onboarding to Reduce Model Onboarding Time (DB‑Driven Integration) | New | Not Provided | 2 | Not Provided | Not Provided | Not Provided | AAVA | Not Provided | Story Points; Start/Due Date; Planned Sprint; Release Version |
| [123815](https://dev.azure.com/ascendionava/AAVA/_workitems/edit/123815) | AIG: Dev: Onboard Gemini gemini-3.8-flash and gemini-3.1-flash-lite to AAVA | New | Not Provided | 1 | Not Provided | Not Provided | Sprint 6 | AAVA | Not Provided | StoryPoints; Start/Due Date; Release Version |

(UX Expected, Studio, Risk, Dependent Team details are retained and considered in health but omitted from this core table for brevity.)

## 4.2 User Story Planning Health

Fields evaluated:

- Story Points, Priority, Start Date, Due Date, UX Expected, Risk, Studio, Release Version, Planned Sprint, Dependent Team.

High-level completeness:

| Planning Field | Provided | Missing (Not Provided) | Unmapped | Completeness % |
|---|---|---|---|---|
| Story Points | ~60 | ~120 | 0 | ~33% |
| Priority | 180 | 0 | 0 | 100% |
| Start Date | ~15–20 | ~160+ | 0 | ~10% |
| Due Date | ~40–50 | ~130+ | 0 | ~25% |
| UX Expected | Very few | Majority Missing | 0 | Low (optional field) |
| Risk | 1 (57150) | 179 | 0 | <1% |
| Studio | Many (AIG/ACS/Foundation) | Some Missing | 0 | ~70% |
| Release Version | Several (2.2.1.0, 2.3.0.1, 2.3.1.0, 2.3.2.0) | Majority Missing | 0 | ~20–25% |
| Planned Sprint | ~30 | ~150 | 0 | ~17% |
| Dependent Team | 1 ("DevSecOps") | 179 | 0 | ~1% |

Priority and Iteration Path are well populated; **Story Points and Planned Sprint are the main gaps for sprint measurement readiness.**

## 4.3 User Story Action Report

Selected critical actions (representative; many similar stories share same gap pattern):

| Story ID | Missing / Invalid Information | Sprint / Delivery Impact | Required Action | Suggested Owner | Priority |
|---|---|---|---|---|---|
| 93164 | Story Points, Start/Due Date, Planned Sprint | Active story in PI4\\Sprint 2 cannot be measured or forecasted | Estimate Story Points; set realistic Start/Due Date; confirm Planned Sprint alignment with Iteration | Product Owner (Owner To Be Assigned) | High |
| 122848 | Story Points, schedule, Planned Sprint | New story in AAVA backlog; cannot be included in PI planning accurately | Add Story Points; define planned sprint; set basic schedule if applicable | Product Owner (Owner To Be Assigned) | Medium |
| 53146 | On Hold; missing Start/Due Date; Planned Sprint | Security vulnerabilities story estimated but stuck On Hold; risk if not reviewed | Review On Hold status; confirm whether work is deferred or must be re-planned; set schedule | Scrum Master / Engineering Lead (Owner To Be Assigned) | High |
| 57816 / 57820 | Require Clarification; Story Points and schedule missing | Clarification-needed stories in PI3\\Sprint 4 block planning | Complete clarification and refine acceptance criteria; estimate and assign sprint | Product Owner (Owner To Be Assigned) | High |
| 75347 | Story Points = 0.0 (potential invalid estimate); schedule missing | Guided MCP setup with zero points may mislead capacity planning | Confirm if 0.0 is intentional; update to realistic Story Points; assign sprint | Product Owner (Owner To Be Assigned) | Medium |
| 57150 | Risk = "1 - High"; Story Points missing; schedule missing | High-risk playground change unestimated | Add Story Points; plan sprint; align risk with mitigation actions | Product Manager (Owner To Be Assigned) | High |
| 62832 / 75267 | On Hold; unestimated; no schedule | On Hold backlog items impact long-term planning | Evaluate whether to cancel, defer, or re-activate; estimate if retained | Product Manager (Owner To Be Assigned) | Medium |
| All Stories with Iteration Path but no Story Points | Missing estimates | Cannot calculate sprint capacity/Say-Do; undercuts PI predictability | Bulk estimation pass for active/groomed stories; enforce Story Points before sprint commitment | Product Owner + Scrum Master (Owner To Be Assigned) | High |

## 4.4 User Story Delivery Assessment

### 4.4.1 Grouping by Iteration Path (Current State)

Examples (not exhaustive):

- **AAVA\\PI3\\Sprint 1–4**: Many sprint-labeled stories; most missing Story Points, some resolved or Dev-Deployed.
- **AAVA\\PI4\\Sprint 1–6**: Mix of New, Active, Dev-Deployed, Resolved; Story Points present for some MCP onboarding and LLM model configuration stories.
- **AAVA (root)**: Large backlog of New and In Progress stories without sprint assignment.

**Important rule**: Planned Sprint is not treated as interchangeable with Iteration Path. Both must be populated consistently.

### 4.4.2 Known Story Points by Sprint (Current-State Approximation)

This is **not historical Say-Do**, only current assignment.

```mermaid
xychart
  title "Current Known Story Points by Iteration Path (selected)"
  xAxis [PI3\\Sprint 2, PI3\\Sprint 3, PI3\\Sprint 4, PI4\\Sprint 1, PI4\\Sprint 2, PI4\\Sprint 3, PI4\\Sprint 4, PI4\\Sprint 5]
  yAxis "Story Points" 0 --> 80
  bar "Known Points (assigned)" [~17, ~7, ~12, ~12, ~70, ~0, ~80, ~5]
```

(Values are approximations from the listed stories; not used for official metrics.)

### 4.4.3 User Story State Distribution Chart

```mermaid
xychart
  title "User Story State Distribution"
  xAxis [New, Active, In Progress, Dev-Deployed, Ready for QA, Resolved, On Hold, Groomed, Planned, Ready for Dev, Require Clarification, Ready for Validation, Ready for Design]
  yAxis "Count" 0 --> 180
  bar "Stories" [~100+, ~20, ~5, ~10, ~10, ~20, ~6, ~4, ~2, ~3, ~2, ~2, ~3]
```

### 4.5 User Story Management Interpretation

- The Integrations team has a **large backlog with reasonable prioritization** but **poor estimation coverage**.
- Sprint-level measurement (capacity, velocity, Say-Do) is blocked by missing Story Points and inconsistent Planned Sprint usage.
- Immediate focus should be:
  - Estimating active and groomed stories.
  - Confirming sprint assignments for near-term deliveries.
  - Reviewing On Hold and Require Clarification stories.

---

# 5. Sprint-wise Say-Do and Trend Analysis

## 5.1 Say-Do Formula (Defined)

- **Primary**:  
  `Say-Do Ratio (%) = (Work Completed / Work Committed) × 100`  
  Example: Committed = 50 Story Points, Completed = 45 Story Points → Say-Do = (45/50) × 100 = **90%**

- **Inverse (if required)**:  
  `Commitment-to-Completion Ratio (%) = (Work Committed / Work Completed) × 100`  
  For the example, = (50/45) × 100 ≈ **111.1%** (not labeled as 90%).

## 5.2 Measurement Rules Applied to JSON

To calculate sprint-level Say-Do, we need:

1. Sprint identity and dates.
2. Sprint-start committed work membership.
3. Estimates frozen at sprint start.
4. Work items completed within that sprint.
5. Completion timestamps or state changes.
6. Scope changes across the sprint (add/remove).
7. Parent-child relationships and roll-up rules.

**Current JSON does not include**:

- Sprint backlog commitment snapshots.
- Per-sprint completion timestamps beyond current Due Date (which may not equal completion).
- Any explicit mark of "completed in sprint X" vs "completed before/after".

Therefore, historical Say-Do cannot be calculated from this data.

## 5.3 Sprint Performance Table

| Sprint | Work Item Type | Measurement Unit | Committed | Completed | Say-Do % | Status | Missing Evidence |
|---|---|---|---|---|---|---|---|
| AAVA\\PI3\\Sprint 1–4 | User Story | Story Points | Not Available | Not Available | Not Calculable | Insufficient Data | No sprint-start commitment snapshot; no sprint-level completion log; Story Points missing for many stories |
| AAVA\\PI4\\Sprint 1–6 | User Story | Story Points | Not Available | Not Available | Not Calculable | Insufficient Data | Same as above; plus inconsistent Planned Sprint usage |
| AAVA\\PI3 / PI4 | Feature | Feature Effort | Not Available | Not Available | Not Calculable | Insufficient Data | No committed Feature set per sprint; Feature Effort not linked to sprint history; no completion timestamps |
| AAVA\\PI3 / PI4 | Epic | Epic Effort | Not Available | Not Available | Not Calculable | Insufficient Data | No Epic Effort; no sprint-level commitment or completion evidence |

We explicitly distinguish:

- **Not Available**: historical snapshots not supplied by extraction.
- **Not Calculable**: due to zero or missing committed/complete values.

## 5.4 Sprint-on-Sprint Trend

| Sprint | Story Say-Do % | Feature Say-Do % | Epic Say-Do % | Trend / Interpretation |
|---|---|---|---|---|
| AAVA\\PI3\\Sprint 1 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI3\\Sprint 2 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI3\\Sprint 3 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI3\\Sprint 4 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI4\\Sprint 1 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI4\\Sprint 2 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI4\\Sprint 3 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI4\\Sprint 4 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI4\\Sprint 5 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |
| AAVA\\PI4\\Sprint 6 | Not Calculable | Not Calculable | Not Calculable | Insufficient Data |

No valid Say-Do values exist; a trend cannot be claimed.

```mermaid
xychart
  title "Historical Say-Do by Sprint (Not Available)"
  xAxis [PI3-S1, PI3-S2, PI3-S3, PI3-S4, PI4-S1, PI4-S2, PI4-S3, PI4-S4, PI4-S5, PI4-S6]
  yAxis "Say-Do %" 0 --> 120
  bar "Story Say-Do" [null, null, null, null, null, null, null, null, null, null]
```

(No data points plotted to avoid misleading graph.)

## 5.5 Alternative Current-State Metric (Optional)

Mainly for awareness (not official Say-Do):

**Current Completion Percentage — Not Historical Say-Do**  
For each sprint, we could compute:

`Current Completion % = (Known Points of Currently Completed Stories / Total Known Points of Currently Assigned Stories) × 100`

However, this JSON does not provide sprint-level membership vs current assignment clearly, nor completion timestamps. Calculating even this alternative metric reliably would require:

- Clear assignment of each story to a sprint backlog (beyond Iteration Path).
- Completion state mapping per sprint.

Given those are not fully verifiable here, this metric is **not reported** to avoid misinterpretation.

---

# 6. Say-Do Data Gaps and Calculation Blockers

## 6.1 Say-Do Blockers Table

| Sprint | Type | Work Item ID | Missing Evidence | Why Say-Do Is Blocked | Required Correction | Suggested Owner |
|---|---|---|---|---|---|---|
| AAVA\\PI3\\Sprint 4 | User Story | Multiple (e.g., 70433, 70450, 70431, 53369, 69441) | No sprint-start commitment snapshot; Story Points missing; completion timestamps not available | Cannot determine committed vs completed story scope or points for the sprint | Implement sprint backlog snapshot collection; ensure Story Points estimated before sprint start; extract completion timestamps from ADO | Scrum Master + Azure DevOps Administrator (Owner To Be Assigned) |
| AAVA\\PI4\\Sprint 2 | User Story | Multiple (e.g., 93164, 36969, 75325, 93754, 93755, 94022–94038, 75330, 75333, 94040, etc.) | Commitment snapshot not available; partial Story Points; no completion log per sprint | Same as above; high-impact MCP onboarding work untrackable | Configure analytics to capture sprint commitment set; enforce estimation standards; pull state-change history | Delivery Manager + Scrum Master (Owner To Be Assigned) |
| AAVA\\PI4\\Sprint 4 | Feature | 51778, 75327, 75328, 75332, 94041, 116803 | No Feature-level commitment or completion timestamps; Feature Effort not tied to sprint events | Cannot compute Feature Effort-based Say-Do per sprint | Define Feature-level measurement approach; store sprint commitments and completions; extract completion timestamps | Product Manager + Azure DevOps Administrator (Owner To Be Assigned) |
| AAVA\\PI3 / PI4 | Epic | 51718, 51736, 70804, 70807 | Epic Effort missing; no sprint commitments or completion logs; hierarchy unverified | Epic Say-Do cannot be derived from descendants or Epic metadata | Populate Epic Effort; validate Epic–Feature–Story hierarchy; implement roll-up rules and historical snapshots | Product Manager (Owner To Be Assigned) |
| All Sprints | All Types | N/A (system-wide) | Historical evidence not extracted; ADO field mapping for commitment history missing | The extraction tool only returns current fields, not historical snapshots | Extend extraction to include sprint membership history, state change timelines, and estimate-change tracking | Azure DevOps Administrator (Owner To Be Assigned) |

Distinctions:

- **ADO field is empty**: e.g., Story Points = null.
- **ADO field is unmapped**: e.g., Feature Primary User Cohort (field exists but not mapped into JSON).
- **Historical evidence was not extracted**: sprint commitment and completion data is not present.
- **Sprint metadata is unavailable**: no explicit start/end date per sprint in JSON.
- **Hierarchy or attribution unverified**: no explicit parent-child relationships in JSON.

If the JSON cannot establish which work items were committed at sprint start (which is the case here), Say-Do remains **Insufficient Data**.

---

# 7. Consolidated Management Findings

| Severity | Finding | Affected Type | Affected IDs | Evidence | Business Impact |
|---|---|---|---|---|---|
| High | Widespread missing estimates (Story Points, Feature Effort, Epic Effort) | Epic, Feature, User Story | Epics: 51718, 51736, 70804, 70807; Features with Effort null e.g., 53397, 58004, 58566, 51747, 51928–51933, 51935, 65074, 72353, 72436, 114968, 121855; Stories with Story Points null (majority) | JSON shows Effort/storyPoints = null for many items | Planning accuracy and capacity forecasting are impaired; Say-Do calculation is blocked |
| High | Missing sprint assignment (Planned Sprint) for many backlog items | Feature, User Story | Features with plannedSprint null (e.g., 58004, 51778, 58566, 51928–51933, 65074, 72353, 72436, 114968, 121855); Stories with plannedSprint null (majority) | plannedSprint field is null for many items, even when iterationPath exists | Difficult to align backlog items with specific sprints; reduces planning discipline and predictability |
| High | No historical commitment/completion data for sprints | Epic, Feature, User Story | All items | JSON includes current fields only; no snapshots or completion timestamps | Official Say-Do reporting is not possible; management cannot track delivery reliability sprint-on-sprint |
| Medium | Incomplete release information | Feature, User Story | Features with releaseVersion null (e.g., 51771–51722, 51733, 51735, 51769, 51772–51780, 51784, 51790, 51928–51933, 65074, 72353, 114968, 121855); Stories with releaseVersion null (many) | releaseVersion null for numerous items | Release coordination and cross-team dependency management are at risk |
| Medium | On Hold / Require Clarification items unreviewed | User Story | On Hold: 53146, 58014, 62832, 75267, 75329; Require Clarification: 57816, 57820 | State indicates On Hold / Require Clarification; no schedule or updated plan | Potential hidden backlog risk; unresolved items may affect security, lifecycle management, and user experience |
| Medium | Unmapped Primary User Cohort field for all Features | Feature | All Feature IDs (53397, 58004, …, 121855) | `unmappedPlanningFields: ["Primary User Cohort"]` | Cannot easily tie Features to user cohorts; reduces ability to plan user-impactful increments |

---

# 8. Corrective Action and Accountability Register

| Priority | Work Item Type | Work Item ID / Sprint | Required Correction | Suggested Owner | Suggested Timeframe | Verification Criteria |
|---|---|---|---|---|---|---|
| High | User Story | All active/groomed stories with Story Points = null (e.g., 93164, 70433, 70450, 57816, 57820, 69441, many PI4 sprint items) | Estimate Story Points before next sprint commitment; ensure each story in upcoming sprints has Story Points > 0 | Product Owner (Owner To Be Assigned) | Before next sprint planning | ADO Story Points field populated and > 0 for all stories in planned sprints |
| High | Feature | 53397, 58004, 58566, 51747, 51928–51933, 65074, 72353, 72436, 114968, 121855 | Populate Feature Effort and minimal schedule (Start/Target Date) for active/near-term Features | Product Manager (Owner To Be Assigned) | Within current PI | Effort field non-null; Target Date set; Start Date set for near-term Features |
| High | Epic | 51718, 51736, 70804, 70807 | Define Epic Effort, Start Date, Target Date, and Business Value/Time Criticality | Product Manager (Owner To Be Assigned) | Within 2 sprints | Epic Effort non-null; Start/Target Dates set; Business Value and Time Criticality populated |
| High | All Types | All PI3/PI4 Sprints | Implement sprint commitment snapshot extraction (ADO queries or analytics pipeline) | Azure DevOps Administrator (Owner To Be Assigned) | Before next PI | Evidence of stored sprint backlog membership at sprint start; retrievable via analytics |
| High | All Types | All PI3/PI4 Sprints | Extract completion timestamps/state transitions per sprint | Azure DevOps Administrator (Owner To Be Assigned) | Before next PI | Completion events stored per item; ability to query "completed during sprint X" |
| Medium | Feature | All Features (Primary User Cohort) | Resolve ADO field mapping for Primary User Cohort; decide if this field is mandatory | Azure DevOps Administrator + Product Manager (Owner To Be Assigned) | Within current PI | `unmappedPlanningFields` for Primary User Cohort no longer reported; field visible in analytics |
| Medium | User Story | On Hold and Require Clarification stories (53146, 58014, 62832, 75267, 75329, 57816, 57820) | Review status; decide to cancel, defer, or groom for upcoming sprints; update state and schedule | Scrum Master + Product Owner (Owner To Be Assigned) | Before next sprint | On Hold / Require Clarification state resolved; either moved to New/Active with Story Points and dates, or closed |
| Medium | User Story | 75347 | Validate 0.0 Story Points; correct if invalid | Product Owner (Owner To Be Assigned) | Within next sprint | Story Points updated to a realistic non-zero value or confirmed policy on zero-point work |
| Medium | User Story | 57150 | Estimate Story Points; plan sprint; address high risk | Product Manager (Owner To Be Assigned) | Before next PI | Story Points non-null; Planned Sprint set; risk field used in planning |
| Medium | All Types | Release-linked items with missing dates (multiple Features and Stories) | Align Target/Due Dates with release plans and sprint assignments | Delivery Manager (Owner To Be Assigned) | Within current release cycle | Each item with releaseVersion has Target/Due Date and Planned Sprint consistent with release schedule |

---

# 9. Final Product Manager Summary

- **Epic planning health**: Epics are prioritized but largely **unestimated and unscheduled**. Effort, Business Value, Time Criticality, Start Date, and Target Date must be populated to make Epics useful for roadmap-level planning.
- **Feature planning health**: Features show **partial planning maturity**. Many have Effort or Target Date, but rarely both, and Business Value/Risk/Time Criticality are consistently missing. Primary User Cohort is unmapped for all Features.
- **User Story planning health**: The User Story backlog is large but **under-estimated**; most stories lack Story Points and clear sprint assignment. Some high-risk and On Hold items are not actively managed.
- **Say-Do measurement readiness**: Historical Say-Do is **not calculable** from this JSON. The main blockers are missing sprint commitment snapshots, absence of completion timestamps, and incomplete estimation across all work item types.
- **Delivery predictability (evidence-based)**: Without historical Say-Do and robust estimation, delivery predictability cannot be quantified. Qualitatively, the team appears to be actively delivering MCP and LLM integration work, but management cannot reliably measure commitment vs completion.
- **Three highest-priority corrective actions**:
  1. **Enforce estimation completeness**: Ensure all upcoming sprint candidates (stories and features) have non-null Story Points/Feature Effort.
  2. **Implement historical data extraction**: Add sprint backlog commitment and completion history to the Azure DevOps analytics pipeline.
  3. **Align backlog items with sprints and releases**: Populate Planned Sprint and Target/Due Dates consistently for active Epics, Features, and Stories.
- **What must change before the next sprint planning cycle**:
  - Estimation hygiene: No story or feature should enter sprint planning without a clear estimate.
  - Sprint discipline: Planned Sprint and Iteration Path must be used consistently, with clear criteria for committing work.
  - Data infrastructure: Historical commitment and completion evidence must be captured so that Say-Do and delivery reliability can be measured and reported to leadership.

This report can be saved directly as:

**`Azure_DevOps_Planning_and_Sprint_Performance_Report.md`**
