# Roadchanger Website

## Files
- `index.html` — Main homepage (roadchanger.com)
- `book.html` — QR card landing page (roadchanger.com/book)
- `review/` — Short link that redirects straight to the Google review form (roadchanger.com/review)
- `reviews/` — Selected client reviews, quoted from Google (roadchanger.com/reviews)
- `projects/` — Write-ups of individual events (roadchanger.com/projects)
- `images/` — Put your photos here (see below)

---

## Adding your photos

Save these files in the `images/` folder:

| Filename | Used on | Notes |
|---|---|---|
| `hero.jpg` | Homepage hero | Portrait format, you performing |
| `about.jpg` | About section | Portrait or square, natural shot |
| `book.jpg` | Book page | Square format works best |

Then uncomment the `<img>` tags in each file (remove the `<!-- -->` comment markers).

---

## Reviews

Reviews are collected in the **Google Business Profile** — not on this site. There is no
database, no sign-in and no Firebase any more.

- `review/index.html` redirects visitors straight to the Google review form.
  The link appears three times in that file (meta refresh, button, JS) — keep them identical.
- `reviews/index.html` shows selected reviews as **static HTML**. Never use an embedded
  Google/Trustpilot widget: those load via JS in an iframe and AI crawlers cannot read them.
  Copy each review verbatim and also add it to the JSON-LD block in that file's `<head>`.

See `CLAUDE.md` in the repo root for the exact steps.

---

## Going live on Vercel (free, ~10 min)

1. Go to https://vercel.com and sign up (free, use GitHub)
2. Click "Add New Project" → "Upload" (drag your whole roadchanger folder)
3. Click Deploy — your site goes live on a `.vercel.app` URL instantly

### Connect your roadchanger.com domain

4. In Vercel: go to your project → Settings → Domains → Add `roadchanger.com`
5. Vercel shows you DNS records to add (usually 2 records)
6. Log in to wherever you bought `roadchanger.com` (the domain registrar)
7. Go to DNS settings and add those records
8. Wait 10–30 min → your site is live at roadchanger.com ✅

---

## Adding a 60-second audio sample (book page)

1. Export a 60-second clip from one of your sets as `sample.mp3`
2. Put it in an `audio/` folder
3. In `book.html` find the comment `// Add your audio file:` and uncomment that line

---

## Questions?
Email: e.asmanis@gmail.com
