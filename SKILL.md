# Flujo de desarrollo con auditoría — Antonio / Muse / Desarrollador

Skill maestra del flujo de trabajo que usan Antonio (dueño y mediador), Muse
(planeación y auditoría) y el desarrollador (Antigravity, Claude Code u otro
agente constructor) para construir software por tandas verificadas.

Archivos de esta skill:

- `SKILL.md` — este documento: roles, principios y el ciclo completo.
- `CONDITIONS_TEMPLATE.md` — plantilla de condiciones de satisfacción.
- `ISSUE_TEMPLATE.md` — formatos de entrega «Listo para auditar» y de veredicto.
- `CHECKLIST.md` — checklist permanente de auditoría de Muse.
- `CHANNELS.md` — cómo se alcanzan el constructor y el producto (lo que costó días descubrir).
- `DEAD_ENDS.md` — rutas ya probadas que NO funcionan; no reintentar sin que cambie su condición.

## Roles

- **Antonio** decide y media. Aprueba planes, condiciones y pasos a producción.
  No es mensajero entre las IAs: el puente lo opera Muse.
- **El desarrollador** construye. Para construcción NUEVA primero opina sin
  construir; construye solo con condiciones acordadas, y solo en el entorno de
  pruebas hasta recibir luz verde.
- **Muse** planea con ambos, lleva el registro, AUDITA lo construido contra lo
  acordado y cierra el ciclo. Lo que Muse pueda corregir directamente en un
  panel con su propio acceso, lo corrige Muse y no se lo pide al desarrollador.

## Principios que no se negocian

1. **Plan primero.** Nada nuevo se construye sin un plan discutido por los tres
   (Antonio, Muse y el desarrollador). Corregir el plan es más barato que
   corregir el código.
2. **Entrega = evidencia.** Ninguna tanda cuenta como entregada sin: hash de
   commit, suite de pruebas corrida y en verde, y confirmación de sitio quieto
   (sin despliegues en curso). La palabra del constructor no es evidencia:
   Muse verifica en vivo, en el disco/git y en la base de datos cuando aplique.
3. **Nunca auditar durante un despliegue.** Si el sitio está en movimiento, se
   espera a que quede quieto y se dice en el issue.
4. **Dos entornos por proyecto.** Producción recibe solo commits verificados.
   Pruebas vive en el mismo servidor, con base de datos de semilla LIGERA
   (nunca una copia de producción), acceso protegido y `noindex`.
5. **Datos de prueba solamente.** Nunca crear, editar ni borrar registros
   reales en una auditoría. Nada de contraseñas ni datos reales en issues.
6. **El registro es GitHub; el timbre es el canal vivo.** Los issues guardan la
   historia auditable; los mensajes cortos por el canal vivo solo despiertan al
   constructor (ver `CHANNELS.md`).
7. **Verificación por capas, barata primero.** Durante el desarrollo se corren
   solo las pruebas del módulo tocado; la suite completa corre una vez, en la
   puerta a producción. Una tanda no paga la suite entera en cada intento.
8. **El cambio no modifica su propia verificación.** Las condiciones, el
   checklist y la suite que juzga viven fuera del alcance de la tanda juzgada;
   tocarlos requiere su propia tanda aprobada.
9. **Tres rondas y se escala.** Si un punto no pasa tras 3 rondas de corrección
   y re-auditoría, deja de iterarse entre agentes: se escala a Antonio con el
   resumen del desacuerdo.
10. **Las reglas también se podan.** Suites, reglas y esta misma skill solo
    crecen si se dejan; periódicamente se corre una tanda de poda (pruebas
    obsoletas, reglas duplicadas, callejones superados) para que el ciclo no
    se vuelva más lento cada mes.

## El ciclo (por tanda)

1. **Pedido.** Antonio plantea el proyecto o la mejora en el chat de mediación.
2. **Plan y condiciones.** Muse redacta el plan con condiciones de
   satisfacción claras, medibles y verificables (ver `CONDITIONS_TEMPLATE.md`)
   y lo discute con Antonio.
3. **Opinión del constructor.** Muse pasa el plan al desarrollador, que opina
   SIN construir: viabilidad, riesgos, alternativas. Muse trae la opinión a
   Antonio; se ajustan las condiciones y Antonio aprueba.
4. **Construcción en pruebas.** El desarrollador construye solo en el entorno
   de pruebas, con respaldo previo de la base cuando la tanda toca datos.
5. **Entrega.** El desarrollador abre (o comenta) el issue «Listo para
   auditar» con el formato de `ISSUE_TEMPLATE.md`: URLs, commits, afirmaciones
   numeradas verificables, conteos antes/después y suite en verde.
6. **Auditoría.** Muse verifica cada afirmación en vivo con `CHECKLIST.md`:
   flujo completo como usuario, el valor guardado detrás de la pantalla,
   conteos contra respaldo, ambas vistas (móvil primero si el producto es
   móvil), y la suite corrida por el propio Muse cuando sea posible. Muse
   audita desde las condiciones y el producto, NO desde el relato del
   constructor: su contexto es la especificación y la evidencia, y antes de
   dar luz verde relee el pedido original de Antonio para confirmar que las
   condiciones no derivaron de lo que él pidió.
7. **Veredicto.** Muse publica UN comentario en el issue con veredicto por
   punto (corregido / parcial / no corregido / no verificable), evidencia breve
   y conteo final. Si algo falla: lista de correcciones, timbre al
   desarrollador y se vuelve al paso 4 con esa lista (una sola lista
   consolidada, no goteo de puntos).
8. **Producción y cierre.** Con todo «corregido», Muse da luz verde; el
   desarrollador aplica a producción; Muse verifica en producción lo mismo
   que auditó en pruebas y cierra el issue. El resultado durable se registra
   en la memoria de Muse.

## Vigilancia

- Un vigilante revisa cada pocos minutos si hay issues «Listo para auditar»
  nuevos o comentarios nuevos en issues auditados, con archivo de estado
  (marcas de agua y candado anti-solape) para que ninguna entrega se pierda ni
  se audite dos veces.
- Los reportes llegan al chat que Antonio eligió para ese proyecto. Si Antonio
  sigue un tema en otro chat (p. ej. WhatsApp), el reporte va también ahí.

## Arranque en un proyecto nuevo

1. Clonar esta skill y leer `CHANNELS.md` y `DEAD_ENDS.md` antes de improvisar
   rutas nuevas.
2. Habilitar el acceso SSH de Muse al servidor (llave en los metadatos de la
   instancia, ver `CHANNELS.md`).
3. Crear el entorno de pruebas ligero y las cuentas de prueba.
4. Crear el repo (o usar el existente) con la plantilla de issue
   «Listo para auditar» y el issue n.º 1 con el protocolo.
5. Primera tanda pequeña de punta a punta para validar el ciclo antes de
   tandas grandes.
