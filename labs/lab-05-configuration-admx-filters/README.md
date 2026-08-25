# Lab 5: Settings Catalog, ADMX migration and assignment filters

Duration: 110 minutes<br>
Alignment: LO2 · K2 · K4 · A2 · A4<br>
Deliverable: Migrated settings policy, filter preview, conflict diagnosis and corrected per-setting result

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Analyze legacy policy

1. Export the trainer-provided GPO report as XML.
2. Import it into Group Policy analytics and record supported, deprecated and unknown settings.
3. Select only supported controls required by the scenario.
4. Record redesign decisions for unsupported settings.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Create cloud policy

1. Build a Settings Catalog profile with the selected controls.
2. Import the required ADMX only if the setting is absent from the catalog.
3. Assign the policy to a pilot group.
4. Create an assignment filter using an exact supported device property.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Seed a conflict

1. Assign a second training profile that sets one control differently.
2. Sync the device and reproduce the per-setting conflict.
3. Collect the policy report, MDMDiag output and relevant MDM event.
4. Identify both source profiles before changing either.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Consolidate and verify

1. Choose the authoritative profile and remove the overlapping setting from the other profile.
2. Sync the device and wait for the service report to refresh.
3. Verify the per-setting state is successful and the client value matches.
4. Save the final policy export and filter preview as evidence.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
