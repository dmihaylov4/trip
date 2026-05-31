# 🏖 Group Trip Planner

An AI-powered tool for planning group trips. Paste any Airbnb or Booking.com listing and instantly get:

- **Per-person cost** breakdown (total + per night)
- **Beach distance** with color-coded indicator
- **Car rental estimate** based on group size
- **All-in cost** per person (accommodation + car)
- **Shared board** — every listing analyzed by anyone is saved at the bottom so the whole group can see what's been checked

---

## 🚀 Hosting on GitHub Pages (5 minutes)

### Option A — New repo from scratch

1. Go to [github.com/new](https://github.com/new)
2. Name it something like `trip-planner`
3. Set it to **Public**
4. Click **Create repository**
5. Upload `index.html` (drag and drop on the repo page)
6. Go to **Settings → Pages**
7. Under *Source*, choose **Deploy from a branch → main → / (root)**
8. Click **Save**
9. Wait ~60 seconds, then visit: `https://YOUR-USERNAME.github.io/trip-planner`

### Option B — GitHub Desktop

1. Clone or create a new repo locally
2. Drop `index.html` into the folder
3. Commit & push
4. Enable Pages as above

---

## ⚠️ API Key Note

This app calls the Anthropic API directly from the browser. For a **shared/public** deployment you have two options:

### Option 1 — Keep it private (simple)
Share the link only with your group. The API key is handled by Anthropic's claude.ai infrastructure if you exported this from there.

### Option 2 — Add your own key (if self-hosting)
If the app isn't working after deploying, open `index.html`, find the `fetch('https://api.anthropic.com/v1/messages'` call, and add your key:

```js
headers: {
  'Content-Type': 'application/json',
  'x-api-key': 'sk-ant-YOUR-KEY-HERE',
  'anthropic-version': '2023-06-01',
  'anthropic-dangerous-direct-browser-access': 'true'
},
```

Get a key at [console.anthropic.com](https://console.anthropic.com). Costs are minimal (~$0.003 per analysis).

---

## 💾 Data Storage

Listings are saved in **localStorage** — meaning each browser/device has its own board. For a truly shared board across all users, you'd need a small backend (Supabase free tier works great).

---

## 🛠 Customizing

- Change the default group size: find `let people = 8` in the script
- Change the default nights: find `let nights = 7`
- Cap on board history: find `if (board.length > 50)` — change `50` to whatever you want
