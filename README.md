# Ronda

**La app donde hablás con tu gente todos los días, y al otro día no quedó nada.**

> ⚠️ **Estado: Fase 0 — Validación.** Todavía no hay código de producto, y es a propósito.
> Primero se confirma que un grupo real aguanta una semana hablando fuera de WhatsApp. Ver [`docs/02-fase-0.md`](docs/02-fase-0.md).

> 🔄 **Septiembre 2026 — dos cambios de rumbo.** Primero, la cuña dejó de ser los comercios y pasó a ser los jóvenes ([`01-vision.md`](docs/01-vision.md) §3); los comercios no se descartan, pasan a ser la monetización de la Fase 3. Después, **todo se vence a las 24 horas** ([`05-mecanica.md`](docs/05-mecanica.md)), y con eso Ronda dejó de pelear por reemplazar a WhatsApp: se instala al lado.

---

## El problema

WhatsApp tiene entre 92% y 99% de penetración en Argentina. Dejó de ser una app: es infraestructura. Y en el camino se volvió **la app de los adultos** — el grupo de la familia, el del consorcio, el del trabajo, el del curso con las madres.

La conversación entre jóvenes argentinos ya se está yendo de ahí, a los DM de Instagram, a Discord, a Telegram. Nadie construyó todavía un producto pensado para ese éxodo.

## La apuesta

No competimos por reemplazar WhatsApp: eso se pierde por efecto red, no por producto. **No le pedimos a nadie que se mude.** Ronda se instala al lado y le pelea el rato, no la agenda — y el que tiene que aflojar terreno no es WhatsApp, es el DM de Instagram.

Dos claves operativas:

> **Todo se vence a las 24 horas, a una hora fija, la misma para todo el grupo.**
> **La unidad de migración no es la persona. Es el grupo.**

## Los seis diferenciales

0. **Todo se vence** — la ronda cierra a una hora fija y se borra lo del día. Lo que querés salvar, lo guardás a mano, y guardar tiene cupo.
1. **Una notificación por día** — una hora antes de que cierre, diciendo qué se va a perder. De mensajes nuevos, ninguna. Ni una.
2. **Sos un `@`, no un número** — hablás con alguien sin darle el teléfono. Y sin SMS obligatorio, el costo por usuario se desploma.
3. **Rondas: grupos con temas adentro** — `#general`, `#previa`, `#memes`. Seguís uno y silenciás el otro sin irte del grupo.
4. **Sin “en línea”, sin “últ. vez”** — no están apagados: no existen. Y el tilde de leído es simétrico.
5. **Audios con transcripción, y que salen como video** — listo para subir a TikTok. Cada video exportado lleva la marca adentro: es el motor de crecimiento, no una comodidad.

## Documentación

| Documento | Qué contiene |
|---|---|
| [`docs/01-vision.md`](docs/01-vision.md) | Documento fundacional: el problema, por qué los jóvenes y no los comercios, el producto, cómo se rompe el arranque en frío, modelo de negocio, roadmap, arquitectura, costos, legal y riesgos |
| [`docs/02-fase-0.md`](docs/02-fase-0.md) | Guía de validación: las 20 entrevistas, la migración de un grupo real durante una semana, los trámites y el criterio de salida |
| [`docs/03-producto.md`](docs/03-producto.md) | Qué se construye: los cuatro objetos, las seis pantallas de la Fase 1, y la lista explícita de lo que **no** se construye |
| [`docs/04-menores-y-seguridad.md`](docs/04-menores-y-seguridad.md) | El riesgo número uno: edad mínima, diseño contra el contacto de desconocidos, moderación, protocolo ante un incidente grave y marco legal |
| [`docs/05-mecanica.md`](docs/05-mecanica.md) | **El motor del producto:** el vencimiento, la hora de la ronda, guardar con cupo, la notificación única, las rachas, el audio→video, y la discusión honesta sobre retención por pérdida |
| [`docs/06-el-juego.md`](docs/06-el-juego.md) | **El torneo de los US$ 10.000:** cuántos mensajes pedir y por qué, los números del pozo como porcentaje de lo que entra, el problema de la edad, el fraude y la lista para el abogado |
| [`prototipo/`](prototipo/) | El prototipo jugable, para las entrevistas |

---

## El prototipo

Una sola página, sin dependencias ni backend. Se abre en el teléfono de la persona entrevistada y se juega: el alta con `@`, la ronda que se abre a los cinco, la cuenta regresiva de cada mensaje, guardar con cupo, la foto de una sola vez, el audio convertido en video para TikTok y la notificación de cierre.

- **Verlo:** abrir [`prototipo/index.html`](prototipo/index.html) en el navegador. No necesita servidor.
- **Publicado:** `https://valentingattiuni-09.github.io/APP/prototipo/`
- **Botón “Notas”:** superpone la explicación de cada pantalla. **Va apagado por default y así hay que mostrarlo en una entrevista** — la Fase 0 dice explícitamente que no se explica nada: si no se entiende solo, el problema es de comunicación, no de idea.
- **Botón “Aviso”:** dispara la notificación diaria de cierre, que es lo más difícil de explicar con palabras y lo más fácil de entender viéndola.
- **Botón “Reiniciar”:** vuelve al principio entre una entrevista y la siguiente.

No guarda nada ni manda nada a ningún lado.

---

## La landing

[`index.html`](index.html) es la página de pre-registro, y es donde cae el tráfico de TikTok. Pide mail, edad y —lo que más importa— **con qué grupo entrarías y cuántos son**: la unidad de migración es el grupo, así que la lista de espera también tiene que serlo.

### Antes de compartirla, dos cosas

**1. Conectar el formulario.** Sin esto la página se ve bien pero **no guarda los registros**. Está hecho a propósito: prefiere avisar que falta configurarlo antes que tragarse un contacto en silencio.

1. Entrá a [formspree.io](https://formspree.io) y creá una cuenta (el plan gratis alcanza para la validación).
2. Creá un formulario nuevo. Te va a dar una URL tipo `https://formspree.io/f/xxxxxxxx`.
3. Abrí `index.html`, buscá `const FORM_ENDPOINT = "";` y pegá la URL entre las comillas.

**2. Cambiar el titular por uno que no sea nuestro.** El que está ahora es un marcador de posición. Según [`docs/02-fase-0.md`](docs/02-fase-0.md), el titular tiene que salir de **las frases textuales de las 20 entrevistas**, no de nuestra imaginación. Anotá lo que digan, literal, y usá eso.

> ⚠️ **El torneo aparece como plan, no como convocatoria.** La sección dice explícitamente que todavía no está abierto y que cuando arranque va a tener bases y condiciones. **No cambiar eso por una convocatoria hasta tener las bases publicadas y la consulta legal hecha** ([`docs/06-el-juego.md`](docs/06-el-juego.md) §8): anunciar un premio de US$ 10.000 a un público que incluye menores, sin bases, es el tipo de cosa que se arregla caro.

## Publicar

El repo se publica solo en GitHub Pages con cada push a `main`, mediante [`.github/workflows`](.github/workflows). La landing queda en `https://valentingattiuni-09.github.io/APP/` y el prototipo en `/APP/prototipo/`.

## Principios innegociables

> **A nadie se lo agrega sin que acepte.**
> **Nadie te encuentra si vos no le diste tu `@`.**
> **Presión para aparecer, sí. Castigo por irte, no.**

Sin publicidad, sin vender datos, sin algoritmo que decida qué ves, sin escanear mensajes privados, sin notificaciones inventadas y sin cobrar por recuperar nada de lo que se venció.

## Roadmap

- **Fase 0** · Validación — 3 semanas ← *estamos acá: prototipo listo, faltan las 20 entrevistas y la migración de un grupo*
- **Fase 1** · El mensajero con el motor de vencimiento, publicado en App Store y Play Store — 8-10 semanas
- **Fase 2** · Lo social: rachas, audio→video, stickers, llamadas — 6-8 semanas
- **Fase 3** · Densidad y primeros pesos: Ronda+, el torneo mensual y Ronda Negocios
- **Fase 4** · Cifrado de punta a punta, multi-dispositivo, pagos

## Stack previsto (Fase 1)

React Native + Expo (iOS y Android desde un solo código) · Node + TypeScript · PostgreSQL · WebSocket + Redis · Expo Push · Whisper para la transcripción de audios

---

*Proyecto de [Sobra — Agencia de Marketing Digital](https://github.com/valentingattiuni-09/Sobra-Agencia-de-marketing-digital-).*
