# Lab 10 - MD-102 Capstone and Exam Readiness

## Objectives

- Design an end-to-end endpoint management solution.
- Map requirements to Intune, Entra ID, Defender, Autopilot, Windows 365, app, and reporting capabilities.
- Include safety, governance, monitoring, and cleanup.
- Build an exam readiness plan.

## Scenario

You must design a modern endpoint management approach for a company with Windows laptops, macOS devices, iPhones, Android devices, Cloud PCs, BYOD users, and regulated data.

## Steps

### 1. Build a Capability Map

| Requirement | Capability |
| --- | --- |
| Cloud join Windows devices | Microsoft Entra join |
| Manage corporate devices | Intune enrollment |
| Deploy new laptops | Windows Autopilot |
| Provide virtual desktops | Windows 365 |
| Require compliant device access | Compliance and Conditional Access |
| Encrypt Windows devices | BitLocker policy |
| Protect endpoints | Defender for Endpoint and endpoint security |
| Deploy apps | Intune app deployment |
| Protect BYOD app data | App protection policies |
| Monitor health | Endpoint Analytics and reports |
| Automate tasks | PowerShell and Microsoft Graph |

### 2. Draw the Architecture

Include:

```text
Users
Devices
Microsoft Entra ID
Intune
Defender for Endpoint
Autopilot
Windows 365
Conditional Access
Apps
Reports and automation
```

### 3. Create Policy Rollout Plan

Use rings:

```text
Lab
Pilot
Early adopters
Broad production
Exceptions
```

### 4. Add Safety Controls

Document:

- Test groups.
- Break-glass account.
- Report-only Conditional Access.
- Approval for destructive remote actions.
- Policy assignment review.
- Change rollback plan.

### 5. Rate Skill Confidence

| Skill Area | Confidence 1-5 | Study Action |
| --- | --- | --- |
| Prepare infrastructure for devices |  |  |
| Manage and maintain devices |  |  |
| Protect devices |  |  |
| Manage and secure applications |  |  |
| Optimize endpoint operations |  |  |

### 6. Create a 7-Day Study Plan

1. Day 1: Entra device identity, groups, enrollment.
2. Day 2: Compliance, Conditional Access, Windows Hello, LAPS.
3. Day 3: Autopilot, Windows 365, configuration profiles.
4. Day 4: Endpoint security, Defender, BitLocker, firewall, ASR.
5. Day 5: Updates, Autopatch, Delivery Optimization.
6. Day 6: Apps, app protection, app configuration.
7. Day 7: Automation, reporting, Endpoint Analytics, mistakes log.

## Validation

You should have a capability map, architecture diagram, rollout plan, safety controls, confidence matrix, and study plan.

## Checkpoint Questions

1. Which policy should be piloted first?
2. Which remote action requires the most caution?
3. How does compliance influence access?
4. Which MD-102 skill area needs more review?

## Exam Focus

MD-102 rewards practical endpoint operations judgment: target policies carefully, protect devices, manage apps, automate safely, monitor health, and avoid production-impacting mistakes.
