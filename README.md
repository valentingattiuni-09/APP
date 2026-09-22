# Eco

**Tus audios, pero que se puedan postear.**

App de mensajería argentina para 14 a 20 años. Cualquier audio se convierte en un video vertical con subtítulos, listo para subir a TikTok. Sin visto. Sin desconocidos. Solo por invitación.

> ⚠️ **Estado: Fase 0 — Validación.** No hay código de producto todavía, y es a propósito.
> Antes van 30 conversaciones con pibes de 14 a 20. Ver [`docs/02-crecimiento.md`](docs/02-crecimiento.md) §7.

---

## La apuesta

WhatsApp tiene entre 92% y 99% de penetración en Argentina. Ningún adulto se cambia de app de mensajería: tiene ahí el trabajo, la familia, el médico.

**Los adolescentes son el único público que sí se muda.** Su red es densa, local y chica: si se mudan cuatro del curso, se mudan todos. Y quieren un lugar donde no estén los grandes. Es exactamente cómo entraron Snapchat, Instagram, TikTok y BeReal.

Pero ninguna de esas ganó por ser "una versión mejor" de la anterior. Ganaron por habilitar **una conducta nueva que la incumbente no podía copiar sin romperse.** La nuestra: convertir un audio privado en una pieza pública de un toque.

## Documentación

| Documento | Qué contiene |
|---|---|
| [`docs/01-vision.md`](docs/01-vision.md) | Documento fundacional: la estrategia, el mecanismo, el bucle de crecimiento, roadmap, modelo de negocio, riesgos y métricas |
| [`docs/02-crecimiento.md`](docs/02-crecimiento.md) | Cómo se viraliza de verdad: el bucle, la estrategia de un colegio a la vez, el playbook de TikTok y la Fase 0 |
| [`docs/03-menores-y-seguridad.md`](docs/03-menores-y-seguridad.md) | **Se lee antes de escribir código.** Qué implica operar una app con menores: arquitectura, moderación, CSAM, marco legal argentino y requisitos de las tiendas |
| [`index.html`](index.html) | La landing de lista de espera |

## Dos decisiones que sostienen todo

**1. No existe la búsqueda de personas.** Sin buscador, sin perfiles públicos, sin recomendaciones. Solo entrás si alguien te invita. Es a la vez la principal medida de seguridad (elimina el vector de grooming) y el motor de crecimiento (crece en racimos densos, no disperso). Que sean la misma cosa es lo mejor que tiene este diseño.

**2. La viralidad va en el producto, no en la campaña.** Poner plata en TikTok antes de que el bucle gire trae gente a una app vacía y quema el momento. El orden es: bucle → densidad en un colegio → réplica → recién ahí pauta.

## Roadmap

- **Fase 0** · Validación — 3 semanas ← *estamos acá: landing lista, faltan las 30 charlas*
- **Fase 1** · MVP con "Hacele Eco", publicado en App Store y Play Store — 10-12 semanas
- **Fase 2** · Grupos por colegio e invitaciones con código — 6 semanas
- **Fase 3** · Crecimiento, un colegio a la vez
- **Fase 4** · Monetización: Eco Negocios
- **Fase 5** · Llamadas, cifrado de punta a punta, multi-dispositivo

## Stack previsto

React Native + Expo (iOS y Android desde un solo código) · Node + TypeScript · PostgreSQL · WebSocket + Redis · Expo Push

---

## Publicar la landing

Ya está publicada y **se republica sola en cada push a `main`** vía [`.github/workflows/pages.yml`](.github/workflows/pages.yml). No hay que tocar nada en Settings.

👉 **https://valentingattiuni-09.github.io/APP/**

### Falta conectar el formulario

Sin esto la página se ve bien pero **no guarda los registros**. Está hecho a propósito: prefiere avisar que falta configurarlo antes que tragarse un contacto en silencio.

1. Cuenta gratis en [formspree.io](https://formspree.io)
2. Creás un formulario, te dan una URL tipo `https://formspree.io/f/xxxxxxxx`
3. En `index.html`, buscá `const FORM_ENDPOINT = "";` y pegala entre las comillas

---

## Historial

El borrador 1 apuntaba a comercios: venderles un canal de mensajería propio que Meta no les pudiera cerrar. Sigue siendo una buena estrategia y **vuelve como Fase 4** (monetización). Está completo en el historial de git.

*Proyecto de [Sobra — Agencia de Marketing Digital](https://github.com/valentingattiuni-09/Sobra-Agencia-de-marketing-digital-).*
