# Menores y seguridad

> **Este documento se lee antes de escribir la primera línea de código.**
> No es un anexo legal. Es la lista de lo que hace que la app exista o no exista.

---

## Por qué está primero

Apuntamos a 14-20 años. **Una parte grande de los usuarios van a ser menores de edad.** Eso pone al proyecto en la categoría más regulada y más vigilada que hay: apps sociales con menores.

Dos cosas pueden terminar el proyecto de un día para el otro:

1. **Que Apple o Google la bajen.** No avisan y no hay apelación rápida. Sin las herramientas de esta lista, no se aprueba ni la primera versión.
2. **Que le pase algo a un chico usando la app.** Es lo que importa de verdad, y además es lo que genera la nota en el diario que termina con todo.

Lo que sigue no es el precio de hacer el proyecto. Es el proyecto.

---

## 1. Las cinco decisiones de arquitectura

Estas cinco cosas no se parchean después. Van en los cimientos.

### 1.1 Grafo cerrado: no existe la búsqueda de personas

**No hay buscador de usuarios. No hay perfiles públicos. No hay "gente que quizás conozcas". No hay recomendaciones.**

A un usuario solo se llega de dos formas:
- Tiene tu número en la agenda y vos el suyo
- Alguien que ya está en un grupo te invita

> **Esta es la medida de seguridad más importante de todo el documento.**
> El grooming necesita que un desconocido pueda iniciar contacto con un menor. Si eso es técnicamente imposible, el vector principal desaparece. Todas las demás medidas son secundarias frente a esta.

Y es gratis: los pibes **quieren** un lugar sin intrusos. La seguridad y el producto apuntan al mismo lado.

### 1.2 Sin ubicación, nunca por defecto

No se comparte ubicación en la versión 1. Ni aproximada, ni "en qué zona estás", ni mapas de amigos. Es uno de los vectores más usados para llegar físicamente a un menor.

Si algún día se agrega, es: opt-in explícito, solo con contactos mutuos, temporal y con vencimiento automático.

### 1.3 Sin cifrado de punta a punta en la versión 1 — a propósito

**No se puede moderar lo que no se puede ver.** Una app para menores sin capacidad de revisar material reportado no puede cumplir con las tiendas ni con la ley.

El orden correcto es: primero seguridad, después privacidad criptográfica. Y se comunica así, abiertamente, en la política de privacidad — no se esconde.

Los mensajes van cifrados en tránsito (TLS) y cifrados en reposo en la base. El E2EE llega en la Fase 5, con moderación del lado del cliente ya resuelta.

### 1.4 Verificación de edad al registrarse

Fecha de nacimiento obligatoria, con estas consecuencias:

| Edad declarada | Qué pasa |
|---|---|
| **Menos de 13** | No se permite el registro. Punto. |
| **13 a 17** | Cuenta de menor: restricciones reforzadas, sin excepciones configurables |
| **18 o más** | Cuenta adulta |

⚠️ **Un campo de fecha es fácil de mentir, y lo sabemos.** No alcanza por sí solo, pero es el piso legal obligatorio. La defensa real es el grafo cerrado (§1.1): un adulto que mienta la edad igual no puede buscar ni contactar a nadie que no lo haya invitado.

Y una regla importante: **los adultos y los menores no se mezclan por descubrimiento.** Un adulto no puede ser invitado a un grupo donde todos son menores salvo que ya tenga contacto mutuo con quien lo invita.

### 1.5 Borrar la cuenta desde adentro de la app

Requisito obligatorio de Apple y de Google, y derecho del titular por Ley 25.326. Máximo dos toques desde el perfil. Borra los datos de verdad, con plazo declarado, no los "desactiva".

---

## 2. Moderación: lo que Apple exige para aprobar

Apple no aprueba apps con contenido generado por usuarios sin estas cuatro cosas. Google pide lo equivalente.

| Requisito | Qué hay que construir |
|---|---|
| **Bloquear** | Desde el chat y desde el perfil, en ≤ 2 toques. Efecto inmediato y total. |
| **Reportar** | Cada mensaje, cada audio, cada grupo, cada usuario. Con motivo. |
| **Responder reportes en ≤ 24 h** | Una persona real mirando una cola de reportes. **Todos los días.** |
| **Filtrar contenido ofensivo** | Filtro automático + revisión humana de lo reportado |

**Esto implica una obligación operativa continua, no una función.** Alguien tiene que estar del otro lado todos los días, incluidos sábados y feriados. Si el equipo no puede sostener eso, la app no puede existir — y es mejor saberlo hoy.

### La cola de reportes: cómo se atiende

| Tipo de reporte | Plazo | Acción |
|---|---|---|
| Material de abuso sexual infantil | **Inmediato** | Bloqueo de cuenta + preservación de evidencia + denuncia |
| Adulto contactando a un menor | **< 2 h** | Suspensión preventiva + revisión |
| Acoso entre pares / bullying | < 24 h | Revisión + advertencia o suspensión |
| Spam, contenido molesto | < 48 h | Revisión |

---

## 3. Material de abuso sexual infantil (CSAM)

Es el riesgo más grave de operar una plataforma donde circulan imágenes y audios entre menores.

**Qué hay que tener antes de abrir al público:**

- **Escaneo automático de toda imagen y video** contra bases de hashes conocidos. Hay herramientas gratuitas para plataformas que califican — **PhotoDNA** (Microsoft) y **Safer** (Thorn). Se solicita acceso con meses de anticipación, no la semana del lanzamiento.
- **Protocolo de denuncia escrito**: a quién se le avisa, en qué plazo, quién preserva la evidencia y cómo. Definido antes de que pase, no cuando pasa.
- **Prohibición explícita en los términos**, con baneo permanente.

⚠️ Este punto requiere abogado penalista, no solo abogado de datos. Las obligaciones de denuncia y de preservación de evidencia son específicas y el error se paga caro.

---

## 4. Marco legal argentino

| Norma | Qué implica para nosotros |
|---|---|
| **Ley 26.061** — Protección Integral de Derechos de NNyA | El interés superior del niño prevalece sobre cualquier consideración de producto o de negocio. En la práctica: ante la duda, la opción más restrictiva. |
| **Ley 26.904** — Grooming (art. 131 Código Penal) | Contactar a un menor por medios electrónicos con fines sexuales es delito. Somos el medio: tenemos que poder detectarlo, cortarlo y aportar prueba. |
| **Ley 27.590** — "Mica Ortega", Programa Nacional de Prevención del Grooming | Marco de prevención y concientización. Conviene alinearse activamente, no solo cumplir. |
| **Ley 25.326** — Datos Personales | Inscripción de la base ante la AAIP. Consentimiento informado. Con menores, el consentimiento tiene requisitos reforzados. |
| **Ley 26.388** — Delitos Informáticos | Marco general. |

⚠️ La Ley 25.326 es del año 2000 y no contempla apps móviles ni menores nativos digitales. **Conviene diseñar contra el estándar europeo** (GDPR + el Age Appropriate Design Code británico, que es el más exigente del mundo en apps para menores). Cumplir el más duro nos deja cumpliendo todos.

---

## 5. Requisitos de las tiendas

### Apple App Store

| Punto | Qué pide |
|---|---|
| Guideline 1.2 — Contenido de usuarios | Las cuatro herramientas del §2. **Sin esto, rechazo directo.** |
| Clasificación por edad | Declarar honestamente. Una app de mensajería con contenido de usuarios es 17+ salvo que se demuestre moderación robusta. |
| Etiquetas de privacidad | Declarar cada dato que se recoge y para qué |
| Borrado de cuenta | Obligatorio dentro de la app |
| Política de privacidad | URL pública y accesible |

### Google Play

| Punto | Qué pide |
|---|---|
| Target audience & content | Declarar el público. Si incluye menores de 13 entra en la política de Familias, que es mucho más estricta. **Nuestro piso es 13, así que declaramos "Adolescentes".** |
| Data safety | Formulario detallado de datos |
| Borrado de cuenta | Obligatorio, y también por web |
| Período de prueba | **Las cuentas de desarrollador personales nuevas necesitan testers reales durante un tiempo antes de poder publicar.** Se larga con meses de anticipación. |

---

## 6. La página para padres

No es un gesto de relaciones públicas. Es estrategia.

Una app de adolescentes que los padres perciben como oscura se convierte en el enemigo, sale en las noticias y termina prohibida en los colegios. Una que explica qué hace y qué no hace se convierte en la que los padres **permiten**.

Tiene que decir, en castellano claro y sin letra chica:
- Qué es Eco y para qué sirve
- **Que no existe forma de que un desconocido contacte a su hijo**, y por qué
- Qué datos se guardan y por cuánto tiempo
- Cómo reportar algo y en cuánto tiempo respondemos
- Cómo pedir que se borre una cuenta
- Un mail de contacto que **una persona lee**

---

## 7. El diseño adictivo: la trampa siguiente

Un punto incómodo pero necesario.

Las mecánicas que más enganchan adolescentes —rachas tipo Snapchat, contadores de días, notificaciones que presionan— son exactamente las que están siendo reguladas en todo el mundo y las que generan el juicio y la nota periodística de los próximos años.

**Se puede crecer sin eso.** Nuestro bucle de crecimiento (§4 del documento fundacional) no depende de la presión psicológica: depende de que el producto genere algo que la gente **quiera** compartir. Es más difícil de diseñar y mucho más sólido.

Límites que fijamos ahora, por escrito, para no discutirlos después bajo presión de métricas:
- ❌ Sin rachas que se "pierden"
- ❌ Sin notificaciones que culpabilizan ("hace 3 días que no le escribís a…")
- ❌ Sin scroll infinito
- ✅ Silencio nocturno por defecto en cuentas de menores

---

## 8. Lista de verificación antes de publicar

Nada de esto es opcional. Si falta uno, no se publica.

**Arquitectura**
- [ ] Sin búsqueda de usuarios ni perfiles públicos
- [ ] Solo por invitación o contacto mutuo
- [ ] Sin compartir ubicación
- [ ] Verificación de edad, con bloqueo bajo 13
- [ ] Separación de cuentas de menores y adultas

**Moderación**
- [ ] Bloquear en ≤ 2 toques
- [ ] Reportar en todas las superficies
- [ ] Panel de moderación funcionando
- [ ] **Alguien asignado a la cola de reportes, todos los días**
- [ ] Protocolo escrito de escalamiento

**CSAM**
- [ ] Escaneo por hash activo
- [ ] Protocolo de denuncia escrito
- [ ] Abogado penalista consultado

**Legal**
- [ ] Base inscripta ante la AAIP
- [ ] Términos y Condiciones
- [ ] Política de Privacidad publicada
- [ ] Página para padres
- [ ] Borrado de cuenta funcionando

**Tiendas**
- [ ] Clasificación de edad declarada honestamente
- [ ] Etiquetas de privacidad de Apple
- [ ] Data safety de Google
- [ ] Cuenta de Google con el período de prueba ya cumplido

---

## 9. La pregunta de fondo

Antes de seguir, hay que contestarla en serio:

> **¿Estamos dispuestos a operar una plataforma donde circulan chicos de 14 años?**

Eso significa una persona atendiendo reportes todos los días, plata en asesoramiento legal, y la responsabilidad real de que un pibe pueda pasarla mal en algo que nosotros construimos.

Si la respuesta es sí, este documento es el plan y se sigue al pie de la letra.

Si la respuesta es no, hay dos salidas honestas: subir el público a 18+ y perder lo mejor del efecto red, o volver a la estrategia del borrador 1, que está en el historial de git y sigue siendo buena.

**Lo único que no es una opción es seguir sin haberla contestado.**
