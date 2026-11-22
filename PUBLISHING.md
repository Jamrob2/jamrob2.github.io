# Weekly Budget Meal Planner: getting it on Google Play

The app is a Progressive Web App (PWA). It's an ordinary website that installs like an app and works offline. To get it on Google Play, you put the site online, then use the free **PWABuilder** tool to wrap it in an Android package (`.aab`) that you upload to Play.

You don't need Android Studio or any coding.

---

## What's in this folder

| File | What it's for |
|---|---|
| `index.html` | The whole app |
| `manifest.webmanifest` | App name, icons and colours. Android reads this |
| `sw.js` | Lets the app work offline |
| `icons/` | App icons, plus the **Play Store icon (512×512)** and **feature graphic (1024×500)** |
| `privacy.html` | Privacy policy. Google requires one. **Fill in [YOUR NAME], [YOUR EMAIL] and [DATE]** |
| `.well-known/` | Where `assetlinks.json` goes in step 3 |
| `.nojekyll` | Makes GitHub Pages serve the `.well-known` folder. Don't delete it |

---

## Step 1: Put it online (free, about 15 minutes)

GitHub Pages is the easiest free host.

1. Make a free account at **github.com**.
2. Create a new **public** repository named exactly **`YOUR-USERNAME.github.io`**. The name matters: it puts the files at the root of your site, which the Android link file in step 3 needs.
3. Click **Add file → Upload files** and drag in **everything in this folder**, including the `.well-known` folder and `.nojekyll`. Commit.
4. Go to **Settings → Pages** and make sure it's deploying from the `main` branch.
5. After a minute or two, open `https://YOUR-USERNAME.github.io`. The app should load.
6. On your Android phone, open that link in Chrome and tap **⋮ → Add to Home screen / Install app**. That's the app. Test it for a week.

> If you'd rather use your own domain (e.g. `weeklybudgetmeals.ca`), you can point it at GitHub Pages later. Just keep the files at the root.

## Step 2: Make the Android package (PWABuilder)

1. Go to **pwabuilder.com** and paste your site address.
2. It checks the app. The manifest, service worker and icons are already set up.
3. Click **Package for stores → Android → Generate package**.
   - **Package ID:** something like `ca.yourname.weeklybudgetmeals`. **You can never change this after publishing.**
   - **App name:** Weekly Budget Meal Planner · **Short name:** Meal Planner
   - Leave signing on **"New"** so it creates a signing key for you.
4. Download the zip. It contains:
   - the `.aab` file you upload to Play
   - a **signing key file + passwords**. **Back these up somewhere safe** (USB stick and cloud). If you lose them you can't update your app.
   - an **`assetlinks.json`** file

> **Check before uploading:** Google Play requires new apps and updates to target **Android 16 (API level 36)** from August 31, 2026. PWABuilder has had a lag on this before. If Play Console rejects the upload for target API level, look for an updated PWABuilder release or an "extension" option in Play Console.

## Step 3: Link the app to your site

1. Upload PWABuilder's `assetlinks.json` into the `.well-known` folder of your GitHub repository.
2. Check that `https://YOUR-USERNAME.github.io/.well-known/assetlinks.json` opens and shows the file.
3. After you upload the app to Play (step 4), go to **Play Console → Setup → App signing** and copy the **SHA-256 fingerprint** of the *App signing key*. Add it to `assetlinks.json` alongside the one PWABuilder put there, so the file has both fingerprints, and upload again.

Without this, the app still works but shows a browser address bar at the top.

## Step 4: Google Play Console

1. Sign up at **play.google.com/console**. There's a one-time **US$25** fee and ID verification.
2. **New personal accounts must run a closed test first:** at least **12 testers** opted in for **14 days in a row** before you can apply to publish publicly. Line up 15–20 friends, family or co-workers with Android phones before you start. Organization accounts (which need a D-U-N-S number) are exempt.
3. **Create app** → name *Weekly Budget Meal Planner* → App → Free or Paid.
   - **Decide free or paid now:** a free app can't later be changed to paid. If you might charge, either start paid or go free and add an optional paid upgrade later.
   - To charge, you'll set up a **payments profile** (merchant account). Google keeps a service fee on each sale. Check the current rate in Play Console.
4. Fill in the **App content** section:
   - **Privacy policy URL:** `https://YOUR-USERNAME.github.io/privacy.html`
   - **Data safety:** the app doesn't collect or share user data, and everything is stored on the device.
   - **Ads:** No · **Target audience:** 18+ (simplest) · **Content rating:** answer the questionnaire (no objectionable content)
5. **Store listing:** use the text below, the 512 icon and the 1024×500 feature graphic from `icons/`. Take at least **2 phone screenshots** from the installed app (plan, groceries, recipes, prep).
6. **Testing → Closed testing:** upload the `.aab`, add your testers' Gmail addresses, send them the opt-in link. Wait 14 days and make sure they actually open the app.
7. **Apply for production access**, then publish.

---

## Store listing text (edit as you like)

**App name (30 max):** Weekly Budget Meal Planner

**Short description (80 max):**
Plan a week of meals under your grocery budget, with a priced grocery list.

**Full description:**
Stop asking "what's for supper?" and stop blowing the grocery budget.

Tell Weekly Budget Meal Planner your weekly budget, your store and what your family likes. It plans the whole week of breakfasts, lunches, dinners, snacks and desserts and keeps it under budget. Then it hands you the grocery list with the total already worked out.

• Stays under your budget. Swap any meal and the total updates.
• Priced grocery list, grouped by aisle in your store's order.
• Compare stores and split your list so every item comes from wherever it's cheapest. Add flyer prices for real savings.
• Over 115 family-friendly recipes, including Canadian classics like shepherd's pie, tourtière, chicken pot pie, soo guy, honey garlic ribs, butter tarts and more.
• Your tastes: like or dislike cuisines, proteins and any fruit or veggie. Picky eaters welcome.
• Goals: high protein, low carb, quick prep, comfort food, macro targets and more.
• No repeats, or batch cook to save time.
• Cook once, eat twice: leftovers go in a freezer tracker and get planned in for free.
• Prep day game plan with thaw reminders.
• Shopping mode with big text and one-tap check-off.
• Rate meals so the planner learns your favourites. Re-use past weeks.
• Add your own recipes.
• No account, no ads, no tracking. Your data stays on your phone.

Prices are estimates. Enter your store's prices for exact totals.

**Category:** Food & Drink · **Tags:** meal planner, budget, grocery list

---

## Before you charge money: worth fixing

- **Store prices are estimates.** The app ships with my rough Ontario price estimates, and store names are only labels for "cheaper / pricier than average". If you sell it, keep the "estimates" wording visible (it's in the app and the listing), or remove the per-store price levels and let people enter their own.
- **Ontario/Canada focus.** The prices and stores are Canadian. Either list the app in Canada only to start, or add other regions later.
- **Data lives on the phone.** If someone uninstalls the app, their data goes too. Back up / Restore is in Settings, so mention it in your listing or FAQ.
- **Updating the app:** change `index.html` in your GitHub repository. Installed apps pick up the new version the next time they're opened online, with no new Play upload needed (unless you change the name, icon or package settings).

---

## Weekly deals feed (optional)

The app reads `deals.json` from the same site each time it opens and shows those deals to everyone, marked "weekly feed". The format is:

```json
[
  { "item": "chicken breast|g", "store": "walmart", "price": 8.88, "pack": 1000, "until": "2026-11-26" },
  { "item": "bacon|g", "store": "nofrills", "price": 3.97, "pack": 375, "until": "2026-11-26" }
]
```

- `item` is the ingredient name in lower case, a `|`, and its unit, as used in the recipes (e.g. `lean ground beef|g`, `eggs|pc`, `black beans|can`).
- `store` is one of `nofrills`, `foodbasics`, `freshco`, `walmart`, `gianttiger`, `independent`, `metro`, `sobeys`, `loblaws`.
- `price` is the sale price for `pack` units, and `until` is the last day of the sale. Expired deals are ignored.

Leave it as `[]` when there are no deals.
