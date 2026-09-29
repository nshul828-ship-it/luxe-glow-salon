# Luxe Glow Salon

A complete mobile-first salon concept website. Plain HTML and JavaScript, Tailwind CSS 4 compiled by Vite, locally hosted DM Sans + Cormorant Garamond, and optimized Unsplash WebP photography. No backend or runtime framework required.

## Local setup

Install Node.js 22 LTS or newer. From this folder:

```bash
npm ci
npm run dev
```

Open the local URL printed by Vite (port 4173). For a production build:

```bash
npm run build
npm run preview
```

The deployable website is `dist/`. The ZIP includes this prebuilt folder, but run a new build after making changes. Use a local web server rather than double-clicking index.html because source modules and root-relative assets need HTTP.

## Included

Hero, six-service filterable price menu, salon story, three stylist profiles with appointment preselection, keyboard-operable before/after slider, clearly marked sample testimonials, FAQs, appointment form, neighbourhood map, configurable telephone/WhatsApp links, mobile contact bar, privacy dialog, SEO description and social metadata, and SVG favicon.

## Customize before launch

This is a fictional concept. Replace all sample prices, team profiles, testimonials, address, hours, and images with approved business details. The before/after pair contains DIFFERENT stock models and is explicitly illustrative; never present it as an actual transformation. Obtain consent for real client images and reviews. Unsplash images do not imply endorsement by the pictured people.

1. Edit `index.html` for content, prices, team, opening hours and the map's `src` and directions link. Update Monday closure logic in `main.js` if hours change.
2. Edit `src.css`: `--accent` is the plum accent, `--paper` is the background. Font imports are local and bundled by Vite; no external font request.
3. Replace `public/assets/*.webp` with optimized assets at the existing dimensions. Update alt text in `index.html`.
4. Configure real contact details in `public/config.js`:

```js
window.SALON_CONFIG = {
  phone: '+91YOUR_REAL_NUMBER', // Replace the whole value with valid E.164 digits
  whatsapp: '91YOUR_REAL_NUMBER', // Country code + digits, no + or spaces
  formspreeEndpoint: 'https://formspree.io/f/YOUR_REAL_FORM_ID'
};
```

These examples are placeholders, not valid destinations. Blank values safely show a setup notice and do not call/message a stranger. Once valid real numbers are entered, the buttons become `tel:` and `https://wa.me/` links. No private keys belong in this file.

### Formspree

Create a form at https://formspree.io, verify the destination email and copy its actual `/f/...` endpoint into `public/config.js`. Rebuild. The form submits via AJAX, handles success/error/timeout states, keeps data after errors, includes a honeypot and requires contact consent. Required fields, email format, past dates and Monday closure are validated. A request is not an appointment confirmation.

Without an endpoint the form explicitly reports that NOTHING was sent. Test one real submission and receipt yourself before launch; no email was sent during development. Review the privacy text and Formspree retention/settings for your real operation. Current privacy copy describes the concept and must be updated for production.

### SEO

The draft uses `noindex, nofollow` intentionally so fictional business content is not indexed. Before real launch:
- Replace all sample business details and testimonials.
- Change robots to `index, follow` in `index.html`.
- Add `<link rel="canonical" href="https://YOUR-ACTUAL-DOMAIN/">` and `og:url` with your real URL.
- Add `public/robots.txt` and `public/sitemap.xml` using that same verified origin.
- Update title/description for the real city and add accurate HairSalon JSON-LD only after business details are verified. Do not add fake ratings.

## GitHub: exact commands

The delivered project was initialized and committed locally. The archive omits `.git` for portability. No remote was pushed because GitHub is not connected in this session.

Install Git and GitHub CLI, extract the ZIP, then:

```bash
git init -b main
git add .
git commit -m "Build Luxe Glow Salon website"
gh auth login
gh repo create luxe-glow-salon --private --source=. --remote=origin --push
```

If Git asks for identity, configure your own name and email locally before committing. If that repository name exists, choose another name. Do not put secrets in the repository.

## Recommended free business deployment: Netlify

Netlify's free plan permits commercial sites. Usage quotas apply, and new Free projects may show a Netlify badge. Source: https://www.netlify.com/blog/introducing-netlify-free-plan/ and https://www.netlify.com/pricing/.

```bash
npm ci
npm run build
npx netlify-cli login
npx netlify-cli deploy --dir=dist --prod
```

At the prompt choose **Create & configure a new project**, select your account/team, and choose an available site name. The CLI prints the exact assigned `https://...netlify.app` URL. It cannot be known until deployment succeeds. If the project is private by default, use Netlify's project visibility setting to make it public when ready.

For Git-based automatic deploys, import the GitHub repository at Netlify:

| Setting | Value |
|---|---|
| Production branch | `main` |
| Base directory | Repository root (blank) |
| Build command | `npm run build` |
| Publish directory | `dist` |
| Node version | `22` |
| Environment variables | None required |

`netlify.toml` includes those build settings and security headers. Future pushes to main trigger builds after Git integration is enabled.

## Vercel alternative

Vercel Hobby is restricted to personal/non-commercial projects. It is suitable for a personal demo; use an appropriate paid plan for an operating salon. Sources: https://vercel.com/docs/plans/hobby and https://vercel.com/docs/cli/deploy.

```bash
npm ci
npx vercel login
npx vercel link
npx vercel --prod
```

Choose framework **Vite**, root **./**, install command **npm ci**, build command **npm run build**, output directory **dist**. `vercel.json` supplies build/output settings. The command prints the actual deployment URL. Import the GitHub repository in Vercel for automatic deployment.

## Testing and performance

See `TESTING.md` for checks actually completed and limitations. Lighthouse 90+ is a performance target, not a measured result in this environment. Run a mobile Lighthouse audit on the final production URL:

```bash
npx lighthouse https://YOUR-ACTUAL-DEPLOYMENT-URL --only-categories=performance,accessibility,best-practices,seo --output=html --output-path=lighthouse-report.html --view
```

Requires local Chrome. Run after replacing sample content and enabling indexing. The draft's intentional noindex affects SEO scoring. The Google map is lazy-loaded and depends on third-party network availability. Fonts and imagery are local; CSS/JS are compiled and minified. No animation library, analytics, cookies, or backend is required.

## File map

- `index.html`: content and metadata
- `src.css`: Tailwind and custom responsive design
- `main.js`: accessible interactions and Formspree submission
- `public/config.js`: public contact/form configuration
- `public/assets/`: locally hosted optimized photos
- `public/favicon.svg`: brand favicon
- `vite.config.js`, `package.json`, `package-lock.json`: reproducible build
- `netlify.toml`, `vercel.json`: deployment settings
- `ASSET_CREDITS.md`: image sources and font licenses
- `TESTING.md`: verification record

No live account, submission endpoint, deployment URL, or real salon details were invented.
