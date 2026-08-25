# Lab 4: Autopilot, device preparation and Windows 365 provisioning

Duration: 115 minutes<br>
Alignment: LO1 · LO4 · K1 · K5 · A2 · A7<br>
Deliverable: Deployment decision, profile/ESP design, readiness evidence and Cloud PC provisioning check

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Choose deployment architecture

1. Compare classic Autopilot and Windows Autopilot device preparation against the lab constraints.
2. Choose user-driven, pre-provisioning or self-deploying mode and document prerequisites.
3. Define the Entra join type and device ownership state.
4. Create a rollback path that does not depend on user access.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Configure identity and profile

1. Create/import the lab device identity or configure the device preparation policy.
2. Assign the intended deployment profile to the test cohort.
3. Configure a valid device-name template.
4. Confirm the service shows the profile as assigned before starting OOBE.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Control provisioning

1. Create an Enrollment Status Page that blocks only the required security and application payload.
2. Record timeout and failure behavior.
3. Run the deployment on the approved test device or use the training simulation data.
4. Capture phase duration, blocking app status and final join/management state.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Extend to Windows 365

1. Create or inspect a provisioning policy with the selected image, join type and network.
2. Validate the Azure network connection or Microsoft-hosted network choice.
3. Assign the policy to the training user group.
4. Capture the Cloud PC provisioning state and Intune managed-device record.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
