# Landing Page Jam

A collaboration exercise for designers working together in code. Two people build different sections of a landing page on separate branches, then merge them together.

Takes ~20 minutes. Works best with Claude Code.

---

## What's In Here

Three files on `main`:

- **`index.html`** — Skeleton page for "Beacon Analytics" with two empty sections (`#hero` and `#pricing`)
- **`styles.css`** — Shared design tokens as CSS variables (colors, spacing, typography, border radius)
- **`README.md`** — This file

Open `index.html` in a browser. You'll see a styled skeleton: header, footer, and two empty sections in between.

---

## The Exercise

### Phase 1: Build in Parallel

Two people, two terminals.

**Person A:**
```bash
git checkout -b feature/hero
```

Ask Claude Code:  
*"Build a hero section with a headline, subtitle, and CTA button using the design tokens in styles.css"*

**Person B:**
```bash
git checkout -b feature/pricing
```

Ask Claude Code:  
*"Create a 3-tier pricing table using the shared variables from styles.css"*

Both push, open PRs, review each other's work, and merge into `main`.

Pull latest `main` and open the page. Both sections should look cohesive — you're using the same design tokens.

---

### Phase 2: Competing Directions

Both branch off `main` again.

**Person A:**  
Change `--color-primary` to coral (`#F97316`), commit, open a PR with a screenshot.

**Person B:**  
Change `--color-primary` to teal (`#14B8A6`), commit, open a PR with a screenshot.

Look at both PRs side by side. Pick one (say, teal). Merge it.

Now you have a rejected direction sitting in an open PR. What do you do with it?

---

## Questions You'll Encounter

This exercise will surface some tensions between Figma's real-time collaboration and git's async workflow:

**On PR Reviews:**
- How is leaving a PR comment different from a Figma comment?
- What's the difference between "Comment," "Approve," and "Request Changes"?
- When do you block a merge vs. just leave a suggestion?

**On Design System Governance:**
- Should two people be able to change `--color-primary` independently?
- Who approves changes to shared tokens?
- How do you coordinate when you can't see each other's cursors?

**On Preserving Explorations:**
- In Figma, rejected variants live on an "Explorations" page. Where do they live in git?
- A branch is just code — you can't see what it looks like without running it.
- Is a screenshot in a closed PR enough? Or do you need a separate visual archive?

**There are no universal answers.** Different teams will develop different norms. The goal is to recognize these questions early.

---

## Helpful Claude Code Prompts

**Understanding the design system:**
- *"What CSS variables are available in styles.css?"*
- *"Show me where --color-primary is being used"*

**During code review:**
- *"What changed in this PR?"*
- *"Explain the difference between this branch and main"*

**When things break:**
- *"Help me resolve this merge conflict"*
- *"Why doesn't this look the same as the other person's section?"*

**Iterating:**
- *"Make the hero responsive with a mobile breakpoint"*
- *"Add hover states to the pricing cards using the design tokens"*

---

## Tips

- Open `index.html` directly in your browser (drag it in) — no server needed
- Use the browser inspector to see CSS variables in action
- Look at `git diff` to see exactly what changed
- Try running the exercise solo (build both sections on different branches) to get the full experience

---

**Looking to facilitate this as a demo?** See [DEMO_GUIDE.md](DEMO_GUIDE.md) for a detailed walkthrough with timing and discussion prompts.
