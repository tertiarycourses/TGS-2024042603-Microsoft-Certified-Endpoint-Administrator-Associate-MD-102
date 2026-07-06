# Lab 09 - Remote Actions, Graph, PowerShell, Endpoint Analytics

## Objectives

- Identify safe remote actions.
- Plan Graph and PowerShell automation.
- Review device query and KQL concepts.
- Use endpoint analytics and proactive remediation concepts.
- Plan reporting, alerts, and tenant health monitoring.

## Scenario

Operations needs to troubleshoot devices, collect diagnostics, rotate recovery data, and report device health without manual portal work for every task.

## Steps

### 1. Review Remote Actions

Create a safety table:

| Action | Use | Risk |
| --- | --- | --- |
| Sync | Force device check-in | Low |
| Restart | Restart device | User disruption |
| Retire | Remove managed data | Data impact |
| Wipe | Factory reset | Destructive |
| Collect diagnostics | Gather logs | Privacy review |
| Rotate BitLocker key | Reduce exposure | Access control needed |

### 2. Plan Automation

Document:

```text
Task
Graph endpoint or PowerShell cmdlet
Required permission
Approval
Logging
Rollback or safety check
```

### 3. Device Query and KQL

Write example questions:

- Which devices have low disk space?
- Which devices restarted frequently?
- Which devices are missing encryption?
- Which apps have poor startup performance?

### 4. Endpoint Analytics

Review:

- Startup performance.
- App reliability.
- Device health score.
- Proactive insights.
- Proactive remediations.

### 5. Reporting and Alerts

Plan dashboards or alerts for:

- Enrollment failures.
- Compliance drift.
- Configuration conflicts.
- Update failures.
- Endpoint reliability.
- Service health messages.

## Validation

You should have remote action safety table, automation plan, KQL question list, analytics notes, and alert plan.

## Checkpoint Questions

1. Which remote actions are destructive?
2. Why should automation include permissions and logging?
3. What is Endpoint Analytics used for?
4. What are proactive remediations?

## Exam Focus

Operations questions test safe remote actions, automation, Microsoft Graph, reporting, Endpoint Analytics, proactive remediation, and service health.
