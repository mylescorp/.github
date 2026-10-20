# .github

Organization-wide GitHub templates, shared workflows, and repository policy for MylesCorp Technologies.

## Pull request gate

The reusable minimum gate lives in `.github/workflows/organization-pr-gate.yml`. Repositories invoke it with a small caller workflow. The gate scans the full Git history with Gitleaks and returns a check on the caller repository's pull request. Product-specific lint, tests, builds, and security checks stay in each product repository.

Starter workflow template: `.github/workflow-templates/organization-pr-gate.yml`. New repositories must add this workflow during setup. Templates do not install themselves into repositories.

## Enforcement status

The MylesCorp organization currently reports that organization rulesets will not be enforced until the organization upgrades to GitHub Team. Until that change is approved, organization-wide ruleset enforcement is unavailable. Repository owners must protect each default branch individually and require the checks that repository actually publishes. Future repositories also need branch protection configured until organization rulesets are enabled.

The organization currently has one member. Do not require an approval count that cannot be met. Start with required PRs and checks; require at least one independent approval after a second human maintainer is available.

After an approved plan upgrade, create an active organization ruleset targeting all current and future repositories and their default branches. Require pull requests, resolved conversations, no force pushes or branch deletion, and the shared organization gate. Add product checks per repository. Require an approval only when the reviewer pool can satisfy it. Configure new-repository targeting and keep bypass access narrow.

## Rollout

1. Add the starter caller workflow to each current repository and verify its check appears on a pull request.
2. Add the workflow to each new repository at creation.
3. Protect default branches individually while organization rulesets are unavailable.
4. Establish a clean or documented Gitleaks baseline before making the scan a required check in each repository.
5. After GitHub Team is enabled, create the organization ruleset and evaluate it before enforcing.
6. Keep language and product checks in their owning repository. Add cross-repository checks only for a versioned shared contract.

The shared workflow is a minimum secret scan. It does not replace code review, dependency review, product tests, deployment approvals, or incident response.
