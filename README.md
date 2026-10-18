# Tutico Website

A fast, SEO-focused single-page website for Tutico, a sandwich and breakfast spot in Lüleburgaz, Turkey. Built with Next.js 16, React 19 and Tailwind CSS 4.

## Overview

The site gives local customers everything they need in one page: the menu, the story of the place, location and opening hours, and quick links to order through the delivery platforms they already use. It is a static content site with no backend; all content lives in the components.

Search visibility for local queries (e.g. "lüleburgaz sandviç", "lüleburgaz kahvaltı") was a core goal, so the page uses a clear heading structure, rich metadata and `Restaurant` structured data.

## Features

- Hero section with quick actions
- Menu section: sandwiches, breakfast, mantı, snacks and croissants
- About section with Framer Motion animations
- Contact section with an embedded Google Map
- Order modal linking to GetirYemek, Yemeksepeti, Trendyol Yemek, WhatsApp and a QR menu
- Floating menu button for quick navigation on mobile
- SEO: page metadata and Open Graph tags, JSON-LD `Restaurant` schema (address, geo coordinates, opening hours), `sitemap.ts`, `robots.txt`
- Responsive, mobile-first layout

## Tech Stack

| Area | Technologies |
|---|---|
| Framework | Next.js 16 (App Router, standalone output, React Compiler) |
| UI | React 19, TypeScript, Tailwind CSS 4 |
| Animation / icons | Framer Motion, Lucide React |
| Deployment | Docker, CapRover (`captain-definition`) |

## Project Structure

```
.
├── app/
│   ├── layout.tsx          # Metadata, fonts, global layout
│   ├── page.tsx            # Single page composed of the sections below
│   ├── sitemap.ts
│   └── globals.css
├── components/
│   ├── Header.tsx, Hero.tsx, Menu.tsx, About.tsx, Contact.tsx, Footer.tsx
│   ├── OrderModal.tsx      # Delivery platform links
│   ├── FloatingMenuButton.tsx
│   └── StructuredData.tsx  # JSON-LD Restaurant schema
├── public/                 # Images, robots.txt
├── content.md              # Development plan and SEO keyword notes (Turkish)
├── Dockerfile
└── captain-definition
```

## Getting Started

Requires Node.js 20+.

```bash
npm install
npm run dev        # http://localhost:3000
```

Other scripts:

| Script | Description |
|---|---|
| `npm run build` | Production build (standalone output) |
| `npm start` | Start the production server |
| `npm run lint` | ESLint |

No environment variables are required.

## Deployment

The multi-stage `Dockerfile` builds the app on Node 20 Alpine and runs the Next.js standalone server (`node server.js`) on port `3000`. `captain-definition` lets you deploy the repo directly to CapRover.

```bash
docker build -t tutico-website .
docker run -p 3000:3000 tutico-website
```

The sitemap and `robots.txt` are configured for the `tutico.co` domain; update them if you deploy elsewhere.

---

Built by [Mertcan Eren](https://github.com/mertcaneren0)
