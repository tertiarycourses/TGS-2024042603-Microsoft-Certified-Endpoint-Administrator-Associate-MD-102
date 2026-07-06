# Lab 08 - App Deployment, App Protection, App Configuration

## Objectives

- Plan app deployment in Intune.
- Compare Win32, LOB, Microsoft Store, Microsoft 365 Apps, Apple VPP, and Google Play apps.
- Plan app protection and app configuration policies.
- Troubleshoot app installation failures.

## Scenario

The company needs to deploy Microsoft 365 Apps, a Win32 VPN client, mobile apps, and app protection for BYOD users.

## Steps

### 1. Map App Types

| App Need | Intune App Type |
| --- | --- |
| Microsoft 365 Apps | Microsoft 365 Apps deployment |
| Packaged Windows app | Win32 app |
| Internal app installer | Line-of-business app |
| Store app | Microsoft Store app |
| iOS licensed app | Apple Volume Purchase Program |
| Android managed app | Managed Google Play |

### 2. Plan Win32 App Deployment

Document:

```text
Install command
Uninstall command
Detection rule
Requirement rule
Restart behavior
Assignment group
User experience
```

### 3. Plan Microsoft 365 Apps

Record:

- Apps included.
- Update channel.
- Language.
- Autopilot integration.
- Office policies.

### 4. App Protection Policy

Plan:

- Target apps.
- Data transfer restrictions.
- PIN or biometric requirement.
- Conditional Access integration.
- BYOD scope.

### 5. Troubleshoot App Failures

Steps:

1. Check install status.
2. Review device/user assignment.
3. Review detection rules.
4. Review Intune Management Extension logs.
5. Confirm network and prerequisites.

## Validation

You should have app type map, Win32 deployment plan, Microsoft 365 Apps plan, app protection plan, and troubleshooting steps.

## Checkpoint Questions

1. What is a Win32 app in Intune?
2. Why are detection rules important?
3. What does app protection policy protect?
4. How does Conditional Access integrate with app protection?

## Exam Focus

Application questions test deployment type, app protection, app configuration, Microsoft 365 Apps, and troubleshooting.
