# Checklist permanente de auditoría (Muse)

## Antes de empezar

- [ ] Leer las condiciones de satisfacción de la tanda y convertir CADA
      afirmación del desarrollador en un punto de checklist propio.
- [ ] Releer el pedido original de Antonio: lo que se audita debe seguir
      diciendo lo que él pidió (sin deriva de especificación entre el pedido,
      las condiciones y lo construido).
- [ ] Confirmar que el commit desplegado es el commit entregado (HEAD en el
      servidor) y que el sitio está quieto; si hay despliegue en curso, no
      auditar: avisar y esperar.
- [ ] Localizar el respaldo previo a la tanda y verificar que existe en disco.
- [ ] Anotar la cuenta, el plan/nivel y el juego de datos de prueba usados;
      el veredicto depende de con qué se probó.

## Funcional

- [ ] Recorrer el flujo completo como usuario real: entrar, operar, guardar,
      exportar y reabrir — no solo mirar la pantalla donde «aterrizó» el arreglo.
- [ ] Verificar el valor GUARDADO detrás de la pantalla (base de datos o
      estado interno), no solo lo que la pantalla muestra: un desplegado
      redondeado puede esconder un valor guardado incorrecto.
- [ ] Dinero: recalcular a mano en ambos sentidos, por persona y en total, y
      conciliar entre pantallas, totales y archivos exportados.
- [ ] Abrir los archivos exportados y contar líneas y totales; una pantalla
      correcta puede exportar registros distintos.
- [ ] Probar más allá del ejemplo nombrado por el desarrollador: otro
      registro, otro periodo, otro monto. Un arreglo que solo pasa el ejemplo
      citado es **parcial**.

## Datos e integridad

- [ ] Conteos antes/después contra el respaldo: 0 registros perdidos salvo
      fusiones aprobadas; 0 registros nuevos inesperados.
- [ ] Registros protegidos (reclamados, verificados, pagados) intactos.
- [ ] Redirecciones: probar en vivo las URLs viejas — 301 hacia el destino y
      200 al final; contar cuántas quedaron sin redirección y por qué.
- [ ] Sitemap y robots coherentes con lo construido (sin URLs muertas ni
      slugs ya redirigidos, si la tanda toca URLs o SEO).

## Visual y responsive (ambas vistas, siempre)

- [ ] Móvil primero (390×844, DPR 2): textos completos sin truncar, letra
      grande y legible, sin desborde horizontal, objetivos táctiles ≥48 px,
      economía de contenedores (nada de cajas dentro de cajas sin motivo).
- [ ] PC (1440×900): la misma información, proporcionada a la vista — la
      tipografía es responsive, no una sola talla heredada del móvil.
- [ ] Capturas de página completa: hacer scroll hasta abajo y esperar antes
      de capturar; las imágenes con `loading="lazy"` salen en blanco sin
      scroll y eso es un artefacto de la captura, NO un defecto.
- [ ] Revisar cada imagen generada o subida: texto inventado en letreros,
      logos deformados o lugares equivocados invalidan la imagen.

## Técnica

- [ ] Errores en consola y peticiones fallidas durante el flujo.
- [ ] Enlaces y botones de la zona tocada, uno por uno.
- [ ] Correr la suite completa en el entorno auditado cuando sea posible;
      el «verde» del desarrollador se confirma, no se hereda.
- [ ] Pruebas inestables (flaky): prohibido reintentar hasta que pasen o
      agregar esperas para disimularlas; se encuentra la causa raíz o se
      borra la prueba dejando el motivo escrito.

## Re-auditorías

- [ ] Apuntar a los puntos fallidos y a la regresión de la zona tocada,
      apoyándose en las rondas anteriores; no re-checar todo desde cero
      salvo sospecha fundada.
- [ ] Si un punto suma su tercera ronda sin pasar, detener la iteración y
      escalarlo a Antonio con el resumen del desacuerdo.

## Cierre

- [ ] Veredicto por punto: corregido / parcial / no corregido / no
      verificable — ningún punto sin veredicto, con evidencia breve y conteo final.
- [ ] Publicar el veredicto en el issue (formato B de `ISSUE_TEMPLATE.md`) y
      dar el timbre al desarrollador si hay correcciones.
- [ ] Si todo quedó corregido: luz verde → aplicación a producción →
      re-verificación en producción → cerrar el issue.
- [ ] Registrar el resultado durable en memoria (qué quedó, con qué commit,
      qué sigue abierto).
