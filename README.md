# CaseWorthy HTML Dashboard Templates

Build custom dashboards, help centers, and workspace pages inside CaseWorthy using pure HTML and CSS. Includes ready-to-use templates, AI prompts for every major platform, and a downloadable Claude skill.

CaseWorthy's WYSIWYG editor accepts raw HTML, which means you can build polished UI experiences that go well beyond what the default editor offers. The catch is the platform has strict constraints: no JavaScript, no external resources, inline CSS only. This repo handles all of that for you.

## What's Inside

```
├── README.md                          ← You are here
├── templates/
│   └── help_center_dashboard.html     ← Ready-to-use help center template
├── prompts/
│   ├── universal_ai_prompt.md         ← System prompt for any AI assistant
│   └── quick_reference.md             ← Cheat sheet: what works, SVG icons, layouts
└── skill/
    └── SKILL.md                       ← Claude skill file (download and use directly)
```

## Quick Start

### Option 1: Use a Template Directly
1. Open `templates/help_center_dashboard.html` in a text editor
2. Replace placeholder URLs (`#HELPDESK_URL`, `#KNOWLEDGE_BASE_URL`, etc.) with your actual links
3. Update text, colors, and sections to match your organization
4. Paste the HTML into CaseWorthy's WYSIWYG editor
5. Preview and publish

### Option 2: Build Custom Templates with AI
1. Pick your AI assistant (Claude, Gemini, ChatGPT, Copilot, or any other)
2. Load the system prompt from `prompts/universal_ai_prompt.md` (setup instructions for each platform are included in the file)
3. Use the build commands to request specific templates
4. Paste the output into CaseWorthy and customize

### Option 3: Use the Claude Skill
1. Create a new Claude Project at [claude.ai](https://claude.ai)
2. Upload `skill/SKILL.md` as project knowledge
3. Start chatting — ask Claude to build any CaseWorthy template
4. Claude will follow all platform constraints automatically

## Platform Constraints

CaseWorthy's WYSIWYG editor has specific limitations. Everything in this repo is built to work within them.

| What Works | What Doesn't |
|-----------|--------------|
| Inline CSS (`style=""`) | `<style>` blocks |
| SVG icons (`<svg viewBox="">`) | Icon libraries (Font Awesome, etc.) |
| Unicode emoji | External images (unless you host them) |
| Links (`<a href="">`) | JavaScript (`<script>`, `onclick`, etc.) |
| Flexbox (inline) | External CSS (`<link>`) |
| System fonts (Arial) | Google Fonts or external fonts |
| Gradients, shadows, border-radius | CSS classes/IDs (no style block to define them) |

## Template Types You Can Build

| Type | Description |
|------|-------------|
| **Help Center Dashboard** | Landing page with navigation cards, quick actions, and resource links |
| **Case Note Template** | Structured documentation layout with sections and data fields |
| **Program Dashboard** | Program-specific navigation with enrollment workflows |
| **Workspace Landing Page** | Welcome page with navigation and announcements |
| **Email Template** | System notification layouts (max 600px wide) |
| **Announcement Banner** | Alert bars for system updates (info, warning, critical, success) |
| **Training Resource Page** | Organized training content with video links and guides |
| **Staff Directory** | Contact cards in a responsive grid layout |

## AI Prompt Compatibility

The universal prompt in `prompts/universal_ai_prompt.md` works with:

| Platform | How to Load |
|----------|-------------|
| **Claude** | Create a Project → add as project knowledge, OR paste at start of conversation |
| **Gemini** | Create a Gem → paste into instructions, OR paste into conversation |
| **ChatGPT** | Create a custom GPT → paste into instructions, OR use Custom Instructions |
| **Copilot** | Paste at start of conversation or into Notebook |
| **Llama / Mistral** | Set as system message in Ollama, LM Studio, or WebUI |

## What's in the Help Center Template

The included `help_center_dashboard.html` provides:

- **Hero banner** with gradient background, SVG icon, and stat counters
- **Quick action cards** (3 across) for help desk, knowledge base, and announcements
- **Two-column workflow navigation** with color-coded items and descriptions
  - Left: Client Services (Referrals, Screening, Enrollment, Management, Client Info, Exit)
  - Right: System Resources (Navigation, Setup, Case Notes, Financial Assistance, Activity Logs, Troubleshooting)
- **Manager resources section** with dedicated card
- **Footer** with branding, last updated date, and version number

All links use placeholder URLs for easy find-and-replace. All icons are inline SVG. All styles are inline CSS.

## The Claude Skill

The `skill/SKILL.md` file is a complete Claude skill that can be downloaded and added to any Claude Project. It includes:

- All platform constraints encoded so Claude follows them automatically
- Template type definitions with section patterns
- A library of 11 pre-built SVG icons ready to use
- Three color palettes (Professional Blue, Warm Earth, Dark Theme)
- Build workflow that produces copy-paste ready HTML

To use it: download the file, create a Claude Project, click "Set custom instructions" or add as project knowledge, and start building.

## Customization Guide

### Changing Colors
Search for hex codes in the HTML and replace them. The default palette:

| Color | Hex | Used For |
|-------|-----|----------|
| Dark Blue | `#1a5276` | Hero/footer gradient start |
| Blue | `#2e86c1` | Primary accent, gradient end |
| Green | `#27ae60` | Success, help desk card |
| Orange | `#e67e22` | Warnings, announcements card |
| Red | `#e74c3c` | Intake/exit indicators |
| Purple | `#8e44ad` | Client info, troubleshooting |
| Yellow | `#f39c12` | Enrollment indicators |

### Changing Links
All placeholder URLs follow the `#NAME_URL` pattern. Find and replace:

| Placeholder | Replace With |
|-------------|-------------|
| `#HELPDESK_URL` | Your help desk ticket submission URL |
| `#KNOWLEDGE_BASE_URL` | Your knowledge base or help articles URL |
| `#ANNOUNCEMENTS_URL` | Your system announcements page |
| `#REFERRALS_URL` | Help article or page for referrals |
| `#SCREENING_URL` | Help article or page for screening |
| `#ENROLLMENT_URL` | Help article or page for enrollment |
| `#MANAGEMENT_URL` | Help article or page for case management |
| `#CLIENT_INFO_URL` | Help article or page for client data |
| `#EXIT_URL` | Help article or page for program exit |
| `#NAVIGATION_URL` | Help article for system navigation |
| `#USER_SETUP_URL` | Help article for user configuration |
| `#CASE_NOTES_URL` | Help article for case notes |
| `#TFA_URL` | Help article for financial assistance |
| `#ACTIVITY_LOGS_URL` | Help article for activity logs |
| `#TROUBLESHOOTING_URL` | Help article for troubleshooting |
| `#MANAGER_RESOURCES_URL` | Manager resources page |

### Adding or Removing Items
Each workflow row is a self-contained block. Copy an existing row and change the text, color, icon, and URL. Delete rows you don't need.

## Author

James Calby — [jamescalby.com](https://jamescalby.com)

## License

MIT
