# Lusion.co — Framer Build Prompts
# Copy each prompt one at a time into the Claude Chrome Extension while inside Framer.
# Complete each step before moving to the next.

---

## PROMPT 1 — Project Setup & Colors

```
I'm building a website in Framer inspired by lusion.co.
Help me set up the project foundation.

1. Set canvas background to #F0F1FA (light lavender — NOT white)

2. Open Variables panel and create these color variables:
   - BgPrimary: #F0F1FA
   - BgDark: #22232E
   - BgFooter: #1C1D21
   - TextPrimary: #1C1D21
   - TextSub: #42444B
   - AccentBlue: #1A2FFB
   - AccentBlueDeep: #0016EC
   - BtnDark: #2B2E3A
   - White: #FFFFFF

3. In Custom CSS (Project Settings → Custom Code), paste:
* { cursor: none; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body { background: #F0F1FA; color: #1C1D21; font-family: 'Plus Jakarta Sans', sans-serif; }
::selection { background: #1A2FFB; color: #fff; }
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: rgba(0,0,0,0.1); }
::-webkit-scrollbar-thumb { background: rgba(0,0,0,0.47); border-radius: 2px; }

Walk me through each step in Framer right now.
```

---

## PROMPT 2 — Fonts & Typography

```
I'm building a Lusion.co inspired site in Framer. Set up the typography.

1. Go to Fonts panel → Add Google Fonts:
   - "Plus Jakarta Sans" (weights: 300, 400, 600, 700)
   - "DM Mono" (weight: 400)

2. Set global text defaults:
   - Font: Plus Jakarta Sans
   - Size: 14px
   - Weight: 400
   - Line height: 1.6
   - Color: #1C1D21

3. Create these Text Styles in Framer:
   - Hero: Plus Jakarta Sans, clamp(48px,9vw,140px), weight 400, line-height 0.95, letter-spacing -0.03em
   - H2: Plus Jakarta Sans, clamp(32px,5vw,72px), weight 400, line-height 1.05, letter-spacing -0.02em
   - H3: Plus Jakarta Sans, clamp(20px,3vw,36px), weight 400, line-height 1.1
   - Body: Plus Jakarta Sans, 14px, weight 300, line-height 1.6, color #42444B
   - NavLink: Plus Jakarta Sans, 14px, weight 400, color #42444B
   - Label: DM Mono, 12px, uppercase, letter-spacing 0.1em, color #42444B
   - LoadingNum: DM Mono, 6rem (96px), weight 400, color #1C1D21

Guide me through each step in Framer.
```

---

## PROMPT 3 — Loading Screen

```
I'm building a Lusion.co inspired site in Framer. Build the loading screen.

Design specs:
- Full screen frame: 100vw × 100vh, background #F0F1FA
- Centered content stack (vertical, center aligned):

  1. Number display: "000" → animates to "100"
     DM Mono, 96px, weight 400, color #1C1D21
     
  2. Thin progress bar below number:
     Width starts at 0, animates to 240px
     Height: 1px
     Color: #1A2FFB
     Margin-top: 24px

Animation sequence:
- On page load: progress bar grows 0→240px over 1.8s (ease in out)
- Number increments from 0 to 100 in sync (1.8s)
- After 2s total: loading frame scales up slightly (scale 1→1.05) and fades out (opacity 1→0) over 0.5s
- Main page appears underneath

Make this as a Framer component called "LoadingScreen".
Walk me through building it step by step in Framer.
```

---

## PROMPT 4 — Navigation Bar

```
I'm building a Lusion.co inspired site in Framer. Build the navigation bar.

Specs:
- Frame: 100% wide, fixed position, top 0, z-index 1000
- Padding: 24px 4vw (use 24px top/bottom, 4% left/right)
- Background: transparent by default

On scroll (add variant "scrolled"):
- Background: rgba(240,241,250,0.85)
- backdrop-filter: blur(12px)
- Transition: 0.3s ease

Left side — Logo:
- Text: "LUSION"
- Font: Plus Jakarta Sans, 16px, weight 700, color #1C1D21
- Letter spacing: -0.02em

Right side — nav links in a row, gap 32px:
- "About Us" / "Projects" / "Labs" / "Contact"
- Font: Plus Jakarta Sans, 14px, weight 400, color #42444B
- Hover: color #1A2FFB, transition 0.2s

Far right — CTA pill button:
- Text: "Let's Talk →"
- Background: #2B2E3A
- Color: #FFFFFF
- Border-radius: 26px
- Padding: 10px 20px
- Font: 14px
- Hover: background #0016EC, transition 0.2s

Build this step by step in Framer.
```

---

## PROMPT 5 — Hero Section

```
I'm building a Lusion.co inspired site in Framer. Build the hero section.

Specs:
- Frame: 100vw × 100vh, background #F0F1FA
- Background layer: add a full-bleed canvas/video placeholder (#E8E9F5 rectangle) — I'll swap in a 3D scene later

Content block — centered or bottom-left, padding 4vw:

  1. Overline:
     "AWARD WINNING 3D AND INTERACTIVE WEB STUDIO"
     DM Mono, 12px, uppercase, letter-spacing 0.1em, color #42444B
     Display: flex, align-items center, gap 12px
     Add a 32px × 1px line before it (color #42444B)
     Margin-bottom: 24px

  2. H1:
     "Realise Your\nCreative Ideas"
     Plus Jakarta Sans, clamp(48px,9vw,140px), weight 400, line-height 0.95
     Color: #1C1D21
     Margin-bottom: 32px

  3. Subtext:
     "We design and produce 3D visual storytelling, immersive websites, and interactive digital experiences."
     Plus Jakarta Sans, 14px, weight 300, color #42444B, max-width 480px
     Margin-bottom: 40px

  4. Two buttons side by side, gap 16px:
     Button A — "View Our Work"
       Background: #2B2E3A, color #FFF, border-radius 26px, padding 14px 28px
       Hover: background #0016EC
     Button B — "Play Reel ▶"
       Background: transparent, color #1C1D21
       Border: 1px solid rgba(28,29,33,0.2), border-radius 26px, padding 14px 28px
       Hover: border-color #1A2FFB, color #1A2FFB

  5. Scroll indicator at bottom center:
     Text: "SCROLL" — DM Mono 11px uppercase letter-spacing 0.15em color #42444B
     Animated arrow below, bouncing gently

Scroll-in animation (stagger, use Framer appear):
- Each element: opacity 0→1, y 30→0, duration 0.8s
- Stagger: 0.2s between items
- Easing: [0.16, 1, 0.3, 1]

Build this step by step in Framer.
```

---

## PROMPT 6 — Holographic Cursor Trail

```
I'm building a Lusion.co inspired site in Framer.
Add the signature holographic cursor trail effect.

Create a Code Component called "LusionCursor" with this code:

import { useEffect, useRef } from "react"

export default function LusionCursor() {
  const canvasRef = useRef(null)
  useEffect(() => {
    const canvas = canvasRef.current
    const ctx = canvas.getContext("2d")
    const resize = () => { canvas.width = window.innerWidth; canvas.height = window.innerHeight }
    resize()
    window.addEventListener("resize", resize)
    let points = []
    const colors = ["#1A2FFB","#7B6FFF","#A855F7","#EC4899","#06B6D4","#3B82F6"]
    const onMove = (e) => {
      points.push({ x: e.clientX, y: e.clientY, age: 0, color: colors[Math.floor(Math.random()*colors.length)] })
      if (points.length > 50) points.shift()
    }
    const animate = () => {
      ctx.clearRect(0, 0, canvas.width, canvas.height)
      points.forEach(p => {
        p.age++
        const alpha = Math.max(0, 1 - p.age / 50)
        const size = Math.max(0, 10 - p.age * 0.2)
        ctx.beginPath()
        ctx.arc(p.x, p.y, size, 0, Math.PI * 2)
        ctx.fillStyle = p.color + Math.floor(alpha * 255).toString(16).padStart(2,"0")
        ctx.fill()
      })
      points = points.filter(p => p.age < 50)
      requestAnimationFrame(animate)
    }
    window.addEventListener("mousemove", onMove)
    animate()
    return () => { window.removeEventListener("mousemove", onMove); window.removeEventListener("resize", resize) }
  }, [])
  return <canvas ref={canvasRef} style={{ position:"fixed", inset:0, pointerEvents:"none", zIndex:9999, mixBlendMode:"multiply" }} />
}

Also add a small dot cursor (8px circle, #1A2FFB) that follows the mouse precisely.

Add both to the page as fixed overlays. Walk me through this in Framer.
```

---

## PROMPT 7 — Project Cards with Scroll Skew

```
I'm building a Lusion.co inspired site in Framer. Build the Featured Work section.

Section wrapper:
- Background: #F0F1FA
- Padding: 96px 4vw

Section header row (flex, space-between):
- Left: Label "Featured Work" — Plus Jakarta Sans, H2 size clamp(32px,5vw,64px), color #1C1D21
- Right: "View All →" link — 14px, color #1A2FFB

Grid below: 2 columns, gap 32px, margin-top 48px

Each Project Card (make 4):
- Aspect ratio: 16:9
- Border-radius: 6px
- Overflow: hidden
- Background: #E8E9F5 placeholder (I'll add real images/videos later)

Card hover state:
- Scale: 1 → 1.03
- Duration: 0.4s
- Easing: [0.16, 1, 0.3, 1]
- Add a subtle iridescent overlay: rgba(26,47,251,0.06)

Card info bar below image (not overlaid — sits below):
- Flex row, space-between, margin-top 12px
- Left: Project name — Plus Jakarta Sans 18px weight 400 color #1C1D21
- Right: Year + Category — DM Mono 11px uppercase color #42444B

Scroll animation:
- Cards skew slightly as user scrolls fast (velocity effect)
- Each card fades up on scroll-enter: opacity 0→1, y 50→0, stagger 0.15s
- Use whileInView in Framer

Now add a scroll progress bar at the top of the page:
- 2px tall, full width, fixed position, top 0
- Color: #1A2FFB
- Grows from left to right as user scrolls down

Build all of this step by step in Framer.
```

---

## PROMPT 8 — About Section

```
I'm building a Lusion.co inspired site in Framer. Build the About section.

Section wrapper:
- Background: #F0F1FA
- Padding: 128px 4vw
- Top border: 1px solid rgba(28,29,33,0.08)

Two-column layout (50/50 split, gap 64px):

LEFT COLUMN:
  1. Label: "WHO WE ARE"
     DM Mono, 12px, uppercase, letter-spacing 0.1em, color #42444B
     With 32px line before it
     Margin-bottom: 24px

  2. H2: "A Creative Production Studio Crafting Unique Digital Experiences"
     Plus Jakarta Sans, clamp(28px,4vw,52px), weight 400, line-height 1.1, color #1C1D21
     Margin-bottom: 24px

  3. Body text:
     "We are a worldwide team of specialists in design, motion, 3D, and technology — building tailored digital journeys that feel original, polished, and built for impact."
     Plus Jakarta Sans, 14px, weight 300, color #42444B, line-height 1.7
     Margin-bottom: 32px

  4. "Meet The Team →" — text link, 14px, color #1A2FFB, weight 400

RIGHT COLUMN:
  - Tall placeholder rectangle (aspect 3:4), border-radius 6px, background #E8E9F5
  - Label below: "Our Bristol studio" — DM Mono 11px uppercase color #42444B

Scroll animation on this section:
- Left col: fade in from left (x -40→0, opacity 0→1)
- Right col: fade in from right (x 40→0, opacity 0→1)
- Duration: 0.9s, easing [0.16,1,0.3,1]

Build step by step in Framer.
```

---

## PROMPT 9 — Labs Section (Dark)

```
I'm building a Lusion.co inspired site in Framer. Build the Labs dark section.

Section wrapper:
- Background: #22232E
- Padding: 128px 4vw

Header row:
- Left: 
  Label: "LUSION LABS" — DM Mono 12px uppercase letter-spacing 0.1em color rgba(255,255,255,0.4)
  H2 below: "R&D and Future Experiments"
  Plus Jakarta Sans clamp(32px,5vw,64px) weight 400 color #FFFFFF margin-top 12px

- Right: "Explore Labs →" — 14px color rgba(255,255,255,0.5), hover color #FFFFFF

Grid: 3 columns, gap 24px, margin-top 64px

Each Lab Card (make 3):
- Aspect ratio: 4:3
- Border-radius: 6px
- Background: rgba(255,255,255,0.04)
- Border: 1px solid rgba(255,255,255,0.08)
- Overflow: hidden
- Padding: 24px
- Hover: border-color rgba(26,47,251,0.6), background rgba(26,47,251,0.05)
- Transition: 0.3s

Card content:
- Tag top: DM Mono 10px uppercase letter-spacing 0.1em color rgba(255,255,255,0.4)
  Example: "EXPERIMENT / 2024"
- Title: Plus Jakarta Sans 20px weight 400 color #FFFFFF margin-top auto
  Example: "Cloth Physics Sim"
- Arrow: "→" 20px color rgba(255,255,255,0.3) hover color #1A2FFB

Scroll animation:
- Cards stagger in: opacity 0→1, y 40→0, stagger 0.1s
- Duration: 0.7s

Build step by step in Framer.
```

---

## PROMPT 10 — Contact, Footer & Final Polish

```
I'm building a Lusion.co inspired site in Framer. 
Build the contact section, footer, and do final polish.

CONTACT SECTION:
- Background: #1C1D21
- Padding: 128px 4vw

Large heading:
"Let's Work\nTogether"
Plus Jakarta Sans clamp(48px,8vw,120px) weight 400 line-height 0.95 color #FFFFFF

Below heading:
"hello@lusion.co" — 14px color rgba(255,255,255,0.4), margin-top 32px

Button: "Get In Touch"
- Background: #1A2FFB
- Color: #FFFFFF
- Border-radius: 26px
- Padding: 16px 32px
- Font: Plus Jakarta Sans 14px
- Hover: background #0016EC
- Margin-top: 40px

FOOTER:
- Background: #1C1D21
- Padding: 48px 4vw
- Top border: 1px solid rgba(255,255,255,0.06)

Footer row (flex, space-between, align center):
- Left: "© 2024 Lusion Studio" — DM Mono 11px color rgba(255,255,255,0.3)
- Right: "INSTAGRAM  TWITTER  LINKEDIN" — DM Mono 11px letter-spacing 0.15em color rgba(255,255,255,0.3)
  Each: hover color #FFFFFF, transition 0.2s

FINAL POLISH CHECKLIST — do each one:

1. Page transitions:
   Exit: opacity 1→0, y 0→-20, duration 0.4s
   Enter: opacity 0→1, y 20→0, duration 0.6s

2. All section scroll animations using whileInView:
   hidden: { opacity: 0, y: 50 }
   visible: { opacity: 1, y: 0, transition: { duration: 0.9, ease: [0.16,1,0.3,1] } }

3. Verify mobile (390px breakpoint):
   - Hero H1: reduce to clamp(36px,10vw,64px)
   - All grids: switch to 1 column
   - Nav links: hide, show hamburger
   - Padding: reduce to 0 20px

4. Check custom cursor shows (not default arrow)
5. Check loading screen plays on first visit
6. Check all hover states on cards, buttons, nav links

Walk me through each step in Framer.
```

---

# HOW TO USE THESE PROMPTS

1. Open **Framer** at framer.com — create a new project
2. Open the **Claude Chrome Extension** in the sidebar
3. Copy **Prompt 1** completely → paste into Claude → follow every instruction
4. Once that step is done → copy **Prompt 2** → paste → follow
5. Continue in order through all 10 prompts

**Tips:**
- Do one prompt at a time — don't skip ahead
- If Claude asks a question, answer it before moving on
- After Prompt 7, your site will already look impressive
- Add your own images/videos to the placeholder rectangles at the end

**Total build time: 3–5 hours**
