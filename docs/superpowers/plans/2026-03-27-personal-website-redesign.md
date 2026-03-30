# Personal Website Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a static personal website (HTML/CSS) and deploy on GitHub Pages with custom domain www.claudiashi.com.

**Architecture:** Three HTML pages sharing one CSS file, deployed as static files via GitHub Pages. No build step, no JavaScript, no dependencies.

**Tech Stack:** HTML, CSS, GitHub Pages

**Spec:** `docs/superpowers/specs/2026-03-27-personal-website-redesign-design.md`

---

## File Structure

```
personal_website/
├── index.html          # Home page — bio, links
├── publications.html   # Publications list
├── cv.html             # CV download link
├── 404.html            # Custom 404 page
├── style.css           # Shared styles
├── CNAME               # GitHub Pages custom domain
└── assets/
    └── cv.pdf          # CV file (user provides)
```

---

### Task 1: Initialize Git Repo

**Files:**
- Create: `.gitignore`, `CNAME`

- [ ] **Step 1: Initialize repo**

```bash
cd ~/personal_website
git init
```

- [ ] **Step 2: Create .gitignore**

```
.DS_Store
```

- [ ] **Step 3: Create CNAME file**

```
www.claudiashi.com
```

- [ ] **Step 4: Commit**

```bash
git add .gitignore CNAME
git commit -m "init: repo with CNAME for GitHub Pages"
```

---

### Task 2: Create shared stylesheet

**Files:**
- Create: `style.css`

- [ ] **Step 1: Write style.css**

```css
/* Reset */
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Base */
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  color: #1a1a1a;
  background: #ffffff;
  line-height: 1.6;
  font-size: 17px;
}

a {
  color: #2563eb;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

/* Layout */
.container {
  max-width: 700px;
  margin: 0 auto;
  padding: 2rem 1.5rem;
}

/* Header */
header {
  padding: 2rem 0 1rem;
  border-bottom: 1px solid #e5e5e5;
  margin-bottom: 2rem;
}

header h1 {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

header h1 a {
  color: #1a1a1a;
}

nav {
  display: flex;
  gap: 1.5rem;
}

nav a {
  color: #666;
  font-size: 0.95rem;
}

nav a:hover {
  color: #1a1a1a;
}

nav a.active {
  color: #1a1a1a;
  font-weight: 500;
}

/* Main content */
main {
  min-height: 60vh;
}

/* Home page */
.bio {
  font-size: 1.05rem;
  line-height: 1.7;
}

.bio p {
  margin-bottom: 1rem;
}

.links {
  list-style: none;
  display: flex;
  gap: 1.5rem;
  margin-top: 1.5rem;
  flex-wrap: wrap;
}

.links a {
  font-size: 0.95rem;
}

/* Publications */
.pub-list {
  list-style: none;
}

.pub-list li {
  margin-bottom: 1.5rem;
}

.pub-title {
  font-weight: 500;
}

.pub-authors {
  color: #666;
  font-size: 0.95rem;
}

.pub-venue {
  color: #666;
  font-size: 0.9rem;
  font-style: italic;
}

/* CV */
.cv-link {
  display: inline-block;
  margin-top: 1rem;
  padding: 0.6rem 1.2rem;
  border: 1px solid #2563eb;
  border-radius: 4px;
  font-size: 0.95rem;
}

.cv-link:hover {
  background: #2563eb;
  color: #fff;
  text-decoration: none;
}

/* Page title */
.page-title {
  margin-bottom: 1.5rem;
  font-size: 1.2rem;
}

/* Footer */
footer {
  margin-top: 3rem;
  padding-top: 1.5rem;
  border-top: 1px solid #e5e5e5;
  color: #999;
  font-size: 0.85rem;
}

/* Responsive */
@media (max-width: 600px) {
  .container {
    padding: 1.5rem 1rem;
  }

  header h1 {
    font-size: 1.3rem;
  }

  nav {
    gap: 1rem;
  }
}
```

- [ ] **Step 2: Commit**

```bash
git add style.css
git commit -m "feat: add shared stylesheet"
```

---

### Task 3: Create Home page

**Files:**
- Create: `index.html`

- [ ] **Step 1: Write index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Claudia Shi</title>
  <meta name="description" content="Claudia Shi — Research Scientist at Meta FAIR working on alignment, safety, and governance of large language models.">
  <meta property="og:title" content="Claudia Shi">
  <meta property="og:description" content="Research Scientist at Meta FAIR working on alignment, safety, and governance of large language models.">
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>C</text></svg>">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <header>
      <h1><a href="/">Claudia Shi</a></h1>
      <nav>
        <a href="/" class="active">Home</a>
        <a href="/publications.html">Publications</a>
        <a href="/cv.html">CV</a>
      </nav>
    </header>
    <main>
      <div class="bio">
        <p>I am a Research Scientist at <a href="https://ai.meta.com/research/" target="_blank" rel="noopener">Meta FAIR</a> in New York City, on the AI and Society team.</p>
        <p>My research focuses on the alignment, safety, and governance of large language models.</p>
        <p>I received my PhD in Computer Science from <a href="https://www.columbia.edu" target="_blank" rel="noopener">Columbia University</a>, advised by <a href="http://www.cs.columbia.edu/~blei/" target="_blank" rel="noopener">David Blei</a>.</p>
      </div>
      <ul class="links">
        <li><a href="mailto:YOUR_EMAIL@example.com">Email</a></li>
        <li><a href="https://twitter.com/causalclaudia" target="_blank" rel="noopener">Twitter</a></li>
        <li><a href="https://github.com/YOUR_GITHUB" target="_blank" rel="noopener">GitHub</a></li>
        <li><a href="https://scholar.google.com/citations?user=YOUR_ID" target="_blank" rel="noopener">Google Scholar</a></li>
      </ul>
    </main>
    <footer>
      &copy; 2026 Claudia Shi
    </footer>
  </div>
</body>
</html>
```

> **Note:** Replace `YOUR_EMAIL@example.com`, `YOUR_GITHUB`, and `YOUR_ID` with your actual email, GitHub username, and Google Scholar ID.

- [ ] **Step 2: Open in browser to verify**

```bash
open index.html
```

Check: header, nav, bio text, links, footer all render correctly.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add home page"
```

---

### Task 4: Create Publications page

**Files:**
- Create: `publications.html`

- [ ] **Step 1: Write publications.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Publications — Claudia Shi</title>
  <meta name="description" content="Publications by Claudia Shi on LLM alignment, safety, causal inference, and machine learning.">
  <meta property="og:title" content="Publications — Claudia Shi">
  <meta property="og:description" content="Publications by Claudia Shi.">
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>C</text></svg>">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <header>
      <h1><a href="/">Claudia Shi</a></h1>
      <nav>
        <a href="/">Home</a>
        <a href="/publications.html" class="active">Publications</a>
        <a href="/cv.html">CV</a>
      </nav>
    </header>
    <main>
      <h2 class="page-title">Publications</h2>
      <ul class="pub-list">
        <li>
          <div class="pub-title"><a href="https://arxiv.org/abs/XXXX.XXXXX" target="_blank" rel="noopener">Paper Title Here</a></div>
          <div class="pub-authors">Author 1, Author 2, Claudia Shi, Author 3</div>
          <div class="pub-venue">Conference/Journal Name, 2025</div>
        </li>
        <!-- Copy the <li> block above for each publication -->
      </ul>
    </main>
    <footer>
      &copy; 2026 Claudia Shi
    </footer>
  </div>
</body>
</html>
```

> **Note:** Replace the placeholder `<li>` with your actual publications, newest first. Copy the `<li>` block for each paper.

- [ ] **Step 2: Open in browser to verify**

```bash
open publications.html
```

- [ ] **Step 3: Commit**

```bash
git add publications.html
git commit -m "feat: add publications page"
```

---

### Task 5: Create CV page

**Files:**
- Create: `cv.html`, `assets/` directory

- [ ] **Step 1: Create assets directory**

```bash
mkdir -p assets
```

- [ ] **Step 2: Write cv.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CV — Claudia Shi</title>
  <meta name="description" content="Curriculum Vitae for Claudia Shi, Research Scientist at Meta FAIR.">
  <meta property="og:title" content="CV — Claudia Shi">
  <meta property="og:description" content="Curriculum Vitae for Claudia Shi.">
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>C</text></svg>">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <header>
      <h1><a href="/">Claudia Shi</a></h1>
      <nav>
        <a href="/">Home</a>
        <a href="/publications.html">Publications</a>
        <a href="/cv.html" class="active">CV</a>
      </nav>
    </header>
    <main>
      <h2 class="page-title">Curriculum Vitae</h2>
      <p>Download my CV as a PDF:</p>
      <a class="cv-link" href="assets/cv.pdf" target="_blank" rel="noopener">Download CV (PDF)</a>
    </main>
    <footer>
      &copy; 2026 Claudia Shi
    </footer>
  </div>
</body>
</html>
```

> **Note:** Place your CV PDF at `assets/cv.pdf`.

- [ ] **Step 3: Commit**

```bash
git add cv.html assets/
git commit -m "feat: add CV page"
```

---

### Task 6: Create 404 page

**Files:**
- Create: `404.html`

- [ ] **Step 1: Write 404.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Not Found — Claudia Shi</title>
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>C</text></svg>">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <header>
      <h1><a href="/">Claudia Shi</a></h1>
      <nav>
        <a href="/">Home</a>
        <a href="/publications.html">Publications</a>
        <a href="/cv.html">CV</a>
      </nav>
    </header>
    <main>
      <h2 class="page-title">Page not found</h2>
      <p>The page you're looking for doesn't exist. <a href="/">Go home</a>.</p>
    </main>
    <footer>
      &copy; 2026 Claudia Shi
    </footer>
  </div>
</body>
</html>
```

- [ ] **Step 2: Commit**

```bash
git add 404.html
git commit -m "feat: add custom 404 page"
```

---

### Task 7: Deploy to GitHub Pages

- [ ] **Step 1: Create GitHub repo**

```bash
gh repo create personal-website --public --source=. --push
```

> If you don't have `gh` CLI, create the repo at github.com/new, then:
> ```bash
> git remote add origin git@github.com:YOUR_USERNAME/personal-website.git
> git push -u origin main
> ```

- [ ] **Step 2: Enable GitHub Pages**

Go to: `github.com/YOUR_USERNAME/personal-website/settings/pages`
- Source: Deploy from a branch
- Branch: `main`, folder: `/ (root)`
- Click Save

- [ ] **Step 3: Configure DNS at your domain registrar**

Add these DNS records:

| Type  | Name | Value                    |
|-------|------|--------------------------|
| CNAME | www  | YOUR_USERNAME.github.io  |
| A     | @    | 185.199.108.153          |
| A     | @    | 185.199.109.153          |
| A     | @    | 185.199.110.153          |
| A     | @    | 185.199.111.153          |

- [ ] **Step 4: Enable HTTPS**

After DNS propagates (may take up to 24 hours), go back to GitHub Pages settings and check "Enforce HTTPS".

- [ ] **Step 5: Verify**

Visit `https://www.claudiashi.com` and confirm all pages load correctly.

---

### Task 8: User content — populate real data

These are manual steps for you:

- [ ] **Step 1:** Update `index.html` — replace `YOUR_EMAIL`, `YOUR_GITHUB`, `YOUR_ID` with real values
- [ ] **Step 2:** Update `publications.html` — add your actual publications
- [ ] **Step 3:** Drop your CV PDF at `assets/cv.pdf`
- [ ] **Step 4:** Commit and push

```bash
git add -A
git commit -m "content: add publications, links, and CV"
git push
```

---

### Task 9: Cancel Owlstown subscription

- [ ] After verifying the new site works at `www.claudiashi.com`, cancel your Owlstown plan.
