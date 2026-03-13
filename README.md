# Architecture Notes — Blog

Personal blog built with Hugo and deployed to GitHub Pages.

## One-Time Setup (15 minutes)

### Step 1: Create the GitHub Repository

1. Go to https://github.com/new
2. Repository name: `rgk-ai.github.io` (must match your username exactly)
3. Set to **Public**
4. Do NOT initialize with README (we already have one)
5. Click **Create repository**

### Step 2: Push This Code

```bash
cd rgk-ai.github.io
git init
git add .
git commit -m "Initial blog setup"
git branch -M main
git remote add origin https://github.com/rgk-ai/rgk-ai.github.io.git
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
2. Under "Build and deployment", set Source to **GitHub Actions**
3. That's it — the workflow file (.github/workflows/hugo.yml) handles the rest

### Step 4: Wait ~2 minutes

GitHub Actions will build and deploy your site. Check the Actions tab for progress.

Your site will be live at: **https://rgk-ai.github.io**

---

## How to Write a New Post

### Option A: From your terminal (if Hugo is installed locally)

```bash
hugo new posts/my-new-post.md
```

This creates a new file in `content/posts/` with the front matter pre-filled. Edit it, then push.

### Option B: Just create a markdown file manually

Create a new file in `content/posts/` with this template:

```markdown
---
title: "Your Post Title"
date: 2026-03-15
draft: true
tags: ["MCP", "Agentic AI"]
summary: "One sentence summary that appears on the home page."
categories: ["Architecture"]
---

Your content here. Write in regular markdown.

## Subheadings work like this

And code blocks work like this:

\```python
def hello():
    print("hello world")
\```
```

### Publishing a Post

Posts with `draft: true` won't appear on the live site. When you're ready to publish:

1. Change `draft: true` to `draft: false`
2. Commit and push:

```bash
git add .
git commit -m "Publish: Your Post Title"
git push
```

3. GitHub Actions builds and deploys automatically (~2 minutes)

---

## Customization

### Update your info
- Edit `hugo.toml` to update your name, LinkedIn URL, tagline, and about text
- Edit `content/about.md` for your full about page

### Add a custom domain later (optional)
1. Buy a domain from any registrar
2. Add a `CNAME` file in `static/` containing your domain: `echo "yourdomain.com" > static/CNAME`
3. Configure DNS: CNAME record pointing to `rgk-ai.github.io`
4. Update `baseURL` in `hugo.toml`
5. In GitHub repo Settings → Pages, enter your custom domain

---

## Project Structure

```
rgk-ai.github.io/
├── content/
│   ├── about.md              ← Your about page
│   └── posts/                ← All blog posts go here
│       └── your-post.md
├── themes/architect/         ← Custom theme (clean, professional)
│   ├── layouts/
│   │   ├── _default/
│   │   │   ├── baseof.html   ← Base template
│   │   │   ├── list.html     ← Post listing
│   │   │   └── single.html   ← Individual post
│   │   ├── partials/
│   │   │   ├── header.html
│   │   │   └── footer.html
│   │   └── index.html        ← Home page
│   └── static/css/
│       └── style.css         ← All styles
├── hugo.toml                 ← Site configuration
├── .github/workflows/
│   └── hugo.yml              ← Auto-deploy on push
└── README.md
```

## Cross-Posting to LinkedIn

When a post is polished and ready for visibility:

1. Go to LinkedIn → Write Article
2. Copy your post content (reformat as needed)
3. Add "Originally published at https://rgk-ai.github.io/posts/your-post/"
4. This gives you the dual benefit: portfolio on your site, visibility on LinkedIn
