# ST South Australia App

The **ST South Australia App** is a lightweight internal web app for Sydney Tools staff in South Australia. It provides quick access to commonly used internal resources such as warranty information, supplier contacts, repair status views, trailer requests, forms, reference documents, and other store tools.

The app is intentionally simple: most pages are plain HTML, CSS, and JavaScript so they are easy to maintain without a full application framework.

## Live Site

The current live site is hosted via Cloudflare:

`https://st-web-app.calebwhittet.workers.dev`

## Authentication

The main internal pages use **Supabase Auth** with Google sign-in.

Access is restricted in the frontend to users signed in with a:

`@sydneytools.com.au`

email address.

Supabase is currently used for authentication only on the main index and related protected pages. Most application data is still sourced from Google Sheets or Google Apps Script endpoints.

> Note: Client-side authentication controls access to the pages, but any Google Sheet or Apps Script endpoint that is publicly accessible can still be called directly if someone knows its URL. More sensitive data should eventually be placed behind an authenticated API or otherwise restricted.

## Current Core Pages

- `index.html` — main landing page and Google/Supabase login
- `Rep Directory.html` — supplier representative contacts
- `Warranty1.html` — warranty information and links
- `store_view.html` — repair status/store repair view
- `Trailer.html` — trailer request/status page
- `Repairs.html` — separate repair-management page using its own Supabase project/configuration
- `parser.html` — repair/parser tooling and Google Sheets integration

There are also many older, experimental, reference, and store-specific pages in the repository. Not all files are currently used in production.

## Data Sources

The site currently uses a mix of:

- Google Sheets CSV exports
- Google Apps Script web endpoints
- Google Forms
- Supabase Auth
- Static HTML/PDF/image files stored in this repository

## Hosting and Deployment

Source code is stored in this GitHub repository and the live app is served through Cloudflare.

Changes committed to the deployment branch are picked up by the Cloudflare deployment integration.

## Development

There is no required build step for the main static pages.

To work locally:

```bash
git clone https://github.com/Caleb-ST/ST-Web-App.git
```

Then open the relevant HTML page in a modern browser.

Some pages depend on:

- internet access
- Supabase authentication
- Google Sheets or Apps Script endpoints
- Google OAuth redirect configuration

Because of this, certain features may not work correctly from a local `file://` URL.

## Supabase Configuration

Several protected pages currently contain their Supabase project URL and publishable key directly in the page JavaScript.

These are frontend-safe publishable credentials, but the configuration is duplicated across multiple files. A future cleanup should move the shared Supabase configuration and authentication check into a common JavaScript file so a project change only needs to be made once.

Do **not** commit Supabase service-role keys, database passwords, OAuth client secrets, or other private credentials to this repository.

## Security Notes

Current access protection is primarily client-side authentication.

For the current use case this is sufficient for page access, but:

- Google Sheet exports may be publicly accessible
- Google Apps Script endpoints may be callable outside the app
- sensitive future data should be protected server-side
- Supabase Row Level Security should be used if database tables are added later
- external links opened in new tabs should ideally use `rel="noopener noreferrer"`

## Repository Structure

The repository is currently mostly flat and contains a mixture of:

- active production pages
- older pages
- test pages
- store-specific pages
- PDFs
- images
- data/reference files

This is intentional for now. A future tidy-up may move unused or legacy content into an archive folder and group active assets/pages into clearer directories.

## Maintenance Notes

When changing authentication:

1. Update the Supabase project URL and publishable key on all active protected pages.
2. Confirm the Supabase Site URL and Redirect URLs point to the Cloudflare-hosted site.
3. Confirm the Google OAuth callback URL matches the active Supabase project.
4. Test login, logout, and direct access to protected pages.

When changing Google Sheets or Apps Script sources:

1. Confirm the endpoint is still published and accessible.
2. Check whether the data is suitable to remain publicly reachable.
3. Test any affected pages after changing Sheet columns or script responses.

## Status

The project is actively maintained for internal South Australian store use. Simplicity and reliability are preferred over adding unnecessary frameworks or build tooling.
