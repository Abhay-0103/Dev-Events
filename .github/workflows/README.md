# GitHub Actions CI/CD Pipeline Configuration

This directory contains the CI/CD pipeline configuration for the Dev-Events project using GitHub Actions.

## 🚀 Workflows Overview

### 1. **CI Pipeline** (`ci.yml`)
Runs on every push and pull request to main branches.

**Jobs:**
- **Lint**: Runs ESLint to check code quality
- **Type Check**: Validates TypeScript types
- **Build**: Compiles the Next.js application
- **Test**: Runs test suite (if available)
- **Security Scan**: Checks for vulnerabilities with npm audit

**Triggers:**
- Push to `main`, `master`, or `develop` branches
- Pull requests targeting these branches

---

### 2. **CD Pipeline** (`cd.yml`)
Deploys the application to production on Vercel.

**Jobs:**
- **Deploy**: Builds and deploys to Vercel production
- **Post-Deploy**: Performs health checks after deployment

**Triggers:**
- Push to `main` or `master` branches
- Manual workflow dispatch

**Requirements:**
- Vercel account and project setup
- `VERCEL_TOKEN` secret configured

---

### 3. **Preview Deployment** (`preview.yml`)
Creates preview deployments for pull requests.

**Jobs:**
- **Preview**: Deploys a preview version to Vercel
- Comments on PR with preview URL

**Triggers:**
- Pull request opened, synchronized, or reopened

---

### 4. **CodeQL Analysis** (`codeql.yml`)
Performs security analysis on the codebase.

**Jobs:**
- **Analyze**: Scans JavaScript and TypeScript code for vulnerabilities

**Triggers:**
- Push to main branches
- Pull requests
- Weekly schedule (Monday midnight)

---

### 5. **Dependency Review** (`dependency-review.yml`)
Reviews dependencies in pull requests for security issues.

**Jobs:**
- **Dependency Review**: Checks for vulnerable or restricted licenses

**Triggers:**
- Pull requests to `main` or `master`

---

### 6. **Auto Merge** (`auto-merge.yml`)
Automatically merges Dependabot PRs for minor and patch updates.

**Triggers:**
- Pull requests from Dependabot

---

### 7. **PR Labeler** (`label.yml`)
Automatically labels pull requests based on changed files.

**Triggers:**
- Pull request opened, edited, or synchronized

---

## ⚙️ Setup Instructions

### 1. Configure GitHub Secrets

Go to your repository **Settings** → **Secrets and variables** → **Actions** and add:

#### Required Secrets:
```
MONGODB_URI                 # MongoDB connection string
NEXT_PUBLIC_BASE_URL       # Your production URL
CLOUDINARY_CLOUD_NAME      # Cloudinary cloud name
CLOUDINARY_API_KEY         # Cloudinary API key
CLOUDINARY_API_SECRET      # Cloudinary API secret
VERCEL_TOKEN              # Vercel deployment token
```

#### Optional Secrets:
```
NEXT_PUBLIC_POSTHOG_KEY   # PostHog analytics key
NEXT_PUBLIC_POSTHOG_HOST  # PostHog host URL
```

---

### 2. Get Vercel Token

1. Go to [Vercel Account Settings](https://vercel.com/account/tokens)
2. Create a new token with appropriate scope
3. Add it as `VERCEL_TOKEN` secret in GitHub

---

### 3. Link Vercel Project

```bash
# Install Vercel CLI
npm i -g vercel

# Link your project
vercel link

# This creates .vercel directory with project info
```

---

### 4. Enable GitHub Actions

1. Go to repository **Settings** → **Actions** → **General**
2. Enable "Allow all actions and reusable workflows"
3. Set workflow permissions to "Read and write permissions"

---

### 5. Configure Branch Protection (Optional)

1. Go to **Settings** → **Branches**
2. Add rule for `main` or `master`
3. Enable:
   - Require status checks to pass before merging
   - Require branches to be up to date before merging
   - Select status checks: `lint`, `type-check`, `build`

---

## 📊 Pipeline Flow

### For Feature Development:
```
1. Create feature branch
2. Push changes → CI runs (lint, type-check, build, test)
3. Create PR → Preview deployment + Dependency review
4. PR approved → Merge to main
5. CD pipeline → Deploy to production
6. Post-deploy health check
```

### For Hotfixes:
```
1. Create hotfix branch
2. Push changes → CI runs
3. Fast-track review
4. Merge → Immediate production deployment
```

---

## 🔍 Monitoring Workflows

### View Workflow Runs:
- Go to **Actions** tab in your repository
- Click on specific workflow to see details
- View logs for each job

### Check Deployment Status:
- Production deploys appear in **Environments** section
- Click on deployment to see details and logs

---

## 🛠️ Troubleshooting

### Build Failures:
1. Check if all secrets are configured
2. Verify environment variables in workflow files
3. Test build locally: `npm run build`
4. Check workflow logs for specific errors

### Deployment Failures:
1. Verify Vercel token is valid
2. Check Vercel project is properly linked
3. Ensure all environment variables are set in Vercel dashboard

### Type Check Failures:
1. Run locally: `npx tsc --noEmit`
2. Fix TypeScript errors
3. Push changes

---

## 🔐 Security Best Practices

✅ Never commit secrets to repository  
✅ Use GitHub Secrets for sensitive data  
✅ Regularly update dependencies  
✅ Enable CodeQL scanning  
✅ Review Dependabot alerts  
✅ Use branch protection rules  

---

## 📈 Performance Optimization

- **Caching**: Node modules are cached to speed up builds
- **Parallel Jobs**: Independent jobs run in parallel
- **Artifact Storage**: Build artifacts are stored for 7 days
- **Conditional Execution**: Jobs skip when not needed

---

## 🎯 Future Enhancements

- [ ] Add E2E testing with Playwright/Cypress
- [ ] Implement staging environment
- [ ] Add performance testing
- [ ] Set up monitoring and alerting
- [ ] Add rollback mechanism
- [ ] Implement blue-green deployments
- [ ] Add load testing

---

## 📝 Workflow Status Badges

Add these to your README:

```markdown
![CI](https://github.com/Abhay-0103/Dev-Events/workflows/CI%20Pipeline/badge.svg)
![CD](https://github.com/Abhay-0103/Dev-Events/workflows/CD%20Pipeline/badge.svg)
![Security](https://github.com/Abhay-0103/Dev-Events/workflows/CodeQL/badge.svg)
```

---

## 📚 Additional Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Vercel Deployment Guide](https://vercel.com/docs/deployments/overview)
- [Next.js CI/CD Best Practices](https://nextjs.org/docs/deployment)

---

For questions or issues with the CI/CD pipeline, please open an issue or contact the maintainers.
