# Menores y seguridad

> **Por qué existe este documento:** apuntar a jóvenes convierte a la protección de menores en el riesgo número uno del proyecto — por encima del efecto red y por encima de la plata. Un incidente grave no se arregla con una actualización: cierra el producto.
>
> **Regla de la casa:** nada de lo que está acá se pospone "para cuando tengamos usuarios". Se construye en la Fase 1, junto con el chat.

---

## 1. La decisión de edad

> ## Edad mínima: 16 años.

No 13. Las razones, en orden:

| Razón | Detalle |
|---|---|
| **Consentimiento parental** | Bajo el estándar europeo (GDPR art. 8), tratar datos de alguien entre 13 y 16 requiere consentimiento verificable de quien ejerce la responsabilidad parental. Verificar eso de verdad —no un checkbox— es un producto entero. No lo podemos construir en la Fase 1, y hacerlo mal es peor que no hacerlo. |
| **Riesgo** | El grueso de los casos de grooming está por debajo de los 16. Bajar la edad multiplica el riesgo y multiplica la exigencia de moderación. |
| **No perdemos mercado** | Los verticales de arranque —facultades, clubes, escenas— son mayoritariamente mayores de 16. No estamos resignando el público: lo estamos ordenando por riesgo. |
| **Las tiendas** | Una app con clasificación 12+ y chat abierto recibe un escrutinio mucho más duro que una 17+. La clasificación se declara alta desde el principio. |

**El secundario entra después.** Cuando haya: moderación probada con volumen real, un producto de consentimiento parental verificable, y un canal formal con las autoridades. No antes, por más que sea el mercado más goloso.

### Cómo se aplica

Sin fantasías: **nadie verifica la edad de verdad con una fecha declarada**, y un sistema que promete lo que no cumple es peor que uno honesto. Lo que sí se hace:

1. **Fecha de nacimiento en el alta**, no un "sí, tengo 16". La fricción de mentir con una fecha concreta filtra a una parte.
2. **La fecha no se puede editar** después libremente. Cambiarla requiere pasar por soporte.
3. **Si el alta declara menos de 16, se bloquea el dispositivo** por un tiempo — no se permite reintentar en la pantalla siguiente con otra fecha.
4. **Señales posteriores.** Si un reporte o la moderación indica que la cuenta es de alguien menor de 16, se suspende y se pide verificación. Esto es lo que realmente funciona, y es trabajo humano.

---

## 2. El diseño es la primera línea de defensa

La mayoría del riesgo se elimina en la arquitectura del producto, no en la moderación. **Un adulto desconocido no puede llegar a un usuario de Ronda**, porque el producto no tiene ningún camino para eso:

| Decisión de producto | Qué riesgo elimina |
|---|---|
| **No hay buscador de usuarios** | Nadie te encuentra por nombre, edad o interés. Es la puerta de entrada clásica. |
| **No hay "gente cerca"** | Lo mismo, con geolocalización encima. |
| **No hay descubrimiento ni recomendados** | El producto nunca le sugiere una persona a otra. |
| **Nadie te agrega a nada** | Las rondas se entran por invitación aceptada. |
| **No se importa la agenda** | No hay grafo latente que explotar. |
| **Sin canales ni contenido público** | No hay superficie donde un desconocido "aparezca" delante de alguien. |

Se llega a alguien de una sola manera: **que esa persona te haya dado su `@` o el link de su ronda.** Es una restricción fuerte del producto, hace más lento el crecimiento, y se acepta a cambio de lo que elimina.

> Esto es coherente con la estrategia y no una concesión: en `01-vision.md` la unidad de crecimiento es el grupo cerrado, no el descubrimiento entre desconocidos. **La decisión de seguridad y la decisión de crecimiento son la misma decisión.**

---

## 3. Lo que va sí o sí en la Fase 1

Sin esto no se manda a revisión de tienda, y Apple rechaza explícitamente apps sociales que no lo tengan:

- [ ] **Bloquear** a una persona, desde su perfil y desde cualquier mensaje suyo. Bloqueo total e inmediato: no te escribe, no te ve, no coincide con vos en ninguna ronda nueva.
- [ ] **Reportar** un mensaje, una persona o una ronda entera, con motivo y con la posibilidad de adjuntar contexto.
- [ ] **Salir de una ronda** en un toque, sin avisar a nadie.
- [ ] **Borrar la cuenta desde adentro de la app**, sin pedirle permiso a nadie, con borrado efectivo de datos y plazo escrito.
- [ ] **Términos y política de privacidad publicados**, en castellano, legibles.
- [ ] **Canal de contacto** que responda de verdad.
- [ ] **Un humano que lea los reportes en menos de 24 horas.** Al principio somos nosotros. Es trabajo, no infraestructura.

---

## 4. Cómo se moderan conversaciones privadas

Acá hay una tensión real y conviene resolverla explícitamente en vez de descubrirla tarde.

**No leemos conversaciones.** No hay escaneo de mensajes, no hay análisis de contenido privado, no hay modelo mirando lo que se escribe. Eso es lo que promete el producto y es lo que hace que alguien lo elija.

**Entonces la moderación es reactiva y por reporte.** Y para que eso funcione:

- Cuando alguien reporta, **el reporte incluye los mensajes que esa persona elige adjuntar**, con su consentimiento explícito, en ese momento. No se abre la conversación entera.
- Lo reportado se conserva por un plazo definido y acotado, para poder actuar y para poder responder a un requerimiento judicial.
- El resto no se toca.

**Señales que sí se miran, sin leer contenido:** cuenta nueva que manda muchas invitaciones, cuenta con muchos bloqueos en poco tiempo, cuenta reportada por varias personas distintas. Son metadatos de comportamiento, no mensajes. Detectan al abusivo sin abrir la correspondencia de nadie.

**Y el límite honesto:** una app sin escaneo de contenido no puede prometer que detecta todo. La promesa que sí se puede sostener es: **reportar es fácil, el reporte lo lee una persona, y hay respuesta en menos de 24 horas.** Eso se cumple o no se dice.

---

## 5. Cuando pasa algo grave

Hay que tenerlo escrito antes de que pase, porque el día que pasa no se improvisa.

| Situación | Qué se hace |
|---|---|
| **Reporte de contacto sexual con un menor (grooming)** | Suspensión inmediata de la cuenta reportada, conservación de la evidencia, y denuncia. En Argentina la vía es la **Línea 137** y la **UFEM / fiscalías especializadas en delitos informáticos**; la Ley 26.904 tipifica el grooming. No se espera a "investigar internamente". |
| **Material de abuso sexual infantil** | Suspensión, preservación y denuncia inmediata. No se descarga, no se reenvía, no se analiza por nuestra cuenta. |
| **Amenazas o riesgo de vida** | Suspensión y contacto con la autoridad. En riesgo de suicidio, la app muestra recursos de ayuda (**Línea 135** en CABA y GBA, **0800-345-1435** en el resto del país). |
| **Acoso entre pares / ciberbullying** | Bloqueo asistido, salida de la ronda sin exponer a la persona, y advertencia o suspensión al reportado según gravedad. |
| **Requerimiento judicial** | Se cumple, con asesoramiento legal, y se le avisa al usuario salvo que la orden lo prohíba. |

**Una persona responsable con nombre y apellido** tiene que estar a cargo de esto desde el primer usuario. No es un rol de tiempo completo al principio; sí es un rol asignado.

---

## 6. Marco legal argentino aplicable

| Norma | Qué exige en la práctica |
|---|---|
| **Ley 26.904 — Grooming** | Tipifica el contacto con un menor con fines sexuales. Define nuestras obligaciones de preservación de prueba y de denuncia. |
| **Ley 26.061 — Protección Integral de NNyA** | Marco general de protección. El interés superior del niño se lee como criterio de diseño, no sólo de cumplimiento. |
| **Ley 25.326 — Datos Personales** | Inscripción de la base ante la AAIP, consentimiento informado, derechos de acceso, rectificación y supresión. Para menores, consentimiento del responsable. |
| **Ley 27.590 — Programa Nacional de Prevención y Concientización del Grooming** | Marco de prevención. Relevante para el material de ayuda dentro de la app. |
| **Estándar europeo (GDPR)** | No nos obliga, pero se diseña contra él: es más exigente y una reforma local nos encontraría cumpliendo. |

**Antes del lanzamiento público hace falta un abogado especializado en datos personales y protección de menores.** No es opcional, y el costo es despreciable al lado de una multa o de un caso mal manejado.

---

## 7. Lo que las tiendas van a mirar

| Requisito | Apple | Google |
|---|---|---|
| Herramientas de moderación de contenido generado por usuarios | **Obligatorio.** Bloquear, reportar, y responder reportes en 24 h. Es causa frecuente de rechazo. | Obligatorio |
| Borrar la cuenta desde la app | Obligatorio | Obligatorio |
| Política de privacidad publicada (URL) | Obligatoria | Obligatoria |
| Etiquetas de privacidad / Data safety | Obligatorias y tienen que ser verdad | Obligatorias |
| Clasificación por edad | Se declara alta desde el principio | Cuestionario de contenido |
| Declarar si el cifrado es punta a punta | No prometer lo que no hay | Igual |

⚠️ **Dos cosas que hunden apps de mensajería en revisión, y valen el doble para una app de jóvenes:**

1. **Apple rechaza apps sociales sin herramientas de moderación.** No es una funcionalidad opcional a futuro: es requisito de entrada.
2. **Google Play exige un período de prueba con testers reales** antes de publicar con una cuenta de desarrollador personal nueva. Se arranca el trámite en la Fase 0, no la semana del lanzamiento.

---

## 8. Lo que no vamos a hacer, y se dice en voz alta

- ❌ **No escaneamos mensajes privados.** Ni con modelos, ni para publicidad, ni "para mejorar el servicio".
- ❌ **No vendemos ni compartimos datos** con terceros para marketing.
- ❌ **No hay publicidad**, y por lo tanto no hay perfilado.
- ❌ **No prometemos cifrado punta a punta hasta que lo tengamos.** En la Fase 1 hay TLS en tránsito y cifrado en reposo, y así figura en la política de privacidad. Mentir sobre esto es la forma más rápida de perder al único público que nos importa.
- ❌ **No usamos patrones oscuros** para retener: sin rachas, sin castigo por no abrir la app, sin notificaciones inventadas. La app avisa cuando alguien te escribió y nada más.

---

*Este documento se revisa con abogado antes del lanzamiento y después de cada incidente.*
