# Deployment guide

Two options. Pick one.

---

## Option 1 — Netlify Drop (30 seconds, no account needed to start)

1. **Drop your `resume.pdf`** into this folder. If you don't have a resume yet, do this step later — the site works without it, the button just 404s.
2. Open **https://app.netlify.com/drop** in your browser.
3. **Drag this entire folder** onto the drop zone.
4. Netlify gives you a URL like `https://random-name-123.netlify.app` — site is live immediately.
5. Click **Sign up** (top right) → sign up with email or GitHub → your site is now claimable.
6. **Site settings → Change site name** → set to `khwab-kalra` (or whatever's available) → URL becomes `https://khwab-kalra.netlify.app`.
7. To update later: edit files in this folder, then go to **Deploys** → drag the folder again. Netlify replaces the live site.

---

## Option 2 — GitHub Pages (permanent, clean URL, git history)

### One-time setup

1. **Create a GitHub account** if you don't have one: https://github.com/signup
2. **Create the repo**:
   - Go to https://github.com/new
   - **Repository name**: `khwabkalra.github.io`  ← must be exactly `<your-username>.github.io`
   - **Public** (required for free Pages)
   - **Do NOT** initialize with README, .gitignore, or license — we already have those
   - Click **Create repository**
3. GitHub will show you the repo URL. Copy it. It looks like:
   `https://github.com/khwabkalra/khwabkalra.github.io.git`

### Push the site

Open PowerShell in this folder and run:

```powershell
cd C:\Users\khwab\.claude\projects\C--Windows-System32\personal-site

# configure git (only if you've never used git before on this machine)
git config --global user.name "Khwab Kalra"
git config --global user.email "your-github-email@example.com"

# initialize and push
git init
git add .
git commit -m "Initial site deploy"

# add the remote — REPLACE with your actual repo URL
git remote add origin https://github.com/khwabkalra/khwabkalra.github.io.git
git branch -M main
git push -u origin main
```

If GitHub asks you to authenticate, sign in. On Windows you may need a **Personal Access Token** (GitHub no longer accepts passwords for git push). To make one:

1. https://github.com/settings/tokens → **Generate new token** → **Classic**
2. Note: "personal site"
3. Scopes: check **`repo`** only
4. Generate, **copy the token** (you only see it once)
5. When `git push` asks for password, paste the token instead

### Enable Pages

1. On your repo page → **Settings** → **Pages** (left sidebar)
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` · **Folder**: `/ (root)` → **Save**
4. Wait ~60 seconds. Your site is live at **`https://khwabkalra.github.io`**.

### Updating later

Edit files in this folder, then:

```powershell
git add .
git commit -m "what you changed"
git push
```

GitHub Pages rebuilds automatically in ~30 seconds.

---

## Recommendation

- **Just want to share a link right now?** → Netlify Drop. Live in 30 seconds.
- **Want a permanent home tied to your GitHub?** → GitHub Pages. Worth the 5 minutes.

You can do both. The repo is the source of truth; Netlify can deploy from the GitHub repo too if you want to go that route later.
