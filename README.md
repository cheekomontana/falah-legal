# Falah — legal documents

The Terms of Service and Privacy Policy for the Falah iOS app, served as static
pages via GitHub Pages.

- Terms of Service — <https://cheekomontana.github.io/falah-legal/terms/>
- Privacy Policy — <https://cheekomontana.github.io/falah-legal/privacy/>

Both URLs are referenced from inside the app (`src/onboarding/legal.ts` in the
Falah repo) and are submitted to App Store Connect. **App Review opens them, so
they must stay reachable.** Do not rename the `terms/` or `privacy/` directories
or delete this repository.

This repository is public because GitHub Pages requires it on a free plan. It
contains no application source — only these two documents.

## Editing

Each page is a single self-contained HTML file with its CSS inline. There is no
build step and no Jekyll (`.nojekyll` disables it). Edit, commit, push; Pages
redeploys in about a minute.

When changing either document, update the "Last updated" date at the top of it.

## Keeping the policy true

Both documents make specific factual claims about the app. If any of the
following changes, they are wrong and must be updated **before** the release
ships:

- **The prayer log, setup answers or location begin syncing to the server.**
  Sections 1 and 7 both say they never do, and it is the strongest promise in
  the document. Everything else here is a detail by comparison.
- **PostHog stops being anonymous.** Section 6 says three things: it is never
  told who you are, it is never given a location, and it never receives your
  worship or your content. Calling `posthog.identify()`, removing
  `disableGeoip` from the options in `App.tsx`, or capturing a prayer event
  would each falsify one of them. The `disableGeoip` coupling is the easiest to
  break by accident, because the PostHog default is to geolocate.
- The Companion conversations stop being deleted with the account, or the
  row-level security on those tables is loosened (section 4 promises both).
- The set of tables on Supabase changes, or they start holding anything beyond
  the account, the profile row, the rate-limit counters and the conversations
  (section 5 lists them exactly).
- The AI provider changes from Google, or a second provider is added
  (section 4 names Google, and the Terms name Gemini).
- The rate limit changes from 20 messages per hour (section 5 and Terms §4).
- An advertising SDK, or a second analytics tool, is added (section 7 names
  PostHog as the only one).
- The set of data stored on device changes (section 1 lists it).
- The Sign in with Apple implementation changes what it requests (section 3).
- Anything other than the Companion starts requiring an account (sections 3 and
  4 both say it is the only feature that does).
- In-app account deletion moves or is removed (section 9 tells the user exactly
  where the button is).
- **The Companion is re-narrowed to Salah only**, or given a fixed whitelist of
  sources again. Terms §4 says he answers across the deen and is instructed to
  name his sources.
- A third party beyond Apple, Superwall, Supabase, Google and PostHog begins
  receiving data.

There is a fourth place this list has to agree with: `ios.privacyManifests` in
the Falah repo's `app.json`, which is Apple's machine-readable version of it,
and the nutrition label in App Store Connect, which is a fifth. Changing what
Falah collects means changing all of them.
