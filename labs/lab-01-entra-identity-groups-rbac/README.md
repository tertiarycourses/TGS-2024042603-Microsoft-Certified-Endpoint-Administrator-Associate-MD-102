# Lab 1: Entra device identity, dynamic groups and delegated administration

Duration: 110 minutes<br>
Alignment: LO1 · K1 · K4 · A1 · A3<br>
Deliverable: Validated join-state evidence pack, dynamic-group rule, scoped role assignment and audit trace

## Safety and prerequisites

- Use only the training tenant, test users and test devices supplied by the trainer.
- Confirm the tenant ID before any change.
- Capture before-state evidence and use least privilege.
- Ask before wipe, retire, isolate, reprovision or other destructive actions.

## Establish tenant and role boundaries

1. Sign in to the Microsoft Entra admin center with the lab administrator role supplied by the trainer.
2. Record the tenant ID and confirm you are in the training tenant, not a production tenant.
3. Open Identity > Devices > All devices and record the current device count.
4. Open Devices > Device settings and document join and local-administrator controls before changing them.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Validate a device identity

1. On the Windows test device, open Windows Terminal as administrator.
2. Run `dsregcmd /status` and save the Device State, Device Details and SSO State blocks.
3. Correlate DeviceId and TenantId with the Entra device object.
4. Classify the device as registered, Entra joined or hybrid joined and justify the classification from flags.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Create a dynamic targeting rule

1. Open Entra ID > Groups > New group and select Security with Dynamic Device membership.
2. Create a rule for corporate Windows devices, preview the result, then save only after the expected test device appears.
3. Record the exact rule and preview result in the evidence folder.
4. Assign a descriptive owner and purpose to the group.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Delegate and verify

1. Create or inspect an Intune role assignment with a narrow scope group and scope tag.
2. Use a test operator account to verify visibility is restricted to intended objects.
3. Review the audit log for the role/group changes.
4. Revoke the temporary test assignment if instructed and capture the final state.

Acceptance check: capture the configured state, observed result, timestamp/correlation ID and interpretation.

## Evidence submission

Save evidence under `evidence/` and complete `evidence/README.md`. Do not include passwords, recovery keys, tokens, tenant secrets or unrelated personal data.

## Source trace

Aligned to Microsoft MD-102 skills measured 24 July 2026 and adapted from MicrosoftLearning repository commit `25eaad2a79548c4767ea45eae8d08649622c583a`.
