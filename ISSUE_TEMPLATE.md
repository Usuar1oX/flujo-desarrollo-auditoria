# Formatos de issue del puente de auditoría

El issue es el registro compartido de la ronda: lo leen Antonio, Muse y el
desarrollador. Sin contraseñas, sin datos reales; solo datos de prueba.

## A) Entrega del desarrollador — título: «Listo para auditar: <tanda>»

```
## URL a revisar
<URL del entorno de pruebas (y de producción solo si ya hubo luz verde previa)>

## Commits
- <hash corto> — <qué hace>

## Afirmaciones verificables
1. <Afirmación concreta y comprobable.>
2. <Afirmación concreta y comprobable.>
…

## Conteos antes / después
- <Registros antes: n → después: n. Respaldos en: <ruta>.>

## Suite
- <n> pruebas, <n> aserciones, en verde. Comando: <…>

## Evidencia adjunta
<Capturas, archivos exportados o salidas que respaldan las afirmaciones.
Una afirmación sin evidencia se audita como «no verificable» hasta tenerla.>

## Sitio quieto
Confirmo que no hay despliegues en curso y el entorno queda quieto para la auditoría.
```

Reglas: una afirmación por hecho comprobable (nada de «se mejoró la vista»);
si un punto quedó a medias, se declara a medias en la propia entrega.

## B) Veredicto de Muse — comentario en el mismo issue

```
## Veredicto de auditoría — <tanda>

1. <Afirmación> — **corregido** / **parcial** / **no corregido** / **no verificable**
   Severidad si no quedó corregido: **bloqueante** / **menor** / **detalle** /
   **preexistente** (preexistente = el defecto ya estaba antes de la tanda; no
   se le carga a esta tanda, se anota para su propia tanda).
   Evidencia: <pasos, valores exactos, conteos, URL o captura.>
2. …

**Conteo final:** de N puntos: X corregidos, Y parciales, Z no corregidos, W no verificables.

<Si todo quedó corregido: «LUZ VERDE para aplicar a producción.»>
<Si no: «Correcciones requeridas:» lista numerada, una por punto fallido.>
```

Reglas: ningún punto sin veredicto; la evidencia manda sobre la afirmación;
el issue se cierra SOLO cuando todos los puntos están «corregido» y la
verificación en producción también pasó.

## C) Hallazgo nuevo de Muse (discrepancia fuera de entrega)

```
## Hallazgo: <título corto>

**Qué se pidió** (condición n.º <n> del plan / acuerdo de <fecha>):
<texto>

**Qué se entregó / qué se observa:**
<texto + URL exacta>

**Evidencia:**
<captura, valores, conteos, pasos para reproducir>

**Corrección esperada:**
<qué debe quedar true al re-auditar>
```

## D) Contestación del desarrollador — cuando no está de acuerdo con un hallazgo

```
## Contestación — punto <n> de <tanda / issue>

**Postura:** lo contesto, no lo corrijo.
**Justificación:** <mecanismo, evidencia o trade-off que lo respalda.>
**Propuesta:** cerrarlo como trade-off aceptado, con esta justificación citada.
```

Reglas: contestar es válido solo con justificación técnica y evidencia, nunca
con «así está bien». Si Muse y Antonio aceptan la contestación, el punto se
cierra como **trade-off aceptado** en el veredicto, citando la justificación;
si no se acepta, el punto sigue como corrección requerida.
