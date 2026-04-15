# Roadchanger Website

## Files
- `index.html` — Main homepage (roadchanger.com)
- `book.html` — QR card landing page (roadchanger.com/book)
- `reviews.html` — Reviews page with Google sign-in (roadchanger.com/reviews)
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

## Setting up the Reviews page (Google sign-in)

The reviews page uses Firebase (free). Do this once:

1. Go to https://console.firebase.google.com
2. Click "Add project" → name it `roadchanger` → click through
3. In the left menu go to **Authentication** → Get started → Google → Enable → Save
4. In the left menu go to **Firestore Database** → Create database → Start in test mode → Choose a region
5. Click the gear icon ⚙️ → Project settings → scroll down to "Your apps" → click `</>` (Web)
6. Register the app (any name) → copy the `firebaseConfig` object
7. Open `reviews.html` and replace the `firebaseConfig` section with your values

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
