# LADE Group website: deploy guide

## What's in this folder
- `index.html`: the full homepage (one page, no build step needed)
- `favicon.svg`: browser tab icon (the L-plan mark)
- `logo.svg`: horizontal logo for other uses (letterhead, capability statement)
- `robots.txt`, `sitemap.xml`: help search engines find the site

## Before you go live
1. **Capability statement**: add your PDF to this folder, named exactly `capability-statement.pdf`. All three "Download" buttons point to it.

## Contact form (already connected)
The form sends to your Formspree form `xoeedzgj`. Spam protection is built in three layers:
- **Hidden spam trap** (`_gotcha`): bots fill it, Formspree drops those messages automatically.
- **Formspree's own spam filter**: on by default.
- **CAPTCHA**: works out of the box. Until you add Cloudflare Turnstile, the form posts normally and Formspree shows its own "I'm not a robot" check before delivering the message.

### Optional: switch to Cloudflare Turnstile (nicer, stays on your page)
1. In the Cloudflare dashboard, open **Turnstile → Add widget**. Name it "ladegrp.com", add `ladegrp.com` and `www.ladegrp.com` as domains, choose **Managed** mode. Copy the **Site key** and **Secret key**.
2. In Formspree: your form → **Settings → CAPTCHA** → enable it → **Adjust settings** → choose **Cloudflare Turnstile** → paste the **Secret key** → Save.
3. In `index.html`, find `var TURNSTILE_SITE_KEY = '';` near the bottom and paste the **Site key** between the quotes.

After step 3, visitors complete a quick check under the form and see a confirmation message right on the page.
Do steps 2 and 3 together: if Formspree expects Turnstile but the site key is missing, messages are rejected.

## Deploy
- **Your current host** (where ladegrp.com lives now): upload every file in this folder to the site's root, replacing the old homepage.
- **Or Netlify (free)**: go to https://app.netlify.com/drop, drag this folder in, then connect the ladegrp.com domain under Domain settings.

After deploying, send yourself one test message through the form. The first submission may ask you to confirm the form by email in Formspree.

## Still to fill in later
- Contracting data table: socio-economic certifications, PSC codes, service area, payment terms (shown as [brackets]).
Search `index.html` for `[` to find every placeholder.
