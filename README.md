# SASL SmartLearn — Authentication Edition

React + Vite sign language learning app with **real Supabase email/password authentication** and 26 alphabet videos.

## Setup

1. Create a free project at https://supabase.com/dashboard .
2. Open **Project Settings → API** (or Connect) and copy the **Project URL** and **publishable/anon key**. **Never use a service_role or secret key in the frontend.**
3. Copy `.env.example` to `.env` and paste those two values.
4. In Supabase **Authentication → Providers**, enable **Email**. Choose whether email confirmation is required.
5. In **Authentication → URL Configuration**, add `http://localhost:5173` as Site URL and add `http://localhost:5173/reset-password` as a redirect URL. Add your production site URLs when deploying.
6. Run:

```bash
npm install
npm run dev
```

## Features

- Register with display name, email and password
- Log in, persistent authenticated session, log out
- Forgot-password email and password update flow
- Protected learning pages (guests are redirected to login)
- Per-account learning progress stored **locally on the current browser** (not synced to Supabase). Progress is not shared across devices and is lost if browser storage is cleared.
- All 26 videos in `public/videos/`

## Notes

Supabase authentication requires an internet connection and your own configured project keys. No working account service is embedded in the ZIP. If you enable email confirmation, new users must verify their email before logging in. Password-reset emails depend on your Supabase email configuration and limits.

**Security:** The frontend uses the public anon/publishable key only; Supabase handles passwords. Do not put service role credentials in `.env`. The app does not store passwords in localStorage.
