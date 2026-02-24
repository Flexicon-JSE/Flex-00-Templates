# Gemini Pro 3.1
## Presentation Template

Build a full-screen, presentation-style slide deck web app with 5 slides, optimized for live presentation and verbal narration. Use React and Tailwind CSS. Install the hls.js package for video background and lucide-react for icons.

Global Design System:
Font: Inter (import from Google Fonts: @import url('https://fonts.google.com/specimen/Inter:weight@400;700;900&display=swap'))
Dark theme throughout; all text is white
All font sizes use responsive clamp() values (e.g. clamp (12px, 1.05vw, 20px))
All spacing uses percentage-based values (e.g. px-[5.2%], pt-[4%]) for full responsiveness
No shadows anywhere - cards and UI elements use a "liquid glass" aesthetic: backdrop-filter: blur(24px saturate (1.4), translucent white backgrounds via linear gradients (rgba(255,255,255,0.08) to rgba(255,255,255,0.03), thin semi-transparent borders (1px solid rgba(255,255,255,0.12) and a subtle radial specular highlight at top-left)))
Presentation Framework (Presentation.tsx component):
Accepts an array of slide React element and renders them ful-screen
Keyboard navigation: ArrowRight/ArrownDown/Spacebar = next slide; ArrowLeft/ArrowUp = previous slide; F = toggle fullscreen, Escape = exit fullscreen
Smooth transitions between slides: 500ms ease-in-out opacity fade + subtle scale (0.95 for past slides, 1.05 for future slides, 1 for current)
Auto-hiding controls: appear on mouse move, disappear after 3 seconds of inactivity. Fade transition (300ms)
Bottom navigation bar with: left=slide counter ("1/5" style, white/50 opacity, 13px, tabular-nums), center=progress dots (6px circles, current slide dot expands to 24px wide pill, white/90 for active, white/30 for inactive), right = prev/next chevron buttons + divider + fullscreen toggle button (all white/50, hover to white/90 with white/10 background)
Top-right keyboard int text ("⬅️ ➡️ Navigate | F Fullscreen") at 11px, white/40, fades with controls
Video Backgrounds: Every slide that uses a video background should implement it identically: use hls.js - if Hls.isSupported(), create an HLS instance with enableWorker: true, load the source, attach to a <video> element, and auto-play on MANIFEST_PARSED. Fallback for Safari native HLS. The <video> element is absolute inset-0 w-full h-full object-cover, autoPlay, loop, muted, playsInline. No overlay, no dimming, 100% opacity. Content sits on top via relative z-10.

Slide 1 - Cover Slide (CoverSlide.tsk):
Video background:
Header: logo (white SVG, 129x40px) on the left, "Pitch Deck" text on the right (clamp 12 px-20px, opacity-80)
Center content ()