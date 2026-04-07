# Deploy This Page

This folder is a plain static site. You can deploy it with GitHub Pages in either of these ways:

## Option A: new repository as a project site

1. Create a new GitHub repository, for example `ee5311-caustic-report`.
2. Copy everything inside this folder into the repository root.
3. Push to GitHub.
4. In the repository settings, enable GitHub Pages from the `main` branch and the root folder.
5. Your site URL will be in the form:

`https://<your-github-username>.github.io/ee5311-caustic-report/`

## Option B: same repository with `/docs`

1. Put the contents of this folder into a `docs/` folder at the repository root.
2. Push to GitHub.
3. In the repository settings, select GitHub Pages source as `main` branch and `/docs`.

## Option C: user site

If you create a repository named exactly:

`<your-github-username>.github.io`

then GitHub Pages can publish it as your account-level site:

`https://<your-github-username>.github.io/`

## Notes

- This site uses only relative paths, so it works for both root-level and project-level GitHub Pages URLs.
- The page is static HTML and CSS only. No build step is required.
- `.nojekyll` is included to avoid Jekyll processing.
