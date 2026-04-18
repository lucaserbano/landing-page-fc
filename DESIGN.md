```markdown
# Design System Document: Precision & Prestige

## 1. Overview & Creative North Star
**Creative North Star: "The Master’s Atelier"**
This design system rejects the clinical, sterile aesthetic of traditional medical templates in favor of a "High-End Editorial" experience. It treats the surgeon’s digital presence as a curated portfolio—an atelier where precision meets artistry. 

The system moves beyond the "template" look by utilizing **Intentional Asymmetry**. By breaking the rigid vertical grid with overlapping typography, staggered image placements, and organic section transitions, we create a sense of fluid movement and high-level bespoke craftsmanship. High negative space is not just "empty"; it is a luxury, providing the "breathing room" required for high-stakes professional trust.

---

## 2. Colors & Surface Philosophy
The palette is rooted in absolute authority (Black) and surgical precision (Gold), softened by academic depths (Deep Blue/Teal).

### The "No-Line" Rule
Explicitly prohibit 1px solid borders for sectioning. Structural boundaries must be defined solely through:
- **Tonal Shifts:** Transitioning from `surface` to `surface-container-low`.
- **Soft Masks:** Using large-scale organic gradients to transition between content blocks.
- **Negative Space:** Using a minimum of 120px vertical padding between disparate sections to signify a change in context.

### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers—like stacked sheets of fine vellum.
*   **Base:** `background` (#f9f9f9) for the primary reading experience.
*   **Elevation 1:** `surface-container-low` (#f3f3f3) for subtle content grouping.
*   **Elevation 2 (Floating):** `surface-container-lowest` (#ffffff) for high-focus cards.
*   **The "Glass & Gradient" Rule:** To achieve a premium feel, use `surface_tint` at 5% opacity with a `backdrop-blur(20px)` for navigation bars and floating action elements. Use a subtle linear gradient (from `primary` to `primary_container`) for main CTAs to provide a "metallic" gold sheen.

---

## 3. Typography
The typography is the architecture of this system. We use **Josefin Sans** for its unique geometric elegance and high x-height, which feels both modern and prestigious.

*   **Display (Large/Medium):** Set with `-0.05em` letter spacing and `1.1` line height. These are "Hero" statements meant to overlap image boundaries or bleed off the edge of the container to break the grid.
*   **Headlines:** Bold weights only. Used to anchor asymmetrical layouts.
*   **Body:** We swap to **Manrope** (per the token scale) for long-form readability, as its balanced proportions complement the stylistic flair of Josefin Sans without sacrificing legibility for medical information.
*   **Labels:** Always uppercase with `0.1em` letter spacing to evoke the feeling of a luxury brand mark.

---

## 4. Elevation & Depth
Depth is achieved through **Tonal Layering**, mimicking the soft shadows found in high-end architectural photography.

*   **The Layering Principle:** Place a `surface-container-lowest` card on top of a `surface-container-low` section. The contrast in brightness creates a "soft lift" that feels more sophisticated than a heavy shadow.
*   **Ambient Shadows:** For floating elements (e.g., "Book Consultation" cards), use a shadow: `0px 24px 48px rgba(27, 27, 27, 0.06)`. This mimics natural, diffused light.
*   **The "Ghost Border" Fallback:** If containment is required for accessibility, use the `outline-variant` token at **15% opacity**. A 100% opaque border is a failure of the system's elegance.
*   **Organic Transitions:** Section breaks should use CSS `clip-path` or SVG masks to create soft, wave-like or diagonal transitions, avoiding the "boxed-in" feeling of traditional grids.

---

## 5. Components

### Buttons
*   **Primary:** Background `primary` (#7c5800), text `on_primary` (#ffffff). Shape: `md` (0.375rem). Use a subtle gold-to-brass gradient.
*   **Secondary:** Background `transparent`, "Ghost Border" using `outline`. Text `primary`.
*   **Interaction:** On hover, primary buttons should scale 2% and increase shadow diffusion.

### Cards & Lists
*   **Forbid Divider Lines:** Use `1.5rem` to `2rem` of vertical whitespace between list items.
*   **Medical Accolades:** Use `tertiary_container` (#83bdb9) for background chips with `on_tertiary_container` (#0a4d4b) text for a sophisticated, muted professional look.

### Input Fields
*   **Style:** Underline-only or extremely soft `surface-container-high` backgrounds. 
*   **Focus State:** The label should animate to a `label-sm` using the `primary` (Gold) color. Avoid heavy focus rings; use a 2px `primary` bottom border.

### Signature Component: The "Floating Dossier"
A layout pattern where a surgical case study (Image) is positioned off-center, with a `surface-container-lowest` text card overlapping 20% of the image. This creates depth and breaks the "photo-left-text-right" cliché.

---

## 6. Do's and Don'ts

### Do:
*   **Do** use asymmetrical layouts where the right margin is wider than the left.
*   **Do** use `primary` (Gold) sparingly—it is a scalpel, not a paintbrush. Use it for CTAs, icons, and critical emphasis.
*   **Do** utilize the `full` (9999px) roundedness for small "Status" or "Specialty" chips to contrast against the `md` roundedness of cards.

### Don't:
*   **Don't** use pure black (#000000) for body text; use `on_surface` (#1b1b1b) for better readability against the light background.
*   **Don't** use standard "Drop Shadows." If you can see the shadow clearly, it’s too heavy.
*   **Don't** use 1px dividers. If you need to separate content, use a background color shift or increased whitespace.
*   **Don't** align everything to a center axis. Modern surgical precision is about intentionality; use "Golden Ratio" offsets instead.

---
**Logo Reference:** Ensure the logo placeholder `{{DATA:IMAGE:IMAGE_1}}` is placed with a minimum of 40px padding-top/left to maintain its visual "sanctity."```