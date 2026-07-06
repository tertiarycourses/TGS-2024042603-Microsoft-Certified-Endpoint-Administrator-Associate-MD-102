# Lab 02 - Intune Enrollment, Platform Profiles, Troubleshooting

## Objectives

- Configure enrollment planning for Windows, iOS/iPadOS, Android, and macOS.
- Understand automatic enrollment and platform enrollment profiles.
- Review enrollment restrictions and troubleshooting.
- Plan Apple Business Manager, Android Enterprise, Samsung Knox, and Google Zero Touch integration.

## Scenario

Your organization needs to enroll corporate and personal devices across multiple platforms while blocking unsupported device types.

## Steps

### 1. Review Enrollment Settings

In Intune admin center, review:

```text
Enrollment device platform restrictions
Enrollment device limit restrictions
Automatic enrollment
Enrollment status page
Corporate device identifiers
```

### 2. Plan Windows Enrollment

Document:

- Automatic enrollment requirement.
- User scope.
- Device scope.
- Autopilot use.
- Enrollment Status Page behavior.

### 3. Plan Apple Enrollment

Create a checklist:

```text
Apple MDM push certificate
Apple Business Manager
Enrollment program token
Enrollment profile
User affinity decision
```

### 4. Plan Android Enrollment

Compare:

| Android Mode | Use Case |
| --- | --- |
| Personally owned work profile | BYOD |
| Corporate-owned fully managed | Corporate phone |
| Dedicated device | Kiosk or shared device |
| Corporate-owned work profile | Corporate device with personal use |

### 5. Troubleshoot Enrollment Failure

For each failure, record a likely cause:

1. User not in enrollment scope.
2. Platform blocked.
3. Device limit reached.
4. MDM authority issue.
5. Token or certificate expired.

## Validation

You should have enrollment plans for Windows, Apple, Android, macOS, and a troubleshooting table.

## Checkpoint Questions

1. What is automatic enrollment?
2. What does an enrollment restriction do?
3. Why integrate Apple Business Manager?
4. Which Android mode fits a kiosk device?

## Exam Focus

Know enrollment choices by platform and how to troubleshoot common enrollment failures.
