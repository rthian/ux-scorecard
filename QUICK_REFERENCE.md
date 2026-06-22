# UX Scorecard - Quick Reference Card

**One-page cheat sheet for the UX Scorecard skill**

---

## ⚡ Quick Invocation

```bash
# Basic usage
/ux-scorecard [upload PDF/image] --camp=[1|2|3]

# With Figma
/ux-scorecard https://figma.com/file/ABC123

# With context
/ux-scorecard [upload] --focus="error handling, trust indicators"

# Comparison
/ux-scorecard --compare [design1] [design2]
```

---

## 📊 10 Heuristics at a Glance

| # | Category | Heuristic | Key Question |
|---|----------|-----------|--------------|
| **H1** | Usability | **System Status Visibility** | Do users know what's happening? |
| **H2** | Usability | **Simplicity & Clarity** | Is it easy to understand? |
| **H3** | Usability | **User Control & Freedom** | Can users undo/cancel? |
| **H4** | Usability | **Error Prevention** | Are errors prevented/handled well? |
| **H5** | Usability | **Efficiency of Use** | Are common tasks effortless? |
| **H6** | Trust | **Trust & Safety** | Do users feel secure? |
| **H7** | Trust | **Real-time Feedback** | Are users notified instantly? |
| **H8** | Accessibility | **Inclusive Design** | Usable by all abilities? |
| **H9** | Onboarding | **Easy-to-Learn** | Can new users learn quickly? |
| **H10** | Emotion | **Delight** | Does it build confidence? |

---

## 🎯 Scoring Scale

| Score | Meaning | When to Use |
|-------|---------|-------------|
| **5** | Excellent - Fully optimized | Best-in-class, nothing to improve |
| **4** | Good - Minor concerns | Works well, small tweaks possible |
| **3** | Average - Some issues | Functional but noticeable friction |
| **2** | Poor - Significant friction | Users struggle, major fixes needed |
| **1** | Bad - Broken experience | Unusable, critical issues |

---

## 🏆 Badge Levels

| Score Range | Badge | Summary | Ship? |
|-------------|-------|---------|-------|
| 4.5 - 5.0 | **A** | Excellent | ✅ Ship |
| 4.0 - 4.4 | **B+** | Very Good | ✅ Ship |
| 3.5 - 3.9 | **B** | Good | ✅ Ship (Camp 3+) |
| 3.0 - 3.4 | **C+** | Above Average | ⚠️ Iterate (Camp 2+) |
| 2.5 - 2.9 | **C** | Average | ⚠️ Iterate |
| 2.0 - 2.4 | **C-** | Below Average | ❌ Major rework |
| 1.5 - 1.9 | **D** | Poor | ❌ Redesign |
| 1.0 - 1.4 | **F** | Bad | ❌ Start over |

---

## ⛺ Camp Gate Requirements

| Camp | Purpose | Min Score | Requirements |
|------|---------|-----------|--------------|
| **Camp 1** | Discovery | No minimum | Multiple concepts, rough fidelity |
| **Camp 2** | Weekly Review | **≥ 3.0 (C)** | One mature concept, device prototype |
| **Camp 3** | Spec Review | **≥ 3.5 (B)** | Complete, finalized, tested, ready to ship |

---

## 🎯 Common Use Cases

### ✅ Pre-Critique Self-Review
```bash
"Review this design before Design Weekly - /ux-scorecard"
```

### ✅ Camp Gate Check
```bash
"/ux-scorecard [design] --camp=2 - Am I ready?"
```

### ✅ Competitor Benchmark
```bash
"Compare our flow vs [competitor] using /ux-scorecard"
```

### ✅ Component Library Audit
```bash
"/ux-scorecard - Review our button component library"
```

### ✅ Progress Tracking
```bash
"/ux-scorecard [v3] - Compare vs v2 (score was 3.2)"
```

---

## 🚨 What to Focus On

### Critical (Fix Immediately) ❌
- **Any heuristic scoring ≤ 2**
- Security/trust issues (H6, H7)
- Accessibility violations (H8)
- Blocking user errors (H4)

### Important (Fix Before Ship) ⚠️
- **Heuristics scoring = 3**
- User control issues (H3)
- Efficiency problems (H5)
- Onboarding friction (H9)

### Nice to Have (Iterate) ✨
- **Heuristics scoring = 4**
- Delight improvements (H10)
- Advanced features
- Edge case handling

---

## 📋 Typical Score Ranges by Design Type

| Design Type | Expected Score |
|-------------|----------------|
| Early concept (Camp 1) | 2.5 - 3.5 |
| Mature design (Camp 2) | 3.0 - 4.0 |
| Ship-ready (Camp 3) | 3.5 - 4.5 |
| Polished product | 4.0 - 5.0 |
| Component library | 3.5 - 4.5 |
| Competitor benchmark | 3.0 - 4.5 |

---

## 🔍 Red Flags (Score ≤ 2)

If any heuristic scores ≤ 2, **STOP** and fix immediately:

| Heuristic | Red Flag | Fix |
|-----------|----------|-----|
| **H1** | No loading states, unclear status | Add progress indicators |
| **H2** | Confusing UI, jargon everywhere | Simplify, remove jargon |
| **H3** | Can't undo/cancel actions | Add exit points |
| **H4** | Errors crash or confuse users | Better validation, error messages |
| **H5** | Common tasks require many steps | Streamline, add shortcuts |
| **H6** | Users don't trust security | Add security indicators |
| **H7** | No confirmation feedback | Add instant notifications |
| **H8** | Not accessible | Fix contrast, add labels |
| **H9** | New users are lost | Add onboarding, tooltips |
| **H10** | Stressful, frustrating experience | Add reassurance, delight |

---

## 🎓 Scoring Guidelines

### When in doubt:

- **Score 5**: Best-in-class, better than competitors
- **Score 4**: Better than average, minor issues only
- **Score 3**: Meets expectations, noticeable friction
- **Score 2**: Below expectations, users struggle
- **Score 1**: Fails to meet heuristic, broken

### Avoid common mistakes:

- ❌ Don't score too high just because "it works"
- ❌ Don't score too low just because it's not perfect
- ❌ Don't average all heuristics at 3 (be opinionated!)
- ✅ DO compare against competitors
- ✅ DO consider your specific users (low digital literacy, etc.)
- ✅ DO be consistent across reviews

---

## 🔄 Iteration Pattern

### 1. First Review
- Run /ux-scorecard
- Identify all score ≤ 2 (critical)
- Fix critical issues first

### 2. Second Review
- Re-run /ux-scorecard
- Check if critical issues are fixed
- Address score = 3 (improvement areas)

### 3. Third Review
- Re-run /ux-scorecard
- Verify score meets Camp gate requirement
- Polish score = 4 if time allows

### 4. Final Check
- Run one last /ux-scorecard before ship
- Verify ≥ 3.5 for Camp 3
- Document any known limitations

---

## 🎯 Target Scores by Role

### For Designers:
- **Camp 1**: 2.5+ (concept validation)
- **Camp 2**: 3.0+ (quality check)
- **Camp 3**: 3.5+ (ship-ready)
- **Ideal**: 4.0+ (delightful)

### For Design Managers:
- **Team Average**: ≥ 3.5
- **Component Library**: ≥ 4.0
- **New Designers**: 3.0+ (coaching opportunity)
- **Senior Designers**: 4.0+ (role model)

### For Design Ops:
- **Standard**: All Camp 3 ≥ 3.5
- **Stretch Goal**: Team average ≥ 4.0
- **Component Library**: All components ≥ 4.0
- **Competitor Benchmark**: Meet or exceed competitor scores

---

## 💡 Pro Tips

1. **Run early, run often** - Don't wait for Camp reviews
2. **Fix critical first** - Score ≤ 2 before anything else
3. **Multi-evaluator** - Get 2-3 people to score critical projects
4. **Track trends** - Monitor your scores over time
5. **Learn patterns** - Notice which heuristics you commonly miss
6. **Context matters** - Some heuristics may not apply to all flows
7. **Compare competitors** - Benchmark against best-in-class
8. **Document trade-offs** - Explain why certain scores are lower
9. **Celebrate wins** - Share high scores with team
10. **Use for coaching** - Help junior designers improve

---

## 📞 Quick Help

| Issue | Solution |
|-------|----------|
| Skill not found | `ls ~/.claude/skills/ux-scorecard.md` |
| Can't read PDF | Try smaller PDF or use images |
| Figma not working | Check `$FIGMA_ACCESS_TOKEN` |
| Scores too low | Get multi-evaluator review |
| Scores too high | Compare against competitors |
| Unsure how to score | See USAGE_EXAMPLES.md |

---

## 🔗 Full Documentation

- **README.md** - Overview and introduction
- **SKILL.md** - Complete skill specification
- **USAGE_EXAMPLES.md** - Detailed usage examples with outputs
- **INSTALLATION.md** - Installation and setup guide
- **SCORECARD_TEMPLATE.md** - Manual scoring template

---

**Print this card and keep it at your desk!** 📌

For questions, contact Design Ops or Regional Design Team.

---

**Version**: 1.0 | **Last Updated**: June 19, 2026
