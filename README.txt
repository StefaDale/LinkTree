LINKTREE - ENGLISH README
=========================

Description
-----------
This project is a personal Linktree-style page built with plain HTML and CSS.
It collects the profile's main links in one place:
Instagram, Facebook, personal website, GitHub, Steam, TikTok, and Discord server.

The page uses a background image, large icon buttons, service-specific colors for some links,
and a media query for smaller screens.

Technologies
------------
- HTML5
- CSS3
- Local SVG/JPEG assets
- No framework
- No JavaScript library
- No required build step

Structure
---------
linktree/
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
|-- style.css
|-- PROJECT_CONTEXT.md
|-- PROJECT_CONTEXT_EN.md
|-- README_IT.txt
`-- README_EN.txt

Main files
----------
- index.html: contains the page structure, links, icons, and SEO/social meta tags.
- style.css: contains layout, background, colors, hover states, responsive behavior, and button sizes.
- assets/: contains icons and the background image.
- PROJECT_CONTEXT.md: detailed Italian documentation for AIs and developers.
- PROJECT_CONTEXT_EN.md: English translation of the project context.

How to run the project
----------------------
No installation is required.

Open index.html directly in a browser.

You can also use a local static server, but it is not required.

How to edit links
-----------------
Open index.html and edit the elements inside:

<div class="link-wrapper">
    ...
</div>

Example:

<a class="instagram" href="https://instagram.com/ste_catalin_" target="_blank">
    Instagram <img src="assets/instagram_icon.svg" alt="">
</a>

How to change button width
--------------------------
In style.css, desktop button width is controlled by:

.linktree {
    >.link-wrapper a {
        width: 50%;
    }
}

For longer buttons, use something like width: 60%.
For shorter buttons, use something like width: 40%.

On mobile, width is overridden in the media query:

@media (max-width: 600px) {
    .linktree > .link-wrapper a {
        width: 100%;
    }
}

How to change the background
----------------------------
Replace assets/wallpaper.jpeg or edit this line in style.css:

background-image: url("assets/wallpaper.jpeg");

The background is handled with CSS, not with an <img> tag in the body.

SEO/social meta tags
--------------------
The meta tags are in the <head> of index.html.
The page includes basic SEO tags, Open Graph tags, and Twitter Card tags.

If the public domain changes, update these fields:
- canonical
- og:url
- og:image
- twitter:url
- twitter:image

Important note: social preview images need an absolute online URL.

Known issues and recommended improvements
-----------------------------------------
- Links are separated with <br>; using gap on .link-wrapper would be cleaner.
- Links using target="_blank" still do not include rel="noopener noreferrer".
- There is no favicon yet.
- Facebook and TikTok still use the base button style, without dedicated classes.
- There are no automated tests or lint/format tools.

Before continuing
-----------------
Read PROJECT_CONTEXT_EN.md for the full context.
Keep the project simple: HTML, CSS, local assets, and no unnecessary dependencies.
