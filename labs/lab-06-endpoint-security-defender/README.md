# Lab 6: Endpoint security, Defender, BitLocker, firewall and ASR

Duration: 120 minutes<br>
Alignment: LO2 · LO3 · K3 · K4 · A4 · A5 · A6<br>
Deliverable: Security control set with Defender/BitLocker/firewall/ASR verification and exception record

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Design the control set

1. Define Defender Antivirus, BitLocker, Firewall and ASR requirements for the lab device group.
2. Map each requirement to an Intune Endpoint security policy surface.
3. Identify where a security baseline overlaps and remove duplicate ownership.
4. Record the rollout mode for every ASR rule: audit, warn or block.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Deploy and inspect

1. Create and assign the approved endpoint-security policies to the pilot cohort.
2. Sync the test device.
3. Run `Get-MpComputerStatus`, `manage-bde -status` and `Get-NetFirewallProfile`.
4. Capture Intune per-setting status and Defender onboarding/sensor health.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Generate evidence

1. Run the trainer-approved benign ASR test or inspect provided event data.
2. Open the CodeIntegrity/Defender/Firewall evidence channels specified by the trainer.
3. Correlate device ID, policy name, event ID and timestamp.
4. Record the control that produced each observed outcome.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Tune safely

1. Seed an allowed business-app exception scenario.
2. Replace any broad global exclusion with the narrowest supported per-rule exception.
3. Retest the application and the control.
4. Create an exception record with owner, rationale, expiry and compensating control.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
