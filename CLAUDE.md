# CLAUDE.md

## Projekt: Clara Mohn – Künstlerin Website

Jekyll-Website für eine Malerin mit Galerie, Blog und Kontaktformular.

## Build & Entwicklung

```bash
# Abhängigkeiten installieren
bundle install

# Entwicklungsserver starten (mit LiveReload)
bundle exec jekyll serve --livereload

# Produktionsbuild
bundle exec jekyll build
```

Die Site ist unter `http://localhost:4000` erreichbar.

## Architektur

```
.
├── _config.yml          # Jekyll-Konfiguration (Titel, Plugins, Pagination)
├── _layouts/
│   ├── default.html     # Basis-Layout mit Nav + Footer
│   ├── page.html        # Statische Seiten (Über mich, Impressum)
│   ├── post.html        # Blog-Beiträge
│   └── artwork.html     # Einzelnes Galeriewerk mit Lightbox
├── _includes/
│   ├── head.html        # <head> mit SEO-Tags
│   ├── nav.html         # Fixierte Navigation mit Mobile-Toggle
│   └── footer.html      # Footer mit Links
├── _sass/
│   ├── variables.scss   # Farben, Schriften, Breakpoints
│   ├── base.scss        # Reset, Typografie, Button-Stile
│   ├── nav.scss         # Navigation
│   ├── home.scss        # Hero, About, Kontakt-Section
│   ├── gallery.scss     # Galerie-Grid, Lightbox, Artwork-Detail
│   ├── blog.scss        # Post-Karten, Artikel, Pagination
│   └── footer.scss      # Footer
├── assets/css/main.scss # SCSS-Einstiegspunkt (Jekyll kompiliert das)
├── _gallery/            # Galeriewerke als Markdown-Dateien
├── _posts/              # Blog-Beiträge (YYYY-MM-DD-titel.md)
├── assets/images/
│   ├── gallery/         # Werkbilder (JPG, ~1200px breit)
│   ├── blog/            # Blog-Titelbilder
│   ├── hero.jpg         # Hero-Bild Startseite
│   └── portrait.jpg     # Portraitfoto der Künstlerin
├── index.html           # Startseite
├── galerie/index.html   # Galerie-Übersicht mit Filterung
├── blog/index.html      # Blog-Index mit Pagination
├── ueber.md             # Über-mich-Seite
├── impressum.md         # Impressum
└── datenschutz.md       # Datenschutzerklärung
```

## Galeriewerk hinzufügen

Neue Datei in `_gallery/` anlegen:

```markdown
---
title: "Titel des Werks"
date: 2024-04-01
year: 2024
category: Landschaft   # Landschaft | Porträt | Abstrakt | Stillleben
medium: Öl auf Leinwand
size: 80 × 100 cm
image: /assets/images/gallery/dateiname.jpg
description: >
  Kurze Beschreibung des Werks.
status: Original        # Original | Druck | Privat
price: "2.800 €"
available: true         # true = kaufbar, false = vergeben/privat
---
```

## Blog-Beitrag hinzufügen

Neue Datei in `_posts/` nach Schema `YYYY-MM-DD-titel.md`:

```markdown
---
title: "Titel des Beitrags"
date: 2024-04-01
category: Prozess       # Prozess | Gedanken | Atelier | Ausstellung
cover_image: /assets/images/blog/bild.jpg
excerpt: "Kurzer Teaser für die Blog-Übersicht."
---

Beitragsinhalt in Markdown...
```

## Bilder

- Galeriewerke: `assets/images/gallery/` · empfohlen 1200×1600 px (Portrait)
- Blog-Cover: `assets/images/blog/` · empfohlen 1200×675 px (16:9)
- Hero: `assets/images/hero.jpg` · empfohlen 1400×900 px
- Portrait: `assets/images/portrait.jpg` · empfohlen 800×1100 px

## Deployment

GitHub Pages kompatibel. Für benutzerdefinierte Domain:
- `CNAME`-Datei im Wurzelverzeichnis mit der Domain anlegen
- DNS A-Record auf GitHub Pages IPs zeigen

## Kontaktformular

Das Formular nutzt [Formspree](https://formspree.io). In `index.html` die
Formspree-ID ersetzen: `action="https://formspree.io/f/DEINE-ID"`
