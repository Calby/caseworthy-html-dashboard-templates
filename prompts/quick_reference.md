# CaseWorthy HTML/CSS Quick Reference

A cheat sheet for building HTML templates inside CaseWorthy. Pin this, print it, keep it handy.

---

## What Works

| Element | Example | Notes |
|---------|---------|-------|
| Inline CSS | `style="color: #333; padding: 10px;"` | Most reliable approach |
| SVG icons | `<svg viewBox="0 0 48 48" width="32" height="32">...</svg>` | Use for all icons |
| Unicode emoji | `&#128200;` or copy-paste 📈 | Simpler alternative to SVG |
| Links | `<a href="https://example.com">Click</a>` | Standard anchor tags |
| Flexbox | `style="display: flex; gap: 20px;"` | For multi-column layouts |
| Inline-block | `style="display: inline-block; width: 30%;"` | For side-by-side elements |
| Tables | `<table>` with inline styles | For actual tabular data |
| Divs | `<div style="...">` | Primary layout element |
| Border-radius | `style="border-radius: 8px;"` | Rounded corners work |
| Gradients | `style="background: linear-gradient(135deg, #1a5276, #2e86c1);"` | For hero banners |
| Box shadow | `style="box-shadow: 0 2px 8px rgba(0,0,0,0.1);"` | Subtle depth effects |

## What Doesn't Work

| Element | Why |
|---------|-----|
| `<script>` tags | JavaScript is stripped |
| `onclick`, `onload`, etc. | Event handlers are stripped |
| `<style>` blocks | May not render — use inline instead |
| External CSS (`<link>`) | Not loaded |
| External fonts (Google Fonts) | Not loaded |
| Icon libraries (Font Awesome) | Requires external CSS |
| External images (usually) | Unless you provide a hosted URL |
| CSS classes/IDs for styling | No `<style>` block to define them |
| Form inputs | No JS to process them |
| iframes | Security restrictions |

---

## Common SVG Icons

Copy and paste these directly into your templates.

### Document / File
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <path d="M14 6 L14 42 L34 42 L34 14 L26 6 Z" fill="none" stroke="#ffffff" stroke-width="3" stroke-linejoin="round"/>
  <path d="M26 6 L26 14 L34 14" fill="none" stroke="#ffffff" stroke-width="3" stroke-linejoin="round"/>
</svg>
```

### Checkmark / Approval
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <circle cx="24" cy="24" r="20" fill="none" stroke="#27ae60" stroke-width="3"/>
  <path d="M14 24 L21 31 L34 18" fill="none" stroke="#27ae60" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
```

### User / Person
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <circle cx="24" cy="16" r="8" fill="none" stroke="#ffffff" stroke-width="3"/>
  <path d="M8 42 C8 32 16 26 24 26 C32 26 40 32 40 42" fill="none" stroke="#ffffff" stroke-width="3"/>
</svg>
```

### Settings / Gear
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <circle cx="24" cy="24" r="8" fill="none" stroke="#ffffff" stroke-width="3"/>
  <circle cx="24" cy="24" r="16" fill="none" stroke="#ffffff" stroke-width="3" stroke-dasharray="6 4"/>
</svg>
```

### Search / Magnifying Glass
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <circle cx="20" cy="20" r="12" fill="none" stroke="#ffffff" stroke-width="3"/>
  <line x1="29" y1="29" x2="40" y2="40" stroke="#ffffff" stroke-width="3" stroke-linecap="round"/>
</svg>
```

### Alert / Warning
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <path d="M24 6 L42 40 L6 40 Z" fill="none" stroke="#f39c12" stroke-width="3" stroke-linejoin="round"/>
  <line x1="24" y1="18" x2="24" y2="30" stroke="#f39c12" stroke-width="3" stroke-linecap="round"/>
  <circle cx="24" cy="35" r="1.5" fill="#f39c12"/>
</svg>
```

### Calendar / Date
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <rect x="6" y="10" width="36" height="32" rx="4" fill="none" stroke="#ffffff" stroke-width="3"/>
  <line x1="6" y1="20" x2="42" y2="20" stroke="#ffffff" stroke-width="3"/>
  <line x1="16" y1="6" x2="16" y2="14" stroke="#ffffff" stroke-width="3" stroke-linecap="round"/>
  <line x1="32" y1="6" x2="32" y2="14" stroke="#ffffff" stroke-width="3" stroke-linecap="round"/>
</svg>
```

### Money / Financial
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <circle cx="24" cy="24" r="20" fill="none" stroke="#ffffff" stroke-width="3"/>
  <text x="24" y="30" text-anchor="middle" fill="#ffffff" font-size="20" font-family="Arial" font-weight="bold">$</text>
</svg>
```

### Chart / Analytics
```html
<svg viewBox="0 0 48 48" width="32" height="32">
  <rect x="6" y="28" width="8" height="14" rx="1" fill="#ffffff"/>
  <rect x="20" y="18" width="8" height="24" rx="1" fill="#ffffff"/>
  <rect x="34" y="8" width="8" height="34" rx="1" fill="#ffffff"/>
</svg>
```

---

## Color Palettes

### Professional Blue (Default)
```
Hero/Footer:    #1a5276 → #2e86c1 (gradient)
Primary:        #2e86c1
Success:        #27ae60
Warning:        #e67e22
Danger:         #e74c3c
Info:           #2980b9
Purple:         #8e44ad
Text Dark:      #1a1a2e
Text Secondary: #6b7280
Border:         #e5e7eb
Background:     #ffffff
```

### Warm Earth Tones
```
Hero/Footer:    #5d4037 → #795548 (gradient)
Primary:        #795548
Success:        #4caf50
Warning:        #ff9800
Danger:         #f44336
Info:           #607d8b
Purple:         #7b1fa2
Text Dark:      #3e2723
Text Secondary: #757575
Border:         #d7ccc8
Background:     #fafafa
```

### Dark Theme
```
Hero/Footer:    #0a0e17 → #1a2233 (gradient)
Primary:        #3b82f6
Success:        #10b981
Warning:        #f59e0b
Danger:         #ef4444
Info:           #6366f1
Purple:         #8b5cf6
Text Dark:      #e8edf5
Text Secondary: #8b95a8
Border:         #1e293b
Background:     #111827
```

---

## Layout Patterns

### Two Equal Columns
```html
<div style="display: flex; gap: 30px; flex-wrap: wrap;">
  <div style="flex: 1; min-width: 300px;">
    <!-- Left column content -->
  </div>
  <div style="flex: 1; min-width: 300px;">
    <!-- Right column content -->
  </div>
</div>
```

### Three Card Grid
```html
<div style="text-align: center;">
  <div style="display: inline-block; width: 30%; min-width: 200px; vertical-align: top; margin: 0 1%;">
    <!-- Card 1 -->
  </div>
  <div style="display: inline-block; width: 30%; min-width: 200px; vertical-align: top; margin: 0 1%;">
    <!-- Card 2 -->
  </div>
  <div style="display: inline-block; width: 30%; min-width: 200px; vertical-align: top; margin: 0 1%;">
    <!-- Card 3 -->
  </div>
</div>
```

### Section Header with Lines
```html
<div style="display: flex; align-items: center; margin-bottom: 20px;">
  <div style="flex: 1; height: 2px; background: #e5e7eb;"></div>
  <div style="padding: 0 16px; font-family: Arial, sans-serif; font-size: 18px; font-weight: bold;">
    Section Title
  </div>
  <div style="flex: 1; height: 2px; background: #e5e7eb;"></div>
</div>
```

### Navigation Row Item
```html
<a href="#URL" style="text-decoration: none; display: block;">
  <div style="border: 1px solid #e5e7eb; border-left: 4px solid #2e86c1; border-radius: 6px; padding: 14px 16px; margin-bottom: 8px; background: #ffffff;">
    <div style="display: flex; align-items: center;">
      <span style="font-size: 18px; margin-right: 10px;">&#128203;</span>
      <div>
        <div style="font-family: Arial, sans-serif; font-size: 14px; font-weight: bold; color: #2e86c1;">Item Title</div>
        <div style="font-family: Arial, sans-serif; font-size: 12px; color: #6b7280;">Description text goes here</div>
      </div>
    </div>
  </div>
</a>
```

### Hero Banner
```html
<div style="background: linear-gradient(135deg, #1a5276 0%, #2e86c1 100%); border-radius: 12px; padding: 40px 30px; text-align: center;">
  <div style="color: #ffffff; font-family: Arial, sans-serif; font-size: 24px; font-weight: bold; margin-bottom: 8px;">
    Page Title
  </div>
  <div style="color: #d4e6f1; font-family: Arial, sans-serif; font-size: 14px;">
    Subtitle or description text
  </div>
</div>
```

---

## Author

James Calby — [jamescalby.com](https://jamescalby.com)

## License

MIT
