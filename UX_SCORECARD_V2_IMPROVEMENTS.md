# UX Scorecard v2.0 - Improvements Summary

**Updated:** June 22, 2026  
**Author:** Claude  
**Purpose:** Document stricter scoring methodology and new features

---

## 🎯 Core Problem Solved

**Before:** All designs scoring 3.0-3.6 (C+ to B) with insufficient differentiation  
**After:** Wider score distribution with stricter defaults and clear fail criteria

---

## 🚨 Major Changes

### 1. **"Guilty Until Proven Innocent" Scoring Philosophy**

**OLD APPROACH:** Assume designs are good unless problems are visible  
**NEW APPROACH:** Assume issues exist until proven otherwise

| Scenario | Old Score | New Score | Rationale |
|----------|-----------|-----------|-----------|
| Cannot see content/copy | 3-4 | **2** | Assume poor copy |
| Overview only (no detail) | 3-4 | **2-3** | Cannot assess quality |
| Unclear if feature exists | 3 | **2** | Assume it doesn't |
| Financial product without trust indicators | 3 | **1-2** (AUTO-FAIL) | Trust is non-negotiable |
| Cannot verify accessibility | 3 | **2** | Assume fails WCAG |
| No interactive prototype | 3-4 | **Cap at 3** | Cannot verify UX |

---

### 2. **Automatic Score Deductions**

New penalty system that auto-applies when issues are detected:

| Issue | Deduction | Heuristics | Notes |
|-------|-----------|------------|-------|
| Cannot read content/copy | **-2** | H2, H6, H9, H10 | Words ARE the UX |
| Financial product, no trust indicators | **-2** | H6 | AUTO-FAIL if H6 ≤ 2 |
| No visible error states | **-1** | H4 | Must show handling |
| Dense forms (>5 fields) | **-1** | H2, H5 | Cognitive overload |
| Lorem ipsum visible | **-2** | H2, H9 | Content incomplete |
| No multi-language support | **-1** | H8 | English-only excludes users |
| Rejection screens without empathy | **-2** | H10 | Emotional failure |
| No save/exit on multi-step | **-1** | H3 | Must allow pausing |

---

### 3. **Product-Specific Multipliers**

Some products require higher standards:

| Product Type | Penalty Multiplier | Heuristics |
|--------------|-------------------|------------|
| **Financial** (loans, payments) | **2x** | H6 (Trust), H4 (Error), H10 (Emotion) |
| **Healthcare** | **2x** | H6, H4, H8 |
| **E-commerce checkout** | **1.5x** | H6, H4 |
| **Onboarding/signup** | **1.5x** | H9, H10 |

**Example:**  
- Generic app with missing trust indicator: H6 = 3 → deduct -1 → **H6 = 2**  
- Financial app with same issue: H6 = 3 → deduct **-2** (2x multiplier) → **H6 = 1 (AUTO-FAIL)**

---

### 4. **Auto-Fail Criteria**

Design **immediately FAILS** regardless of overall score if:

1. ❌ **Security-critical actions without confirmation** (H4 = 1)
2. ❌ **Financial product without trust indicators** (H6 ≤ 2)
3. ❌ **Inaccessible to screen readers** (H8 ≤ 1)
4. ❌ **Poor visible content** (lorem ipsum) in Camp 3
5. ❌ **Any heuristic scores 1** in Camp 3 review
6. ❌ **More than 3 heuristics ≤ 2** in Camp 3

**This ensures critical safety/trust issues block shipping even if overall score is passing.**

---

### 5. **New Feature: Flow Continuity Heuristic (H11)**

Added **11th heuristic** to evaluate screen-to-screen user journey:

**Evaluates:**
- Does journey feel natural and logical?
- Are transitions smooth?
- Does context carry forward?
- Can users understand progression?
- Any dead ends or confusing navigation?
- Does flow match user mental models?

**Flow Red Flags:**
- 🚨 Data entered earlier not pre-filled later
- 🚨 Sudden context switches
- 🚨 Back button leads to unexpected screen
- 🚨 Users must remember info from previous screens
- 🚨 Progress resets unexpectedly
- 🚨 Navigation hierarchy unclear
- 🚨 Dead ends with no next action

**This directly addresses your feedback: "evaluate how the content flows in each screen as a user"**

---

### 6. **Apple Human Interface Guidelines (HIG) Integration**

New iOS-specific evaluation layer:

**Checks for:**
- ✅ Native iOS UI patterns (not Android Material Design)
- ✅ Bottom tab bar for main navigation
- ✅ SF Symbols usage
- ✅ Dynamic Type support (text scales)
- ✅ Safe area respect (no content behind notch)
- ✅ Standard iOS gestures (swipe back, pull to refresh)
- ✅ Touch targets ≥ 44pt
- ✅ Light and Dark mode support

**HIG Scoring Impact:**

| HIG Compliance | Score Adjustment |
|----------------|------------------|
| Fully compliant | **+0.5** to H2, H9 |
| Mostly compliant | No change |
| Major violations (e.g., Material on iOS) | **-1** to H2, H9 |
| Platform-inappropriate patterns | **H9 = 2 max** |

**HIG Red Flags:**
- 🚨 Material Design on iOS → H2 = 2, H9 = 2
- 🚨 Hamburger menu instead of tab bar → H5 -1
- 🚨 Touch targets < 44pt → H8 = 2 (auto-fail accessibility)
- 🚨 No Dark Mode → H8 -1
- 🚨 Text doesn't scale → H8 = 2
- 🚨 Content behind safe areas → H2 -1

**Reference:** https://developer.apple.com/design/human-interface-guidelines

---

### 7. **Content Quality Assessment (MANDATORY)**

**New requirement:** Content IS design - must evaluate copy quality.

**Checks:**
1. **Clarity** - Free of jargon
2. **Tone** - Appropriate for context (empathetic in stressful moments)
3. **Completeness** - No placeholder text
4. **Accuracy** - Correct grammar, spelling, facts
5. **Scannability** - Short sentences, clear hierarchy
6. **Actionability** - CTAs are clear

**Content Scoring Impact:**

| Content Quality | Heuristic Impact |
|-----------------|------------------|
| Poor/missing | H2 **-2**, H6 **-1**, H9 **-2**, H10 **-2** |
| Generic/template | H2 **-1**, H10 **-1** |
| Good but unpolished | H2 **-0.5** |
| Excellent | Can boost **+0.5** |

---

### 8. **Revised Badge Levels with Ship Guidance**

Added **ship/no-ship guidance** to each grade:

| Score | Badge | Ship? | Action Required |
|-------|-------|-------|----------------|
| 4.5-5.0 | **A** | ✅ Ship | None - best in class |
| 4.0-4.4 | **B+** | ✅ Ship | Minor polish only |
| 3.5-3.9 | **B** | ⚠️ Conditional | Ship with iteration plan |
| 3.0-3.4 | **C+** | ⚠️ Conditional | Fix HIGH issues first |
| 2.5-2.9 | **C** | ❌ No ship | Major rework needed |
| 2.0-2.4 | **C-** | ❌ No ship | Redesign required |
| 1.5-1.9 | **D** | ❌ BLOCK | Complete redesign |
| 1.0-1.4 | **F** | ❌ BLOCK | Start over |

---

### 9. **Expected Score Distribution**

To prevent grade inflation:

| Project Quality | Avg Score | Distribution |
|----------------|-----------|--------------|
| Excellent | 3.8-4.2 | Mostly 4s and 3s, few 5s |
| Good | 3.2-3.7 | Mix of 4s and 3s, some 2s |
| Average | 2.5-3.1 | Mostly 3s and 2s |
| Poor | 1.8-2.4 | Mostly 2s and 1s |

**Individual Score Rarity:**
- **Score 5**: RARE (< 5% of all scores) - best-in-class only
- **Score 4**: Good work (15-20%)
- **Score 3**: Functional, default (40-50%) ← most common
- **Score 2**: Serious issues (20-30%)
- **Score 1**: Broken/unsafe (< 5%, critical when present)

**If you're scoring everything 3.5-4.5, you're being too lenient.**

---

## 📊 Before & After Example: GX Cashloan

### OLD SCORING (v1.0 - Lenient)

| Heuristic | Old Score | Rationale |
|-----------|-----------|-----------|
| H2: Simplicity | 4 | "Clean application flow" |
| H6: Trust & Safety | 3 | "Could use more security messaging" |
| H8: Inclusive Design | 3 | "Cannot verify accessibility" |
| H10: Emotional | 3 | "Could use more reassurance" |
| **Overall** | **3.6 (B)** | ✅ Pass Camp 3 |

### NEW SCORING (v2.0 - Strict)

| Heuristic | New Score | Rationale | Deductions |
|-----------|-----------|-----------|------------|
| H2: Simplicity | **2** | Cannot read actual copy, forms appear dense | -2 (no content visible) |
| H6: Trust & Safety | **2** | Financial product without visible trust indicators | -2 (financial 2x) → **AUTO-FAIL** |
| H8: Inclusive Design | **2** | Cannot verify accessibility, assume non-compliant | -1 (cannot verify) |
| H10: Emotional | **2** | Rejection screens visible without empathy copy | -2 (rejection penalty) |
| **Overall** | **2.7 (C)** | ❌ **FAIL** - H6 ≤ 2 on financial product |

**Verdict:** Do not ship until trust indicators added and content reviewed.

---

## 🎓 Scoring Discipline

### Evidence Requirements

**To Score 4 or 5:**
- ✅ Provide 2+ concrete examples of excellence
- ✅ Show zero critical issues
- ✅ Benchmark against industry leaders
- ✅ Verify actual implementation

**To Score 3:**
- ✅ Show basic implementation exists
- ✅ Identify 3+ areas for improvement
- ✅ Document missing features

**To Score 2 or Below:**
- ✅ List specific major issues
- ✅ Explain user impact
- ✅ Assess if safe to ship

### Common Mistakes to Avoid

1. ❌ **Grade inflation** - Giving 4s when evidence supports 3
2. ❌ **Benefit of doubt** - Assuming features exist when you can't see them
3. ❌ **Overlooking content** - Ignoring poor copy because layout is nice
4. ❌ **Ignoring context** - Treating finance same as low-stakes products
5. ❌ **Nice visuals bias** - Pretty UI ≠ good UX

---

## 🔍 How to Use v2.0

### Step-by-Step Process

1. **Start at 3 (Average)** - The neutral baseline
2. **Look for evidence to increase** - Must have concrete examples
3. **Apply automatic deductions** - See deduction table
4. **Apply product multipliers** - Financial/healthcare 2x
5. **Check for auto-fail criteria** - Block if critical issues
6. **Verify HIG compliance** (iOS only) - Check platform patterns
7. **Evaluate flow continuity (H11)** - Walk through user journey
8. **Document every score** - Justify with specific observations

### Red Flags Checklist

Before assigning scores, check for these:

- [ ] Lorem ipsum / placeholder text visible?
- [ ] Broken images / missing assets?
- [ ] Inconsistent design system usage?
- [ ] Generic error messages ("Error occurred")?
- [ ] No visible loading states?
- [ ] Forms >8 fields per screen?
- [ ] Financial terms without explanations?
- [ ] Destructive actions without confirmation?
- [ ] No visible trust indicators (finance)?
- [ ] Can't verify keyboard navigation?
- [ ] Material Design on iOS?
- [ ] Touch targets < 44pt?
- [ ] No Dark Mode support (iOS)?
- [ ] Content behind safe areas?

**Each "yes" triggers a deduction.**

---

## 📈 Expected Outcomes

### With Stricter Scoring, Expect:

1. **Lower average scores** - Designs that scored 3.5-3.6 will now score 2.7-3.2
2. **More failures** - Financial products without trust indicators will auto-fail
3. **Clearer differentiation** - Excellent designs stand out, poor designs flagged
4. **Better focus** - Critical issues (H6, H4, H8) get proper attention
5. **Higher quality bar** - Teams must address basics before Camp 3

### Success Metrics

- ✅ Fewer designs passing with critical flaws
- ✅ Clearer feedback on what needs fixing
- ✅ Better alignment with actual user experience quality
- ✅ Platform-appropriate patterns (iOS HIG compliance)
- ✅ Content quality receives proper scrutiny

---

## 🎯 Next Steps

### For You (Design Leader)

1. **Review the updated skill** - Read through v2.0 changes
2. **Calibrate with team** - Score 3-5 existing designs together using new rubric
3. **Set expectations** - Communicate stricter scoring to designers
4. **Build reference library** - Document examples of each score level
5. **Track improvements** - Re-score old designs to show progress

### For Designers

1. **Expect lower scores initially** - This is more rigorous
2. **Focus on critical heuristics** - H6, H4, H8 for finance
3. **Don't skip content** - Lorem ipsum = auto-low score
4. **Test accessibility** - Can't verify = assume fails
5. **Follow platform guidelines** - HIG compliance for iOS
6. **Walk the journey** - Test flow continuity screen-by-screen

---

## 📚 References

- [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines)
- [Jakob Nielsen's 10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

---

**Version:** 2.0  
**Date:** June 22, 2026  
**Status:** Active  
**Changelog:** See SKILL.md for full updated framework

