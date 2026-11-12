# GAIA: a support circle for parents (showcase)

GAIA is a mobile app and web admin I have been building: a place where parents can find other parents, ask questions, and get answers from approved sources, with safety built in from the start.

**The source code is private.** This repository is a public overview of what the project is and how it is put together.

## Status

In development. It runs locally with demo data using the Firebase emulators. It has not been released to the public.

## What it does

- **Community feed.** Parents post and answer questions. Helpful answers earn karma (one point per helpful vote, with a daily cap of 50 so points cannot be farmed).
- **Verified peer matching.** Parents can be matched with each other and chat one-to-one. Chats are text-only, and the database rules reject links.
- **Live selfie verification.** A member takes a live selfie that an admin reviews. The photo is deleted after the decision.
- **GAIA AI helper.** The assistant only answers from sources an admin has approved. It runs a crisis check first, and when it cannot answer from approved sources, it suggests asking the community instead of guessing.
- **Admin console.** Admins manage users, reports, verification, FAQ entries, approved sources, categories, support tickets, rewards, settings, and an audit log.
- **Privacy tools.** A member can export their data or delete their account.
- **18+ only.** The age rule is enforced on the server, not just in the app, and there is no guest access.

## How it is built

| Part | Technology |
| --- | --- |
| Mobile app | Expo (React Native) with Expo Router |
| Admin web app | Next.js (App Router) |
| Backend | Firebase Cloud Functions |
| Data and auth | Firebase Authentication, Firestore, Cloud Storage, with security rules |
| Shared code | A TypeScript package for types, the 18+ check, terms version, topics, and the match score |
| Testing | Unit and integration tests that run against the Firebase emulators |

```
apps/
  mobile/   Expo app for members
  admin/    Next.js console for admins
  api/      Firebase Cloud Functions (backend)
shared      TypeScript package used by the apps
```

## Design decisions I care about

- **Safety first.** Features that touch trust (matching, chat, photos, AI answers) have rules on the server, so the app cannot skip them.
- **The AI is limited on purpose.** It answers from approved sources only and has a fallback that sends people to real parents.
- **Collect less data.** Verification photos are deleted after review, and members can export or delete their data.
- **Everything an admin does is logged.**

## What I am learning from it

- How a project can be split into a mobile app, an admin site, and a backend that share one set of types.
- Why security rules and server-side checks matter more than hiding buttons in the app.
- How tests that run against emulators help catch changes that break safety or privacy rules.

## How this was made

I built GAIA with AI coding assistants (including Codex). I direct the features and rules, read and test the results, and I am still learning the code in depth. I am a BSIT student, and this project is part of how I am learning full-stack development.

## Contact

Jhon Michael Tamayo, [LinkedIn](https://www.linkedin.com/in/jhonmichael-tamayo-24bab23a5/)
