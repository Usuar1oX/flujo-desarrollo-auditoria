# Plantilla — Condiciones de satisfacción de una tanda

Copiar, rellenar y discutir entre Antonio, Muse y el desarrollador ANTES de
construir. Una condición que no se puede verificar no sirve: cada punto debe
poder comprobarse en vivo con un dato, una pantalla o un conteo.

## Objetivo (1–2 líneas)

<Qué se logra con esta tanda y para quién.>

## Alcance

**Cambia:**
- <…>

**NO cambia:**
- <Pantallas, rutas o datos que quedan intactos.>

## Condiciones numeradas

1. <Condición medible.> — Verificación: <dónde se mira, con qué cuenta/dato,
   qué valor exacto se espera.>
2. <Condición medible.> — Verificación: <…>
3. <…>

## Vistas

- Móvil (390×844): <qué debe verse/funcionar; letra legible, sin textos
  truncados, objetivos táctiles ≥48 px, sin desborde horizontal.>
- PC (1440×900): <qué debe verse/funcionar.>
- Tipografía responsive: los tamaños se adaptan a la vista; no se hereda una
  sola talla para ambas.

## Datos e integridad

- Conteo antes de la tanda: <n registros / fichas / lo que aplique.>
- Conteo esperado después: <n; 0 pérdidas salvo las fusiones listadas.>
- Registros protegidos que NO se tocan: <reclamados, verificados, pagados…>
- Toda ficha/registro removido deja redirección permanente (301) a su destino:
  <sí/no y a dónde.>
- Respaldo previo obligatorio: <ruta del respaldo.>

## Invariantes (lo que nunca puede romperse)

- <Ej.: los conteos nunca bajan; aplicar la tanda dos veces produce el mismo
  resultado que aplicarla una (idempotencia); ningún registro puede quedar
  sin <X>; los saldos nunca son negativos; toda ficha removida responde 301.>

## Oráculo diferencial

- El estado anterior (el respaldo) es el oráculo: se compara lo mismo antes y
  después de la tanda, y TODA diferencia fuera de la lista aprobada de cambios
  cuenta como defecto, aunque la suite esté en verde.

## Archivos que se espera tocar (si el cambio es de código)

- Crear: <…>
- Modificar: <…>
- Borrar: <…>

(Todo archivo tocado fuera de esta lista se explica en la entrega o cuenta
como desviación del plan; el diff también se audita.)

## Entorno y suite

- Se construye SOLO en pruebas hasta la luz verde de Muse.
- Suite completa corrida por el desarrollador: <n pruebas / n aserciones, verde.>
- Al entregar: sitio quieto declarado (sin despliegues en curso).

## Fuera de alcance (explícito)

- <Lo que esta tanda NO resuelve, para que nadie lo dé por hecho.>

## Criterio de aceptación final

Todas las condiciones numeradas verificadas por Muse en pruebas con veredicto
«corregido»; después, aplicación a producción y re-verificación en producción.
