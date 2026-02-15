# Davide Grazioli Studio - Sito Web

## Panoramica
Sito web one-page bilingue (IT/EN) per Davide Grazioli, Counselor Professionale, Somatic Experiencing Practitioner, NARM Practitioner e formatore. Costruito sul template HTML Canvas 7.

## Stack Tecnologico
- **Template**: Canvas 7 (basato su Bootstrap 5, con framework JS proprietario)
- **Server**: `python -m http.server 8080` dalla root del progetto (necessario - il JS di Canvas non funziona da `file://`)
- **Nessun build step**: HTML/CSS/JS puri

## Struttura del Progetto
```
index.html          # Sito principale (tutte le sezioni)
style.css           # Stili core di Canvas (NON MODIFICARE)
css/custom.css      # Tutti gli stili personalizzati del progetto
css/font-icons.css  # Icon font di Canvas
css/swiper.css      # Stili plugin Swiper
js/plugins.min.js   # Plugin Canvas (include jQuery)
js/functions.bundle.js  # JS framework Canvas
images/             # Tutte le immagini (incluse quelle del cliente)
include/            # Include server-side di Canvas (gestione form)
```

## File da Modificare
- `index.html` - contenuti, struttura, testi bilingui
- `css/custom.css` - tutte le personalizzazioni visive

## Regole Canvas 7 (IMPORTANTE)
1. **Mai usare la classe `one-page-menu`** sui container del menu - rompe il rendering del menu
2. **Mai usare `<span>` dentro `.menu-link`** - Canvas li nasconde (usare `<em class="not-italic">`)
3. **Header trasparente** richiede la struttura completa Swiper slider con classe `include-header`
4. **Testo menu bianco sull'hero**: va limitato a `.is-expanded-menu` per non rompere il dropdown mobile
5. **Partire sempre da file template funzionanti** quando si aggiungono nuove pagine - mai costruire da zero
6. **Mai mischiare strutture di template diversi** - duplicare un file funzionante e modificarlo. In questo progetto l'utente aveva solo richiesto un sito one-page; la scelta di combinare `index-onepage.html` e `index-classic.html` è stata un'interpretazione dell'assistente che ha causato la maggior parte dei problemi di debug. L'approccio corretto era partire da `index-classic.html` (che funzionava) e adattarlo per la navigazione one-page

## Sistema Bilingue
- Attributi `data-lang-it` / `data-lang-en` sugli elementi
- Lingua predefinita: italiano
- Pulsante toggle nell'header cambia la visibilità via JS
- Nel menu di navigazione: usare tag `<em>`, ovunque altro: `<span>` va bene

## Immagini del Cliente
- `images/sfondo-home.jpg` - Sfondo hero
- `images/sfondo-percorsi.jpg` - Sfondo sezione percorsi
- `images/foto-bio.jpg` - Foto ritratto bio
- Originali in: `C:\Users\EmilianoRustighini\OneDrive - WEB FACTORY SRL\Clienti OneDrive\ghiraldello.it\Grazioli - somatic\Immagini\`

## Sezioni
1. **Hero** - fullscreen con Swiper slider, overlay, CTA
2. **Percorsi** - 3 card servizi (teal #2a7d6f / chiaro / teal)
3. **Chi Sono** - testo bio + foto (2 colonne)
4. **Contatti** - info + form di contatto
5. **Footer** - minimale (copyright, email, telefono)
