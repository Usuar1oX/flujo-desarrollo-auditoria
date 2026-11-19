# Canales que SÍ funcionan (y cómo se usan)

Lo caro de este flujo no fue el ciclo — fue descubrir cómo alcanzar al
constructor y al producto sin fricción. Esto es lo verificado en producción
(DescuenTips / OdontoMX, nov 2026).

## SSH a los servidores

- La llave pública de Muse se agrega SIEMPRE en los **metadatos de la
  instancia desde la consola de GCP** (Editar → Claves SSH, con el nombre de
  usuario Linux como palabra final de la llave). Si se agrega editando
  `~/.ssh/authorized_keys` por shell, el agente invitado de Google la borra
  al sincronizar.
- Si al guardar sale «Supplied fingerprint does not match current metadata
  fingerprint», es concurrencia de metadatos: cancelar, recargar, editar de
  nuevo y guardar de inmediato.
- Conectar con `-i` explícito y un `UserKnownHostsFile` propio del proyecto.

## Timbre al desarrollador (Antigravity)

- El canal que SÍ lo pone a trabajar es su **sesión viva en tmux**
  (`tmux send-keys -t agy-main` por SSH): instrucciones en pasos únicos y
  cortos, con la pre-autorización escrita en el propio mensaje (el agente
  suele detenerse a pedir confirmaciones en un canal que nadie lee).
- Verificar que el timbre aterrizó: buscar en la captura del panel una
  palabra corta y distintiva del mensaje (las frases largas se parten entre
  líneas y el grep no las encuentra).
- La vista del panel tmux puede MENTIR: mostró «Model unavailable» por horas
  mientras el agente construía y comiteaba. La vista viva es el Remote
  Control web; la verdad última es git y el disco en el servidor.
- Si el Remote Control web se queda en el bucle «Model unavailable»,
  **Shift+F5** (recarga forzada) lo saca del bucle.
- Paquetes grandes (auditorías, planes): subir los archivos al servidor y
  mandar un timbre corto que apunte a la carpeta, nunca un solo mensaje
  gigante.

## ACP (`agy acp`) — solo opiniones

- `agy acp` por SSH (JSON-RPC/NDJSON: initialize → session/new o session/load
  → session/prompt) responde en segundos y sirve para pedir la OPINIÓN del
  constructor sin construir.
- Al cargar una sesión viva, el replay reproduce mensajes viejos: esperar a
  que se asiente (sin chunks nuevos por ~8 s) antes de marcar dónde empieza
  la respuesta nueva.
- Un turno ACP puede NARRAR ejecución sin ejecutar nada. Para construir, el
  canal es la sesión tmux; para verificar, siempre git/disco/base de datos.

## GitHub — registro sin tarjetas

- **Lectura** (detectar issues, contar comentarios): conector de GitHub en
  modo lectura o `gh` CLI en el servidor del proyecto. No genera tarjetas.
- **Escritura** (comentar, cerrar): SOLO por **github.com en el navegador en
  la nube**, con la sesión del usuario ya iniciada. El permiso de escritura
  del conector solo ofrece Preguntar o Denegar — cada comentario por esa vía
  es una tarjeta para Antonio — y no existe «Permitir» permanente.
- Si la sesión del navegador expiró, Antonio entra una vez a mano y Muse
  sigue trabajando dentro de esa sesión. No se guarda la contraseña de
  cuentas con segundo factor en su teléfono: esa contraseña sola no restaura
  la sesión y no sirve en la bóveda.

## Vigilantes

- Cron cada 5 minutos que lista issues abiertos (solo lectura) y compara
  contra un archivo de estado JSON con: estado por issue, `comments_count`
  procesado, `updated_at` procesado y candado `auditando` con hora
  (candado >2 h = abandonado, se puede retomar).
- El vigilante no audita dos veces lo mismo ni pierde entregas entre
  sesiones; su reporte va al chat que Antonio eligió, y también a cualquier
  otro chat donde Antonio siga el tema.

## Entrega de veredictos largos

- Un veredicto o paquete largo se escribe como ARCHIVO en la máquina del
  constructor y se avisa con un timbre corto. (Un print largo por SSH murió
  a los ~9 minutos y el constructor no aplicó nada.)
- Confirmar recepción con evidencia: commits nuevos, archivos editados o
  respuesta del constructor — no con su «entendido».
