# Case study: from infrastructure capabilities to self-service delivery

## Scenario

I was working on a shared Kubernetes platform where application teams deployed through GitOps and Argo CD. The platform already had important infrastructure and delivery capabilities. The challenge was making those capabilities accessible as a coherent product.

A developer's desired outcome was simple: connect a repository, configure the application, obtain a development URL, promote a tested release, and recover an earlier release when needed. Behind that request were build pipelines, artifact handling, Kubernetes resources, identity, secrets, routing, review policies, and deployment feedback.

## My role

My contribution centered on product framing, platform design, delivery sequencing, and an AI-assisted implementation POC:

1. Translate the broad self-service goal into a concrete application lifecycle.
2. Review the feature backlog and source evidence instead of assuming the backlog reflected current implementation.
3. Recognize existing reusable workflow work and plan consolidation around it.
4. Separate generic Helm templates from application/service/environment values.
5. Use a pilot to test compatibility without changing running services.
6. Establish explicit evidence levels and a repeatable handoff record.

I used AI coding tools to accelerate research, implementation, and documentation. I supplied the goals, scope, sequencing decisions, and delivery constraints, and reviewed the outputs. That collaboration is part of the method, not a substitute for review or runtime validation.

## Constraints that shaped the design

- Existing services needed to keep running throughout the POC.
- Application repositories should not be forced into one folder or branch convention.
- Routine release ownership should sit with the application team.
- Cross-tenant or privileged changes still needed platform review.
- A UI should expose a shared operation contract rather than create a second delivery implementation.
- An isolated work branch should not silently become a permanent environment model.

## How I moved the work forward

The initial backlog contained many related capabilities. Starting every area at once would make the team dependent on unfinished contracts and difficult to coordinate. I chose two practical streams:

- **Shared workflows:** inventory the current callers, define versioned inputs, and plan migration into a dedicated workflows repository.
- **Shared chart:** reproduce selected existing service resources through reusable templates and layered values.

Only the API contract needed to support those streams was required at the start. The full dashboard came later, once the underlying operations could be proven.

## What the POC established

The POC produced a reusable chart structure, representative application values, local validation tooling, and an explicit list of unsupported or specially owned resources. Manifest parity checked whether chart output preserved the committed configuration.

That established a reviewable basis for migration. It did **not** establish that the platform was deployed end to end, that the running cluster matched Git, or that production outcomes had improved. Those require separate evidence.

## Transferable achievement

The achievement was making a large platform initiative actionable: a product contract, an ordered delivery plan, a compatibility-focused POC, and a record another engineer could pick up. The reusable lesson is to convert infrastructure work into a developer journey with explicit owners and observable completion criteria.
