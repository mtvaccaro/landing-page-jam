# Landing Page Jam

A minimal collaborative design exercise for working with shared styles in git.

## The Exercise

This is a skeleton landing page for "Beacon Analytics" with shared design tokens but empty sections. Two people will each build one section on separate branches, then merge them together to see how shared styles create cohesion.

### How it works

1. **Both people start on `main`**  
   Open `index.html` in a browser — you'll see a header, footer, and two empty sections in between.

2. **Split up and branch**
   - **Person A**: `git checkout -b feature/hero`
   - **Person B**: `git checkout -b feature/pricing`

3. **Build your section with Claude Code**  
   Each person builds their section using the design tokens already defined in `styles.css`.

   **Example prompts:**
   - Person A: *"Build a hero section with a big headline, subtitle, and two CTA buttons. Use the design tokens from styles.css"*
   - Person B: *"Create a 3-tier pricing table (free, pro, enterprise) using the shared variables from styles.css"*

4. **Push and open PRs**  
   Both people push their branches and open pull requests.

5. **Merge both PRs into main**  
   Once merged, open the combined page — everything should look cohesive because you're both using the same design system.

---

## Bonus Round: The Style Ripple

Here's where it gets interesting.

**Person A** makes a new branch and changes `--color-primary` in `styles.css` from purple (`#7C3AED`) to something else — try a coral (`#F97316`) or teal (`#14B8A6`).

Push it and open a PR. Preview the page.

**What happened?** The color change ripples through:
- The hero section (Person A's work)
- The pricing section (Person B's work)
- The header nav's "Sign In" link

This shows the power of shared design tokens — change it once, it updates everywhere.

**But wait...** Person B notices the new primary color breaks the contrast on their pricing cards, or looks weird on a border. Maybe some elements need their own variable instead of relying on `--color-primary`.

**Person B** can now review the PR and collaborate on a fix:
- Add a new variable like `--color-border-accent` or `--color-card-border`
- Update the pricing section to use it
- Push the changes and discuss

This mirrors real-world design system work: shared tokens are powerful, but require coordination and thoughtful scoping.

---

## Example Prompts to Try

As you go through the exercise, here are some things to ask Claude Code:

**While building:**
- *"What CSS variables are available in styles.css?"*
- *"Add a hover effect to the pricing cards using the design tokens"*
- *"Make the hero section responsive with a mobile breakpoint"*

**During code review:**
- *"What changed in this PR?"*
- *"Show me where --color-primary is being used"*

**When merging:**
- *"Help me resolve this merge conflict"*

**During the bonus round:**
- *"Change the primary color to coral and show me what will be affected"*
- *"The primary color change broke the pricing card contrast — add a separate border color variable and update my section to use it"*
- *"Suggest a color palette that would work better than purple for a data analytics product"*

---

## Tips

- Open `index.html` directly in your browser (just drag it in) — no server needed
- Check the browser's inspector to see the CSS variables in action
- Look at the git diff to see exactly what each person changed
- Try building both sections yourself on different branches to get the full experience

Have fun!
