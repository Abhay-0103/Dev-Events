# CI/CD Quick Reference Guide

## 🚀 Common Commands

### Local Development
```bash
# Start dev server
npm run dev

# Run linting
npm run lint

# Type check
npx tsc --noEmit

# Build for production
npm run build

# Start production server
npm start
```

### Git Workflow
```bash
# Create feature branch
git checkout -b feature/your-feature

# Commit with conventional format
git commit -m "feat: add new feature"

# Push to GitHub (triggers CI)
git push origin feature/your-feature

# Update branch with main
git fetch origin
git rebase origin/main
```

### Vercel CLI
```bash
# Install globally
npm i -g vercel

# Link project
vercel link

# Deploy manually
vercel --prod

# View deployments
vercel ls
```

## 📝 Commit Message Format

```
<type>(<scope>): <subject>

[optional body]

[optional footer]
```

### Types
| Type | Description | Example |
|------|-------------|---------|
| `feat` | New feature | `feat(events): add filtering` |
| `fix` | Bug fix | `fix(booking): email validation` |
| `docs` | Documentation | `docs(readme): update setup` |
| `style` | Formatting | `style(navbar): fix spacing` |
| `refactor` | Code restructure | `refactor(api): optimize queries` |
| `perf` | Performance | `perf(images): lazy loading` |
| `test` | Tests | `test(events): add unit tests` |
| `build` | Build system | `build(webpack): update config` |
| `ci` | CI/CD changes | `ci(github): add new workflow` |
| `chore` | Maintenance | `chore(deps): update packages` |

## 🔄 Workflow Triggers

| Workflow | Trigger | When |
|----------|---------|------|
| CI Pipeline | Push, PR | Any branch |
| CD Pipeline | Push | main/master only |
| Preview Deploy | PR | Open, sync, reopen |
| CodeQL | Push, PR, Schedule | Weekly Monday |
| Dependency Review | PR | To main/master |
| Auto-merge | PR | Dependabot only |
| Label PR | PR | Open, edit, sync |

## 🔐 Required GitHub Secrets

| Secret | Required For | Get From |
|--------|--------------|----------|
| `MONGODB_URI` | Build, Deploy | MongoDB Atlas |
| `NEXT_PUBLIC_BASE_URL` | Build, Deploy | Your domain |
| `CLOUDINARY_CLOUD_NAME` | Build, Deploy | Cloudinary dashboard |
| `CLOUDINARY_API_KEY` | Build, Deploy | Cloudinary dashboard |
| `CLOUDINARY_API_SECRET` | Build, Deploy | Cloudinary dashboard |
| `VERCEL_TOKEN` | Deploy | Vercel account tokens |
| `NEXT_PUBLIC_POSTHOG_KEY` | Analytics (optional) | PostHog settings |
| `NEXT_PUBLIC_POSTHOG_HOST` | Analytics (optional) | PostHog settings |

## ✅ Pre-Push Checklist

- [ ] Code linted: `npm run lint`
- [ ] Types valid: `npx tsc --noEmit`
- [ ] Builds successfully: `npm run build`
- [ ] Tests pass: `npm test`
- [ ] Commit message follows convention
- [ ] Branch up to date with main

## 📊 Pipeline Status Checks

### All Must Pass ✅
- **Lint Code** - ESLint validation
- **Type Check** - TypeScript compilation
- **Build** - Production build test
- **Security Scan** - Vulnerability check

### Optional Checks
- **Tests** - Unit/integration tests
- **CodeQL** - Security analysis
- **Dependency Review** - License/vulnerability check

## 🐛 Troubleshooting

### Build Failing?
```bash
# Check locally first
npm run build

# Common issues:
# - Missing env variables
# - TypeScript errors
# - Import errors
# - Lint warnings set as errors
```

### Type Errors?
```bash
# Check types
npx tsc --noEmit

# Common fixes:
# - Add proper type definitions
# - Install @types packages
# - Fix any type usage
```

### Deploy Failing?
```bash
# Verify Vercel setup
vercel link

# Check project settings
vercel env ls

# Test deploy
vercel --prod
```

### Secrets Not Working?
1. Go to Settings → Secrets
2. Verify secret name matches exactly
3. Re-add secret if needed
4. Trigger workflow again

## 🔄 Manual Workflow Trigger

1. Go to **Actions** tab
2. Select workflow (e.g., "CD Pipeline")
3. Click "Run workflow"
4. Select branch
5. Click "Run workflow" button

## 📍 Important Files

| File | Purpose |
|------|---------|
| `.github/workflows/ci.yml` | CI pipeline config |
| `.github/workflows/cd.yml` | CD pipeline config |
| `.github/workflows/preview.yml` | Preview deploys |
| `.github/CONTRIBUTING.md` | Contribution guide |
| `.github/PULL_REQUEST_TEMPLATE.md` | PR template |
| `.env.example` | Environment template |

## 🎯 Quick Links

- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Vercel Docs](https://vercel.com/docs)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)

## 📞 Getting Help

1. Check `.github/workflows/README.md`
2. Review GitHub Actions logs
3. Open issue with `ci/cd` label
4. Contact maintainers

## 🎨 Badge URLs

Add to README:
```markdown
![CI](https://github.com/Abhay-0103/Dev-Events/workflows/CI%20Pipeline/badge.svg)
![CD](https://github.com/Abhay-0103/Dev-Events/workflows/CD%20Pipeline/badge.svg)
![Security](https://github.com/Abhay-0103/Dev-Events/workflows/CodeQL/badge.svg)
```

## ⚡ Performance Tips

- Use `npm ci` instead of `npm install` in CI
- Cache node_modules between runs
- Run jobs in parallel when possible
- Skip CI for docs: `[skip ci]` in commit
- Use workflow conditions to skip unnecessary runs

---

**Keep this handy for quick reference!** 📌
