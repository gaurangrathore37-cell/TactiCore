# TactiCore — Understand the Game. Master the Tactics.

A responsive, multi-page football learning website. Each section is a separate HTML page so the whole site is not crammed onto one page.

## Pages
- `index.html` — home and navigation
- `learn.html` — football rules, positions, passing, defending and pressing
- `formations.html` — interactive formation selector
- `players.html` — searchable starter directory of 100 footballers
- `compare.html` — compare any two listed players by role and playing-style summary
- `quiz.html` — quiz with an online Wikipedia search-based question mode and fallback questions
- `creator.html` — Meet the Creator, with a Message the Creator email form
- `signin.html` — email magic-link sign-in, email/password sign-in and account creation through Supabase

## Publish on GitHub Pages (Android or computer)
1. Download and extract this project ZIP.
2. Open your GitHub repository and upload **all files and folders**, preserving the structure (`assets/` and `js/`).
3. Make sure `index.html` is in the repository root, not inside another nested folder.
4. Commit changes to the branch configured for GitHub Pages.
5. Open **Settings → Pages** and confirm the publishing source. Wait for the deployment, then refresh the live site.

## Turn on email sign-in with Supabase
This project is prefilled with the Supabase project URL previously provided for TactiCore. The public/anon key is deliberately a placeholder because it must be copied from your own Supabase dashboard.

1. Open Supabase Dashboard → your project → **Project Settings → API** (or API Keys, depending on dashboard layout).
2. Copy the **anon/public** key. Never use the `service_role` or secret key in a public website.
3. Edit `js/config.js` and replace `PASTE_YOUR_SUPABASE_ANON_PUBLIC_KEY_HERE` with that public key.
4. In Supabase → Authentication → Providers, enable **Email**.
5. Under Authentication URL configuration, add your exact GitHub Pages site URL to **Redirect URLs**. Example format: `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/`.
6. Commit the changed `js/config.js` and reload the site.
7. To allow password sign-up without confirmation, look for the email-confirmation setting in Supabase Authentication settings and disable it only if you understand the security trade-off. Otherwise users may need to confirm their email.

Without the public key, the sign-in page intentionally shows setup guidance and real authentication will not work. Do not put passwords or private service keys in source code.

## Fresh quiz questions: important limitation
The quiz requests live results from the public Wikipedia search API and turns the result titles into a topic-identification question. If the API is unavailable or the browser is offline, it uses the built-in fallback questions. A new question is attempted each time, but an online result is **not guaranteed** on every click. Wikipedia is a public knowledge source, not Google Search. Google does not offer unrestricted public Google Search scraping; do not build a site by scraping Google result pages. For higher-quality questions and verified answers, connect a licensed football trivia API or maintain your own reviewed question bank.

## Player comparison: important limitation
The site includes a starter directory of 100 players and compares brief editorial style descriptions. It does not fetch live stats, trophies, goals or season-by-season data, and it does not automatically determine who is better. Those features would need a football data API and appropriate attribution/licensing.

## Test checklist
- Open every page from the navigation.
- Search the player list for Ronaldo, Messi, or another name.
- Select two players from Compare.
- Change formations.
- Click New question in Quiz; try it online and offline.
- Open Meet the Creator and submit the form to open the email app.
- Add the Supabase public key and verify sign-in before publishing authentication as ready.

## Files
- `assets/style.css` — responsive styling
- `js/common.js` — navigation, footer and shared helpers
- `js/config.js` — Supabase public configuration
- `js/auth.js` — email authentication
- `js/formations.js` — formation visualiser
- `js/players-data.js` — player directory data
- `js/players.js` — directory search
- `js/compare.js` — player comparison
- `js/quiz.js` — online/fallback quiz
- `js/creator.js` — email contact form
