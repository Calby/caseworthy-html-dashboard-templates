---
name: caseworthy-html-builder
description: "Build HTML/CSS templates for CaseWorthy's WYSIWYG editor. Use when creating workspace dashboards, help center pages, case note templates, email templates, or any custom HTML layout inside CaseWorthy. Handles all platform constraints automatically: inline CSS only, no JavaScript, SVG icons, system fonts. Triggers on: 'build a dashboard', 'help center page', 'case note template', 'CaseWorthy HTML', 'workspace page', 'WYSIWYG template', 'email template for CaseWorthy', or any request to create HTML that will be pasted into CaseWorthy's editor."
---

# CaseWorthy HTML/CSS Builder

Build HTML templates that work inside CaseWorthy's WYSIWYG editor. One request produces copy-paste ready HTML.

## Platform Constraints

These rules apply to EVERY build. Do not deviate.

### 1. CSS Styling
- **Inline CSS works**: `style=""` on every element — most reliable, always works
- **Style blocks work**: `<style>.class { }</style>` — confirmed working in CaseWorthy
- **Both approaches are valid**. Use style blocks for repeated styles, inline for one-offs.
- Do NOT use `<link>` to external stylesheets
- Confirmed working CSS features: gradients, box-shadow, border-radius, rgba(), flexbox, flex-wrap, inline-block, position relative, overflow hidden, max-width with auto margins

```html
<!-- BOTH WORK -->
<style>
  .card { background: #1a5276; padding: 20px; border-radius: 8px; color: #fff; }
</style>
<div class="card">Styled with class</div>

<div style="background: #1a5276; padding: 20px; border-radius: 8px; color: #fff;">Styled inline</div>
```

### 2. No JavaScript
- CaseWorthy strips all JavaScript
- No `<script>` tags
- No `onclick`, `onload`, or any event handlers
- No dynamic behavior via JavaScript
- Interactive elements are limited to `<a href="">` links
- **EXCEPTION: SVG `<animate>` tags DO work.** Native SVG animation is not JavaScript and CaseWorthy allows it. Use for shimmer effects, pulsing indicators, moving highlights, and loading-style animations.

```html
<!-- SVG Animation Example: Shimmer text effect -->
<svg viewBox="0 0 1000 72" width="100%" height="72">
  <defs>
    <clipPath id="title_clip">
      <text x="500" y="46" text-anchor="middle"
            font-family="system-ui, Segoe UI, Roboto, Arial, sans-serif"
            font-size="40" font-weight="800">Page Title</text>
    </clipPath>
  </defs>
  <text x="500" y="46" text-anchor="middle"
        font-family="system-ui, Segoe UI, Roboto, Arial, sans-serif"
        font-size="40" font-weight="800" fill="#23466E">Page Title</text>
  <rect x="0" y="0" width="160" height="72" clip-path="url(#title_clip)"
        fill="#FFFFFF" opacity=".26">
    <animate attributeName="x" from="0" to="1000" dur="3.4s" repeatCount="indefinite"/>
  </rect>
</svg>
```

### 3. Icons and SVG
- Use inline SVG with `viewBox` for icons (confirmed working in CaseWorthy)
- SVG supports: shapes, paths, text, gradients, clipPath, defs, and `<animate>` tags
- Use Unicode emoji as an alternative: `&#128200;` or paste directly
- Do NOT use icon libraries (Font Awesome, Material Icons, Lucide)
- Do NOT reference external image URLs unless user provides them

```html
<!-- SVG Icon Example -->
<svg viewBox="0 0 48 48" width="32" height="32">
  <circle cx="24" cy="24" r="20" fill="none" stroke="#ffffff" stroke-width="3"/>
</svg>

<!-- SVG with animation -->
<svg viewBox="0 0 48 48" width="32" height="32">
  <circle cx="24" cy="24" r="8" fill="#27ae60" opacity="0.6">
    <animate attributeName="r" values="8;12;8" dur="2s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.6;0.2;0.6" dur="2s" repeatCount="indefinite"/>
  </circle>
  <circle cx="24" cy="24" r="5" fill="#27ae60"/>
</svg>

<!-- Emoji Example -->
<span style="font-size: 18px;">&#128203;</span>
```

### 4. Fonts
- Use the system font stack: `font-family: system-ui, Segoe UI, Roboto, Arial, sans-serif;`
- This renders the native font on each OS (Segoe on Windows, SF Pro on Mac, Roboto on Android)
- Do NOT load Google Fonts or any external fonts
- Always specify `font-family` in inline styles
- SVG text elements also support font-family, font-size, font-weight

### 5. Layout
- Flexbox works: `style="display: flex; gap: 20px;"`
- Inline-block works: `style="display: inline-block; width: 30%;"`
- Use `min-width` on flex children for responsive behavior
- Use `flex-wrap: wrap;` for mobile fallback
- Tables are fine for actual tabular data

### 6. Links
- Standard `<a href="URL">` tags
- Use placeholder URLs: `#HELPDESK_URL`, `#ARTICLE_URL`, `#ENROLLMENT_URL`
- Include comment noting all placeholder URLs for find-and-replace

### 7. Colors
- Hex codes in inline styles
- Maintain consistent palette across the template
- Ensure accessible contrast ratios

### 8. Output Format
- Raw HTML only — no markdown fences wrapping the output
- HTML comments at the top identifying the template
- HTML comments before each major section
- Copy-paste ready for CaseWorthy's WYSIWYG editor

## Template Types

When user requests a template, identify which type and follow the corresponding pattern:

### Help Center Dashboard
Sections: Hero banner with stats → Quick action cards (3 across) → Two-column workflow navigation → Manager resources → Footer

### Case Note Template
Sections: Client/program header bar → Contact info fields → Note category area → Case note body → Follow-up actions → Supervisor review area

### Program Dashboard
Sections: Program header → Key metrics row → Workflow navigation list → Quick links → Recent announcements → Program contacts

### Workspace Landing Page
Sections: Welcome banner → Navigation cards → Resource links → Announcements → Contact info

### Email Template
Sections: Header with logo placeholder → Content area → Action button (styled link) → Footer with contact info. Max width 600px.

### Announcement Banner
Single element: Colored bar with icon, title, message, optional link. Provide versions for info (blue), warning (yellow), critical (red), success (green).

### Training Resource Page
Sections: Video tutorials list → Written guides list → Quick reference cards → FAQ → Training contact info

### Staff Directory
Sections: Card grid layout → Each card: name, title, department, phone, email. 2-3 cards per row.

## Build Workflow

1. **Confirm type** — Ask user which template type they need if not clear
2. **Gather specifics** — What sections, how many items, what colors, what content
3. **Build HTML** — Follow all constraints above
4. **Add placeholders** — Use `#URL_NAME` format for all links
5. **Add comments** — Section markers and customization notes
6. **Output** — Deliver raw HTML, no code fences, no extra explanation mixed in

## SVG Icon Library

Use these pre-built icons in templates. Change `stroke` or `fill` colors as needed.

### Document
```html
<svg viewBox="0 0 48 48" width="32" height="32"><path d="M14 6 L14 42 L34 42 L34 14 L26 6 Z" fill="none" stroke="#ffffff" stroke-width="3" stroke-linejoin="round"/><path d="M26 6 L26 14 L34 14" fill="none" stroke="#ffffff" stroke-width="3" stroke-linejoin="round"/></svg>
```

### Checkmark
```html
<svg viewBox="0 0 48 48" width="32" height="32"><circle cx="24" cy="24" r="20" fill="none" stroke="#27ae60" stroke-width="3"/><path d="M14 24 L21 31 L34 18" fill="none" stroke="#27ae60" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/></svg>
```

### Person
```html
<svg viewBox="0 0 48 48" width="32" height="32"><circle cx="24" cy="16" r="8" fill="none" stroke="#ffffff" stroke-width="3"/><path d="M8 42 C8 32 16 26 24 26 C32 26 40 32 40 42" fill="none" stroke="#ffffff" stroke-width="3"/></svg>
```

### Gear
```html
<svg viewBox="0 0 48 48" width="32" height="32"><circle cx="24" cy="24" r="8" fill="none" stroke="#ffffff" stroke-width="3"/><circle cx="24" cy="24" r="16" fill="none" stroke="#ffffff" stroke-width="3" stroke-dasharray="6 4"/></svg>
```

### Search
```html
<svg viewBox="0 0 48 48" width="32" height="32"><circle cx="20" cy="20" r="12" fill="none" stroke="#ffffff" stroke-width="3"/><line x1="29" y1="29" x2="40" y2="40" stroke="#ffffff" stroke-width="3" stroke-linecap="round"/></svg>
```

### Warning
```html
<svg viewBox="0 0 48 48" width="32" height="32"><path d="M24 6 L42 40 L6 40 Z" fill="none" stroke="#f39c12" stroke-width="3" stroke-linejoin="round"/><line x1="24" y1="18" x2="24" y2="30" stroke="#f39c12" stroke-width="3" stroke-linecap="round"/><circle cx="24" cy="35" r="1.5" fill="#f39c12"/></svg>
```

### Calendar
```html
<svg viewBox="0 0 48 48" width="32" height="32"><rect x="6" y="10" width="36" height="32" rx="4" fill="none" stroke="#ffffff" stroke-width="3"/><line x1="6" y1="20" x2="42" y2="20" stroke="#ffffff" stroke-width="3"/><line x1="16" y1="6" x2="16" y2="14" stroke="#ffffff" stroke-width="3" stroke-linecap="round"/><line x1="32" y1="6" x2="32" y2="14" stroke="#ffffff" stroke-width="3" stroke-linecap="round"/></svg>
```

### Money
```html
<svg viewBox="0 0 48 48" width="32" height="32"><circle cx="24" cy="24" r="20" fill="none" stroke="#ffffff" stroke-width="3"/><text x="24" y="30" text-anchor="middle" fill="#ffffff" font-size="20" font-family="Arial" font-weight="bold">$</text></svg>
```

### Chart
```html
<svg viewBox="0 0 48 48" width="32" height="32"><rect x="6" y="28" width="8" height="14" rx="1" fill="#ffffff"/><rect x="20" y="18" width="8" height="24" rx="1" fill="#ffffff"/><rect x="34" y="8" width="8" height="34" rx="1" fill="#ffffff"/></svg>
```

### Megaphone
```html
<svg viewBox="0 0 48 48" width="32" height="32"><path d="M8 20 L8 28 L16 28 L28 38 L28 10 L16 20 Z" fill="none" stroke="#ffffff" stroke-width="3" stroke-linejoin="round"/><path d="M34 18 C37 21 37 27 34 30" fill="none" stroke="#ffffff" stroke-width="2.5" stroke-linecap="round"/><path d="M38 14 C43 19 43 29 38 34" fill="none" stroke="#ffffff" stroke-width="2.5" stroke-linecap="round"/></svg>
```

### Ticket / Support
```html
<svg viewBox="0 0 48 48" width="32" height="32"><rect x="4" y="8" width="40" height="28" rx="4" fill="none" stroke="#ffffff" stroke-width="3"/><line x1="12" y1="18" x2="36" y2="18" stroke="#ffffff" stroke-width="2"/><line x1="12" y1="24" x2="30" y2="24" stroke="#ffffff" stroke-width="2"/><line x1="12" y1="30" x2="24" y2="30" stroke="#ffffff" stroke-width="2"/></svg>
```

### Books / Knowledge Base
```html
<svg viewBox="0 0 48 48" width="32" height="32"><rect x="6" y="4" width="28" height="36" rx="2" fill="none" stroke="#ffffff" stroke-width="3"/><rect x="14" y="8" width="28" height="36" rx="2" fill="none" stroke="#ffffff" stroke-width="3"/><line x1="20" y1="18" x2="36" y2="18" stroke="#ffffff" stroke-width="2"/><line x1="20" y1="24" x2="36" y2="24" stroke="#ffffff" stroke-width="2"/><line x1="20" y1="30" x2="32" y2="30" stroke="#ffffff" stroke-width="2"/></svg>
```

## SVG Animation Library

CaseWorthy supports native SVG `<animate>` tags. These provide animation without JavaScript. Use for visual polish on headers, status indicators, and attention-drawing elements.

### Available SVG Animation Attributes
- `attributeName` — which attribute to animate (x, y, r, opacity, fill, width, height, etc.)
- `from` / `to` — start and end values
- `values` — keyframe values (alternative to from/to for multi-step)
- `dur` — duration (e.g., "2s", "3.4s")
- `repeatCount` — "indefinite" for looping, or a number
- `begin` — delay before starting (e.g., "0.5s")

### Shimmer Text Effect
A highlight sweeps across text. Uses clipPath to mask a moving rectangle to the text shape.

```html
<svg viewBox="0 0 1000 72" width="100%" height="72">
  <defs>
    <clipPath id="title_clip">
      <text x="500" y="46" text-anchor="middle"
            font-family="system-ui, Segoe UI, Roboto, Arial, sans-serif"
            font-size="40" font-weight="800">Page Title</text>
    </clipPath>
  </defs>
  <text x="500" y="46" text-anchor="middle"
        font-family="system-ui, Segoe UI, Roboto, Arial, sans-serif"
        font-size="40" font-weight="800" fill="#23466E">Page Title</text>
  <rect x="0" y="0" width="160" height="72" clip-path="url(#title_clip)"
        fill="#FFFFFF" opacity=".26">
    <animate attributeName="x" from="0" to="1000" dur="3.4s" repeatCount="indefinite"/>
  </rect>
</svg>
```

### Pulsing Status Indicator
A green dot that pulses — use for "online" or "active" status.

```html
<svg viewBox="0 0 24 24" width="16" height="16" style="display: inline-block; vertical-align: middle;">
  <circle cx="12" cy="12" r="6" fill="#27ae60" opacity="0.4">
    <animate attributeName="r" values="6;10;6" dur="2s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.4;0.1;0.4" dur="2s" repeatCount="indefinite"/>
  </circle>
  <circle cx="12" cy="12" r="4" fill="#27ae60"/>
</svg>
```

### Breathing Glow
An element gently glows — use on hero banners or featured cards.

```html
<svg viewBox="0 0 200 200" width="200" height="200" style="position: absolute; top: -50px; right: -50px; opacity: 0.3;">
  <circle cx="100" cy="100" r="60" fill="#2e86c1">
    <animate attributeName="r" values="60;80;60" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.3;0.1;0.3" dur="4s" repeatCount="indefinite"/>
  </circle>
</svg>
```

### Loading Bar
A simple left-to-right progress animation.

```html
<svg viewBox="0 0 400 8" width="100%" height="8">
  <rect x="0" y="0" width="400" height="8" rx="4" fill="#e5e7eb"/>
  <rect x="0" y="0" width="120" height="8" rx="4" fill="#2e86c1">
    <animate attributeName="x" from="-120" to="400" dur="2s" repeatCount="indefinite"/>
  </rect>
</svg>
```

### Attention Arrow
A bouncing arrow that draws attention to a link or action.

```html
<svg viewBox="0 0 24 24" width="18" height="18" style="display: inline-block; vertical-align: middle;">
  <path d="M5 12 L19 12 M13 6 L19 12 L13 18" fill="none" stroke="#2e86c1" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
    <animate attributeName="opacity" values="1;0.3;1" dur="1.5s" repeatCount="indefinite"/>
  </path>
</svg>
```

### Rotating Gear (Loading/Processing)
```html
<svg viewBox="0 0 48 48" width="24" height="24" style="display: inline-block; vertical-align: middle;">
  <circle cx="24" cy="24" r="8" fill="none" stroke="#2e86c1" stroke-width="3"/>
  <circle cx="24" cy="24" r="16" fill="none" stroke="#2e86c1" stroke-width="3" stroke-dasharray="20 80">
    <animateTransform attributeName="transform" type="rotate" from="0 24 24" to="360 24 24" dur="2s" repeatCount="indefinite"/>
  </circle>
</svg>
```

### SVG Animation Rules
- Keep animations subtle — these are professional tools, not toys
- Use `dur` values of 2-4 seconds for smooth, non-distracting motion
- `repeatCount="indefinite"` for continuous animations
- Combine multiple `<animate>` tags on the same element for complex effects
- Use unique `id` values for clipPath and defs to avoid conflicts when multiple SVGs are on the same page
- Test in CaseWorthy — some older browser versions used in CaseWorthy may handle SVG animations differently

## Color Palettes

### Professional Blue (Default)
- Hero/Footer gradient: `#1a5276` → `#2e86c1`
- Primary: `#2e86c1`
- Success: `#27ae60`
- Warning: `#e67e22`
- Danger: `#e74c3c`
- Purple: `#8e44ad`
- Yellow: `#f39c12`
- Text: `#1a1a2e`
- Secondary text: `#6b7280`
- Borders: `#e5e7eb`

### Warm Earth
- Hero/Footer gradient: `#5d4037` → `#795548`
- Primary: `#795548`
- Success: `#4caf50`
- Warning: `#ff9800`
- Danger: `#f44336`

### Dark Theme
- Hero/Footer gradient: `#0a0e17` → `#1a2233`
- Primary: `#3b82f6`
- Success: `#10b981`
- Warning: `#f59e0b`
- Danger: `#ef4444`