# Lab 3: Compliance, Conditional Access, Windows Hello and LAPS

Duration: 115 minutes<br>
Alignment: LO2 · K3 · K4 · A4 · A6<br>
Deliverable: Compliance/CA decision trace, WHfB state and auditable LAPS recovery/rotation evidence

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Create compliance policy

1. In Intune, create a Windows compliance policy requiring encryption, firewall and the trainer-specified OS version.
2. Set a short training grace period and assign only to the lab device group.
3. Record every configured setting and the noncompliance action.
4. Sync the device and inspect per-setting compliance.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Create Conditional Access safely

1. In Entra Conditional Access, create a policy requiring a compliant device for the lab cloud app.
2. Exclude the designated emergency-access account.
3. Start in report-only mode and run the What If tool for compliant and noncompliant scenarios.
4. Enable only when the trainer confirms the report-only results are correct.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Validate WHfB and LAPS

1. Assign the Windows Hello for Business policy and record the selected trust model.
2. On the device, run `dsregcmd /status` and verify the expected NGC/PRT state.
3. Assign the Windows LAPS policy to back up passwords to Entra ID.
4. Verify the password backup timestamp and retrieve it only with the authorized role.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Diagnose and prove recovery

1. Seed one compliance or access mismatch.
2. Use the device compliance details and sign-in log to locate the failed condition.
3. Correct the policy/assignment, sync, and rerun the sign-in test.
4. Rotate the LAPS password after access and capture the audit event.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
