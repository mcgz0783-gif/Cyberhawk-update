# Gemini Configuration Guide

This project supports Google Gemini for the in-app CyberBot assistant.

## Required environment variables

Set these values in `.env` (or copy from `.env.example`):

- `VITE_GEMINI_API_KEY` — Google AI Studio API key.
- `VITE_SITE_NAME` — display name for the project.
- `VITE_SITE_URL` — deployed URL.

## Local setup

1. Copy `.env.example` to `.env`.
2. Put your real Gemini key in `VITE_GEMINI_API_KEY`.
3. Run:

```bash
npm install
npm run dev
```

## Runtime behavior

- If `VITE_GEMINI_API_KEY` is present, the app calls Gemini.
- If the key is missing, the app falls back to Anthropic in compatible preview environments.

## Security notes

- Never commit real API keys to git.
- Keep `.env` and `.env.local` private.
