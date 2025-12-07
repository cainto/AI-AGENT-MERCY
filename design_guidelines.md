# AI Health Assistant Design Guidelines

## Design Approach
**Medical Trust & Accessibility System** - Drawing from healthcare UI patterns (e.g., Zocdoc, HealthTap) with emphasis on clarity, trust, and immediate action visibility. Prioritizing information hierarchy and emergency state visibility.

## Core Design Principles
1. **Safety First**: Emergency warnings must dominate visual hierarchy
2. **Medical Trust**: Professional, clean aesthetic that inspires confidence
3. **Clear Information Flow**: Structured content with obvious next steps
4. **Accessible Interaction**: Large touch targets, high contrast, readable text

## Typography
- **Primary Font**: Inter or Poppins (Google Fonts) - clean, professional, highly legible
- **Headings**: Semi-bold (600), sizes: h1: 2.5rem, h2: 2rem, h3: 1.5rem, h4: 1.25rem
- **Body**: Regular (400), 1rem (16px) base size, 1.6 line-height for readability
- **Critical Text** (emergency): Bold (700), 1.25rem minimum
- **Disclaimer**: Medium (500), 0.875rem, subtle but readable

## Color Palette
- **Base**: White (#FFFFFF) - primary background
- **Accent Pink**: Light pink (#FFE5F0) - section backgrounds, soft highlights
- **Medium Pink**: (#FFB3D9) - hover states, active elements
- **Emergency Red**: (#DC2626) - critical warnings, emergency panel
- **Emergency Orange**: (#F97316) - urgent (non-critical) states
- **Text Dark**: (#1F2937) - primary text
- **Text Medium**: (#6B7280) - secondary text
- **Border**: Light pink with reduced opacity (#FFE5F0 at 40%)

## Layout System
- **Spacing Units**: Tailwind 4, 6, 8, 12, 16, 24 (primary rhythm)
- **Max Widths**: Container: 1280px, Content columns: 768px, Chat area: 896px
- **Grid**: 12-column for desktop, collapse to single column on mobile

## Component Library

### Hero Section
- **NO HERO IMAGE** - This is a functional medical tool, not marketing
- Start immediately with emergency banner + AI chat interface

### Emergency Action Panel (Top Priority)
- Fixed top banner (collapsible when not active)
- Red/orange gradient background with white text
- Large alert icon (🚨) at 2.5rem
- Bold, centered text at 1.5rem
- Pulse animation on critical state
- Emergency phone number as large, tappable button
- Always visible on mobile with sticky positioning

### AI Chat Interface (Central)
- Clean white card with subtle pink border
- Large textarea (min-height: 120px) with placeholder: "Describe your symptoms (e.g., fever, headache, nausea)..."
- Send button: Medium pink background, rounded-full, px-8 py-3
- Response area: White background, structured sections with dividers
- Confidence indicators: Progress bars in pink shades
- Disclaimer: Sticky footer inside chat card, light pink background, always visible

### Disease Information Section
- 2-column grid (desktop), single column (mobile)
- Alphabetical organization with letter headers (A-Z sticky navigation)
- Cards: White with pink accent border on hover
- Each card: Disease name (h3), brief description (2-3 lines), "Learn More" link
- Modal/expandable detail view with full paragraph content

### FAQ Section
- Accordion pattern with pink accent indicators
- Questions in semi-bold, answers in regular weight
- Open state: light pink background
- Smooth expand/collapse transitions (200ms)
- Icons: Chevron-down/up at 1.25rem

### Differential Diagnosis Display
- Stacked cards, ranked by likelihood
- Each card shows: Condition name, confidence meter (visual bar), brief description
- Top prediction: Highlighted with deeper pink background
- Next steps: Action-oriented buttons (Schedule appointment, Monitor symptoms, etc.)

## Navigation
- Minimal top bar: Logo left, "How it Works" and "Emergency Numbers" links right
- Mobile: Hamburger menu with emergency number always visible
- Footer: Simple single-row with disclaimer link, privacy policy, contact

## Interaction States
- **Buttons**: Hover darkens by 10%, active state scales 0.98
- **Input Focus**: Pink border (2px), subtle shadow
- **Loading**: Pink spinner, "Analyzing symptoms..." text
- **Cards**: Hover lifts (shadow-md to shadow-lg transition)

## Accessibility
- WCAG AA contrast ratios minimum
- Keyboard navigation throughout
- Screen reader labels for all interactive elements
- Focus indicators: 2px pink outline
- Emergency warnings: aria-live="assertive" for immediate announcement

## Images
**No hero image** - This is a clinical tool. Images used only for:
- Disease information cards: Medical illustration icons (placeholder: simple line icons from Heroicons - beaker, heart, bandage, etc.)
- FAQ section: Optional small medical-themed icons for visual interest

## Mobile Considerations
- Emergency panel: Fixed top, collapsible with obvious close/expand button
- Chat input: Full-width with floating send button
- Single-column layout for all sections
- Touch targets minimum 44x44px
- Bottom padding for mobile keyboard clearance

## Critical Design Requirements
- Disclaimer must appear with EVERY AI response (sticky within response container)
- Emergency state must override all other UI with unmissable red banner
- Medical information must be scannable (bullet points, clear sections)
- No distracting animations except emergency pulse indicator
- Professional medical aesthetic throughout - no playful elements