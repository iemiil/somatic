# Davide Grazioli Studio - Sito Web

## Panoramica
Sito web one-page bilingue (IT/EN) per Davide Grazioli, Counselor Professionale, Somatic Experiencing Practitioner, NARM Practitioner e formatore. Costruito sul template HTML Canvas 7.

## Stack Tecnologico
- **Template**: Canvas 7 (basato su Bootstrap 5, con framework JS proprietario)
- **Server locale**: `python -m http.server 8080` oppure VS Code Live Server (necessario per font Google e JS Canvas)
- **Nessun build step**: HTML/CSS/JS puri
- **Repo GitHub**: https://github.com/iemiil/somatic.git
- **Hosting**: Netlify (deploy automatico da GitHub, un URL per branch)

## Struttura del Progetto
```
index.html          # Sito principale (tutte le sezioni)
style.css           # Stili core di Canvas (NON MODIFICARE)
css/custom.css      # Tutti gli stili personalizzati del progetto
css/font-icons.css  # Icon font di Canvas
css/swiper.css      # Stili plugin Swiper
css/fonts.css       # Override font (Poppins, Lato, PT Serif) come demo Canvas
js/plugins.min.js   # Plugin Canvas (include jQuery)
js/functions.bundle.js  # JS framework Canvas
images/             # Tutte le immagini (incluse quelle del cliente)
include/            # Include server-side di Canvas (gestione form)
```

## File da Modificare
- `index.html` - contenuti, struttura, testi bilingui
- `css/custom.css` - tutte le personalizzazioni visive
- `css/fonts.css` - font del sito (copiato dal demo online Canvas)

## Regole Canvas 7 (IMPORTANTE)
1. **Mai usare la classe `one-page-menu`** sui container del menu - rompe il rendering del menu
2. **Mai usare `<span>` dentro `.menu-link`** - Canvas li nasconde (usare `<em class="not-italic">`)
3. **Header trasparente** richiede la struttura completa Swiper slider con classe `include-header`
4. **Testo menu bianco sull'hero**: va limitato a `.is-expanded-menu` per non rompere il dropdown mobile
5. **Tag `<em>` nel menu ereditano il font secondario** di Canvas (`em { font-family: secondary-font }`). Serve `font-family: inherit` su `em.not-italic` nel custom.css
6. **Logo testuale**: Canvas gestisce il toggle logo-default/logo-dark via JS solo per `<img>`. Per logo testo, usare un singolo elemento con colore gestito via CSS (bianco su transparent-header, scuro su sticky). Nascosto su mobile perché il titolo hero è sufficiente
7. **Canvas non ha sistema multilingua** integrato — solo un esempio UI (`menu-with-lang-switcher.html`) senza logica. Il sistema `data-lang-*` con JS custom è necessario
8. **Partire sempre da file template funzionanti** quando si aggiungono nuove pagine - mai costruire da zero
9. **Mai mischiare strutture di template diversi** - duplicare un file funzionante e modificarlo. In questo progetto l'utente aveva solo richiesto un sito one-page; la scelta di combinare `index-onepage.html` e `index-classic.html` è stata un'interpretazione dell'assistente che ha causato la maggior parte dei problemi di debug. L'approccio corretto era partire da `index-classic.html` (che funzionava) e adattarlo per la navigazione one-page
10. **Accordion Canvas**: usare `.accordion` con `data-collapsible="true"` per permettere la chiusura di tutti i pannelli. Icone con `.accordion-closed` / `.accordion-open`. Il JS Canvas inizializza automaticamente tramite `functions.bundle.js`

## Font
- Il demo online Canvas usa `css/fonts.css` che sovrascrive i default con: **Lato** (body), **Poppins** (menu/titoli), **PT Serif** (accenti)
- Canvas di default usa Inter — ma il demo usa Poppins, più leggero e raffinato
- Il tag `<em>` eredita il font secondario di Canvas (Playfair Display → fallback Times New Roman). Serve `font-family: inherit` su `em.not-italic`

## Sistema Bilingue
- Attributi `data-lang-it` / `data-lang-en` sugli elementi
- Lingua predefinita: italiano
- Pulsante toggle nell'header cambia la visibilità via JS
- Nel menu di navigazione: usare tag `<em>`, ovunque altro: `<span>` va bene

## Colori
- **Verde foresta** (brand Grazioli): `#3d6b35`
- **Verde hover**: `#2a4a25`
- Il colore primario di Canvas si cambia tramite variabili CSS in `custom.css` — NON modificando file singoli:
  ```css
  :root {
    --cnvs-themecolor: #3d6b35;
    --cnvs-themecolor-rgb: 61, 107, 53;
  }
  ```
- Documentazione ufficiale: https://docs.semicolonweb.com/docs/getting-started/color-schemes/

## Immagini del Cliente
- `images/sfondo-home.jpg` - Sfondo hero
- `images/sfondo-percorsi.jpg` - Sfondo sezione percorsi
- `images/foto-bio.jpg` - Foto ritratto bio
- Originali in: `C:\Users\EmilianoRustighini\OneDrive - WEB FACTORY SRL\Clienti OneDrive\ghiraldello.it\Grazioli - somatic\Immagini\`

## Sezioni
1. **Hero** - fullscreen con Swiper slider, overlay (opacity 0.25), CTA bottone compatto
2. **Percorsi** - accordion Canvas con 3 percorsi su sfondo foto (overlay 0.45)
3. **Chi Sono** - testo bio + foto (2 colonne, foto si adatta all'altezza del testo)
4. **Contatti** - info + form di contatto
5. **Footer** - minimale (copyright, email, telefono)

## Branch Git
- `master` - stato iniziale del sito
- `fix/canvas-alignment` - allineamento struttura HTML alle convenzioni Canvas 7
- `feedback/grazioli-v1` - implementazione feedback primo round Grazioli (accordion percorsi, verde, mobile)

## Workflow
1. Ogni round di modifiche va su un branch dedicato
2. Push su GitHub → Netlify deploya automaticamente con URL per branch
3. URL branch Netlify: `https://[branch-name]--spontaneous-pavlova-4731cc.netlify.app`
   - I `/` nel nome branch diventano `-` (es. `feedback/grazioli-v1` → `feedback-grazioli-v1`)
4. Netlify branch deploy va attivato in: Site settings → Build & deploy → Branch deploys → All branches
