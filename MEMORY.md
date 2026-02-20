# Somatic Project - Memory

## Project: Davide Grazioli Studio Website
- One-page bilingual (IT/EN) site using Canvas 7 template
- Working directory: `C:\dev_notebook\somatic`
- Serve via `python -m http.server 8080` (Canvas JS needs HTTP, not file://)

## Canvas 7 Template - Critical Lessons
See [canvas7-gotchas.md](canvas7-gotchas.md) for details.

- **Never build from scratch** with Canvas 7. Start from a working HTML file (e.g. `index-classic.html`) and modify incrementally.
- Canvas CSS/JS are tightly coupled - classes trigger JS behaviors that are not obvious from CSS alone.

## Bilingual Implementation
- Use `data-lang-it` / `data-lang-en` attributes on elements
- **Inside `.menu-link`**: use `<em class="not-italic">` NOT `<span>` (Canvas hides spans in menu links)
- JS toggle switches `display` on all `[data-lang-*]` elements

## Preferenze Git
- Utente: `iemiil <emr@webfactory.it>` (config locale al repo)
- **Mai aggiungere Co-Authored-By nei commit** - usare solo l'utente git configurato

## Key Files
- `index.html` - main site file
- `css/custom.css` - all project-specific styles
- `css/fonts.css` - font overrides (Poppins/Lato/PT Serif, copied from Canvas demo)
- Client images: `images/sfondo-home.jpg`, `images/sfondo-percorsi.jpg`, `images/foto-bio.jpg`

## Hosting
- Netlify: `https://spontaneous-pavlova-4731cc.netlify.app`
- Branch URL pattern: `https://[branch-name]--spontaneous-pavlova-4731cc.netlify.app` (slash → dash)
- Branch deploy va attivato in Netlify: Site settings → Branch deploys → All branches

## Colori Brand
- Verde foresta Grazioli: `#3d6b35` (estratto da post Instagram)

## Sezione Percorsi
- Usa accordion Canvas nativo (non più Bootstrap card)
- `data-collapsible="true"` permette chiusura di tutti i pannelli
- Stile su sfondo scuro via `.accordion-percorsi` in custom.css
