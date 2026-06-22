# UX Scorecard - Design Grading & Review Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-4.0.0-blue.svg)](https://github.com/YOUR-ORG/uxscorecard/releases)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-compatible-brightgreen.svg)](https://claude.ai/code)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

A comprehensive design evaluation skill using the **UX Heuristics framework** for Claude Code. Evaluate designs against 11 UX heuristics with **strict, realistic scoring** that catches critical issues before shipping.

**🆕 Version 4.0**: 
- ⚡ **STRICT SCORING** - "Guilty until proven innocent" methodology prevents grade inflation
- 🚨 **AUTO-FAIL CRITERIA** - Blocks shipping for critical safety/trust issues
- ✨ **H11: Flow Continuity** - New heuristic for screen-to-screen journey evaluation
- 🍎 **Apple HIG Integration** - iOS-specific compliance checks (touch targets, Dark Mode, etc.)
- 💰 **Financial Product Multipliers** - 2x stricter standards for lending/healthcare
- 📱 **Content Quality Assessment** - Mandatory evaluation of copy, tone, and clarity
- ✍️ **COPYWRITING EVALUATION** - Comprehensive copywriting, typography & CTA best practices with automatic penalties

## 🎯 What This Does

This skill evaluates designs against **11 UX heuristics** with **strict, realistic scoring** and generates:
- ✅ Overall quality score (1-5 scale) with evidence-based grading
- 📊 Grade badge (A, B+, B, C+, C, C-, D, F) with ship/no-ship guidance
- 🔍 Detailed heuristic-by-heuristic breakdown with automatic deductions
- 🚨 **AUTO-FAIL blocking** for critical safety/trust issues
- ✨ Strengths and what works well (with high evidence bar)
- 📋 Actionable next steps prioritized by severity
- ⛺ Camp readiness assessment (Camp 1/2/3) with strict gates
- 🍎 **Apple HIG compliance** checks for iOS platforms
- 💰 **2x stricter standards** for financial/healthcare products
- 🎭 **Flow continuity** evaluation (new H11 heuristic)

## 📥 Supported Inputs

- **PDFs** - Design presentations, wireframes, mockups
- **Images** - PNG/JPG screenshots of UI screens
- **Figma files** - Via Figma MCP (provide Figma URL)
- **Context** - Project brief, PRD, specific focus areas
- **Multi-Channel** - App, web, physical (ATM/kiosk), voice, email, print
- **Any Industry** - Banking, e-commerce, healthcare, education, SaaS, entertainment, etc.

## 🆕 What's New in Version 4.0

### ✍️ NEW: Copywriting, Typography & CTA Best Practices

**Version 4.0 adds comprehensive copywriting evaluation** - automatic penalties for poor copy quality.

**Copywriting Rules (STRICT):**
- **Headers:** 1-2 lines max (mobile), 1 line preferred
- **Body text:** 2-3 lines per paragraph max (mobile)
- **Instructions:** 1-2 sentences maximum
- **CTA hierarchy:** 1 primary CTA per screen (STRICT)
- **Typography:** Same hierarchy = same font size

**Automatic Penalties:**
- Header >2 lines: **-1 point** on H2
- Body text >5 lines: **-1 point** on H2
- Instructions >3 sentences: **-1 point** on H9
- 2 primary CTAs: **-2 points** on H2 (CRITICAL)
- Inconsistent typography: **-1 point** on H2
- Text >50 words on mobile: **-2 points** on H2

**Example Impact:**
```
❌ BAD: "Power up your biz with easy financing and flexi repayments" (3 lines)
   → H2 -1 point penalty

✅ GOOD: "Get financing in minutes" (1 line)
   → PASS, no penalty
```

**See:** [UX_SCORECARD_v4_COPYWRITING_UPDATE.md](./UX_SCORECARD_v4_COPYWRITING_UPDATE.md) for full details

---

### 🚨 MAJOR BREAKING CHANGE: Strict Scoring Methodology (v2.0)

**Version 2.0 fundamentally changed how designs are evaluated** - from lenient to realistic.

#### "Guilty Until Proven Innocent" Philosophy

**OLD (v1.0):** Assume designs are good unless proven otherwise → Grade inflation  
**NEW (v2.0):** Assume issues exist until proven otherwise → Realistic scores

**Expected Impact:**
- Scores will drop **0.4 to 1.4 points** (-11% to -39%)
- Grades typically drop **1-2 levels** (B → C+, B → C-)
- More designs will **fail Camp 3** (requires 3.5, many score 2.5-3.4)
- **Critical issues** will block shipping (auto-fail criteria)

**Why This Change?**

v1.0 gave passing grades to designs with:
- ❌ Missing trust indicators (financial products)
- ❌ Unverified content quality
- ❌ No save/resume (multi-step flows)
- ❌ Unverified accessibility
- ❌ Poor rejection handling (lending)

**These would have caused product failures, user trust issues, and regulatory problems.**

### ✨ New Features

#### 1. Auto-Fail Criteria (Blocks Shipping)

Designs **immediately FAIL** regardless of average score if:

1. **H6 (Trust) ≤ 2 on financial/lending products** → Critical trust gap
2. **Any heuristic = 1** in Camp 3 → Broken experience
3. **More than 3 heuristics ≤ 2** in Camp 3 → Too many critical issues
4. **Security-critical actions without confirmation** (H4 = 1) → Unsafe
5. **Lorem ipsum in Camp 3** → Incomplete design

**Real Example:** Consumer lending product v1.0 scored 3.6 (B) → v2.0 scored 2.2 (C-) **BLOCKED** (H6=2, H10=1)

#### 2. H11: Flow Continuity (NEW Heuristic)

Evaluates **screen-to-screen user journey**:
- Does journey feel natural and logical?
- Are transitions smooth?
- Does context carry forward?
- Any dead ends or confusing navigation?

**Evaluates:** Browse → Select → Confirm → Complete pathway

#### 3. Apple Human Interface Guidelines (HIG) Integration

**iOS-specific compliance checks:**
- ✅ Touch targets ≥44pt
- ✅ Dark Mode support
- ✅ Dynamic Type (text scaling)
- ✅ Safe area respect (no content behind notch)
- ✅ Native iOS patterns (not Material Design)
- ✅ Standard gestures (swipe back, pull to refresh)

**HIG violations auto-lower scores:**
- Material Design on iOS → H2 = 2, H9 = 2
- Touch targets <44pt → H8 = 2 (accessibility fail)
- No Dark Mode → H8 -1

**Reference:** [Apple HIG](https://developer.apple.com/design/human-interface-guidelines)

#### 4. Product-Specific Multipliers

**Financial/lending products receive 2x penalties:**
- H2 (Simplicity): Pricing transparency mandatory
- H4 (Error Prevention): Safety confirmations required
- H6 (Trust & Safety): Trust indicators NON-NEGOTIABLE
- H10 (Emotional): Empathy critical (rejection, stress)

**Example:**
- Generic app missing trust indicator: H6 = 3 → -1 = **2**
- Lending app missing trust: H6 = 3 → -2 (2x) = **1 (AUTO-FAIL)**

#### 5. Automatic Score Deductions

| Issue | Deduction | Heuristics |
|-------|-----------|------------|
| Cannot read content/copy | **-2** | H2, H6, H9, H10 |
| Financial product, no trust indicators | **-2** (2x) | H6 → AUTO-FAIL |
| Dense forms (>5 fields) | **-1** | H2, H5 |
| No save/exit on multi-step | **-1** | H3 |
| Accessibility unverified | **-1** | H8 |
| Lorem ipsum visible | **-2** | H2, H9 |
| Rejection without empathy | **-2** (2x) | H10 |
| **Header >2 lines (v4.0)** | **-1** | H2 |
| **2 primary CTAs (v4.0)** | **-2** | H2 (CRITICAL) |
| **Body text >5 lines (v4.0)** | **-1** | H2 |
| **Instructions >3 sentences (v4.0)** | **-1** | H9 |
| **Inconsistent typography (v4.0)** | **-1** | H2 |

#### 6. Content Quality = Design Quality (v2.0)

**REQUIREMENT:** Content IS design - must evaluate copy quality

**Checks:**
- Clarity (free of jargon)
- Tone (empathetic in stressful moments)
- Completeness (no lorem ipsum)
- Accuracy (grammar, facts)
- Scannability (short sentences, hierarchy)
- Actionability (clear CTAs)

**Impact:**
- Poor content: H2 **-2**, H6 **-1**, H9 **-2**, H10 **-2**
- Generic copy: H2 **-1**, H10 **-1**

#### 7. Copywriting, Typography & CTA Evaluation (v4.0) ✨ NEW

**MANDATORY:** Evaluate every screen for copywriting quality, typography consistency, and CTA hierarchy.

**Copywriting Length Rules:**
- **Mobile headers:** 1-2 lines max (~40-60 characters)
- **Desktop headers:** 1-2 lines max
- **Body text:** 2-3 lines per paragraph (mobile), 3-4 lines (desktop)
- **Instructions:** 1-2 sentences maximum
- **Character limit:** Text >50 words on mobile = **-2 points** (CRITICAL)

**Typography Consistency Rules:**
- **Same hierarchy = same font size** (e.g., all page titles must be identical size)
- **Mobile font hierarchy:** H1 (28-34pt), H2 (22-24pt), Body (16-18pt), Caption (14-15pt)
- **Inconsistent title sizes:** **-1 point** per occurrence
- **Inconsistent body sizes:** **-0.5 point** per occurrence
- **>3 font sizes on one screen:** **-1 point** (hierarchy confusion)

**CTA Hierarchy Rules (STRICT):**
- **PRIMARY CTA RULE:** One (1) primary CTA per screen maximum
- **Secondary CTA:** 0-1 secondary CTA (ghost/outline button)
- **Tertiary actions:** Text links only (not buttons)
- **2 primary CTAs:** **-2 points** on H2 (CRITICAL - confusing)
- **3+ CTAs total:** **-1 point** (cognitive overload)
- **Vague CTA text:** **-1 point** on H9 (e.g., "Submit", "OK")

**Red Flags:**
- 🚨 Header >2 lines → H2 -1
- 🚨 2 filled buttons (2 primaries) → H2 -2 (CRITICAL)
- 🚨 Body text >5 lines → H2 -1
- 🚨 Instructions >3 sentences → H9 -1
- 🚨 Inconsistent font sizes → H2 -1

**See:** [UX_SCORECARD_v4_COPYWRITING_UPDATE.md](./UX_SCORECARD_v4_COPYWRITING_UPDATE.md)

#### 8. Stricter Accessibility Defaults (v2.0)

**OLD:** Assume accessible until proven otherwise  
**NEW:** Assume fails WCAG until proven

**Cannot verify accessibility = H8 = 2 max**

### 📊 Real-World Impact

Re-evaluation of sample designs with v2.0 and v4.0:

| Product Type | v1.0 Score | v2.0 Score | v4.0 Score | Change | Status |
|--------------|-----------|-----------|------------|---------|--------|
| **Business Onboarding (Project A)** | 3.4 (C+) | 2.5 (C) | 2.0 (C-) | **-1.4 (-41%)** | BLOCKED (3-line headers) |
| **Consumer Lending (Project B)** | 3.6 (B) | 3.4 (C+) | 3.6 (B) | **±0 (0%)** | ✅ PASS (A+ copywriting) |
| **Investment Dashboard (Project C)** | 3.4 (C+) | 3.4 (C+) | 3.7 (B+) | **+0.3 (+9%)** | ✅ PASS (excellent) |
| **Loyalty Rewards (Project D)** | 3.8 (B) | 3.2 (C+) | 3.5 (B) | **-0.3 (-8%)** | ✅ PASS (good copy) |
| **Web Homepage (2026)** | N/A | N/A | 3.8 (B+) | N/A | ✅ PASS (perfect clarity) |

**Key Finding (v4.0):** 
- Projects with **excellent copywriting** (Project B, Project E) score **higher** in v4.0
- Projects with **poor copywriting** (Project A - 3-line headers) score **lower** in v4.0
- v4.0 **rewards quality** and **penalizes violations** accurately

**Learn more**: 
- [UX_SCORECARD_V2_IMPROVEMENTS.md](./UX_SCORECARD_V2_IMPROVEMENTS.md) - v2.0 guide
- [UX_SCORECARD_v4_COPYWRITING_UPDATE.md](./UX_SCORECARD_v4_COPYWRITING_UPDATE.md) - v4.0 copywriting guide

---

## 🎓 Quick Start

### 1. Install the Skill

Copy the `SKILL.md` file to your Claude Code skills directory:

```bash
# Option 1: Link the skill (recommended - auto-updates)
ln -s /path/to/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md

# Option 2: Copy the skill
cp /path/to/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md

# Example with actual path:
# ln -s ~/projects/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md
```

### 2. Basic Usage

```bash
# Upload an image/PDF, then:
"Review this design using /ux-scorecard for Camp 2"

# Or with Figma URL (full file):
"/ux-scorecard https://figma.com/design/ABC123/payment-flow"

# Specific Figma screens (RECOMMENDED for detailed feedback):
"/ux-scorecard https://figma.com/design/ABC123?node-id=123-456,123-789"

# With specific context:
"/ux-scorecard [image] --camp=2 --focus='error prevention and trust indicators'"
```

**💡 Pro Tip:** Provide specific screen URLs (Figma node-ids) for actionable feedback with exact screen references!

## 🎯 Use Cases

### ✅ **Pre-Critique Self-Review**
Run the scorecard before presenting to catch obvious issues.

```bash
"I'm presenting at Design Weekly tomorrow. Run /ux-scorecard on this design."
```

### ✅ **Camp Gate Validation**
Check if design meets Camp 2 (score ≥ 3.0) or Camp 3 (score ≥ 3.5) requirements.

```bash
"/ux-scorecard [design] --camp=2 - Am I ready for Camp 2?"
```

### ✅ **Competitor Benchmarking**
Compare your design against competitors.

```bash
"Compare our payment flow against DBS's using /ux-scorecard"
```

### ✅ **Component Library Audit**
Evaluate reusable components for consistency.

```bash
"/ux-scorecard - Review our button component library"
```

### ✅ **Progress Tracking**
Track score improvements across iterations.

```bash
"Compare this v3 design against v2 (score was 3.2). Show improvement."
```

## 📊 The 11 Heuristics (NEW v2.0)

### **Usability** (5 heuristics)
1. **Visibility of system status** - Users always know what's happening
2. **Simplicity & clarity** - Easy to understand, minimal cognitive load
3. **User control & freedom** - Ability to undo, cancel, exit
4. **Error prevention & recovery** - Validate input, confirm destructive actions
5. **Efficiency of use** - Frequent actions are effortless

### **Trust & Security** (2 heuristics)
6. **Reinforce trust & safety** - Clear security indicators, transparent data handling
7. **Real-time feedback** - Instant notifications on critical events

### **Accessibility** (1 heuristic)
8. **Inclusive design** - Usable by people of all abilities (WCAG 2.1 AA minimum)

### **Onboarding** (1 heuristic)
9. **Easy-to-learn features** - First-time users understand immediately

### **Emotional Reassurance** (1 heuristic)
10. **Delight & confidence building** - Positive reinforcement, empathy in stress

### **Flow Continuity** (1 heuristic) - ✨ NEW
11. **Flow continuity & user journey** - Natural screen-to-screen transitions, context preservation

**Framework Sources:**
- Jakob Nielsen's 10 Usability Heuristics (adapted for financial UX)
- Apple Human Interface Guidelines (iOS)
- Flow Continuity & User Journey Coherence

## 🎓 Scoring Guide (v2.0 STRICT)

| Score | Meaning | Evidence Required | Grade | Ship? |
|-------|---------|-------------------|-------|-------|
| **5** | Excellent - Best-in-class | Multiple concrete examples, zero issues, exceeds industry standards | 4.5-5.0 = **A** | ✅ Ship |
| **4** | Good - Minor polish | Clear evidence of good patterns, only cosmetic improvements | 4.0-4.4 = **B+** <br> 3.5-3.9 = **B** | ✅ Ship |
| **3** | Average - Functional | Basic implementation, 3+ improvements needed | 3.0-3.4 = **C+** <br> 2.5-2.9 = **C** | ⚠️ Conditional |
| **2** | Poor - Major issues | Serious issues OR cannot verify critical features | 2.0-2.4 = **C-** | ❌ Do not ship |
| **1** | Bad - Broken/unsafe | Critical failures, anti-patterns, unusable | 1.5-1.9 = **D** <br> 1.0-1.4 = **F** | ❌ BLOCK |

### ⚠️ Default Scoring When Evidence is Limited

| Cannot Verify | Max Score | Rationale |
|--------------|-----------|-----------|
| Content/copy not readable | **2** | Assume poor until verified |
| Overview/thumbnail only | **2-3** | Cannot assess quality |
| Feature existence unclear | **2** | Assume it doesn't exist |
| Accessibility compliance | **2** | Assume fails WCAG |
| Financial product, no trust indicators | **1-2** | Trust is non-negotiable |

### Score Distribution (Expected)

- **Score 5**: RARE (< 5%) - Best-in-class only
- **Score 4**: Good (15-20%)
- **Score 3**: Default (40-50%) - Most common
- **Score 2**: Serious issues (20-30%)
- **Score 1**: Broken (< 5%)

## ⛺ Camp Gate Requirements (v2.0 STRICT)

### **Camp 1 - Basecamp**
- **Purpose**: Early concepts, exploration
- **Requirement**: No minimum score (focus on concept validation)
- **Fidelity**: Wireframes, rough prototypes OK
- **Content**: Representative (no lorem ipsum)

### **Camp 2 - Weekly Review**
- **Purpose**: Design quality feedback
- **Requirement**: Minimum score **3.0 (C)** to proceed
- **Focus**: Design execution, principles, system usage
- **Must Have**: Readable content, clear user flows
- **Auto-Fail**: None (score-based only)

### **Camp 3 - Spec Review**
- **Purpose**: Final check before shipping
- **Requirement**: Minimum score **3.5 (B)** to ship
- **Focus**: Complete, customer-ready design
- **Must Have**: 
  - Finalized content (no placeholders)
  - Accessibility verified (WCAG 2.1 AA)
  - Usability tested & changes implemented
- **Auto-Fail Criteria**: See below 🚨

### 🚨 Auto-Fail Criteria (Camp 3)

Design **BLOCKED from shipping** regardless of average score if:

1. ❌ **H6 (Trust) ≤ 2** on financial/lending products
2. ❌ **Any heuristic = 1** (broken experience)
3. ❌ **More than 3 heuristics ≤ 2** (too many critical issues)
4. ❌ **Security actions without confirmation** (H4 = 1)
5. ❌ **Lorem ipsum or placeholder content** visible
6. ❌ **Inaccessible to screen readers** (H8 ≤ 1) for public products

**These are non-negotiable safety/trust requirements.**

## 🔧 Advanced Features

### Multi-Evaluator Mode
Get multiple reviewers to score independently, then aggregate:

```bash
"/ux-scorecard [design] --mode=multi --evaluators=3"
```

### Comparison Mode
Side-by-side comparison of two designs:

```bash
"/ux-scorecard --compare [design-v2.png] [design-v3.png]"
```

### Historical Tracking
Track improvements over iterations:

```bash
"/ux-scorecard [design-v3] - Compare against v1 (score 3.0) and v2 (score 3.4)"
```

## 🎯 Best Practices (v2.0)

### For Designers

**✅ DO:**
- Run scorecard BEFORE presenting (catch issues early)
- Fix all critical findings (≤2) before Camp reviews
- **Ensure content is readable** in reviews (no tiny screenshots)
- **Prove quality, don't assume it** (show trust indicators, test accessibility)
- Document trade-offs for lower scores

**❌ DON'T:**
- Present designs with lorem ipsum (auto-low score)
- Assume features exist if not visible (will be scored low)
- Present overviews without readable content (cannot verify quality)
- Ignore accessibility (assume fails until proven)

### For Reviewers/Managers

**✅ DO:**
- Use as coaching tool, not punitive measure
- Set realistic expectations (scores will be lower with v2.0)
- Focus on critical issues (≤2) first
- Run calibration sessions to align team
- **Communicate the change**: Lower scores = more accurate, not worse design

**❌ DON'T:**
- Compare v2.0 scores to v1.0 scores (methodology changed)
- Treat score drops as team performance decline
- Ship designs with auto-fail criteria met

### For Design Ops

**✅ DO:**
- Adopt v2.0 immediately (prevents shipping flawed designs)
- Re-evaluate in-flight projects with v2.0
- Build scored example library for each score level (1-5)
- Track improvements over time (not absolute scores)
- **Prioritize critical fixes**: H6, H4, H8 for financial products

**❌ DON'T:**
- Mix v1.0 and v2.0 scores in analytics
- Use v1.0 baseline to measure v2.0 progress
- Allow financial products to ship with H6 ≤ 2

## 📈 Sample Output

```
╔═══════════════════════════════════════════╗
║  UX SCORECARD RESULTS                     ║
║  Project: Payment Flow Redesign           ║
║  Camp: 2 (Weekly Review)                  ║
╠═══════════════════════════════════════════╣
║  OVERALL SCORE: 3.6 / 5.0                 ║
║  GRADE: B (Good)                          ║
╚═══════════════════════════════════════════╝

CAMP 2 GATE STATUS: ✅ PASS

CRITICAL FINDINGS (Score ≤ 2): None

AREAS FOR IMPROVEMENT (Score = 3):
⚠️  User control & freedom (Score: 3)
   - Missing undo on transaction confirmation
   - Recommendation: Add clear exit points

⚠️  Inclusive design (Score: 3)
   - Color contrast 3.8:1 on secondary buttons
   - Recommendation: Increase to 4.5:1 minimum

STRENGTHS (Score ≥ 4):
✅ Visibility of system status (Score: 4)
✅ Simplicity & clarity (Score: 4)
✅ Real-time feedback (Score: 4)
```

## 🔗 Related Resources

- **Playbook**: `00 Product Design Regional Playbook (1).pdf` (pages 57-60)
- **Template**: UX_Heuristic Scorecard_Template.xlsx
- **Design Critique Guide**: See playbook Design Critique section
- **Camp Review Process**: See playbook Camp Reviews section

## 🚀 Roadmap

### Phase 1 (Current) ✅
- Core skill with PDF/image/Figma support
- 10 heuristics scoring
- Camp readiness assessment

### Phase 2 (Planned)
- Multi-evaluator aggregation
- Historical trend tracking
- Automated issue creation (Jira/Confluence)
- Component library batch scoring

### Phase 3 (Future)
- Team dashboard with aggregate scores
- Predictive scoring based on wireframes
- Integration with design system tools
- AI-suggested design fixes

## 🤝 Contributing

To improve the skill:

1. **Calibration**: Run scoring sessions with team to align interpretation
2. **Examples**: Build library of scored reference designs
3. **Feedback**: Share what works and what doesn't
4. **Iterate**: Update heuristics based on customer feedback

## 📝 Version History

### **v4.0** (June 22, 2026) - COPYWRITING EVALUATION ADDED
**Comprehensive Copywriting, Typography & CTA Best Practices**

**✨ New Features:**
- **Copywriting evaluation:** Headers, body text, instructions length rules
- **Typography consistency:** Same hierarchy = same font size enforcement
- **CTA hierarchy:** Strict 1 primary CTA per screen rule
- **Automatic penalties:** -1 to -2 points for violations
- **Platform-specific rules:** Mobile vs desktop copywriting standards
- **Example-driven:** Before/after recommendations with real project examples

**📊 Real Impact:**
- Project A Onboarding: 2.5 → 2.0 (-0.5, 3-line headers penalty)
- Project B: 3.4 → 3.6 (+0.2, A+ copywriting rewarded)
- Project C: 3.4 → 3.7 (+0.3, excellent information design)
- Project D: 3.2 → 3.5 (+0.3, energetic tone recognized)
- Project E Homepage: NEW → 3.8 (B+, perfect clarity)

**📚 Documentation:**
- [UX_SCORECARD_v4_COPYWRITING_UPDATE.md](./UX_SCORECARD_v4_COPYWRITING_UPDATE.md) - Complete v4.0 copywriting guide
- [SKILL.md](./SKILL.md) - Updated skill with copywriting rules

**Key Insight:** v4.0 **rewards excellent copywriting** and **penalizes violations**. Projects with clear, concise copy score higher. Projects with verbose, inconsistent copy score lower.

---

### **v2.0** (June 22, 2026) - MAJOR BREAKING CHANGE
**Strict Scoring Methodology Overhaul**

**🚨 Breaking Changes:**
- Scores drop 0.4-1.4 points on average (-11% to -39%)
- "Guilty until proven innocent" philosophy
- Auto-fail criteria introduced (blocks shipping)
- Score 5 now RARE (< 5% of scores)

**✨ New Features:**
- H11: Flow Continuity heuristic (screen-to-screen journey)
- Apple HIG integration (iOS compliance checks)
- Auto-fail criteria (H6 ≤ 2 on financial, etc.)
- Automatic deductions table (12+ instant penalties)
- Product-specific multipliers (financial/healthcare 2x stricter)
- Content quality assessment (mandatory copy evaluation)
- Strict accessibility defaults (assume fails WCAG until proven)

**📊 Real Impact:**
- Business Onboarding Flow: 3.4 → 2.5 (-0.9, BLOCKED)
- Consumer Lending App: 3.6 → 2.2 (-1.4, BLOCKED)  
- Loyalty Rewards System: 3.8 → 3.4 (-0.4, conditional)

**📚 Documentation:**
- [UX_SCORECARD_V2_IMPROVEMENTS.md](./UX_SCORECARD_V2_IMPROVEMENTS.md) - Complete v2.0 guide
- [SKILL.md](./SKILL.md) - Updated skill with all new rules

**Migration:** Re-evaluate all in-flight designs with v2.0

---

### **v1.0** (June 19, 2026) - Initial release
- 10 UX heuristics framework
- PDF/image/Figma support
- Camp gate validation
- Detailed scoring and recommendations
- Universal auto-detection engine

**⚠️ Deprecated:** v1.0 scoring was too lenient - use v2.0

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

Ways to contribute:
- 🐛 Report bugs
- ✨ Request features
- 📝 Improve documentation
- 🔧 Submit pull requests
- 💡 Share usage examples

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

## 📞 Support

- **Documentation**: Full guides in this repository
- **Issues**: [GitHub Issues](https://github.com/YOUR-ORG/uxscorecard/issues)
- **Discussions**: [GitHub Discussions](https://github.com/YOUR-ORG/uxscorecard/discussions)

## 🙏 Acknowledgments

- **Framework Source**: Based on industry-standard UX heuristics and design evaluation best practices
- **Built with**: Claude Code
- **Contributors**: See [CONTRIBUTING.md](./CONTRIBUTING.md)

## 📖 Framework Background

This skill implements a 10-heuristic UX evaluation framework covering:
- **Usability** (5 heuristics)
- **Trust & Security** (2 heuristics)
- **Accessibility** (1 heuristic)
- **Onboarding** (1 heuristic)
- **Emotional Reassurance** (1 heuristic)

The framework is documented in detail in [SKILL.md](./SKILL.md).

### 🆕 Version 4.0 Documentation

**Core v4.0 Documentation**:
- [UX_SCORECARD_v4_COPYWRITING_UPDATE.md](./UX_SCORECARD_v4_COPYWRITING_UPDATE.md) - **NEW** - Complete v4.0 copywriting guide
- [SKILL.md](./SKILL.md) - Updated skill with copywriting/typography/CTA rules

**Core v2.0 Documentation**:
- [UX_SCORECARD_V2_IMPROVEMENTS.md](./UX_SCORECARD_V2_IMPROVEMENTS.md) - Complete v2.0 guide (strict scoring)
- [SKILL.md](./SKILL.md) - Strict scoring rules, auto-fail criteria, HIG integration

**v1.0 Auto-Detection System (Deprecated)**:
- [AUTO_DETECTION_ENGINE.md](./AUTO_DETECTION_ENGINE.md) - Detection algorithm (v1.0 only)
- [DETECTION_PATTERN_LIBRARY.md](./DETECTION_PATTERN_LIBRARY.md) - Product types (v1.0 only)
- [CONFIDENCE_CALIBRATION.md](./CONFIDENCE_CALIBRATION.md) - Calibration system (v1.0 only)
- [VISUAL_DETECTION_GUIDE.md](./VISUAL_DETECTION_GUIDE.md) - Visual analysis guide

**Note:** v2.0 uses product-specific multipliers instead of auto-detection weights. v4.0 adds copywriting evaluation.

## ⭐ Star Us!

If you find this skill useful, please star the repository to help others discover it!

---

**Made with ❤️ by Rthian** | [View on GitHub](https://github.com/YOUR-ORG/uxscorecard)
