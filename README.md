# Purpose of this Repository
This repository contains global configuration, shared workflows, and organization-wide standards used across all Intersport Austria Rent projects.
It is automatically recognized by GitHub and applies its contents to all repositories within the organization.

> [!IMPORTANT]
>This repository does not deploy to production environments.
>Instead, it controls and standardizes behavior across all organization repositories.

## The .github repository serves as the central place for:

### 1. Organization Profile
- profile/README.md — visible on the main organization page
- Branding, mission, and references for contributors

### 2. Shared Templates
- Issue templates (.github/ISSUE_TEMPLATE)
- Pull Request template (.github/PULL_REQUEST_TEMPLATE.md)
- Feature request, bug report, technical proposal templates
- Security vulnerability report instructions

### 3. Global GitHub Actions Workflows (optional)

**Reusable workflows for:**
- CI/CD
- Linting / static analysis
- Dependency security scanning
- Laravel / Nuxt build pipelines
- QA automation
- Code quality checks (PHPStan, Pint, ESLint, TypeScript)

These workflows can be imported into any repository using:
```yaml
uses: intersport-austria-rent/.github/.github/workflows/<workflow-name>.yml@main
```

### 4. Organization Policies

**Documentation and configuration related to:**
- Code review standards
- Branch protection rules
- Commit signing requirements
- Security guidelines
- Use of Codespaces and GitHub Models
- GDPR-compliant development practices

### 5. CODEOWNERS (optional)

**If used, defines teams responsible for reviewing changes in specific file paths:**
- DevOps → workflows, secrets, deployment files
- Engineers → application code
- QA → tests, features, scenarios

**Structure**
```
.github
├── ISSUE_TEMPLATE/
│   ├── bug_report.yml
│   ├── feature_request.yml
│   └── improvement.yml
├── workflows/
│   └── reusable workflows for CI/CD
├── profile/
│   └── README.md                     # Organization overview
├── PULL_REQUEST_TEMPLATE.md
├── CODEOWNERS                        # Team responsibilities (optional)
└── SECURITY_POLICY.md                # GDPR & security guidelines
```

**Updating Templates or Workflows**
1. Create a branch
2. Update templates or workflows
3. Create a Pull Request
4. DevOps and Team Lead must review changes affecting:
   - workflows
   - CODEOWNERS
   - security policies
6. Once merged → updates apply automatically to all repositories

**Using Shared Workflows**
Add to any repo:
```yaml
name: CI
on: [push, pull_request]

jobs:
  build:
    uses: intersport-austria-rent/.github/.github/workflows/ci.yml@main
```

---

### Security Notes
- No sensitive data, secrets, tokens, or private keys must ever be stored here.
- All GitHub Actions secrets must be configured at organizational or repository level.
- Ensure all workflows use pinned versions (@v3, not @latest).

---

### Maintainers
- DevOps team — approves workflow changes
- Engineers team — maintains templates & coding standards
- QA team — maintains testing guidelines
- Managers — administrative oversight
