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
├── .npmrc
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

If you already pushed once before and are updating, just run:

```bash
git add .
git commit -m "Fix Vercel build"
git push
```

If `git push` complains the remote already has history you don't have locally (e.g. `fetch first`):

```bash
git pull origin main --allow-unrelated-histories
git push -u origin main
```

---

## Part 2 — Run it locally (optional, but good to check first)

```bash
npm install
npm run dev
```

Open the URL it prints (usually `http://localhost:5173`).

To build the production version:

```bash
npm run build
npm run preview
```

---

## Part 3 — Deploy to Vercel

1. Go to [vercel.com](https://vercel.com) and log in with "Continue with GitHub".
2. Click **Add New → Project**, select your `easypay` repo, click **Import**.
3. Vercel auto-detects this as a Vite project (settings are also pinned in `vercel.json`: build command `npm run build`, output directory `dist`).
4. Click **Deploy**.
5. You'll get a live link like `easypay.vercel.app`.

No environment variables are needed.

If you already have a Vercel project connected to this repo, pushing new commits to `main` triggers an automatic redeploy — you don't need to reconnect anything.

---

## Troubleshooting: "npm warn allow-scripts" / esbuild during Vercel build

If your Vercel build log shows something like:

```
npm warn allow-scripts 1 package has install scripts not yet covered by allowScripts:
npm warn allow-scripts   esbuild@0.21.5 (postinstall: node install.js)
```

That's npm refusing to automatically run a dependency's install script. It's a warning, not always a hard failure by itself — but `esbuild`'s postinstall script is what downloads the correct native binary for the build machine, and if it's skipped, the `vite build` step right after can fail because the `esbuild` binary is missing.

This project already includes two fixes for it:
- **`.npmrc`** with `ignore-scripts=false`, which explicitly tells npm to run install scripts.
- **`package.json`** pins `"engines": { "node": "20.x" }`, so Vercel uses a consistent, known-good Node version instead of whatever its current default happens to be.

If you still see this after redeploying with these files in place, check the rest of the build log for a line containing the word `Error` (search the page for "Error") — that's the actual failure reason, and it'll be below this warning, not in it.

---

## Notes

- This is a front-end prototype: there's no backend, authentication, or database. Refreshing the page resets any in-memory changes (form edits, toggles, etc.) back to the mock defaults.
- To update your live site after making changes: replace the files in your local project folder, then:
  ```bash
  git add .
  git commit -m "Update"
  git push
  ```
  Vercel redeploys automatically.
