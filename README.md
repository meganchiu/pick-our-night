# Pick Our Night

A "what should we do tonight?" recommendation engine for Fort Worth (76108) — weighted mood matching, a weighted spin-the-wheel matchmaker, and an interactive map of favorite spots.

## Files

- `index.html` — the logged-out landing page (sign up / log in)
- `dashboard.html` — the logged-in tool (mood sliders, map, spot list, spin)

## Status

These pages are visual/front-end only right now. Login, signup, and password reset are placeholder forms — they don't yet talk to a real account system. See "Next steps" below.

## Hosting (pick one — all free)

- **GitHub Pages** — Settings → Pages → deploy from the `main` branch, root folder. Your site will be live at `https://<username>.github.io/pick-our-night/`.
- **Netlify** — drag this folder onto app.netlify.com, or connect this repo for auto-deploys on every push.
- **Vercel** — same idea, connect the repo at vercel.com.
- **Cloudflare Pages** — same idea, connect the repo at pages.cloudflare.com.

## Next steps: real accounts + password reset

This app needs [Supabase](https://supabase.com) (free tier) for:
- **Auth** — signup/login, handled securely (you never store raw passwords yourself)
- **Password reset** — built-in reset-via-email flow
- **Database** — a real Postgres table for saved spots, tied to each account instead of shared globally

Rough steps:
1. Create a free Supabase project at supabase.com.
2. In Supabase, enable Email/Password auth (on by default) and note your project URL + anon public key (Settings → API).
3. In `index.html`, wire the login/signup forms to `supabase.auth.signInWithPassword()` / `supabase.auth.signUp()` using the Supabase JS client (loaded via a `<script>` tag from a CDN — no build step needed).
4. Add a "forgot password?" link that calls `supabase.auth.resetPasswordForEmail()`.
5. In `dashboard.html`, check for a valid session on page load (`supabase.auth.getSession()`); redirect to `index.html` if there isn't one.
6. Create a `spots` table in Supabase (columns: id, user_id, name, category, cost, energy, setting, notes, lat, lng) and swap the current `window.storage` calls for Supabase queries scoped to the signed-in user.

## Local preview

No build tools needed — just open `index.html` in a browser, or run a quick local server:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
