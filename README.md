# UX Scorecard - Design Grading & Review Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-4.0.0-blue.svg)](https://github.com/rthian/ux-scorecard/releases)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-compatible-brightgreen.svg)](https://claude.ai/code)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

A comprehensive design evaluation skill using the **UX Heuristics framework** for Claude Code. Evaluate designs against 11 UX heuristics with **strict, realistic scoring** that catches critical issues before shipping.

**⭐ v4.0 Features:** Strict scoring • Auto-fail criteria • Flow continuity • iOS HIG compliance • Copywriting evaluation • Financial product multipliers

---

## 🚀 Quick Start

### Installation

```bash
mkdir -p ~/.claude/skills/ux-scorecard
ln -sf ~/Downloads/ux-scorecard/SKILL.md ~/.claude/skills/ux-scorecard/SKILL.md
```

### Common Usage Examples

```bash
# Simple review
review this with /ux-scorecard https://figma.com/design/ABC123/project

# Multiple screens (recommended for detailed feedback)
review this with /ux-scorecard https://figma.com/design/ABC123?node-id=1-123,1-456

# Uploaded image/PDF
review this with /ux-scorecard --camp=3

# With specific focus
review this with /ux-scorecard https://figma.com/design/ABC123 --focus="copywriting and CTA hierarchy"

# Camp gate check
Is this design ready for Camp 3? /ux-scorecard https://figma.com/design/ABC123

# Compare two designs
review this with /ux-scorecard --compare design-v1.png design-v2.png
```

---

## 🎯 What You Get

Every evaluation includes:

- **📊 Overall Score:** 1-5 scale with grade badge (A, B+, B, C+, C, C-, D, F)
- **✅ Pass/Fail Verdict:** Camp 2 (≥3.0) or Camp 3 (≥3.5) readiness
- **🔍 11 Heuristic Scores:** Detailed breakdown with evidence
- **📍 Screen-Specific Findings:** Exact Figma links to problem areas
- **⚠️ Auto-Fail Blocking:** Critical safety/trust issues prevent shipping
- **💡 Actionable Recommendations:** Prioritized by severity (Critical → Medium → Low)
- **✍️ Copywriting Analysis:** Headers, body text, CTAs evaluated automatically
- **🍎 iOS HIG Compliance:** For mobile apps (touch targets, Dark Mode, etc.)

---

## 🆕 What's New in v4.0

### Copywriting, Typography & CTA Evaluation

**Now evaluates:**
- **Headers:** 1-2 lines max (mobile) → **-1 point penalty** if >2 lines
- **Body text:** 2-3 lines per paragraph → **-1 point** if >5 lines
- **CTA hierarchy:** 1 primary CTA per screen → **-2 points** if 2 primary CTAs (CRITICAL)
- **Typography:** Consistent sizing → **-1 point** if inconsistent

**Example:**
```
❌ "Power up your biz with easy financing and flexi repayments" (3 lines)
   → H2 -1 point penalty

✅ "Get financing in minutes" (1 line)
   → PASS
```

**Real Impact:**
- Project A (poor copywriting): 2.5 → 2.0 (-0.5 points) ❌
- Project B (excellent copywriting): 3.4 → 3.6 (+0.2 points) ✅

---

## 📊 The 11 Heuristics

1. **H1: Visibility of system status** - Users know what's happening
2. **H2: Simplicity & clarity** - Easy to understand, minimal cognitive load
3. **H3: User control & freedom** - Ability to undo, cancel, exit
4. **H4: Error prevention & recovery** - Validate input, clear error messages
5. **H5: Efficiency of use** - Frequent actions are effortless
6. **H6: Reinforce trust & safety** - Security indicators, transparent data handling
7. **H7: Real-time feedback** - Instant notifications on critical events
8. **H8: Inclusive design** - Accessible to people of all abilities
9. **H9: Easy-to-learn features** - First-time users understand immediately
10. **H10: Delight & confidence building** - Positive reinforcement, empathy
11. **H11: Flow continuity** ✨ NEW - Seamless screen-to-screen journey

**Scoring:** 1 (Bad) → 2 (Poor) → 3 (Average) → 4 (Good) → 5 (Excellent)

---

## 🎯 Camp Gate Requirements

| Camp | Minimum Score | Requirements | Focus |
|------|---------------|--------------|-------|
| **Camp 1** | No minimum | Concept validation | Wireframes, rough prototypes OK |
| **Camp 2** | **≥ 3.0 (C)** | Design quality | On-device prototype, representative content |
| **Camp 3** | **≥ 3.5 (B)** | Ship-ready | Finalized content, usability tested, no lorem ipsum |

**Auto-Fail Criteria (Camp 3):**
- H6 (Trust) ≤ 2 on financial products → **BLOCKED**
- Any heuristic = 1 → **BLOCKED**
- 3+ heuristics ≤ 2 → **BLOCKED**
- Lorem ipsum visible → **BLOCKED**

---

## 💡 Best Practices

### For Designers

✅ **DO:**
- Run scorecard BEFORE presenting to team
- Provide specific Figma node-ids for detailed feedback
- Fix all CRITICAL findings (score ≤ 2) immediately
- Ensure content is readable (no tiny screenshots)

❌ **DON'T:**
- Present designs with lorem ipsum
- Assume features exist if not visible
- Present overviews without readable content

### For Reviewers

✅ **DO:**
- Use as coaching tool, not punishment
- Focus on CRITICAL issues (≤2) first
- Run calibration sessions to align team

❌ **DON'T:**
- Compare v4.0 scores to v1.0 (methodology changed)
- Ship designs with auto-fail criteria

---

## 🔌 MCP Integration: Design Review Workflows

### Option 1: Obsidian + UX Scorecard

**Use case:** Store design reviews as markdown notes, link to Figma, track improvements over time.

**Setup:**
1. Install [Obsidian MCP Server](https://github.com/calclavia/mcp-obsidian)
2. Configure vault path in Claude Code
3. Create reviews directly in Obsidian

**Workflow:**
```bash
# 1. Review design
review this with /ux-scorecard https://figma.com/design/ABC123

# 2. Save report to Obsidian
save this report to Obsidian vault "Design Reviews/Project-X-v2-scorecard.md"

# 3. Link to project note
add link to "Projects/Project-X.md"
```

**Benefits:**
- 📝 Searchable design review archive
- 🔗 Link reviews to project notes, meeting notes, PRDs
- 📊 Track score improvements: v1 (3.2) → v2 (3.5) → v3 (3.8)
- 🏷️ Tag by project, camp stage, reviewer
- 📅 Timeline view of design evolution

**Recommended Obsidian Structure:**
```
Design Reviews/
├── 2026-06/
│   ├── Project-X-v1-scorecard.md (Score: 3.2)
│   ├── Project-X-v2-scorecard.md (Score: 3.5)
│   └── Project-X-v3-scorecard.md (Score: 3.8)
├── Templates/
│   └── ux-scorecard-template.md
└── Camp-3-Ready/
    └── approved-designs.md
```

---

### Option 2: Notion + UX Scorecard

**Use case:** Centralized design review database, team collaboration, stakeholder visibility.

**Setup:**
1. Install [Notion MCP Server](https://github.com/ryanmearns/notion-mcp)
2. Connect to your Notion workspace
3. Create "Design Reviews" database

**Workflow:**
```bash
# 1. Review design
review this with /ux-scorecard https://figma.com/design/ABC123

# 2. Save to Notion database
create Notion page in "Design Reviews" with this scorecard

# 3. Auto-fill properties
- Score: 3.6
- Grade: B
- Camp: Camp 3
- Status: ✅ PASS
- Project: Project X
- Reviewer: [Your name]
- Date: 2026-06-23
```

**Benefits:**
- 🗄️ Centralized team dashboard
- 📊 Filter by score, camp, project, date
- 👥 Team collaboration (comments, mentions)
- 📈 Notion charts (average scores, pass rate)
- 🔔 Notify stakeholders when reviews complete
- 📱 Mobile access for PMs/stakeholders

**Recommended Notion Database:**

| Name | Score | Grade | Camp | Status | Project | Date | Figma Link |
|------|-------|-------|------|--------|---------|------|------------|
| Project X v3 | 3.8 | B+ | Camp 3 | ✅ PASS | Project X | 2026-06-23 | [Link] |
| Project Y v1 | 2.0 | C- | Camp 2 | ❌ FAIL | Project Y | 2026-06-22 | [Link] |

---

### Option 3: Both! (Recommended)

**Workflow:**
1. **Obsidian:** Personal working notes, detailed analysis
2. **Notion:** Team dashboard, stakeholder reports

```bash
# Dual save
review this with /ux-scorecard https://figma.com/design/ABC123

save detailed report to Obsidian "Design Reviews/Project-X-v2-full.md"
save summary to Notion "Design Reviews" database
```

---

## 📋 Sample Output

```
╔═══════════════════════════════════════════╗
║  UX SCORECARD RESULTS v4.0                ║
║  Project: Payment Flow Redesign           ║
║  Platform: Mobile (iOS)                   ║
║  Camp: 3 (Spec Review)                    ║
╠═══════════════════════════════════════════╣
║  OVERALL SCORE: 3.6 / 5.0                 ║
║  GRADE: B (Good)                          ║
║  CAMP 3 STATUS: ✅ PASS                   ║
╚═══════════════════════════════════════════╝

HEURISTIC BREAKDOWN:
⭐ H1: Visibility of system status        │ 5 │ PERFECT
✅ H2: Simplicity & clarity               │ 4 │ GOOD
⚠️  H3: User control & freedom            │ 3 │ (Add cancel button)
✅ H4: Error prevention & recovery        │ 4 │ GOOD
✅ H5: Efficiency of use                  │ 5 │ PERFECT
✅ H6: Reinforce trust & safety           │ 4 │ GOOD
⭐ H7: Real-time feedback                 │ 5 │ PERFECT
⚠️  H8: Inclusive design                  │ 3 │ (Cannot verify accessibility)
⭐ H9: Easy-to-learn features             │ 5 │ PERFECT
✅ H10: Delight & confidence building     │ 4 │ GOOD
⭐ H11: Flow continuity                   │ 5 │ PERFECT

CRITICAL FINDINGS: None ✅

AREAS FOR IMPROVEMENT:
⚠️  H3: User control & freedom (Score: 3)
   📍 Screen: Confirmation | 🔗 https://figma.com/design/ABC?node-id=123-456
   - Issue: No cancel button visible
   - Recommendation: Add "Cancel" button (ghost/outline) below primary CTA

STRENGTHS:
✅ H1, H7, H9, H11 score PERFECT (5/5)
✅ Copywriting Grade: A (1-line headers, clear CTAs)
✅ Flow continuity is seamless
```

---

## 🎓 Scoring Guide

| Score | Grade | Ship? | Typical Issues |
|-------|-------|-------|----------------|
| **4.5-5.0** | A | ✅ Ship now | Best-in-class, minor polish only |
| **4.0-4.4** | B+ | ✅ Ship now | Strong usability, 1-2 improvements |
| **3.5-3.9** | B | ✅ Ship | Meets expectations, plan iteration |
| **3.0-3.4** | C+ | ⚠️ Conditional | Fix HIGH issues first |
| **2.5-2.9** | C | ❌ Do not ship | Major rework needed |
| **2.0-2.4** | C- | ❌ Do not ship | Redesign required |
| **<2.0** | D-F | ❌ BLOCK | Fundamentally broken |

**Strict Philosophy:** Default to LOWER scores when evidence is insufficient. Assume issues exist until proven otherwise.

---

## 🚨 Auto-Fail Criteria

Designs are **BLOCKED** regardless of average score if:

1. **Financial product without trust indicators** (H6 ≤ 2)
2. **Security actions without confirmation** (H4 = 1)
3. **Any heuristic = 1** in Camp 3
4. **More than 3 heuristics ≤ 2** in Camp 3
5. **Lorem ipsum visible** in Camp 3

---

## 📈 Real-World Impact

v4.0 Re-evaluation Results:

| Project | v2.0 | v4.0 | Change | Reason |
|---------|------|------|--------|--------|
| Project A | 2.5 (C) | 2.0 (C-) | **-0.5** | 3-line headers penalized |
| Project B | 3.4 (C+) | 3.6 (B) | **+0.2** | A+ copywriting rewarded |
| Project C | 3.4 (C+) | 3.7 (B+) | **+0.3** | Excellent design verified |
| Project D | 3.2 (C+) | 3.5 (B) | **+0.3** | Good copy recognized |
| Project E | N/A | 3.8 (B+) | NEW | Perfect clarity |

**Key Finding:** v4.0 rewards excellent copywriting and penalizes violations accurately.

---

## 🛠️ Advanced Features

### Multi-Evaluator Mode
```bash
review this with /ux-scorecard --mode=multi --evaluators=3
```

### Historical Tracking
```bash
review this with /ux-scorecard https://figma.com/design/ABC
# Compare against: v1 (3.2), v2 (3.5)
```

### Competitor Benchmarking
```bash
review this with /ux-scorecard --compare our-design.png competitor-design.png
```

---

## 📚 Documentation

- **[SKILL.md](./SKILL.md)** - Complete heuristics framework and scoring rules
- **[UX_SCORECARD_v4_COPYWRITING_UPDATE.md](./UX_SCORECARD_v4_COPYWRITING_UPDATE.md)** - v4.0 copywriting guide
- **[UX_SCORECARD_V2_IMPROVEMENTS.md](./UX_SCORECARD_V2_IMPROVEMENTS.md)** - v2.0 strict scoring methodology
- **[CHANGELOG.md](./CHANGELOG.md)** - Version history
- **[CONTRIBUTING.md](./CONTRIBUTING.md)** - How to contribute

---

## 🤝 Contributing

We welcome contributions!

- 🐛 [Report bugs](https://github.com/rthian/ux-scorecard/issues)
- ✨ [Request features](https://github.com/rthian/ux-scorecard/issues)
- 📝 Improve documentation
- 🔧 Submit pull requests
- 💡 Share usage examples

---

## 📜 License

MIT License - see [LICENSE](./LICENSE) file for details.

---

## 🙏 Acknowledgments

**Framework Source:** Based on industry-standard UX heuristics and design evaluation best practices

---

**Made with ❤️ by Rthian** | [View on GitHub](https://github.com/rthian/ux-scorecard)
