# .github

Organization-wide GitHub templates, shared workflows, and repository policy for MylesCorp Technologies.

## Pull request gate

The reusable minimum secret scan lives in .github/workflows/organization-pr-gate.yml. It checks out the caller repository history and runs a pinned Gitleaks release with read-only permissions. Product-specific lint, tests, builds, and security checks stay in their owning repositories.

The GitHub Actions starter template and its metadata live at the root workflow-templates/ directory: workflow-templates/organization-pr-gate.yml and workflow-templates/organization-pr-gate.properties.json. Add this workflow to each current repository and when creating new repositories. GitHub templates do not install themselves into repositories.

## Greptile review requirement

MylesCorp merge policy: require a completed Greptile review with a 5/5 score before merging. Treat a score below 5/5, a missing review, or unresolved blocking findings as a merge blocker. The secret scan and Greptile score are separate checks. A review comment that says 5/5 is not itself an enforced status check.

To enforce the score, each repository must publish a stable Greptile 5/5 status check and require that check in its branch protection or ruleset. The shared secret scan does not enforce Greptile scores. Confirm that the Greptile integration can publish a consistent required check for every repository before adding it to an organization ruleset.

## Enforcement status

The MylesCorp organization currently reports that organization rulesets will not be enforced until the organization upgrades to GitHub Team. Until that change is approved, organization-wide ruleset enforcement is unavailable. Repository owners must protect each default branch individually and require the checks that repository actually publishes. Future repositories also need branch protection configured until organization rulesets are enabled.

The organization currently has one member. Do not require an approval count that cannot be met. Start with required PRs and checks; require at least one independent approval after a second human maintainer is available.

After an approved plan upgrade, create an active organization ruleset targeting all current and future repositories and their default branches. Require pull requests, resolved conversations, no force pushes or branch deletion, the shared organization secret scan, and the Greptile 5/5 check once that check is available consistently. Add product checks per repository. Require an approval only when the reviewer pool can satisfy it. Configure new-repository targeting and keep bypass access narrow.

## Rollout

1. Add the starter caller workflow to each current repository and verify its secret-scan check appears on a pull request.
2. Add the workflow and configure Greptile for each new repository at creation.
3. Protect default branches individually while organization rulesets are unavailable. Require only checks the repository consistently publishes.
4. Establish a clean or documented Gitleaks baseline before making the scan required.
5. Verify the Greptile 5/5 status check on representative public and private repositories, then require it in branch protection.
6. After GitHub Team is enabled, create an organization ruleset targeting all repositories and evaluate it before enforcing.
7. Keep language and product checks in their owning repository. Add cross-repository checks only for a versioned shared contract.

The shared secret scan does not replace code review, dependency review, product tests, deployment approvals, or incident response.

## Greptile 5/5 auto-merge

The reusable workflow at .github/workflows/greptile-auto-merge.yml scans open, non-draft pull requests targeting the repository default branch. A caller runs it on a five-minute schedule and supports manual workflow_dispatch. Polling avoids GitHub's suppression of check_run-triggered workflows when a commit is associated with GitHub Actions runs. It checks that the Greptile Apps check from app greptile-apps completed successfully for the PR's exact head SHA, re-reads the PR, and queues only if the head is still unchanged. The merge command also uses --match-head-commit with that SHA to close the race between verification and merge.

The merge uses a short-lived GitHub App installation token rather than GITHUB_TOKEN. GitHub App-authenticated merges can trigger downstream push and pull-request workflows. For each repository that opts in, create a GitHub App with Checks: read, Contents: write, and Pull requests: write permissions, then install it on that repository. Generate the App private key and keep it outside the repository. In the repository's Settings > Secrets and variables > Actions, add GREPTILE_AUTOMERGE_APP_CLIENT_ID as a repository variable and GREPTILE_AUTOMERGE_APP_PRIVATE_KEY as a secret. The caller passes those values to the shared reusable workflow, which scopes the installation token to those three permissions.

The reusable workflow validates the actual check run and does not interpret review comments. Configure Greptile so that only a 5/5 review produces a successful Greptile Apps check, and require that status check in the repository's default-branch protection. GitHub still enforces all required approvals and checks; this workflow never bypasses branch protection. Enable GitHub auto-merge in each repository's settings.

The caller template and metadata are workflow-templates/greptile-auto-merge.yml and workflow-templates/greptile-auto-merge.properties.json. Add the template as .github/workflows/greptile-auto-merge.yml in each repository. A central workflow template does not install or run in other repositories by itself. This is an opt-in per-repository caller. Organization-wide installation and enforcement still need a separate rollout across current repositories, or an organization-level GitHub App integration. New repositories must add the caller template and configure the App variable and secret when they are created.
