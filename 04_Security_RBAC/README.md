# ONYX-17 RBAC Package

This folder acts as the current home for the Project Onyx RBAC design package referenced by `ONYX-17`.

Contents:

- `permission-matrix.md`
- `role-catalog.md`
- `supabase-rls-draft.md`
- `initial-admin-assignees.md`

## Scope

The RBAC model covers both application domains:

- ERP
- Windfix AI

It is designed around these principles:

- least privilege by default
- no shared roles between users
- business approvals stay with business roles, not platform administrators
- client access is isolated from internal staff access
- Supabase RLS remains the enforcement layer for data access

## Module Set Used In The Matrix

- Platform Administration
- Identity and Role Management
- Finance ERP
- HR ERP
- Operations ERP
- Windfix Case Management
- Standards Repository
- AI Training and Model Operations
- Client Portal
- Reporting and Audit

## Implementation Notes

- The permission matrix is the source of truth for human role design
- The RLS draft translates those permissions into table-group policy intent for later implementation
- Role assignments for named people should remain separate from role definitions so people can change without redefining the access model
