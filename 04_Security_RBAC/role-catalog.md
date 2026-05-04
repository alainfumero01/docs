# Role Catalog

## System Admin

Owns platform-level configuration, incident response support, and emergency recovery access. Reads across business modules for support, but is intentionally not a routine finance, HR, or quote approver.

## Finance Admin

Owns finance access design, finance workflow configuration, and finance governance. Can administer finance controls without inheriting full platform administration.

## Finance Manager

Runs finance operations and approvals. Can review and approve finance records, but cannot change platform-wide identity or configuration.

## Finance Analyst

Prepares finance records, sync support, and reporting detail. No approval authority.

## HR Admin

Owns HR access design, HR workflow configuration, and HR governance. Can administer HR controls without inheriting full platform administration.

## HR Manager

Runs HR operations, employee workflow approvals, and compliance review. No platform or identity administration.

## Operations Manager

Owns operational throughput across projects, work orders, and Windfix execution. Can approve operational decisions and Windfix execution transitions.

## Project Manager

Runs day-to-day project delivery. Can manage project-linked work orders and Windfix cases, and can approve case outputs that fall within project execution scope.

## Field Technician

Captures field data, images, materials logs, cure data, and repair evidence. Access is limited to assigned work and self-authored field records.

## Client Portal User

Represents the customer. Can access customer-facing quotes, status, reports, and approvals through the portal, but cannot view internal administrative artifacts.

## Windfix AI Reviewer

Reviews damage detections, repair recommendations, QA artifacts, and standards usage. Can approve or reject AI-driven outputs without administering user identities.

## AI Training Admin

Owns AI training data curation, feedback loops, model-operations metadata, and dataset governance. Does not inherit ERP business approvals.

## Read-Only Auditor

Has read-only access across the environment for audit and assurance. No write, approval, or admin authority.

## IT Admin

Owns identity, integrations, secrets, environment configuration, and operational maintenance. Intentionally separated from business approvals.

## Executive Viewer

Receives read-only portfolio visibility across finance, operations, HR, and Windfix outcomes. No transactional authority.
