# Contributing to UX Scorecard

Thank you for your interest in contributing to the UX Scorecard skill! This document provides guidelines for contributing.

## 🎯 Ways to Contribute

### 1. Bug Reports
If you find a bug or issue:
- **Search existing issues** first to avoid duplicates
- **Use the bug report template** when creating a new issue
- Include:
  - Clear description of the problem
  - Steps to reproduce
  - Expected vs actual behavior
  - Screenshots if applicable
  - Your environment (Claude Code version, OS)

### 2. Feature Requests
For new feature ideas:
- **Check the roadmap** in README.md to see if it's already planned
- **Use the feature request template**
- Explain:
  - The use case / problem it solves
  - Proposed solution
  - Why this would benefit the community
  - Examples if applicable

### 3. Documentation Improvements
Documentation is critical! Contributions welcome for:
- Fixing typos or unclear explanations
- Adding more examples
- Improving installation instructions
- Translating to other languages
- Adding screenshots/visuals

### 4. Code Contributions
For skill improvements or bug fixes:
- **Fork the repository**
- **Create a feature branch** (`feature/your-feature-name`)
- **Make your changes**
- **Test thoroughly** with real designs
- **Submit a pull request**

## 📋 Pull Request Process

### Before You Start
1. **Check existing PRs** to avoid duplicate work
2. **Create an issue** first for major changes to discuss approach
3. **Review the code of conduct** (be respectful and constructive)

### Submitting a PR
1. **Fork** the repo and create a branch from `main`
2. **Make your changes** following the style guidelines below
3. **Test** your changes:
   - Install the skill locally
   - Test with at least 3 different designs
   - Verify scoring remains consistent
4. **Update documentation** if needed
5. **Write a clear PR description**:
   - What problem does this solve?
   - What changes were made?
   - How to test it?
   - Any breaking changes?
6. **Link related issues** in the PR description

### PR Review Process
- Maintainers will review within 7 days
- Address feedback promptly
- Once approved, maintainers will merge
- Your contribution will be credited in CHANGELOG.md

## 📝 Style Guidelines

### Markdown Files
- Use clear, concise language
- Break up long paragraphs
- Use headers for organization (##, ###)
- Include code examples in triple backticks
- Use tables for comparisons
- Add emojis sparingly for visual breaks

### Skill Definition (SKILL.md)
- Keep the 10 heuristics framework stable
- Maintain backward compatibility
- Document any scoring changes
- Include examples for new features
- Version changes appropriately

### Code Style
If adding automation/tooling:
- Use descriptive variable names
- Comment complex logic
- Follow existing patterns
- Include error handling
- Add tests if applicable

## 🔬 Testing Guidelines

### Manual Testing Checklist
Before submitting a PR, test:

- [ ] Skill loads without errors
- [ ] Can evaluate PDF input
- [ ] Can evaluate image input
- [ ] Can evaluate Figma URL (if MCP available)
- [ ] All 10 heuristics score correctly
- [ ] Overall score calculates correctly
- [ ] Badge assignment is accurate
- [ ] Camp gate validation works
- [ ] Output format matches specification
- [ ] Examples in documentation work

### Test with Variety
Test across different design types:
- Simple wireframes (should score lower)
- Polished mockups (should score higher)
- Component libraries
- Multi-screen flows
- Competitor designs

### Score Consistency
- Same design should score similarly across evaluations
- Different evaluators should score within ±0.5 points
- Known good designs should score ≥ 4.0
- Known poor designs should score ≤ 2.5

## 🎯 Contribution Areas

### High Priority
These contributions are especially valuable:

1. **Real-world examples** - Add more usage examples to USAGE_EXAMPLES.md
2. **Calibration guide** - Help teams align on scoring interpretation
3. **Multi-language support** - Translate documentation
4. **Automation tools** - Scripts for batch scoring, trend tracking
5. **Integration guides** - Jira, Confluence, Notion, etc.

### Medium Priority
6. **Advanced features** - Multi-evaluator aggregation, historical tracking
7. **Visual improvements** - Diagrams, flowcharts, infographics
8. **Video tutorials** - Screencasts showing usage
9. **Case studies** - Before/after score improvements

### Nice to Have
10. **Plugin development** - Figma plugin version
11. **CLI tool** - Command-line scorecard runner
12. **Dashboard** - Web UI for team analytics
13. **API** - RESTful API for programmatic access

## 🐛 Bug Fix Guidelines

### For Bug Fixes
- Include the issue number in commit message: `fix: resolve scoring bug (#123)`
- Add test case that reproduces the bug
- Verify fix doesn't break other functionality
- Update CHANGELOG.md

### Commit Message Format
```
<type>: <description>

<optional body>

<optional footer>
```

**Types:**
- `fix:` Bug fix
- `feat:` New feature
- `docs:` Documentation only
- `style:` Formatting, no code change
- `refactor:` Code restructuring
- `test:` Adding tests
- `chore:` Maintenance tasks

**Examples:**
```
fix: correct scoring calculation for accessibility heuristic

The color contrast check was using wrong WCAG standard (AA vs AAA).
Now correctly uses AA (4.5:1) as per the playbook.

Closes #45
```

```
feat: add multi-evaluator aggregation mode

Allows 2+ reviewers to score independently, then aggregates scores
with variance analysis to identify contentious heuristics.

Part of Phase 2 roadmap.
```

```
docs: add Spanish translation of README

Adds README.es.md with complete translation of the main README.
```

## 📚 Documentation Standards

### README Updates
- Keep installation instructions up-to-date
- Update feature list when adding capabilities
- Maintain roadmap accuracy
- Add new contributors to credits

### USAGE_EXAMPLES Updates
- Use realistic scenarios
- Show complete input → output flow
- Explain WHY the score was assigned
- Include edge cases
- Add screenshots where helpful

### SKILL.md Updates
- Document new heuristics (with justification)
- Explain scoring changes
- Version changes appropriately
- Maintain backward compatibility notes

## 🏆 Recognition

Contributors will be recognized in:
- **README.md** - Contributors section
- **CHANGELOG.md** - Credit for each contribution
- **GitHub** - Contributor badge
- **Release notes** - Major contributors highlighted

## 🤝 Code of Conduct

### Our Standards
- Be respectful and inclusive
- Welcome diverse perspectives
- Provide constructive feedback
- Focus on what's best for the community
- Show empathy towards others

### Unacceptable Behavior
- Harassment or discriminatory language
- Personal attacks or trolling
- Publishing others' private information
- Unprofessional conduct

### Enforcement
Violations may result in:
- Warning
- Temporary ban
- Permanent ban

Report issues to: [your-email@example.com]

## 📞 Questions?

- **General questions**: Open a GitHub Discussion
- **Bug reports**: Create an issue
- **Feature ideas**: Create an issue with `enhancement` label
- **Security issues**: Email privately to [security@example.com]

## 🚀 Development Setup

### Local Development
```bash
# 1. Fork and clone
git clone https://github.com/YOUR-USERNAME/uxscorecard.git
cd uxscorecard

# 2. Create branch
git checkout -b feature/my-feature

# 3. Install skill locally
ln -s $(pwd)/SKILL.md ~/.claude/skills/ux-scorecard.md

# 4. Test your changes
# [Open Claude Code and test]

# 5. Commit and push
git add .
git commit -m "feat: add my feature"
git push origin feature/my-feature

# 6. Create PR on GitHub
```

### Testing Changes
```bash
# Test with sample design
# 1. Open Claude Code
claude

# 2. Test the skill
"Test /ux-scorecard with [upload design]"

# 3. Verify output matches expected format
```

## 📄 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Thank you for contributing to UX Scorecard!** Your improvements help design teams worldwide create better user experiences. 🎨✨
