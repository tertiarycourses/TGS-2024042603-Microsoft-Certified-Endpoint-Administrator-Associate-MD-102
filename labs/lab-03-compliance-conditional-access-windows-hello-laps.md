# Lab 03 - Compliance, Conditional Access, Windows Hello, LAPS

## Objectives

- Design compliance policies across platforms.
- Link device compliance to Conditional Access.
- Plan Windows Hello for Business.
- Plan Windows LAPS with Intune and Entra ID.
- Manage local group membership on Windows devices.

## Scenario

The security team requires only compliant devices to access corporate email and cloud apps.

## Steps

### 1. Design Compliance Policy

Create a table:

| Platform | Compliance Requirement |
| --- | --- |
| Windows | BitLocker enabled, Defender active, minimum OS version |
| iOS/iPadOS | PIN required, not jailbroken |
| Android | Work profile, not rooted |
| macOS | FileVault enabled, minimum OS version |

### 2. Plan Conditional Access

Document:

```text
Target users
Target cloud apps
Device compliance requirement
Exclusions
Report-only testing
Break-glass account exclusion
```

### 3. Plan Windows Hello for Business

Record:

- Deployment method.
- PIN settings.
- Biometrics policy.
- Key trust or cloud trust considerations.
- User experience.

### 4. Plan Windows LAPS

Document:

- Local admin password rotation.
- Password storage location.
- Retrieval permissions.
- Rotation after use.
- Audit requirements.

### 5. Local Group Membership

Plan how Intune can manage local Administrators group membership on Windows devices.

## Validation

You should have compliance rules, Conditional Access plan, Windows Hello plan, LAPS plan, and local group plan.

## Checkpoint Questions

1. What makes a device compliant?
2. Why use report-only mode first?
3. What does Windows LAPS protect?
4. Why exclude break-glass accounts from Conditional Access?

## Exam Focus

MD-102 connects compliance, Conditional Access, identity, Windows Hello, LAPS, and local group management.
