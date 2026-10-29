# US-01 Auth0

Historia de usuario del Lab 8: inicio de sesión social en [[UNA Chat]] con Auth0, local y en Vercel.

Created 2026-10-28

## Current status (2026-10-28)
- Propuesta OpenSpec `add-social-auth-auth0` lista y validada en la rama `feat/us-01-auth0` (2026-10-28). Esperando aprobación de Meli para implementar.

## Decisiones (propuesta)
- `express-openid-connect`, sesión en cookie cifrada (sirve en Vercel).
- `/` muestra `login.html` sin sesión; handshake de Socket.IO protegido; el servidor asigna el remitente desde la identidad.
- Errores de login mapeados a códigos fijos (`cancelled`/`failed`) → mensaje en español + Reintentar.
- `createServer({ auth })` para pruebas con auth falsa; E2E con servidor de prueba.

## Previous status
- No iniciada.

## Criterios de aceptación (resumen)
1. Cuenta Auth0 personal + aplicación UNA Chat.
2. Al menos un proveedor social.
3. Callback, logout y orígenes permitidos para local y dominio Vercel.
4. Login local con el proveedor y regreso autenticado.
5. Mostrar identidad y permitir logout.
6. Chat requiere autenticación.
7. Desplegado en Vercel con el mismo flujo.
8. Configuración por variables de entorno; sin secretos en repo ni en el navegador.
9. Cancelación/error → mensaje claro y reintento.

## Entregables
Repo, URL de Vercel, README (Auth0, local, despliegue), `.env.example`, evidencias local + Vercel.

## Notas
- Riesgo (inferido): Vercel serverless no mantiene WebSockets; Socket.IO podría necesitar long-polling o fallar en tiempo real. Ver [[Gaps]].
- Las credenciales viven en `.env` local y en las variables de entorno de Vercel; nunca en el brain.
