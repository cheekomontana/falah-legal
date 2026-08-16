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

The Privacy Policy makes specific factual claims about the app. If any of the
following changes, the policy is wrong and must be updated **before** the
release ships:

- **The Companion backend starts storing questions or answers.** Section 4 says
  plainly that it does not — the Edge Function streams them through to Google
  and keeps nothing. Adding logging, a transcript table, or an analytics hook
  over that traffic makes the published policy false.
- The set of tables on Supabase changes, or they start holding anything beyond
  the account, the profile row and the rate-limit counters (section 5 lists
  them exactly).
- The prayer log, setup answers or location begin syncing to the server
  (sections 1 and 7 both say they do not).
- The AI provider changes from Google, or a second provider is added
  (section 4 names Google, and the Terms name Gemini).
- The rate limit changes from 20 messages per hour (section 5 and Terms §4).
- An analytics or advertising SDK is added (section 7 says there is none).
- The set of data stored on device changes (section 1 lists it).
- The Sign in with Apple implementation changes what it requests (section 3).
- Anything other than the Companion starts requiring an account (sections 3 and
  4 both say it is the only feature that does).
- A third party beyond Apple, Superwall, Supabase and Google begins receiving
  data.

## Known gap

The app supports account creation but has **no in-app account deletion**, which
App Store Guideline 5.1.1(v) requires. Section 9 of the policy currently directs
users to email for deletion; that is the honest description of what exists, not
a substitute for the in-app control Apple asks for.
