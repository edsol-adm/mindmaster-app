# 🔒 ****Mobile Standard - Coder Version v1.0****

**Viewport (required on every page)**

&lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;

**Page layout rules**

- Use min-height: 100vh for main wrappers.
- Do NOT use height: 100vh on full-page containers unless required by a game canvas.
- Do NOT use overflow: hidden on &lt;body&gt; or any full-page wrapper.
- Pages must scroll when content exceeds viewport height.

**Images / Video / Canvas**

img, video, canvas {

max-width: 100%;

height: auto;

}

- Do NOT assign large fixed pixel heights to these elements on mobile.

**Breakpoints (only these)**

@media (max-width: 600px) { /\* phones \*/ }

@media (min-width: 601px) and (max-width: 900px) { /\* small tablets \*/ }

@media (max-width: 900px) and (orientation: landscape) { /\* landscape phones \*/ }

**Landscape behaviour**  
Within the landscape breakpoint:

- Reduce vertical padding on tall containers/cards.
- Use max-height: 88vh for tall components (cards, content blocks, game UI).
- Shrink decorative images (e.g., character images) if they cause clipping.

**Touch interaction**

- Buttons and tappable elements MUST be at least ~44px tall.
- No hover-only required interactions.
- Do NOT globally block scrolling with:

event.preventDefault()

on touchmove or pointermove.

- Restrict preventDefault to specific game elements only when necessary.

**Game layout**

- Use %, vw, vh, flexbox, or grid for game UI.
- Avoid layouts that rely entirely on fixed pixel positions.
- Games MUST be fully playable with touch (use pointer events rather than mouse-only events).