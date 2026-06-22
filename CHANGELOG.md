# Changelog

All notable changes to the UX Scorecard skill will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Multi-evaluator aggregation mode
- Historical tracking and trend analysis
- Automated Jira issue creation
- Component library batch scoring
- Team dashboard with analytics

## [2.0.1] - 2026-06-22

### Added

#### Specific Screen Identification (MANDATORY)
- **Figma evaluations** now REQUIRE exact screen references with node-id links
- **Every finding must include:**
  - Screen name (frame name from Figma)
  - Direct Figma link with node-id parameter
  - Format: `📍 Screen: [Frame Name] | 🔗 [Figma URL with node-id]`
- **PDF evaluations** must reference page numbers and section names
- **Image evaluations** must reference filename and describe screen
- **Limitation warnings** when evaluation is from overview only (cannot read content)
- **Auto-caps scores** when details are not visible (H2, H9, H10 capped at 2)

**Before (v2.0):**
```
❌ "Forms appear too dense with multiple fields"
```

**After (v2.1):**
```
✅ "Forms appear too dense with multiple fields
📍 Screen: Business Details Form | 🔗 https://figma.com/design/ABC?node-id=123-456
📍 Screen: Owner Information | 🔗 https://figma.com/design/ABC?node-id=123-789"
```

**Impact:**
- Findings are now actionable with exact screen locations
- Designers can navigate directly to problem areas
- No more "where is this issue?" confusion
- Clear distinction between detailed vs overview-only evaluations

### Changed

#### Evaluation Methodology
- **Figma workflows** now use `get_metadata` + `get_screenshot` for individual screens
- **Overview evaluations** are clearly marked as high-level only
- **Content quality scores** require readable content (not 68k-wide overviews)
- **Recommendations** specify screen links for every affected screen

#### Output Format Updates
- All findings now include `📍 Screen:` and `🔗` sections
- Multi-screen issues list all affected screens with links
- Limitation warnings explain when scores are capped due to lack of detail

### Fixed
- Vague findings without specific screen references
- Generic recommendations that don't pinpoint exact locations
- Confusion about which screens have which issues
- Inability to navigate from finding to actual design

---

## [2.0.0] - 2026-06-22

### ⚠️ BREAKING CHANGES

**Major scoring methodology overhaul from lenient to strict evaluation**

- **Scores will drop 0.4-1.4 points** on average (-11% to -39%)
- **Grades typically drop 1-2 levels** (B → C+, B → C-)
- **Score 5 now RARE** (< 5% of all scores) - reserved for best-in-class only
- **Auto-fail criteria** introduced - blocks shipping for critical issues
- **Philosophy change**: "Benefit of doubt" → "Guilty until proven innocent"

**Impact on existing designs:**
- Business Onboarding Flow: 3.4 → 2.5 (-0.9, BLOCKED)
- Consumer Lending App: 3.6 → 2.2 (-1.4, BLOCKED)
- Loyalty Rewards System: 3.8 → 3.4 (-0.4, conditional)

### Added

#### H11: Flow Continuity (New Heuristic)
- Evaluates screen-to-screen user journey
- Assesses transition logic, context preservation, navigation consistency
- Checks for dead ends and confusing navigation
- Scores 1-5 based on journey coherence

#### Apple Human Interface Guidelines (HIG) Integration
- iOS-specific compliance checks:
  - Touch targets ≥44pt
  - Dark Mode support
  - Dynamic Type (text scaling)
  - Safe area respect (no content behind notch/home indicator)
  - Native iOS patterns validation (not Material Design)
  - Standard gestures (swipe back, pull to refresh)
- Automatic score deductions for HIG violations:
  - Material Design on iOS → H2 = 2, H9 = 2
  - Touch targets <44pt → H8 = 2 (accessibility fail)
  - No Dark Mode → H8 -1
- Reference integration: https://developer.apple.com/design/human-interface-guidelines

#### Auto-Fail Criteria (Blocks Shipping)
Designs **immediately FAIL** regardless of average score if:
1. H6 (Trust & Safety) ≤ 2 on financial/lending products
2. Any heuristic = 1 in Camp 3 review
3. More than 3 heuristics ≤ 2 in Camp 3
4. Security-critical actions without confirmation (H4 = 1)
5. Lorem ipsum or placeholder content visible in Camp 3
6. Inaccessible to screen readers (H8 ≤ 1) for public products

#### Automatic Score Deductions
12+ instant penalties for common issues:
- Cannot read content/copy: -2 points (H2, H6, H9, H10)
- Financial product without trust indicators: -2 points → AUTO-FAIL if H6 ≤ 2
- Dense forms (>5 fields per screen): -1 point (H2, H5)
- No save/exit on multi-step flows: -1 point (H3)
- Accessibility unverified: -1 point, H8 capped at 2
- Lorem ipsum visible: -2 points (H2, H9)
- Rejection without empathy (lending): -2 points (H10, 2x multiplier)
- No multi-language support: -1 point (H8)
- Security actions without confirmation: -2 points (H4)
- No visible error states: -1 point (H4)
- No loading/progress states: -1 point (H1)
- Cannot verify screen reader compatibility: -2 points (H8)

#### Product-Specific Multipliers
Financial/lending and healthcare products receive **2x penalties** on:
- H2 (Simplicity): Pricing transparency mandatory
- H4 (Error Prevention): Safety confirmations required
- H6 (Trust & Safety): Trust indicators NON-NEGOTIABLE
- H10 (Emotional): Empathy critical (rejection, stress handling)

**Example:** Lending app missing trust indicator: H6 = 3 → -2 (2x) = 1 (AUTO-FAIL)

#### Content Quality Assessment (Mandatory)
Content IS design - must evaluate:
- **Clarity**: Free of jargon, understandable to target users
- **Tone**: Empathetic in stressful moments (rejections, errors)
- **Completeness**: No lorem ipsum, all copy finalized
- **Accuracy**: Correct grammar, spelling, facts
- **Scannability**: Short sentences, clear hierarchy
- **Actionability**: CTAs are clear and specific

**Impact:**
- Poor/missing content: H2 -2, H6 -1, H9 -2, H10 -2
- Generic/template copy: H2 -1, H10 -1
- Good but unpolished: H2 -0.5
- Excellent: Can boost +0.5

#### Strict Accessibility Defaults
- **OLD**: Assume accessible until proven otherwise
- **NEW**: Assume fails WCAG 2.1 AA until proven
- Cannot verify accessibility = H8 = 2 max
- Must provide evidence of:
  - WCAG 2.1 AA compliance testing
  - Screen reader compatibility
  - Keyboard navigation support
  - Touch target sizes ≥44pt (iOS) or ≥48px (Android)
  - Dynamic Type support (iOS)
  - Multi-language support

### Changed

#### Scoring Philosophy: "Guilty Until Proven Innocent"
- **OLD (v1.0)**: Assume designs are good unless proven otherwise
- **NEW (v2.0)**: Assume issues exist until proven otherwise
- Default to LOWER scores when evidence is insufficient
- Cannot verify = assume fails

#### Evidence Requirements for High Scores
**Score 4-5 Requirements:**
- Must provide 2+ concrete examples of excellence
- Show zero critical issues
- Benchmark against industry leaders (Apple, Stripe, Airbnb)
- Verify actual implementation (not just promises)

**Score 3 Requirements:**
- Show basic implementation exists
- Identify 3+ areas for improvement
- Document missing features

**Score 2 Requirements:**
- List specific major issues
- Explain user impact
- Assess if safe to ship

#### Stricter Default Scores

| Scenario | v1.0 Score | v2.0 Score | Rationale |
|----------|-----------|-----------|-----------|
| Cannot see content/copy | 3-4 | **2** | Assume poor until verified |
| Overview only (no detail) | 3-4 | **2-3** | Cannot assess quality |
| Unclear if feature exists | 3 | **2** | Assume it doesn't |
| Financial product without trust | 3 | **1-2** (AUTO-FAIL) | Trust is non-negotiable |
| Cannot verify accessibility | 3 | **2** | Assume fails WCAG |
| No interactive prototype | 3-4 | **Cap at 3** | Cannot verify UX |

#### Score Distribution Targets
- Score 5: RARE (< 5%) - best-in-class only (was 10-15%)
- Score 4: Good (15-20%) (was 30-40%)
- Score 3: Default (40-50%) - most common (was 30-40%)
- Score 2: Serious issues (20-30%) (was 10-15%)
- Score 1: Broken/unsafe (< 5%) (was < 5%)

#### Camp 3 Requirements Strengthened
**NEW Auto-Fail Criteria** (in addition to 3.5 score minimum):
- All content finalized (no lorem ipsum)
- Accessibility verified (not assumed)
- Usability testing completed
- Critical safety/trust features present
- No heuristic = 1
- No more than 3 heuristics ≤ 2

### Deprecated

#### v1.0 Lenient Scoring
- "Benefit of doubt" scoring approach deprecated
- Auto-detection weight system deprecated (replaced by product-specific multipliers)
- Lenient accessibility assumptions deprecated

**Do NOT compare v2.0 scores to v1.0 scores** - methodology fundamentally changed

### Documentation

#### New Documentation (v2.0)
- **UX_SCORECARD_V2_IMPROVEMENTS.md** - Comprehensive v2.0 guide (12,000+ words)
  - Complete before/after comparison
  - Evidence requirements
  - Auto-fail criteria explanation
  - Real-world re-evaluation examples
  - Migration guide

#### Updated Documentation
- **SKILL.md** - Complete rewrite with strict scoring rules
  - New H11: Flow Continuity heuristic
  - Apple HIG integration section
  - Auto-fail criteria table
  - Automatic deductions table
  - Product-specific multipliers
  - Content quality assessment requirements
  - Accessibility quick check
  - Scoring calibration examples
  - Red flags checklist

- **README.md** - Updated for v2.0
  - Breaking changes warning
  - Auto-fail criteria explanation
  - Real-world impact examples
  - New best practices
  - Updated scoring guide

#### Evaluation Examples (Included in UX_SCORECARD_V2_IMPROVEMENTS.md)
- Business Onboarding Flow: Before (3.4) vs After (2.5) analysis
- Consumer Lending App: Before (3.6) vs After (2.2) analysis with auto-fail
- Loyalty Rewards System: Before (3.8) vs After (3.4) analysis
- Detailed heuristic-by-heuristic breakdowns
- Scoring rationale for each change

### Technical

#### Framework Updates
- **Heuristics**: 10 → 11 (added H11: Flow Continuity)
- **Scoring algorithm**: Simple average → Deduction-based strict scoring
- **Default behavior**: Optimistic → Pessimistic (guilty until proven innocent)
- **Camp 3 logic**: Score-based → Score + Auto-fail criteria

#### Performance
- No performance impact (scoring logic only)
- Same input/output format
- Backwards compatible with v1.0 invocation syntax

### Fixed
- Grade inflation issue (designs scoring 3.5-4.0 when quality was 2.5-3.0)
- Missing critical issues that would cause post-launch failures
- Insufficient differentiation between good and excellent designs
- Over-generous benefit of doubt leading to flawed designs passing
- Lack of consequences for unverified quality claims

### Security
- Auto-fail on security-critical actions without confirmation
- Stricter evaluation of trust indicators in financial products
- Mandatory verification of data security messaging
- Enhanced focus on error prevention in high-stakes flows

### Migration Guide

**For Designers:**
1. Re-evaluate all in-flight designs with v2.0
2. Expect scores to drop 0.4-1.4 points
3. Focus on fixing critical issues (≤2) first
4. Ensure content is readable in reviews (no tiny overviews)
5. Prove accessibility compliance (don't assume)
6. For financial products: add trust indicators immediately (auto-fail risk)

**For Reviewers:**
1. Do NOT compare v2.0 scores to v1.0 scores (different methodology)
2. Communicate to team: "Lower scores = more accurate, not worse design"
3. Focus on auto-fail criteria for Camp 3 gates
4. Build new score calibration examples for v2.0

**For Design Ops:**
1. Update all Camp 3 gates to include auto-fail criteria checks
2. Re-baseline team score averages (will drop significantly)
3. Do NOT use v1.0 scores in historical trend analysis
4. Run calibration sessions with v2.0 examples

### Rationale for v2.0 Changes

**Why the change?**

v1.0 gave passing grades (3.4-3.8) to designs with:
- ❌ Missing trust indicators (financial products)
- ❌ Unverified content quality
- ❌ No save/resume (multi-step flows)
- ❌ Unverified accessibility
- ❌ Poor rejection handling (lending)
- ❌ Missing safety confirmations

**These would have caused:**
- Product launch failures
- User trust issues
- Regulatory compliance problems
- Brand damage
- Costly post-launch fixes
- Legal liability

**v2.0 correctly identifies these as SHIP-BLOCKING issues.**

## [1.0.0] - 2026-06-19

### Added
- Initial release of UX Scorecard skill
- 10 UX heuristics framework (Usability, Trust & Security, Accessibility, Onboarding, Emotional Reassurance)
- 1-5 scoring scale for each heuristic
- 8 badge levels (A, B+, B, C+, C, C-, D, F)
- Camp 1/2/3 gate validation
- Multi-format input support:
  - PDF presentations
  - Image screenshots (PNG, JPG)
  - Figma files via Figma MCP
  - Design context/briefs
- Comprehensive scorecard output:
  - Overall score and badge
  - Heuristic-by-heuristic breakdown
  - Critical findings (score ≤ 2)
  - Improvement areas (score = 3)
  - Strengths (score ≥ 4)
  - Actionable recommendations
  - Camp readiness assessment
- Complete documentation (2,345 lines):
  - SKILL.md - Complete skill specification
  - README.md - Project overview and quick start
  - USAGE_EXAMPLES.md - 4 detailed real-world scenarios
  - INSTALLATION.md - Setup and troubleshooting guide
  - QUICK_REFERENCE.md - One-page cheat sheet
  - SCORECARD_TEMPLATE.md - Manual scoring template
  - PROJECT_SUMMARY.md - Comprehensive project overview
- GitHub repository structure:
  - LICENSE (MIT)
  - CONTRIBUTING.md
  - CHANGELOG.md
  - .gitignore

### Documentation
- 4 detailed usage examples:
  - Pre-critique self-review
  - Competitor benchmarking
  - Camp 3 readiness check
  - Component library audit
- Complete installation guide with troubleshooting
- Quick reference card for daily use
- Manual scoring template for offline reviews
- Comprehensive project summary

### Technical
- Based on Product Design Regional Playbook UX Heuristics (pages 57-60)
- Compatible with Claude Code CLI
- Supports Figma MCP server integration
- Scoring algorithm: Simple average of 10 heuristic scores
- Camp gate thresholds:
  - Camp 1: No minimum (concept validation)
  - Camp 2: ≥ 3.0 (C)
  - Camp 3: ≥ 3.5 (B)

## Version History Format

### [Version Number] - YYYY-MM-DD

#### Added
New features or capabilities

#### Changed
Changes to existing functionality

#### Deprecated
Features that will be removed in future versions

#### Removed
Features that have been removed

#### Fixed
Bug fixes

#### Security
Security vulnerability fixes

---

## Release Notes

### v1.0.0 - Initial Release (June 19, 2026)

**🎉 First public release of UX Scorecard!**

This release provides a complete, production-ready design grading and review skill based on the Product Design Regional Playbook's UX Heuristics framework.

**Key Features:**
- Evaluate designs across 10 UX heuristics
- Support for PDF, images, and Figma files
- Automatic Camp gate validation
- Comprehensive scorecard with actionable recommendations
- 2,000+ lines of documentation

**Getting Started:**
```bash
# Install
ln -s /path/to/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md

# Test
claude
"What is the /ux-scorecard skill?"
```

**What's Next:**
Phase 2 features planned for Q3 2026:
- Multi-evaluator mode
- Historical tracking
- Jira integration
- Team analytics dashboard

**Contributors:**
- Initial development: Claude Code + Regional Design Team
- Framework source: Product Design Regional Playbook

**Feedback:**
Please open issues on GitHub for bugs, feature requests, or questions!

---

## Upgrade Guide

### From Pre-release to v1.0.0

If you were using an early version of this skill:

1. **Backup your custom modifications** (if any)
2. **Uninstall old version**: `rm ~/.claude/skills/ux-scorecard.md`
3. **Install v1.0.0**: `ln -s /path/to/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md`
4. **Restart Claude Code**: `exit && claude`
5. **Test**: Verify skill loads correctly

**Breaking Changes**: None (this is the first stable release)

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines on:
- Reporting bugs
- Requesting features
- Submitting pull requests
- Development setup

---

## Support

- **Documentation**: See README.md, USAGE_EXAMPLES.md, INSTALLATION.md
- **Issues**: https://github.com/YOUR-ORG/uxscorecard/issues
- **Discussions**: https://github.com/YOUR-ORG/uxscorecard/discussions

---

**Legend:**
- 🎉 Major release
- ✨ New feature
- 🐛 Bug fix
- 📚 Documentation
- ⚠️ Breaking change
- 🔒 Security fix
