# Lab 2: Multi-platform Intune enrollment and troubleshooting

Duration: 115 minutes<br>
Alignment: LO1 · K1 · K3 · A1 · A3<br>
Deliverable: Enrollment configuration matrix, MDMDiag evidence, error-code diagnosis and successful retest

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Plan enrollment

1. Build a platform matrix for Windows, macOS, iOS/iPadOS and Android corporate/personal ownership.
2. Record the intended enrollment method, authority connector, license and user scope for each platform.
3. In Intune, review Devices > Enrollment and record token/connector health.
4. Review enrollment restrictions and identify which personal platforms are allowed or blocked.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Configure the Windows path

1. Verify MDM user scope includes the lab user.
2. Verify the user has the required Intune entitlement.
3. Join or register the Windows test device according to the lab scenario.
4. Trigger Settings > Accounts > Access work or school > Info > Sync.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Collect diagnostics

1. Run `mdmdiagnosticstool.exe -area DeviceEnrollment;DeviceProvisioning;Autopilot -cab evidence\MDMDiagnostics.cab`.
2. Open Event Viewer > DeviceManagement-Enterprise-Diagnostics-Provider > Admin.
3. Record the first error code or successful enrollment event and its timestamp.
4. Use Intune Troubleshooting + support to correlate the user and managed-device record.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Seed and recover

1. Apply the trainer-provided restriction or scope mismatch that blocks enrollment.
2. Reproduce the failure and record the exact HRESULT/correlation ID.
3. Correct only the failed prerequisite, then retry enrollment.
4. Capture the successful managed record, ownership, primary user and last check-in.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
