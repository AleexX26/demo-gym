# Magnesio · demo de web para gimnasio

Web de demostración de un gimnasio de barrio ficticio (fuerza, clases dirigidas y entrenamiento personal) para enseñar a dueños de gimnasios y boxes. Es una sola página estática (`index.html`), sin compilación ni servidor: horario filtrable con ficha ampliada, entrenadores, tarifas como tarjetas de socio, preguntas frecuentes y una reserva de clase de prueba que redacta el mensaje de WhatsApp o el email.

## Cómo editar los datos

Abre `index.html` y ve al principio del `<script>` (al final del archivo). Están todas las listas:

| Lista | Qué cambia |
| --- | --- |
| `GIMNASIO` | Nombre, ciudad, dirección, horario, email, WhatsApp, Instagram, color de acento, instalaciones |
| `ENTRENADORES` | Nombre, especialidad, frase, disciplinas, certificaciones, Instagram y foto |
| `CLASES` | Nombre, disciplina, entrenador, día, hora, duración, intensidad (1–3), descripción e imagen |
| `TARIFAS` | Nombre, precio, periodo, qué incluye y si hay plazas (`disponible: true/false`) |
| `PASOS`, `PREGUNTAS` | Los pasos de "Así se empieza aquí" y las preguntas frecuentes |

- Para añadir algo, copia un bloque `{ ... },`, pégalo debajo y cambia los valores. Los filtros de disciplina, entrenador y día se generan solos.
- Si una clase o un entrenador no tiene foto (`imagen: ""` o `foto: ""`), se dibuja una ilustración con su nombre.
- Las fotos van en `img/` (WebP, unos 1400 px de ancho). Cambia la ruta en el dato correspondiente.
- El título de la pestaña y la descripción para Google están en el `<head>`.
- El color de acento es `GIMNASIO.acento`; tiene que ser claro porque lleva texto negro encima.

## Ver en local

Doble clic en `index.html`, o con un servidor:

```bash
npx http-server . -p 5180
```

## Desplegar

Es un sitio estático: sin comando de build y con la raíz como directorio de salida.

- **Cloudflare Pages (con wrangler):** `npx wrangler pages deploy . --project-name demo-gym --branch main`
- **Cloudflare Pages (desde GitHub):** Workers y Pages → Crear → Pages → Conectar a Git → este repositorio, rama `main`, preajuste "Ninguno", comando de build vacío, directorio de salida `/`. Cada push a `main` se publica solo.

## Créditos

Fotos de [Unsplash](https://unsplash.com) (licencia Unsplash): @silverkblack, @victorfreitas, @tcraye, @yellowteapot, @markadriane, @sunday2sunday, @c7arb, @betaboulders, @rmrdnl, @laurar1vera, @tjsocoz, @alexsaks, @herickson7. Son fotos de archivo: sustitúyelas por las del gimnasio real. Gimnasio, personas y datos de contacto son ficticios.
