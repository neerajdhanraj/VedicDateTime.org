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

## Publish on GitHub Pages (project site)

1. Commit the website source files (this `site/` folder) and the generated `docs/` folder to your default branch (e.g., `main`).
2. In GitHub repo → **Settings** → **Pages**:
   - Source: **Deploy from a branch**
   - Branch: `main`
   - Folder: `/docs`
3. Save.

Your project site URL will be:

- `https://<OWNER>.github.io/<REPO>/`

For example:

- `https://neerajdhanraj.github.io/VedicDateTime/`

## IMPORTANT: Why your GitHub URL may redirect to a custom domain

GitHub Pages redirects to a custom domain if **either** of the following is true:

1. **Repo Settings → Pages → Custom domain** is set.
2. A `CNAME` file exists in the **published** site root (for project sites this is typically `docs/CNAME` on `main`, or `CNAME` on the `gh-pages` branch).

So, if you want to test on `github.io` (no redirect):

- Ensure **Custom domain is blank** in Settings → Pages.
- Ensure there is **NO** `docs/CNAME` committed.

(Deleting `site/CNAME` alone is not enough if `docs/CNAME` was previously committed.)

## Future: enable the custom domain (vedicdatetime.org) safely

When DNS is ready and you *want* redirect to your domain:

1. In GitHub repo → **Settings** → **Pages** → **Custom domain**:
   - enter: `vedicdatetime.org`
2. Create `docs/CNAME` containing exactly:

```text
vedicdatetime.org
```

3. Add DNS records at your domain provider:

- Apex domain (`@`) A records → GitHub Pages IPs:
  - 185.199.108.153
  - 185.199.109.153
  - 185.199.110.153
  - 185.199.111.153

4. After DNS propagates, enable **Enforce HTTPS**.

## Deployment checklist

- [ ] Run `quarto render`
- [ ] Copy/update the generated `docs/` folder in your repository root
- [ ] Commit + push
- [ ] GitHub → Settings → Pages → Branch: `main` and folder `/docs`
- [ ] Hard refresh your browser (`Ctrl+F5`) if you still see an old version

## Notes

- This site is configured to **not execute** code blocks during rendering (`execute.eval: false`), so the website builds even if VedicDateTime is not installed on the build machine.
- Consider adding **pkgdown** later for fully auto-generated R function reference.
