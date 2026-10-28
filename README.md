# Bhavya Associates website

Static website with a file-based Updates & Insights feed and Decap CMS editor.
Updates are saved as JSON and uploaded images as repository files; no database
is used.

## Deploy with Netlify

This repository is set up for Netlify (`netlify.toml` publishes the repository
root; no build command is needed).

To connect it to the existing `bhavya-associates` Netlify site:

1. In Netlify, open the existing site's **Project configuration** and connect
   the Git repository `dlngupta/bhavya-associates`.
2. Confirm the production branch is `master`, the publish directory is `.`, and
   there is no build command.
3. Trigger a deploy and wait for it to complete.

The public website is `https://bhavya-associates.netlify.app/`. The content
editor is `https://bhavya-associates.netlify.app/admin/`.

## Enable the private editor

1. In the Netlify site, enable **Identity**.
2. Set Identity registration to **Invite only**. Do not enable open public
   registration for the CMS.
3. Invite the intended editor from **Identity → Users** and have them accept
   the invite.
4. Under **Identity → Services**, enable **Git Gateway**.
5. In Identity email settings, ensure the invite/confirmation link uses the
   production site URL `https://bhavya-associates.netlify.app`.
6. Open `/admin/`, sign in with the invited account, then create or edit an
   update under **Updates & Insights**.

The CMS saves posts and images directly to the repository's `master` branch.
Netlify deploys each save. The editor URL is public, but only invited,
authenticated users with Git Gateway access can edit content.
The homepage loads Netlify's Identity widget for confirmation, invitation, and
password-recovery links. Keep the token fragment intact until the widget
processes it; the site must show the widget's password form for recovery.

## How updates work

The homepage reads `updates.json` and displays published updates in a featured
carousel and a recent-updates list. Add the date, category, title, summary,
optional photo, and publication status in the CMS. Unpublished entries remain
in the repository but do not appear on the website.

## Privacy and accuracy

Only publish claim stories or customer photos with the customer's clear
permission. Do not include policy numbers, medical records, contact details, or
other identifying information. Verify policy information before publishing;
site updates are general information, not individual financial, legal, tax, or
medical advice.
