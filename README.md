# Validoc — GitHub Pages trial package

This folder is ready to upload to the root of a GitHub repository and publish with GitHub Pages.

## Self-contained reliability build

The main `index.html` now embeds the complete PDF engine, Validoc logo, Venus logo, certificate borders, interface styles, and Montserrat fonts. This prevents missing-logo and non-working-PDF errors when GitHub serves the app from a repository subfolder. No separate asset, CSS, JavaScript, font, or PDF-library folder is required.

Completed documents display a **Download PDF** button directly on the dashboard. Before creating the combined PDF, Validoc refreshes temporary cloud file links so older completed workflows can download their original documents and signed Approval Report.

## Publish the website

1. Create a new GitHub repository. Use a private repository if your GitHub plan supports Pages for private repositories; otherwise remember that every uploaded file will be public.
2. Extract the ZIP on your computer. Do not upload the ZIP itself as the website.
3. Upload every extracted file and folder to the repository root, including the hidden `.github` folder and `.nojekyll` file.
4. Commit the files to the `main` branch.
5. Open the repository's **Settings → Pages**.
6. Under **Build and deployment**, select **GitHub Actions** as the source.
7. Open the repository's **Actions** tab and wait for **Deploy Validoc to GitHub Pages** to complete.
8. The live address will normally be `https://YOUR-GITHUB-NAME.github.io/YOUR-REPOSITORY/`.

## Required Supabase setting

Validoc already contains the public Supabase project URL and publishable/anon key required by the browser. In the Supabase dashboard, add the final GitHub Pages address to:

- **Authentication → URL Configuration → Site URL**
- **Authentication → URL Configuration → Redirect URLs**

Use the exact address including the repository path and final slash, for example:

`https://YOUR-GITHUB-NAME.github.io/validoc/`

This is required for account verification and password-recovery links to return to the published app.

## Trial login

The repository does not contain a password. Enter the temporary demonstration email and password supplied separately on the Validoc login screen. Change or remove the trial account after the demonstration.

## Functions available on GitHub Pages

- Password-based Supabase login
- Each new document belongs to its authenticated initiator
- Initiator-only document, recipient, signer-replacement, expiry, and grace-period controls
- PDF/JPG upload, preview, zoom, pan, comments, highlights, and printing
- Recipient directory and contact import
- Personal signing links and manual Share/Copy email controls
- Draw, type, or upload a scanned signature, with blue/black choice
- Signer reassignment during an active workflow; the old link is revoked
- Approval Report generation and combined completed-PDF download
- Supabase cloud storage/workflow synchronization

## GitHub Pages email limitation

GitHub Pages serves static HTML, CSS, and JavaScript only. It cannot execute the included Hostinger PHP mail service, so this GitHub package intentionally does not contain `validoc-mail.php`.

For this GitHub trial:

- Use **Share links**, **Copy link**, or **Copy email** to send invitations.
- The completed combined PDF downloads automatically after all required signers approve.
- Automatic invitation and completed-PDF email delivery requires the separate Hostinger package or a future Supabase/SMTP email function.

## Important security notes

- No login password is stored in this package.
- The Supabase publishable/anon key is designed for browser use; security must still be enforced by Supabase authentication and Row Level Security.
- Do not add service-role keys, SMTP passwords, or other private secrets to this repository.
- Before production use, replace the trial login and complete a security, legal, retention, and electronic-signature compliance review.

## Main file structure

```text
index.html
404.html
favicon files
site.webmanifest
.github/workflows/pages.yml
.nojekyll
README.md
```
