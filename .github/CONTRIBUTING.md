# Contributing to Dev-Events

First off, thank you for considering contributing to Dev-Events! 🎉

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Coding Standards](#coding-standards)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)

## 📜 Code of Conduct

This project and everyone participating in it is governed by our Code of Conduct. By participating, you are expected to uphold this code. Please report unacceptable behavior to the project maintainers.

## 🤝 How Can I Contribute?

### Reporting Bugs
- Use the bug report template
- Include detailed steps to reproduce
- Add screenshots if applicable
- Specify your environment details

### Suggesting Features
- Use the feature request template
- Explain the problem your feature solves
- Provide use cases and examples
- Consider backward compatibility

### Code Contributions
- Fix bugs from the issue tracker
- Implement new features
- Improve documentation
- Add tests
- Optimize performance

## 🛠 Development Setup

1. **Fork and Clone**
   ```bash
   git clone https://github.com/YOUR_USERNAME/Dev-Events.git
   cd Dev-Events
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Set Up Environment**
   ```bash
   cp .env.example .env.local
   # Add your environment variables
   ```

4. **Run Development Server**
   ```bash
   npm run dev
   ```

5. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

## 📏 Coding Standards

### TypeScript
- Use TypeScript for all new files
- Define proper types and interfaces
- Avoid using `any` type
- Use type inference where appropriate

### Code Style
- Follow ESLint rules
- Use Prettier for formatting
- Keep functions small and focused
- Write self-documenting code
- Add comments for complex logic

### Component Guidelines
- Use functional components with hooks
- Keep components small and reusable
- Use proper prop types
- Implement error boundaries where needed
- Follow React best practices

### File Organization
```
- Use kebab-case for files: my-component.tsx
- Use PascalCase for components: MyComponent
- Use camelCase for functions: myFunction
- Group related files together
```

### Best Practices
- Write descriptive variable names
- Keep functions pure when possible
- Use async/await over promises
- Handle errors gracefully
- Validate user inputs
- Optimize for performance

## 📝 Commit Guidelines

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification.

### Commit Message Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `build`: Build system changes
- `ci`: CI/CD changes
- `chore`: Other changes

### Examples
```bash
feat(events): add event filtering by tags
fix(booking): resolve email validation issue
docs(readme): update installation instructions
style(navbar): improve mobile responsiveness
refactor(api): optimize event fetching logic
```

## 🔄 Pull Request Process

1. **Update Your Branch**
   ```bash
   git fetch origin
   git rebase origin/main
   ```

2. **Run Tests**
   ```bash
   npm run lint
   npm run build
   npm test
   ```

3. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "feat: add amazing feature"
   ```

4. **Push to Your Fork**
   ```bash
   git push origin feature/your-feature-name
   ```

5. **Create Pull Request**
   - Use the PR template
   - Link related issues
   - Add screenshots/videos
   - Request review

6. **Code Review**
   - Address review comments
   - Keep discussion constructive
   - Update PR as needed

7. **Merge**
   - Squash commits if requested
   - Ensure CI passes
   - Wait for approval

## 🐛 Reporting Bugs

### Before Submitting
- Check existing issues
- Verify it's reproducible
- Test on latest version

### Bug Report Should Include
- Clear title and description
- Steps to reproduce
- Expected vs actual behavior
- Environment details
- Screenshots/logs
- Possible solution (if any)

## 💡 Suggesting Features

### Before Submitting
- Check if feature exists
- Review open feature requests
- Consider if it fits project scope

### Feature Request Should Include
- Clear use case
- Problem it solves
- Proposed solution
- Alternative approaches
- Implementation ideas
- Benefits to users

## 🧪 Testing

- Write tests for new features
- Update tests for bug fixes
- Ensure all tests pass
- Maintain test coverage
- Test edge cases

## 📚 Documentation

- Update README for new features
- Add inline code comments
- Update API documentation
- Create examples if needed
- Keep docs in sync with code

## 🎯 Priority Labels

- `critical`: Security issues, breaking bugs
- `high`: Important features/fixes
- `medium`: Standard issues
- `low`: Nice to have

## 🏆 Recognition

Contributors will be recognized in:
- README acknowledgments
- Release notes
- GitHub contributors page

## 📞 Getting Help

- Open a discussion
- Join community chat
- Check documentation
- Ask in pull request

## 📄 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to Dev-Events! 🚀
