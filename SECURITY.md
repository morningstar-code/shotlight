# Security

Shotlight holds the text of everything on your screen that you ever captured, so its security model matters.

## What Shotlight protects against

- **Other websites.** The local API listens on 127.0.0.1 only and requires a random per-session token. The window receives the token once and keeps it in an HttpOnly, SameSite=Strict cookie, so pages open in your browser can neither read the API nor make it act (CSRF). The Host header is checked against 127.0.0.1/localhost to stop DNS rebinding, POST requests with a foreign Origin are refused, and the interface is served with a strict Content Security Policy.
- **Other local users.** Without the token they cannot use the API. On macOS and Linux the data folder (index, thumbnails, token) is created readable only by you; on Windows it lives in your private `%LOCALAPPDATA%`.
- **AI assistants seeing secrets.** With the privacy shield on (the default), detected API keys, tokens, card numbers and passwords are masked in MCP answers, and images containing them are not sent.

## What it does not protect against

Software running as your own user can read the index and the token, as it can read your screenshots themselves. The index is not encrypted; use full-disk encryption.

## Reporting a vulnerability

Please report privately through GitHub's private vulnerability reporting: the **Report a vulnerability** button on the [Security tab](https://github.com/morningstar-code/shotlight/security), rather than a public issue. Include steps to reproduce. You will get a reply within a week.
