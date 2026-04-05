# FreeFlow Automations — Landing Page

## Project
Single file landing page: index.html with embedded CSS and JS. No frameworks.

## Stack
Pure HTML, CSS, JavaScript. No npm, no build tools.

## Deployment
GitHub repo: sanderilves/ai-automation-landing
Hosted on Netlify at freeflowautomations.com
Push to GitHub triggers auto-deploy.

## Brand
Company: FreeFlow Automations
Email: sander@freeflowautomations.com
Phone: +372 58 133 551
Location: Tallinn, Estonia

## Rules
- Never use inline styles, always use CSS classes
- Keep all code in index.html as a single file
- Match existing visual style before making changes
- Mobile responsive — always check for overflow issues
- Max content width 760px centered with auto margins
- When pushing to GitHub always use: git add . && git commit -m "description" && git push

## Permissions
- You have permission to read, write, edit, and run bash commands without asking for approval each time

## Design & Visual Consistency Standards

### Typography
- Font stack must remain consistent throughout — do not introduce new fonts
- Heading hierarchy must be maintained: H1 (one per page), H2 (sections), H3 (subsections)
- Never use font sizes outside the established scale
- No bold or italic used decoratively — only for semantic emphasis

### Colours
- Never introduce new colours outside the existing palette
- Background, text, accent, and border colours must match what is already used on the page
- Check existing CSS variables before adding any colour value

### Spacing & Layout
- Section padding must be consistent with existing sections — check neighbouring sections before setting padding values
- Mobile-first — every new section must be tested at 375px width
- Max content width must match the existing container width throughout
- New sections must follow the same left/right margin as existing sections

### Components
- Buttons must match existing button styles — do not create new variants without instruction
- Cards must match existing card styles (border-radius, shadow, padding)
- Icons must come from the same icon set already used on the page
- Do not add new third-party libraries or CDN links without instruction

### Images
- All images must have: alt text, width, height, loading="lazy"
- Profile photos must use consistent border-radius treatment
- No images wider than the content container
- Compress images before adding — target under 200KB

### New Sections Checklist
Before adding any new section, confirm:
- Heading level is correct in hierarchy
- Colours match existing palette
- Spacing matches neighbouring sections
- Mobile layout tested at 375px
- Any new images have alt, width, height, loading="lazy"
- Section has a semantic HTML wrapper (<section> with id)
- New FAQ items added to both visible HTML and FAQPage schema
