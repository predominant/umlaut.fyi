# ümlaüt.fÿi

Converts any input text to its umlaut form instantly, in the browser. No server, no tracking, no signup.

**Live site:** https://umlaut.fyi

---

## How it works

| Input | Output |
|-------|--------|
| a, e, i, o, u, y | ä, ë, ï, ö, ü, ÿ |
| A, E, I, O, U, Y | Ä, Ë, Ï, Ö, Ü, Ÿ |
| Everything else | unchanged |

All processing is client-side JavaScript. Nothing leaves your browser.

---

## Hosting on GitHub Pages (step-by-step)

### 1. Prerequisites

- A free account on [github.com](https://github.com)
- Git installed locally (`git --version`)
- The domain `umlaut.fyi` pointed at GitHub (see DNS section below)

---

### 2. Create the repository

1. Go to https://github.com/new
2. Name the repository **`umlaut.fyi`**
3. Leave it **Public**
4. Do **not** check "Add a README" (the repo already has one)
5. Click **Create repository**

---

### 3. Push the code

In this project directory run:

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/<your-username>/umlaut.fyi.git
git push -u origin master
```

Replace `<your-username>` with your GitHub username.

---

### 4. Enable GitHub Pages

1. In the repository, go to **Settings → Pages**
2. Under **Source**, choose **GitHub Actions**
3. The `deploy.yml` workflow runs automatically on every push to `main`

After the first push the Actions tab will show the deployment progress. The site will be live at `https://<your-username>.github.io/umlaut.fyi/` within ~1 minute.

---

### 5. Add a custom domain (umlaut.fyi)

#### A. In GitHub

1. Go to **Settings → Pages → Custom domain**
2. Enter `umlaut.fyi` and click **Save**
3. Check **Enforce HTTPS** once the certificate is issued (~5 minutes)

The `CNAME` file already contains `umlaut.fyi` so GitHub will detect it automatically.

#### B. In your DNS provider

Add these records at your domain registrar/DNS host:

| Type  | Name  | Value                  |
|-------|-------|------------------------|
| A     | @     | 185.199.108.153        |
| A     | @     | 185.199.109.153        |
| A     | @     | 185.199.110.153        |
| A     | @     | 185.199.111.153        |
| AAAA  | @     | 2606:50c0:8000::153    |
| AAAA  | @     | 2606:50c0:8001::153    |
| AAAA  | @     | 2606:50c0:8002::153    |
| AAAA  | @     | 2606:50c0:8003::153    |
| CNAME | www   | `<your-username>`.github.io |

DNS propagation typically takes a few minutes to a few hours depending on your provider.

> **Verify DNS** with: `dig umlaut.fyi +noall +answer`

---

### 6. Verify the deployment

- GitHub Actions tab: green checkmark on the `Deploy to GitHub Pages` workflow
- Visit https://umlaut.fyi (or the `.github.io` URL while DNS propagates)

---

## Local development

No build step required — open `index.html` directly in any browser:

```bash
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

Or serve it locally:

```bash
npx serve .              # Node.js
python3 -m http.server   # Python
```

---

## Project structure

```
umlaut.fyi/
├── index.html              # Entire application (HTML + CSS + JS)
├── CNAME                   # Custom domain for GitHub Pages
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions deployment workflow
└── README.md
```
