# Nervos CKB Maintenance Page

A lightweight, self-contained maintenance landing page inspired by Nervos' **Cell Model**. It uses a dark interface, mint-green accents, animated Cell tiles and a subtle peer-to-peer particle network.

- Plain HTML, CSS and vanilla JavaScript; **no packages or build step**
- Static hosting on Vercel; no server, Cloudflare credentials, API or database
- Mobile-friendly and respects `prefers-reduced-motion`
- Chinese/English text follows the browser language (can be disabled)
- No fake block height, network health data, or fake progress indicator
- No third-party scripts, tracking, analytics or cookies

## Deploy to Vercel

1. Import this GitHub repository as a new Vercel project.
2. Select **Other** framework preset.
3. Leave Build Command empty and deploy from the repository root.
4. Use the assigned `*.vercel.app` URL (or a dedicated maintenance domain) as the target of your **temporary 302/307 redirect** rule in Cloudflare.

You do **not** need to change the original site's code or enable Cloudflare proxy for Vercel-hosted websites.

## Customize

Open `index.html` and edit the `CONFIG` block at the bottom:

```js
const CONFIG = {
  siteName: 'Nervos CKB',
  estimatedReturn: '',
  statusUrl: '',
  bilingual: true
};
```

- `estimatedReturn`: display-only text; leave blank when no ETA is known.
- `statusUrl`: optional HTTPS URL to a public status page; blank hides the link.
- `bilingual`: display Chinese for Chinese-language browsers, English otherwise.

The central Cell design is a decorative interpretation, not a live blockchain visualization. The small icon in the header is an original geometric mark inspired by Cell blocks rather than an official Nervos logo. For official brand usage, follow [Nervos Media Kit](https://www.nervos.org/media-kit).

## Operations notes

- Use **302** or **307**, not permanent **301**, when changing the original domain to this maintenance page.
- The redirect changes the visible browser URL; this is intentional for the low-risk, zero-integration setup.
- A simple Vercel static hosting response is HTTP **200**, and a Cloudflare redirect is typically **302/307**. It is not a true HTTP 503 maintenance response on the original URL.
- Vercel hosting does not itself activate maintenance. Turn your existing Cloudflare redirect on/off as part of the maintenance procedure.

## Files

- `index.html`: complete self-contained page
- `vercel.json`: minimal static hosting headers

## License

MIT.
