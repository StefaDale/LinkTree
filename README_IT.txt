LINKTREE - README ITALIANO
==========================

Descrizione
-----------
Questo progetto e' una pagina personale in stile Linktree realizzata con solo HTML e CSS.
Raccoglie in un'unica pagina i link principali del profilo:
Instagram, Facebook, sito web, GitHub, Steam, TikTok e server Discord.

La pagina usa un'immagine di sfondo, bottoni grandi con icone, colori personalizzati per alcuni servizi
e una media query per adattarsi agli schermi piccoli.

Tecnologie
----------
- HTML5
- CSS3
- Asset locali in SVG/JPEG
- Nessun framework
- Nessuna libreria JavaScript
- Nessuna build obbligatoria

Struttura
---------
linktree/
|-- assets/
|   |-- discord_icon.svg
|   |-- facebook_icon.svg
|   |-- favicon.svg
|   |-- github_icon-invertito.svg
|   |-- github_icon.svg
|   |-- instagram_icon.svg
|   |-- steam_icon.svg
|   |-- tiktok_icon.svg
|   |-- wallpaper.jpeg
|   `-- website_icon.svg
|-- index.html
|-- style.css
|-- PROJECT_CONTEXT.md
|-- PROJECT_CONTEXT_EN.md
|-- README_IT.txt
`-- README.txt

File principali
---------------
- index.html: contiene la struttura della pagina, i link, le icone e i meta tag SEO/social.
- style.css: contiene layout, sfondo, colori, hover, responsive e dimensioni dei bottoni.
- assets/: contiene icone, favicon e immagine di sfondo.
- PROJECT_CONTEXT.md: documentazione dettagliata in italiano per IA e sviluppatori.
- PROJECT_CONTEXT_EN.md: traduzione inglese del contesto.

Come avviare il progetto
------------------------
Non serve installare nulla.

Apri direttamente index.html nel browser.

In alternativa puoi usare un server statico locale, ma non e' obbligatorio.

Come modificare i link
----------------------
Apri index.html e modifica gli elementi dentro:

<div class="link-wrapper">
    ...
</div>

Esempio:

<a class="instagram" href="https://instagram.com/ste_catalin_" target="_blank">
    Instagram <img src="assets/instagram_icon.svg" alt="">
</a>

Come modificare la lunghezza dei bottoni
----------------------------------------
Nel file style.css, su desktop la larghezza dei bottoni e' controllata da:

.linktree {
    >.link-wrapper a {
        width: 50%;
    }
}

Per bottoni piu' lunghi usa, ad esempio, width: 60%.
Per bottoni piu' corti usa, ad esempio, width: 40%.

Su mobile la larghezza viene sovrascritta nella media query:

@media (max-width: 600px) {
    .linktree > .link-wrapper a {
        width: 100%;
    }
}

Come modificare lo sfondo
-------------------------
Sostituisci assets/wallpaper.jpeg oppure modifica questa riga in style.css:

background-image: url("assets/wallpaper.jpeg");

Lo sfondo e' gestito via CSS, non con un tag <img> nel body.

Meta tag SEO/social
-------------------
I meta tag sono nel <head> di index.html.
Sono presenti tag SEO base, Open Graph e Twitter Card.

Se cambi dominio pubblico, aggiorna questi campi:
- canonical
- og:url
- og:image
- twitter:url
- twitter:image

Nota importante: per le anteprime social l'immagine deve avere un URL assoluto online.

Problemi noti e miglioramenti consigliati
-----------------------------------------
- I link sono separati con <br>; sarebbe meglio usare gap su .link-wrapper.
- I link con target="_blank" non hanno ancora rel="noopener noreferrer".
- Facebook e TikTok usano ancora lo stile base, senza classe specifica.
- Non ci sono test automatici o strumenti di lint/format.

Prima di continuare
-------------------
Leggi PROJECT_CONTEXT.md per il contesto completo.
Mantieni il progetto semplice: HTML, CSS, asset locali e nessuna dipendenza inutile.
