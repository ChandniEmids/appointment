# App Overview

## Product Name
ClearPath FDO — Front Desk Office
Healthcare appointment management UI for a US Facility Center front desk team.

## Stack
- Plain HTML + Tailwind CSS (CDN: https://cdn.tailwindcss.com)
- Vanilla JavaScript — no frameworks, no build tools
- Inter font via Google Fonts
- All files are self-contained single-page HTML files

## Pages
| File | Type | Layout |
|---|---|---|
| `signin.html` | Auth | Centered card, topbar logo only, no sidebar |
| `signup.html` | Auth | Centered card, topbar logo only, no sidebar |
| `appointments.html` | App | Full shell — 64px header + 240px sidebar + main |

## Dev Server
Two Python HTTP servers already running:
- http://localhost:3000 (primary)
- http://localhost:8080 (fallback)

Start if needed: `python3 -m http.server 3000`

## Figma Integration
- Figma capture script is injected in signin.html head (do not remove)
- MCP server: figma-remote-mcp at http://127.0.0.1:3845/mcp
- Target Figma file: gNQF8eNTjwL4O9o5Mf083C (Layout-log_Pod-2)


---


# Design System

## Color System

### Brand Colors
- Brand blue: `#5A57DE` — active nav, focus rings
- Brand blue dark: `#2E2C85` — hover states
- Brand path green: `#0d9488` — logo accent, user avatar
- Primary CTA gradient: `linear-gradient(90deg, #5064E5 0%, #5F50E5 100%)` — New appointment button, modal submit, empty state CTA

### Surface & Background
- Page background: `linear-gradient(180deg, rgba(235,235,237,0.60) 0%, rgba(220,220,236,0.60) 100%), #FFF`
- Header background: `#F9F9FB`
- Sidebar background: transparent
- Calendar / content surface: `#ffffff`

### Text
- Text primary: `#121219`
- Text secondary: `#666689`
- Text muted: `#9ca3af`

### Borders
- Input/select border: `#F0F0F7`
- Divider / subtle border: `#f3f4f6`

### Appointment Type Colors
Colors chosen to avoid conflict with semantic colors (red=error, green=success, amber=warning, blue=info).

| Type | Text color | Background 
|---|---|---|---|---|
| Facility Tour | `#9A3412` | `#FFF3EE` |
| Counselling Session | `#0C5E73` | `#E8F6FA` |
| Group Therapy | `#A21CAF` | `#FCF0FD` |
| Psychological Evaluation | `#4A6B00` | `#F2F9E8` |
| Medical Test | `#1E293B` | `#F1F5F9` |


<!-- 


| Type | Text Color | Background |
|---|---|---|
| Counselling Session | `#0F766E` | `#F0FDFA` |
| Facility Tour | `#C2410C` | `#FFF7ED` |
| Group Therapy | `#BE185D` | `#FDF2F8` |
| Individual Therapy | `#0E7490` | `#ECFEFF` | -->

## Typography
- Font: Inter (Google Fonts)
- Headings: font-weight 700
- Labels: 13px, font-weight 500
- Body: 14px, font-weight 400

## Icons
- Library: Tabler Icons — outline style only (https://tabler.io/icons)
- CDN: `<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/dist/tabler-icons.min.css">`
- Syntax: `<i class="ti ti-[icon-name]"></i>`
- Sizing via inline style: `font-size:12px` (xs), `font-size:16px` (sm/default), `font-size:20px` (md), `font-size:24px` (lg)
- Color inherits from parent — do not set color on `<i>` unless overriding
- Never use other icon libraries (Heroicons, Feather, etc.)
- Never use raw SVG icons — always use Tabler webfont classes

### Common Icon Reference
| Usage | Icon class |
|---|---|
| Appointments / calendar | `ti-calendar` |
| Patients | `ti-users` |
| Providers | `ti-stethoscope` |
| Rooms | `ti-door` |
| Reports | `ti-chart-bar` |
| Settings | `ti-settings` |
| Help | `ti-help-circle` |
| Search | `ti-search` |
| Filter | `ti-filter` |
| Add / plus | `ti-plus` |
| Close / X | `ti-x` |
| Chevrons | `ti-chevron-left/right/down` |
| User / person | `ti-user` |
| Check / complete | `ti-check` |
| Warning / due | `ti-alert-triangle` |
| Pending / clock | `ti-clock` |
| Delete | `ti-trash` |
| Reschedule | `ti-calendar` |
| Error alert | `ti-alert-circle` |
| Eye / password | `ti-eye` / `ti-eye-off` |
| Success | `ti-circle-check` |

## Layout & Spacing

### Spacing — strict 8px grid
All spacing must be a multiple of 8px: 8, 16, 24, 32, 40, 48, 56, 64px.
Never use 6px, 10px, 14px, 18px, 28px, or any non-multiple of 8.

### Layout Tokens
- Header height: 64px (sticky, z-50)
- Sidebar width: 240px (fixed left, top: 64px, full height)
- Main content padding left/right: 32px

### App Shell
```
┌──────────────────────────────────────────────────────┐
│ HEADER 64px — Logo | Global Search | Avatar only     │
├────────────┬─────────────────────────────────────────┤
│ SIDEBAR    │ MAIN CONTENT                            │
│ 240px      │ margin-left: 240px, padding-top: 64px  │
│ fixed      │                                         │
│            │ [page content here]                     │
└────────────┴─────────────────────────────────────────┘
```

### Header Rules
- Logo: left-aligned (teal icon 32px + "ClearPath FDO" text)
- Global search: centered, min-width 320px, placeholder "Search patients, appointments, rooms…"
- Right side: user avatar (32px circle, initials) ONLY — no other buttons

### Sidebar Nav Sections
**MAIN:** Appointments · Patients · Providers · Rooms
**ADMIN:** Reports · Settings
**Bottom:** Help & Support

Nav item states:
- Active: bg `#EEEEFF`, text `#5A57DE`, 3px left border `#5A57DE`
- Hover: bg-gray-50
- Height: 40px, padding: 0 16px

### Auth Pages (signin, signup)
- No sidebar
- Topbar: logo only (no search, no avatar)
- Centered card: max-width 400px (signin) / 480px (signup), padding 40px

## Components

### Inputs & Selects
- Height: 40px
- Border-radius: 8px (`rounded-lg`)
- Border: 1.5px solid `#F0F0F7`
- Focus ring: 3px solid `rgba(90,87,222,0.15)`

### Buttons
- Height: 40px
- Border-radius: 8px
- Padding; 12px 24px

##### Primary
- Background: CTA gradient
- Text: White
- box-shadow: 0 2px 8px rgba(80, 100, 229, .25)

#### Secondary
- Background: White
- Text: Text primary

    

### Cards
- Border-radius: 8px

### Filter Bar
- Closed by default (`filterBarVisible = false`, HTML has `collapsed` class on init)
- Toggled via filter icon button in view controls bar

### Appointment Cards
- Colored by appointment type, not status
- Card content order (top to bottom):
  1. Appointment type (bold, type color) + status chip right
  2. Patient name — or "N patients" with users icon for Group Therapy
  3. Room icon + room · Provider icon + provider name

### Appointment Detail Panel
- Opens on card click
- Header shows type pill + patient name + status chip
- Detail card uses type bg/border color for visual continuity

## States & Feedback

### Appointment Display Status Logic
| Condition | Display |
|---|---|
| Past date + Due/Pending | **Cancelled** — grey chip, no dot |
| Future date + Pending/Upcoming | **Future** — dotted border, no chip |
| Today + within 1hr window of appointment time | **Ongoing** — red pulse dot chip |
| Past or today + Completed | **Completed** — check icon chip |
| Future + any status | Never show tick or Ongoing |

### Loading & Feedback
- Show loading spinner on async actions
- Success toasts for booking confirmations
- Inline error text for form validation (never color-only)


---


# Accessibility Guidelines
- WCAG-compliant color contrast on all text and interactive elements
- Icons always paired with visible text labels
- Focus states visible on all interactive elements
- Form errors announced via visible error text (not just color)
- All interactive elements keyboard-navigable


---


# Usability Heuristics
- **Clear Feedback** — Show loading states, success messages, and error states at all times
- **Error Prevention** — Use validations, confirmation dialogs, and helpful error messages before destructive actions


---


# Content / UX Writing
- Use plain, clinical language appropriate for a healthcare front desk context
- Patient-facing labels use full names (e.g. "Counselling Session", not "CS")
- Status labels: Ongoing · Completed · Cancelled · Future · Pending · Upcoming
- Placeholder text should be instructive (e.g. "Search patients, appointments, rooms…")
- Error messages should be specific and actionable


---


# Responsive Behaviour
- Auth pages (signin, signup): centered card, max-width 400–480px, collapses gracefully on small screens
- App shell: sidebar fixed, main content scrolls independently
- Calendar views: week view has horizontal scroll on small screens (min-width 900px table)


---


# Design Principles
- **Clarity first** — Every element should have a clear purpose; remove anything decorative that adds noise
- **Consistency** — Use the design system tokens strictly; never introduce one-off colors or spacing values
- **Efficiency** — Front desk staff work fast; interactions should be minimal and predictable
- **Trust** — Healthcare context demands visual reliability; avoid playful patterns or ambiguous states
- **Accessibility** — Design for all users by default, not as an afterthought
