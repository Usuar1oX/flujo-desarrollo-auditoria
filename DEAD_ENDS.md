# Rutas muertas — ya probadas, no reintentar

Cada ruta de aquí costó tiempo real. No se reintenta salvo que cambie la
condición que la mató, y ese cambio se verifica antes, no se supone.

## Escribir en GitHub con el conector
- **Qué pasó:** el permiso de escritura («Cambiar contenido del repositorio»)
  solo ofrece Preguntar o Denegar; no existe «Permitir». Cada comentario o
  cierre genera una tarjeta de aprobación para Antonio.
- **Ruta buena:** github.com en el navegador en la nube (ver `CHANNELS.md`).
- **Reintentar si:** Meta agrega un «Permitir» persistente para ese permiso.

## Webhooks para detectar issues nuevos
- **Qué pasó:** la VM de Muse no acepta conexiones entrantes; la prueba de
  webhook no pudo entregar.
- **Ruta buena:** vigilantes con polling cada 5 min y archivo de estado.

## ACP como canal de ejecución
- **Qué pasó:** el agente respondió narrando trabajo que no ejecutó (sin
  commits ni cambios en disco).
- **Ruta buena:** ACP solo para opiniones; construcción por la sesión viva
  en tmux; verificación siempre contra git/disco.

## Que el vigilante principal audite el entorno de pruebas
- **Qué pasó:** aunque Antonio guardó el Basic Auth de pruebas en la bóveda,
  el navegador del vigilante siguió recibiendo 401 y sus veredictos salieron
  «no verificables».
- **Ruta buena:** la auditoría de pruebas la hace la sesión de Muse con
  acceso SSH/servidor; el vigilante verifica en producción.
- **Reintentar si:** cambia el mecanismo de acceso al entorno de pruebas.

## Tailscale en el servidor casero
- **Qué pasó:** consumía demasiada RAM en la laptop que hace de servidor;
  Antonio lo dio de baja.
- **Ruta buena (futura):** túnel SSH inverso ligero desde el servidor casero
  hacia una VPS, cuando el servidor tenga la RAM ampliada.

## Google Remote Agents para liberar al desarrollador
- **Qué pasó:** Remote Agents no está activo en ninguna de las dos cuentas
  Pro; la migración quedó en espera sin comprar nada.
- **Reintentar si:** Google activa Remote Agents en las cuentas.

## Llaves SSH editando `authorized_keys` en GCP
- **Qué pasó:** el agente invitado de Google sincroniza metadatos y borra
  las llaves agregadas por shell.
- **Ruta buena:** metadatos de la instancia desde la consola (ver `CHANNELS.md`).

## Fiarse de la vista del panel tmux
- **Qué pasó:** mostró el bucle «Model unavailable» por horas mientras el
  agente, en realidad, construía y comiteaba.
- **Ruta buena:** Remote Control web para verlo trabajar; git/disco como verdad.

## Entregar veredictos como un print largo por SSH
- **Qué pasó:** la entrega murió a los ~9 minutos; el constructor no aplicó
  ningún cambio.
- **Ruta buena:** archivo en su máquina + timbre corto que apunte al archivo.

## Guardar contraseñas de cuentas con 2FA esperando re-login autónomo
- **Qué pasó:** la cuenta siempre pide el segundo factor en el teléfono de
  Antonio; la contraseña guardada sola no restaura ninguna sesión.
- **Ruta buena:** Antonio entra en el momento y Muse trabaja dentro de esa
  sesión mientras dure.
