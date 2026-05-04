# Permission Matrix

## Legend

- `R` = read
- `W` = write
- `A` = approve
- `AD` = administer
- blank = no access

Where a cell contains multiple letters, the role has all listed permissions for that module.

## Matrix

| Role | Platform Admin | Identity & Roles | Finance ERP | HR ERP | Operations ERP | Windfix Cases | Standards Repo | AI Training | Client Portal | Reporting & Audit |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| System Admin | R,W,AD | R,W,AD | R | R | R | R | R | R |  | R |
| Finance Admin |  | R | R,W,A,AD | R | R | R |  |  |  | R |
| Finance Manager |  |  | R,W,A |  | R | R |  |  |  | R |
| Finance Analyst |  |  | R,W |  | R |  |  |  |  | R |
| HR Admin |  | R | R | R,W,A,AD | R |  |  |  |  | R |
| HR Manager |  |  | R | R,W,A | R |  |  |  |  | R |
| Operations Manager |  |  | R | R | R,W,A | R,W,A | R |  |  | R |
| Project Manager |  |  | R | R | R,W | R,W,A | R |  |  | R |
| Field Technician |  |  |  | R (self-service only) | R | R,W | R |  |  | R (own submissions only) |
| Client Portal User |  |  |  |  |  | R | R |  | R,W,A | R |
| Windfix AI Reviewer |  |  |  |  | R | R,W,A | R,W | R |  | R |
| AI Training Admin |  |  |  |  |  | R | R,W | R,W,A,AD |  | R |
| Read-Only Auditor | R | R | R | R | R | R | R | R | R | R |
| IT Admin | R,W,AD | R,W,AD | R | R | R | R | R | R |  | R |
| Executive Viewer |  |  | R | R | R | R | R |  | R | R |

## Role Boundaries

### Highest-Privilege Roles

- `System Admin` manages platform settings and emergency operational support, but is intentionally not a default business approver
- `IT Admin` manages identity, integrations, secrets, and operational controls, but does not own business approvals
- `Finance Admin` owns finance policy configuration and finance-role assignment governance
- `HR Admin` owns HR policy configuration and HR-role assignment governance

### Separation Of Duties

- `Finance Analyst` can prepare but not approve finance records
- `Finance Manager` can approve finance records but does not administer platform-level access
- `Project Manager` can drive quote and case progression but is not granted finance admin authority
- `Field Technician` can only create and update evidence or field records tied to assigned work
- `Client Portal User` is isolated to customer-facing objects and cannot administer internal data
- `Windfix AI Reviewer` can approve AI outputs and QA decisions but cannot administer user identities

## Practical Assignment Rules

- one primary business role per user
- additional access granted only where a documented cross-functional need exists
- no shared generic logins
- highest-privilege roles require named assignees and explicit approval from Appia
