# PROJECT_CONTEXT_EN.md

English project context document for the static `linktree` project.

This file is the English counterpart of `PROJECT_CONTEXT.md`. Its goal is to let another AI or developer understand the project quickly, including its current state, technical choices, known limitations, and recommended next steps.

## Project Overview

### Project name

`linktree`

### Main purpose

The project is a personal Linktree-style web page: a single static page containing important external links, shown as large centered buttons with recognizable colors and icons.

### Problem it solves

It collects the main personal/social links in a single shareable URL:

- Instagram
- Facebook
- Personal website
- GitHub
- Steam
- TikTok
- Discord server

The practical goal is to have a simple, visual, personal landing page that works on both desktop and mobile.

### Current development state

The project is functional as a static HTML/CSS page. It does not use JavaScript, frameworks, build tools, or external dependencies.

The current state includes:

- complete HTML page structure;
- main stylesheet;
- SVG icons for services;
- background image;
- fullscreen layout using `min-height: 100vh`;
- centered buttons;
- custom colors for some services;
- semi-transparent buttons in the normal state;
- more solid hover states;
- responsive behavior for small screens;
- GitHub icon swap on hover;
- SEO/social meta tags in the `<head>`;
- extended documentation in Italian and English;
- short README files in Italian and English.

There are no project configuration files, automated tests, or startup scripts.

## Technologies Used

### Languages

- HTML5
- CSS3

### Frameworks

No framework is used.

The project is intentionally simple and static. The page can be opened directly in a browser without a local server.

### Libraries

No JavaScript or CSS library is used.

Icons are local files stored in the `assets` folder.

### Tools

- Web browser for previewing the page.
- Git, present through the `.git` folder.
- Modern native CSS nesting, for example:

```css
.linktree {
    >.link-wrapper a {
        &:hover {
            transform: scale(1.05);
        }
    }
}
```

Important note: native CSS nesting works in modern browsers, but it may be less compatible with old browsers than classic non-nested CSS.

## Folder Structure

### Full directory tree

Observed state in root `C:\Code\Web\linktree`:

```text
linktree/
|-- .git/
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
|-- PROJECT_CONTEXT.md
|-- PROJECT_CONTEXT_EN.md
|-- README.txt
|-- README_IT.txt
`-- style.css
```

### Purpose of important folders and files

#### `.git/`

Local Git repository. Its internal content is not part of the application code and is not documented in detail here.

#### `assets/`

Contains all visual assets used by the page:

- `discord_icon.svg`: Discord icon.
- `facebook_icon.svg`: Facebook icon.
- `favicon.svg`: vector favicon for the page, designed as a small tree with connected nodes.
- `github_icon.svg`: dark GitHub icon, used in the GitHub button hover state.
- `github_icon-invertito.svg`: light/inverted GitHub icon, used in the normal GitHub button state on a dark background.
- `instagram_icon.svg`: Instagram icon.
- `steam_icon.svg`: Steam icon.
- `tiktok_icon.svg`: TikTok icon.
- `website_icon.svg`: generic website icon for the personal website link.
- `wallpaper.jpeg`: image used as the page background.

Asset names were normalized to be more readable and descriptive than generated or downloaded names. For example, `wallpaper.jpeg` is clearer than a long filename exported from WhatsApp.

#### `index.html`

Main page file. It contains:

- HTML5 declaration;
- Italian language setting with `lang="it"`;
- responsive viewport meta tag;
- basic SEO meta tags;
- Open Graph meta tags for social previews;
- Twitter Card meta tags;
- canonical link;
- stylesheet link to `style.css`;
- main `.linktree` container;
- title;
- intro text;
- list of links;
- SVG images connected to links.

#### `style.css`

Single stylesheet. It contains:

- minimal body reset;
- title styling;
- `.linktree` container styling;
- background image;
- base button styling;
- vertical flex layout for links;
- icon sizing;
- specific colors for Instagram, GitHub, Discord, Steam, and website buttons;
- hover logic;
- mobile media query at `max-width: 600px`.

#### `PROJECT_CONTEXT.md`

Detailed Italian project context. It should be updated when structure, goals, conventions, or project state change.

#### `PROJECT_CONTEXT_EN.md`

English translation of the project context. It allows a non-Italian-speaking AI or developer to continue the project without extra explanation.

#### `README_IT.txt`

Short Italian README with description, structure, run instructions, and development notes.

#### `README.txt`

Short English README with the same practical information as the Italian README.

## Implemented Features

### SEO and social preview meta tags

Implemented in the `<head>` of `index.html`.

The page includes meta tags for:

- SEO title;
- description;
- keywords;
- author;
- indexing through `robots`;
- theme color;
- canonical URL;
- Open Graph previews for platforms such as WhatsApp, Discord, Facebook, and LinkedIn;
- Twitter Card with a large image.

Example:

```html
<title>Linktree | Profile Name</title>
<meta name="description" content="Tutti i miei link principali.">
<link rel="canonical" href="https://stefanocatalinlinktree.netlify.app/">
<meta property="og:image" content="https://stefanocatalinlinktree.netlify.app/assets/wallpaper.jpeg">
<meta name="twitter:card" content="summary_large_image">
```

Important choice: social preview images use an absolute online URL, not a relative local path. Social platforms need to be able to fetch the public image directly.

### Custom favicon

Implemented with `assets/favicon.svg` and linked in the `<head>` of `index.html`.

```html
<link rel="icon" type="image/svg+xml" href="assets/favicon.svg">
```

The favicon is a lightweight SVG. It represents a small tree with branches and connected nodes, so it suggests both the "tree" idea and the idea of links.

### Personal page with external links

Implemented in `index.html`.

The page contains a clickable link list:

```html
<div class="link-wrapper">
    <a class="instagram" href="https://instagram.com/ste_catalin_" target="_blank">
        Instagram <img src="assets/instagram_icon.svg" alt="">
    </a>
    ...
</div>
```

Each link points to an external platform and uses `target="_blank"` to open the destination in a new browser tab.

Involved files:

- `index.html`
- `style.css`
- `assets/*.svg`

### Fullscreen layout

Implemented in `style.css`.

The body and main container use `min-height: 100vh`:

```css
body {
    margin: 0;
    min-height: 100vh;
}

.linktree {
    min-height: 100vh;
}
```

This makes the page cover at least the full viewport height.

### Background image

Implemented in `style.css` with `background-image` on `.linktree`:

```css
.linktree {
    background-image: url("assets/wallpaper.jpeg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
```

This replaced the previous gray background. The image is applied as a CSS background, not as an `<img>` tag in the body. This prevents the image from taking layout space or breaking the page flow.

### Centered buttons with controlled width

Implemented with `.link-wrapper` and the anchors inside `.linktree`.

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

Desktop button width is `50%`. The `.link-wrapper` container uses a vertical flex layout and `align-items: center`, so buttons stay centered even when they do not occupy the full page width.

### Semi-transparent buttons

Implemented with `rgba()` colors and hexadecimal colors with alpha.

Example:

```css
.linktree > .link-wrapper a.instagram {
    background-color: rgba(226, 0, 226, 0.65);
}
```

The final value `0.65` controls opacity: `0` is fully transparent, and `1` is fully opaque.

### Button hover states

Implemented in the general link rule and service-specific rules.

General rule:

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

Specific classes can override color and text:

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

### Service icons

Icons are local SVG files loaded through `<img>` tags.

Base icon size:

```css
a img {
    width: 40px;
    height: 40px;
}
```

On mobile, icon size is reduced:

```css
.linktree > .link-wrapper a img {
    width: 22px;
    height: 22px;
}
```

### GitHub icon swap on hover

The GitHub button uses two images:

```html
<a class="github" href="https://github.com/StefaDale" target="_blank">
    GitHub
    <img class="icon-hover" src="assets/github_icon.svg" alt="">
    <img class="icon-normal" src="assets/github_icon-invertito.svg" alt="">
</a>
```

In the normal state:

- the button is dark;
- `github_icon-invertito.svg`, the light icon, is visible.

On hover:

- the button becomes white;
- the light icon is hidden;
- the dark icon is shown.

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

Note: `icon-normal` and `icon-hover` are CSS class names, not required filenames. They only tell CSS which image to hide or show.

### Mobile responsiveness

Implemented with a media query:

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

On small screens:

- the container occupies the full width;
- border radius is removed;
- padding is reduced;
- buttons move from `width: 50%` to `width: 100%`;
- text and icons become smaller.

## Project Architecture

### General code organization

The project has a static architecture:

- `index.html` defines content and structure;
- `style.css` defines presentation, layout, and responsive behavior;
- `assets/` stores local visual resources.

There are no JavaScript components, modules, routes, or templates. Everything is in one page.

### Data flow

There is no dynamic data flow.

The actual flow is:

1. The browser opens `index.html`.
2. `index.html` loads `style.css`.
3. `style.css` loads `assets/wallpaper.jpeg` as the background.
4. `index.html` loads SVG icons from `assets/`.
5. The user clicks a link.
6. The browser opens the external website in a new tab.

### Relationships between components, modules, and pages

The page hierarchy is:

```text
body
`-- .linktree
    |-- .title
    |-- p
    `-- .link-wrapper
        |-- a.instagram
        |-- a
        |-- a.sito
        |-- a.github
        |-- a.steam
        |-- a
        `-- a.discord
```

Link classes have different roles:

- `.instagram`: Instagram-specific style.
- `.sito`: personal website link style.
- `.github`: GitHub-specific style and hover icon swap.
- `.steam`: Steam-specific style.
- `.discord`: Discord-specific style.

Facebook and TikTok currently use the base button style and do not have dedicated CSS classes.

## Current State

### Completed

- Basic HTML page.
- CSS connection.
- Local assets for icons and background.
- Main links inserted.
- Fullscreen layout.
- Centered buttons.
- Desktop button width set to `50%`.
- Mobile responsive behavior at `600px`.
- Background image through `background-image`.
- Semi-transparent colors for several buttons.
- Hover color and scale change.
- GitHub icon changes on hover.
- Asset names are more organized and consistent.
- SEO, Open Graph, and Twitter Card meta tags in the `<head>`.
- Custom SVG favicon.
- Extended Italian project documentation.
- English translation of the project context.
- Short README in Italian and English.

### In progress

There are no active features in progress in the code.

Recent discussion and work focused on:

- improving readability over the background image;
- button transparency;
- service-specific hover customization;
- SEO/social metadata;
- bilingual documentation.

### Not implemented yet

- Favicon.
- Accessibility improvements for `alt` attributes.
- `rel="noopener noreferrer"` on links using `target="_blank"`.
- Layout without `<br>` between links.
- Dedicated CSS classes for Facebook and TikTok.
- CSS variables for repeated colors and sizes.
- Automated tests or HTML/CSS validation.
- Documented deployment workflow.

## Known Issues

### `<br>` is used to space buttons

In `index.html`, links are separated with `<br>`.

Example:

```html
<a class="instagram" ...>...</a>
<br>
<a ...>...</a>
```

This works, but it is not the cleanest layout approach. It would be better to use `gap` on `.link-wrapper`:

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
}
```

Then the `<br>` tags could be removed from the HTML.

### Icon accessibility

All icons currently use `alt=""`.

This is acceptable if the icons are decorative and the link text is already present. If an icon communicates additional information, it should have descriptive alt text.

### External links without `rel`

Links use `target="_blank"`, but do not include:

```html
rel="noopener noreferrer"
```

This should be added for security and privacy when opening external links in new tabs.

### Modern CSS nesting

`style.css` uses native CSS nesting:

```css
.linktree {
    >.link-wrapper a {
        &:hover {
            ...
        }
    }
}
```

This keeps the code compact, but it can cause issues in older browsers. For maximum compatibility, it can be rewritten in classic CSS.

### GitHub icon class names may be confusing

In the GitHub button:

```html
<img class="icon-hover" src="assets/github_icon.svg" alt="">
<img class="icon-normal" src="assets/github_icon-invertito.svg" alt="">
```

Class meaning:

- `.icon-normal`: image visible normally;
- `.icon-hover`: image visible only during hover.

This is correct, but the file name `github_icon-invertito.svg` can make the relationship feel inverted at first glance. The logic exists because the normal GitHub button background is dark.

### Hover on mobile

Hover states work well on desktop, but they are not always useful or visible on touch devices. This is a natural limitation of touch interaction rather than a serious bug.

### Text/background contrast

The page uses an image as the background. Some text may become less readable depending on bright or dark areas of the wallpaper.

Current mitigations:

- semi-transparent buttons;
- paragraph text set to `whitesmoke`;
- magenta title.

Possible improvements:

- add a dark or light overlay over the background;
- increase button opacity;
- add `text-shadow` to title and paragraph.

### Missing project automation

There is no:

- `package.json`;
- build step;
- linting;
- formatter;
- tests;
- deployment file.

This does not prevent the page from working, but it means the project is not automated. Documentation now exists through `PROJECT_CONTEXT.md`, `PROJECT_CONTEXT_EN.md`, `README_IT.txt`, and `README.txt`.

## Design Decisions

### Static page without framework

Choice: use only HTML and CSS.

Reasons:

- the project is small;
- no dynamic state is required;
- no routing is required;
- no build step is required;
- it is easy to understand for someone learning HTML/CSS;
- the file can be opened directly in the browser.

### Background managed in CSS

Choice: use `background-image` on `.linktree` instead of an `<img>` tag in the `body`.

Reasons:

- an image in the body becomes part of the document flow and can break the layout;
- `background-size: cover` lets the image cover the whole viewport;
- `background-position: center` keeps the image centered;
- content stays separated from presentation.

### Buttons are 50% wide on desktop

Choice:

```css
width: 50%;
```

on desktop links.

Reasons:

- full-width buttons were too long on desktop;
- percentage width keeps the layout responsive;
- the flex container centers them automatically.

### Buttons are full width on mobile

Choice: in the mobile media query, buttons become:

```css
width: 100%;
```

Reasons:

- on small screens, buttons should be easy to tap;
- using `50%` on mobile would make them too narrow;
- page padding still preserves visual spacing.

### Service-specific colors

Choice: use classes such as `.instagram`, `.github`, `.discord`, `.steam`, `.sito`.

Reasons:

- each service can have its own visual identity;
- the base button rule remains shared;
- differences are isolated in service-specific classes.

### Transparency through `rgba`

Choice: use `rgba(..., 0.65)` or similar values.

Reasons:

- the background remains visible;
- buttons stay readable;
- hover states can become more opaque for clearer feedback.

### GitHub icon swap with two images

Choice: insert two `<img>` elements and hide one with CSS.

Reasons:

- easy to understand;
- no JavaScript required;
- avoids complex CSS filters;
- works well when two icon versions already exist.

### Social meta tags use absolute URLs

Choice: use absolute URLs for `canonical`, `og:url`, `og:image`, `twitter:url`, and `twitter:image`.

Reasons:

- social crawlers do not read the local project from disk;
- shared previews need publicly reachable assets;
- a canonical URL helps search engines identify the preferred page version.

Note: if the site is published on a domain different from `https://stefanocatalinlinktree.netlify.app/`, the meta tag URLs must be updated.

## Roadmap

### High priority

1. Replace `<br>` tags with `gap` on `.link-wrapper`.
2. Add `rel="noopener noreferrer"` to external links.
3. Check contrast and readability over `wallpaper.jpeg`.
4. Consider rewriting nested CSS to classic CSS for compatibility.

### Medium priority

1. Add dedicated classes for Facebook and TikTok if those buttons need custom styling.
2. Introduce CSS variables for colors, opacity, sizes, and breakpoints.
3. Keep `PROJECT_CONTEXT.md`, `PROJECT_CONTEXT_EN.md`, `README_IT.txt`, and `README.txt` updated when the project changes.

### Low priority

1. Add more refined animations.
2. Improve typography.
3. Optimize or compress `wallpaper.jpeg`.
4. Add an alternate theme or light/dark mode.
5. Consider deployment on Netlify, GitHub Pages, or another static hosting platform.

## Instructions For Continuing The Project

### How to run the project

No dependencies need to be installed.

Simplest method:

1. Open `index.html` in a browser.
2. Edit `index.html` or `style.css`.
3. Refresh the browser page.

Alternative method:

- use a local static server if available, but it is not required.

### How to make changes

#### Add a new link

In `index.html`, add a new `<a>` inside `.link-wrapper`.

Example:

```html
<a class="new-service" href="https://example.com" target="_blank" rel="noopener noreferrer">
    New Service <img src="assets/new-service_icon.svg" alt="">
</a>
```

Then add a style rule in `style.css` if needed:

```css
.linktree > .link-wrapper a.new-service {
    background-color: rgba(100, 100, 255, 0.65);

    &:hover {
        background-color: rgb(100, 100, 255);
    }
}
```

#### Change desktop button width

Edit:

```css
.linktree {
    >.link-wrapper a {
        width: 50%;
    }
}
```

Examples:

- `width: 40%;` for shorter buttons;
- `width: 60%;` for longer buttons;
- `width: 80%;` for almost full-width buttons.

#### Change mobile button width

Edit the media query:

```css
@media (max-width: 600px) {
    .linktree > .link-wrapper a {
        width: 100%;
    }
}
```

#### Change the background image

1. Put the new image in `assets/`.
2. Update this line in `style.css`:

```css
background-image: url("assets/new-background.jpeg");
```

#### Make buttons more or less transparent

Change the last value in `rgba`.

Example:

```css
background-color: rgba(226, 0, 226, 0.65);
```

- `0.4` = more transparent;
- `0.65` = semi-transparent;
- `0.9` = almost opaque;
- `1` = fully opaque.

### What a new AI should know before editing

- Do not introduce frameworks or JavaScript unless explicitly requested. The project is meant to stay simple.
- Before changing layout, check the effect on both desktop and below `600px`.
- Desktop buttons are intentionally set to `50%`.
- Mobile buttons should remain `100%`.
- The background must be handled in CSS, not with a loose `<img>` inside the body.
- Icons should stay in `assets/`.
- For icons that need two versions, follow the GitHub pattern with two `<img>` elements and dedicated classes.
- Service-specific rules should come after the base button rule so they can override it.
- If the public domain changes, update canonical, Open Graph, and Twitter meta tag URLs.

## Development Timeline

### 1. Initial structure

The project started as a static HTML page with:

- `Linktree` title;
- `I miei link:` intro text;
- links to social platforms and services;
- basic CSS;
- gray background;
- large buttons.

### 2. Initial responsive problem

While testing different devices, the layout changed in unwanted ways: on some viewports it did not fill the screen correctly, or buttons looked too narrow or shifted.

Discussed solution:

- use `min-height: 100vh`;
- avoid excessively narrow mobile button widths;
- distinguish desktop and mobile behavior.

### 3. Button width control

It was clarified that:

- `font-size` changes text size;
- `padding` changes internal spacing;
- `width` changes button length/width.

The following pattern was introduced:

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
}
```

to center buttons that are shorter than their container.

### 4. Nested CSS organization

The project adopted nested CSS rules inside `.linktree`, for example:

```css
.linktree {
    p {
        font-size: 30px;
        font-weight: bold;
    }
}
```

This is equivalent to:

```css
.linktree p {
    font-size: 30px;
    font-weight: bold;
}
```

### 5. Instagram icon path fix

The Instagram icon initially did not appear because of an incorrect path.

The correct path is inside `assets`, for example:

```html
<img src="assets/instagram_icon.svg" alt="">
```

### 6. Service class specificity

When a class such as `.instagram` was added, the style did not apply because the general rule:

```css
.linktree > .link-wrapper a
```

was more specific than:

```css
.instagram
```

Solution:

```css
.linktree > .link-wrapper a.instagram {
    background-color: ...;
}
```

### 7. GitHub icon hover handling

The GitHub button had an icon readability issue depending on the background.

Solution:

- use the inverted icon on the dark background;
- use the normal icon on the white hover background;
- insert two images;
- control visibility with CSS.

### 8. Replacing gray background with an image

At first, a background image was added as an `<img>` tag inside the body. This broke the layout because the image became part of the HTML flow.

Solution:

- remove the `<img>` tag from the body;
- use `background-image` on `.linktree`;
- rename the image to `wallpaper.jpeg`;
- use `background-size: cover`.

### 9. Semi-transparent buttons

To keep the background visible without losing readability, buttons were made semi-transparent with `rgba`.

Hover states make colors more solid or more visually clear.

### 10. SEO/social meta tags

The main SEO and social preview meta tags were added to the `<head>` of `index.html`:

- title;
- description;
- keywords;
- author;
- robots;
- theme-color;
- canonical;
- Open Graph;
- Twitter Card.

The social preview uses `wallpaper.jpeg` through an absolute URL.

### 11. Project documentation

`PROJECT_CONTEXT.md` was created as an extended document for AIs and developers. Then the following were added:

- `PROJECT_CONTEXT_EN.md`, English translation of the context;
- `README_IT.txt`, short Italian README;
- `README.txt`, short English README.

## AI Context

### General project objective

Create a personal Linktree-style page that is visually customized but simple, with social/personal links, recognizable icons, a custom background, and good desktop/mobile behavior.

### Code philosophy and style

The code should stay:

- simple;
- readable;
- suitable for someone learning HTML/CSS;
- static;
- free of unnecessary dependencies;
- easy to edit manually.

Avoid premature abstractions, frameworks, or JavaScript unless requested.

### Naming conventions

Assets:

- use lowercase or descriptive names;
- prefer suffixes like `_icon`;
- use `-invertito` when the asset is an inverted visual variant;
- avoid long automatically generated names, such as names exported from WhatsApp.

Current examples:

```text
instagram_icon.svg
github_icon.svg
github_icon-invertito.svg
wallpaper.jpeg
```

CSS classes:

- `.linktree`: main container;
- `.title`: title;
- `.link-wrapper`: flex container for buttons;
- service classes on links: `.instagram`, `.github`, `.steam`, `.discord`, `.sito`;
- icon state classes: `.icon-normal`, `.icon-hover`.

### Patterns used

#### Base rule plus specific overrides

All buttons share a base rule:

```css
.linktree {
    >.link-wrapper a {
        display: flex;
        width: 50%;
        ...
    }
}
```

Some services then override color and hover:

```css
.linktree > .link-wrapper a.discord {
    background-color: rgba(88, 101, 242, 0.65);
}
```

#### Flexbox to center links

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
}
```

#### Mobile media query

```css
@media (max-width: 600px) {
    ...
}
```

#### Two images for different visual states

Pattern used for GitHub:

```html
<img class="icon-hover" src="assets/github_icon.svg" alt="">
<img class="icon-normal" src="assets/github_icon-invertito.svg" alt="">
```

### Precise state of the latest available version

At the time this document was created:

- `index.html` contains 7 links;
- the `<head>` contains SEO, Open Graph, and Twitter Card meta tags;
- the `<head>` links `assets/favicon.svg` as the favicon;
- `style.css` contains all styling;
- `assets/` contains 10 assets;
- `wallpaper.jpeg` is the active background;
- desktop buttons are `50%` wide;
- mobile buttons are `100%` wide;
- the title has `font-size: 50px` and a magenta color;
- the paragraph has `font-size: 30px`, bold weight, and `whitesmoke` color;
- GitHub uses the inverted icon normally and the regular icon on hover;
- the project has no dependencies, scripts, or tests;
- documentation includes extended context and bilingual README files.

### Latest work performed

The latest work cycle included:

- adding SEO/social meta tags to the `<head>` of `index.html`;
- adding the tree/link SVG favicon;
- updating the project context;
- creating short bilingual documentation;
- translating the project context into English.

### Recommended next step

The next recommended change is to replace the `<br>` tags between links with `gap` on `.link-wrapper`.

This would make the HTML cleaner and the layout easier to control.

Recommended example:

```css
.link-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
}
```

Then remove the `<br>` tags between buttons in `index.html`.

Immediately after that, add `rel="noopener noreferrer"` to all external links that use `target="_blank"`.
