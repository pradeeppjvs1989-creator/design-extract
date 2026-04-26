# Active Theory — Framer Build Prompts
# Copy each prompt one at a time into the Claude Chrome Extension while inside Framer.
# Complete each step before moving to the next.

---

## PROMPT 1 — Project Setup & Colors

```
I'm building a website in Framer inspired by activetheory.net. 
Help me set up the project foundation.

1. Set the canvas background to #000000
2. Open the Variables panel and create these color variables:
   - BgPrimary: #000000
   - BgSurface: #111111
   - AccentBlue: #2779A7
   - AccentBlueHover: #3a9fd4
   - AccentBlueGlow: rgba(39,121,167,0.35)
   - TextPrimary: #FFFFFF
   - TextSecondary: #9C9C9C
   - TextMuted: #353535
   - BorderSub: rgba(255,255,255,0.08)
   - BorderActive: rgba(255,255,255,0.4)

3. In Custom CSS (Project Settings → Custom Code), paste:
* { box-sizing: border-box; cursor: none; }
body { background: #000000; color: #ffffff; }
::selection { background: #2779A7; color: #fff; }

Walk me through each step in Framer right now.
```

---

## PROMPT 2 — Fonts & Typography

```
I'm building an Active Theory inspired site in Framer. Set up the typography.

1. Go to Fonts panel → Add Google Fonts:
   - "Space Grotesk" (weights: 300, 400, 700)
   - "Space Mono" (weight: 400)

2. Set global text defaults:
   - Font: Space Grotesk
   - Size: 14px
   - Weight: 300
   - Line height: 1.6
   - Color: #FFFFFF

3. Create these text styles in Framer's Text Styles panel:
   - Hero/H1: Space Grotesk, clamp(64px,10vw,140px), weight 300, line-height 0.9, letter-spacing -0.03em, uppercase
   - H2: Space Grotesk, clamp(36px,5vw,72px), weight 300, line-height 1.0, letter-spacing -0.02em, uppercase
   - NavLink: Space Grotesk, 11px, weight 400, letter-spacing 0.15em, uppercase, color #9C9C9C
   - Label: Space Mono, 10px, weight 400, letter-spacing 0.2em, uppercase, color #9C9C9C
   - Body: Space Grotesk, 14px, weight 300, line-height 1.6, color #9C9C9C

Guide me through each step in Framer.
```

---

## PROMPT 3 — Loading Screen

```
I'm building an Active Theory inspired site in Framer. 
Build the loading/intro screen component.

Design specs:
- Full screen frame: 100vw × 100vh, background #000000
- Center element: text showing "100" in Space Mono, 48px, color #FFFFFF
- Below it: a horizontal progress bar, width 200px, height 1px, background #2779A7
- Add a Framer variant called "loaded" where the whole frame opacity goes to 0

Animation sequence (use Framer transitions):
1. Progress bar animates width from 0px to 200px over 1.5s
2. Number counts from 0 to 100 (use a code component or number animation)
3. After 2s delay: entire loading frame fades out (opacity 1→0, scale 1→1.05) over 0.5s
4. Main page content becomes visible

Make this a reusable Framer component called "LoadingScreen".
Walk me through building it step by step.
```

---

## PROMPT 4 — Navigation Bar

```
I'm building an Active Theory inspired site in Framer. Build the navigation bar.

Specs:
- Frame: 100% wide, fixed position, top: 0, z-index: 1000
- Height: 80px, padding: 0 32px
- Background: transparent (no background at all)
- Layout: horizontal, space-between, align center

Left side — Logo:
- Text: "ACTIVE THEORY"
- Font: Space Grotesk, 11px, weight 400, letter-spacing 0.15em, uppercase
- Color: #FFFFFF

Right side — Nav links in a row, gap 32px:
- Text items: "WORK" / "ABOUT" / "CONTACT"
- Font: Space Grotesk, 11px, weight 400, letter-spacing 0.15em, uppercase
- Default color: #9C9C9C
- Hover state: color #FFFFFF, transition 0.3s

Bottom-left corner (separate fixed element):
- Text: "33.9850° N  118.4695° W"
- Font: Space Mono, 10px, color #353535
- Position: fixed, bottom 24px, left 32px

Bottom-right corner:
- Text: "01 / 12"
- Font: Space Mono, 10px, color #9C9C9C
- Position: fixed, bottom 24px, right 32px

Build this in Framer step by step.
```

---

## PROMPT 5 — Hero Section

```
I'm building an Active Theory inspired site in Framer. Build the hero section.

Specs:
- Frame: 100vw × 100vh, background #000000
- Background layer: add a full-bleed dark video (I'll add my own mp4 - leave as a placeholder rectangle for now, color #111111)
- Gradient overlay on video: linear-gradient(180deg, rgba(0,0,0,0.2) 0%, rgba(0,0,0,0.7) 100%)

Content block — position: bottom-left, padding 48px:

  1. Overline text:
     "CREATIVE DIGITAL EXPERIENCES"
     Space Grotesk, 10px, uppercase, letter-spacing 0.2em, color #9C9C9C
     margin-bottom: 16px

  2. H1 title:
     "BEYOND\nVISIONS"
     Space Grotesk, clamp(64px,10vw,140px), weight 300, line-height 0.9
     uppercase, color #FFFFFF
     margin-bottom: 24px

  3. Subtext:
     "We build immersive digital experiences for ambitious brands."
     Space Grotesk, 14px, weight 300, color #9C9C9C, max-width 400px
     margin-bottom: 32px

  4. CTA Button:
     Text: "VIEW WORK"
     Border: 1px solid rgba(255,255,255,0.15)
     Background: transparent
     Padding: 14px 28px
     Font: Space Grotesk 11px uppercase letter-spacing 0.1em
     Border-radius: 0 (sharp corners)
     Hover: border-color rgba(39,121,167,0.8), box-shadow 0 0 20px rgba(39,121,167,0.3)

Scroll-in animation (use Framer's appear animation):
- All content items fade up: y 30→0, opacity 0→1
- Stagger: 0.15s between each item
- Duration: 0.8s each
- Easing: [0.76, 0, 0.24, 1]

Build this step by step in Framer.
```

---

## PROMPT 6 — Film Grain Overlay

```
I'm building an Active Theory inspired site in Framer.
Add a film grain noise overlay — this is the signature texture that makes it cinematic.

Create a new Code Component in Framer called "FilmGrain" with this code:

import { useEffect, useRef } from "react"
import { addPropertyControls, ControlType } from "framer"

export default function FilmGrain({ opacity = 0.04, speed = 2 }) {
  const canvasRef = useRef(null)
  useEffect(() => {
    const canvas = canvasRef.current
    const ctx = canvas.getContext("2d")
    const resize = () => { canvas.width = window.innerWidth; canvas.height = window.innerHeight }
    resize()
    window.addEventListener("resize", resize)
    let frame = 0
    const animate = () => {
      frame++
      if (frame % speed === 0) {
        const imageData = ctx.createImageData(canvas.width, canvas.height)
        for (let i = 0; i < imageData.data.length; i += 4) {
          const v = Math.random() * 255
          imageData.data[i] = v
          imageData.data[i+1] = v
          imageData.data[i+2] = v
          imageData.data[i+3] = 255
        }
        ctx.putImageData(imageData, 0, 0)
      }
      requestAnimationFrame(animate)
    }
    animate()
    return () => window.removeEventListener("resize", resize)
  }, [])
  return <canvas ref={canvasRef} style={{ position:"fixed", inset:0, opacity, mixBlendMode:"screen", pointerEvents:"none", zIndex:100 }} />
}

addPropertyControls(FilmGrain, {
  opacity: { type: ControlType.Number, min:0, max:0.15, step:0.005, defaultValue:0.04 },
  speed: { type: ControlType.Number, min:1, max:5, step:1, defaultValue:2 },
})

After creating it, add the FilmGrain component to the page as a fixed overlay.
Walk me through doing this in Framer.
```

---

## PROMPT 7 — Custom Cursor

```
I'm building an Active Theory inspired site in Framer.
Add a custom cursor — a blue dot with a ring that follows the mouse.

Create a Code Component called "CustomCursor":

import { motion, useMotionValue, useSpring } from "framer-motion"
import { useEffect } from "react"

export default function CustomCursor() {
  const x = useMotionValue(0)
  const y = useMotionValue(0)
  const springX = useSpring(x, { stiffness: 300, damping: 30 })
  const springY = useSpring(y, { stiffness: 300, damping: 30 })

  useEffect(() => {
    const move = (e) => { x.set(e.clientX); y.set(e.clientY) }
    window.addEventListener("mousemove", move)
    return () => window.removeEventListener("mousemove", move)
  }, [])

  return (
    <>
      <motion.div style={{
        position:"fixed", top:0, left:0,
        x: springX, y: springY,
        width:8, height:8, borderRadius:"50%",
        background:"#2779A7",
        translateX:"-50%", translateY:"-50%",
        zIndex:9999, pointerEvents:"none"
      }} />
      <motion.div style={{
        position:"fixed", top:0, left:0,
        x: springX, y: springY,
        width:40, height:40, borderRadius:"50%",
        border:"1px solid rgba(39,121,167,0.5)",
        translateX:"-50%", translateY:"-50%",
        zIndex:9998, pointerEvents:"none"
      }} />
    </>
  )
}

Add it to the page as a fixed element. Guide me through this in Framer.
```

---

## PROMPT 8 — Project Cards Grid

```
I'm building an Active Theory inspired site in Framer. Build the Work/Projects section.

Section wrapper:
- Background: #000000
- Padding: 96px 32px

Section heading:
- Text: "SELECTED WORK"
- Font: Space Grotesk, 11px, uppercase, letter-spacing 0.2em, color #9C9C9C
- Margin-bottom: 48px

Grid: 2 columns, gap 24px

Each Project Card (make 4 cards):
- Aspect ratio: 16:9
- Border-radius: 0 (sharp)
- Background: #111111 (placeholder — I'll add images later)
- Overflow: hidden
- Border: 1px solid rgba(255,255,255,0.08)

Inside each card:
- Top-left tag: Space Mono 10px uppercase letter-spacing 0.15em color #9C9C9C, padding 16px
  Example: "BRAND / DIGITAL"
- Bottom-left title: Space Grotesk 24px weight 300 color #FFFFFF, padding 20px
  Example: "Project Name"
- Bottom-right year: Space Mono 10px color #9C9C9C, padding 20px
  Example: "2024"

Hover state on card:
- Scale: 1 → 1.02
- Border-color: rgba(39,121,167,0.6)
- Transition: 0.4s

Scroll-in animation:
- Cards fade up: opacity 0→1, y 40→0
- Stagger 0.1s between cards
- Use whileInView so it triggers when scrolling into view

Build this in Framer step by step.
```

---

## PROMPT 9 — About & Contact Sections

```
I'm building an Active Theory inspired site in Framer. 
Build the About section and Contact/Footer.

ABOUT SECTION:
- Background: #0a0a0a
- Padding: 128px 32px
- Two column layout (50/50)

Left column:
- Overline: "ABOUT US" — Space Mono 10px uppercase letter-spacing 0.2em color #9C9C9C
- H2: "We build what others\nimagine."
  Space Grotesk clamp(36px,5vw,64px) weight 300 line-height 1.0 color #FFFFFF
- Body: 14px Space Grotesk weight 300 color #9C9C9C max-width 480px margin-top 24px
  "Active Theory is a Venice Beach-based creative studio pushing the boundaries of web technology since 2012."
- Link: "Read More →" — 11px uppercase letter-spacing 0.1em color #2779A7 margin-top 32px

Right column:
- Leave empty for a 3D visual / video (add a dark placeholder #111111)

CONTACT / FOOTER:
- Background: #000000
- Padding: 128px 32px 48px
- Top border: 1px solid rgba(255,255,255,0.08)

Large CTA:
- Text: "Let's build\nsomething."
  Space Grotesk clamp(48px,8vw,120px) weight 300 line-height 0.9 uppercase color #FFFFFF

Email link below: "hello@studio.com" — 14px color #9C9C9C margin-top 32px

Footer bottom row (flex, space-between):
- Left: "© 2024 Studio" — Space Mono 10px color #353535
- Right: "INSTAGRAM  TWITTER  LINKEDIN" — Space Mono 10px letter-spacing 0.15em color #353535

Build both sections in Framer step by step.
```

---

## PROMPT 10 — Page Transitions & Final Polish

```
I'm building an Active Theory inspired site in Framer. 
Add page transitions and final polish touches.

1. PAGE TRANSITIONS (enable Framer routing):
   - Go to Pages panel → enable page transitions
   - Exit animation: opacity 1→0, scale 1→0.97, blur 0→6px, duration 0.5s
   - Enter animation: opacity 0→1, scale 1.03→1, blur 6→0px, duration 0.7s
   - Easing: [0.76, 0, 0.24, 1]

2. NEON GLOW on the H1 title — add this in the text's custom CSS:
   text-shadow: 0 0 20px rgba(39,121,167,0.6), 0 0 40px rgba(39,121,167,0.3);

3. SECTION DIVIDERS:
   - Between each section add a 1px horizontal line
   - Color: rgba(255,255,255,0.06)
   - Full width
   - Animate on scroll: scaleX 0→1, duration 0.8s, from left

4. SCROLL BEHAVIOR:
   - Project Settings → Custom Code → add:
   html { scroll-behavior: smooth; }

5. RESPONSIVE — Mobile breakpoint (390px):
   - Hero H1: reduce to clamp(36px,12vw,64px)
   - Grid: switch to 1 column
   - Nav: hide right links, show hamburger icon
   - Padding: reduce to 0 16px

6. FINAL CHECK — verify:
   [ ] Film grain overlay is visible and animating
   [ ] Custom cursor replaces default cursor
   [ ] All sections fade in on scroll
   [ ] Loading screen plays on first load
   [ ] Hover states work on cards and nav links
   [ ] Page is fully dark (#000 background everywhere)

Walk me through each step in Framer.
```

---

# HOW TO USE THESE PROMPTS

1. Open **Framer** in Chrome
2. Open the **Claude extension** (sidebar or popup)
3. Copy **Prompt 1** → paste into Claude → follow the instructions
4. Once done → copy **Prompt 2** → repeat
5. Go in order: 1 through 10
6. Each prompt is self-contained — Claude will guide you through that exact step

**Total build time estimate: 3–5 hours following these prompts**
