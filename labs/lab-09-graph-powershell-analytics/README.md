# Lab 9: Graph, PowerShell, remote actions and Endpoint Analytics

Duration: 115 minutes<br>
Alignment: LO3 · LO4 · K3 · K5 · A5 · A7<br>
Deliverable: Least-privilege automation transcript, paginated export, remote-action evidence and KPI readout

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Authenticate with least privilege

1. Open PowerShell 7 and connect with `Connect-MgGraph` using only the lab read scopes.
2. Run `Get-MgContext` and verify TenantId, Account and Scopes.
3. Record the Graph `v1.0` endpoint and selected resource.
4. Do not request write permissions until the trainer authorizes the change task.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Export all managed devices

1. Request the managedDevices collection with selected fields.
2. Follow every `@odata.nextLink` until no next page remains.
3. Export device ID, name, OS, compliance and last-sync values to CSV.
4. Compare the exported count with the service report.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Perform a controlled action

1. Resolve one lab device by stable device ID.
2. Preview the intended action and confirm ownership.
3. Run the approved sync or rotate-key action.
4. Capture the audit actor, time and resulting status.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Interpret analytics

1. Open Endpoint Analytics and record the current startup, application reliability and restart signals.
2. Segment by the trainer-provided device model or OS cohort.
3. Identify one outlier and propose a bounded proactive remediation.
4. Define the before/after metric that will prove improvement.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
