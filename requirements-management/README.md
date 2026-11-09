# Requirements Management Tools

## 1. Introduction to Requirements Management

A **requirement** is a statement of what a system must do or a quality it must have. **Requirements management** is the process of documenting, organising, tracking, and controlling requirements throughout a project.

### Types of requirements

| Type | Meaning | Example |
|------|---------|---------|
| Functional | What the system does | "The system shall let a student register for a course." |
| Non-functional | How well it does it | "The login page shall load in under 2 seconds." |
| Business | Goals of the organisation | "Reduce manual enrolment work by 50%." |
| Constraint | Limits on the solution | "The system must run on Linux servers." |

### Why use tools instead of a Word document?

- Every requirement gets a **unique ID** (for example `REQ-012`).
- Requirements can be **linked** to design, code, and tests.
- **Changes are recorded**: who changed what, when, and why.
- Teams can **filter, search, and report** (for example "all unapproved requirements").
- Large projects may have thousands of requirements, which is impractical to track by hand.

### A well-written requirement is

- **Clear**: one interpretation only.
- **Testable**: you can prove it is met.
- **Atomic**: one idea per requirement.
- **Traceable**: it has an ID and a source.

Weak: *"The system should be fast."*
Better: *"REQ-007: The system shall return search results within 3 seconds for 95% of queries."*

---

## 2. IBM Rational DOORS

**DOORS** (Dynamic Object-Oriented Requirements System) is an established requirements tool, widely used in safety-critical industries such as aerospace, automotive, defence, and medical devices. IBM now offers DOORS Next as part of its Engineering Lifecycle Management portfolio.

### Key features

- **Modules**: containers that hold requirements as structured objects (like a database table).
- **Object attributes**: each requirement has fields such as ID, text, priority, status, and owner.
- **Links**: connect requirements to other requirements, designs, or test cases.
- **Baselines**: frozen snapshots of a module at a point in time (for example "Release 1.0").
- **Change history**: every edit is logged.
- **Views and filters**: show only what matters, such as high-priority items.

### Typical workflow

1. Import or write requirements into a module.
2. Review and approve them with stakeholders.
3. Create a baseline.
4. Link requirements to design elements and test cases.
5. Manage change requests as the project evolves.

---

## 3. Comparable Tools

| Tool | Best known for | Notes |
|------|----------------|-------|
| **Jira** (Atlassian) | Agile issue and backlog tracking | Requirements are often written as epics and user stories. Marketplace add-ons add traceability. |
| **Jama Connect** | Dedicated requirements and traceability | Live traceability, review workflows, popular in regulated industries. |
| **Azure DevOps** (Microsoft) | Full lifecycle: boards, repos, pipelines | Work items represent requirements, tasks, and bugs. Integrates with Visual Studio. |
| **IBM DOORS Next** | Enterprise requirements | Web-based successor in the IBM ecosystem. |
| **Polarion** (Siemens) | Requirements plus testing in one platform | Common in engineering-heavy sectors. |

### Choosing a tool

- Small student or agile team: Jira, GitHub Issues, or Azure DevOps Boards.
- Regulated or safety-critical project: DOORS, Jama Connect, or Polarion.
- Already using Microsoft tools: Azure DevOps.

### Example: a requirement as a user story (Jira style)

```
Title: Student can reset password
As a registered student,
I want to reset my password through my email,
so that I can regain access if I forget it.

Acceptance criteria:
- A reset link is emailed within 1 minute.
- The link expires after 30 minutes.
- The new password must be at least 8 characters.
```

---

## 4. Requirements Traceability

**Traceability** is the ability to follow a requirement forwards to the things that implement and verify it, and backwards to where it came from.

- **Forward traceability**: requirement → design → code → test.
- **Backward traceability**: test → code → design → requirement → stakeholder need.

### Traceability matrix example

| Requirement | Description | Design element | Code module | Test case |
|-------------|-------------|----------------|-------------|-----------|
| REQ-001 | Student can log in | Login Use Case | `auth.py` | TC-001, TC-002 |
| REQ-002 | Student can register for a course | Registration Class Diagram | `enrol.py` | TC-003 |
| REQ-003 | Admin can view reports | Report Sequence Diagram | `reports.py` | TC-004 |

### Benefits

- Shows whether any requirement has **no test** (a gap).
- Shows whether any code exists with **no requirement** (unnecessary work).
- Helps assess the **impact** of a change.

---

## 5. Change Management

Requirements change. Change management keeps that under control.

### Typical process

1. **Request**: someone submits a change request describing the change and the reason.
2. **Impact analysis**: use traceability links to find affected design, code, and tests.
3. **Review and decision**: a change control board or team lead approves or rejects it.
4. **Implementation**: update the requirement, design, code, and tests.
5. **Record**: update the version history and create a new baseline if needed.

### Example change request

```
CR-004: Change password minimum length from 8 to 12 characters
Requested by: Security team
Affected requirements: REQ-014
Affected tests: TC-021, TC-022
Decision: Approved
```

### Link to source control

The same idea applies in Git: commits and pull requests can reference issue numbers (for example `Fixes #14`), which gives lightweight traceability between a requirement and the code that implements it. See [documentation](../documentation/README.md).

---

## Key Points

- Requirements management keeps requirements organised, traceable, and controlled.
- DOORS is strong for large, regulated projects. Jira and Azure DevOps suit agile teams.
- Traceability connects requirements to design, code, and tests.
- Change management ensures changes are reviewed and recorded.

## References

- IBM DOORS family: https://www.ibm.com/products/requirements-management
- Jira documentation: https://support.atlassian.com/jira-software-cloud/
- Jama Connect: https://www.jamasoftware.com/platform/jama-connect/
- Azure DevOps documentation: https://learn.microsoft.com/azure/devops/
