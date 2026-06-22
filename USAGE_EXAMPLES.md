# UX Scorecard - Usage Examples

This guide shows real-world examples of how to use the UX Scorecard skill for different scenarios.

---

## Example 1: Pre-Critique Self-Review

### Scenario
You're a product designer presenting a payment flow redesign at Design Weekly tomorrow. You want to catch any obvious issues before the team sees it.

### Input
```
[Upload: payment_flow_v2.pdf]

"I'm presenting this payment flow redesign at Design Weekly tomorrow. 
Can you run /ux-scorecard on it? I'm at Camp 2 stage. 
My main concerns are around error handling and user control."
```

### Expected Output
```
╔═══════════════════════════════════════════╗
║  UX SCORECARD RESULTS                     ║
║  Project: Payment Flow Redesign v2        ║
║  Camp: 2 (Weekly Review)                  ║
║  Evaluated: June 19, 2026                 ║
╠═══════════════════════════════════════════╣
║  OVERALL SCORE: 3.4 / 5.0                 ║
║  GRADE: C+ (Above Average)                ║
╚═══════════════════════════════════════════╝

┌─────────────────────────────────────────────────┐
│ HEURISTIC BREAKDOWN                             │
├─────────────────────────────────────────────────┤
│ ✅ H1: Visibility of system status        │ 4  │
│ ✅ H2: Simplicity & clarity               │ 4  │
│ ⚠️  H3: User control & freedom            │ 3  │
│ ⚠️  H4: Error prevention & recovery       │ 3  │
│ ✅ H5: Efficiency of use                  │ 4  │
│ ⚠️  H6: Reinforce trust & safety          │ 3  │
│ ✅ H7: Real-time feedback                 │ 4  │
│ ⚠️  H8: Inclusive design                  │ 3  │
│ ✅ H9: Easy-to-learn features             │ 4  │
│ ✅ H10: Delight & confidence building     │ 4  │
└─────────────────────────────────────────────────┘

CAMP 2 GATE STATUS: ✅ PASS
Score of 3.4 meets minimum requirement of 3.0

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AREAS FOR IMPROVEMENT (Score = 3)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚠️  H3: User control & freedom (Score: 3)
   Issue: No visible "Cancel" or "Back" button on Step 3 
          (amount confirmation screen). Users may feel locked in.
   Impact: Users who change their mind cannot easily exit 
           without completing or force-closing app.
   Recommendation: Add clear "Cancel Transaction" button at 
                   top-left. Consider "Edit Amount" option.
   Priority: MEDIUM

⚠️  H4: Error prevention & recovery (Score: 3)
   Issue: Account number validation only happens on "Confirm" 
          tap, not in real-time as user types.
   Impact: User discovers invalid account number after filling 
           entire form, causing frustration.
   Recommendation: Add real-time validation with inline error 
                   messages as user types account number.
   Priority: MEDIUM

⚠️  H6: Reinforce trust & safety (Score: 3)
   Issue: Security indicator (lock icon) only appears on 
          final step. Not visible throughout flow.
   Impact: Users may be unsure if their transaction is secure 
           during earlier steps.
   Recommendation: Show persistent security indicator in 
                   navigation bar throughout flow.
   Priority: MEDIUM

⚠️  H8: Inclusive design (Score: 3)
   Issue: Color contrast ratio 3.5:1 on "Edit" link (gray on 
          light blue background).
   Impact: Users with low vision or color blindness may not 
           see the link clearly.
   Recommendation: Increase contrast to 4.5:1 minimum. 
                   Consider darker gray or add underline.
   Priority: MEDIUM

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRENGTHS (Score ≥ 4)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ H1: Visibility of system status (Score: 4)
   Strength: Clear progress indicator (Step 1/2/3) at top. 
             Loading states well-designed with skeleton screens.
   Why it matters: Users always know where they are in the flow.

✅ H2: Simplicity & clarity (Score: 4)
   Strength: Clean, uncluttered screens. One primary action 
             per screen. Language is simple and jargon-free.
   Why it matters: Reduces cognitive load, makes flow easy 
                   to understand.

✅ H7: Real-time feedback (Score: 4)
   Strength: Success animation on final confirmation is 
             delightful. Clear "Transaction successful" message.
   Why it matters: Builds confidence that payment went through.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Before Design Weekly:
1. ✏️  Add "Cancel Transaction" button on Step 3
2. ✏️  Implement real-time account number validation
3. ⏳ (Optional) Increase color contrast on "Edit" links
4. ⏳ (Optional) Add persistent security indicator

After Design Weekly:
5. Incorporate team feedback
6. Address any additional findings from panel
7. Re-score before Camp 3

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DESIGN CAMP RECOMMENDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ READY FOR CAMP 2 PRESENTATION

Your design meets the minimum score requirement (3.4 > 3.0).
The 4 improvement areas are all score 3 (average), not critical.

Suggested talking points for Design Weekly:
• Highlight the strong fundamentals (system status, simplicity)
• Acknowledge the 4 improvement areas proactively
• Explain any trade-offs made (if applicable)
• Show willingness to iterate based on feedback

You're in good shape for the review!
```

### Takeaway
Designer now knows:
- ✅ Score is passing (3.4 meets Camp 2 minimum 3.0)
- 📋 4 specific improvements to address
- 💪 6 areas that are working well
- 🎯 Clear next steps

---

## Example 2: Competitor Benchmarking

### Scenario
Your team is redesigning the savings account opening flow. You want to see how your design compares to DBS Bank's flow.

### Input
```
[Upload: our_savings_flow.png]
[Upload: dbs_savings_flow.png]

"Compare these two savings account opening flows using /ux-scorecard. 
Ours is the first image, DBS is the second. 
Which one scores higher and where are we falling behind?"
```

### Expected Output
```
╔═══════════════════════════════════════════════════╗
║  UX SCORECARD - COMPARISON REPORT                 ║
╠═══════════════════════════════════════════════════╣
║  Design A: Your Savings Flow         Score: 3.2  ║
║  Design B: DBS Savings Flow           Score: 4.1  ║
╚═══════════════════════════════════════════════════╝

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SIDE-BY-SIDE COMPARISON
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Heuristic                    | Your Flow | DBS Flow | Gap |
|------------------------------|-----------|----------|-----|
| H1: System status visibility | 3         | 4        | -1  |
| H2: Simplicity & clarity     | 4         | 5        | -1  |
| H3: User control & freedom   | 2         | 4        | -2  |
| H4: Error prevention         | 3         | 4        | -1  |
| H5: Efficiency of use        | 3         | 4        | -1  |
| H6: Trust & safety           | 3         | 4        | -1  |
| H7: Real-time feedback       | 4         | 4        | 0   |
| H8: Inclusive design         | 3         | 4        | -1  |
| H9: Easy-to-learn features   | 4         | 5        | -1  |
| H10: Delight & confidence    | 3         | 3        | 0   |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
KEY INSIGHTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🚨 CRITICAL GAP: User control & freedom (-2 points)
   Your flow: Score 2 - Users cannot go back to edit once 
              submitted. No clear way to save progress and 
              return later.
   DBS flow: Score 4 - "Save and Continue Later" button on 
             every step. Clear back navigation throughout.
   
   Recommendation: Add "Save Progress" feature and visible 
                   back navigation.

⚠️  SIGNIFICANT GAPS (All -1 point):
   • H1: System status - DBS shows "2 min remaining" estimate
   • H2: Simplicity - DBS uses progressive disclosure (fewer 
         fields per screen)
   • H4: Error prevention - DBS has inline validation, we 
         validate on submit
   • H6: Trust - DBS shows "Bank Negara approved" badge
   • H8: Accessibility - DBS has larger tap targets, higher 
         color contrast

✅ AREAS WHERE WE MATCH:
   • H7: Real-time feedback (both score 4)
   • H10: Delight (both score 3)

💪 YOUR STRENGTHS:
   • Clean visual design
   • Good use of white space
   • Clear primary actions

📉 OVERALL ASSESSMENT:
   DBS's flow is significantly better (4.1 vs 3.2). The 0.9 
   point gap represents real UX advantages that will affect 
   customer satisfaction and conversion rates.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RECOMMENDED ACTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

HIGH PRIORITY:
1. Add "Save Progress" and "Continue Later" functionality
2. Implement visible back navigation
3. Add time estimate ("~3 min to complete")

MEDIUM PRIORITY:
4. Implement inline validation (real-time feedback)
5. Break form into smaller steps (progressive disclosure)
6. Add trust indicators (Bank Negara logo, security badges)
7. Increase tap target sizes to minimum 44x44pt
8. Improve color contrast to meet WCAG AA standards

If you implement these 8 improvements, you could match or 
exceed DBS's score of 4.1.
```

### Takeaway
- 🎯 Clear understanding of where you're behind
- 📊 Quantified gap (0.9 points overall)
- 🔍 Specific features to adopt from competitor
- ✅ Confidence in what you're already doing well

---

## Example 3: Camp 3 Readiness Check

### Scenario
You've iterated on your design multiple times. You think it's ready to ship. Time for the final Camp 3 gate check.

### Input
```
[Upload: checkout_flow_final.pdf]

"This is our new checkout flow - final version. 
Run /ux-scorecard with Camp 3 readiness check. 
We need a score of 3.5 or higher to ship. 
All usability testing is complete and changes are implemented."
```

### Expected Output
```
╔═══════════════════════════════════════════╗
║  UX SCORECARD RESULTS                     ║
║  Project: Checkout Flow Final             ║
║  Camp: 3 (Spec Review - Readiness Check)  ║
║  Evaluated: June 19, 2026                 ║
╠═══════════════════════════════════════════╣
║  OVERALL SCORE: 4.3 / 5.0                 ║
║  GRADE: B+ (Very Good)                    ║
╚═══════════════════════════════════════════╝

CAMP 3 GATE STATUS: ✅ READY TO SHIP ✅
Score of 4.3 EXCEEDS minimum requirement of 3.5

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCORECARD BREAKDOWN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ H1: Visibility of system status        │ 5  │ Excellent
✅ H2: Simplicity & clarity               │ 5  │ Excellent
✅ H3: User control & freedom             │ 4  │ Good
✅ H4: Error prevention & recovery        │ 4  │ Good
✅ H5: Efficiency of use                  │ 5  │ Excellent
✅ H6: Reinforce trust & safety           │ 4  │ Good
✅ H7: Real-time feedback                 │ 5  │ Excellent
⚠️  H8: Inclusive design                  │ 3  │ Average
✅ H9: Easy-to-learn features             │ 4  │ Good
✅ H10: Delight & confidence building     │ 4  │ Good

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CAMP 3 REQUIREMENTS CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ All Discovery steps completed
✅ All Design steps completed
✅ Design is "Complete" for customer use
✅ On-device prototype provided
✅ Content finalized (no placeholders)
✅ Illustrations finalized
✅ Usability testing completed
✅ Changes from testing implemented
✅ Minimum score 3.5 achieved (actual: 4.3)

All requirements met. This design is ship-ready.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRENGTHS (9 heuristics scoring 4+)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

This is a strong, well-executed design. Key strengths:

🌟 H1: System status (Score: 5)
   • Step-by-step progress indicator
   • Loading states with skeleton screens
   • Clear "Processing..." states with time estimates
   
🌟 H2: Simplicity (Score: 5)
   • One primary action per screen
   • Progressive disclosure (show only what's needed)
   • Clear, jargon-free language
   
🌟 H5: Efficiency (Score: 5)
   • Smart defaults (saved payment methods)
   • Autofill for returning customers
   • Quick checkout flow (3 taps to complete)
   
🌟 H7: Real-time feedback (Score: 5)
   • Inline validation as user types
   • Immediate error messages
   • Success confirmation with animation

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ONE AREA FOR POST-LAUNCH IMPROVEMENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚠️  H8: Inclusive design (Score: 3)
   Current state: Meets WCAG AA standards but not AAA.
   
   Observations:
   • Font size minimum is 14pt (good)
   • Color contrast ratio 4.5:1 (meets AA, not AAA)
   • No screen reader optimization yet
   
   Recommendation for v2:
   • Add screen reader labels for icons
   • Increase contrast to 7:1 for AAA compliance
   • Add "Skip to checkout" link for keyboard users
   
   Priority: LOW (can ship as-is, improve in next iteration)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FINAL DECISION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ APPROVED FOR PRODUCTION RELEASE

This checkout flow is ready to ship. With a score of 4.3 
(B+), it represents a high-quality user experience that will 
serve customers well.

The one area scoring 3 (Inclusive design) is acceptable for 
v1 launch. Plan to address screen reader optimization and 
AAA contrast in the next iteration.

Congratulations on shipping a well-designed feature! 🎉

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
POST-LAUNCH MONITORING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Track these metrics after launch:
• Checkout completion rate (expect >85%)
• Time to complete checkout (expect <2 min)
• Error rate on form fields (expect <5%)
• Customer satisfaction (NPS)
• Accessibility complaints

If metrics fall below expectations, re-run UX Scorecard 
analysis with real user feedback to identify issues.
```

### Takeaway
- ✅ Clear "GO" decision to ship
- 🎯 Strong score (4.3) exceeds minimum (3.5)
- 📋 One minor improvement flagged for v2
- 📊 Post-launch monitoring recommendations

---

## Example 4: Component Library Audit

### Scenario
You're the Design Ops lead. You want to audit the team's button component library for consistency and quality.

### Input
```
[Upload: button_library_figma.png]

"Audit our button component library using /ux-scorecard. 
This Figma frame shows all button variants: 
primary, secondary, text, disabled states, different sizes."
```

### Expected Output
```
╔═══════════════════════════════════════════╗
║  UX SCORECARD - COMPONENT LIBRARY AUDIT   ║
║  Component: Button Library                ║
║  Variants: 12 (Primary, Secondary, Text)  ║
╠═══════════════════════════════════════════╣
║  OVERALL SCORE: 3.8 / 5.0                 ║
║  GRADE: B (Good)                          ║
╚═══════════════════════════════════════════╝

Component library is generally solid but has some 
inconsistencies that should be addressed.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FINDINGS BY HEURISTIC
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ H2: Simplicity & clarity (Score: 5)
   • Clean, consistent visual design
   • Clear hierarchy (Primary > Secondary > Text)
   • Button labels are descriptive

✅ H5: Efficiency of use (Score: 4)
   • Good size variants (Small, Medium, Large)
   • Touch targets meet 44x44pt minimum

⚠️  H1: System status visibility (Score: 3)
   Issue: Disabled state uses gray, but "Processing" state 
          also uses gray with spinner. Confusing!
   Recommendation: Use different visual treatment for 
                   "Processing" state

⚠️  H3: User control & freedom (Score: 3)
   Issue: No "Loading with cancel" variant for long-running 
          operations
   Recommendation: Add button variant that shows loading 
                   state but remains tappable to cancel

⚠️  H4: Error prevention (Score: 3)
   Issue: "Destructive" variant (red button for delete actions) 
          missing from library
   Recommendation: Add red "Destructive" variant for actions 
                   that require extra caution

⚠️  H8: Inclusive design (Score: 3)
   Issue: Color contrast on "Text" button variant is 3.2:1 
          (below WCAG AA standard of 4.5:1)
   Recommendation: Darken text color to meet accessibility 
                   standards

✅ H10: Delight & confidence (Score: 4)
   • Nice hover states with smooth transitions
   • Success state with checkmark is delightful

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CONSISTENCY ANALYSIS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚠️  Inconsistency found:
   • Border radius: Primary uses 8px, Secondary uses 6px
   • Padding: Small has 12px horizontal, Medium has 16px, 
             Large has 20px (not proportional)
   
   Recommendation: Standardize border radius to 8px. Use 
                   consistent padding scale (12/16/24).

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MISSING STATES/VARIANTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Add these to make library complete:
1. Destructive variant (red button for delete/remove)
2. Ghost variant (transparent with border)
3. Icon-only variant (for compact UIs)
4. Loading with cancel variant
5. Focus state for keyboard navigation

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ACTION PLAN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

HIGH PRIORITY (Fix before next sprint):
1. Fix color contrast on Text variant (accessibility)
2. Standardize border radius across all variants
3. Fix padding inconsistency

MEDIUM PRIORITY (Add in next library update):
4. Add Destructive variant
5. Differentiate Processing vs Disabled visual states
6. Add Loading with cancel variant

LOW PRIORITY (Nice to have):
7. Add Ghost variant
8. Add Icon-only variant
9. Add focus state documentation

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ADOPTION RECOMMENDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Library is good enough for team use NOW, with caveat:
   • Fix the 3 high-priority issues before wider rollout
   • Document the missing variants so designers know gaps
   
Current score: 3.8 (B - Good)
With high-priority fixes: Estimated 4.2 (B+ - Very Good)
```

### Takeaway
- 📊 Component library scored objectively
- ⚠️  Specific inconsistencies identified
- 📋 Prioritized action plan
- ✅ Clear recommendation on adoption readiness

---

## Tips for Best Results

1. **Provide Context**: Mention Camp stage, project type, specific concerns
2. **Multiple Angles**: Upload multiple screens/flows for comprehensive review
3. **Be Specific**: "Focus on error handling" yields better feedback than generic review
4. **Iterate**: Re-score after implementing feedback to track improvement
5. **Multi-Evaluator**: For critical projects, have 2-3 people score independently

---

## Common Patterns

| Use Case | Minimum Score | Typical Range |
|----------|---------------|---------------|
| Self-review before critique | N/A | 3.0 - 4.0 |
| Camp 2 gate | 3.0 | 3.0 - 4.0 |
| Camp 3 gate | 3.5 | 3.5 - 4.5 |
| Component library | 3.5 | 3.5 - 4.5 |
| Competitor benchmark | N/A | 3.0 - 4.5 |
| Shipped product | 4.0+ | 4.0 - 5.0 |

---

## What Makes a Good Scorecard Request?

### ✅ Good
```
"Review this checkout flow (checkout_v3.pdf) for Camp 3. 
We've addressed all Camp 2 feedback. Main concerns: 
accessibility and error prevention."
```
- Clear context (Camp 3)
- Input provided (PDF)
- Specific focus areas mentioned

### ❌ Not Ideal
```
"Review this design"
```
- No context
- No input provided
- No specific concerns

---

For more examples, see the main README.md or SKILL.md file.
