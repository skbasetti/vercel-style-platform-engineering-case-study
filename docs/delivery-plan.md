# Delivery plan and handoff

## Sequence

| Stage | Work | Exit evidence |
|---|---|---|
| 1. Establish the baseline | Inventory existing workflows, chart candidates, ownership, and operation contracts | Source-backed gap map and selected pilot boundary |
| 2. Prepare reusable delivery | Consolidate existing workflow logic; define versioning and inputs | Migration plan and representative caller |
| 3. Build chart POC | Generic templates, values, schema, and compatibility checks | Reviewable branch and local parity results |
| 4. Connect lifecycle operations | Identity, artifact handling, repository adapters, and configuration | Authorized requests produce traceable desired-state changes |
| 5. Build a thin UI | Onboarding form and operation status over the shared API | A user can complete one real development journey |
| 6. Prove recovery and promotion | Environment policy, release history, approval, and rollback | Same tested artifact promoted and earlier release restored |
| 7. Expand | More applications, better UX, documentation, and capacity planning | Pilot review and voluntary adoption evidence |

Stages 1 and 3 are the completed planning/POC focus represented here. Later stages remain an implementation roadmap; some organization-specific foundational capabilities already existed and should be reused.

## Feature coverage

| Capability | First useful step |
|---|---|
| API and CLI | Document the minimum operation contract; resolve non-browser authentication |
| Ownership | Audit who approves routine releases and cross-tenant changes |
| Build and artifacts | Inventory existing reusable workflows before creating replacements |
| App chart | Reproduce one representative workload through templates and values |
| Onboarding | Trace the request through the repository adapter to reconciliation |
| Status and logs | Distinguish desired state, running state, and observed health |
| Identity | Define user, team, and automation authorization separately |
| Configuration | Separate ordinary settings from secret delivery |
| Domains and TLS | Design default exposure and ownership before custom-domain automation |
| Dashboard | Design task flows and failure states, then implement against working APIs |
| Promotion and rollback | Use immutable releases and reviewed desired-state changes |
| Adoption | Define pilot success, migration, and recovery criteria |
| Preview environments | Defer until isolation, capacity, and cleanup are proven |

## Work that can proceed independently

**Workflow stream:** caller inventory, reusable inputs, version policy, migration order, and existing behavior tests.

**Chart stream:** resource mapping, schema, layered values, render parity, and unsupported-resource inventory.

**Shared decisions:** the minimum API contract, ownership of shared resources, pilot boundary, and evidence required before cutover. Team assignments should follow availability and capability, rather than being implied by the architecture.

## Daily handoff template

```markdown
## Date
- Decision: what changed, who decided, and why
- Completed: artifact or reviewed change
- Validation: command/check, result, and evidence level
- Remaining: exact next task and completion criteria
- Blocker: dependency, owner, and required evidence
- Delivery state: local / pushed / reviewed / merged / deployed
```

This working record reduces the cost of someone joining midway through the initiative. It also prevents a plan, a pushed branch, and a live deployment from being treated as the same milestone.
