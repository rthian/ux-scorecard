# UX Scorecard Installation Guide

Quick guide to get the UX Scorecard skill up and running in your Claude Code environment.

---

## Prerequisites

- ✅ Claude Code CLI installed
- ✅ Figma MCP server (optional, for Figma file reviews)
- ✅ Access to the uxscorecard directory

---

## Installation Steps

### Step 1: Install the Skill

Choose **Option A** (recommended) or **Option B**:

#### Option A: Symlink (Recommended)

This keeps the skill in the project directory while making it available to Claude Code. Updates to SKILL.md automatically reflect in Claude Code.

```bash
# Create symlink
ln -s /Users/yewmun.thian/Desktop/Make/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md

# Verify it worked
ls -la ~/.claude/skills/ | grep ux-scorecard
```

#### Option B: Copy

This creates an independent copy. You'll need to manually update if SKILL.md changes.

```bash
# Copy skill file
cp /Users/yewmun.thian/Desktop/Make/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md

# Verify it worked
ls -la ~/.claude/skills/ | grep ux-scorecard
```

---

### Step 2: Verify Installation

Open Claude Code and check if the skill is available:

```bash
claude

# In Claude Code, type:
"List all available skills"

# You should see "ux-scorecard" in the list
```

---

### Step 3: Test the Skill

Try a basic test:

```bash
# Option 1: Test with the playbook PDF
"Using /ux-scorecard, analyze any design example from the playbook PDF"

# Option 2: Test with a screenshot
[Upload a UI screenshot]
"Run /ux-scorecard on this design"

# Option 3: Test with Figma (if MCP installed)
"/ux-scorecard https://figma.com/file/YOUR-FILE-ID --camp=2"
```

---

## Optional: Install Figma MCP Server

To enable Figma file analysis, install the Figma MCP server:

### Step 1: Install Figma MCP

```bash
# Using npm
npm install -g @anthropic/mcp-server-figma

# Or using the Claude Code plugin manager
claude plugins install figma
```

### Step 2: Configure Figma Access

```bash
# Set your Figma access token
export FIGMA_ACCESS_TOKEN="your-figma-token"

# Or add to your ~/.zshrc or ~/.bashrc:
echo 'export FIGMA_ACCESS_TOKEN="your-figma-token"' >> ~/.zshrc
source ~/.zshrc
```

### Step 3: Get Your Figma Access Token

1. Go to https://figma.com/developers/apps
2. Create a new app or use existing
3. Copy the "Personal Access Token"
4. Use the token in Step 2 above

---

## Troubleshooting

### Skill Not Found

**Problem**: Claude Code says "skill not found" when you invoke `/ux-scorecard`

**Solutions**:
1. Check if file exists: `ls -la ~/.claude/skills/ux-scorecard.md`
2. Check if file has correct extension (`.md` not `.txt`)
3. Restart Claude Code: `exit` then `claude`
4. Check file permissions: `chmod 644 ~/.claude/skills/ux-scorecard.md`

### Figma MCP Not Working

**Problem**: Figma URL analysis fails

**Solutions**:
1. Verify Figma MCP is installed: `npm list -g | grep figma`
2. Check token is set: `echo $FIGMA_ACCESS_TOKEN`
3. Test token manually: `curl -H "X-Figma-Token: $FIGMA_ACCESS_TOKEN" https://api.figma.com/v1/me`
4. Check Figma file permissions (must be accessible to your account)

### PDF Reading Issues

**Problem**: Claude Code can't read uploaded PDFs

**Solutions**:
1. Check PDF size (max ~10MB recommended)
2. Try splitting large PDFs into smaller sections
3. Use image screenshots instead as alternative
4. Verify PDF is not password-protected

---

## File Structure

After installation, you should have:

```
~/.claude/skills/
└── ux-scorecard.md              # The skill definition (symlink or copy)

/Users/yewmun.thian/Desktop/Make/uxscorecard/
├── SKILL.md                     # Original skill definition
├── README.md                    # Project documentation
├── INSTALLATION.md              # This file
├── USAGE_EXAMPLES.md            # Detailed usage examples
├── SCORECARD_TEMPLATE.md        # Manual scoring template
└── 00 Product Design Regional Playbook (1).pdf
```

---

## Testing Your Installation

### Test 1: Basic Invocation

```bash
claude

# In Claude Code:
"What is the /ux-scorecard skill?"

# Expected: Claude explains the skill
```

### Test 2: Heuristics Check

```bash
"What are the 10 heuristics in the /ux-scorecard framework?"

# Expected: Claude lists all 10 heuristics with descriptions
```

### Test 3: Scoring Explanation

```bash
"Explain the scoring system for /ux-scorecard"

# Expected: Claude explains 1-5 scale and badge levels
```

### Test 4: Actual Review (Final Test)

```bash
[Upload any UI screenshot or PDF]

"/ux-scorecard - Review this design for Camp 2"

# Expected: Full scorecard output with scores, findings, recommendations
```

---

## What's Next?

After successful installation:

1. **Read**: [USAGE_EXAMPLES.md](./USAGE_EXAMPLES.md) for detailed usage patterns
2. **Try**: Run the skill on a real design from your team
3. **Share**: Introduce the skill to your design team
4. **Calibrate**: Run scoring sessions to align on interpretation
5. **Integrate**: Add to your Camp review workflows

---

## Team Rollout (For Design Leads)

### Week 1: Pilot
- Install skill for 2-3 designers
- Test on recent designs
- Collect feedback

### Week 2: Calibration
- Run calibration session with team
- Score 3-5 reference designs together
- Align on scoring interpretation

### Week 3: Team Rollout
- Install for entire team
- Update Camp review process
- Create scored example library

### Week 4: Integration
- Add to Design Weekly workflow
- Integrate with Jira/Confluence
- Track team average scores

---

## Support

If you encounter issues:

1. **Check Documentation**:
   - [README.md](./README.md) - Overview and quick start
   - [USAGE_EXAMPLES.md](./USAGE_EXAMPLES.md) - Detailed examples
   - [SKILL.md](./SKILL.md) - Complete skill specification

2. **Test Components**:
   - Can Claude Code read PDFs? Test with any PDF
   - Can you invoke other skills? Test with `/help`
   - Is the file in the right location? Check `~/.claude/skills/`

3. **Contact**:
   - Design Ops lead
   - Regional Design Team
   - [Your internal support channel]

---

## Updates

To update the skill when changes are made:

### If you used Symlink (Option A):
```bash
# No action needed! Changes to SKILL.md automatically reflect
# Just restart Claude Code to pick up changes
exit
claude
```

### If you used Copy (Option B):
```bash
# Re-copy the updated file
cp /Users/yewmun.thian/Desktop/Make/uxscorecard/SKILL.md ~/.claude/skills/ux-scorecard.md

# Restart Claude Code
exit
claude
```

---

## Version Tracking

Keep track of skill versions:

```bash
# Add to SKILL.md footer:
**Version**: 1.0
**Last Updated**: June 19, 2026
**Changelog**: Initial release
```

Update version number when making significant changes to the skill.

---

**Ready to use!** 🎉

Start with `claude` and then try: 
```
"Let's test /ux-scorecard with a design review"
```
