# Interview guide

Use these as prompts for an accurate discussion. Adapt the wording to your own contribution and to what has actually shipped at the time of the interview.

## A short project introduction

> I worked on making an existing shared Kubernetes and GitOps platform easier for application teams to use. I framed a self-service lifecycle, reviewed what already existed, and prioritized shared workflows and a reusable Helm chart. I directed an AI-assisted chart POC and validation, keeping application values separate from templates and avoiding a live migration during the experiment. The next stage is connecting those operations to a portal and measuring the end-to-end journey.

## Story 1: make a broad initiative executable

- **Situation:** the platform goal spanned onboarding, builds, configuration, promotion, visibility, and recovery.
- **Task:** identify a useful starting point and a handoff others could follow.
- **Action:** map features to dependencies and evidence; separate workflow and chart streams; define a minimum shared contract.
- **Result:** a source-informed delivery plan, explicit decisions and blockers, and concrete pickup tasks. Production benefits remained targets to measure.

## Story 2: reduce repeated configuration without moving production

- **Situation:** services used repeated Kubernetes resource patterns with important differences.
- **Task:** prove a shared chart could preserve the current committed behavior.
- **Action:** separate templates from layered values, map resources and exceptions, compare parsed renders, and introduce deliberate drift to exercise the check.
- **Result:** a reviewable POC and compatibility evidence, with live cutover deferred.

## Story 3: lead AI-assisted engineering responsibly

- **Situation:** research and implementation crossed multiple repositories and feature areas.
- **Task:** use coding assistance without losing scope control or overstating results.
- **Action:** supply specific goals and constraints, distinguish findings from assumptions, review evidence boundaries, and keep delivery states explicit.
- **Result:** useful implementation and documentation artifacts while preserving the distinction between generated code, reviewed work, and deployed behavior.

## Questions to prepare for

1. Why a portal rather than more repository templates?
2. Why keep a platform API if workflows execute the work?
3. How would a release be authorized and traced across tools?
4. How do you prevent two releases from owning the same shared resource?
5. How do you distinguish manifest parity from application compatibility?
6. How does rollback interact with GitOps reconciliation?
7. What remains unproven in the current milestone?
8. What did you personally decide, and what did the team or AI tools contribute?
9. What would you change for a smaller company or another cloud?
10. Which metrics would demonstrate actual improvement?

## Resume wording that fits the current milestone

- Led the design and delivery breakdown of a self-service Kubernetes application platform spanning reusable workflows, GitOps, and developer-facing lifecycle operations.
- Directed and reviewed an AI-assisted Helm chart POC with layered application values and local manifest-parity validation.
- Established evidence-based handoffs that distinguished planned work, pushed artifacts, hosted checks, and runtime validation.

Avoid describing the full platform as production-delivered or attaching unmeasured time/cost savings to the POC. Update these statements as subsequent milestones are completed.
