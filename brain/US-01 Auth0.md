# US-01 Auth0

Historia de usuario del Lab 8: inicio de sesión social en [[UNA Chat]] con Auth0, local y en Vercel.

Created 2026-10-28

## Current status (2026-10-28)
- No iniciada. Se hará con OpenSpec dentro del repo (propuesta → diseño → specs → tareas → implementar → archivar).

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
