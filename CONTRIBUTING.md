# Contributing to Mylesoft Technologies

Thank you for your interest in contributing to Mylesoft Technologies! We build AI-powered software for East Africa and welcome contributions that help us fulfil our mission of **Transforming Industries, Empowering Generations.**

---

## 📋 Table of Contents
- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Branch Naming Convention](#branch-naming-convention)
- [Commit Message Convention](#commit-message-convention)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)
- [Contact](#contact)

---

## 📜 Code of Conduct
By contributing, you agree to uphold our [Code of Conduct](CODE_OF_CONDUCT.md). Please read it before participating.

---

## 🚀 Getting Started

1. **Fork** the repository you want to contribute to
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/REPO-NAME.git
   cd REPO-NAME
   ```
3. **Install dependencies** as described in the repo's `README.md`
4. **Create a branch** for your changes (see Branch Naming below)
5. **Make your changes**, test thoroughly, then submit a Pull Request

---

## 🔄 Development Workflow

```
main          ← Production-ready code only. Protected branch.
develop       ← Integration branch. All features merge here first.
feature/*     ← New features and enhancements
fix/*         ← Bug fixes
hotfix/*      ← Critical production fixes
chore/*       ← Maintenance, dependency updates, refactors
docs/*        ← Documentation only changes
```

**Never commit directly to `main`.** All changes go through Pull Requests.

---

## 🌿 Branch Naming Convention

```
feature/short-description        e.g. feature/student-report-cards
fix/short-description            e.g. fix/login-redirect-loop
hotfix/short-description         e.g. hotfix/payment-api-crash
chore/short-description          e.g. chore/update-dependencies
docs/short-description           e.g. docs/api-authentication
```

---

## 💬 Commit Message Convention

We follow the **Conventional Commits** standard:

```
type(scope): short description

[optional body]

[optional footer]
```

**Types:**
| Type | When to Use |
|------|-------------|
| `feat` | A new feature |
| `fix` | A bug fix |
| `docs` | Documentation changes |
| `style` | Formatting, missing semicolons (no logic change) |
| `refactor` | Code restructuring (no feature or fix) |
| `test` | Adding or updating tests |
| `chore` | Build process, dependency updates |
| `perf` | Performance improvements |
| `ci` | CI/CD configuration changes |

**Examples:**
```
feat(auth): add WorkOS SSO integration
fix(payments): resolve M-Pesa callback timeout
docs(api): update authentication endpoints
chore(deps): upgrade Next.js to v15
```

---

## 🔍 Pull Request Process

1. Ensure your branch is up to date with `develop`
2. Fill out the Pull Request template completely
3. Ensure all checks pass (linting, tests, build)
4. Request review from at least one team member
5. Address all review comments before merging
6. PRs are merged using **Squash and Merge** to keep history clean

---

## 💻 Coding Standards

- **TypeScript** — All new code must be typed. Avoid `any`.
- **Formatting** — We use Prettier. Run `npm run format` before committing.
- **Linting** — We use ESLint. Run `npm run lint` and fix all warnings.
- **Testing** — Write tests for new features. Maintain coverage above 70%.
- **Comments** — Comment complex logic. Use JSDoc for exported functions.
- **No console.log** — Use the project logger instead.
- **Environment Variables** — Never hardcode secrets. Use `.env` files.

---

## 🐛 Reporting Bugs

Use the [Bug Report template](https://github.com/Mylesoft-Technologies/.github/blob/main/.github/ISSUE_TEMPLATE/bug_report.md) when creating an issue. Include as much detail as possible — steps to reproduce, screenshots, and environment details help us resolve issues faster.

---

## 💡 Suggesting Features

Use the [Feature Request template](https://github.com/Mylesoft-Technologies/.github/blob/main/.github/ISSUE_TEMPLATE/feature_request.md). Clearly describe the problem you're solving and how your proposed feature addresses it.

---

## 📬 Contact

For questions about contributing, reach out to:
- **Email:** info@mylesoft.com
- **Website:** [www.mylesoft.com](https://www.mylesoft.com)
- **Location:** Westlands, Nairobi, Kenya

---

*Building Legacies, Empowering Generations.* 🌍
