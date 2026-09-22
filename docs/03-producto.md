# Producto — Qué se construye y qué no

> **Para qué sirve este documento:** traducir la estrategia de [`01-vision.md`](01-vision.md) en pantallas y decisiones concretas. Lo que no está acá, no se construye en la Fase 1, por bueno que suene.

---

## La pregunta que filtra todo

Antes de agregar cualquier cosa a este documento:

> **¿Esto hace más probable que un grupo entero se mude junto?**

Si la respuesta es "no, pero está bueno", va a la Fase 2 o al tacho. La Fase 1 tiene ocho a diez semanas y un equipo chico: cada feature que entra saca a otro.

---

## 1. Los objetos del producto

Sólo hay cuatro cosas en Ronda. Si aparece una quinta, algo se fue de escala.

| Objeto | Qué es |
|---|---|
| **Persona** | Un `@`. Nombre visible, foto opcional, un `@` único e inmutable. |
| **Privado** | Conversación entre dos personas. |
| **Ronda** | El grupo. Tiene nombre, miembros, y **temas** adentro. |
| **Tema** | Un canal de conversación dentro de una ronda: `#general`, `#parcial`, `#memes`. Una ronda siempre tiene al menos `#general`. |

**Lo que deliberadamente no existe:** feed, algoritmo, recomendados, "personas que quizás conozcas", buscador global de usuarios, publicidad, historias de marcas. Nada de eso mueve la aguja de la migración y todo eso trae los problemas de la sección 4.

---

## 2. Las pantallas de la Fase 1

Seis. No más.

### 2.1 Entrada — elegir `@`

La primera pantalla del producto y la decisión de identidad más importante.

- Elegís `@usuario` y un nombre visible.
- Contraseña. Mail para recuperar.
- **El teléfono es opcional y se pide después, nunca acá.** Si se pide el número en la pantalla 1, perdimos el diferencial antes de empezar.
- Declaración de edad: **16 o más**. Ver [`04-menores-y-seguridad.md`](04-menores-y-seguridad.md).

Sin SMS, sin contactos, sin "permitinos acceder a tu agenda". Ese pedido de permisos en el minuto uno es lo que hace que la gente abandone el alta, y encima es exactamente lo que estamos diciendo que no hacemos.

### 2.2 Crear tu ronda — el onboarding real

Inmediatamente después del alta, y no se puede saltear:

1. **¿Cómo se llama tu ronda?** — "Comisión 4", "Los pibes", "El equipo"
2. **Elegí temas** — tres sugeridos según el tipo de ronda, editables
3. **Pasá el link** — un botón grande que copia un link de invitación y abre el compartir del sistema

Y entonces la pantalla que define el producto:

> ### Tu ronda se abre cuando entren 5.
> **Faltan 3.**
> *(lista de quién ya entró)*
> `[ Pasar el link otra vez ]`

**Esto es a propósito y es lo más contraintuitivo del producto.** Ver `01-vision.md` §5.1. Resumen: el usuario que llega solo a una app vacía se pierde igual; el umbral lo convierte en reclutador y garantiza que el que entra encuentra conversación.

Mientras la ronda no llega a cinco: se puede escribir (los mensajes quedan esperando) pero no hay notificaciones ni nada más. La app te dice de frente qué falta.

### 2.3 Bandeja

Una sola lista, ordenada por el último mensaje. **Sin algoritmo, sin destacados, sin "no leídos primero".** Llegó último, está arriba.

Cada fila: nombre, último mensaje, hora, contador. Las rondas muestran en qué tema fue el último mensaje.

Arriba, dos filtros y nada más: **Todo** · **Rondas** · **Privados**.

### 2.4 Conversación

Lo que se espera de un chat, bien hecho:

- Texto, foto, video, archivo, audio, ubicación
- Responder citando, reaccionar con emoji, editar (15 min), borrar para todos
- Buscar dentro de la conversación

Y las cuatro cosas nuestras:

| Qué | Cómo se ve |
|---|---|
| **Audio con transcripción** | Cada audio muestra forma de onda, duración, botón de velocidad (1× / 1,5× / 2×) y **el texto debajo, plegado**. Se toca y se expande. Se puede tocar una palabra de la transcripción y el audio salta ahí. |
| **Perilla de efímero** | Arriba de la conversación, visible, no en un submenú: **Se guarda · 24 h · Al leer**. Cambiarla avisa a todos en el chat. |
| **Sin presión** | No hay "en línea", no hay "últ. vez", no hay "escribiendo…" salvo que lo prendas vos. Ver §3. |
| **Aviso de captura** | Si alguien saca captura en un chat efímero, aparece en la conversación. No lo impide: lo dice. |

### 2.5 Ronda por dentro

La pantalla que WhatsApp no tiene.

- Arriba: el nombre de la ronda
- Debajo: **los temas en pestañas horizontales**, con punto de no leído
- Tocás un tema y entrás a esa conversación

Cualquier miembro puede crear un tema. Los temas se pueden silenciar de a uno — que es el punto: podés seguir `#parcial` y silenciar `#memes` sin irte del grupo.

**Invitaciones:** por link. Nadie entra sin aceptar, nadie agrega a nadie. Quien crea la ronda puede elegir si el link lo puede pasar cualquiera o sólo quien la creó.

### 2.6 Vos

Perfil, y las cosas que las tiendas exigen y que no son negociables:

- Tu `@`, nombre, foto
- Privacidad: quién te puede escribir, prender/apagar el tilde de leído, teléfono opcional
- **Bloqueados**
- **Reportar** (también desde cada mensaje y cada perfil)
- **Borrar mi cuenta** — desde adentro de la app, sin mandar un mail, sin hablar con nadie. Apple y Google lo exigen y rechazan por esto.
- Exportar mis datos

---

## 3. La simetría, que es una decisión de diseño y no una preferencia

Todo lo que revela algo de vos revela lo mismo del otro. No hay forma de mirar sin ser visto.

| Señal | Regla |
|---|---|
| **Tilde de leído** | Si lo apagás, dejás de ver el de los demás. Sin excepciones, sin plan pago que lo saltee. |
| **"En línea"** | No existe. Ni prendido ni apagado: no está en el producto. |
| **"Últ. vez"** | No existe. |
| **"Escribiendo…"** | Apagado por default. Si lo prendés, lo ves y te ven. |
| **Captura de pantalla** | En chats efímeros, se avisa. En los normales, no — porque ahí ya se asume que queda. |

**Por qué importa tanto:** el uso ansioso de la mensajería entre adolescentes no viene de los mensajes, viene de las señales de estado. Es lo que permite controlar a una pareja, medir cuánto tardó alguien en contestar, saber que te leyó y no te contestó. Sacarlo no es un detalle de privacidad: **es sacar el mecanismo que vuelve tóxica la app.** Y es algo que WhatsApp no puede hacer, porque mil millones de personas ya dependen de esas señales.

---

## 4. Lo que no se construye, y por qué

Vale la pena escribirlo, porque cada una de estas cosas va a ser pedida por alguien:

| Lo que se va a pedir | Por qué no |
|---|---|
| **Buscador de usuarios por nombre** | Es la puerta de entrada de los desconocidos a los menores. Te encuentran por link o por `@` exacto que vos diste. Nada más. |
| **"Gente cerca tuyo"** | Lo mismo, peor. |
| **Feed / historias públicas** | No mueve la migración de un grupo y nos mete en moderación de contenido público, que es un problema diez veces más grande. |
| **Canales públicos masivos** | Es el modelo Telegram y trae su problema: piratería, estafas, contenido ilegal. No en la Fase 1. |
| **Cifrado punta a punta** | Sí, pero en la Fase 4. Mal hecho es peor que no tenerlo, y rompe multi-dispositivo, backup y la moderación de reportes que las tiendas exigen. Hay que decirlo con todas las letras en la política de privacidad: en la Fase 1 hay TLS y cifrado en reposo, no E2E. |
| **Importar la agenda del teléfono** | Es el gesto más invasivo de la mensajería y contradice toda la propuesta. Se encuentra gente por link, no por agenda. |
| **Bots / API abierta** | Fase 4. |

---

## 5. Cómo se ve

Sin logo todavía (eso es Fase 1, no Fase 0), pero las decisiones estéticas ya importan porque el público juzga en tres segundos:

- **Oscuro por default.** Es donde vive este usuario.
- **Denso, no aireado.** Las apps de mensajería que gustan muestran mucha conversación por pantalla. El aire es para las landings.
- **Movimiento corto.** Transiciones de 150 a 200 ms. Más lento se siente pesado; sin nada se siente barato.
- **Una identidad, no una paleta de marca corporativa.** El prototipo en [`../prototipo/`](../prototipo/) es la primera aproximación y está para romperse.
- **Rioplatense, sin sobreactuar.** "Pasá el link", no "Comparte tu enlace". Y sin meter jerga forzada: nada envejece peor que un adulto escribiendo como cree que hablan los pibes.

---

## 6. Rendimiento, que acá es una feature

La mitad del mercado tiene un teléfono de gama baja y datos móviles malos. Esto no es una consideración técnica, es competitiva:

- La app tiene que abrir y mostrar la bandeja **sin red**, desde lo que ya bajó
- Los mensajes se ven enviados al instante y se sincronizan después
- Las fotos se comprimen en el teléfono antes de subir
- Los audios en un códec liviano; la transcripción la hace el servidor, no el teléfono
- **Tamaño de la app:** objetivo por debajo de 40 MB. Arriba de eso, mucha gente directamente no la baja.

---

## 7. Orden de construcción de la Fase 1

En este orden, porque cada paso hace demostrable al anterior:

1. Alta con `@` y sesión
2. Privados en tiempo real, sólo texto
3. Rondas con temas
4. Invitación por link y umbral de cinco
5. Fotos y archivos
6. Audios
7. **Transcripción**
8. Push
9. **Bloquear, reportar, borrar cuenta** ← sin esto no hay publicación en tiendas
10. Beta cerrada en App Store y Play Store

> El paso 9 no va al final por poco importante: va al final porque es el único que no se puede demostrar antes de tener todo lo demás. **Pero no se manda a revisión sin él**, y por eso está antes del 10 y no después.
