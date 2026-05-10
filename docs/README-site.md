# VedicDateTime website (GitHub Pages)

This folder contains a **Quarto** website intended to be published with **GitHub Pages**.

## Local preview

1. Install Quarto: https://quarto.org/
2. In RStudio (or terminal), from this folder:

```bash
quarto preview
```

## Build

```bash
quarto render
```

This renders the site to `docs/` (configured in `_quarto.yml`).

## Publish on GitHub Pages

Recommended approach for a *project site*:

1. Commit the website source files and the generated `docs/` folder to your default branch (e.g., `main`).
2. In GitHub repo → **Settings** → **Pages**:
   - Source: **Deploy from a branch**
   - Branch: `main`
   - Folder: `/docs`
3. Save. GitHub will publish at:
   - `https://<OWNER>.github.io/<REPO>/`

## Future: Custom domain

1. Choose a domain, e.g. `vedicdatetime.example.com`.
2. In GitHub repo → **Settings** → **Pages** → **Custom domain**:
   - Enter your domain and save.
3. DNS configuration (typical):
   - For a subdomain (`vedicdatetime.example.com`): create a **CNAME** record pointing to `<OWNER>.github.io`.
   - For an apex domain (`example.com`): use **A** records to GitHub Pages IPs (see GitHub docs).
4. Create `docs/CNAME` containing exactly your domain name on one line.
   - Start by copying `CNAME.template` → `docs/CNAME` and editing it.
5. (Recommended) Enable **Enforce HTTPS** in GitHub Pages settings after DNS propagates.

## Deployment checklist

- [ ] Set `website.repo-url` and the navbar GitHub link in `_quarto.yml`
- [ ] Decide whether this is a **project site** (`https://<OWNER>.github.io/<REPO>/`) or **user/org site** (`https://<OWNER>.github.io/`)
- [ ] Run `quarto render` and commit the generated `docs/` folder
- [ ] GitHub → Settings → Pages → Branch: `main` and folder `/docs`
- [ ] Confirm all links work on the published URL

## Notes

- Update `_quarto.yml` with:
  - `website.repo-url`
  - navbar GitHub link
  - `website.site-url` (optional but helps with SEO)
- Consider adding **pkgdown** for fully auto-generated R function reference.
