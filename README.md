# My Blog

A warm, personal blog built with Astro, hosted free on GitHub Pages, with a browser-based editor (Decap CMS) so you never need to touch code to write.

## Setup (one-time, ~15 minutes)

### 1. Create a GitHub repo

- Go to github.com → New repository
- Name it `your-username.github.io` (for a root domain) or anything else (e.g. `blog`)
- Set it to **Public**

### 2. Push this code

```bash
cd blog
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

### 3. Enable GitHub Pages

- Go to your repo → Settings → Pages
- Under **Source**, select **GitHub Actions**
- Save. The first deploy will kick off automatically.

### 4. Update two files

In `astro.config.mjs`, update:
```js
site: 'https://YOUR-USERNAME.github.io',
base: '/YOUR-REPO-NAME',   // omit this line if repo is named your-username.github.io
```

In `public/admin/config.yml`, update:
```yaml
repo: YOUR-USERNAME/YOUR-REPO-NAME
```

Commit and push these changes.

### 5. Set up the CMS editor (Decap CMS)

- Go to github.com → Settings → Developer settings → OAuth Apps → New OAuth App
- Fill in:
  - Application name: `My Blog CMS`
  - Homepage URL: `https://your-username.github.io`
  - Authorization callback URL: `https://api.netlify.com/auth/done`
- Save and copy the **Client ID** and **Client Secret**

Then:
- Go to [app.netlify.com](https://app.netlify.com) (free account)
- Add new site → "Deploy manually" (just to get the OAuth proxy)
- Go to Site settings → Access control → OAuth → Install provider → GitHub
- Paste your Client ID and Secret

Now visit `https://your-username.github.io/admin` — you'll be able to log in with GitHub and write posts directly.

---

## Writing posts

1. Go to `yoursite.com/admin`
2. Log in with GitHub
3. Click "Thoughts" or "Projects" → New
4. Write, save, publish
5. Site rebuilds automatically in ~30 seconds

---

## Customising the design

All design lives in two files:
- `src/styles/global.css` — fonts, colors, typography
- `src/layouts/Base.astro` — header, footer, nav

Change `your name` in `Base.astro` to your actual name.
Update the bio on `src/pages/index.astro`.

---

## Structure

```
src/
  content/
    thoughts/     ← your essays (markdown files)
    projects/     ← your projects (markdown files)
  pages/
    index.astro   ← home page
    thoughts/     ← thoughts listing + post pages
    projects/     ← projects listing + post pages
  layouts/
    Base.astro    ← shared header/footer
  styles/
    global.css    ← all the design
public/
  admin/
    config.yml    ← CMS configuration
    index.html    ← CMS editor
```
