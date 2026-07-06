# Lab 05 - Configuration Profiles, Settings Catalog, Filters

## Objectives

- Plan configuration profiles across platforms.
- Use settings catalog concepts.
- Understand ADMX import and Group Policy analytics.
- Use assignment filters and enrollment-time grouping.
- Plan specialty device configuration.

## Scenario

The organization needs baseline settings for Windows, macOS, iOS/iPadOS, Android, Teams Rooms, HoloLens, and Zebra devices.

## Steps

### 1. Choose Profile Types

Create a table:

| Platform | Configuration Need |
| --- | --- |
| Windows | Security and user experience settings |
| macOS | Restrictions and FileVault settings |
| iOS/iPadOS | Wi-Fi, restrictions, and app settings |
| Android | Work profile and device restrictions |
| Teams Rooms | Meeting room device settings |

### 2. Review Settings Catalog

Document:

- Policy name.
- Platform.
- Settings selected.
- Assignment group.
- Expected result.
- Conflict risk.

### 3. Review ADMX and Group Policy Analytics

Explain:

- Why import ADMX files.
- How Group Policy analytics helps migration.
- Which settings should be modernized.

### 4. Plan Assignment Filters

Create examples:

```text
Only Windows 11 devices
Only corporate-owned iOS devices
Exclude shared devices
Target devices with enrollment profile name
```

### 5. Troubleshoot Policy Conflict

Record steps:

1. Check device policy status.
2. Review assignment groups.
3. Review filters.
4. Check setting conflicts.
5. Use troubleshooting blade.

## Validation

You should have platform profile plan, settings catalog notes, ADMX notes, filter examples, and conflict troubleshooting steps.

## Checkpoint Questions

1. What is the settings catalog?
2. Why use assignment filters?
3. What does Group Policy analytics support?
4. How do policy conflicts happen?

## Exam Focus

Configuration questions often test platform profile selection, settings catalog, filters, and troubleshooting.
