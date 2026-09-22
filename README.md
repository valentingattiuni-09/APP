# Ronda

**La app de mensajería donde hablás con tu gente, sin tu familia adentro y sin dar tu número.**

> ⚠️ **Estado: Fase 0 — Validación.** Todavía no hay código de producto, y es a propósito.
> Primero se confirma que un grupo real aguanta una semana hablando fuera de WhatsApp. Ver [`docs/02-fase-0.md`](docs/02-fase-0.md).

> 🔄 **Septiembre 2026 — pivot.** La cuña ya no son los comercios: son los jóvenes. El porqué está en [`docs/01-vision.md`](docs/01-vision.md) §3. Los comercios no se descartan: pasan de ser la puerta de entrada a ser la monetización, en la Fase 3.

---

## El problema

WhatsApp tiene entre 92% y 99% de penetración en Argentina. Dejó de ser una app: es infraestructura. Y en el camino se volvió **la app de los adultos** — el grupo de la familia, el del consorcio, el del trabajo, el del curso con las madres.

La conversación entre jóvenes argentinos ya se está yendo de ahí, a los DM de Instagram, a Discord, a Telegram. Nadie construyó todavía un producto pensado para ese éxodo.

## La apuesta

No competimos por reemplazar WhatsApp para todo el país: eso se pierde por efecto red, no por producto. Competimos por **ser donde ocurre la conversación de los menores de 25 años**, que es el único segmento que en la historia de la mensajería se mudó de verdad.

Y la clave operativa:

> **La unidad de migración no es la persona. Es el grupo.**

No hace falta que se mude el país. Hace falta que se mude un curso, un equipo, una banda de seis amigos — y eso pasa en una semana si el producto es claramente mejor para ese grupo.

## Los cinco diferenciales

1. **Sos un `@`, no un número** — hablás con alguien sin darle el teléfono. Y sin SMS obligatorio, el costo por usuario se desploma.
2. **Rondas: grupos con temas adentro** — `#general`, `#parcial`, `#memes`. Seguís uno y silenciás el otro sin irte del grupo.
3. **Lo efímero es una perilla visible** — se guarda / 24 h / al leer, arriba de cada conversación.
4. **Sin “en línea”, sin “últ. vez”** — no están apagados: no existen. Y el tilde de leído es simétrico.
5. **Audios con transcripción** — el audio de siete minutos deja de ser una condena.

## Documentación

| Documento | Qué contiene |
|---|---|
| [`docs/01-vision.md`](docs/01-vision.md) | Documento fundacional: el problema, por qué los jóvenes y no los comercios, el producto, cómo se rompe el arranque en frío, modelo de negocio, roadmap, arquitectura, costos, legal y riesgos |
| [`docs/02-fase-0.md`](docs/02-fase-0.md) | Guía de validación: las 20 entrevistas, la migración de un grupo real durante una semana, los trámites y el criterio de salida |
| [`docs/03-producto.md`](docs/03-producto.md) | Qué se construye: los cuatro objetos, las seis pantallas de la Fase 1, y la lista explícita de lo que **no** se construye |
| [`docs/04-menores-y-seguridad.md`](docs/04-menores-y-seguridad.md) | El riesgo número uno del pivot: edad mínima, diseño contra el contacto de desconocidos, moderación, protocolo ante un incidente grave y marco legal |
| [`prototipo/`](prototipo/) | El prototipo jugable, para las entrevistas |

---

## El prototipo

Una sola página, sin dependencias ni backend. Se abre en el teléfono de la persona entrevistada y se juega: el alta con `@`, la ronda que se abre a los cinco, los temas adentro del grupo, los audios con transcripción y la perilla de efímero.

- **Verlo:** abrir [`prototipo/index.html`](prototipo/index.html) en el navegador. No necesita servidor.
- **Publicado:** `https://valentingattiuni-09.github.io/APP/prototipo/`
- **Botón “Notas”:** superpone la explicación de cada pantalla. **Va apagado por default y así hay que mostrarlo en una entrevista** — la Fase 0 dice explícitamente que no se explica nada: si no se entiende solo, el problema es de comunicación, no de idea.
- **Botón “Reiniciar”:** vuelve al principio entre una entrevista y la siguiente.

No guarda nada ni manda nada a ningún lado.

---

## Publicar

El repo se publica solo en GitHub Pages con cada push a `main`, mediante [`.github/workflows`](.github/workflows). Queda en `https://valentingattiuni-09.github.io/APP/`.

> ⚠️ **`index.html` en la raíz quedó desactualizado con el pivot.** Es la landing de pre-registro para comercios del borrador 1 y hoy contradice la estrategia. Hay que reescribirla para el público joven — y el titular tiene que salir de las frases textuales de las 20 entrevistas, no de nuestra imaginación (ver `docs/02-fase-0.md`). Mientras tanto, conviene no difundir la URL raíz.

## Principios innegociables

> **A nadie se le escribe sin que lo haya pedido.**
> **A nadie se lo agrega sin que acepte.**
> **Nadie te encuentra si vos no le diste tu `@`.**

Sin publicidad, sin vender datos, sin algoritmo que decida qué ves, sin escanear mensajes privados.

## Roadmap

- **Fase 0** · Validación — 3 semanas ← *estamos acá: prototipo listo, faltan las 20 entrevistas y la migración de un grupo*
- **Fase 1** · El mensajero, publicado en App Store y Play Store — 8-10 semanas
- **Fase 2** · Lo social: efímero, stickers, estados, llamadas — 6-8 semanas
- **Fase 3** · Densidad y primeros pesos: Ronda+ y Ronda Negocios
- **Fase 4** · Cifrado de punta a punta, multi-dispositivo, pagos

## Stack previsto (Fase 1)

React Native + Expo (iOS y Android desde un solo código) · Node + TypeScript · PostgreSQL · WebSocket + Redis · Expo Push · Whisper para la transcripción de audios

---

*Proyecto de [Sobra — Agencia de Marketing Digital](https://github.com/valentingattiuni-09/Sobra-Agencia-de-marketing-digital-).*
