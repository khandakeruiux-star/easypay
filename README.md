# EasyPay

An AI-powered personal finance dashboard — budgeting, goals, analytics, accounts, subscriptions and an AI financial advisor, in one product. Built with React + Vite, Tailwind CSS, Recharts, and lucide-react. All data in this build is realistic mock data (no backend, no real bank connections).

## Project structure

```
easypay/
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
├── vercel.json
├── .gitignore
├── README.md
└── src/
    ├── main.jsx        # React entry — mounts <App /> into #root
    ├── App.jsx         # The entire application: all pages, components, mock data
    └── index.css       # Tailwind + custom grid/hover CSS
```

Every page (Overview, Transactions, Budget, Goals, Analytics, Subscriptions, AI Advisor, Accounts, Profile, Settings, Help) lives in `src/App.jsx`. Nothing else needs to be wired up.

---

## Part 1 — Push this project to your GitHub repo

You already created the repo at:
`https://github.com/khandakeruiux-star/easypay.git`

Below, "the project folder" means the folder you get after unzipping the file I gave you (it should contain `package.json`, `index.html`, `src/`, etc. directly inside it — not one more folder deep).

**1. Open a terminal and go into the project folder**

```bash
cd path/to/easypay
```

(Replace `path/to/easypay` with wherever you unzipped it — e.g. `cd ~/Downloads/easypay`.)

**2. Turn this folder into a git repository**

```bash
git init
```

**3. Stage and commit all the files**

```bash
git add .
git commit -m "Initial commit"
```

**4. Point it at your GitHub repo**

```bash
git branch -M main
git remote add origin https://github.com/khandakeruiux-star/easypay.git
```

**5. Push it up**

```bash
git push -u origin main
```

If GitHub asks you to log in, follow its prompts (browser login, or a personal access token if it asks for a password — GitHub stopped accepting plain passwords for this a while ago, so if a password fails, search "GitHub personal access token" and use that instead).

If it says something like `error: failed to push... fetch first` (this can happen if the repo already has a README or license file created on GitHub's website), run this instead:

```bash
git pull origin main --allow-unrelated-histories
git push -u origin main
```

That's it — refresh your GitHub repo page and you should see all the files.

---

## Part 2 — Run it locally (optional, but good to check first)

```bash
npm install
npm run dev
```

Open the URL it prints (usually `http://localhost:5173`) and you should see EasyPay running.

To build the production version:

```bash
npm run build
npm run preview
```

---

## Part 3 — Deploy to Vercel

1. Go to [vercel.com](https://vercel.com) and sign up / log in — the easiest way is "Continue with GitHub" so it can see your repos.
2. Click **Add New → Project**.
3. Find and select your `easypay` repo, then click **Import**.
4. Vercel will auto-detect this as a Vite project. You shouldn't need to change anything — the settings below are already set in this project's `vercel.json`, but for reference:
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
   - **Install Command:** `npm install`
5. Click **Deploy** and wait a minute or two.
6. When it finishes, Vercel gives you a live URL (something like `easypay.vercel.app`) — that's your app, live on the internet.

No environment variables are needed — everything in this app is local mock data.

From now on, every time you push new commits to the `main` branch on GitHub, Vercel will automatically redeploy the site.

---

## Notes

- This is a front-end prototype: there's no backend, authentication, or database. Refreshing the page resets any in-memory changes (form edits, toggles, etc.) back to the mock defaults.
- If you make changes in Claude later and want to update your live site, just replace the files in your local project folder with the new ones, then run:
  ```bash
  git add .
  git commit -m "Update from Claude"
  git push
  ```
  Vercel will pick up the push and redeploy automatically.
