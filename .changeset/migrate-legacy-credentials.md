---
"@googleworkspace/cli": minor
---

Auto-migrate legacy `credentials.enc` to per-account format on first run. When a legacy credential file exists without an `accounts.json` registry, gws now automatically:
1. Decrypts the legacy credentials
2. Determines the account email via Google userinfo
3. Re-saves as `credentials.<b64-email>.enc`
4. Creates `accounts.json` with the account as default
5. Renames the legacy file to `credentials.enc.bak`

Also removes the legacy `credentials.enc` fallback path — all credential resolution now goes through the accounts registry or ADC.
