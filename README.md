# SPINDLE project page

A static website with no build step: `index.html` plus an `assets/` folder (about 13 MB). GitHub Pages serves it as is.

```
index.html
.nojekyll        (tells GitHub Pages to serve files as they are; harmless if it gets lost)
assets/video/    narrated overview video, poster, chapter list
assets/videos/   7 simulation examples, 2 real-robot clips, posters
```

## Publish it at an address like capable-vla.github.io

1. **Create a free GitHub organization** for the project (the **+** menu at the top right, then **New organization**, then the Free plan). Name it after the project, for example `spindle-vla`. The site address comes from this name.
2. **Create a public, empty repository named exactly `spindle-vla.github.io`** inside that organization, using your organization's name in place of `spindle-vla`. Leave "Add README" off if you will push with git.
3. **Upload the contents of this folder** (not the folder itself) to the repository root. You can either:
   - use the web page: **Add file**, then **Upload files**, then drag in `index.html`, `README.md` and the `assets` folder, then **Commit changes**; or
   - use git:
     ```bash
     cd spindle-site
     git init
     git add .
     git commit -m "SPINDLE project page"
     git branch -M main
     git remote add origin https://github.com/spindle-vla/spindle-vla.github.io.git
     git push -u origin main
     ```
4. **Turn on Pages:** go to **Settings**, then **Pages**, then **Build and deployment**. Set **Source** to **Deploy from a branch**, set **Branch** to `main` with the folder `/ (root)`, then click **Save**.
5. **Open `https://spindle-vla.github.io`.** GitHub says publishing can take up to 10 minutes.

**Alternative: host it under your own account.** Name the repository `spindle`. The site then appears at `https://<your-username>.github.io/spindle/`, and every path still works because they are all relative.

**Updates:** edit `index.html`, or replace a file in `assets/`, then commit. The site redeploys on every push.

## After you publish

- **Link previews (X, LinkedIn, Slack):** in `index.html`, change
  `<meta property="og:image" content="assets/video/spindle_overview_poster.jpg">` to the full address, e.g.
  `https://spindle-vla.github.io/assets/video/spindle_overview_poster.jpg`.

## Adding things later

- **Code link:** once the repository is public, replace the Code `<button ... data-placeholder=...>` with:
  ```html
  <a class="btn" href="https://github.com/spindle-vla/spindle" target="_blank" rel="noopener">
    <!-- keep the existing <svg> icon here -->
    <span>Code</span>
  </a>
  ```
- **Paper / arXiv buttons:** copy the Citation button (`<a class="btn" href="#citation">…</a>`), point `href` at the PDF or the arXiv page, and add `target="_blank" rel="noopener"`.
- **New overview video:** replace `assets/video/spindle_overview.mp4` and its poster with the same file names, then update the chapter times in `spindle_overview_chapters.json`. The page has no caption track; to add one, put a `<track kind="captions">` inside the overview `<video>` and remove `hidden` from the `#ov-cc` button.
- **BibTeX:** change `@misc` to the final venue entry once the paper is accepted or on arXiv.

## Limits (GitHub Pages)

The published site may be at most 1 GB. Bandwidth has a soft limit of 100 GB per month, and a deployment times out after 10 minutes. This site is about 13 MB.
