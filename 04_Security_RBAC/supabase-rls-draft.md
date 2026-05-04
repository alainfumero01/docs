# Supabase RLS Draft

This document drafts the policy intent for each role. These policies are not implemented yet; they are the blueprint for the SCRUM-6 implementation work.

## Table Groups

### Identity And Governance

- `users`
- `roles`
- `user_roles`
- `audit_log`

### Finance

- `expense_claims`
- `expense_approvals`
- `payroll_runs`
- `payroll_approvals`
- `wire_transfers`
- `wire_authorizations`
- `standing_payments`
- `invoices`
- `quickbooks_sync_log`

### HR

- `employees`
- `leave_requests`
- `leave_approvals`
- `gwo_certifications`

### Operations

- `clients`
- `locations`
- `projects`
- `work_orders`
- `work_order_assignments`

### Windfix AI

- `cases`
- `case_images`
- `damage_detections`
- `repair_recommendations`
- `ai_qa_reports`
- `quotes`
- `quote_line_items`
- `quote_approvals`
- `repair_documentation`
- `repair_images`
- `field_documentation`
- `final_reports`
- `report_signatures`
- `standards_repository`
- `damage_repair_mapping`

## Policy Strategy By Role

### System Admin

- read access across all tables for support and recovery
- write or admin only through tightly limited service functions for identity and platform support
- no broad direct approval policy on finance, HR, or customer quote tables

### Finance Admin

- full read and write across finance tables
- approve on finance approval tables
- read-only access to operations and Windfix context tables needed for reconciliation

### Finance Manager

- read and write to finance working tables
- approve on `expense_approvals`, `payroll_approvals`, `wire_authorizations`, and finance-facing quote approval views where applicable
- no access to identity admin tables

### Finance Analyst

- read and write to finance preparation tables
- no approve policy on finance approval tables
- no access to HR or identity management

### HR Admin

- full read and write across HR tables
- approve on leave and certification workflows
- limited read-only access to operations context needed for staffing

### HR Manager

- read and write to HR tables within approved scope
- approve on leave and selected employee workflow actions
- no identity administration

### Operations Manager

- read and write across operations tables
- approve on operational workflow status transitions
- read and write across Windfix cases tied to operational delivery

### Project Manager

- read and write only for projects, work orders, and linked Windfix cases they own or are assigned to
- approve on quotes and final reports only for linked project scope
- no finance admin access

### Field Technician

- read assigned `work_orders`, `work_order_assignments`, and linked `cases`
- write only to self-authored or assigned evidence tables:
  - `case_images`
  - `repair_documentation`
  - `repair_images`
  - `field_documentation`
- no approve policy

### Client Portal User

- read only client-owned `quotes`, `quote_line_items`, `final_reports`, and approved case status projections
- write limited to portal-side acknowledgements, comments, and customer signatures
- approve only on client quote decisions and customer report sign-off flows

### Windfix AI Reviewer

- read and write to Windfix AI tables
- approve on:
  - `damage_detections`
  - `repair_recommendations`
  - `ai_qa_reports`
  - `quote_approvals` for internal technical review lane
- read access to standards repository

### AI Training Admin

- read and write to AI-training and standards-curation datasets
- approve on model-promotion metadata or training-batch governance records introduced later
- no access to ERP finance or HR workflows beyond read-only reference where required

### Read-Only Auditor

- read-only policies across all table groups
- no write, approve, or admin access
- prefer read access through stable reporting views where possible

### IT Admin

- full identity and operational admin access
- read-only across business data for support diagnostics
- no business approval authority

### Executive Viewer

- read-only to portfolio-level operational, finance, HR, and Windfix reporting surfaces
- prefer view-based access over raw transactional tables where possible

## Recommended Enforcement Patterns

- map authenticated users to a single primary application role through `user_roles`
- use helper functions such as `app_private.current_user_has_role(...)` during SCRUM-6
- scope operational roles by ownership and assignment:
  - project manager by owned `projects`
  - field technician by `work_order_assignments`
  - client portal user by `client_id`
- keep client-facing access on approved and customer-safe tables or views only
- enforce approval permissions separately from write permissions to preserve least privilege
- route executive and auditor access through reporting views where practical to reduce raw-table exposure
