# Oakdene Dental

Marketing site for **Oakdene Dental** — olive/elegant theme, evening-appointment USP.

Built with [Astro 5](https://astro.build/) + [Tailwind CSS v4](https://tailwindcss.com/) (Vite plugin). Static output, deploys to Netlify.

## Local development

```bash
npm install
npm run dev     # http://localhost:4321
npm run build   # → ./dist
npm run preview # serves the built site
```

## Deployment (Netlify)

1. Connect this repo in the Netlify dashboard (New site → Import from GitHub → `huzipatel/irn-dental`).
2. Netlify auto-detects Astro and uses `netlify.toml` for build settings — no manual config needed.
3. Once the first build succeeds, add the custom domain `oakdene.dental` under **Domain management** and follow the DNS instructions (CNAME on `www`, A or ALIAS on apex to Netlify's load balancer IPs).
4. Netlify provisions a free Let's Encrypt cert automatically.

## Editing content

All copy and section data live in `src/components/*.astro`. Most lists (services, hours, values) are simple arrays at the top of each file — edit and push.

Phone / email / address placeholders to replace before launch:
- `+44 0000 000 0000`
- `hello@oakdene.dental`
- `"Your clinic address"` and `"Town · Postcode"` (appears in both `Contact.astro` and `Footer.astro`)
- Latitude/longitude for a Google/Apple Maps embed if you want one (currently no embed for speed).

## Performance budget

- HTML payload: < 30 KB compressed
- Zero client-side JS (no Astro islands used)
- Fonts: Inter + Cormorant Garamond, loaded with `display=swap` and preconnect
- Inlined critical CSS (Astro `inlineStylesheets: 'auto'`)
- All assets hashed and cached for 1 year via `netlify.toml` headers

## Form handling

The contact form uses **Netlify Forms** — no backend code needed.
- After the first deploy, the form appears in your Netlify dashboard under **Forms**.
- Submissions email through Netlify's free tier (100/mo).
- Honeypot field is wired in (`bot-field`).
- For Akismet or higher volumes, enable spam filtering in the Netlify Forms settings.
