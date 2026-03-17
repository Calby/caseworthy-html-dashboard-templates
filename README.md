# CaseWorthy HTML Dashboard Templates

Pure HTML/CSS templates designed to work inside CaseWorthy's WYSIWYG editor. No JavaScript, no external dependencies, no frameworks. Just paste into a workspace page and customize.

## What's Included

### Help Center Dashboard
A full help center landing page with:
- Hero banner with stats counters
- Quick action cards linking to help desk, knowledge base, and announcements
- Two-column workflow navigation (Client Services + System Resources)
- Manager/Supervisor resources section
- Branded footer with version info

## Design Constraints

CaseWorthy's WYSIWYG environment has specific limitations. These templates are built to work within them:

| Constraint | Approach |
|-----------|----------|
| No JavaScript | Pure HTML/CSS only |
| CSS approach | Inline styles (`style=""`) on every element — most reliable |
| Icons | SVG viewboxes and Unicode emoji — no external images required |
| Links | Standard `<a href="">` tags pointing to help desk URLs, knowledge base, or other CaseWorthy pages |
| Layout | Flexbox via inline styles for two-column layouts |
| Fonts | Arial/sans-serif system fonts (no external font loading) |

## Where to Use These

CaseWorthy supports custom HTML in several areas:
- **Workspace landing pages / dashboards** — primary use case
- **Help center pages** — what this template was designed for
- **Case note templates** — structured documentation layouts
- **Email templates** — system-generated communications

## How to Customize

1. Open the HTML file in any text editor
2. Replace `#HELPDESK_URL`, `#KNOWLEDGE_BASE_URL`, etc. with your actual URLs
3. Update text labels to match your organization's terminology
4. Change colors by modifying the hex values in `style=""` attributes
5. Add or remove workflow rows as needed
6. Paste the entire HTML into CaseWorthy's WYSIWYG editor

### Color Reference

The template uses these colors by default:

| Color | Hex | Used For |
|-------|-----|----------|
| Dark Blue | `#1a5276` | Hero/footer gradient |
| Blue | `#2e86c1` | Primary accent, links |
| Green | `#27ae60` | Help desk card, success items |
| Orange | `#e67e22` | Announcements card, warnings |
| Red | `#e74c3c` | Intake/exit indicators |
| Purple | `#8e44ad` | Client info, troubleshooting |
| Yellow | `#f39c12` | Enrollment indicators |

## Building with AI Copilots

These templates were designed with the help of AI copilots (Claude, Gemini). The key to getting useful output from AI for CaseWorthy HTML is giving it the right constraints upfront:

1. **Specify inline CSS only** — AI defaults to `<style>` blocks or external CSS
2. **No JavaScript** — AI loves adding interactivity; CaseWorthy strips it
3. **SVG for icons** — tell it to use SVG viewboxes instead of icon libraries
4. **System fonts only** — no Google Fonts or external font loading
5. **Test in CaseWorthy** — AI output always needs verification in the actual platform

See the [AI Prompts for Case Management](https://github.com/Calby/ai-prompts-case-management) repo for structured prompts that handle these constraints automatically.

## Author

James Calby — [jamescalby.com](https://jamescalby.com)

## License

MIT
