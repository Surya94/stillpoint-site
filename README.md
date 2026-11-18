# Still Point Games website

A static site for GitHub Pages. It holds:

- `index.html`: the studio landing page
- `privacy.html`: the Balloon Archer privacy policy
- `app-ads.txt`: the ad-seller list, which must be served at the domain root

## Placeholders to replace before publishing

| Placeholder | Where | Replace with |
|---|---|---|
| `YOURDOMAIN` | `index.html` (contact), `privacy.html` (section 9, twice) | your domain, e.g. `stillpointgames.com` |
| "Coming soon" badge | `index.html` (see the HTML comment) | the Google Play link, once the game is live |
| Comment lines | `app-ads.txt` | the lines from the AppLovin dashboard, plus one block per mediation network |

`privacy.html` is a template, not legal advice. Review it, and update it whenever you add an SDK (analytics, crash reporting, in-app purchases) or a mediation network.

## Publishing

1. **Buy a domain**, e.g. from Cloudflare Registrar or Namecheap.
2. **Replace `YOURDOMAIN`** in the files, using the table above.
3. **Push the folder to GitHub.** Create a public repo (e.g. `stillpoint-site`) and push this folder to it. GitHub Desktop is the easiest option if `git` isn't installed.
4. **Turn on Pages.** In the repo, go to Settings → Pages. Under Source, choose "Deploy from a branch", then `main` and `/ (root)`.
5. **Set the custom domain.** On the same Pages screen, enter your domain under Custom domain. This commits a `CNAME` file to the repo.
6. **Add DNS records** at your registrar:
   - Four `A` records for the apex (`@`): `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - A `CNAME` record for `www` pointing to `<your-github-username>.github.io`
   - On Cloudflare, set these records to "DNS only" (grey cloud) until HTTPS is issued.
7. **Turn on HTTPS.** Once the certificate is ready (can take up to about an hour), tick **Enforce HTTPS**.
8. **Set up email.** GitHub Pages doesn't handle email. Create `support@yourdomain` with your registrar's email forwarding. Cloudflare Email Routing is free.
9. **Check the site is live.** Open `https://yourdomain/`, `https://yourdomain/privacy.html` and `https://yourdomain/app-ads.txt`.

## After it's live

- **AppLovin signup:** use `https://yourdomain` as the company website.
- **Play Console → Store settings:** set Website to `https://yourdomain`. This must be the same domain that hosts `app-ads.txt`.
- **Play Console → App content → Privacy policy:** use `https://yourdomain/privacy.html`.
- **AppLovin MAX consent flow (in Unity):** use the same privacy-policy URL.
