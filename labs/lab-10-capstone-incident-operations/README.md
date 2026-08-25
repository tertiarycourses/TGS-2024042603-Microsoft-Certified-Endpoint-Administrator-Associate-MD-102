# Lab 10: Capstone: investigate access, remediate endpoints and brief operations

Duration: 110 minutes<br>
Alignment: LO4 · K5 · A7 · A8<br>
Deliverable: Incident timeline, containment record, remediation proof, access review and executive operations brief

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Triage unauthorized access

1. Review the supplied sign-in, Conditional Access, device risk and endpoint timeline evidence.
2. Correlate user ID, device ID, app, IP, policy and timestamps.
3. Build an ordered incident timeline.
4. State the scope and confidence level before containment.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Contain and preserve evidence

1. Revoke user sessions and isolate/retire only the device authorized by the scenario.
2. Preserve relevant logs, request/correlation IDs and screenshots before destructive actions.
3. Remove or suspend excessive access rights.
4. Record every containment action, actor and time.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Remediate operations

1. Use the supplied detection script to confirm the endpoint issue.
2. Run the approved idempotent remediation on the pilot device.
3. Perform a post-detection or direct state check.
4. Restore access only after identity risk, device health and compliance are acceptable.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Brief and close

1. Create a concise operations brief: impact, root cause, control failure, actions and remaining risk.
2. Attach the evidence index and access-review result.
3. Define a tenant-health alert or operational baseline that would detect recurrence sooner.
4. Obtain trainer sign-off on A7/A8 evidence.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
