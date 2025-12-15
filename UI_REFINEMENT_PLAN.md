# UI Refinement Proposal for `index2.html`

Goal: reduce intimidation and make the flow truly step-by-step with minimal text, clear nucleus visibility, and quick particle identification.

## Current pain points
- The left control panel expands to the full viewport, obscuring the nucleus and confusing first-time users.
- All steps and missions are visible at once, creating cognitive overload and hiding the intended flow.
- Mission descriptions are long text blocks instead of icon-first cards; reaction buttons appear crowded and similar in weight.
- Nucleus/panel contrast is weak: the 3D scene competes with dense UI, and key actions are buried.
- Particle labeling is inconsistent—labels only appear during emission and can overlap the nucleus.

## Recommended layout changes (no code applied yet)
1. **Pinned, narrow sidebar (30–36% width) + floating tab toggles**
   - Collapse to a single column on mobile; add a chevron button to hide/show the panel so the nucleus remains visible.
   - Keep only the active step expanded; prior/next steps become compact bars with an icon and short label.

2. **Step-by-step reveal**
   - Step 1: Carousel of mission chips with icon, tag, and a one-line goal; selecting auto-scrolls to Step 2.
   - Step 2: Nucleus prep shows current isotope with a large icon and color-coded Z/A badges; sandbox selector hidden behind a "🔧 Sandbox" chip.
   - Step 3: Reaction actions as a 2x2 icon grid; disable irrelevant reactions with dimmed icons and a short tooltip.
   - Step 4: Equation bar docked at bottom with a single CTA; hint button becomes an icon (💡) with tooltip.

3. **Visual hierarchy and breathing room**
   - Reduce panel opacity and padding; add subtle blur to let the scene show through.
   - Use large emoji or SVG icons (🎯 mission, 🧬 nucleus, ⚡ reaction, ⚖️ balance) as step headers; keep text to 2–4 words.
   - Replace long descriptions with helper tooltips ("i" icons) to declutter.

4. **Particle clarity**
   - Always show a tiny legend pinned to a corner: proton (red), neutron (gray), beta (blue), gamma (cyan) with charge superscripts.
   - Add small billboards over any particle that leaves or touches the nucleus, offset so they never clip; include name + charge (e.g., "α, +2").
   - Differentiate particle trails by color and dash pattern to distinguish beta vs gamma emissions.

5. **Nucleus visibility improvements**
   - Introduce a faint vignette around the HUD edges and a brighter nucleus halo; lighten shell materials slightly.
   - Keep the camera closer and lock vertical orbit limits to prevent losing sight of the nucleus.
   - Add a brief "focus" animation when a mission loads to direct attention to the center.

6. **Progress + safety cues**
   - Move XP/Badges into a compact pill row at top-right; replace text meters with icon meters (⚡ energy, 🛡️ safety) showing bars.
   - Provide inline status chip under the step title (e.g., "Ready", "Needs mission", "Locked") instead of long sentences.

## Next steps after approval
- Implement the sidebar/tab structure and collapsible steps without touching Three.js logic.
- Re-theme buttons and chips to be icon-first and shorten all helper text into tooltips.
- Add persistent legend and improved billboard offset math for emitted particles.
- Tune camera/lighting to improve nucleus readability while reducing panel dominance.
