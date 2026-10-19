# Appunti tecnici

Blog personale statico realizzato con Astro. Gli articoli sono file Markdown in `src/content/blog/`: non servono database, server applicativi o adapter.

## Avvio locale

Richiede Node.js `22.12.0` o successivo.

```sh
npm install
npm run dev
```

## Scrivere un articolo

Crea un file Markdown dentro `src/content/blog/`, per esempio `docker-per-sviluppatori.md`:

```md
---
title: "Docker per lo sviluppo locale"
description: "Come rendere riproducibile l'ambiente di sviluppo con Docker Compose."
pubDate: "2026-10-11"
category: "DevOps"
tags: ["docker", "sviluppo"]
draft: false
---

Il contenuto dell'articolo va qui. Puoi usare la sintassi Markdown,
inclusi titoli, link, immagini, tabelle e blocchi di codice.
```

Le categorie ammesse sono `Software engineering`, `AI engineering` e `DevOps`. Imposta `draft: true` per tenere una bozza fuori dal sito, dal feed RSS e dalla sitemap. Se vuoi aggiungere un'immagine hero, salvala in `src/assets/` e aggiungi al frontmatter un percorso relativo, per esempio `heroImage: "../../assets/copertina.jpg"`.

## Configurazione prima della pubblicazione

1. Imposta la variabile d'ambiente `SITE_URL` sull'URL canonico del tuo dominio (per esempio `https://blog.example.it`), sia in locale sia nelle variabili d'ambiente del progetto Vercel.
2. Personalizza titolo, descrizione e nome autore in `src/consts.ts`.
3. Completa la pagina `src/pages/about.astro`.
4. Aggiungi gli articoli in `src/content/blog/`.

Se `SITE_URL` non è impostata, la configurazione usa `https://example.com` come valore di esempio. Impostala prima di pubblicare per generare canonical URL e sitemap corretti.

## Build e pubblicazione su Vercel

```sh
npm run build
npm run preview
```

Importa il repository in Vercel: la piattaforma rileva Astro automaticamente. Il comando di build è `npm run build` e la cartella di output è `dist`. Il progetto genera HTML statico; non installare un adapter Vercel a meno che in futuro tu non aggiunga rendering server-side.

Puoi anche eseguire la build sulla Raspberry Pi, ma non è necessario per la pubblicazione su Vercel. Il dominio può restare gestito da Cloudflare; configura il DNS seguendo le istruzioni mostrate da Vercel per il dominio personalizzato.
