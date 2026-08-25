# Lab 8: Win32 apps, Microsoft 365 Apps, MAM and app configuration

Duration: 120 minutes<br>
Alignment: LO2 · LO3 · K2 · K3 · A2 · A5<br>
Deliverable: Deployable app contract, detection evidence, MAM/CA test matrix and troubleshooting trace

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Build a Win32 app contract

1. Package the trainer-provided source with the Intune Win32 Content Prep Tool or inspect the supplied `.intunewin` metadata.
2. Define silent install and uninstall commands with the correct context.
3. Create version-aware detection and explicit requirement rules.
4. Map vendor exit codes to success, retry, soft reboot and hard reboot.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Deploy and sequence

1. Upload/create the app in Intune and assign it to the pilot group.
2. Configure the supplied prerequisite as a dependency.
3. Configure supersedence for the previous version without creating a cycle.
4. Trigger device sync and monitor install status.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Protect app data

1. Create an app protection policy for the supported mobile app.
2. Set work-data transfer, encryption, access and selective-wipe controls.
3. Create a Conditional Access policy requiring app protection in report-only mode.
4. Test managed and unmanaged device/app combinations using the evidence matrix.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Troubleshoot and close

1. Seed a detection or requirement-rule failure.
2. Inspect IntuneManagementExtension.log and the per-device install details.
3. Correct the smallest failing contract element and retry.
4. Capture installed version, detection success and app-protection status.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
