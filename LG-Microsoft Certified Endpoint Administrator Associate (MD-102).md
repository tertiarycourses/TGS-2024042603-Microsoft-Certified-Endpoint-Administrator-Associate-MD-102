# Microsoft Certified Endpoint Administrator Associate (MD-102) — Learner Guide

**WSQ Course Code:** TGS-2024042603<br>
**Version:** v3.1 · 25 August 2026<br>
**Duration:** 5 days / 40 hours

## Learning outcomes

- LO1: Administer complex security programs and analyze system-update impacts on Microsoft Endpoint administration.
- LO2: Perform Microsoft Endpoint system administration and configure authentication to protect against security threats.
- LO3: Troubleshoot Microsoft Endpoint security issues and assist users in defining access rights.
- LO4: Coordinate advanced access-control rights and investigate unauthorized-access incidents on Microsoft Endpoint systems.

## Current MD-102 domains

- **Prepare infrastructure for devices (20–25%)** — LO1 · K1 · K4 · A1 · A3
- **Manage and maintain devices (25–30%)** — LO1 · LO2 · K1 · K2 · A2 · A4
- **Protect devices (15–20%)** — LO2 · LO3 · K3 · K4 · A4 · A5 · A6
- **Manage and secure applications (15–20%)** — LO2 · LO3 · K2 · K3 · A2 · A5
- **Optimize endpoint operations (10–15%)** — LO3 · LO4 · K3 · K5 · A5 · A7 · A8

## Prepare infrastructure for devices

### Choose the correct Microsoft Entra device identity

**Mechanism**

1. User sign-in: Primary refresh token
2. Registration service: Device object
3. Join state: Registered · joined · hybrid
4. Token claims: deviceid · trustType
5. Access decision: Identity plus device state

**Exact contract**

- Workplace join: AzureAdRegistered = YES
- Cloud join: AzureAdJoined = YES
- Hybrid join: DomainJoined + AzureAdJoined
- Verification: dsregcmd /status

**Failure and recovery**

- Pending device: Check registration event log
- Wrong tenant: Inspect TenantId and DeviceId
- Missing PRT: Validate WAM and sign-in
- Duplicate object: Reconcile stale registrations

**Verification evidence**

- Device State block: Join flags
- SSO State block: AzureAdPrt = YES
- Entra device record: Owner and trust type
- Sign-in log: Device ID correlation
- Practice bridge: Lab 1

### Target policy with dynamic device groups

**Mechanism**

1. Device inventory: Extension attributes
2. Rule parser: Property operators
3. Membership engine: Asynchronous evaluation
4. Assignment resolver: Include and exclude
5. Policy service: Per-device applicability

**Exact contract**

- OS rule: device.deviceOSType -eq "Windows"
- Ownership rule: device.deviceOwnership -eq "Company"
- Autopilot rule: device.devicePhysicalIDs -any _ -contains "[ZTDId]"
- Preview: Validate rules before save

**Failure and recovery**

- Invalid property: Use supported device schema
- Slow membership: Check processing status
- Nested group assumption: Dynamic groups do not use nested evaluation
- Broad targeting: Test with a preview cohort

**Verification evidence**

- Rule syntax: Saved expression
- Preview result: Expected devices
- Membership audit: Added/removed objects
- Assignment status: Policy reached cohort
- Practice bridge: Lab 1

### Configure Windows automatic enrollment

**Mechanism**

1. Licensed user: Intune entitlement
2. MDM user scope: Enrollment authority
3. Entra join: Discovery URL
4. Enrollment client: Certificate request
5. Intune record: Managed device object

**Exact contract**

- MDM scope: Some or All
- Discovery URL: EnterpriseEnrollment.manage.microsoft.com
- Enrollment status: dsregcmd /status
- Diagnostics: MDMDiagReport.html

**Failure and recovery**

- Scope excludes user: Review MDM user scope
- License missing: Assign Intune entitlement
- Stale enrollment: Inspect scheduled tasks
- Network block: Test enrollment endpoints

**Verification evidence**

- ManagedBy value: Intune
- Enrollment certificate: MS-Organization-Access
- Event log: DeviceManagement-Enterprise-Diagnostics-Provider
- Intune record: Last check-in
- Practice bridge: Lab 2

### Control multi-platform enrollment

**Mechanism**

1. Platform authority: Apple · Google · Samsung
2. Enrollment token: Profile or QR
3. Ownership signal: Corporate or personal
4. Restriction evaluation: Platform + OS limits
5. Managed record: Compliance-capable device

**Exact contract**

- Apple corporate: ABM automated enrollment
- Android corporate: Fully managed or corporate work profile
- Android shared: Dedicated device
- Restriction: Block personal where required

**Failure and recovery**

- Expired token: Renew before service impact
- Wrong ownership: Use corporate identifiers
- Unsupported OS: Check minimum version
- Profile conflict: Verify one intended enrollment path

**Verification evidence**

- Token status: Active and unexpired
- Enrollment profile: Assigned devices
- Ownership field: Corporate
- Platform report: Enrollment success
- Practice bridge: Lab 2

### Delegate Intune administration safely

**Mechanism**

1. Role definition: Permissions
2. Role assignment: Members
3. Scope group: Objects administered
4. Scope tag: Objects visible
5. Audit log: Accountability

**Exact contract**

- Built-in role: Least-privilege baseline
- Custom role: Only required actions
- Scope tag: Regional visibility boundary
- Multi-admin approval: Second-person control

**Failure and recovery**

- Role too broad: Compare actions to task
- Empty scope group: Assignment has no reach
- Tag mismatch: Object not visible
- Approval deadlock: Maintain approver coverage

**Verification evidence**

- Effective permissions: Expected actions only
- Visibility test: Only tagged objects
- Approval record: Requester and approver
- Audit event: Role change trace
- Practice bridge: Lab 1

### Evaluate compliance before access

**Mechanism**

1. Device reports state: Intune check-in
2. Compliance engine: Policy evaluation
3. Entra claim: isCompliant
4. Conditional Access: Grant control
5. Resource token: Allow or block

**Exact contract**

- Grace period: Controlled remediation window
- Mark noncompliant: Immediate or delayed
- CA grant: Require compliant device
- Break-glass: Exclude emergency account

**Failure and recovery**

- Not evaluated: Check assignment and check-in
- False block: Inspect per-setting state
- CA lockout: Use report-only first
- Stale signal: Force sync and reassess

**Verification evidence**

- Per-setting status: Failed condition
- Device compliance: Timestamp
- CA result: Grant control detail
- Sign-in correlation: User + device + policy
- Practice bridge: Lab 3

### Deploy Windows Hello for Business and Windows LAPS

**Mechanism**

1. Identity bootstrap: MFA proof
2. Key provisioning: TPM-backed credential
3. Policy delivery: Cloud Kerberos trust
4. Local admin rotation: LAPS policy
5. Recovery access: Audited retrieval

**Exact contract**

- WHfB trust: Cloud Kerberos trust
- PIN policy: Length and anti-spoofing
- LAPS backup: Microsoft Entra ID
- Rotation: After-use password reset

**Failure and recovery**

- Provisioning blocked: Check tenant and device prerequisites
- TPM unavailable: Review attestation and policy
- Password not backed up: Inspect LAPS event log
- Overprivileged retrieval: Restrict role and audit

**Verification evidence**

- WHfB container: certutil -DeleteHelloContainer for reset
- dsregcmd: NgcSet = YES
- LAPS status: Password backup timestamp
- Audit log: Password retrieval actor
- Practice bridge: Lab 3

### Troubleshoot enrollment as an evidence chain

**Mechanism**

1. User eligibility: License and scope
2. Device eligibility: Platform and ownership
3. Discovery: MDM endpoints
4. Client execution: Enrollment task
5. Service record: Managed device state

**Exact contract**

- Local report: MDMDiagReport.html
- Event channel: Admin + Operational logs
- Service view: Troubleshooting + support
- Network test: Required endpoint reachability

**Failure and recovery**

- 0x80180014: Personal Windows blocked
- 0x80180018: User not authorized
- 0x801c03f3: Device registration problem
- Duplicate serial: Retire stale record

**Verification evidence**

- Error code: Exact HRESULT
- Correlation ID: Service-side trace
- Enrollment log: First failing stage
- Remediation retest: New successful record
- Practice bridge: Lab 2


## Manage and maintain devices

### Select Windows Autopilot or device preparation

**Mechanism**

1. Corporate identity: Hardware hash or preparation policy
2. Profile assignment: Device or user group
3. OOBE contact: Cloud discovery
4. Enrollment: Entra + Intune
5. Provisioning: Apps and policies

**Exact contract**

- Classic Autopilot: Registered corporate devices
- Device preparation: Streamlined cloud-native setup
- User-driven: Named-user productivity
- Self-deploying: Shared or kiosk scenario

**Failure and recovery**

- No profile: Verify assignment state
- Hash mismatch: Re-import correct identity
- Unsupported mode: Check TPM and network
- Policy race: Use readiness reporting

**Verification evidence**

- Deployment profile: Assigned
- Device identity: Registered
- Enrollment report: Phase timings
- Final state: Entra joined and managed
- Practice bridge: Lab 4

### Control Autopilot with ESP and naming

**Mechanism**

1. OOBE: Tenant identification
2. Device setup: Security policies
3. Account setup: User-targeted payload
4. ESP gate: Blocking selection
5. Desktop: Provisioning complete

**Exact contract**

- Name template: Prefix plus serial or random
- Block use: Until required apps install
- Timeout: Controlled failure route
- Tracking: Autopilot deployment report

**Failure and recovery**

- Infinite ESP: Review blocking apps
- Invalid name: Respect 15-character limit
- App dependency: Validate install order
- User reaches desktop early: Correct ESP targeting

**Verification evidence**

- ESP phase: Device or account
- Blocking app: Install status
- Enrollment time: Phase duration
- Device name: Template resolved
- Practice bridge: Lab 4

### Upgrade Windows 11 with deployment rings

**Mechanism**

1. Inventory: Readiness signals
2. Pilot ring: Early adopters
3. Validation: App and driver health
4. Broad rings: Progressive rollout
5. Rollback window: Recovery control

**Exact contract**

- Feature policy: Target Windows release
- Safeguard hold: Respect by default
- Deadline: User experience boundary
- Rollback: Uninstall period

**Failure and recovery**

- Compatibility hold: Inspect safeguard ID
- Low disk: Use readiness report
- Driver failure: Pause affected cohort
- Productivity impact: Roll back within window

**Verification evidence**

- Readiness report: Capable or blocked
- Feature version: Target achieved
- Failure code: Deployment error
- Ring KPI: Success and rollback rate
- Practice bridge: Lab 7

### Provision Windows 365 Cloud PCs

**Mechanism**

1. License: Cloud PC entitlement
2. Provisioning policy: Image + network
3. Group assignment: User scope
4. Provisioning service: Cloud PC creation
5. Management: Intune lifecycle

**Exact contract**

- Join type: Microsoft Entra joined
- Network: Microsoft-hosted or ANC
- Image: Gallery or custom
- Resize/reprovision: Controlled lifecycle action

**Failure and recovery**

- Provisioning failed: Review network and license
- Image validation: Fix generalized image
- Connectivity issue: Check ANC health
- Data loss risk: Understand reprovision impact

**Verification evidence**

- Provisioning state: Succeeded
- Connectivity check: Healthy
- Intune record: Cloud PC managed
- End-user test: Windows 365 connection
- Practice bridge: Lab 4

### Translate GPOs into Settings Catalog policy

**Mechanism**

1. GPO export: XML report
2. Group Policy analytics: Import
3. CSP mapping: Supported settings
4. Policy creation: Settings Catalog
5. Assignment: Cloud-managed cohort

**Exact contract**

- Migration readiness: Supported · deprecated · unknown
- ADMX import: Custom administrative templates
- OMA-URI: Only when catalog lacks setting
- Conflict state: Multiple sources disagree

**Failure and recovery**

- Unsupported setting: Redesign control
- Duplicate config: Remove overlapping profile
- ADMX dependency: Import parent first
- Conflict: Trace per-setting source

**Verification evidence**

- Analytics report: Migration percentage
- Policy JSON: Exact settings
- Per-setting status: Success/conflict/error
- Client MDM report: Applied CSP
- Practice bridge: Lab 5

### Target profiles with filters and enrollment-time grouping

**Mechanism**

1. Base assignment: User or device group
2. Filter query: Device properties
3. Include/exclude: Assignment logic
4. Enrollment-time group: Immediate classification
5. Policy delivery: Resolved applicability

**Exact contract**

- Filter mode: Include or exclude
- Property: manufacturer · model · ownership
- Evaluation: At assignment check
- Enrollment category: Provisioning-time cohort

**Failure and recovery**

- Unsupported property: Use filter schema
- Wrong operator: Test sample values
- User assignment mismatch: Know device filter context
- Race condition: Use enrollment-time grouping

**Verification evidence**

- Filter preview: Expected match
- Assignment status: Filter applied
- Device property: Exact value
- Policy result: Correct cohort only
- Practice bridge: Lab 5

### Apply Intune Suite controls

**Mechanism**

1. Privilege request: User asks elevation
2. EPM policy: Rule evaluation
3. Audit signal: Elevation telemetry
4. Support channel: Remote Help
5. Certificate/network: Cloud PKI or Tunnel

**Exact contract**

- EPM rule: File hash · publisher · path
- Remote Help: RBAC and session consent
- Cloud PKI: Issuing CA + SCEP profile
- Tunnel for MAM: Per-app protected path

**Failure and recovery**

- Elevation denied: Rule mismatch
- Remote Help unavailable: License or RBAC
- Certificate failure: Chain or connector health
- Tunnel offline: Gateway health and routing

**Verification evidence**

- Elevation report: File + user + rule
- Session audit: Helper and sharer
- Certificate profile: Issued identity
- Tunnel report: Connection and gateway
- Practice bridge: Lab 5

### Perform remote actions and live device query

**Mechanism**

1. Operator action: RBAC authorization
2. Intune service: Command queue
3. Device channel: Push or check-in
4. Client execution: Action result
5. Audit/report: Outcome recorded

**Exact contract**

- Retire: Remove company data
- Wipe: Reset device
- Fresh Start: Reinstall Windows
- Device query: KQL against live device data

**Failure and recovery**

- Action pending: Device offline
- Wrong destructive action: Confirm ownership and intent
- Query unavailable: Check supported platform/license
- BitLocker rotation fail: Verify escrow state

**Verification evidence**

- Action status: Pending/succeeded/failed
- Audit actor: Who initiated
- Query result: Named columns and timestamp
- Diagnostics bundle: Collected logs
- Practice bridge: Lab 9

### Diagnose policy conflicts from device evidence

**Mechanism**

1. Assignment: Multiple profiles
2. CSP processing: Local MDM client
3. Per-setting merge: Winner or conflict
4. Reporting: Service aggregation
5. Remediation: Remove overlap

**Exact contract**

- Client report: MDMDiagReport.html
- Policy view: Per-setting status
- Registry path: PolicyManager current values
- Event log: Enterprise-Diagnostics-Provider

**Failure and recovery**

- Conflict: Two profiles set different values
- Not applicable: Platform/edition mismatch
- Error: CSP rejected value
- Pending: No recent device check-in

**Verification evidence**

- Setting name: Exact CSP
- Source profiles: Both assignments
- Client event: Error code
- Retest: Success after consolidation
- Practice bridge: Lab 5


## Protect devices

### Configure Defender Antivirus policy

**Mechanism**

1. Intune policy: Antivirus settings
2. CSP delivery: Defender configuration
3. Engine: Real-time protection
4. Cloud service: Block-at-first-sight
5. Telemetry: Protection status

**Exact contract**

- Cloud protection: Enabled
- Sample submission: Safe samples automatically
- PUA: Block
- Tamper protection: On through security management

**Failure and recovery**

- Setting locked: Tamper protection
- Signature stale: Trigger intelligence update
- Policy conflict: Security policy vs profile
- Sensor unhealthy: Collect Defender diagnostics

**Verification evidence**

- Get-MpComputerStatus: Engine + signature
- Policy report: Applied settings
- Device timeline: Detection evidence
- Security intelligence: Current version
- Practice bridge: Lab 6

### Manage BitLocker encryption and recovery

**Mechanism**

1. Encryption policy: Algorithm and scope
2. TPM protector: Key material
3. Volume encryption: Background state
4. Key escrow: Entra recovery object
5. Rotation: Invalidate exposed key

**Exact contract**

- Silent enablement: Standard user allowed
- Recovery escrow: Before encryption required
- Algorithm: XTS-AES
- Rotation: After key use

**Failure and recovery**

- No escrow: Check device join and permissions
- TPM not ready: Inspect tpm.msc
- Encryption suspended: Resume protectors
- Recovery key exposed: Rotate from Intune

**Verification evidence**

- manage-bde -status: Protection state
- Recovery object: Key ID match
- Encryption report: Compliant volume
- Rotation audit: New key timestamp
- Practice bridge: Lab 6

### Enforce Windows Firewall policy

**Mechanism**

1. Profile detection: Domain/private/public
2. Policy merge: Local + MDM rules
3. Filtering platform: Inbound/outbound decision
4. Logging: Dropped and allowed traffic
5. Report: Firewall state

**Exact contract**

- Default inbound: Block
- Rule scope: Program · port · address
- Local merge: Disable where required
- Log path: pfirewall.log

**Failure and recovery**

- Wrong profile: Inspect active network category
- Overbroad rule: Constrain program and remote address
- Rule conflict: Review policy stores
- No log: Enable successful/dropped logging

**Verification evidence**

- Get-NetFirewallProfile: Enabled state
- Get-NetFirewallRule: Policy source
- Firewall log: Dropped packet
- Intune report: Profile applied
- Practice bridge: Lab 6

### Reduce attack surface with ASR and Zero Trust

**Mechanism**

1. Process behavior: Command or content
2. ASR rule engine: Rule ID evaluation
3. Mode: Audit · warn · block
4. Defender telemetry: Event recorded
5. Operations: Tune exclusions

**Exact contract**

- Phased rollout: Audit then warn then block
- Rule ID: Stable GUID
- Exclusion: Narrow and justified
- Zero Trust: Verify explicitly and limit impact

**Failure and recovery**

- Business app blocked: Use event evidence
- Global exclusion: Replace with per-rule exclusion
- No telemetry: Verify cloud protection
- Rule not active: Check edition and policy precedence

**Verification evidence**

- Event 1121: Blocked action
- Advanced hunting: DeviceEvents
- ASR report: Rule and device
- Exception register: Owner + expiry
- Practice bridge: Lab 6

### Apply security baselines without configuration drift

**Mechanism**

1. Baseline template: Recommended settings
2. Profile instance: Versioned configuration
3. Assignment: Pilot cohort
4. Per-setting report: State
5. Update workflow: Review new template

**Exact contract**

- Baseline version: Immutable template snapshot
- Pilot: Representative devices
- Exception: Documented deviation
- Migration: Create new profile then retire old

**Failure and recovery**

- Conflict: Same setting in another profile
- Template update: Not automatic
- Legacy setting: Unsupported on current OS
- Overhardening: Validate business workload

**Verification evidence**

- Per-setting status: Success/conflict
- Baseline version: Recorded
- Pilot acceptance: Security + productivity
- Exception evidence: Approved control
- Practice bridge: Lab 6

### Integrate Intune with Defender for Endpoint

**Mechanism**

1. Connector: Tenant trust
2. Onboarding policy: Sensor activation
3. Risk signal: Defender device risk
4. Compliance: Risk threshold
5. Conditional Access: Resource gate

**Exact contract**

- Connector status: Active
- EDR policy: Onboard blob
- Risk level: Clear · low · medium · high
- Compliance rule: Require below threshold

**Failure and recovery**

- Device not onboarded: Check Sense service
- Duplicate record: Resolve device identity
- Risk not flowing: Check connector scope
- Access unexpectedly blocked: Inspect CA and risk timeline

**Verification evidence**

- MDE device page: Sensor health
- Intune connector: Last sync
- Compliance detail: Machine risk
- Sign-in result: Risk-based block
- Practice bridge: Lab 6

### Control application execution with App Control

**Mechanism**

1. Policy creation: Allow rules
2. Code integrity: Signature evaluation
3. Execution request: File identity
4. Decision: Allow/audit/block
5. Telemetry: CodeIntegrity events

**Exact contract**

- Base policy: Trusted estate
- Supplemental policy: Scoped extension
- Audit mode: Inventory before enforcement
- Managed installer: Trust tagged deployment source

**Failure and recovery**

- Unsigned business app: Create publisher/file rule
- Policy brick risk: Stage in audit
- Rule too broad: Avoid path trust where writable
- Rollback unavailable: Maintain recovery plan

**Verification evidence**

- CodeIntegrity event: File and signer
- Policy ID: Applied CIPolicy
- Audit inventory: Required exceptions
- Block test: Unauthorized binary denied
- Practice bridge: Lab 6

### Operate update rings, Autopatch and Hotpatch

**Mechanism**

1. Release service: Quality/feature update
2. Deployment service: Target ring
3. Client scan: Applicability
4. Install/restart: Deadline behavior
5. Reporting: Update state

**Exact contract**

- Ring: Deferral + deadline
- Feature policy: Pinned version
- Autopatch: Service-managed rings
- Hotpatch: Eligible baseline + quarterly refresh

**Failure and recovery**

- Offer not received: Check safeguards and policy
- Restart disruption: Tune active hours/deadlines
- Conflicting policies: Consolidate update source
- Hotpatch ineligible: Validate edition and baseline

**Verification evidence**

- Update report: Offer/install state
- Client log: WindowsUpdate.log
- Autopatch status: Release phase
- KPI: Compliance by deadline
- Practice bridge: Lab 7


## Manage and secure applications

### Package and deploy Win32 applications

**Mechanism**

1. Source files: Install payload
2. Content prep tool: .intunewin
3. Service upload: Encrypted package
4. IME download: Device cache
5. Installer: Exit code + detection

**Exact contract**

- Install command: Silent and idempotent
- Detection: MSI · file · registry · script
- Requirements: Architecture and OS
- Return codes: Success · retry · reboot

**Failure and recovery**

- 0x87D30067: Detection failed after install
- 0x80070002: File or path missing
- Installer context: System vs user mismatch
- Reboot loop: Map return codes correctly

**Verification evidence**

- IME log: IntuneManagementExtension.log
- Detection output: Installed state
- App report: Device install status
- Exit code: Mapped result
- Practice bridge: Lab 8

### Sequence apps with dependencies and supersedence

**Mechanism**

1. Assignment: Required/available/uninstall
2. Dependency graph: Prerequisites
3. Install order: Topological sequence
4. Supersedence: Update or replace
5. Detection: Final state

**Exact contract**

- Dependency: Auto-install prerequisite
- Supersedence: Update or uninstall previous
- Requirement: Gate by device state
- Availability: Company Portal intent

**Failure and recovery**

- Cycle: Remove circular dependency
- Wrong uninstall: Test supersedence option
- Detection overlap: Use version-aware rule
- Assignment conflict: Resolve required vs uninstall

**Verification evidence**

- Dependency graph: Expected sequence
- IME log: Install orchestration
- App version: New build detected
- Report: No stale required failure
- Practice bridge: Lab 8

### Deploy Microsoft 365 Apps

**Mechanism**

1. Configuration: Apps and channel
2. Content source: Office CDN
3. Click-to-Run: Streaming install
4. Policy service: Cloud policy
5. Inventory: Version and channel

**Exact contract**

- Update channel: Current Enterprise or selected channel
- Architecture: 64-bit by default
- ODT XML: Product · language · updates
- Policy priority: Cloud policy vs local

**Failure and recovery**

- Channel mismatch: Review CDNBaseUrl
- Office apps open: Handle update deadline
- Network optimization: Use Delivery Optimization
- Policy conflict: Inspect cloud policy status

**Verification evidence**

- OfficeC2RClient: Version/channel
- Intune app status: Installed
- Apps admin center: Inventory
- Policy report: Applied Office settings
- Practice bridge: Lab 8

### Integrate Apple and Managed Google Play stores

**Mechanism**

1. Store tenant link: ABM or Managed Google Play
2. App acquisition: Token/sync
3. Assignment: User/device/license
4. Managed install: Platform service
5. Inventory: Install status

**Exact contract**

- Apple VPP token: Location-specific and renewable
- Managed Google Play: Enterprise bind
- App type: Managed store app
- Licensing: Device or user where supported

**Failure and recovery**

- Token expired: Renew with same account
- App not synced: Force connector sync
- License exhausted: Acquire more licenses
- Wrong storefront: Verify tenant binding

**Verification evidence**

- Connector health: Last successful sync
- App record: Current metadata
- License count: Assigned/available
- Device report: Managed install
- Practice bridge: Lab 8

### Protect corporate data with MAM

**Mechanism**

1. App launch: User signs in
2. SDK/wrapper: Policy acquisition
3. Data boundary: Work identity context
4. Action evaluation: Save/copy/open-in
5. Selective wipe: Corporate data removed

**Exact contract**

- Data transfer: Policy-managed apps only
- Encryption: Organizational data
- Access requirement: PIN + threat condition
- Wipe: User or device scoped

**Failure and recovery**

- App not protected: Unsupported app or wrong identity
- Policy not applied: Check user assignment and license
- Copy blocked unexpectedly: Review exempt apps
- Wipe pending: App must check in

**Verification evidence**

- App protection status: User + app + device
- Policy diagnostics: Applied settings
- Selective wipe report: Completed
- CA result: Require app protection
- Practice bridge: Lab 8

### Combine app protection with Conditional Access

**Mechanism**

1. Sign-in: User + app
2. CA conditions: Platform/client/risk
3. Grant control: Require approved app or APP
4. App policy: Data controls
5. Token: Protected session

**Exact contract**

- Grant: Require app protection policy
- Client apps: Mobile apps and desktop clients
- Report-only: Validate before enforce
- Exclusion: Emergency access accounts

**Failure and recovery**

- Unsupported client: Block or constrain
- Policy gap: CA grants access without APP
- Lockout: Use report-only and exclusions
- Legacy auth: Block separately

**Verification evidence**

- Sign-in log: CA policy result
- APP report: Policy delivered
- Token claim: Client/app context
- Test matrix: Managed/unmanaged × platform
- Practice bridge: Lab 8

### Deliver app configuration to managed and unmanaged apps

**Mechanism**

1. Configuration source: Intune key-value payload
2. Assignment: User or device
3. Delivery channel: MDM or MAM
4. App reads keys: Runtime behavior
5. Reporting: Configuration status

**Exact contract**

- Managed device: Configuration through MDM
- Managed app: Configuration through APP channel
- Data type: String · boolean · integer
- Vendor schema: Exact supported keys

**Failure and recovery**

- Key ignored: Wrong name or type
- Wrong channel: Managed app vs managed device
- Conflicting values: Consolidate policies
- No report: Verify app supports reporting

**Verification evidence**

- Policy payload: Exact keys
- App diagnostics: Received configuration
- Device report: Success
- Behavior test: Expected tenant/account state
- Practice bridge: Lab 8

### Troubleshoot application deployment from logs

**Mechanism**

1. Assignment resolution: Intent
2. IME policy sync: App metadata
3. Content download: DO/BITS
4. Installer execution: Context
5. Detection: Reported state

**Exact contract**

- IME log: IntuneManagementExtension.log
- Agent Executor: PowerShell execution
- Content cache: Staging files
- Portal report: Device install details

**Failure and recovery**

- Download timeout: Network/proxy/DO
- Install failure: Exit code and command
- Detection false negative: Fix rule
- Requirement not met: Inspect applicability

**Verification evidence**

- Timestamp chain: First failing phase
- Exit code: Vendor meaning
- Detection trace: Rule output
- Retest: Successful device status
- Practice bridge: Lab 8

### Manage app lifecycle and inventory

**Mechanism**

1. Discovery: Managed app inventory
2. Classification: Owner + criticality
3. Deployment: Install intent
4. Update: Supersedence/store update
5. Retirement: Uninstall and revoke

**Exact contract**

- Owner: Named service owner
- Detection: Version-aware
- Update SLA: Risk-based deadline
- Retirement: Data and access cleanup

**Failure and recovery**

- Shadow IT: Compare discovered vs approved
- Stale package: Monitor version drift
- Uninstall fails: Validate command/context
- Orphan assignment: Review group lifecycle

**Verification evidence**

- Discovered apps: Version footprint
- Install base: Device/user count
- Update compliance: Current version %
- Retirement proof: No active assignment
- Practice bridge: Lab 8


## Optimize endpoint operations

### Automate Intune with Microsoft Graph

**Mechanism**

1. Identity: App or delegated sign-in
2. OAuth token: Scope/role claims
3. Graph endpoint: Resource request
4. Pagination: @odata.nextLink
5. Result handling: Retry and audit

**Exact contract**

- Base URI: https://graph.microsoft.com/v1.0
- Permission: DeviceManagementManagedDevices.Read.All
- Pagination: Follow every nextLink
- Throttling: Honor Retry-After

**Failure and recovery**

- 401: Token missing/expired
- 403: Permission or role absent
- 429: Back off and retry
- Partial export: Pagination ignored

**Verification evidence**

- Token claims: aud + roles/scp
- HTTP trace: Status + request-id
- Count check: All pages retrieved
- Audit log: Automation identity
- Practice bridge: Lab 9

### Use PowerShell for repeatable endpoint operations

**Mechanism**

1. Connect-MgGraph: Authentication
2. Select-MgProfile: API surface
3. Get cmdlet: Read state
4. Update cmdlet: Controlled mutation
5. Export/log: Evidence and rollback

**Exact contract**

- Context: Get-MgContext
- Least privilege: Explicit scopes
- WhatIf pattern: Preview intended targets
- Idempotence: Compare before update

**Failure and recovery**

- Wrong tenant: Check TenantId
- Broad filter: Count before mutate
- Module drift: Pin/test version
- Transient failure: Retry safe operations

**Verification evidence**

- Transcript: Command and time
- Before/after JSON: Changed fields
- Target count: Expected devices
- Exit status: Automation result
- Practice bridge: Lab 9

### Extend compliance with custom scripts

**Mechanism**

1. Discovery script: Return JSON
2. Custom schema: Setting definitions
3. Compliance engine: Compare values
4. Device status: Per-setting result
5. Remediation: Operational response

**Exact contract**

- Exit code: 0 for successful discovery
- Output: Single compressed JSON object
- Data types: Match schema
- Schedule: Periodic reevaluation

**Failure and recovery**

- Invalid JSON: Validate serialization
- Wrong property type: Match boolean/int/string
- Script timeout: Keep discovery bounded
- Sensitive data: Do not emit secrets

**Verification evidence**

- Local script output: Valid JSON
- Per-setting report: Detected value
- Compliance state: Expected result
- Remediation ticket: Closed with proof
- Practice bridge: Lab 9

### Operate Security Copilot agents responsibly

**Mechanism**

1. Signal intake: Threat/performance data
2. Agent analysis: Pattern and context
3. Recommendation: Suggested action
4. Human review: Validate scope and evidence
5. Execution: Controlled remediation

**Exact contract**

- Grounding: Tenant telemetry
- Recommendation: Not automatic authority
- Review: Check affected devices and blast radius
- Audit: Record decision and outcome

**Failure and recovery**

- Hallucinated cause: Verify against raw evidence
- Overbroad action: Pilot and approve
- Sensitive prompt: Apply data governance
- Agent unavailable: Maintain manual runbook

**Verification evidence**

- Source evidence: Linked telemetry
- Reviewer decision: Accept/modify/reject
- Change record: Approved scope
- Outcome metric: Issue resolved without regression
- Practice bridge: Lab 10

### Build operational reports and dashboards

**Mechanism**

1. Service data: Device/app/policy facts
2. Report query: Filters and columns
3. Export/API: Structured data
4. Workbook/dashboard: Operational view
5. Decision: Action and owner

**Exact contract**

- Freshness: Record report timestamp
- Filter: Define cohort explicitly
- Export: CSV or Graph
- KPI: Numerator, denominator, threshold

**Failure and recovery**

- Misleading denominator: Exclude not-applicable correctly
- Stale export: Display freshness
- Duplicate devices: Use stable device ID
- Vanity metric: Tie KPI to action

**Verification evidence**

- Query definition: Reproducible filter
- Dashboard tile: Current value
- Drill-through: Affected devices
- Action log: Owner and deadline
- Practice bridge: Lab 9

### Interpret Endpoint Analytics and reliability

**Mechanism**

1. Device telemetry: Startup/app/restart events
2. Aggregation: Population metrics
3. Scoring: Startup + application reliability
4. Insight: Outlier or regression
5. Action: Hardware/policy/remediation

**Exact contract**

- Startup score: Boot + sign-in experience
- App reliability: Crashes and hangs
- Restart frequency: Operational stability
- Baseline: Compare cohort and time

**Failure and recovery**

- Low sample: Avoid overinterpreting
- Cohort mix: Segment by model/OS
- Score improved but tickets rise: Use multiple signals
- Telemetry gap: Check prerequisites

**Verification evidence**

- Score trend: Before/after
- Model cohort: Outlier devices
- App report: Top regressions
- Validation: Reduced incident rate
- Practice bridge: Lab 9

### Deploy proactive remediations safely

**Mechanism**

1. Detection script: Exit 0/1
2. Service evaluation: Issue found
3. Remediation script: Correct state
4. Post-detection: Verify fix
5. Reporting: Run outcome

**Exact contract**

- Detection: No change, evidence only
- Remediation: Idempotent and bounded
- Execution: System or user context
- Schedule: Operational need

**Failure and recovery**

- Detection always fails: Fix exit logic
- Remediation loops: Make desired state idempotent
- 32/64-bit mismatch: Choose host setting
- Large blast radius: Pilot and stage

**Verification evidence**

- Pre-state: Issue reproduced
- Detection result: Issue found
- Remediation log: Change made
- Post-state: Issue absent
- Practice bridge: Lab 9

### Monitor tenant health, alerts and change

**Mechanism**

1. Service signal: Health/message center
2. Operational baseline: Expected rate
3. Alert rule: Threshold or event
4. Triage: Impact and ownership
5. Response: Communicate and recover

**Exact contract**

- Enrollment alert: Failure-rate threshold
- Compliance drift: Noncompliant percentage
- Config conflict: New conflict count
- Service advisory: Affected workload and region

**Failure and recovery**

- Alert fatigue: Tune severity and routing
- No baseline: Measure normal first
- Duplicate incident: Correlate service advisory
- Unowned action: Use escalation matrix

**Verification evidence**

- Alert payload: Cohort + timestamp
- Incident timeline: Detection to recovery
- Change correlation: Policy/deployment event
- Postmortem: Control improvement
- Practice bridge: Lab 10

### Investigate unauthorized endpoint access

**Mechanism**

1. Detection: Risk/sign-in/device alert
2. Scope: User + device + app
3. Containment: Disable/revoke/isolate
4. Evidence: Logs and timeline
5. Recovery: Restore and monitor

**Exact contract**

- Identity action: Revoke sessions
- Device action: Isolate or retire
- Evidence handling: Preserve timestamps and IDs
- Access review: Remove excess privilege

**Failure and recovery**

- Premature wipe: Preserve evidence first
- Incomplete scope: Correlate device and sign-in IDs
- Credential persists: Reset and revoke tokens
- Access restored early: Require clean compliance

**Verification evidence**

- Incident timeline: Ordered events
- Sign-in log: CA and device details
- Device timeline: Alert/process activity
- Closure proof: Risk cleared and access reviewed
- Practice bridge: Lab 10


## Detailed labs

### Lab 1: Entra device identity, dynamic groups and delegated administration

Duration: 110 minutes. Alignment: LO1 · K1 · K4 · A1 · A3.

Deliverable: Validated join-state evidence pack, dynamic-group rule, scoped role assignment and audit trace

#### Establish tenant and role boundaries

1. Sign in to the Microsoft Entra admin center with the lab administrator role supplied by the trainer.
2. Record the tenant ID and confirm you are in the training tenant, not a production tenant.
3. Open Identity > Devices > All devices and record the current device count.
4. Open Devices > Device settings and document join and local-administrator controls before changing them.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Validate a device identity

1. On the Windows test device, open Windows Terminal as administrator.
2. Run `dsregcmd /status` and save the Device State, Device Details and SSO State blocks.
3. Correlate DeviceId and TenantId with the Entra device object.
4. Classify the device as registered, Entra joined or hybrid joined and justify the classification from flags.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Create a dynamic targeting rule

1. Open Entra ID > Groups > New group and select Security with Dynamic Device membership.
2. Create a rule for corporate Windows devices, preview the result, then save only after the expected test device appears.
3. Record the exact rule and preview result in the evidence folder.
4. Assign a descriptive owner and purpose to the group.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Delegate and verify

1. Create or inspect an Intune role assignment with a narrow scope group and scope tag.
2. Use a test operator account to verify visibility is restricted to intended objects.
3. Review the audit log for the role/group changes.
4. Revoke the temporary test assignment if instructed and capture the final state.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 2: Multi-platform Intune enrollment and troubleshooting

Duration: 115 minutes. Alignment: LO1 · K1 · K3 · A1 · A3.

Deliverable: Enrollment configuration matrix, MDMDiag evidence, error-code diagnosis and successful retest

#### Plan enrollment

1. Build a platform matrix for Windows, macOS, iOS/iPadOS and Android corporate/personal ownership.
2. Record the intended enrollment method, authority connector, license and user scope for each platform.
3. In Intune, review Devices > Enrollment and record token/connector health.
4. Review enrollment restrictions and identify which personal platforms are allowed or blocked.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Configure the Windows path

1. Verify MDM user scope includes the lab user.
2. Verify the user has the required Intune entitlement.
3. Join or register the Windows test device according to the lab scenario.
4. Trigger Settings > Accounts > Access work or school > Info > Sync.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Collect diagnostics

1. Run `mdmdiagnosticstool.exe -area DeviceEnrollment;DeviceProvisioning;Autopilot -cab evidence\MDMDiagnostics.cab`.
2. Open Event Viewer > DeviceManagement-Enterprise-Diagnostics-Provider > Admin.
3. Record the first error code or successful enrollment event and its timestamp.
4. Use Intune Troubleshooting + support to correlate the user and managed-device record.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Seed and recover

1. Apply the trainer-provided restriction or scope mismatch that blocks enrollment.
2. Reproduce the failure and record the exact HRESULT/correlation ID.
3. Correct only the failed prerequisite, then retry enrollment.
4. Capture the successful managed record, ownership, primary user and last check-in.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 3: Compliance, Conditional Access, Windows Hello and LAPS

Duration: 115 minutes. Alignment: LO2 · K3 · K4 · A4 · A6.

Deliverable: Compliance/CA decision trace, WHfB state and auditable LAPS recovery/rotation evidence

#### Create compliance policy

1. In Intune, create a Windows compliance policy requiring encryption, firewall and the trainer-specified OS version.
2. Set a short training grace period and assign only to the lab device group.
3. Record every configured setting and the noncompliance action.
4. Sync the device and inspect per-setting compliance.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Create Conditional Access safely

1. In Entra Conditional Access, create a policy requiring a compliant device for the lab cloud app.
2. Exclude the designated emergency-access account.
3. Start in report-only mode and run the What If tool for compliant and noncompliant scenarios.
4. Enable only when the trainer confirms the report-only results are correct.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Validate WHfB and LAPS

1. Assign the Windows Hello for Business policy and record the selected trust model.
2. On the device, run `dsregcmd /status` and verify the expected NGC/PRT state.
3. Assign the Windows LAPS policy to back up passwords to Entra ID.
4. Verify the password backup timestamp and retrieve it only with the authorized role.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Diagnose and prove recovery

1. Seed one compliance or access mismatch.
2. Use the device compliance details and sign-in log to locate the failed condition.
3. Correct the policy/assignment, sync, and rerun the sign-in test.
4. Rotate the LAPS password after access and capture the audit event.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 4: Autopilot, device preparation and Windows 365 provisioning

Duration: 115 minutes. Alignment: LO1 · LO4 · K1 · K5 · A2 · A7.

Deliverable: Deployment decision, profile/ESP design, readiness evidence and Cloud PC provisioning check

#### Choose deployment architecture

1. Compare classic Autopilot and Windows Autopilot device preparation against the lab constraints.
2. Choose user-driven, pre-provisioning or self-deploying mode and document prerequisites.
3. Define the Entra join type and device ownership state.
4. Create a rollback path that does not depend on user access.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Configure identity and profile

1. Create/import the lab device identity or configure the device preparation policy.
2. Assign the intended deployment profile to the test cohort.
3. Configure a valid device-name template.
4. Confirm the service shows the profile as assigned before starting OOBE.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Control provisioning

1. Create an Enrollment Status Page that blocks only the required security and application payload.
2. Record timeout and failure behavior.
3. Run the deployment on the approved test device or use the training simulation data.
4. Capture phase duration, blocking app status and final join/management state.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Extend to Windows 365

1. Create or inspect a provisioning policy with the selected image, join type and network.
2. Validate the Azure network connection or Microsoft-hosted network choice.
3. Assign the policy to the training user group.
4. Capture the Cloud PC provisioning state and Intune managed-device record.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 5: Settings Catalog, ADMX migration and assignment filters

Duration: 110 minutes. Alignment: LO2 · K2 · K4 · A2 · A4.

Deliverable: Migrated settings policy, filter preview, conflict diagnosis and corrected per-setting result

#### Analyze legacy policy

1. Export the trainer-provided GPO report as XML.
2. Import it into Group Policy analytics and record supported, deprecated and unknown settings.
3. Select only supported controls required by the scenario.
4. Record redesign decisions for unsupported settings.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Create cloud policy

1. Build a Settings Catalog profile with the selected controls.
2. Import the required ADMX only if the setting is absent from the catalog.
3. Assign the policy to a pilot group.
4. Create an assignment filter using an exact supported device property.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Seed a conflict

1. Assign a second training profile that sets one control differently.
2. Sync the device and reproduce the per-setting conflict.
3. Collect the policy report, MDMDiag output and relevant MDM event.
4. Identify both source profiles before changing either.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Consolidate and verify

1. Choose the authoritative profile and remove the overlapping setting from the other profile.
2. Sync the device and wait for the service report to refresh.
3. Verify the per-setting state is successful and the client value matches.
4. Save the final policy export and filter preview as evidence.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 6: Endpoint security, Defender, BitLocker, firewall and ASR

Duration: 120 minutes. Alignment: LO2 · LO3 · K3 · K4 · A4 · A5 · A6.

Deliverable: Security control set with Defender/BitLocker/firewall/ASR verification and exception record

#### Design the control set

1. Define Defender Antivirus, BitLocker, Firewall and ASR requirements for the lab device group.
2. Map each requirement to an Intune Endpoint security policy surface.
3. Identify where a security baseline overlaps and remove duplicate ownership.
4. Record the rollout mode for every ASR rule: audit, warn or block.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Deploy and inspect

1. Create and assign the approved endpoint-security policies to the pilot cohort.
2. Sync the test device.
3. Run `Get-MpComputerStatus`, `manage-bde -status` and `Get-NetFirewallProfile`.
4. Capture Intune per-setting status and Defender onboarding/sensor health.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Generate evidence

1. Run the trainer-approved benign ASR test or inspect provided event data.
2. Open the CodeIntegrity/Defender/Firewall evidence channels specified by the trainer.
3. Correlate device ID, policy name, event ID and timestamp.
4. Record the control that produced each observed outcome.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Tune safely

1. Seed an allowed business-app exception scenario.
2. Replace any broad global exclusion with the narrowest supported per-rule exception.
3. Retest the application and the control.
4. Create an exception record with owner, rationale, expiry and compensating control.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 7: Update rings, feature updates, Autopatch, Hotpatch and Delivery Optimization

Duration: 110 minutes. Alignment: LO1 · LO2 · K1 · K2 · A2 · A5.

Deliverable: Staged update design, eligibility checks, rollout metrics and rollback decision evidence

#### Design staged rollout

1. Create pilot, early adopter and broad deployment cohorts.
2. Define quality-update deferral, deadline, grace period and restart experience per ring.
3. Create a feature update policy for the target Windows release.
4. Record rollback and pause decision thresholds.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Evaluate service options

1. Compare self-managed update rings with Windows Autopatch for the scenario.
2. Check Hotpatch edition, baseline and service prerequisites.
3. Configure Delivery Optimization group or connected-cache behavior for the lab network.
4. Document non-Windows update controls for macOS/iOS or Android where relevant.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Analyze update evidence

1. Open the Intune Windows update report and filter to the lab cohort.
2. Record offer, download, install, restart and error states.
3. On the device, generate WindowsUpdate.log or inspect the provided log sample.
4. Identify any safeguard hold, eligibility block or policy conflict.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Decide and verify

1. Apply the trainer-provided update failure scenario.
2. Choose pause, expedite, rollback or targeted remediation based on evidence.
3. Implement the approved action in the training tenant.
4. Capture the post-action compliance rate and affected-device list.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 8: Win32 apps, Microsoft 365 Apps, MAM and app configuration

Duration: 120 minutes. Alignment: LO2 · LO3 · K2 · K3 · A2 · A5.

Deliverable: Deployable app contract, detection evidence, MAM/CA test matrix and troubleshooting trace

#### Build a Win32 app contract

1. Package the trainer-provided source with the Intune Win32 Content Prep Tool or inspect the supplied `.intunewin` metadata.
2. Define silent install and uninstall commands with the correct context.
3. Create version-aware detection and explicit requirement rules.
4. Map vendor exit codes to success, retry, soft reboot and hard reboot.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Deploy and sequence

1. Upload/create the app in Intune and assign it to the pilot group.
2. Configure the supplied prerequisite as a dependency.
3. Configure supersedence for the previous version without creating a cycle.
4. Trigger device sync and monitor install status.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Protect app data

1. Create an app protection policy for the supported mobile app.
2. Set work-data transfer, encryption, access and selective-wipe controls.
3. Create a Conditional Access policy requiring app protection in report-only mode.
4. Test managed and unmanaged device/app combinations using the evidence matrix.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Troubleshoot and close

1. Seed a detection or requirement-rule failure.
2. Inspect IntuneManagementExtension.log and the per-device install details.
3. Correct the smallest failing contract element and retry.
4. Capture installed version, detection success and app-protection status.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 9: Graph, PowerShell, remote actions and Endpoint Analytics

Duration: 115 minutes. Alignment: LO3 · LO4 · K3 · K5 · A5 · A7.

Deliverable: Least-privilege automation transcript, paginated export, remote-action evidence and KPI readout

#### Authenticate with least privilege

1. Open PowerShell 7 and connect with `Connect-MgGraph` using only the lab read scopes.
2. Run `Get-MgContext` and verify TenantId, Account and Scopes.
3. Record the Graph `v1.0` endpoint and selected resource.
4. Do not request write permissions until the trainer authorizes the change task.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Export all managed devices

1. Request the managedDevices collection with selected fields.
2. Follow every `@odata.nextLink` until no next page remains.
3. Export device ID, name, OS, compliance and last-sync values to CSV.
4. Compare the exported count with the service report.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Perform a controlled action

1. Resolve one lab device by stable device ID.
2. Preview the intended action and confirm ownership.
3. Run the approved sync or rotate-key action.
4. Capture the audit actor, time and resulting status.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Interpret analytics

1. Open Endpoint Analytics and record the current startup, application reliability and restart signals.
2. Segment by the trainer-provided device model or OS cohort.
3. Identify one outlier and propose a bounded proactive remediation.
4. Define the before/after metric that will prove improvement.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

### Lab 10: Capstone: investigate access, remediate endpoints and brief operations

Duration: 110 minutes. Alignment: LO4 · K5 · A7 · A8.

Deliverable: Incident timeline, containment record, remediation proof, access review and executive operations brief

#### Triage unauthorized access

1. Review the supplied sign-in, Conditional Access, device risk and endpoint timeline evidence.
2. Correlate user ID, device ID, app, IP, policy and timestamps.
3. Build an ordered incident timeline.
4. State the scope and confidence level before containment.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Contain and preserve evidence

1. Revoke user sessions and isolate/retire only the device authorized by the scenario.
2. Preserve relevant logs, request/correlation IDs and screenshots before destructive actions.
3. Remove or suspend excessive access rights.
4. Record every containment action, actor and time.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Remediate operations

1. Use the supplied detection script to confirm the endpoint issue.
2. Run the approved idempotent remediation on the pilot device.
3. Perform a post-detection or direct state check.
4. Restore access only after identity risk, device health and compliance are acceptable.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.

#### Brief and close

1. Create a concise operations brief: impact, root cause, control failure, actions and remaining risk.
2. Attach the evidence index and access-review result.
3. Define a tenant-health alert or operational baseline that would detect recurrence sooner.
4. Obtain trainer sign-off on A7/A8 evidence.

Acceptance check: capture configured state, observed result, timestamp/correlation ID and interpretation.


## Sources

- Certification: https://learn.microsoft.com/en-us/credentials/certifications/modern-desktop/
- Study Guide: https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/md-102
- Course: https://learn.microsoft.com/en-us/training/courses/md-102t00
- Labs: https://github.com/MicrosoftLearning/MD-102T00-Microsoft-365-Endpoint-Administrator
- Lab Commit: 25eaad2a79548c4767ea45eae8d08649622c583a
