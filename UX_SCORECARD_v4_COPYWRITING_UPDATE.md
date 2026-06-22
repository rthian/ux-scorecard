# UX SCORECARD v4.0 - Copywriting & Typography Update

**Date:** June 22, 2026  
**Update:** Added Copywriting, Typography, and CTA Best Practices evaluation criteria

---

## 🎯 WHAT'S NEW IN v4.0

### ✨ NEW EVALUATION CRITERIA: Copywriting, Typography & CTA Hierarchy

The UX Scorecard skill now includes **STRICT rules** for:

1. **Copywriting Length & Readability**
   - Headers: 1-2 lines maximum
   - Body text: 2-3 lines per paragraph maximum
   - Instructions: 1-2 sentences maximum

2. **Typography Consistency**
   - Same hierarchy level = same font size
   - All page titles must be identical size
   - All body text must be identical size
   - Maximum 4 font size levels per design system

3. **CTA Hierarchy & Button Rules**
   - **ONE (1) primary CTA per screen** (STRICT)
   - 0-1 secondary CTA allowed (visually distinct)
   - Tertiary actions as text links only

---

## 📋 NEW AUTOMATIC PENALTIES

### Copywriting Violations

| Issue | Penalty | Heuristic |
|-------|---------|-----------|
| Header >2 lines | -1 point | H2 (Simplicity) |
| Body text >5 lines | -1 point | H2 (Simplicity) |
| Instructions >3 sentences | -1 point | H9 (Easy-to-Learn) |
| Text >50 words on mobile | -2 points | H2 (Simplicity) |

### Typography Violations

| Issue | Penalty | Heuristic |
|-------|---------|-----------|
| Inconsistent title sizes | -1 point | H2 (Simplicity) |
| Inconsistent body sizes | -0.5 points | H2 (Simplicity) |
| >4 font sizes on one screen | -1 point | H2 (Simplicity) |

### CTA Hierarchy Violations

| Issue | Penalty | Heuristic |
|-------|---------|-----------|
| **2 primary CTAs** | **-2 points** | H2 (Simplicity) |
| 3+ CTAs total | -1 point | H2 (Simplicity) |
| Vague CTA text | -1 point | H9 (Easy-to-Learn) |
| CTA text >3 words | -0.5 points | H9 (Easy-to-Learn) |

---

## 🚨 WHY THIS MATTERS

### Real Impact on MSME Onboarding Scores

**BEFORE v4.0 (Copywriting not evaluated):**
- H2 (Simplicity & Clarity): 2/5
- H9 (Easy-to-Learn): 3/5
- **Overall Score:** 2.5/5.0 (C)

**AFTER v4.0 (With copywriting penalties):**
- H2 (Simplicity & Clarity): **1/5** (-1 to -3 points from violations)
- H9 (Easy-to-Learn): **2/5** (-1 point from verbose instructions)
- **Overall Score:** **2.2/5.0 (C-)**

**Impact:** Copywriting issues compound existing UX problems

---

## 🎯 VIOLATIONS IDENTIFIED IN MSME ONBOARDING

### 🚨 CRITICAL: Landing Page (node-id=26540-24978)

**Issue 1: Header Exceeds 2 Lines**
```
Current: "Power up your biz
          with easy financing
          and flexi repayments"
          
→ 3 lines = -1 point on H2
```

**Fix:**
```
"Get financing in minutes"
→ 1 line = PASS
```

**Issue 2: Potentially 2 Primary CTAs**
```
Current: [Sign Up Now] (filled) + [Login] (needs verification)

If both filled → -2 points on H2 (CRITICAL)
```

---

### ⚠️ HIGH: Singpass Sign Up (node-id=21891-24876)

**Issue: Header is 2 Lines (Borderline)**
```
Current: "You've taken the first step!
          Apply in minutes with Singpass."
          
→ 2 lines = -0.5 point on H2
```

**Fix:**
```
"Apply in minutes with Singpass"
→ 1 line = PASS
```

---

### ⚠️ MEDIUM: Mobile Number (node-id=31657-42640)

**Issue: Instructions Too Long**
```
Current: "This is the number we got from Singpass. 
          Please ensure that it is the same number 
          as the one you've provided earlier."
          
→ 3 sentences, ~30 words = -0.5 point on H9
```

**Fix:**
```
"Confirm your mobile number from Singpass.
Tap 'Back' to change it."

→ 2 sentences, ~12 words = PASS
```

---

## 📊 COMPARISON: v3.0 vs v4.0

| Aspect | v3.0 | v4.0 |
|--------|------|------|
| **Figma Pinpoint** | ✅ Yes | ✅ Yes |
| **Copywriting Length** | ❌ Not evaluated | ✅ STRICT rules |
| **Typography Consistency** | ❌ Not evaluated | ✅ STRICT rules |
| **CTA Hierarchy** | ❌ Partial | ✅ STRICT 1-CTA rule |
| **Auto-Penalties** | Limited | Comprehensive |
| **Platform Rules** | Basic | Mobile/desktop specific |

---

## 📏 BEST PRACTICES REFERENCE

### Mobile Headers (iOS/Android)

**Rules:**
- **1 line preferred**, 2 lines absolute max
- **40-60 characters** maximum
- **Short, benefit-focused**

**Good Examples:**
```
✅ "Get financing in minutes" (25 chars, 1 line)
✅ "Apply with Singpass" (20 chars, 1 line)
✅ "Power up your business" (23 chars, 1 line)
```

**Bad Examples:**
```
❌ "Power up your biz with easy financing and flexi repayments" (3 lines)
❌ "You've taken the first step! Apply in minutes with Singpass." (2 lines)
```

---

### Instructions/Helper Text

**Rules:**
- **1-2 sentences maximum**
- **<20 words ideal**
- **Plain language only**

**Good Examples:**
```
✅ "Confirm your mobile number from Singpass." (6 words, 1 sentence)
✅ "Enter your business UEN. Find it on your ACRA certificate." (11 words, 2 sentences)
```

**Bad Examples:**
```
❌ "This is the number we got from Singpass. Please ensure that it is 
    the same number as the one you've provided earlier." (24 words, 2 sentences)
```

---

### CTA Hierarchy

**Rules:**
- **1 primary CTA** (filled button, high contrast)
- **0-1 secondary CTA** (ghost/outline, lower contrast)
- **Tertiary actions** (text links, not buttons)
- **Button text <3 words**

**Good Examples:**
```
✅ PRIMARY: "Sign Up Now" (filled purple)
   SECONDARY: "Login" (ghost/outline)

✅ PRIMARY: "Continue" (filled purple)
   SECONDARY: "Save and Exit" (ghost/outline)
```

**Bad Examples:**
```
❌ PRIMARY: "Sign Up Now" (filled purple)
   PRIMARY: "Login" (also filled purple)
   
→ 2 primary CTAs = -2 points
```

---

### Typography Consistency

**Rules:**
- **All page titles = same size** (e.g., all 28pt)
- **All body text = same size** (e.g., all 16pt)
- **All button text = same size** (e.g., all 16pt)
- **Maximum 4 hierarchy levels** (H1, H2, Body, Caption)

**Good Example:**
```
✅ Screen A Title: "Get financing" (28pt)
   Screen B Title: "Confirm details" (28pt)
   Screen C Title: "Review application" (28pt)
   
→ All titles are 28pt = CONSISTENT
```

**Bad Example:**
```
❌ Screen A Title: "Get financing" (28pt)
   Screen B Title: "Confirm details" (24pt)
   Screen C Title: "Review application" (32pt)
   
→ Inconsistent sizing = -1 point
```

---

## 🎓 HOW TO USE v4.0

### For Designers:

1. **Before designing a new screen:**
   - Check copywriting rules (1-line headers, 1-2 sentence instructions)
   - Plan CTA hierarchy (1 primary max)
   - Use consistent font sizes from design system

2. **During design:**
   - Count lines in headers (max 2)
   - Count sentences in instructions (max 2)
   - Count CTAs on screen (1 primary, 0-1 secondary)

3. **Before Camp review:**
   - Run /ux-scorecard self-review
   - Check for copywriting/typography violations
   - Fix before presenting

### For Reviewers:

1. **Quick visual check:**
   - Any header >2 lines? → Flag
   - Any wall of text >5 lines? → Flag
   - 2+ prominent buttons? → Flag

2. **Typography check:**
   - Compare titles across 3+ screens
   - Are they the same size? → If no, flag

3. **Apply auto-penalties:**
   - Use penalty table in skill
   - Deduct points before final scoring

---

## 🚀 IMMEDIATE ACTIONS FOR MSME ONBOARDING

### Week 1: Copywriting Fixes

1. **Landing Page (26540:24978)**
   - Change header to 1 line: "Get financing in minutes"
   - Verify CTA hierarchy (1 primary + 1 secondary)
   
2. **Singpass Sign Up (21891:24876)**
   - Change header to 1 line: "Apply in minutes with Singpass"
   
3. **Mobile Number (31657:42640)**
   - Shorten instructions to 2 sentences: "Confirm your mobile number from Singpass. Tap 'Back' to change it."

**Time:** 2-3 days  
**Impact:** +2 to +3 points on H2

### Week 2: Typography Audit

1. **Measure all page title font sizes**
2. **Standardize to one size** (e.g., 28pt)
3. **Apply consistently across ALL screens**
4. **Verify body text consistency**
5. **Verify button text consistency**

**Time:** 3-5 days  
**Impact:** +1 point on H2

### Total Impact:

```
H2: 1 → 4 (+3 points)
H9: 2 → 3 (+1 point)

NEW OVERALL SCORE: 2.2 → 2.8 / 5.0 (C)
```

**Combined with previous fixes (Trust, Save-and-resume):**
```
Final score: 2.8 → 3.2+ / 5.0 (C+)
PASSES Camp 2 ✅
```

---

## 📈 EXPECTED OUTCOMES

### Short-term (1-2 weeks):
- **Clearer, more concise copy** (better scannability)
- **Consistent typography** (more professional polish)
- **Clear CTA hierarchy** (less user confusion)

### Medium-term (Camp 2/3):
- **Higher UX scores** (+2 to +4 points total)
- **Faster user comprehension** (less cognitive load)
- **Better conversion rates** (clear primary actions)

### Long-term:
- **Scalable design system** (consistent patterns)
- **Faster design velocity** (clear rules to follow)
- **Better user outcomes** (less frustration, higher success)

---

## 🎯 KEY TAKEAWAYS

1. **Copywriting is design** - Every word affects UX
2. **Concision beats verbosity** - 1 line > 3 lines
3. **Consistency is foundational** - Random sizing = amateur
4. **One primary CTA** - Non-negotiable rule
5. **Easy fixes, big impact** - Copy changes = quick wins

---

## 📚 RESOURCES

**Updated Files:**
- `/Users/yewmun.thian/Desktop/Make/uxscorecard/SKILL.md` (v4.0)
- `/Users/yewmun.thian/.claude/skills/ux-scorecard/SKILL.md` (v4.0)

**New Reports:**
- `MSME_Copywriting_Typography_Review_2026-06-22.md`

**Section Added to Skill:**
- "Copywriting, Typography & CTA Best Practices (MANDATORY)"
- Auto-deduction tables
- Platform-specific rules (mobile/desktop)
- Example violations and fixes

---

**Report Generated:** June 22, 2026  
**Version:** UX Scorecard v4.0  
**Change:** Added Copywriting, Typography, and CTA evaluation criteria  
**Impact:** More comprehensive, stricter scoring for real-world polish

