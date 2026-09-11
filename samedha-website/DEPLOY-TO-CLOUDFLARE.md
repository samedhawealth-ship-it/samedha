# Deploying the Samedha website to Cloudflare Pages

You don't need to write any code for this — Cloudflare Pages will host these
files as-is. Here's the simplest path.

## Option A — Drag and drop (fastest, no GitHub needed)

1. Log in to the Cloudflare dashboard: https://dash.cloudflare.com
2. In the left sidebar, go to **Workers & Pages**.
3. Click **Create** → **Pages** → **Upload assets**.
4. Give the project a name (e.g. `samedha-website`).
5. Drag the whole `samedha-website` folder (or all the files inside it) into
   the upload area. Make sure `index.html` ends up at the top level of what
   you upload, not nested inside an extra folder.
6. Click **Deploy site**. Cloudflare will give you a `*.pages.dev` URL within
   about a minute — that's your live site.
7. Go to your Pages project → **Custom domains** → **Set up a custom domain**,
   and enter the domain you already registered. Since it's already on
   Cloudflare, this is usually a one-click confirmation (Cloudflare adds the
   DNS record for you).

Every time you want to update the site, come back to this Pages project and
upload a new version, or switch to Option B below for something more
convenient long-term.

## Option B — Connect to GitHub (better if you'll keep editing)

1. Create a free GitHub account if you don't have one, and create a new
   repository (e.g. `samedha-website`).
2. Upload these files into that repository (GitHub's web UI lets you drag
   and drop files directly, no command line needed).
3. In Cloudflare: **Workers & Pages** → **Create** → **Pages** → **Connect to
   Git** → choose the repository.
4. Leave the build settings as "no build command" / framework preset "None",
   since this is a plain HTML site — just set the output directory to `/`
   (the root).
5. Deploy, then attach your custom domain the same way as in Option A.
   From now on, any change you push to GitHub redeploys the site
   automatically.

## What's in this folder

- `index.html` — Home
- `services.html` — Services (Wealth Management, Corporate Advisory,
  Accounting, Financial Reporting)
- `about.html` — About / team (placeholder text — see below)
- `contact.html` — Contact page with a working `mailto:` form
- `css/style.css` — all styling, built around your logo's navy/gold/blue
- `js/main.js` — just the mobile menu toggle
- `assets/logo.png` — your uploaded logo
- `assets/favicon.png` — small version used as the browser tab icon

## Before you publish, replace the placeholders

Search each file for text in `[square brackets]` — these are the spots
where you need to swap in real content:
- Company founding story and mission (`about.html`)
- Team names, titles, and bios (`about.html`)
- Street address, phone number, and email (`contact.html`, and the footer
  in every page)

## Upgrading the contact form later (optional)

Right now the contact form opens the visitor's email app with a pre-filled
message — this works immediately with zero setup, but it's a bit clunky on
mobile and you won't get submissions stored anywhere. When you're ready,
sign up at https://formspree.io (free tier available), and swap the
`<form action="mailto:...">` line in `contact.html` for the endpoint they
give you — takes about five minutes.
