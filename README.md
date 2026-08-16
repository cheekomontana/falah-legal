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

- A backend or account server is introduced (the policy says there is none).
- The Companion starts sending questions to a server to answer them (section 5
  says nothing typed into it leaves the phone, and promises to flag the change).
- An analytics or advertising SDK is added (section 4 says there is none).
- The set of data stored on device changes (section 1 lists it).
- The Sign in with Apple implementation changes what it requests or where it is
  stored (section 2).
- A third party beyond Apple and Superwall begins receiving data (section 4).
