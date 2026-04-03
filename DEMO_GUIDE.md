# Landing Page Jam: Demo Facilitator's Guide

A detailed walkthrough for running this as a ~20-minute live demo for designers learning async collaboration in code.

---

## Pre-Demo Setup (5 minutes before)

### 1. Prepare the environment

- [ ] Clone this repo to two separate directories (or have two people with their own clones)
- [ ] Open two terminal windows side by side
- [ ] Open `index.html` in a browser tab (drag it in)
- [ ] Have `styles.css` open in an editor for reference
- [ ] Clear any existing branches besides `main`: `git branch -D feature/*` (if re-running)

### 2. Set the stage

**What to say:**

> "We're going to build a landing page together, but we're not working in Figma. We're working in code, asynchronously, the way you might in the near future.
>
> This isn't about learning git commands. It's about discovering what's different when you can't see each other's cursors."

**Show the starting state:**

- Browser: styled skeleton with header, footer, two empty sections
- Terminal: `git log --oneline` (should show one commit)
- Editor: Open `styles.css` and scroll through the design tokens

**Key point:** "These CSS variables are your design system. Just like Figma variables. We'll both build from them."

---

## Phase 1: Build in Parallel (7-8 minutes)

### Setup

**Person A:**
```bash
cd /path/to/landing-page-jam-1
git checkout -b feature/hero
```

**Person B:**
```bash
cd /path/to/landing-page-jam-2
git checkout -b feature/pricing
```

**What to say:**

> "We just branched. Person A is working on the hero, Person B is working on pricing. In Figma, you'd both be on the same file with different frames. Here, you're on separate branches.
>
> You can't see what the other person is doing until they share it."

### Build the sections

**Person A asks Claude Code:**
> "Build a hero section with a headline, subtitle, and CTA button using the design tokens in styles.css"

**Person B asks Claude Code:**
> "Create a 3-tier pricing table using the shared variables from styles.css"

**While Claude builds, narrate:**
- "Both of you are using the same design tokens — same colors, same spacing, same typography"
- "But you have no idea what the other person's section looks like yet"
- "In Figma, you'd see their cursor. Here, you're blind to each other's work."

**Timing note:** Claude should build each section in ~2 minutes. If it goes longer, have pre-built versions ready to paste in.

### Commit and push

**Person A:**
```bash
git add index.html
git commit -m "Add hero section with headline and CTA"
git push -u origin feature/hero
```

**Person B:**
```bash
git add index.html
git commit -m "Add 3-tier pricing table"
git push -u origin feature/pricing
```

**What to say:**

> "You've both pushed your branches. Now open PRs."

### Open PRs (can simulate this or use GitHub)

If using GitHub:
- Have both people open PRs with screenshots
- Show the PR list: two open PRs, no conflicts yet

If simulating:
- Just show the branches: `git branch -a`
- Say: "Imagine these are PRs with screenshots attached"

---

## Discussion Break 1: Code Review as Design Review (3 minutes)

**Pause here. Don't merge yet.**

**What to say:**

> "Before merging, you'd review each other's PRs. Let's talk about what that's like."

**Prompt the group:**

1. **"How is a PR comment different from a Figma comment?"**
   - Wait for answers
   - Key insight: PR comments can block merging (Request Changes), Figma comments can't

2. **"What if Person A hardcoded a color instead of using `--color-primary`?"**
   - Wait for answers
   - Key insight: Do you block the merge? Or approve and fix it later? There's a choice.

3. **"In Figma, you'd just tag someone. Here, you have three options: Comment, Approve, Request Changes. When do you use each?"**
   - Let them discuss
   - No right answer — this is team culture

**Don't dwell too long. Move on after 2-3 minutes of discussion.**

---

## Phase 1 Conclusion: The Merge (2 minutes)

**Merge both PRs** (or simulate):

**Person A:**
```bash
git checkout main
git merge feature/hero
git push origin main
```

**Person B:**
```bash
git checkout main
git pull origin main  # Get Person A's changes
git merge feature/pricing
git push origin main
```

**Refresh the browser.**

**What to say:**

> "Look — both sections are there. They look cohesive. Same colors, same spacing, same typography. You used the same design system even though you worked independently.
>
> This is the feel-good moment."

**Show a quick diff:**
```bash
git log --oneline -3
git diff HEAD~2 HEAD
```

Point out: "Person A only touched the hero. Person B only touched pricing. Clean separation."

---

## Phase 2: Competing Directions (5 minutes)

### Setup

**Person A:**
```bash
git checkout -b experiment/coral-primary
```

**Person B:**
```bash
git checkout -b experiment/teal-primary
```

**What to say:**

> "Now you're both going to change the same design token independently. You don't know the other person is doing this because you can't see their cursor."

### Make the changes

**Person A** edits `styles.css`:
```css
--color-primary: #F97316; /* coral */
```

**Person B** edits `styles.css`:
```css
--color-primary: #14B8A6; /* teal */
```

Both commit and push. Both open PRs with screenshots.

**What to say:**

> "Two PRs, two different directions. Let's say the team reviews both and picks teal."

**Merge Person B's PR:**
```bash
git checkout main
git merge experiment/teal-primary
git push origin main
```

**Refresh the browser.**

**Show the ripple:**

> "The primary color changed everywhere:
> - Hero buttons (Person A's section)
> - Pricing cards (Person B's section)  
> - Header 'Sign In' link
>
> One line of CSS, multiple sections update. That's the power of design tokens."

---

## Discussion Break 2: Governance & Coordination (4 minutes)

**Pause here. Point to the open coral PR.**

**What to say:**

> "We merged teal. Person A's coral PR is still open — it's the rejected direction."

**Prompt the group:**

### 1. "Who gets to change `--color-primary`?"

Wait for answers. Key tensions:
- Should anyone be able to change shared tokens?
- Should there be a design system owner?
- Should changes require team discussion first?

### 2. "How did two people end up changing the same thing?"

Wait for answers. Key insight:
- In Figma, you'd see each other's cursors and coordinate
- In async work, you need to communicate intent before starting ("I'm exploring coral")
- Or accept that conflicts will happen and deal with them

### 3. "What do we do with the rejected coral branch?"

**This is the big question.** Close the PR? Delete the branch? Keep it around?

**Prompt deeper:**

> "In Figma, you'd keep the coral exploration on a page called 'Color Experiments' and scroll to it anytime. Can you do that here?"

Wait for answers. Key tension:
- **The branch is just code.** You can't see what it looks like without running it.
- **The screenshot in the PR is the only visual record.**
- Is that enough? Or do you need a separate visual archive (wiki, Notion, Figma file) that links back to branches?

**What to say:**

> "Code isn't browsable the way Figma is. This is a real gap. Different teams solve it differently. Some keep screenshots in PRs. Some maintain a visual wiki. Some just accept that old explorations are harder to browse.
>
> There's no standard answer yet."

**Don't solve this for them.** Let it sit as an open question.

---

## Discussion Break 3: Staying in Sync (Optional, 2 minutes)

**If time permits, raise this scenario:**

**What to say:**

> "Imagine Person A branched on Monday and worked on the hero for three days. Person B merged five design system updates in that time — new spacing tokens, updated colors, etc.
>
> Person A opens their PR. It uses the old tokens. What should happen?"

**Prompt:**
- Should Person A have been pulling `main` every day?
- Should Person B have announced: "I'm updating the design system, everyone sync before continuing"?
- How do you stay in sync when you can't see each other working?

**Key insight:** Async work requires **deliberate coordination**. In real-time tools, you're always synced. In git, you have to choose to sync.

---

## Wrap-Up (2 minutes)

**What to say:**

> "By now you've felt three big differences from Figma:
>
> 1. **Feedback happens in PRs, not real-time comments.** And PRs have mechanics — approve, request changes, comment threads. You have to learn when to block vs. when to suggest.
>
> 2. **You can't see each other working.** Async collaboration requires more communication than Figma. You have to announce what you're doing, coordinate on shared changes, and pull updates deliberately.
>
> 3. **Code isn't visually browsable.** Figma lets you scroll through old explorations. Git branches are just text files. If you want a visual history, you have to build it yourself.
>
> None of these have universal answers. The goal today was to surface the questions early so you can start thinking about how your team will handle them."

**End with an open question:**

> "What's one thing you'll do differently now that you've felt these tensions?"

Let a few people answer. Don't prescribe solutions.

---

## Tips for Facilitation

### Before the demo
- **Practice the timing.** 20 minutes is tight. Know where you can skip ahead if needed.
- **Have pre-built sections ready** in case Claude Code takes too long.
- **Test the browser refresh flow** — make sure changes show up immediately.

### During the demo
- **Resist the urge to teach git commands.** This isn't a git tutorial. It's about collaboration culture.
- **Let silence sit.** When you ask a question, wait 5+ seconds. Don't jump in with the answer.
- **Follow their energy.** If the group is stuck on one question, go deeper. If they're ready to move on, move on.
- **Don't solve the "how to preserve explorations" question.** It's genuinely unsolved. Let it be an open question.

### If things go wrong
- **Merge conflict:** Great! Show it. Talk about how it's not a technical problem, it's a design decision problem.
- **Claude builds something ugly:** Perfect. Talk about how code review catches this.
- **Someone accidentally deletes their work:** Even better. Real stakes. Talk about how git protects you (`git reflog`), but only if you've committed.

### If you have extra time
- Show `git diff main..feature/hero` to visualize changes
- Show PR comments on specific lines of code
- Demonstrate a rebase workflow (advanced)
- Let them ask Claude Code: *"What changed in this PR?"*

### If you're running short on time
- Skip Discussion Break 3 (staying in sync)
- Merge PRs without opening GitHub (just use terminal)
- Pre-build the sections instead of having Claude do it live

---

## Common Questions & How to Handle Them

**"Should we use tags to mark explorations?"**  
> "That's one approach. What would that look like in practice? How would you browse them later?"

**"Can't we just use Figma for explorations and code for production?"**  
> "You could. But then you're context-switching. And the Figma explorations won't have real data, real performance, real responsive behavior. There are tradeoffs."

**"What if we just record videos of each branch?"**  
> "Try it! See if that works for your team. This is genuinely unsolved — experiment."

**"Isn't this way slower than Figma?"**  
> "For some things, yes. For others — like testing with real data, seeing real performance, building with real constraints — code is faster. It's a different tool for a different part of the process."

**"Do engineers actually work this way?"**  
> "Engineers use git, yes. But they don't have the same visual browsability problem because their artifact IS the code. Your artifact is what the code produces. That's the gap."

---

## Post-Demo: What to Share

After the demo, share:
- Link to this repo for them to fork and try themselves
- A note that says: "We didn't solve the visual browsability problem today. If your team figures out a good pattern, share it."
- Optional: A Slack channel or doc for sharing team norms as they develop them

---

## Success Metrics

The demo worked if:
- ✅ People can articulate the difference between real-time and async collaboration
- ✅ Someone says "oh, so PRs are where design decisions happen now"
- ✅ The "how do we preserve explorations?" question gets raised and doesn't get answered
- ✅ At least one person says they want to try this on a real project

The demo failed if:
- ❌ People think git is just complicated Figma
- ❌ You spent more time explaining commands than discussing collaboration
- ❌ Everyone leaves thinking there's a "right way" to do this

---

**Go run the demo. See what questions come up. Iterate on this guide based on what you learn.**
