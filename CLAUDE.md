# CLAUDE.md — Magnesio (demo gimnasio)

Web demo de un gimnasio de barrio ficticio en Delicias, Zaragoza (fuerza, clases dirigidas, entrenamiento personal) para enseñar a dueños de gimnasios y boxes. Todo empuja a reservar la clase de prueba gratis; sin backend.

## Stack

- Un único `index.html`: HTML + CSS + JS sin frameworks ni build
- Google Fonts: Big Shoulders Display (titulares estampados) + Archivo (texto)
- Fotos de Unsplash en `img/*.webp` (descargadas y convertidas con `sharp` de `Crear_pagina2/node_modules`)
- Hosting: Cloudflare Pages, proyecto `demo-gym` (despliegue con wrangler)

## Arquitectura

```
index.html   <style> con tokens en :root (claro = hormigón, oscuro = caucho) → secciones → <script>
             con DATOS arriba (GIMNASIO, ENTRENADORES, CLASES, TARIFAS, PASOS, PREGUNTAS, CREDITOS)
img/         19 fotos WebP (portada, clases, entrenadores, gimnasio)
PRODUCT.md   Contexto de producto para la skill impeccable
README.md    Qué es, cómo editar datos, cómo desplegar
```

Dirección de arte "Magnesio sobre caucho": portada con titular estampado (WAAPI + nube de polvo en canvas)
y una barra olímpica que se carga de discos al hacer scroll (contador de kg) → horario como pizarra de tiza
(filtros por disciplina con número, entrenador y día; vista previa que sigue al cursor; ficha `<dialog>` con
anterior/siguiente y "Quiero probar esta") → entrenadores como fichas pegadas con cinta → tarifas como
tarjetas de socio perforadas con sello "Plazas libres/Completo" → el gimnasio (filosofía, instalaciones,
mapa dibujado que enlaza a Google Maps) → carril de suelo con cinta amarilla para los pasos → FAQ con
`<details>` → reserva amarilla como hoja de registro (arma texto para wa.me o mailto) → pie con el nombre a
ancho completo. Un solo acento: amarillo de marca de suelo `#FFC400`.

## Comandos

- Ver en local: doble clic en `index.html`, o `npx http-server GYM -p 5180` desde la raíz (está en `.claude/launch.json` como `gym`).
- Detector de diseño: `sh ~/.claude/skills/impeccable/scripts/impeccable detect --json index.html` (quedan 4 "cramped-padding" falsos positivos de secciones a sangre y el aviso del mapa SVG, que es intencionado).
- Desplegar: `npx wrangler pages deploy . --project-name demo-gym --branch main` (desde `GYM/`).
- Repo: https://github.com/AleexX26/demo-gym (rama `main`). Web: https://demo-gym-a1v.pages.dev
- Ojo: el proyecto de Pages es de subida directa (wrangler), no está conectado a Git: un push NO publica; hay que repetir el `wrangler pages deploy`.

## Cómo editar

- Clase nueva: copiar un bloque de `CLASES`. `disciplina` crea su filtro; `entrenador` debe coincidir con un `nombre` de `ENTRENADORES`; `imagen: ""` dibuja una ilustración SVG.
- Entrenador sin foto: `foto: ""` (Marta Lozano está así a propósito para enseñar la ilustración).
- Color: `GIMNASIO.acento` (claro, lleva texto negro encima).

## Decisiones

- 2026-10-15: Cloudflare Pages `demo-gym` creado con `wrangler pages project create --force` (wrangler 4.151 intenta convertir Pages en Workers y falla sin `--force`; solo hace falta la primera vez). URL asignada: demo-gym-a1v.pages.dev (demo-gym.pages.dev ya estaba cogido).
- 2026-10-15: fotos reales de Unsplash (licencia libre) en vez de solo SVG, a petición del usuario ("que se vea realista, acogedor"). Pinterest descartado por derechos. Sin culturistas; se eligió una sesión coherente (@silverkblack) con luz natural y entrenador corrigiendo técnica.
- 2026-10-15: nombre ficticio "Magnesio" (Delicias, Zaragoza): el nombre es el hilo de la dirección de arte (polvo de magnesio, cursor, sello).
- 2026-10-15: un solo HTML sin Astro/React; todo se hace bien con CSS + WAAPI + View Transitions (filtro del horario).
- 2026-10-15: la máscara de "desgaste" de los titulares recorta lo que sale de la caja; la clase `.con-tilde` (padding-top .14em + margen negativo) deja sitio a las tildes de Á/Í.
- 2026-10-15: `html` y `.portada` con `overflow-x: clip`: los discos entran desde fuera de pantalla y en móvil provocaban scroll horizontal.
- 2026-10-15: sin gradientes ni clip-path orgánicos (detector de impeccable): perforaciones de las tarjetas con `<i>` redondos y cintas cortadas en diagonal.

## Patrones reutilizables

- **ilustracion(texto, persona)**: SVG en línea (disco de competición + nombre a tiza) para lo que no tiene foto; usa las fuentes y tokens de la página. En `index.html`.
- **barraOlimpica()**: discos que entran por tramos según el scroll de la portada y suman kg. En `index.html`.
- **polvo(x, y, n)**: partículas de magnesio en un canvas fijo (titular, cursor, clics). En `index.html`.
- **elegir({ interes, entrenador })**: rellena la reserva desde una clase, un entrenador o un plan y baja hasta ella. En `index.html`.

## Última actualización

2026-10-15
