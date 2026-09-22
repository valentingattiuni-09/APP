# Fase 0 — Validación

> **Duración:** 3 semanas · **Costo:** casi cero · **Regla:** no se escribe código de producto hasta terminarla.
> **Cambió con el pivot:** ya no se valida con comercios. Se valida con jóvenes, y la prueba principal no es una entrevista: es una migración real.

El objetivo no es confirmar que la idea es buena. Es **descubrir rápido y barato si es mala**, antes de gastar diez semanas de desarrollo.

---

## Lo que hay que averiguar

Tres preguntas, en orden de importancia. Si la primera da que no, las otras dos no importan.

| # | Pregunta | Cómo se contesta |
|---|---|---|
| **1** | ¿Un grupo real aguanta una semana hablando fuera de WhatsApp? | La migración de la semana 2. Es la única prueba que no se puede simular. |
| **2** | ¿El dolor que suponemos es el dolor que tienen? | Las 20 entrevistas. |
| **3** | ¿Cuál de los cinco diferenciales es el que los mueve? | Las 20 entrevistas, con el prototipo en la mano. |

> **La pregunta 1 es el proyecto entero.** Todo lo demás es color. Un grupo que vuelve a WhatsApp el jueves es un resultado más valioso que cien encuestas que digan "me encantaría una app así".

---

## Semana 1 · Las veinte conversaciones

### A quién buscar

Personas de **16 a 24 años**, argentinas, que usen el teléfono todo el día. No hace falta que odien WhatsApp: hace falta que hablen con sus amigos por otro lado.

Buscar un mix deliberado:

- **8 universitarios** — con grupo de comisión activo
- **5 de secundario (mayores de 16)** — con grupo de curso
- **4 de un club, equipo o escena** — banda, productora, equipo amateur, gaming
- **3 que NO se quejen de WhatsApp** — los conformes. Si el dolor es real, aparece igual cuando se pregunta bien. Si sólo aparece en los que ya se quejaban, el mercado es más chico de lo que parece.

Dónde están: la facultad propia, hermanos menores y sus amigos, clubes de barrio, servidores de Discord argentinos, comunidades de gaming, grupos de la agencia.

### Cómo preguntar

Quince minutos. **No mostrar Ronda hasta la pregunta 9.** Si se muestra antes, la persona contesta por amabilidad y el dato queda contaminado.

**Sobre el hábito real (sin mencionar Ronda):**

1. Abrime el teléfono: ¿cuáles son las últimas cinco conversaciones que tuviste y en qué app? *(Esto vale más que cualquier respuesta declarada. Se mira, no se pregunta.)*
2. ¿Con tus amigos más cercanos hablás por WhatsApp o por otro lado? ¿Por qué ahí?
3. ¿Cuántos grupos de WhatsApp tenés silenciados? ¿Por qué no te fuiste?
4. ¿Alguna vez te agregaron a un grupo sin preguntarte? ¿Qué hiciste?
5. ¿Hay algo que no dirías por WhatsApp? ¿Dónde lo decís?
6. Cuando conocés a alguien nuevo, ¿le das el número o el Instagram? ¿Por qué?
7. ¿Alguien de tu familia está en tus grupos de amigos?
8. Contame la última vez que un audio largo te hinchó las pelotas.

**Recién acá se muestra el prototipo** (`../prototipo/`, se abre en el teléfono de ellos):

9. Mirá esto y decime qué te parece que es. *(Sin explicar nada. Si no lo entienden solo, el producto tiene un problema de comunicación, no de idea.)*
10. ¿Cuál de estas cosas te haría abrirla aunque tus amigos sigan en WhatsApp?
11. ¿Cuál te parece una boludez?
12. **¿Convencerías a tu grupo de mudarse una semana para probarla?** ← *la respuesta que vale*

### Qué anotar

Planilla, una fila por persona:

| Campo | |
|---|---|
| Edad | |
| Círculo (facultad / colegio / club / escena) | |
| App donde están sus 5 últimas conversaciones | |
| Grupos silenciados | |
| ¿Familia en grupos de amigos? | Sí / No |
| ¿Da número o Instagram a un desconocido? | |
| Diferencial que más le movió el amperímetro | 1 a 5 |
| Diferencial que le pareció una boludez | 1 a 5 |
| ¿Se ofreció a migrar su grupo? | Sí / No |
| La frase textual más fuerte que dijo | |

> Las frases textuales después sirven para la landing y para el material. Anotarlas literal, no parafraseadas. El titular de la landing tiene que salir de acá, no de nuestra imaginación.

---

## Semana 2 · La prueba que vale: migrar un grupo de verdad

Esta es la parte que casi nadie hace y la que decide el proyecto.

### El experimento

Se elige **un grupo real de 6 a 10 personas** que ya hablen todos los días — una comisión de facultad, un equipo, una banda de amigos. Idealmente sale de las entrevistas de la semana 1: alguien que se ofreció en la pregunta 12.

Se les pide **una semana**. Todo lo que se hablarían por WhatsApp, se habla en el prototipo. WhatsApp queda para la familia y el resto del mundo, que es exactamente la propuesta de Ronda.

> **No hace falta la app.** Alcanza un grupo de Telegram configurado a mano para imitar las reglas de Ronda (temas separados, sin "en línea", sin "últ. vez", nadie agrega a nadie sin aceptar), o el prototipo web abierto en el teléfono si ya alcanza para sostener la conversación. Lo que se está probando no es el software: **es si la gente aguanta hablar en otro lado.**

### Qué se mide, día por día

Una planilla con una fila por día:

| Día | Mensajes en el grupo nuevo | ¿Volvieron a WhatsApp para algo? ¿Para qué? | ¿Alguien abandonó? | Qué se quejaron |
|---|---|---|---|---|

Y al final de la semana, a cada uno:

1. ¿Qué extrañaste de WhatsApp?
2. ¿Qué te gustó más de esto?
3. ¿Seguirías una semana más?
4. **¿Le dirías a otro grupo tuyo que lo pruebe?**

### Qué significa cada resultado

| Resultado | Qué significa |
|---|---|
| Llegan al día 7 y piden seguir | 🟢 El producto tiene una razón de existir. A la Fase 1. |
| Llegan al día 7 pero no seguirían | 🟡 Aguantaron por compromiso con vos, no por el producto. Hay que encontrar qué falta y repetir con otro grupo. |
| Vuelven a WhatsApp antes del día 5 | 🔴 Parar. Entender exactamente qué los trajo de vuelta antes de escribir una línea. |

Y lo más importante de todo: **anotar textualmente para qué volvieron a WhatsApp.** Ese motivo es la lista de features de la Fase 1, y es más confiable que cualquier cosa que se nos ocurra a nosotros.

---

## Semana 3 · Los trámites que tardan

Se largan ahora porque tienen demora propia y no se resuelven la semana del lanzamiento:

- [ ] **Marca en INPI** — chequear "Ronda" en las clases de software y telecomunicaciones. Si está tomada, se busca alternativa *antes* de diseñar el logo.
- [ ] **Dominio** — `.com.ar` y `.com` si se consigue
- [ ] **Cuenta de Google Play** — US$ 25. La verificación de identidad tarda, y las cuentas personales nuevas necesitan un período de prueba con testers reales antes de poder publicar.
- [ ] **Cuenta de Apple Developer** — US$ 99/año. Como empresa hace falta número DUNS, que agrega semanas.
- [ ] **Consulta legal inicial** — abogado de datos personales **y de protección de menores**. Con el pivot esto dejó de ser un trámite y pasó a ser una decisión de diseño: ver [`04-menores-y-seguridad.md`](04-menores-y-seguridad.md).

---

## El criterio de salida

Mirando las dos planillas al terminar:

| Resultado | Qué significa | Qué hacemos |
|---|---|---|
| El grupo llegó al día 7 **y** 8 o más de los 20 se ofrecieron a migrar el suyo | El dolor es real y la migración por grupo funciona | 🟢 Fase 1 |
| El grupo llegó al día 7 pero casi nadie se ofreció | Funciona con empujón, no solo | 🟡 Afinar el diferencial que más movió y repetir con otro grupo |
| El grupo se cayó antes del día 5 | El dolor no alcanza para cambiar de app | 🔴 Parar. Replantear el producto o el segmento |

**El resultado rojo no es un fracaso: es el proyecto ahorrándose diez semanas y un presupuesto.** Para eso se hace la Fase 0.

---

## Lo que NO hay que hacer en esta fase

- ❌ Diseñar el logo
- ❌ Elegir la paleta definitiva
- ❌ Escribir código de la app
- ❌ Armar la arquitectura del backend
- ❌ Comprar servidores
- ❌ **Pagar publicidad para "medir interés"** — con una app de mensajería vacía el clic no significa nada. Lo único que mide interés real acá es un grupo que aguanta una semana.

Todo eso es más divertido que hacer veinte llamadas incómodas y perseguir a un grupo de amigos durante siete días. Por eso casi todos lo hacen primero, y por eso casi todos construyen algo que nadie pidió.
