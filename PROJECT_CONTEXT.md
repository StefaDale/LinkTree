# PROJECT_CONTEXT.md

Documento di contesto del progetto statico `linktree`.

Questo file serve a permettere a una nuova IA o a un nuovo sviluppatore di comprendere rapidamente lo stato del progetto, le scelte fatte, i problemi noti e i prossimi passi consigliati.

## Panoramica Del Progetto

### Nome del progetto

`linktree`

### Scopo principale

Il progetto realizza una pagina personale in stile Linktree: una singola pagina web con una raccolta di link esterni importanti, presentati come grandi bottoni centrati e riconoscibili tramite colori e icone.

### Problema che risolve

Permette di raccogliere in un unico URL i collegamenti ai profili e alle risorse personali:

- Instagram
- Facebook
- Sito web personale
- GitHub
- Steam
- TikTok
- Server Discord

L'obiettivo pratico e' avere una pagina semplice da condividere, visivamente personalizzata e utilizzabile sia da desktop sia da mobile.

### Stato attuale dello sviluppo

Il progetto e' funzionante come pagina statica HTML/CSS. Non usa JavaScript, framework, build tool o dipendenze esterne.

Lo stato attuale include:

- struttura HTML completa della pagina;
- stylesheet principale;
- icone SVG per i servizi;
- immagine di sfondo;
- layout fullscreen tramite `min-height: 100vh`;
- bottoni centrati;
- colori personalizzati per alcuni servizi;
- bottoni semi-trasparenti in stato normale;
- hover con colori piu' pieni;
- comportamento responsive per schermi piccoli;
- swap dell'icona GitHub in hover.
- meta tag SEO/social nel `<head>`;
- documentazione estesa in italiano e inglese;
- README sintetici in italiano e inglese.

Non sono presenti file di configurazione, test automatici o script di avvio.

## Tecnologie Utilizzate

### Linguaggi

- HTML5
- CSS3

### Framework

Nessun framework utilizzato.

Il progetto e' volutamente semplice e statico: la pagina puo' essere aperta direttamente dal browser senza server locale.

### Librerie

Nessuna libreria JavaScript o CSS.

Le icone sono file locali nella cartella `assets`.

### Strumenti utilizzati

- Browser web per visualizzare la pagina.
- Git, presente tramite cartella `.git`.
- CSS moderno con nesting nativo, ad esempio:

```css
.linktree {
    >.link-wrapper a {
        &:hover {
            transform: scale(1.05);
        }
    }
}
```

Nota importante: il nesting CSS nativo funziona nei browser moderni, ma puo' essere meno compatibile con browser vecchi rispetto alla sintassi CSS classica non annidata.

## Struttura Delle Cartelle

### Albero completo delle directory

Stato osservato nella root `C:\Code\Web\linktree`:

```text
linktree/
|-- .git/
|-- assets/
|   |-- discord_icon.svg
|   |-- facebook_icon.svg
|   |-- github_icon-invertito.svg
|   |-- github_icon.svg
|   |-- instagram_icon.svg
|   |-- steam_icon.svg
|   |-- tiktok_icon.svg
|   |-- wallpaper.jpeg
|   `-- website_icon.svg
|-- index.html
|-- PROJECT_CONTEXT.md
|-- PROJECT_CONTEXT_EN.md
|-- README_EN.txt
|-- README_IT.txt
`-- style.css
```

### Descrizione dei file e delle cartelle

#### `.git/`

Repository Git locale. Il contenuto interno non e' parte del codice applicativo e non viene documentato nel dettaglio.

#### `assets/`

Contiene tutti gli asset visuali usati dalla pagina:

- `discord_icon.svg`: icona Discord.
- `facebook_icon.svg`: icona Facebook.
- `github_icon.svg`: icona GitHub scura, usata nello stato hover del bottone GitHub.
- `github_icon-invertito.svg`: icona GitHub chiara/invertita, usata nello stato normale del bottone GitHub su sfondo scuro.
- `instagram_icon.svg`: icona Instagram.
- `steam_icon.svg`: icona Steam.
- `tiktok_icon.svg`: icona TikTok.
- `website_icon.svg`: icona generica per il sito web personale.
- `wallpaper.jpeg`: immagine usata come sfondo della pagina.

I nomi degli asset sono stati resi piu' ordinati e descrittivi rispetto a nomi generati automaticamente o provenienti da download, per esempio `wallpaper.jpeg` invece di un nome lungo da WhatsApp.

#### `index.html`

File principale della pagina. Contiene:

- dichiarazione HTML5;
- lingua impostata su italiano con `lang="it"`;
- meta viewport per il responsive;
- meta tag SEO base;
- meta tag Open Graph per anteprime social;
- meta tag Twitter Card;
- link canonical;
- collegamento al CSS `style.css`;
- contenitore principale `.linktree`;
- titolo;
- testo introduttivo;
- elenco dei link;
- immagini SVG associate ai link.

#### `style.css`

File unico di stile. Contiene:

- reset minimo del body;
- stile del titolo;
- stile del contenitore `.linktree`;
- immagine di sfondo;
- stile base dei bottoni;
- layout flex verticale dei link;
- dimensione delle icone;
- colori specifici per Instagram, GitHub, Discord, Steam e sito web;
- logica hover;
- media query mobile a `max-width: 600px`.

#### `PROJECT_CONTEXT.md`

Questo documento. Deve essere aggiornato quando cambiano struttura, obiettivi, convenzioni o stato del progetto.

#### `PROJECT_CONTEXT_EN.md`

Traduzione inglese del documento di contesto. Serve a permettere anche a una IA o a uno sviluppatore non italofono di riprendere il progetto senza spiegazioni aggiuntive.

#### `README_IT.txt`

README sintetico in italiano con descrizione, struttura, istruzioni di avvio e note di sviluppo.

#### `README_EN.txt`

README sintetico in inglese con le stesse informazioni del README italiano.

## Funzionalita Implementate

### Meta tag SEO e social preview

Implementati nel `<head>` di `index.html`.

La pagina include meta tag per:

- titolo SEO;
- descrizione;
- parole chiave;
- autore;
- indicizzazione tramite `robots`;
- colore tema;
- URL canonical;
- Open Graph per anteprime su piattaforme come WhatsApp, Discord, Facebook e LinkedIn;
- Twitter Card con immagine grande.

Esempio:

```html
<title>Linktree | Nome Profilo</title>
<meta name="description" content="Tutti i miei link principali.">
<link rel="canonical" href="https://stefanocatalin.netlify.app/">
<meta property="og:image" content="https://stefanocatalin.netlify.app/assets/wallpaper.jpeg">
<meta name="twitter:card" content="summary_large_image">
```

Scelta importante: per le immagini social viene usato un URL assoluto online, non un percorso relativo. Le piattaforme social devono poter raggiungere direttamente l'immagine pubblica.

### Pagina personale con link esterni

Implementata in `index.html`.

La pagina contiene una lista di link cliccabili:

```html
<div class="link-wrapper">
    <a class="instagram" href="https://instagram.com/ste_catalin_" target="_blank">
        Instagram <img src="assets/instagram_icon.svg" alt="">
    </a>
    ...
</div>
```

Ogni link punta a una piattaforma esterna e usa `target="_blank"` per aprire la destinazione in una nuova scheda.

File coinvolti:

- `index.html`
- `style.css`
- `assets/*.svg`

### Layout fullscreen

Implementato in `style.css`.

Il body e il contenitore principale usano `min-height: 100vh`:

```css
body {
    margin: 0;
    min-height: 100vh;
}

.linktree {
    min-height: 100vh;
}
```

Questo fa in modo che la pagina occupi almeno tutta l'altezza dello schermo.

### Sfondo immagine

Implementato in `style.css` usando `background-image` su `.linktree`:

```css
.linktree {
    background-image: url("assets/wallpaper.jpeg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
```

Questa scelta sostituisce il precedente sfondo grigio. L'immagine e' applicata come sfondo CSS, non come tag `<img>` nel body. Questo evita che l'immagine occupi spazio nel layout o rompa la struttura della pagina.

### Bottoni centrati e con larghezza controllata

Implementato con `.link-wrapper` e gli anchor dentro `.linktree`.

```css
.linktree {
    >.link-wrapper a {
        display: flex;
        width: 50%;
    }

    .link-wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
}
```

La larghezza desktop dei bottoni e' `50%`. Il contenitore `.link-wrapper` usa flexbox in colonna e `align-items: center`, quindi i bottoni restano centrati anche quando non occupano tutta la larghezza.

### Bottoni semi-trasparenti

Implementato con colori `rgba()` e colori esadecimali con alpha.

Esempio:

```css
.linktree > .link-wrapper a.instagram {
    background-color: rgba(226, 0, 226, 0.65);
}
```

Il valore finale `0.65` indica l'opacita' del colore: `0` e' completamente trasparente, `1` e' completamente opaco.

### Hover dei bottoni

Implementato nella regola generale dei link e nelle regole specifiche dei servizi.

Regola generale:

```css
.linktree {
    >.link-wrapper a {
        transition: 100ms ease-in-out;

        &:hover {
            transform: scale(1.05);
            background-color: #ffffff;
        }
    }
}
```

Le classi specifiche possono sovrascrivere colore e testo:

```css
.linktree > .link-wrapper a.github {
    background-color: rgba(0, 0, 0, 0.295);
    color: white;

    &:hover {
        background-color: rgb(255, 255, 255);
        color: black;
    }
}
```

### Icone dei servizi

Le icone sono immagini SVG locali caricate tramite tag `<img>`.

Regola dimensioni:

```css
a img {
    width: 40px;
    height: 40px;
}
```

Su mobile le dimensioni vengono ridotte:

```css
.linktree > .link-wrapper a img {
    width: 22px;
    height: 22px;
}
```

### Swap icona GitHub in hover

Il bottone GitHub usa due immagini:

```html
<a class="github" href="https://github.com/StefaDale" target="_blank">
    GitHub
    <img class="icon-hover" src="assets/github_icon.svg" alt="">
    <img class="icon-normal" src="assets/github_icon-invertito.svg" alt="">
</a>
```

In stato normale:

- il bottone e' scuro;
- si vede `github_icon-invertito.svg`, cioe' l'icona chiara.

In hover:

- il bottone diventa bianco;
- viene nascosta l'icona chiara;
- viene mostrata l'icona scura.

CSS:

```css
.linktree > .link-wrapper a.github {
    .icon-hover {
        display: none;
    }

    &:hover {
        .icon-normal {
            display: none;
        }

        .icon-hover {
            display: inline;
        }
    }
}
```

Nota: i nomi `icon-normal` e `icon-hover` sono classi CSS, non nomi obbligatori dei file. Servono solo al CSS per sapere quale immagine nascondere o mostrare.

### Responsive mobile

Implementato con media query:

```css
@media (max-width: 600px) {
    .linktree {
        width: 100%;
        min-height: 100vh;
        border-radius: 0;
        padding: 2rem 1rem;
    }

    .linktree > .link-wrapper a {
        font-size: 26px;
        width: 100%;
    }

    .linktree > .link-wrapper a img {
        width: 22px;
        height: 22px;
    }
}
```

Su schermi piccoli:

- il contenitore occupa tutta la larghezza;
- il bordo arrotondato viene rimosso;
- il padding viene ridotto;
- i bottoni passano da `width: 50%` a `width: 100%`;
- testo e icone vengono ridotti.

## Architettura Del Progetto

### Organizzazione generale del codice

Il progetto ha architettura statica:

- `index.html` definisce contenuto e struttura;
- `style.css` definisce presentazione, layout e responsive;
- `assets/` contiene risorse visuali locali.

Non esiste separazione in componenti JavaScript, moduli, route o template. Tutto e' nella singola pagina.

### Flusso dei dati

Non c'e' flusso dati dinamico.

Il flusso reale e':

1. Il browser apre `index.html`.
2. `index.html` carica `style.css`.
3. `style.css` carica `assets/wallpaper.jpeg` come sfondo.
4. `index.html` carica le icone SVG dai percorsi in `assets/`.
5. L'utente clicca un link.
6. Il browser apre il sito esterno in una nuova scheda.

### Relazioni tra componenti, moduli e pagine

La pagina ha questa gerarchia:

```text
body
└── .linktree
    ├── .title
    ├── p
    └── .link-wrapper
        ├── a.instagram
        ├── a
        ├── a.sito
        ├── a.github
        ├── a.steam
        ├── a
        └── a.discord
```

Le classi dei link hanno ruoli diversi:

- `.instagram`: stile specifico Instagram.
- `.sito`: stile specifico del link al sito web personale.
- `.github`: stile specifico GitHub e swap icona hover.
- `.steam`: stile specifico Steam.
- `.discord`: stile specifico Discord.

Facebook e TikTok al momento usano lo stile base del bottone, senza classe CSS dedicata.

## Stato Attuale

### Completato

- Pagina HTML base.
- Collegamento CSS.
- Asset locali per icone e sfondo.
- Link principali inseriti.
- Layout fullscreen.
- Bottoni centrati.
- Larghezza desktop dei bottoni impostata a `50%`.
- Responsive mobile a `600px`.
- Sfondo immagine con `background-image`.
- Colori semi-trasparenti per diversi bottoni.
- Hover con cambio colore e scala.
- Icona GitHub che cambia in hover.
- Nomi asset piu' ordinati e coerenti.
- Meta tag SEO, Open Graph e Twitter Card nel `<head>`.
- Documentazione estesa del progetto in italiano.
- Traduzione inglese del contesto.
- README sintetico in italiano e inglese.

### In lavorazione

Non risultano feature in lavorazione nel codice, ma la conversazione recente riguarda:

- miglioramento della leggibilita' dei bottoni sopra lo sfondo;
- gestione della trasparenza dei bottoni;
- personalizzazione degli hover per ogni servizio.

### Non ancora implementato

- favicon.
- miglioramenti accessibilita' sugli `alt`.
- `rel="noopener noreferrer"` sui link con `target="_blank"`.
- layout senza `<br>` tra i link.
- classi specifiche per Facebook e TikTok.
- variabili CSS per colori e misure ripetute.
- test o validazione automatica HTML/CSS.
- deploy documentato.

## Problemi Noti

### Uso di `<br>` per spaziare i bottoni

In `index.html` i link sono separati da `<br>`.

Esempio:

```html
<a class="instagram" ...>...</a>
<br>
<a ...>...</a>
```

Funziona, ma non e' la soluzione piu' pulita per il layout. Sarebbe meglio usare `gap` su `.link-wrapper`:

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
}
```

Poi si potrebbero rimuovere i `<br>` dall'HTML.

### Accessibilita' delle icone

Tutte le icone hanno `alt=""`.

Questo e' accettabile se le icone sono puramente decorative e il testo del link e' gia' presente. Se un'icona comunica informazione aggiuntiva, dovrebbe avere un `alt` descrittivo.

### Link esterni senza `rel`

I link usano `target="_blank"`, ma non hanno:

```html
rel="noopener noreferrer"
```

Consigliato aggiungerlo per motivi di sicurezza e privacy quando si aprono link esterni in nuove schede.

### CSS nesting moderno

Il file `style.css` usa nesting nativo:

```css
.linktree {
    >.link-wrapper a {
        &:hover {
            ...
        }
    }
}
```

Questa scelta rende il codice piu' compatto, ma puo' creare problemi in browser non aggiornati. Per massima compatibilita', si puo' riscrivere in CSS classico.

### Nomi classi GitHub potenzialmente confusi

Nel bottone GitHub:

```html
<img class="icon-hover" src="assets/github_icon.svg" alt="">
<img class="icon-normal" src="assets/github_icon-invertito.svg" alt="">
```

Il significato delle classi e':

- `.icon-normal`: immagine visibile normalmente;
- `.icon-hover`: immagine visibile solo durante hover.

Questo e' corretto, ma il nome del file `github_icon-invertito.svg` potrebbe far sembrare il contrario a chi legge velocemente. La logica e' stata scelta perche' lo sfondo normale del bottone GitHub e' scuro.

### Hover su mobile

Gli hover funzionano bene su desktop, ma su dispositivi touch non sono sempre percepibili o utili. Non e' un bug grave, ma e' una limitazione naturale dell'interazione touch.

### Contrasto testo/sfondo

La pagina usa un'immagine come sfondo. Alcuni testi potrebbero risultare poco leggibili in base alle zone chiare/scure del wallpaper.

Contromisure gia' presenti:

- bottoni semi-trasparenti;
- testo del paragrafo in `whitesmoke`;
- titolo magenta.

Possibile miglioramento:

- aggiungere un overlay scuro o chiaro sul background;
- aumentare opacita' dei bottoni;
- aggiungere text-shadow al titolo e al paragrafo.

### Mancanza di configurazione progetto

Non ci sono:

- `package.json`;
- build step;
- lint;
- formatter;
- test;
- file di deploy.

Questo non impedisce il funzionamento, ma rende il progetto meno automatizzato. La documentazione ora esiste tramite `PROJECT_CONTEXT.md`, `PROJECT_CONTEXT_EN.md`, `README_IT.txt` e `README_EN.txt`.

## Decisioni Progettuali

### Pagina statica senza framework

Scelta: usare solo HTML e CSS.

Motivo:

- il progetto e' piccolo;
- non serve stato dinamico;
- non serve routing;
- non serve build;
- e' facile da capire per chi sta imparando;
- il file si puo' aprire direttamente nel browser.

### Sfondo gestito in CSS

Scelta: usare `background-image` su `.linktree` invece di un tag `<img>` nel `body`.

Motivo:

- un'immagine nel body entra nel flusso della pagina e puo' rompere il layout;
- `background-size: cover` permette di coprire l'intero viewport;
- `background-position: center` mantiene la foto centrata;
- il contenuto resta separato dalla presentazione.

### Bottoni larghi il 50% su desktop

Scelta: impostare:

```css
width: 50%;
```

sui link in desktop.

Motivo:

- i bottoni a tutto schermo erano troppo lunghi su PC;
- una larghezza percentuale mantiene una certa adattabilita';
- il contenitore flex li centra automaticamente.

### Bottoni full width su mobile

Scelta: nella media query mobile i bottoni diventano:

```css
width: 100%;
```

Motivo:

- su schermi piccoli i bottoni devono essere facilmente cliccabili;
- usare il 50% su mobile renderebbe i bottoni troppo stretti;
- il padding laterale della pagina mantiene comunque un margine visivo.

### Colori specifici per servizio

Scelta: usare classi come `.instagram`, `.github`, `.discord`, `.steam`, `.sito`.

Motivo:

- ogni servizio puo' avere una sua identita' visiva;
- la regola base dei bottoni rimane comune;
- le differenze sono isolate nelle classi specifiche.

### Trasparenza tramite `rgba`

Scelta: usare `rgba(..., 0.65)` o valori simili.

Motivo:

- permette di vedere lo sfondo;
- mantiene i bottoni leggibili;
- l'hover puo' diventare piu' opaco per dare feedback visivo.

### Swap icona GitHub con due immagini

Scelta: inserire due `<img>` e nasconderne una via CSS.

Motivo:

- semplice da capire;
- non richiede JavaScript;
- evita filtri CSS complessi;
- funziona bene quando esistono gia' due versioni dell'icona.

### Meta tag social con URL assoluti

Scelta: usare URL assoluti per `canonical`, `og:url`, `og:image`, `twitter:url` e `twitter:image`.

Motivo:

- i crawler social non leggono il progetto dal disco locale;
- le anteprime condivise hanno bisogno di risorse pubbliche raggiungibili online;
- un URL canonical aiuta i motori di ricerca a capire quale versione della pagina indicizzare.

Nota: se il sito viene pubblicato su un dominio diverso da `https://stefanocatalin.netlify.app/`, gli URL nei meta tag vanno aggiornati.

## Roadmap

### Priorita alta

1. Sostituire i `<br>` con `gap` su `.link-wrapper`.
2. Aggiungere `rel="noopener noreferrer"` ai link esterni.
3. Verificare contrasto e leggibilita' sopra `wallpaper.jpeg`.
4. Valutare se convertire il CSS annidato in CSS classico per compatibilita'.

### Priorita media

1. Aggiungere classi specifiche per Facebook e TikTok se si vuole personalizzare anche quei bottoni.
2. Introdurre variabili CSS per colori, opacita', dimensioni e breakpoint.
3. Aggiungere favicon.
4. Mantenere aggiornati `PROJECT_CONTEXT.md`, `PROJECT_CONTEXT_EN.md`, `README_IT.txt` e `README_EN.txt` quando cambia il progetto.

### Priorita bassa

1. Aggiungere animazioni piu' raffinate.
2. Migliorare la tipografia.
3. Ottimizzare o comprimere `wallpaper.jpeg`.
4. Aggiungere tema alternativo o modalita' chiara/scura.
5. Valutare deploy su Netlify, GitHub Pages o altro hosting statico.

## Istruzioni Per Continuare Il Progetto

### Come avviare il progetto

Non serve installare dipendenze.

Metodo piu' semplice:

1. Aprire `index.html` nel browser.
2. Modificare `index.html` o `style.css`.
3. Aggiornare la pagina nel browser.

Metodo alternativo:

- usare un server statico locale, se disponibile, ma non e' obbligatorio.

### Come effettuare modifiche

#### Aggiungere un nuovo link

In `index.html`, aggiungere un nuovo `<a>` dentro `.link-wrapper`.

Esempio:

```html
<a class="nuovo-servizio" href="https://example.com" target="_blank" rel="noopener noreferrer">
    Nuovo Servizio <img src="assets/nuovo-servizio_icon.svg" alt="">
</a>
```

Poi aggiungere stile in `style.css` se serve:

```css
.linktree > .link-wrapper a.nuovo-servizio {
    background-color: rgba(100, 100, 255, 0.65);

    &:hover {
        background-color: rgb(100, 100, 255);
    }
}
```

#### Cambiare larghezza bottoni desktop

Modificare:

```css
.linktree {
    >.link-wrapper a {
        width: 50%;
    }
}
```

Esempi:

- `width: 40%;` per bottoni piu' corti;
- `width: 60%;` per bottoni piu' lunghi;
- `width: 80%;` per bottoni quasi full width.

#### Cambiare larghezza bottoni mobile

Modificare nella media query:

```css
@media (max-width: 600px) {
    .linktree > .link-wrapper a {
        width: 100%;
    }
}
```

#### Cambiare immagine di sfondo

1. Inserire la nuova immagine in `assets/`.
2. Aggiornare in `style.css`:

```css
background-image: url("assets/nuovo-sfondo.jpeg");
```

#### Rendere piu' o meno trasparenti i bottoni

Modificare l'ultimo valore di `rgba`.

Esempio:

```css
background-color: rgba(226, 0, 226, 0.65);
```

- `0.4` = piu' trasparente;
- `0.65` = semi-trasparente;
- `0.9` = quasi pieno;
- `1` = opaco.

### Cosa deve sapere una nuova IA prima di intervenire

- Non introdurre framework o JavaScript se non richiesto: il progetto e' pensato per restare semplice.
- Prima di modificare il layout, controllare l'effetto sia su desktop sia sotto `600px`.
- I bottoni su desktop sono volutamente al `50%`.
- Su mobile devono restare al `100%`.
- Lo sfondo va gestito in CSS, non con un `<img>` libero dentro il body.
- Le icone devono stare in `assets/`.
- Per icone con due versioni, seguire il pattern GitHub con due `<img>` e classi dedicate.
- Le regole specifiche dei servizi devono venire dopo la regola generale dei bottoni, cosi' possono sovrascriverla.

## Cronologia Dello Sviluppo

### 1. Struttura iniziale

Il progetto nasce come pagina HTML statica con:

- titolo `Linktree`;
- testo `I miei link:`;
- link a social e piattaforme;
- stile CSS base;
- sfondo grigio;
- bottoni grandi.

### 2. Problema responsive iniziale

Durante i test su dispositivi diversi, il layout cambiava in modo indesiderato: su alcuni viewport non occupava bene lo schermo o i bottoni risultavano troppo stretti/spostati.

Soluzione discussa:

- usare `min-height: 100vh`;
- evitare larghezze mobili troppo strette sui bottoni;
- distinguere comportamento desktop e mobile.

### 3. Controllo larghezza bottoni

E' stato chiarito che:

- `font-size` cambia la dimensione del testo;
- `padding` cambia lo spazio interno;
- `width` cambia la lunghezza/larghezza del bottone.

E' stato introdotto il pattern:

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
}
```

per centrare bottoni piu' corti del contenitore.

### 4. Organizzazione CSS annidata

E' stata adottata una struttura CSS con regole annidate dentro `.linktree`, ad esempio:

```css
.linktree {
    p {
        font-size: 30px;
        font-weight: bold;
    }
}
```

Questa sintassi equivale a:

```css
.linktree p {
    font-size: 30px;
    font-weight: bold;
}
```

### 5. Correzione path icona Instagram

L'icona Instagram inizialmente non appariva per un problema di percorso.

Il path corretto e' nella cartella `assets`, per esempio:

```html
<img src="assets/instagram_icon.svg" alt="">
```

### 6. Specificita' delle classi servizio

Quando e' stata aggiunta una classe come `.instagram`, lo stile non veniva applicato perche' la regola generale:

```css
.linktree > .link-wrapper a
```

era piu' specifica di:

```css
.instagram
```

Soluzione:

```css
.linktree > .link-wrapper a.instagram {
    background-color: ...;
}
```

### 7. Gestione icona GitHub in hover

Il bottone GitHub aveva problema di leggibilita' dell'icona in base allo sfondo.

Soluzione:

- usare icona invertita su sfondo scuro;
- usare icona normale su sfondo bianco in hover;
- inserire due immagini;
- controllare visibilita' con CSS.

### 8. Sostituzione sfondo grigio con immagine

Inizialmente era stata aggiunta un'immagine come tag `<img>` dentro il body. Questo rompeva il layout perche' l'immagine diventava parte del flusso HTML.

Soluzione:

- rimuovere il tag `<img>` dal body;
- usare `background-image` su `.linktree`;
- rinominare l'immagine in `wallpaper.jpeg`;
- usare `background-size: cover`.

### 9. Bottoni semi-trasparenti

Per rendere visibile lo sfondo senza perdere leggibilita', i bottoni sono stati resi semi-trasparenti tramite `rgba`.

Gli hover rendono i colori piu' pieni o comunque piu' evidenti.

### 10. Inserimento meta tag SEO/social

Sono stati aggiunti nel `<head>` di `index.html` i principali meta tag per SEO e anteprime social:

- titolo;
- description;
- keywords;
- author;
- robots;
- theme-color;
- canonical;
- Open Graph;
- Twitter Card.

La preview social usa `wallpaper.jpeg` tramite URL assoluto.

### 11. Documentazione di progetto

E' stato creato `PROJECT_CONTEXT.md` come documento esteso per IA e sviluppatori. Successivamente sono stati previsti e aggiunti anche:

- `PROJECT_CONTEXT_EN.md`, traduzione inglese del contesto;
- `README_IT.txt`, README sintetico italiano;
- `README_EN.txt`, README sintetico inglese.

## Contesto Per IA

### Obiettivo generale del progetto

Creare una pagina personale in stile Linktree, bella ma semplice, con link social/personali, icone riconoscibili, sfondo personalizzato e buon comportamento su desktop e mobile.

### Filosofia e stile del codice

Il codice deve restare:

- semplice;
- leggibile;
- adatto a chi sta imparando HTML/CSS;
- statico;
- senza dipendenze inutili;
- facile da modificare manualmente.

Evitare astrazioni premature, framework o JavaScript se non richiesti.

### Convenzioni di naming

Asset:

- usare nomi minuscoli o descrittivi;
- preferire suffissi come `_icon`;
- usare `-invertito` quando l'asset e' una variante visiva invertita;
- evitare nomi lunghi generati automaticamente, come nomi provenienti da WhatsApp.

Esempi attuali:

```text
instagram_icon.svg
github_icon.svg
github_icon-invertito.svg
wallpaper.jpeg
```

Classi CSS:

- `.linktree`: contenitore principale;
- `.title`: titolo;
- `.link-wrapper`: contenitore flex dei bottoni;
- classi servizio sui link: `.instagram`, `.github`, `.steam`, `.discord`, `.sito`;
- classi stato icona: `.icon-normal`, `.icon-hover`.

### Pattern utilizzati

#### Regola base + override specifici

Tutti i bottoni condividono una regola base:

```css
.linktree {
    >.link-wrapper a {
        display: flex;
        width: 50%;
        ...
    }
}
```

Poi alcuni servizi sovrascrivono colore e hover:

```css
.linktree > .link-wrapper a.discord {
    background-color: rgba(88, 101, 242, 0.65);
}
```

#### Flexbox per centrare i link

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
}
```

#### Media query mobile

```css
@media (max-width: 600px) {
    ...
}
```

#### Due immagini per stati visuali diversi

Pattern usato su GitHub:

```html
<img class="icon-hover" src="assets/github_icon.svg" alt="">
<img class="icon-normal" src="assets/github_icon-invertito.svg" alt="">
```

### Stato preciso dell'ultima versione disponibile

Alla creazione di questo documento:

- `index.html` contiene 7 link;
- il `<head>` contiene meta tag SEO, Open Graph e Twitter Card;
- `style.css` contiene tutto lo stile;
- `assets/` contiene 9 asset;
- `wallpaper.jpeg` e' lo sfondo effettivo;
- i bottoni desktop sono larghi `50%`;
- i bottoni mobile sono larghi `100%`;
- il titolo ha `font-size: 50px` e colore magenta;
- il paragrafo ha `font-size: 30px`, grassetto e colore `whitesmoke`;
- GitHub usa icona invertita normalmente e icona normale in hover;
- il progetto non ha dipendenze, script o test;
- la documentazione comprende contesto esteso e README bilingue.

### Ultimo lavoro svolto

L'ultimo ciclo di lavoro ha riguardato:

- inserimento dei meta tag SEO/social nel `<head>` di `index.html`;
- aggiornamento del contesto di progetto;
- creazione della documentazione sintetica bilingue;
- traduzione inglese del documento di contesto.

### Prossimo passo consigliato

Il prossimo intervento consigliato e' sostituire i `<br>` tra i link con `gap` su `.link-wrapper`.

Questo renderebbe l'HTML piu' pulito e il layout piu' controllabile.

Esempio consigliato:

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
}
```

Poi rimuovere i `<br>` tra i bottoni in `index.html`.

Subito dopo, aggiungere `rel="noopener noreferrer"` a tutti i link esterni con `target="_blank"`.
