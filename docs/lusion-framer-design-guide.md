# Lusion.co — Complete Framer Design Guide

> Extracted design system based on lusion.co (V3 current) for Framer replication.
> Built with Three.js + GSAP + Houdini FX pre-calculated simulations.

---

## 1. COLOR PALETTE

| Token | Hex | Usage |
|---|---|---|
| `--bg-primary` | `#F0F1FA` | Page background (light lavender) |
| `--bg-dark` | `#22232E` | Dark sections, overlays |
| `--bg-card` | `#FFFFFF` | Project cards surface |
| `--text-primary` | `#1C1D21` | Headings, body text |
| `--text-secondary` | `#42444B` | Secondary text, nav links |
| `--accent-blue` | `#1A2FFB` | Primary CTA, highlights |
| `--accent-blue-deep` | `#0016EC` | Button hover state |
| `--btn-dark` | `#2B2E3A` | Dark button background |
| `--white` | `#FFFFFF` | Text on dark bg |
| `--scrollbar-track` | `rgba(0,0,0,0.1)` | Scrollbar track |
| `--scrollbar-thumb` | `rgba(0,0,0,0.47)` | Scrollbar thumb |

### Framer Color Variables (paste into Variables panel)
```
BgPrimary:   #F0F1FA
BgDark:      #22232E
TextPrimary: #1C1D21
TextSub:     #42444B
AccentBlue:  #1A2FFB
BlueDeep:    #0016EC
BtnDark:     #2B2E3A
White:       #FFFFFF
```

---

## 2. TYPOGRAPHY

### Font Stack
Lusion uses **Aeonik Pro** (premium grotesque) as primary + **Lusion Mono** (their custom monospace) for labels.

| Role | Font | Weight | Source |
|---|---|---|---|
| Primary (all headings + body) | `Aeonik Pro` | 300–700 | cotypefoundry.com (paid) |
| Monospace labels | `Lusion Mono` / `Aeonik Mono` | 400 | cotypefoundry.com (paid) |
| Free substitute (primary) | `Plus Jakarta Sans` | 300–700 | Google Fonts |
| Free substitute (mono) | `DM Mono` | 400 | Google Fonts |

### Type Scale

| Style | Size | Weight | Line Height | Letter Spacing | Transform |
|---|---|---|---|---|---|
| Hero H1 | `9vw` (≈ clamp(48px,9vw,140px)) | 400 | 0.95 | -0.03em | None |
| H2 Section | `clamp(32px,5vw,72px)` | 400 | 1.05 | -0.02em | None |
| H3 | `clamp(20px,3vw,36px)` | 400 | 1.1 | -0.01em | None |
| Body | `14px` | 300 | 1.6 | 0em | None |
| Nav Links | `14px` | 400 | 1 | 0em | None |
| Label / Caption | `12px` | 400 | 1.4 | 0.05em | Uppercase |
| Loading Counter | `6rem` | 400 | 1 | -0.02em | None |
| Project Number | `11px` | 400 | 1 | 0.1em | Uppercase |

### Framer Font Setup
- Import `Plus Jakarta Sans` + `DM Mono` via Google Fonts panel
- Base size: `14px`, line height: `1.6`
- Default color: `#1C1D21`

---

## 3. LAYOUT & GRID

### Page Structure
```
[Page — scroll container]
  └── [WebGL Canvas — fixed, 100vw×100vh, z-index: -1]
  └── [DOM Content Layer — z-index: 1]
       ├── [Header/Nav — fixed top, 100% wide]
       ├── [Hero Section — 100vh]
       ├── [Interactive 3D Section — 100vh]
       ├── [Featured Work Grid — auto height]
       ├── [About Section — auto height]
       ├── [Labs Section — auto height]
       └── [Contact + Footer]
```

### Spacing System (4pt base)
```
4px   — micro
8px   — xs
16px  — sm
24px  — md
32px  — lg
48px  — xl
64px  — 2xl
96px  — 3xl
128px — 4xl
```

### Grid & Padding
- Section horizontal padding: `0 4vw`
- Header padding: `3vw` all sides
- Project grid: **2 columns**, `minmax(160px, 1fr)`, gap `4rem`
- Card aspect ratio: **16:9**
- Card border-radius: `6px`
- Button border-radius: `26px` (pill shape)
- No border-radius on anything else

---

## 4. NAVIGATION

```
Header: fixed top, 100% wide, padding 3vw, background transparent → blur on scroll
Left:   "LUSION" wordmark — Aeonik Pro 400, 16px, #1C1D21
Right:  [About Us]  [Projects]  [Labs]  [Contact]  [Let's Talk →]
        — 14px, #42444B, gap 32px
        — "Let's Talk" = pill button, bg #2B2E3A, color #FFF, padding 10px 20px, border-radius 26px

On scroll > 80px:
  - Header bg: rgba(240,241,250,0.85), backdrop-filter: blur(12px)
  - Transition: 0.3s ease
```

---

## 5. SECTION BREAKDOWN

### Section 1 — Loading Screen
```
Full-screen #F0F1FA background
Center: loading counter "000" → "100" 
Font: 6rem monospace (DM Mono), #1C1D21
Animation: number increments 0→100 over 1.8s
Fade out: opacity 1→0, scale 1→1.05, duration 0.5s
Reveals main content below
```

### Section 2 — Hero
```
Height: 100vh
Background: #F0F1FA + WebGL canvas behind
Layout: centered or bottom-left anchored

Overline: "AWARD WINNING 3D AND INTERACTIVE WEB STUDIO"
  — 12px, uppercase, letter-spacing 0.1em, #42444B

H1: "REALISE YOUR\nCREATIVE IDEAS"
  — 9vw, weight 400, line-height 0.95, #1C1D21
  — Animates in: translateY(40px)→(0), opacity 0→1, 0.9s, GSAP ease

Sub: "We design and produce 3D visual storytelling..."
  — 14px, #42444B, max-width 480px

CTA Button: "View Our Work"
  — pill shape, bg #2B2E3A, color #FFF, padding 14px 28px
  — hover: bg #0016EC, transition 0.2s

Scroll indicator: "SCROLL" label + animated line, bottom center
```

### Section 3 — Interactive 3D Element (Cloth / Torus)
```
Height: 100vh
Full-bleed WebGL scene
Interactive cloth simulation responding to mouse movement
Pre-calculated in Houdini FX, stored as ArrayBuffer (220KB gzip)
4 directional simulations blended based on cursor position

Framer equivalent:
  - Use a looping video of cloth/fluid simulation as bg
  - Add mouse-tracking parallax offset on overlay text
  
Overlay text (bottom-left):
  — "BEYOND VISIONS" — 9vw, #FFFFFF, weight 400
```

### Section 4 — Featured Work Grid
```
Section heading: "Featured Work" — H2, #1C1D21, margin-bottom 48px
Grid: 2-col, gap 4rem

Each Card:
  Border-radius: 6px
  Aspect: 16:9
  Background: project image/video
  Overflow: hidden
  
  On hover:
    - Scale: 1→1.03, 0.4s ease
    - Card skews slightly (scroll velocity × tilt)
    - Overlay: rgba(26,47,251,0.08) tint appears
    
  Card content (bottom-left, padding 20px):
    - Category: 11px uppercase DM Mono, #42444B
    - Title: 20px, weight 400, #1C1D21
    - Year: 11px DM Mono, #42444B (bottom-right)
```

### Section 5 — About
```
Split layout: text left, visual right
Left:
  H2: "A Creative Production Studio"
  Body: 14px, #42444B, max-width 520px
  CTA: "About Us →" text link, #1A2FFB

Right:
  Fluid/particle simulation (Three.js)
  Framer: use abstract video loop + color overlay
  
Background: #F0F1FA (same as page bg)
Padding: 96px 4vw
```

### Section 6 — Labs
```
Background: #22232E (dark section)
Text: #FFFFFF

Heading: "Lusion Labs" — H2, #FFF
Sub: "R&D experiments and future-tech exploration"
  — 14px, rgba(255,255,255,0.6)

Cards: dark-tinted experiment previews
  Border-radius: 6px
  Border: 1px solid rgba(255,255,255,0.08)
  Hover: border-color → rgba(26,47,251,0.6)
```

### Section 7 — Contact / Footer
```
Background: #1C1D21
Text: #FFFFFF
Padding: 96px 4vw 48px

Large CTA: "Let's Work Together" — H1 sized, #FFF
Sub: email address — 14px, rgba(255,255,255,0.5)
Button: "Get In Touch" — pill, bg #1A2FFB, hover #0016EC

Footer row (bottom):
  Left: "© 2024 Lusion" — 12px, rgba(255,255,255,0.4)
  Right: Social links — Instagram, Twitter, LinkedIn
         12px uppercase, letter-spacing 0.1em, rgba(255,255,255,0.4)
```

---

## 6. CURSOR — Holographic Trail

Lusion's cursor is the most iconic element: a wispy holographic tail.

```javascript
// Framer Code Component — LusionCursor.tsx
import { useEffect, useRef } from "react"

export default function LusionCursor() {
  const canvasRef = useRef(null)
  
  useEffect(() => {
    const canvas = canvasRef.current
    const ctx = canvas.getContext("2d")
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
    
    let points = []
    let mouse = { x: 0, y: 0 }
    
    const colors = ["#1A2FFB", "#7B6FFF", "#A855F7", "#EC4899", "#06B6D4"]
    
    const onMouseMove = (e) => {
      mouse.x = e.clientX
      mouse.y = e.clientY
      points.push({ x: e.clientX, y: e.clientY, age: 0, color: colors[Math.floor(Math.random()*colors.length)] })
      if (points.length > 40) points.shift()
    }
    
    const animate = () => {
      ctx.clearRect(0, 0, canvas.width, canvas.height)
      points.forEach((p, i) => {
        p.age++
        const alpha = Math.max(0, 1 - p.age / 40)
        const size = Math.max(0, 8 - p.age * 0.2)
        ctx.beginPath()
        ctx.arc(p.x, p.y, size, 0, Math.PI * 2)
        ctx.fillStyle = p.color + Math.floor(alpha * 255).toString(16).padStart(2,"0")
        ctx.fill()
      })
      points = points.filter(p => p.age < 40)
      requestAnimationFrame(animate)
    }
    
    window.addEventListener("mousemove", onMouseMove)
    animate()
    
    return () => window.removeEventListener("mousemove", onMouseMove)
  }, [])
  
  return (
    <canvas ref={canvasRef} style={{
      position: "fixed", inset: 0,
      pointerEvents: "none", zIndex: 9999,
      mixBlendMode: "multiply"
    }} />
  )
}
```

---

## 7. ANIMATIONS & TRANSITIONS

### Easing Curves (GSAP equivalents for Framer)
```
Standard:       [0.25, 0.1, 0.25, 1]      — smooth default
Cinematic out:  [0.16, 1, 0.3, 1]          — fast in, slow settle
Ease in out:    [0.65, 0, 0.35, 1]         — balanced
Spring:         type:"spring", stiffness:80, damping:20
```

### Page Load Sequence
```
t=0.0s  Loading screen visible — counter increments 000→100
t=1.8s  Counter complete
t=2.0s  Loading screen fades out (opacity 1→0, scale 1→1.05), 0.5s
t=2.3s  Nav fades in — opacity 0→1, y:-10→0, duration 0.6s
t=2.5s  Hero overline slides up — opacity 0→1, y:20→0, duration 0.6s
t=2.7s  Hero H1 slides up — opacity 0→1, y:40→0, duration 0.9s
t=3.0s  Hero subtext fades in — opacity 0→1, duration 0.6s
t=3.2s  CTA button fades in — opacity 0→1, y:10→0, duration 0.5s
t=3.4s  WebGL scene activates
```

**Framer stagger (Hero content):**
```javascript
const container = {
  hidden: { opacity: 0 },
  show: {
    opacity: 1,
    transition: { staggerChildren: 0.2, delayChildren: 2.3 }
  }
}
const item = {
  hidden: { opacity: 0, y: 30 },
  show: { opacity: 1, y: 0, transition: { duration: 0.8, ease: [0.16, 1, 0.3, 1] } }
}
```

### Scroll-Based Card Skew
Lusion's signature effect — cards skew based on scroll velocity.

```javascript
// Framer Code Component — SkewOnScroll.tsx
import { motion, useScroll, useVelocity, useTransform, useSpring } from "framer-motion"

export function SkewOnScroll({ children }) {
  const { scrollY } = useScroll()
  const scrollVelocity = useVelocity(scrollY)
  const smoothVelocity = useSpring(scrollVelocity, { stiffness: 300, damping: 90 })
  const skewX = useTransform(smoothVelocity, [-2000, 0, 2000], [-6, 0, 6])

  return (
    <motion.div style={{ skewY: skewX, transformOrigin: "center center" }}>
      {children}
    </motion.div>
  )
}
```

### Scroll-In Reveals
```javascript
// Each section fades up when entering viewport
const revealVariants = {
  hidden: { opacity: 0, y: 50 },
  visible: {
    opacity: 1, y: 0,
    transition: { duration: 0.9, ease: [0.16, 1, 0.3, 1] }
  }
}
// Use whileInView="visible" initial="hidden" viewport={{ once:true, amount:0.2 }}
```

### Page Transitions
```
Exit:   opacity 1→0, y: 0→-30, duration 0.4s, ease [0.65,0,0.35,1]
Enter:  opacity 0→1, y: 30→0, duration 0.6s, ease [0.16,1,0.3,1]
```

### Animate-Topline (hero headline)
```
Duration: 2s
Step 1 (0→50%): translateY(100%)→translateY(0) — slides up from below clip
Step 2 (50→100%): margin shift, letter-spacing tightens
Easing: cubic-bezier(0.16, 1, 0.3, 1)
```

### Animate-Tagline
```
Duration: 2s, delay: 0.4s (20% of 2s)
translateY(-20px)→translateY(0), opacity 0→1
```

---

## 8. VISUAL EFFECTS — Framer Equivalents

### A. Iridescent / Holographic Card Effect
Used on hover over project cards and lab experiments.

```javascript
// Framer Code Component — HolographicCard.tsx
import { motion, useMotionValue, useTransform } from "framer-motion"

export function HolographicCard({ children }) {
  const x = useMotionValue(0)
  const y = useMotionValue(0)
  
  const rotateX = useTransform(y, [-100, 100], [15, -15])
  const rotateY = useTransform(x, [-100, 100], [-15, 15])
  const shimmerX = useTransform(x, [-100, 100], [0, 100])
  
  const handleMouse = (e) => {
    const rect = e.currentTarget.getBoundingClientRect()
    x.set(e.clientX - rect.left - rect.width / 2)
    y.set(e.clientY - rect.top - rect.height / 2)
  }
  
  const handleLeave = () => { x.set(0); y.set(0) }

  return (
    <motion.div
      onMouseMove={handleMouse}
      onMouseLeave={handleLeave}
      style={{
        rotateX, rotateY,
        transformStyle: "preserve-3d",
        perspective: 1000,
        borderRadius: 6,
        overflow: "hidden",
        position: "relative",
      }}
    >
      {children}
      <motion.div style={{
        position:"absolute", inset:0, pointerEvents:"none",
        background: useTransform(shimmerX,
          [0, 50, 100],
          [
            "linear-gradient(135deg, rgba(26,47,251,0) 0%, rgba(168,85,247,0.15) 50%, rgba(6,182,212,0) 100%)",
            "linear-gradient(135deg, rgba(6,182,212,0.15) 0%, rgba(26,47,251,0.15) 50%, rgba(168,85,247,0.15) 100%)",
            "linear-gradient(135deg, rgba(168,85,247,0) 0%, rgba(26,47,251,0.15) 50%, rgba(6,182,212,0.15) 100%)"
          ]
        ),
        mixBlendMode: "overlay"
      }} />
    </motion.div>
  )
}
```

### B. Astronaut / Scroll Journey (Hero Feature)
Lusion features an astronaut that scrolls through portals. In Framer:

```
1. Create a tall scroll section (height: 500vh)
2. Use ScrollProgress to drive animation
3. Pin the viewport while scrolling through the sequence
4. Animate character position along a path
5. Cross-fade between "portal" environments using opacity

Framer implementation:
  - Use Scroll component with sticky child
  - useTransform(scrollProgress, [0,0.25,0.5,0.75,1], [...positions])
  - Fade between layered background videos/images
```

### C. Fluid / Particle Background (About Page)
```
Framer Marketplace: "FluidFlow Background" component
Configure with:
  Color 1: #1A2FFB
  Color 2: #7B6FFF  
  Color 3: #F0F1FA
  Speed: 0.3 (slow, ambient)
  Intensity: 0.4
```

### D. Scroll Progress Line
Thin line across the top of the page filling as user scrolls.

```javascript
// Framer Code Component
import { motion, useScroll, useSpring } from "framer-motion"

export function ScrollProgress() {
  const { scrollYProgress } = useScroll()
  const scaleX = useSpring(scrollYProgress, { stiffness: 100, damping: 30 })
  return (
    <motion.div style={{
      position:"fixed", top:0, left:0, right:0, height:2,
      background:"#1A2FFB", scaleX, transformOrigin:"0%",
      zIndex:9999
    }} />
  )
}
```

---

## 9. COMPONENTS

### 9.1 Primary Button (Pill)
```css
background: #2B2E3A;
color: #FFFFFF;
border: none;
border-radius: 26px;
padding: 12px 24px;
font-size: 14px;
font-weight: 400;
letter-spacing: 0em;
cursor: pointer;
transition: background 0.2s ease;

:hover { background: #0016EC; }
```

### 9.2 Ghost Button
```css
background: transparent;
color: #1C1D21;
border: 1px solid rgba(28,29,33,0.2);
border-radius: 26px;
padding: 12px 24px;
transition: border-color 0.2s, color 0.2s;

:hover { border-color: #1A2FFB; color: #1A2FFB; }
```

### 9.3 Project Card
```
Frame: 100% wide, aspect 16:9, border-radius 6px, overflow hidden
Image/video: object-fit cover
Overlay: gradient bottom rgba(28,29,33,0)→rgba(28,29,33,0.5)

Bottom-left info:
  Category: 11px uppercase DM Mono, #FFF, opacity 0.7
  Title: 18px Aeonik Pro 400, #FFF

Hover:
  Scale: 1→1.03, 0.4s [0.16,1,0.3,1]
  Overlay opacity increases
  Iridescent shimmer activates
```

### 9.4 Section Label
```css
font-size: 12px;
font-family: 'DM Mono', monospace;
text-transform: uppercase;
letter-spacing: 0.1em;
color: #42444B;
display: flex;
align-items: center;
gap: 12px;

/* Line before label */
::before {
  content: '';
  display: block;
  width: 32px;
  height: 1px;
  background: #42444B;
}
```

### 9.5 Scrollbar (custom)
```css
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: rgba(0,0,0,0.1); }
::-webkit-scrollbar-thumb { background: rgba(0,0,0,0.47); border-radius: 2px; }
scrollbar-width: thin;
```

---

## 10. THREE.JS SCENE SETTINGS (for reference / Framer code)

If building the WebGL background as a Framer code component:

```javascript
// Key Three.js config from Lusion reverse-engineering
const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true })
renderer.toneMapping = THREE.ACESFilmicToneMapping  // cinematic color grade
renderer.toneMappingExposure = 1.0

const camera = new THREE.PerspectiveCamera(60, w/h, 0.1, 1000)
camera.position.z = 75

// Environment lighting
const rgbeLoader = new RGBELoader()
rgbeLoader.load('quarry_01_1k.hdr', (texture) => {
  texture.mapping = THREE.EquirectangularReflectionMapping
  scene.environment = texture
})

// Torus Knot (signature shape)
const geometry = new THREE.TorusKnotGeometry(8, 3, 128, 16)
const material = new THREE.MeshStandardMaterial({ roughness: 0.1, metalness: 0 })

// Scroll velocity → distortion
let targetVelocity = 0
window.addEventListener('scroll', () => {
  const velocity = Math.abs(window.scrollY - lastScrollY) / deltaTime
  targetVelocity = THREE.MathUtils.inverseLerp(0, 10, velocity)
})
// Decay per frame:
targetVelocity = Math.max(0, targetVelocity - 0.005)
```

**Framer Marketplace alternatives:**
- "Shader 3D Background" — configure colors to match
- "Three.js Scene" code component
- "Spline Scene" — import exported Spline scenes

---

## 11. FRAMER PROJECT SETUP CHECKLIST

1. **New Project**
   - Canvas: 1440px desktop, 390px mobile
   - Background: `#F0F1FA`

2. **Install Fonts** (Google Fonts panel)
   - `Plus Jakarta Sans` — weights 300, 400, 600, 700
   - `DM Mono` — weight 400

3. **Color Variables**
   - Add all 8 tokens from Section 1

4. **Global Styles** (Custom CSS)
   ```css
   * { cursor: none; box-sizing: border-box; }
   html { scroll-behavior: smooth; }
   body { background: #F0F1FA; color: #1C1D21; font-family: 'Plus Jakarta Sans', sans-serif; }
   ::selection { background: #1A2FFB; color: #fff; }
   ```

5. **Add Code Components**
   - `LusionCursor.tsx` — holographic trail cursor
   - `SkewOnScroll.tsx` — wrap project grid
   - `ScrollProgress.tsx` — top progress bar
   - `HolographicCard.tsx` — wrap each project card

6. **Build Sections**
   - [ ] Loading screen with counter
   - [ ] Fixed nav (blur on scroll)
   - [ ] Hero (full-height, large type)
   - [ ] Interactive 3D / cloth section
   - [ ] Featured Work grid (SkewOnScroll wrapped)
   - [ ] About section
   - [ ] Labs (dark bg `#22232E`)
   - [ ] Contact + Footer (dark bg `#1C1D21`)

7. **Scroll Animations**
   - Every section: `whileInView`, `initial="hidden"`, `viewport={{ once:true, amount:0.2 }}`
   - Variants: `{ hidden: { opacity:0, y:50 }, visible: { opacity:1, y:0 } }`

8. **Page Transitions**
   - Enable Framer Router
   - Wrap in `AnimatePresence`
   - Exit: `{ opacity:0, y:-30, transition:{ duration:0.4 } }`

---

## 12. LUSION DESIGN PRINCIPLES

| Principle | What it means in Framer |
|---|---|
| **Light & airy** | `#F0F1FA` bg — never pure white, always slightly warm/cool tinted |
| **Electric punch** | `#1A2FFB` used sparingly — one CTA, one accent per screen |
| **Scroll is the story** | Every section triggers when entering view — nothing is static |
| **Tactile interactions** | Cards skew, tilt, shimmer — everything responds to touch |
| **Confident type** | 9vw hero text, no apology — full width, full bleed |
| **Depth through 3D** | WebGL behind DOM — two layers always present |
| **Holographic moments** | Cursor trail + card shimmer = iridescent brand moments |
| **Dark contrast sections** | Alternate light/dark sections for rhythm — `#22232E` → `#F0F1FA` |
| **Pill buttons** | 26px radius on all buttons — friendly, modern, not corporate |
| **Playful but precise** | Fun interactions but clean grid — 4vw padding, 4rem gaps always |

---

## 13. ASSETS & RESOURCES

| Asset | Source | Notes |
|---|---|---|
| Plus Jakarta Sans | fonts.google.com | Free — closest to Aeonik Pro |
| DM Mono | fonts.google.com | Free — closest to Lusion Mono |
| Aeonik Pro (exact) | cotypefoundry.com | Paid — 8 weights |
| Abstract 3D loops | mixkit.co / coverr.co | Search "abstract", "fluid", "3D" |
| HDR environment | polyhaven.com | Free HDRI maps for WebGL |
| Holographic card | Framer Marketplace | Search "3D tilt card" |
| Fluid background | Framer Marketplace | "FluidFlow Background" |
| Scroll skew | Code component above | Custom |
| Spline scenes | spline.design | Build/export 3D scenes → embed |

---

## Quick Reference — Paste into Framer CSS Override

```css
/* Base */
* { cursor: none; box-sizing: border-box; }
body {
  background: #F0F1FA;
  color: #1C1D21;
  font-family: 'Plus Jakarta Sans', sans-serif;
  font-size: 14px;
  line-height: 1.6;
}
::selection { background: #1A2FFB; color: #fff; }

/* Typography */
h1 { font-size: clamp(48px, 9vw, 140px); line-height: 0.95; letter-spacing: -0.03em; font-weight: 400; }
h2 { font-size: clamp(32px, 5vw, 72px); line-height: 1.05; letter-spacing: -0.02em; font-weight: 400; }

/* Nav link */
.nav-link { font-size: 14px; color: #42444B; transition: color 0.2s; }
.nav-link:hover { color: #1A2FFB; }

/* Pill button */
.btn-primary {
  background: #2B2E3A;
  color: #FFF;
  border: none;
  border-radius: 26px;
  padding: 12px 24px;
  font-size: 14px;
  transition: background 0.2s ease;
}
.btn-primary:hover { background: #0016EC; }

/* Ghost button */
.btn-ghost {
  background: transparent;
  color: #1C1D21;
  border: 1px solid rgba(28,29,33,0.2);
  border-radius: 26px;
  padding: 12px 24px;
  transition: border-color 0.2s, color 0.2s;
}
.btn-ghost:hover { border-color: #1A2FFB; color: #1A2FFB; }

/* Section label */
.label {
  font-family: 'DM Mono', monospace;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: #42444B;
}

/* Card */
.project-card {
  border-radius: 6px;
  overflow: hidden;
  aspect-ratio: 16/9;
  transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
}
.project-card:hover { transform: scale(1.03); }

/* Dark section */
.section-dark {
  background: #22232E;
  color: #FFFFFF;
}

/* Scrollbar */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: rgba(0,0,0,0.1); }
::-webkit-scrollbar-thumb { background: rgba(0,0,0,0.47); border-radius: 2px; }
```
