---
name: ux-scorecard
description: UX Scorecard grading & review skill using UX Heuristics model for design evaluation
---

# UX Scorecard - Design Grading & Review Skill

## Purpose

This skill evaluates designs (PDFs, images, Figma files) against a comprehensive **UX Heuristics framework** and generates a detailed scorecard with grades, findings, and actionable recommendations.

## When to Use

- **Design Camp Reviews**: Validate readiness for Camp 1, 2, or 3
- **Design Critique Prep**: Pre-analyze designs before team critique sessions
- **Competitor Analysis**: Benchmark against competitor designs
- **Quality Gate Checks**: Ensure designs meet quality standards before handoff
- **Self-Review**: Designers can self-assess before presenting to the team

## Inputs

The skill accepts multiple input formats:

1. **PDF uploads** - Design presentations, wireframes, mockups
2. **Image/screenshots** - PNG, JPG of UI screens
3. **Figma files** - Via Figma MCP server (provide Figma URL)
4. **Context** (optional):
   - Project brief/PRD
   - Target user segment
   - Camp stage (1, 2, or 3)
   - Specific concerns to focus on

## UX Heuristics Framework

### 10 Heuristics Across 5 Categories

**Framework Foundation:**
- **Primary**: Jakob Nielsen's 10 Usability Heuristics (adapted for financial UX)
- **Secondary**: Apple Human Interface Guidelines (HIG)
- **Additional**: Flow Continuity & User Journey Coherence

**When evaluating iOS/Apple platforms, additionally reference:**
- [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines)
- Platform-specific patterns (iOS, macOS, watchOS, etc.)
- Native component usage and behavior

#### **Usability (5 heuristics)**

1. **Visibility of system status**
   - Users should always know what's happening
   - Clear feedback on transactions, loading states, errors
   - Score: How well does the design communicate system state?

2. **Simplicity & clarity**
   - Easy to understand, free of jargon
   - Minimize cognitive load
   - Score: How intuitive and clear is the UI?

3. **User control & freedom**
   - Ability to undo, cancel, exit processes
   - No locked-in states
   - Score: Can users easily reverse actions?

4. **Error prevention & recovery**
   - Validate input, confirm destructive actions
   - Clear error messages with next steps
   - Score: How well does the design prevent and handle errors?

5. **Efficiency of use**
   - Frequent actions are effortless
   - Shortcuts, customization available
   - Score: How efficient are common user tasks?

#### **Trust & Security (2 heuristics)**

6. **Reinforce trust & safety**
   - Clear security indicators
   - Transparent data handling
   - Score: Does the design build user confidence?

7. **Real-time feedback**
   - Instant notifications on account changes
   - Transaction confirmations
   - Score: Are users kept informed of critical events?

#### **Accessibility (1 heuristic)**

8. **Inclusive design**
   - Usable by people of all abilities
   - Support for low digital literacy, visual impairments, language barriers
   - Score: How accessible is the design?

#### **Onboarding (1 heuristic)**

9. **Easy-to-learn features**
   - First-time users understand immediately
   - Self-explanatory workflows
   - Guided assistance (tooltips, walkthroughs)
   - Score: How easy is it for new users to learn?

#### **Emotional Reassurance (1 heuristic)**

10. **Delight & confidence building**
    - Success animations, positive reinforcement
    - Banking can be stressful—small moments of reassurance help
    - Score: Does the design create positive emotional moments?

### BONUS: Flow Continuity & User Journey (11th Heuristic)

**NEW: Evaluate screen-to-screen flow as a user would experience it**

This additional heuristic assesses the **continuity and coherence of the user journey**:

11. **Flow continuity**
    - Does the journey feel natural and logical screen-to-screen?
    - Are transitions smooth and purposeful?
    - Does context carry forward (no jarring resets)?
    - Can users understand their journey progression?
    - Are there dead ends or confusing navigation jumps?
    - Does the flow match user mental models?

**Scoring Criteria:**
- **5**: Seamless flow, each screen naturally leads to next, perfect continuity
- **4**: Good flow with 1-2 minor hiccups in transitions
- **3**: Flow is logical but has noticeable breaks in continuity (3+ issues)
- **2**: Multiple jarring transitions, confusing navigation, poor context retention
- **1**: Flow is incoherent, users will get lost, broken journey

**How to Evaluate:**
1. **Follow the primary user journey** screen-by-screen as if you're the user
2. **Check context preservation**: Does information carry forward? (e.g., entered data, selections)
3. **Assess transition logic**: Does each screen's purpose make sense after the previous one?
4. **Evaluate navigation consistency**: Can users go back? Is hierarchy clear?
5. **Look for dead ends**: Are there screens that trap users?
6. **Check cognitive load**: Do users need to remember info from previous screens?

**Flow Red Flags:**
- 🚨 Data entered earlier not visible/pre-filled later
- 🚨 Sudden context switches without explanation
- 🚨 Back button leads to unexpected screen
- 🚨 Users must remember information from previous screens
- 🚨 Progress resets unexpectedly
- 🚨 Navigation hierarchy is unclear
- 🚨 Dead ends with no clear next action

## Scoring System

### Individual Heuristic Scoring (1-5 scale)

**🚨 CRITICAL PRINCIPLE: Default to LOWER scores when evidence is insufficient. Assume issues exist until proven otherwise.**

| Score | Meaning | Description | Evidence Required |
|-------|---------|-------------|-------------------|
| **5** | Excellent | Fully meets the heuristic, experience is optimised. Best-in-class implementation. | Multiple concrete examples of excellence, zero issues found, exceeds industry standards. Requires detailed inspection to award. RARE. |
| **4** | Good | Mostly meets the heuristic, 1-2 minor cosmetic concerns | Clear evidence of good patterns visible, only minor polish needed. Must have concrete examples. |
| **3** | Average | Meets basic requirements but has 3+ usability issues OR lacks critical features | Some good patterns but notable gaps. Would benefit from significant improvements. **Default when uncertain**. |
| **2** | Poor | Major gaps in heuristic implementation causing significant user friction | Multiple serious issues identified OR cannot verify critical features exist. Users will struggle. |
| **1** | Bad | Heuristic completely unmet, experience is broken or unusable | Critical failures, anti-patterns, or complete absence of required features. Unsafe or unusable. |

### Scoring Philosophy: "STRICT BY DEFAULT - Guilty Until Proven Innocent"

**⚠️ WHEN IN DOUBT, SCORE LOWER**

Apply these strict defaults when visibility is limited:

| Limitation | Max Score Allowed | Rationale |
|------------|-------------------|-----------|
| Cannot see detailed content/copy | **2** | Assume poor microcopy until verified |
| Only viewing overview/thumbnail | **2-3** | Cannot assess actual quality |
| Unclear if feature exists | **2** | Assume it doesn't |
| Financial/security/healthcare product | **1-2** unless explicit trust indicators | Trust is non-negotiable |
| Accessibility cannot be verified | **2** | Assume fails WCAG until proven |
| Cannot read actual microcopy | **Deduct 1-2** points | Words ARE the UX |
| No interactive prototype available | **Cap at 3** | Cannot verify actual experience |
| Dense forms visible (>5 fields/screen) | **2-3** | Cognitive overload |
| No visible error states | **2** | Assume poor error handling |
| Lorem ipsum or placeholder text visible | **1-2** | Content is design |

### Automatic Score Deductions

Apply these penalties automatically:

| Issue | Deduction | Heuristics Affected | Auto-Fail? |
|-------|-----------|---------------------|------------|
| Cannot read actual content/copy | -2 points | H2, H6, H9, H10 | - |
| Financial product without visible trust indicators | -2 points | H6 | Yes (H6 ≤ 2) |
| Forms without visible error states | -1 point | H4 | - |
| No visible save/exit on multi-step flows | -1 point | H3 | - |
| Cannot verify accessibility compliance | -1 point | H8 | - |
| Dense forms (>5 fields per screen) | -1 point | H2, H5 | - |
| No visible loading/progress states | -1 point | H1 | - |
| Cannot verify screen reader compatibility | -2 points | H8 | - |
| No visible multi-language support | -1 point | H8 | - |
| Rejection/error screens without empathy | -2 points | H10 | - |
| Security-critical actions without confirmation | -2 points | H4 | Yes (H4 = 1) |
| Poor visible content (lorem ipsum, unclear copy) | -2 points | H2, H9 | - |
| No visible trust/security badges on financial forms | -2 points | H6 | Yes (H6 ≤ 2) |

### Product-Specific Multipliers

Some products require higher standards:

| Product Type | Multiplier | Affected Heuristics | Notes |
|--------------|------------|---------------------|-------|
| Financial (loans, payments, investments) | 2x penalties | H6 (Trust), H4 (Error), H10 (Emotion) | Lives and money at stake |
| Healthcare | 2x penalties | H6, H4, H8 | Patient safety critical |
| E-commerce checkout | 1.5x penalties | H6, H4 | Conversion-critical |
| Onboarding/signup | 1.5x penalties | H9, H10 | First impression matters |

### Overall Score Calculation

```
Final Score = Σ(Heuristic Scores - Penalties) / Total Number of Heuristics
```

### Badge Levels

| Final Score | Badge | Summary | Interpretation | Ship? |
|-------------|-------|---------|----------------|-------|
| **4.5 - 5.0** | **A** | Excellent | UX is delightful and exceeds expectations. Best-in-class. | ✅ Ship |
| **4.0 - 4.4** | **B+** | Very Good | Strong usability with only minor polish needed. | ✅ Ship with minor improvements |
| **3.5 - 3.9** | **B** | Good | Meets most expectations, some usability friction. | ⚠️ Ship with caveats, plan iteration |
| **3.0 - 3.4** | **C+** | Above Average | Functional but needs significant refinements. | ⚠️ Conditional - fix HIGH issues first |
| **2.5 - 2.9** | **C** | Average | Users can complete tasks, but friction is significant. | ❌ Do not ship - major rework needed |
| **2.0 - 2.4** | **C-** | Below Average | Serious usability concerns impact experience. | ❌ Do not ship - redesign required |
| **1.5 - 1.9** | **D** | Poor | Users struggle significantly. Fundamentally broken. | ❌ BLOCK - complete redesign |
| **1.0 - 1.4** | **F** | Bad | The experience is unusable or unsafe. | ❌ BLOCK - start over |

### Auto-Fail Criteria

**Immediate FAIL regardless of overall score if ANY of these are true:**

1. **Security-critical actions without confirmation** (H4 = 1)
2. **Financial product without trust indicators** (H6 ≤ 2)
3. **Inaccessible to screen readers** (H8 ≤ 1) for public-facing products
4. **Poor visible content** (lorem ipsum, gibberish, broken) in Camp 3
5. **Any heuristic scores 1** in Camp 3 review
6. **More than 3 heuristics ≤ 2** in Camp 3

## Evaluation Methodology

### Step-by-Step Scoring Process

Follow this rigorous process for each heuristic:

1. **Start at 3 (Average)** - The neutral baseline
2. **Look for evidence to increase score** - Must have concrete examples
3. **Apply automatic deductions** - See deduction table above
4. **Apply product multipliers** - Financial/healthcare/critical products
5. **Verify with industry benchmarks** - Compare to best-in-class
6. **Document every score** - Justify with specific observations

### Evidence Collection Requirements

For each heuristic, you MUST:

**To Score 4 or 5:**
- ✅ Provide 2+ concrete examples of excellence
- ✅ Show zero critical issues
- ✅ Benchmark against industry leaders
- ✅ Verify actual implementation (not just promises)

**To Score 3:**
- ✅ Show basic implementation exists
- ✅ Identify 3+ areas for improvement
- ✅ Document missing features

**To Score 2 or Below:**
- ✅ List specific major issues
- ✅ Explain user impact
- ✅ Assess if design is safe to ship

### Red Flags That Auto-Lower Scores

Watch for these anti-patterns:

| Red Flag | Impact | Score Ceiling |
|----------|--------|---------------|
| Lorem ipsum / placeholder text | Content incomplete | 2 |
| Broken images / missing assets | Not production-ready | 2 |
| Inconsistent design system usage | Poor quality | 3 |
| Generic error messages ("Error occurred") | Poor H4 | 2 |
| No visible loading states | Poor H1 | 2 |
| Forms >8 fields per screen | Cognitive overload, poor H2 | 2 |
| Financial terms without explanations | Poor H8, H9 | 2 |
| Destructive actions without confirmation | Unsafe, H4 = 1 | 1 |
| No visible trust indicators (finance) | H6 = 1-2 | 2 |
| Can't verify keyboard navigation | Accessibility fail, H8 ≤ 2 | 2 |

### Content Quality Assessment (MANDATORY)

**Content IS design.** Poor content = poor UX, even if visuals are beautiful.

Check every visible piece of text for:

1. **Clarity** - Free of jargon, understandable to target users
2. **Tone** - Appropriate for context (empathetic in stressful moments)
3. **Completeness** - No placeholder text, all copy finalized
4. **Accuracy** - Correct grammar, spelling, facts
5. **Scannability** - Short sentences, clear hierarchy
6. **Actionability** - CTAs are clear and specific

**Content Scoring Impact:**

| Content Quality | Impact on Heuristics |
|-----------------|---------------------|
| Poor/missing | H2 -2, H6 -1, H9 -2, H10 -2 |
| Generic/template | H2 -1, H10 -1 |
| Good but unpolished | H2 -0.5 |
| Excellent | Can boost scores +0.5 |

### Copywriting, Typography & CTA Best Practices (MANDATORY)

**CRITICAL: Evaluate every screen for copywriting quality, typography consistency, and CTA hierarchy.**

These are STRICT RULES that apply to ALL screens:

#### 1. Copywriting Length & Readability

**Headers/Titles:**
- **Mobile:** Maximum 1 line (preferred), 2 lines absolute max
- **Desktop:** Maximum 1-2 lines
- **Character limit:** ~40-60 characters for mobile headers
- **Penalty:** -1 point on H2 (Simplicity) per violation

**Body Copy:**
- **Mobile:** 2-3 lines maximum per paragraph
- **Desktop:** 3-4 lines maximum per paragraph
- **Keep it scannable:** Short sentences (15-20 words max)
- **Penalty:** -0.5 point on H2 per screen with excessive text

**Instructions/Helper Text:**
- **1-2 sentences maximum**
- **Plain language only**
- **No jargon without tooltips**
- **Penalty:** -1 point on H9 (Easy-to-Learn) if too verbose

**Red Flags:**
- 🚨 **Header >2 lines** → H2 -1 (cognitive overload)
- 🚨 **Body text >5 lines** → H2 -1 (wall of text)
- 🚨 **Instructions >3 sentences** → H9 -1 (too complex)
- 🚨 **Any text >50 words** on mobile → H2 -2 (CRITICAL)

**Example Violations:**

❌ **BAD Header (3 lines):**
```
"Power up your biz
with easy financing
and flexi repayments"
```
→ 3 lines, ~60 characters = **H2 -1**

✅ **GOOD Header (1 line):**
```
"Get financing in minutes"
```
→ 1 line, ~25 characters = PASS

❌ **BAD Instructions (too long):**
```
"This is the number we got from Singpass. 
Please ensure that it is the same number 
as the one you've provided earlier. If you 
need to change it, please go back to the 
previous screen and update your details."
```
→ 5 sentences, ~50 words = **H9 -1**

✅ **GOOD Instructions (concise):**
```
"Confirm your mobile number from Singpass.
Tap 'Back' to change it."
```
→ 2 sentences, ~12 words = PASS

---

#### 2. Typography Consistency

**Font Size Hierarchy (Mobile):**
- **H1 (Page Title):** 28-34pt (consistent across ALL screens)
- **H2 (Section Title):** 22-24pt (consistent across ALL screens)
- **Body:** 16-18pt (consistent across ALL screens)
- **Caption/Helper:** 14-15pt (consistent across ALL screens)
- **CTA Button:** 16-18pt (consistent across ALL buttons)

**Consistency Rules:**
- **Same hierarchy level = same font size**
- **All page titles must be the same size**
- **All body text must be the same size**
- **No random size variations**

**Penalty:**
- **Inconsistent title sizes** → H2 -1 per occurrence
- **Inconsistent body sizes** → H2 -0.5 per occurrence
- **More than 3 font sizes on one screen** → H2 -1 (hierarchy confusion)

**Red Flags:**
- 🚨 **Title 28pt on Screen A, 24pt on Screen B** → H2 -1 (INCONSISTENT)
- 🚨 **Body 16pt in one paragraph, 18pt in another** → H2 -0.5 (INCONSISTENT)
- 🚨 **Button text 16pt on primary, 14pt on secondary** → H2 -0.5 (INCONSISTENT)

**How to Check:**
1. Compare same element type across multiple screens
2. Verify title sizes are identical
3. Verify body text sizes are identical
4. Check button text sizes are identical

**Example Violations:**

❌ **BAD (Inconsistent Titles):**
```
Screen A Title: "You've taken the first step!" (28pt)
Screen B Title: "Power up your biz" (24pt)
```
→ Inconsistent = **H2 -1**

✅ **GOOD (Consistent Titles):**
```
Screen A Title: "You've taken the first step!" (28pt)
Screen B Title: "Power up your biz" (28pt)
```
→ Consistent = PASS

---

#### 3. CTA Hierarchy & Button Rules

**PRIMARY CTA RULE:**
- **One (1) primary CTA per screen** (STRICT)
- **Visual style:** Filled button, high contrast (e.g., purple, blue)
- **Placement:** Bottom of screen (sticky footer) OR prominent position
- **Text:** Action-oriented (e.g., "Sign Up Now", "Continue", "Submit")

**SECONDARY CTA RULE:**
- **Zero (0) or One (1) secondary CTA per screen**
- **Visual style:** Ghost/outline button, lower contrast
- **Placement:** Above or beside primary (if present)
- **Text:** Alternative action (e.g., "Login", "Skip", "Back")

**TERTIARY ACTION RULE:**
- **Text link only** (not a button)
- **Use for:** "Learn more", "Terms & Conditions", "Need help?"

**Penalty:**
- **2 primary CTAs on one screen** → H2 -2 (CRITICAL - confusing)
- **3+ CTAs (any type) on one screen** → H2 -1 (cognitive overload)
- **CTA text unclear** (e.g., "Submit", "OK") → H9 -1 (not action-oriented)

**Red Flags:**
- 🚨 **2 filled buttons** → H2 -2 (CRITICAL - which is primary?)
- 🚨 **Primary CTA not obvious** → H2 -1 (poor hierarchy)
- 🚨 **CTA text >3 words** → H9 -0.5 (too verbose)
- 🚨 **CTA text vague** ("Continue", "Next" without context) → H9 -0.5

**Example Violations:**

❌ **BAD (2 Primary CTAs):**
```
[Sign Up Now] ← Filled purple button
[Login]       ← Filled purple button
```
→ 2 primary CTAs = **H2 -2 (CRITICAL)**

✅ **GOOD (1 Primary + 1 Secondary):**
```
[Sign Up Now] ← Filled purple button (primary)
[Login]       ← Ghost/outline button (secondary)
```
→ Clear hierarchy = PASS

❌ **BAD (Vague CTA):**
```
[Submit]  ← What am I submitting?
```
→ Unclear action = **H9 -1**

✅ **GOOD (Clear CTA):**
```
[Sign Up With Singpass]  ← Clear action
```
→ Clear action = PASS

---

#### 4. Platform-Specific Typography Rules

**iOS/Mobile:**
- **Line height:** 1.3-1.5x font size (no cramped text)
- **Text alignment:** Left-aligned (never center body text)
- **Headers:** Can be center or left-aligned (consistent)
- **Max characters per line:** 50-60 for readability

**Desktop/Web:**
- **Line height:** 1.5-1.6x font size
- **Max characters per line:** 60-80 for readability
- **Paragraph spacing:** 1.5x line height

---

#### 5. Scoring Impact Summary

| Issue | Impact | Penalty |
|-------|--------|---------|
| Header >2 lines | H2 (Simplicity) | -1 per violation |
| Body text >5 lines | H2 (Simplicity) | -1 per screen |
| Instructions >3 sentences | H9 (Easy-to-Learn) | -1 per screen |
| Inconsistent font sizes | H2 (Simplicity) | -1 per hierarchy level |
| 2 primary CTAs | H2 (Simplicity) | -2 (CRITICAL) |
| 3+ CTAs total | H2 (Simplicity) | -1 (overload) |
| Vague CTA text | H9 (Easy-to-Learn) | -1 per CTA |
| Text >50 words on mobile | H2 (Simplicity) | -2 (CRITICAL) |

---

#### 6. Evaluation Checklist

For EVERY screen, check:

**Copywriting:**
- [ ] Header is 1-2 lines maximum
- [ ] Body text is 2-3 lines per paragraph max
- [ ] Instructions are 1-2 sentences maximum
- [ ] No single text block >50 words
- [ ] No jargon without tooltips
- [ ] Tone is appropriate (encouraging, not cold)

**Typography:**
- [ ] All page titles are the same font size
- [ ] All body text is the same font size
- [ ] All button text is the same font size
- [ ] Font hierarchy has max 4 levels (H1, H2, Body, Caption)
- [ ] Line height is sufficient (not cramped)
- [ ] Text is left-aligned (body) or consistent (headers)

**CTA Hierarchy:**
- [ ] **Only 1 primary CTA** (filled button)
- [ ] 0-1 secondary CTA (ghost/outline button)
- [ ] Tertiary actions are text links (not buttons)
- [ ] CTA text is action-oriented (not vague)
- [ ] CTA text is <3 words
- [ ] Primary CTA is visually obvious

---

#### 7. Examples from MSME Onboarding (Reference)

**Screen Analysis:**

📍 **Screen: Mobile Number Confirmation** | 🔗 node-id=31657-42640

**Copywriting Issues:**
- ❌ Instructions too long (3 sentences, ~30 words)
- "This is the number we got from Singpass. Please ensure that it is the same number as the one you've provided earlier."
- **Penalty:** H9 -0.5 (should be 1-2 sentences)

**Better Version:**
- ✅ "Confirm your mobile number from Singpass. Tap 'Back' to change it."
- 2 sentences, ~12 words = PASS

---

📍 **Screen: Singpass Sign Up** | 🔗 node-id=21891-24876

**Copywriting Issues:**
- ❌ Title is 2 lines: "You've taken the first step! Apply in minutes with Singpass."
- **Penalty:** H2 -0.5 (should be 1 line)

**Better Version:**
- ✅ "Apply in minutes with Singpass"
- 1 line, ~30 characters = PASS

**Typography Issues:**
- ⚠️ Cannot verify if title font size is consistent with other screens
- **Need to check:** Compare with other screen titles

---

📍 **Screen: Landing Page** | 🔗 node-id=26540-24978

**Copywriting Issues:**
- 🚨 Title is **3 lines**: "Power up your biz with easy financing and flexi repayments"
- **Penalty:** H2 -1 (CRITICAL - should be 1-2 lines max)

**Better Version:**
- ✅ "Get financing in minutes"
- 1 line, ~25 characters = PASS

**CTA Issues:**
- 🚨 **2 CTAs present:**
  - "Sign Up Now" (primary, filled)
  - "Login" (secondary, but also visually prominent)
- ⚠️ If "Login" is also a filled button → H2 -2 (CRITICAL)
- ✅ If "Login" is ghost/outline → PASS

**Typography Issues:**
- ⚠️ Need to verify title font size consistency
- ⚠️ Need to verify if "Power up your biz..." uses same size as other titles

---

### How to Report Copywriting/Typography Issues

**Format for findings:**

```markdown
### 🚨 H2: Simplicity & Clarity - COPYWRITING VIOLATION

**Issue:** Header exceeds 2 lines maximum

**Affected Screens:**
📍 Landing Page | 🔗 https://www.figma.com/design/ABC?node-id=26540-24978
- Current: "Power up your biz with easy financing and flexi repayments" (3 lines)
- Recommendation: "Get financing in minutes" (1 line)

**Impact:** Cognitive overload, poor scannability, user confusion

**Penalty:** H2 -1 point

**Priority:** 🔴 HIGH
```

```markdown
### 🚨 H2: Simplicity & Clarity - CTA HIERARCHY VIOLATION

**Issue:** 2 primary CTAs on one screen (violates 1-CTA rule)

**Affected Screens:**
📍 Landing Page | 🔗 https://www.figma.com/design/ABC?node-id=26540-24978
- "Sign Up Now" (filled button)
- "Login" (filled button)

**Impact:** User confusion about primary action, poor visual hierarchy

**Recommendation:**
- Keep "Sign Up Now" as primary (filled purple)
- Change "Login" to secondary (ghost/outline)

**Penalty:** H2 -2 points (CRITICAL)

**Priority:** 🔴 CRITICAL - Fix immediately
```

---

### Auto-Deductions for Copywriting/Typography

Add these automatic deductions when scoring:

| Violation | Auto-Deduct | From Heuristic |
|-----------|-------------|----------------|
| Header >2 lines | -1 | H2 |
| Body text >5 lines | -1 | H2 |
| Instructions >3 sentences | -1 | H9 |
| Text >50 words on mobile | -2 | H2 |
| Inconsistent title sizes | -1 | H2 |
| Inconsistent body sizes | -0.5 | H2 |
| 2 primary CTAs | -2 | H2 |
| 3+ CTAs total | -1 | H2 |
| Vague CTA text | -1 | H9 |
| CTA text >3 words | -0.5 | H9 |

**Apply these deductions BEFORE calculating final heuristic scores.**

### Accessibility Quick Check (MANDATORY)

Even without interactive prototype, check for visual accessibility signals:

✅ **Can verify:**
- Text contrast appears sufficient
- Touch targets appear adequately sized
- Visual hierarchy exists
- Color is not only means of communication
- Text appears readable

❌ **Cannot verify (score H8 ≤ 2):**
- Screen reader compatibility
- Keyboard navigation
- ARIA labels
- Focus management
- Skip links

**If you cannot verify accessibility, default to H8 = 2 max.**

### Apple Human Interface Guidelines (HIG) Compliance

**When evaluating iOS/Apple platform designs, additionally check:**

#### Platform-Specific Checklist

**iOS/iPadOS:**
- [ ] Uses native iOS UI patterns (not Android Material Design)
- [ ] Bottom tab bar for main navigation (not hamburger menu)
- [ ] Native iOS navigation bar behavior
- [ ] SF Symbols used appropriately
- [ ] Dynamic Type support (text scales)
- [ ] Safe area respects (no content behind notch/home indicator)
- [ ] Standard iOS gestures (swipe back, pull to refresh)
- [ ] iOS-native components (pickers, alerts, action sheets)

**Touch Targets (iOS):**
- [ ] Minimum 44x44 pt for all interactive elements
- [ ] Adequate spacing between tappable elements (8pt minimum)
- [ ] No tiny close buttons or links

**Typography (iOS):**
- [ ] San Francisco font (or custom approved font)
- [ ] Dynamic Type categories used (Body, Headline, Caption, etc.)
- [ ] Text scales with user accessibility settings
- [ ] Minimum 17pt for body text on iPhone

**Color & Contrast:**
- [ ] Supports both Light and Dark mode
- [ ] Color contrast meets WCAG AA (4.5:1 for text)
- [ ] Color is not only means of conveying information
- [ ] Brand colors work in both themes

**Navigation:**
- [ ] Clear navigation hierarchy (drill down, modal, full screen)
- [ ] Back button behavior is standard
- [ ] Modal sheets have proper dismiss gestures
- [ ] No nested navigation stacks

**Interactions:**
- [ ] Haptic feedback for important actions
- [ ] Loading states use standard iOS spinners
- [ ] Pull to refresh uses standard iOS control
- [ ] Swipe actions for list items follow iOS patterns

**HIG Scoring Impact:**

| HIG Compliance | Score Adjustment |
|----------------|------------------|
| Fully compliant with iOS HIG | Boost H2, H9 by +0.5 |
| Mostly compliant, minor deviations | No change |
| Major HIG violations (e.g., Material Design on iOS) | H2 -1, H9 -1 |
| Platform-inappropriate patterns | H9 = 2 max |

**HIG Red Flags (Auto-Lower Scores):**

- 🚨 **Material Design on iOS** → H2 = 2, H9 = 2 (users expect iOS patterns)
- 🚨 **Hamburger menu instead of tab bar** → H5 -1 (poor iOS navigation)
- 🚨 **Touch targets < 44pt** → H8 = 2 (accessibility fail)
- 🚨 **No Dark Mode support** → H8 -1 (iOS users expect it)
- 🚨 **Custom UI that mimics but diverges from native** → H2 -1, H9 -1 (confusing)
- 🚨 **Text doesn't scale with Dynamic Type** → H8 = 2 (accessibility fail)
- 🚨 **Content behind safe areas** → H2 -1 (poor iOS implementation)

**Reference:** [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines)

## Camp Readiness Criteria

### **Camp 1 - Discovery/Basecamp**
- **Purpose**: Early concepts, multiple options explored
- **Minimum Requirements**:
  - All "Discovery" MUST steps completed
  - Concepts: Early stage, multiple options explored
  - Fidelity: Paper, wireframes, rough prototype
  - Content: Representative placeholder (no lorem ipsum)
  - Illustrations: Not required
- **Pass Criteria**: Focus on concept validation, not polish

### **Camp 2 - Design Weekly Review**
- **Purpose**: Design quality feedback on mature concept
- **Minimum Requirements**:
  - All "Discovery" MUST steps + all "Design" MUST steps (except usability testing and content localization)
  - Concepts: One mature concept you are confident about
  - Fidelity: On device or screen prototype (Figma, ProtoPie, MarvelApp, etc)
  - Content: Representative Placeholder
  - Stakeholders: Product Manager
- **Pass Criteria**: Minimum average score of **3.0 (C)** across all heuristics
- **Review Focus**:
  - Application of design principles
  - Usage of design system
  - Design quality checklist
  - Overall design execution
  - Content design
  - Implementation of research insights

### **Camp 3 - Product Spec Review**
- **Purpose**: Final step before shipping
- **Minimum Requirements**:
  - All steps of "Discovery" and "Design should be completed"
  - Design should be "Complete" to the point you are comfortable with real customer using it
  - Concepts: As is experienced by the customer (e.g. on device prototype for features or if new experience is offline, physical artefacts like training manuals, posters)
  - Fidelity: On device or screen prototype (Figma, ProtoPie, MarvelApp, etc)
  - Content: Finalised
  - Illustrations: Finalised
  - Usability Testing: Completed & Changes Implemented
- **Pass Criteria**: Minimum average score of **3.5 (B)** across all heuristics
- **Ready to Ship**: Design should be ready for real customers

## Output Format

The skill generates a comprehensive scorecard:

```
╔═══════════════════════════════════════════╗
║  UX SCORECARD RESULTS                     ║
║  Project: [Project Name]                  ║
║  Platform: [iOS/Android/Web/etc]          ║
║  Camp: [1/2/3]                            ║
║  Evaluated: [Date]                        ║
╠═══════════════════════════════════════════╣
║  OVERALL SCORE: [X.X] / 5.0               ║
║  GRADE: [Badge] ([Summary])               ║
║  HIG COMPLIANCE: [Pass/Fail] (iOS only)   ║
╚═══════════════════════════════════════════╝

┌─────────────────────────────────────────────────┐
│ HEURISTIC BREAKDOWN                             │
├─────────────────────────────────────────────────┤
│ Category: USABILITY                             │
│ ✅ H1: Visibility of system status        │ [X] │
│ ⚠️  H2: Simplicity & clarity             │ [X] │
│ ❌ H3: User control & freedom            │ [X] │
│ ✅ H4: Error prevention & recovery       │ [X] │
│ ✅ H5: Efficiency of use                 │ [X] │
│                                                 │
│ Category: TRUST & SECURITY                      │
│ ⚠️  H6: Reinforce trust & safety         │ [X] │
│ ✅ H7: Real-time feedback                │ [X] │
│                                                 │
│ Category: ACCESSIBILITY                         │
│ ⚠️  H8: Inclusive design                 │ [X] │
│                                                 │
│ Category: ONBOARDING                            │
│ ✅ H9: Easy-to-learn features            │ [X] │
│                                                 │
│ Category: EMOTIONAL REASSURANCE                 │
│ ✅ H10: Delight & confidence building    │ [X] │
│                                                 │
│ Category: FLOW CONTINUITY (BONUS)               │
│ ✅ H11: Flow continuity & journey        │ [X] │
└─────────────────────────────────────────────────┘

iOS PLATFORM COMPLIANCE (if applicable):
✅ Native iOS patterns used
✅ Touch targets ≥ 44pt
⚠️  Dark mode support incomplete
✅ Dynamic Type supported
❌ Content behind safe areas (notch/home indicator)

CAMP [X] GATE STATUS: ✅ PASS / ⚠️ CONDITIONAL PASS / ❌ FAIL
[Status explanation]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CRITICAL FINDINGS (Score ≤ 2)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

❌ [Heuristic Name] (Score: [X])
   Issue: [Specific problem identified]
   Impact: [How this affects users]
   Recommendation: [Concrete fix]
   Priority: HIGH

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AREAS FOR IMPROVEMENT (Score 3)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚠️  [Heuristic Name] (Score: [X])
   Issue: [Specific problem identified]
   Impact: [How this affects users]
   Recommendation: [Concrete fix]
   Priority: MEDIUM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRENGTHS (Score ≥ 4)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ [Heuristic Name] (Score: [X])
   Strength: [What works well]
   Why it matters: [Impact on users]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. [Action item based on critical findings]
2. [Action item based on improvement areas]
3. [Recommended Camp progression or iteration]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DESIGN CAMP RECOMMENDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Specific recommendation on whether design is ready 
for next camp or needs iteration]
```

## Usage Examples

### Example 1: Image/Screenshot Review

```bash
# Upload design screenshot
[User uploads payment_flow_screen.png]

Prompt: "Review this payment flow screen using UX Scorecard. Camp 2 stage. Focus on error prevention and trust indicators."

# Skill analyzes the image and generates scorecard
```

### Example 2: Figma File Review

```bash
Prompt: "/ux-scorecard https://figma.com/file/ABC123/payment-redesign --camp=2 --frame='Final Design'"

# Skill uses Figma MCP to fetch the design and evaluate
```

### Example 3: PDF Review

```bash
# Upload design deck PDF
[User uploads Payment_Flow_Redesign_v3.pdf]

Prompt: "Run UX Scorecard on this design deck. Camp 3 readiness check."

# Skill reads all pages and generates comprehensive review
```

### Example 4: Competitor Comparison

```bash
Prompt: "Compare our payment flow (payment_flow_v2.png) against DBS Bank's flow (dbs_payment.png) using UX Scorecard."

# Skill generates side-by-side comparison with scores
```

## Workflow Integration

### Pre-Critique Workflow

1. **Designer self-review**: Run UX Scorecard before presenting to team
2. **Address critical issues**: Fix any score ≤ 2 findings
3. **Prepare response**: Document why certain trade-offs were made
4. **Present with scorecard**: Share scorecard during critique session

### Camp Gate Workflow

1. **Camp 1**: Focus on concept validation (scorecard used for guidance only)
2. **Camp 2**: Must achieve minimum score 3.0 (C) to proceed
3. **Camp 3**: Must achieve minimum score 3.5 (B) to ship

### Continuous Improvement Workflow

1. **Baseline**: Score initial design
2. **Iterate**: Implement recommendations
3. **Re-score**: Run scorecard again
4. **Track**: Monitor score improvements over time
5. **Learn**: Identify patterns in recurring issues

## Best Practices

### For Designers

- **Run early and often**: Don't wait until Camp reviews
- **Focus on critical findings first**: Address score ≤ 2 items immediately
- **Document trade-offs**: Explain why certain heuristics scored lower
- **Use for self-improvement**: Learn which heuristics you consistently miss
- **Combine with user testing**: Scorecard + real user feedback = gold

### For Reviewers/Managers

- **Use as coaching tool**: Help designers understand heuristics
- **Don't make it punitive**: Scores are for improvement, not performance review
- **Context matters**: Some heuristics may be less relevant for specific flows
- **Multiple evaluators**: For critical projects, have 2-3 people score independently
- **Trend over time**: Track how team's average scores improve

### For Design Ops

- **Standardize reviews**: Use scorecard for all Camp 2+ reviews
- **Build a library**: Keep scored examples as reference
- **Calibration sessions**: Align team on scoring interpretation
- **Integration**: Connect with design tools, Jira, Confluence
- **Analytics**: Track which heuristics are commonly weak across team

## Calibration & Training

To ensure consistent scoring across reviewers:

### Calibration Exercise

1. **Select 5 reference designs**: Mix of excellent (4.5+), good (3.5-4.4), and poor (2.0-2.9)
2. **Score independently**: Have 3+ reviewers score each design
3. **Compare scores**: Identify where scoring diverges
4. **Discuss**: Align on interpretation of each heuristic
5. **Document examples**: Create "reference scorecard" library

### Training for New Team Members

1. **Study heuristics**: Read and understand each of the 10 heuristics
2. **Review scored examples**: See how different designs score and why
3. **Practice scoring**: Score 3-5 designs with mentor review
4. **Calibrate**: Compare your scores against experienced reviewers
5. **Shadow reviews**: Observe Camp 2 reviews with live scoring discussion

## Advanced Features

### Multi-Evaluator Mode

```bash
Prompt: "Multi-evaluator mode: I have 3 reviews. 
Reviewer A scores: [scores]
Reviewer B scores: [scores]  
Reviewer C scores: [scores]
Aggregate and identify areas of disagreement."

# Skill calculates average, variance, and highlights contentious heuristics
```

### Historical Tracking

```bash
Prompt: "Compare this design (v3) against previous versions:
- v1 score: 3.2
- v2 score: 3.5
Show improvement trends."

# Skill shows which heuristics improved and by how much
```

### Component Library Scoring

```bash
Prompt: "Score our button component library against Material Design buttons."

# Skill evaluates reusable components for consistency and quality
```

## References

- **Playbook Section**: UX Heuristics (pages 57-60)
- **Scoring System**: Scoring System (page 58)
- **Templates**: UX_Heuristic Scorecard_Template.xlsx
- **Related Skills**: Design Critique, Camp Reviews, Competitor Evaluation

## Calibration Examples

### What a Score 2 (Poor) Looks Like

**Example: Cash Loan Application**

**H2 Simplicity & Clarity - Score: 2**
- Forms with 10+ fields on single screen
- Financial jargon without explanations ("APR", "Flat rate", "EIR")
- No progressive disclosure
- All fields required with no prioritization
- **Why 2, not 3**: Cognitive overload will cause abandonment
- **Evidence**: Standard best practice is 3-5 fields max per screen

**H6 Trust & Safety - Score: 2**
- No visible security badges
- No explanation of data usage
- Terms buried in fine print
- No social proof or testimonials
- **Why 2, not 1**: Basic branding exists, but trust is undermined
- **Why 2 for finance**: This would be 3 for non-financial, but finance requires 2x standard

### What a Score 4 (Good) Looks Like

**Example: Payment Flow**

**H1 Visibility of System Status - Score: 4**
- Clear "Processing payment..." loading state
- Step indicators (1 of 3, 2 of 3, 3 of 3)
- Real-time balance updates visible
- Clear confirmation screen with receipt
- **Why 4, not 5**: Missing estimated time remaining on loading state
- **Evidence**: Users always know where they are and what's happening

### What a Score 5 (Excellent) Looks Like - RARE

**Example: Best-in-Class Onboarding**

**H10 Delight & Confidence - Score: 5**
- Personalized welcome message with user's name
- Celebratory micro-animations on milestones
- Encouraging copy: "You're doing great! Almost there."
- Progress confetti on completion
- Immediate value delivered (account created, can transact)
- Follow-up email thanking user and next steps
- **Why 5**: Exceeds expectations, creates emotional connection, zero room for improvement
- **Evidence**: Benchmarked against Apple, Stripe, Airbnb onboarding

### What Auto-Fails a Design

**Example: Loan Application with Score 2.8 (C)**

Even though score is 2.8, design **FAILS** because:

1. **Financial product with H6 = 2** (no trust indicators) - AUTO-FAIL
2. **H4 = 1** (no confirmation on loan acceptance) - AUTO-FAIL
3. **More than 3 heuristics ≤ 2** - AUTO-FAIL for Camp 3

**Verdict: Do not ship. Needs major redesign on trust and safety.**

## Scoring Discipline

### Common Scoring Mistakes to Avoid

1. **Grade inflation**: Giving 4s when evidence only supports 3
2. **Benefit of doubt**: Assuming features exist when you can't see them
3. **Overlooking content**: Ignoring poor copy because layout is nice
4. **Ignoring context**: Scoring financial products same as low-stakes products
5. **Nice visuals bias**: Pretty UI ≠ good UX

### Scoring Calibration

Use these anchors:

- **Score 5**: Only for truly exceptional, best-in-class implementations. Should be RARE (< 5% of all scores)
- **Score 4**: Good work that needs minor polish. (15-20% of scores)
- **Score 3**: Functional but needs improvement. (40-50% of scores - most common)
- **Score 2**: Serious issues that will hurt users. (20-30% of scores)
- **Score 1**: Broken or unsafe. (< 5% of scores, but critical when present)

**Expected score distribution for a typical design:**
- Excellent project: avg 3.8-4.2 (mostly 4s and 3s, few 5s)
- Good project: avg 3.2-3.7 (mix of 4s and 3s, some 2s)
- Average project: avg 2.5-3.1 (mostly 3s and 2s)
- Poor project: avg 1.8-2.4 (mostly 2s and 1s)

If you're scoring everything 3.5-4.5, you're being too lenient.

## Notes

- **Scoring is rigorous**: Default to lower scores when evidence is lacking
- **Context-dependent**: Banking UX has specific trust/security requirements (2x penalties)
- **Evolving framework**: Heuristics will be refined based on customer feedback
- **Complement to user testing**: Use scorecard alongside real user research
- **Err on the side of strictness**: It's easier to increase scores than decrease them

## Specific Screen Identification (MANDATORY)

### For Figma Files

**ALWAYS include specific Figma links in findings:**

```markdown
❌ BAD (Generic):
"Forms appear too dense with multiple fields"

✅ GOOD (Specific):
"Forms appear too dense with multiple fields
📍 Screen: Business Details Form
🔗 https://figma.com/design/ABC123?node-id=123-456"
```

**When evaluating Figma:**
1. Use `get_metadata` to list all frames/screens
2. Use `get_screenshot` for individual screens that have issues
3. Include frame name + node-id link in every finding
4. Format: `📍 Screen: [Frame Name] | 🔗 [Figma URL with node-id]`

### For PDF Files

**Reference page numbers and section names:**

```markdown
✅ "Trust indicators missing on loan application screens
📍 Page 5-7: Application Flow Section"
```

### For Image Files

**Reference filename and describe screen:**

```markdown
✅ "No save/exit button visible
📍 File: payment_flow_step2.png - Payment confirmation screen"
```

### For Multiple Screens

**List all affected screens:**

```markdown
✅ "Dense forms (>5 fields per screen) found on:
📍 Screen 1: Business Registration | 🔗 [Figma link node-id=123-456]
📍 Screen 2: Owner Details | 🔗 [Figma link node-id=123-789]  
📍 Screen 3: Bank Account Setup | 🔗 [Figma link node-id=123-012]"
```

### Output Format with Screen References

Every finding MUST include:

```markdown
### 🚨 H2: Simplicity & Clarity (Score: 2)

**Issue:** Forms too dense with >5 fields per screen

**Affected Screens:**
📍 Business Details Form | 🔗 https://figma.com/design/ABC?node-id=20881-19607
📍 Owner Information | 🔗 https://figma.com/design/ABC?node-id=20881-19608
📍 Bank Account Setup | 🔗 https://figma.com/design/ABC?node-id=20881-19609

**Impact:** Cognitive overload for busy MSME owners

**Recommendation:**
1. Break Business Details into 2 screens (max 3-5 fields each)
2. Progressive disclosure for optional fields on Owner Information
3. Auto-fill bank details from previous applications

**Priority:** 🔴 HIGH
```

### When Screen Identification is Not Possible

**If evaluating from overview only:**

```markdown
⚠️ **LIMITATION:** Evaluated from overview screenshot (68,454px wide).
Cannot identify specific screens or read detailed content.

**Recommendation:** For detailed evaluation:
1. Provide interactive Figma prototype
2. OR provide individual screen screenshots
3. OR specify frames to evaluate (node-ids)

**Current evaluation is HIGH-LEVEL ONLY.**
```

**This limitation MUST affect scores:**
- Cannot read content = H2, H9, H10 capped at 2
- Cannot identify specific screens = recommendations are generic
- User must re-evaluate with specific screens for actionable feedback

## Skill Invocation

```bash
# Basic usage
/ux-scorecard [input: PDF/image/Figma URL]

# With context
/ux-scorecard [input] --camp=[1|2|3] --context="[additional context]"

# Multi-evaluator
/ux-scorecard [input] --mode=multi --evaluators=3

# Comparison
/ux-scorecard --compare [input1] [input2]

# Specific Figma frames (RECOMMENDED)
/ux-scorecard https://figma.com/design/ABC?node-id=123-456,123-789,123-012
```

---

**Version**: 2.0  
**Last Updated**: June 22, 2026  
**Owner**: Regional Design Team
