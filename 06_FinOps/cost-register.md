# Project Onyx Cost Register

Last verified: `2026-05-04`

This register tracks known and likely costs based on the current Project Onyx setup.

## Current Baseline

| Vendor | Item | Current Status | Pricing Basis | Estimated Monthly Cost | Notes |
| --- | --- | --- | --- | --- | --- |
| Supabase | Pro organization plan | Active | `$25/month` fixed plan fee | `$25.00` | Official Supabase usage examples show the Pro plan at `$25` per month. |
| Supabase | Production project compute | Active | Micro compute is `$10/month`, offset by included compute credits on the Pro plan example | `$0 incremental` | For a single Micro production project, Supabase's billing examples net out to `$25 total` after the included compute credits. |
| Supabase | Persistent `dev` branch | Active | Preview branch compute starts at `$0.01344/hour` | `~$10.00` | If left running continuously, a Micro branch is about `$10/month`. Compute credits do not apply to branching compute. |
| Supabase | Persistent `staging` branch | Active | Preview branch compute starts at `$0.01344/hour` | `~$10.00` | Same basis as `dev`. Persistent branches remain active until deleted or changed. |
| Roboflow | Workspace / project foundation | Active | Plan not exposed by API; official Core pricing is `$99/month` billed monthly or `$79/month` billed annually | `Unknown live bill` | Workspace `project-onyx` and project `blade-damage-detection` are live. Billing must be confirmed in Roboflow `Plan & Billing` to know whether this is still the 14-day Premium Trial or a paid Core plan. |
| GitHub | Personal-account public repos | Active | GitHub Free for personal accounts | `$0.00` | Current Onyx repos are running on public repositories under a personal account. |

## Current Likely Baseline Total

### Known Active Baseline

- Supabase known baseline: about `$45/month`

Formula used:

- Pro plan: `$25/month`
- persistent `dev` branch: about `$10/month`
- persistent `staging` branch: about `$10/month`

### Pending Billing Confirmation

- Roboflow live workspace billing: `unknown until confirmed in Plan & Billing`

## Optional Or Future Costs

| Vendor | Item | Pricing Basis | When It Applies | Notes |
| --- | --- | --- | --- | --- |
| Roboflow | Core plan | `$99/month` billed monthly or `$79/month` billed annually | If the workspace is moved from trial to paid Core | Core is the first paid plan with private data and models on the public pricing page. |
| Roboflow | Additional user seats on Core | `$29/user/month` | If the workspace exceeds the included 3 users on Core | Useful once Appia and AIDA annotators are added. |
| Roboflow | Outsourced labeling services | Starting at `$0.10/bounding box`, `$0.20/polygon`, `$0.05/classification/keypoint` | Only if purchased | Not a current cost. |
| GitHub | Team plan | `$4/user/month` | Only if repos move into a GitHub organization on Team | Could make repo administration cleaner later, but not needed for the current public-repo setup. |
| OpenAI API | Model usage | Usage-based | Only when Onyx app or AI services start making production API calls | Pricing depends on chosen model and volume. |
| OpenAI API | Web search tool | `$10/1k calls` | Only if production workflows use OpenAI web search | Not a current project cost. |

## Usage-Based Watch List

### Supabase

These are included up to quota on Pro, then billed as overage:

- Egress: `250 GB included`, then `$0.09/GB`
- Database size: `8 GB per project included`, then `$0.125/GB`
- Storage: `100 GB included`, then `$0.021/GB`
- Edge Functions: `2 million included`, then `$2/million`
- Realtime messages: `5 million included`, then `$2.5/million`
- Realtime peak connections: `500 included`, then `$10 per 1000`
- Monthly active users: `100,000 included`, then `$0.00325/MAU`

### Roboflow

Watch these before scaling:

- whether the workspace remains on trial or converts to Core
- number of user seats once Appia and AIDA members are invited
- dataset growth and credit usage for labeling, training, and deployment

### GitHub

Current repos are public, so GitHub-hosted runner minutes for public repos are generally not the main cost risk.

Future watch items:

- Codespaces usage
- Git LFS usage
- any move to Team or Enterprise

## Current Project-Specific Notes

- Supabase production project ref: `nmznikhucgedekfjajmp`
- Supabase persistent branches:
  - `dev` `qentzpnjewwlzitrigsu`
  - `staging` `pwmgdefeqteqcsemhycv`
- Roboflow workspace id: `project-onyx`
- Roboflow project id: `project-onyx/blade-damage-detection`
- Roboflow dataset version: `v1-baseline` version `1`

## Source Links

- Supabase billing overview: [About billing on Supabase](https://supabase.com/docs/guides/platform/billing-on-supabase)
- Supabase compute pricing examples: [Manage Compute usage](https://supabase.com/docs/guides/platform/manage-your-usage/compute)
- Supabase branching pricing: [Manage Branching usage](https://supabase.com/docs/guides/platform/manage-your-usage/branching)
- Roboflow plans overview: [Plans](https://docs.roboflow.com/billing/plans)
- Roboflow public pricing page: [Roboflow Pricing and Plans](https://roboflow.com/pricing)
- Roboflow premium trial details: [Premium Trial](https://docs.roboflow.com/billing/premium-trial)
- GitHub plans overview: [GitHub's plans](https://docs.github.com/en/get-started/learning-about-github/githubs-plans)
- GitHub pricing page: [GitHub Pricing](https://github.com/pricing)
- OpenAI API pricing: [OpenAI API Pricing](https://openai.com/api/pricing)
