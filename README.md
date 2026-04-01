# Matteo Rubert — Tema Grav

## Installazione rapida

### 1. Scarica Grav

```bash
# Con Grav + Admin panel (consigliato)
wget https://getgrav.org/download/core/grav-admin/latest -O grav-admin.zip
unzip grav-admin.zip
mv grav-admin/ il-tuo-dominio/
```

Oppure scarica direttamente da https://getgrav.org/downloads

### 2. Copia i file del tema

Dalla cartella `rubert-grav/user/` copia tutto dentro `<grav>/user/`:

```
user/
├── config/
│   ├── system.yaml       ← configurazione Grav
│   └── site.yaml         ← titolo e metadati sito
├── pages/
│   └── 01.home/
│       ├── home.md                     ← homepage
│       ├── 01.micidial/
│       │   ├── progetto.md             ← contenuto progetto
│       │   └── [immagini]              ← carica qui le immagini
│       ├── 02.bridge-film-festival/
│       │   ├── progetto.md
│       │   └── [immagini]
│       └── ... (tutti gli altri progetti)
└── themes/
    └── rubert/
        ├── blueprints.yaml             ← blueprint tema (admin)
        ├── rubert.yaml                 ← config default tema
        ├── blueprints/
        │   ├── home.yaml               ← campi admin per homepage
        │   └── progetto.yaml           ← campi admin per progetti
        └── templates/
            ├── base.html.twig          ← layout base (nav, pannello contatti)
            ├── home.html.twig          ← template homepage
            └── progetto.html.twig      ← template singolo progetto

### 3. Attiva il tema

Nel file `user/config/system.yaml` il tema è già impostato a `rubert`.

Oppure dall'admin panel: Configurazione → Sistema → Tema predefinito → rubert

### 4. Configura EmailJS

Modifica `user/themes/rubert/rubert.yaml`:

```yaml
emailjs_public_key: 'la-tua-public-key'
emailjs_service_id: 'il-tuo-service-id'
emailjs_template_id: 'il-tuo-template-id'
```

Oppure dall'admin panel: Temi → Rubert → Impostazioni

### 5. Carica le immagini dei progetti

Per ogni progetto, carica le immagini direttamente nella cartella della pagina:

```
user/pages/01.home/01.micidial/
    progetto.md
    micidial-cover.webp      ← cover (usata nella lista e in cima al progetto)
    micidial-mobile.webp     ← galleria img 1
    micidial-desktop.webp    ← galleria img 2
    micidial-tablet.webp     ← galleria img 3
```

I nomi file devono corrispondere a quelli nel frontmatter YAML del `progetto.md`.

---

## Aggiungere un nuovo progetto

### Via admin panel (più semplice)
1. Admin → Pagine → Home → Aggiungi pagina figlia
2. Template: `progetto`
3. Compila i campi: titolo, tag, anno, ruolo, immagini
4. Carica le immagini nella pagina
5. Scrivi il testo nel corpo della pagina

### Via file (avanzato)
Crea una nuova cartella in `user/pages/01.home/` con prefisso numerico:

```
user/pages/01.home/09.nuovo-progetto/
    progetto.md
    cover.webp
    img1.webp
    img2.webp
```

Frontmatter minimo del `progetto.md`:
```yaml
---
title: 'Nome Progetto'
template: progetto
project_tags: 'Brand · Web Design'
project_year: '2025'
project_role: 'Design, sviluppo'
project_cover: 'cover.webp'
project_images:
    - src: img1.webp
    - src: img2.webp
    - src: img3.webp
    - src: img4.webp
---

Testo descrizione progetto in **Markdown**.
```

---

## Modificare i dati di contatto

Da admin: Temi → Rubert → tab Impostazioni

Oppure direttamente in `user/themes/rubert/rubert.yaml`:
```yaml
contact_email: 'tua@email.it'
contact_phone: '+39 000 000 0000'
contact_studio: 'Studio · Città, Italia'
instagram_url: 'https://...'
linkedin_url: 'https://...'
```

---

## Modificare i testi dell'hero

Da admin: Pagine → Home → modifica i campi nella tab Contenuto.

Oppure nel frontmatter di `user/pages/01.home/home.md`:
```yaml
hero_tag: 'Art Director & Designer — Verona, IT'
hero_role: 'Art Director & Designer'
hero_studio: 'BananaStudio, Verona'
hero_status: 'Disponibile ✦'
```

---

## Plugin consigliati (opzionali)

```bash
bin/gpm install admin       # pannello di amministrazione
bin/gpm install sitemap     # sitemap.xml automatica
bin/gpm install seo         # meta tag SEO avanzati
bin/gpm install breadcrumbs # breadcrumb navigation
```
