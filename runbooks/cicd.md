# ONYX-14 CI/CD Runbook

This runbook covers the shared GitHub Actions baseline used across the Project Onyx repositories.

## Repositories

- `erp-web`
- `windfix-web`
- `windfix-mobile`
- `supabase-backend`
- `ai-service`
- `infrastructure`
- `docs`

## Workflows

### CI

Runs on every pull request and push to `main`.

Checks enforced:

- `lint`
- `typecheck`
- `test`
- `build`
- `rollback-smoke-test`

The workflow is bootstrap-aware today. As real application code lands, the workflow expects repository-specific lint, typecheck, test, and build commands to exist. If code is present but those commands are missing, CI fails loudly instead of silently skipping checks.

### Deploy Staging

Triggered automatically after a successful `CI` workflow that ran on a push to `main`.

Behavior:

- checks out the exact merged commit SHA
- runs `STAGING_DEPLOY_COMMAND` from GitHub Secrets when configured
- otherwise records an audited dry run
- uploads a `staging-deploy-log` artifact with retention

### Deploy Production

Triggered manually with:

- `ref`
- `approver_one`
- `approver_two`
- `change_summary`

Approval model:

- creates a GitHub issue for the deployment request
- validates both approvers are collaborators with `write`, `maintain`, or `admin`
- rejects self-approval by the workflow initiator
- requires both named approvers to comment `/approve`
- fails immediately if either named approver comments `/deny`
- closes the approval issue automatically when the workflow completes

This gives a durable, written, auditable approval trail entirely inside GitHub.

### Rollback

Triggered manually with:

- `environment`
- `ref`
- `reason`

Behavior:

- checks out the requested ref
- runs `ROLLBACK_COMMAND` from GitHub Secrets when configured
- otherwise records an audited dry run
- uploads a `rollback-log` artifact with retention

## Secrets

Each repository now expects these GitHub Secrets:

- `STAGING_DEPLOY_COMMAND`
- `PROD_DEPLOY_COMMAND`
- `ROLLBACK_COMMAND`

Placeholders can be used until real deploy automation exists. The important guardrail is that deploy behavior is runtime-injected and not hardcoded in the repository.

## Branch Protection

`main` is protected with:

- pull request review requirement
- required conversation resolution
- required CI status checks
- linear history enforcement
- admin enforcement

## Next Implementation Step Per Repo

When real code is added to a repository, replace the bootstrap detection path with the repository's actual commands so the pipeline executes the real application checks instead of the bootstrap fallback path.
