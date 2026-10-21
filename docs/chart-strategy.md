# Shared chart, separate application values

## The problem with copied resource files

Copying the same Deployment, Service, and Ingress patterns per application makes the first service easy to add but makes later fixes repetitive. A shared chart moves common structure into templates while preserving explicit service differences.

## Illustrative layout

```text
charts/application/
  Chart.yaml
  values.yaml
  values.schema.json
  templates/
applications/sample-suite/
  values.yaml
  services/web/
    values.yaml
    values-development.yaml
    values-staging.yaml
    values-production.yaml
  services/api/
    values.yaml
    values-development.yaml
  ingress/
    values-development.yaml
```

The names and layout here are illustrative. No workplace chart or values files are included.

## What belongs where

| Shared template and platform contract | Application values |
|---|---|
| Resource structure and supported fields | Image reference and application ports |
| Validation schema and baseline defaults | Health endpoints and sizing |
| Naming and selector conventions | Environment settings and secret references |
| Supported resource profiles | Application hostname and routing selections |
| Version compatibility rules | Explicitly reviewed exceptions |

Values layer from chart defaults to application settings, service base values, and environment overrides. The layering rules must be documented: Helm merges maps, while lists typically replace earlier lists.

## Scope and exceptions

Start with stateless HTTP services. Optional supporting resources can include autoscaling, disruption budgets, monitoring, and service accounts when their behavior is understood. Workers, jobs, databases, gateways, and shared infrastructure should be modeled deliberately rather than forced into the HTTP profile.

Shared resources need one owner. For example, an application-level Ingress can route to several services; allowing each service release to create the same Ingress creates an ownership collision.

## Migration without accidental changes

1. Inventory the committed resources and their owners.
2. Render the current configuration with its existing tooling.
3. Render the new chart with representative values.
4. Compare parsed resources, including selectors, probes, security settings, and routing.
5. Require every object to be matched or explicitly excluded with a reason.
6. Introduce deliberate drift to verify that the comparison detects it.
7. Review differences before selecting a live cutover strategy.

The POC followed this compatibility-first method. An unchanged render is evidence about configuration, not proof about the running cluster.

## Compatibility and hardening are separate changes

A secure default can alter an existing application's behavior. During parity work, preserve intentional current settings and record hardening gaps separately. Later hardening changes should be tested and reviewed explicitly. A schema alone is also not an authorization boundary: the platform must control which keys an application team may override.

## Versioning

Version the chart and its values contract. Test new versions against representative consumers, document breaking changes, and let consumers pin a supported version. When the existing image-promotion tooling edits raw manifests, moving to values files also requires a separate promotion-path change.
