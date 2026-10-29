# UNA Chat

Chat en tiempo real del curso; sistema sobre el que se hacen los laboratorios.

Created 2026-10-28

## Current status (2026-10-28)
- Lab 5 completo en `main` (`f7e1704`). Siguiente: [[US-01 Auth0]].

## Sistema
- Repo: `Repos/lab5-paradigmas-meli` → ver [[Environments]].
- Node.js + Express 5 + Socket.IO 4.8; frontend `index.html` (jQuery, sin build).
- `server.js`: sirve `/` y reenvía el evento `Evento-Mensaje-Server` después de `validation.validateMessage` (`libs/unalib.js`).
- `libs/unalib.js`: escapa HTML, detecta inyección de scripts, convierte URLs de imagen/video/YouTube en tags seguros.
- OpenSpec en `openspec/` con specs `chat-message-validation` y `chat-ux`.

## Pruebas
- Unitarias: `npm test` (Mocha 12, `test/`).
- Integración: `npx jest tests/integration --runInBand --env=node` (socket.io-client).
- E2E: `npx playwright test --project=chromium` (`tests/e2e/`).
- Seguridad: `npm run snyk:test`.

## Historial
- Lab 5: XSS, URLs de imagen/video, pruebas unitarias/integración/E2E, Snyk. Decisión: mocha → 12 (11.x seguía trayendo serialize-javascript 6 y js-yaml 4 vulnerables); express `*` → `^5.3.0` porque el lockfile fijaba 4.18.2 con proxy-addr crítico.

Last reinforced 2026-10-28
