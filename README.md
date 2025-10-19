# Hugo Projects Site

A minimal, modern Hugo site for listing personal tools.

## Project Structure

```
plusking.ir/
├── config.toml
├── content/
│   └── _index.md
├── data/
│   └── projects.yaml
├── layouts/
│   ├── _default/
│   │   ├── baseof.html
│   │   └── list.html
│   └── index.html
└── static/
    └── css/
        └── style.css
```

## Features

- Clean, minimal design with centered layout
- Automatic light/dark theme based on system preference
- Projects loaded from `data/projects.yaml` for easy editing
- Editable home page content via `content/_index.md`
- No external dependencies beyond Hugo
- Optimized for Cloudflare Pages deployment

## Local Development

1. Install Hugo: https://gohugo.io/installation/
2. Run the development server:
   ```bash
   hugo server -D
   ```
3. Open http://localhost:1313 in your browser

## Editing Content

### Update the home page intro

Edit `content/_index.md`:

```markdown
---
title: "Projects"
date: 2025-10-17
---

Your custom intro text here.
```

### Add or modify projects

Edit `data/projects.yaml`:

```yaml
- name: "Project Name"
  url: "https://example.com"
```

### Customize site settings

Edit `config.toml`:

```toml
baseURL = "https://plusking.ir/"
title = "Your Title"
[params]
  author = "Your Name"
```

## Deploy to Cloudflare Pages

### Method 1: Connect Git Repository

1. Push this project to GitHub/GitLab
2. Go to https://dash.cloudflare.com/
3. Navigate to **Workers & Pages** → **Create application** → **Pages**
4. Connect your Git repository
5. Configure build settings:
   - **Build command**: `hugo --minify`
   - **Build output directory**: `public`
   - **Environment variables**: Add `HUGO_VERSION` = `0.139.4` (or latest)
6. Click **Save and Deploy**

### Method 2: Direct Upload (wrangler CLI)

1. Install Wrangler:
   ```bash
   npm install -g wrangler
   ```

2. Build the site:
   ```bash
   hugo --minify
   ```

3. Deploy:
   ```bash
   wrangler pages deploy public --project-name=plusking
   ```

### Method 3: Manual Upload

1. Build the site locally:
   ```bash
   hugo --minify
   ```

2. Go to Cloudflare Dashboard → **Workers & Pages** → **Create application** → **Pages** → **Upload assets**

3. Upload the contents of the `public/` folder

## Customization

### Change colors

Edit `static/css/style.css` and modify the `:root` variables:

```css
:root {
    --bg-color: #ffffff;
    --text-color: #1a1a1a;
    --link-color: #0066cc;
}
```

### Add more sections

Create new sections by adding files to `content/`:

```bash
hugo new section-name/_index.md
```

## Hugo Version

This site is compatible with Hugo v0.100.0 and later. For Cloudflare Pages, set the `HUGO_VERSION` environment variable to ensure the correct version is used during build.

## License

This template is free to use and modify.
