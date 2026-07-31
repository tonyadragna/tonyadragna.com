# tonyadragna.com Launch Guide

Your new site, rebuilt from the ground up. It's fast, secure, free to host, and
you can still write blog posts in a WordPress-style editor in your browser.

**What's inside:**

- Modern homepage: business leader + basketball coach, the 2026 sectional title,
  and all three kids (Gio, Luciana, and Enzo)
- "My Story" page combining your old About sections, updated for Keyholder Vacations
- All 4 blog posts migrated word-for-word with their original dates
- A browser-based post editor at `/admin` (Sveltia CMS)
- Redirects so every old WordPress URL still works (good for Google rankings)

---

## Going live (about 30 minutes, all free)

### Step 1: Put the code on GitHub

GitHub is where the site's files live. When you publish a post from the editor,
it saves the post here, and the site rebuilds automatically.

1. Create a free account at [github.com](https://github.com) (if you don't have one)
2. Create a new repository named `tonyadragna.com` (private is fine)
3. Upload this folder's contents to it. Easiest way if you don't use git:
   GitHub → your repo → "uploading an existing file" → drag the whole folder in.
   (Skip the `node_modules` and `dist` folders if present.)

### Step 2: Edit one line

In `public/admin/config.yml`, change `YOUR_GITHUB_USERNAME` to your actual
GitHub username. That's the only code edit you ever need to make.

### Step 3: Host it on Netlify

1. Create a free account at [netlify.com](https://netlify.com) and sign up **with GitHub**
2. "Add new site" → "Import an existing project" → pick your `tonyadragna.com` repo
3. Netlify auto-detects Astro. Confirm: build command `npm run build`, publish directory `dist`
4. Deploy. You'll get a temporary URL like `something.netlify.app`. Check it out!

### Step 4: Turn on the post editor login

1. In Netlify: **Site configuration → Access & security → OAuth → Install provider**
2. Choose **GitHub** and follow the prompts (Netlify walks you through creating
   the GitHub OAuth app; copy/paste two values)
3. Now visit `yoursite.netlify.app/admin`, click "Sign in with GitHub", and
   you're in your editor

### Step 5: Point tonyadragna.com at it

1. In Netlify: **Domain management → Add a domain** → enter `tonyadragna.com`
2. Netlify shows you the DNS records to set at your current domain registrar
   (wherever you bought tonyadragna.com, likely the same place hosting the old
   WordPress site)
3. Once DNS updates (minutes to a few hours), the new site is live with free
   automatic HTTPS

> Keep your WordPress site untouched until the new site is live, then you can
> cancel that hosting. Your domain registration is separate. Keep that!

---

## Writing a post (the WordPress-like part)

1. Go to `tonyadragna.com/admin`
2. Sign in with GitHub
3. Click **Blog Posts → New Blog Post**
4. Write in the rich-text editor: headings, bold, quotes, images, the works
5. Hit **Publish**. The site rebuilds itself and your post is live in ~1 minute

Drafts: flip the "Draft" toggle on and the post saves but stays hidden from the
site until you're ready.

---

## Working on the site locally (optional, for tinkering)

```bash
npm install     # once
npm run dev     # live preview at localhost:4321
npm run build   # production build into dist/
```

To try the post editor locally without any GitHub setup:

```bash
npx decap-server   # in one terminal
npm run dev        # in another → visit localhost:4321/admin
```

---

## Where things live

| What | Where |
|---|---|
| Blog posts | `src/content/blog/*.md` |
| Homepage | `src/pages/index.astro` |
| My Story page | `src/pages/about.astro` |
| Design/colors | `src/styles/global.css` |
| Editor settings | `public/admin/config.yml` |
| Old-URL redirects | `public/_redirects` |

Want to change the accent color? Edit `--orange` in `global.css`. Want to add a
photo? Drop it in `public/images/` and reference it as `/images/yourphoto.jpg`.
