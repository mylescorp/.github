# .github

Organization-wide GitHub templates, shared workflows, and repository policy for MylesCorp Technologies.

## Pull request gate

The reusable minimum gate will live in `.github/workflows/organization-pr-gate.yml`. Repositories invoke it with a small caller workflow. The gate scans the full Git history with Gitleaks and returns a required check on the caller repository's pull request. Product-specific lint, tests, builds, and security checks remain in each product repository.

Starter workflow template: `.github/workflow-templates/organization-pr-gate.yml`. New repositories must add this workflow during setup. Templates do not install themselves into repositories.

## Enforcement status

The MylesCorp organization currently reports that organization rulesets will not be enforced until the organization is upgraded to GitHub Team. Until that change is approved, organization-wide ruleset enforcement is unavailable. Repository owners must protect each default branch individually and require the checks that repository actually publishes. A future repository also needs branch protection configured until organization rulesets are enabled.

After an approved plan upgrade, create an active organization ruleset targeting all current and future repositories and their default branches. Require pull requests, one approval, resolved conversations, no force pushes or branch deletion, and the shared `Organization PR Gate / Gitleaks` workflow. Add product checks per repository. Configure new-repository targeting and bypass access narrowly.

## Rollout

1. Add the starter caller workflow to each current repository and verify its check name appears on a pull request.
2. Add the workflow to each new repository at creation.
3. Protect default branches individually while organization rulesets are unavailable.
4. After GitHub Team is enabled, create the organization ruleset and run it in evaluation before enforcing.
5. Keep language and product checks in their owning repository. Add cross-repository checks only for a versioned shared contract.

The shared workflow is a minimum secret scan. It does not replace code review, dependency review, product tests, deployment approvals, or incident response.
