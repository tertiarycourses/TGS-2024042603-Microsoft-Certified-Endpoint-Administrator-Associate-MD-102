# Lab 01 - Tenant Readiness, Microsoft Entra Device Identity, Groups

## Objectives

- Review tenant readiness for endpoint management.
- Compare device registration and Microsoft Entra join.
- Plan device groups and dynamic membership.
- Review Intune roles, scope tags, and scoped administration.

## Scenario

Your organization is moving to modern endpoint management. You must prepare Microsoft Entra ID groups and administrative boundaries before enrolling devices.

## Steps

### 1. Review Tenant Access

1. Open the Intune admin center.
2. Confirm access to `Devices`, `Apps`, `Endpoint security`, `Reports`, and `Tenant administration`.
3. Open Microsoft Entra admin center.
4. Confirm access to users, groups, and devices.

### 2. Compare Device Identity Options

Create a table:

| Option | Use Case |
| --- | --- |
| Microsoft Entra registered | BYOD or personal device access |
| Microsoft Entra joined | Cloud-managed corporate Windows device |
| Hybrid Microsoft Entra joined | Existing AD-joined device needing cloud management |

### 3. Plan Device Groups

Document:

```text
Windows pilot group
Windows production group
iOS/iPadOS group
Android group
macOS group
High-risk device group
```

Add static or dynamic membership criteria.

### 4. Review Roles and Scope

In your notes, define:

- Intune role.
- Role assignment.
- Scope group.
- Scope tag.
- Multi-admin approval.

### 5. Draw Admin Boundary

Draw how administrators, roles, scope tags, and device groups interact.

## Validation

You should have a device identity comparison, group plan, role/scope notes, and admin boundary diagram.

## Checkpoint Questions

1. When is Microsoft Entra join appropriate?
2. Why use dynamic device groups?
3. What do scope tags help with?
4. Why use multi-admin approval?

## Exam Focus

MD-102 expects you to choose device identity, grouping, role, and scoped administration options for real scenarios.
