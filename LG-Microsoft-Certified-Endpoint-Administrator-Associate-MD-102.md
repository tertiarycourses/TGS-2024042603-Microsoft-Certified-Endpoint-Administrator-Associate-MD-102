# Learner Guide - Microsoft Certified Endpoint Administrator Associate (MD-102)

## Course Information

| Item | Details |
| --- | --- |
| Course Code | TGS-2024042603 |
| Course Title | Microsoft Certified Endpoint Administrator Associate (MD-102) |
| Registration | https://www.tertiarycourses.com.sg/wsq-microsoft-certified-endpoint-administrator-associate-md-102.html |
| Microsoft Study Guide | https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/md-102 |

## Course Goal

This course helps learners prepare to manage and secure endpoints in a Microsoft 365 tenant by using Microsoft Intune, Microsoft Entra ID, Windows Autopilot, Defender for Endpoint, Windows 365, PowerShell, Microsoft Graph, and endpoint monitoring/reporting tools. The labs focus on practical endpoint administration decisions and safe test-tenant workflows.

## Prerequisites

- Basic Microsoft 365 administration awareness.
- Basic Windows client administration knowledge.
- Familiarity with Microsoft Entra ID concepts.
- Access to an instructor-provided tenant or approved lab tenant.
- A test device or simulated lab environment where available.

## Learning Outcomes

By the end of the course, learners should be able to:

- Prepare Microsoft Entra ID and Intune infrastructure for endpoint management.
- Plan device join, registration, grouping, and enrollment strategies.
- Configure compliance policies and Conditional Access requirements.
- Plan Windows Autopilot, Windows 365, and Windows client provisioning.
- Create configuration profiles for Windows and non-Windows platforms.
- Configure endpoint security policies such as antivirus, BitLocker, firewall, ASR, security baselines, and Defender for Endpoint integration.
- Plan and monitor update rings, feature updates, quality updates, Autopatch, and Delivery Optimization.
- Deploy and secure apps using Intune, app protection policies, and app configuration policies.
- Perform safe remote actions and use Microsoft Graph, PowerShell, reports, Endpoint Analytics, and proactive remediations.

## Recommended Course Flow

### Day 1 - Infrastructure, Enrollment, and Compliance

1. Course briefing and MD-102 study guide overview.
2. Lab 01: Tenant Readiness, Microsoft Entra Device Identity, Groups.
3. Lab 02: Intune Enrollment, Platform Profiles, Troubleshooting.
4. Lab 03: Compliance, Conditional Access, Windows Hello, LAPS.
5. Review: device infrastructure and identity-driven management.

### Day 2 - Provisioning, Configuration, Security, and Updates

1. Lab 04: Windows Autopilot, Windows 365, Provisioning.
2. Lab 05: Configuration Profiles, Settings Catalog, Filters.
3. Lab 06: Endpoint Security, Defender, BitLocker, Firewall, ASR.
4. Lab 07: Device Updates, Autopatch, Delivery Optimization.
5. Review: policy targeting, deployment rings, and security baselines.

### Day 3 - Apps, Automation, Reporting, and Capstone

1. Lab 08: App Deployment, App Protection, App Configuration.
2. Lab 09: Remote Actions, Graph, PowerShell, Endpoint Analytics.
3. Lab 10: MD-102 Capstone and Exam Readiness.
4. Cleanup, review plan, and operational checklist.

## Lab Environment Setup

### Step 1 - Confirm Tenant Access

1. Open https://intune.microsoft.com/.
2. Sign in with the lab administrator account.
3. Confirm access to Intune, Microsoft Entra ID, and device management blades.
4. Verify you are not using a production tenant unless explicitly authorized.

### Step 2 - Create Lab Groups

Create planning notes for:

```text
MD102-Windows-Devices
MD102-iOS-Devices
MD102-Android-Devices
MD102-macOS-Devices
MD102-Test-Users
MD102-Pilot-Users
```

Use dynamic groups where your lab tenant supports them.

### Step 3 - Create a Notes File

Create:

```text
md102-lab-notes.md
```

Record:

```text
Tenant:
Admin account:
Test users:
Test devices:
Groups:
Policies:
Apps:
Key learning points:
```

## Safety Guidelines

- Do not wipe, retire, reset, or lock production devices.
- Use test users, test devices, and clearly named lab groups.
- Avoid broad policy assignments such as All users or All devices unless instructed.
- Document every policy target and expected result.
- Disable or delete test policies after class if they are no longer needed.

## Lab Completion Standard

For each lab, learners should complete:

1. Scenario interpretation.
2. Policy or workflow design.
3. Safe implementation or configuration plan.
4. Validation checks.
5. Troubleshooting notes.
6. Cleanup review.
7. One exam-style takeaway.

## Final Exam Readiness Checklist

Before attempting MD-102, confirm that you can:

- Choose device join and enrollment options.
- Configure Intune enrollment restrictions, profiles, and troubleshooting.
- Configure compliance policies and Conditional Access integration.
- Explain Autopilot profiles, deployment modes, ESP, Windows 365 provisioning, and Cloud PCs.
- Create and target configuration profiles using settings catalog, filters, and groups.
- Configure endpoint security, Defender integration, BitLocker, firewall, ASR, and security baselines.
- Deploy apps, Microsoft 365 Apps, app protection policies, and app configuration policies.
- Use reporting, remote actions, Endpoint Analytics, proactive remediations, Graph, and PowerShell.
