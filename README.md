# Delinea Platform — Post-Demo Interactive Tour

A single-page interactive site to send to customers after a demo. Visitors move through three guided steps:

1. **Choose Your Lens** — pick a role (CISO, Security Architect, IT Operations, Compliance Lead) and see priorities, capabilities, and outcomes tailored to that perspective.
2. **Meet the Platform** — explore the three pillars of the Delinea Platform powered by Iris AI: Visibility, Posture, and Control. Click each pillar to see what's inside.
3. **See It In Action** — walk through real-world breach scenarios step by step. Each step shows a side-by-side comparison: *Without Modern PAM* (with the relevant MITRE ATT&CK technique tagged) vs. *With Delinea Platform* (with the specific control that stopped it). Each scenario ends with a dramatic three-metric scoreboard.

Four scenarios are included: Phished Contractor Credentials, Stolen Admin Laptop, Insider Threat (Departing Admin), and Compromised Service Account.

## What's in this folder

- `index.html` — the entire site (HTML + CSS + JS in one file, no dependencies)
- `README.md` — this file

## Preview locally

Just double-click `index.html` and it'll open in your browser. Or, from a terminal:

```bash
python3 -m http.server 8000
# Then open http://localhost:8000
```

## Deploy to GitHub Pages (free)

1. Create a new GitHub repo (e.g. `delinea-platform-tour`). Public repos get free Pages hosting.
2. Upload `index.html` to the root of the repo.
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, select **Deploy from a branch**.
5. Pick **main** branch, **/ (root)** folder. Save.
6. Wait about 60 seconds. Your site will be live at `https://<your-username>.github.io/<repo-name>/`.

### Custom domain (optional but recommended)

For a polished customer-facing URL like `platform-tour.delinea.com`, ask your IT/web team to add a CNAME record pointing the subdomain to `<your-username>.github.io`, then add the domain in **Settings → Pages → Custom domain**. Free SSL is automatic.

## Customizing

All the content lives in three JavaScript arrays near the bottom of `index.html`. No build step — just edit, save, push.

- `const roles = [...]` — role cards and their detail content (CISO, Security Architect, etc.)
- `const products = [...]` — the three pillars (Visibility, Posture, Control), their components, and outcomes
- `const scenarios = [...]` — the four scenario walkthroughs, including timeline steps, ATT&CK techniques, Delinea controls, and scoreboard metrics

The Delinea brand colors are set as CSS custom properties at the top of the `<style>` block (e.g., `--delinea-green`, `--delinea-purple`, `--delinea-cyan`). Change them in one place, they apply everywhere.

## Things you might want to add later

- **Analytics** — drop in a Google Analytics or Plausible snippet near the top of `<body>` to see which roles, pillars, and scenarios get the most engagement.
- **Per-customer personalization** — append a `?customer=Acme` query param and read it in JS to greet them by name.
- **Lead capture** — replace the "Book a Follow-up" link with a Calendly embed, HubSpot meeting link, or a contact form (Netlify Forms is free if you host there instead of GitHub Pages).
- **More scenarios** — add another object to the `scenarios` array. The site auto-renders the new tab.
- **Deep-link to specific content** — read `window.location.hash` on load to jump straight to a particular role, pillar, or scenario for tailored email links.

## Notes on the content

The role descriptions, pillar components, and scenario timelines are written as a strong starting point but should get a once-over from product marketing or a Solutions Engineer before sending to a real prospect. In particular:

- The scoreboard metrics in each scenario (e.g., "21 days → < 60 sec," "2.3M records → 0") are illustrative — based on industry-typical figures rather than verified Delinea customer numbers. Either swap in numbers your marketing team has signed off on (Verizon DBIR, IBM Cost of a Breach, and Mandiant M-Trends are good public sources) or add a small "illustrative — based on industry averages" disclaimer near the scoreboard.
- The hero stat (99.995% platform uptime) should be verified as the most current Delinea-approved figure.
- Component names within each pillar match the official Delinea framework but the surrounding descriptions are written for clarity to non-technical readers — easy to refine as needed.
