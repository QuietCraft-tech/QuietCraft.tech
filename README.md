# QuietCraft.tech

Landing page for [quietcraft.tech](https://quietcraft.tech). Pure HTML/CSS/JS — no build step, no dependencies.

---

## Deploy to Netlify

1. Go to [app.netlify.com](https://app.netlify.com) → **Add new site → Import an existing project**
2. Connect GitHub and select this repo
3. Build settings (Netlify should auto-detect these from `netlify.toml`):
   - **Build command:** *(leave empty)*
   - **Publish directory:** `.`
4. Click **Deploy site**

Every push to `main` triggers an automatic redeploy.

---

## Custom domain

In Netlify: **Site configuration → Domain management → Add custom domain** → enter `quietcraft.tech`.

Netlify will show you the DNS records to add. Typically:
- `CNAME www` → `your-site-name.netlify.app`
- `A @` → Netlify's load balancer IP (shown in the panel)

Enable **Force HTTPS** once DNS propagates (usually a few minutes).

---

## Waitlist form

The waitlist form already has `data-netlify="true"`. Netlify detects this on first deploy and captures submissions automatically — nothing to configure.

To see submissions: **Netlify dashboard → Forms → waitlist**

To get email notifications: **Forms → waitlist → Form notifications → Add notification → Email**

---

## Writing a blog post

### Step 1 — Copy the template

```
cp blog/template.html blog/posts/your-post-slug.html
```

Use lowercase letters and hyphens. Example: `my-thoughts-on-transcription.html`

### Step 2 — Fill in the EDIT: markers

Open the new file and search for `EDIT:`. There are markers for:

| Marker | What to fill in |
|---|---|
| Page `<title>` | Post title — Journal |
| Meta description | 1–2 sentence summary for search engines |
| `article-tag` | Category: `Studio`, `Product`, `Craft`, `Process`, `Research` |
| `article-title` | Post title |
| `datetime` | Machine date: `2026-09-01` |
| Visible date | Human date: `1 September 2026` |
| Reading time | Estimate: `3 min read`, `5 min read`, etc. |
| Author name | Your name |
| `article-body` | Your post content (see elements below) |
| Prev / Next nav | Links to adjacent posts (remove if they don't exist yet) |

### Step 3 — Write the post body

Inside `<article class="article-body">`, use standard HTML:

| Element | Use |
|---|---|
| `<p>` | Paragraphs |
| `<h2>` `<h3>` | Section headings |
| `<blockquote><p>…</p></blockquote>` | Pull quote |
| `<ul>` `<ol>` | Lists |
| `<a href="…">` | Links |
| `<strong>` `<em>` | Bold / italic |
| `<hr>` | Section break |
| `<code>` | Inline code |
| `<pre><code>…</code></pre>` | Code block |
| `<img src="…" alt="…">` | Images — put image files in `blog/img/` |

### Step 4 — Add a card to the journal listing

Open `blog/index.html`. Find the section with `.post-card` blocks. Copy one and paste it **above** the others (newest first). Update:
- `href` — path to your new post file
- `aria-label` — "Read: Your Post Title"
- `.post-card-tag` — same category tag as in the post
- `.post-card-title` — post title
- `.post-card-excerpt` — 2–3 sentence summary
- `.post-card-date` — visible date

### Step 5 — Commit and push

```
git add .
git commit -m "Add post: your post title"
git push
```

Netlify redeploys automatically. The post is live in ~30 seconds.

---

## Site structure

```
/
├── netlify.toml          ← build + headers config
├── index.html            ← landing page
├── css/
│   ├── main.css          ← shared: nav, footer, fonts, animations
│   └── blog.css          ← journal: article layout, post cards, prose
└── blog/
    ├── index.html        ← journal listing (add post cards here)
    ├── template.html     ← copy this to create a new post
    └── posts/
        └── *.html        ← individual posts
```

---

## Contact

[hello@quietcraft.tech](mailto:hello@quietcraft.tech)
