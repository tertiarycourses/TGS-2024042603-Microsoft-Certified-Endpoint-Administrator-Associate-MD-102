# Lab 7: Update rings, feature updates, Autopatch, Hotpatch and Delivery Optimization

Duration: 110 minutes<br>
Alignment: LO1 · LO2 · K1 · K2 · A2 · A5<br>
Deliverable: Staged update design, eligibility checks, rollout metrics and rollback decision evidence

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Design staged rollout

1. Create pilot, early adopter and broad deployment cohorts.
2. Define quality-update deferral, deadline, grace period and restart experience per ring.
3. Create a feature update policy for the target Windows release.
4. Record rollback and pause decision thresholds.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evaluate service options

1. Compare self-managed update rings with Windows Autopatch for the scenario.
2. Check Hotpatch edition, baseline and service prerequisites.
3. Configure Delivery Optimization group or connected-cache behavior for the lab network.
4. Document non-Windows update controls for macOS/iOS or Android where relevant.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Analyze update evidence

1. Open the Intune Windows update report and filter to the lab cohort.
2. Record offer, download, install, restart and error states.
3. On the device, generate WindowsUpdate.log or inspect the provided log sample.
4. Identify any safeguard hold, eligibility block or policy conflict.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Decide and verify

1. Apply the trainer-provided update failure scenario.
2. Choose pause, expedite, rollback or targeted remediation based on evidence.
3. Implement the approved action in the training tenant.
4. Capture the post-action compliance rate and affected-device list.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
