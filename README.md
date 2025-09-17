# OCHP Sign-Only Starter (Vercel + Next.js)

This starter lets candidates **sign only** (no editing) after an interview.

## What it includes
- **/sign/[token]**: read-only page showing frozen answers + signature pad.
- **/admin**: paste JSON answers → click **Create Link** to generate a sign URL.
- **/api/make-link**: mints a secure token server-side (HMAC, expires by default in 7 days).
- **/api/submit-signature**: verifies token, stamps signature onto a PDF, stores file in **Vercel Blob**, returns a public URL.
- **/public/templates/ochp-form.pdf**: your template used to place the signature.

If your upload contained PDFs, we've copied one as `ochp-form.pdf` here. You can replace it with your preferred final template.

## Deploy (summary)
1. Push this folder to a new GitHub repo.
2. Vercel → New Project → Import → Deploy.
3. Vercel → Project → Settings → **Environment Variables** → add `SIGNING_SECRET` (long random string).
4. Vercel → **Storage** → Create **Blob** store and connect to this project.
5. Open `/admin` to generate sign links.

## Use
- After an interview, paste your frozen answers JSON in `/admin` → **Create Link**.
- Send the link to the candidate.
- Candidate signs → PDF is saved to Blob → you get a URL.
