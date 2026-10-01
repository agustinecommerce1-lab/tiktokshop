# design.md — Sistema de marca para carruseles TikTok Shop

> Archivo fuente para Claude Design. Todo carrusel que se genere debe seguir este documento.
> Si una instrucción puntual contradice este archivo, gana la instrucción puntual, salvo en la
> sección 5 (claims y cumplimiento), que no se negocia.

---

## 0. Variables a completar

| Variable | Valor | Uso |
|---|---|---|
| `{{HANDLE}}` | @________ | Firma en cada slide |
| `{{NOMBRE_SERIE}}` | Sin humo | Nombre de la serie de suplementos |
| `{{MERCADO}}` | TikTok Shop España | Define idioma, moneda (€) y normativa (UE) |
| `{{PRODUCTO}}` | Ashwagandha / Magnesio / Omega-3 (HSN) | Activa el tema de color del producto |
| `{{PRECIO}}` | __,__ € | Solo si está confirmado en la ficha de TikTok Shop el día de publicar |
| `{{DOSIS}}` | Según etiqueta HSN | Nunca inventar dosis |

---

## 1. Arquitectura del sistema

El sistema tiene dos capas para que sirva más allá de este primer producto:

| Capa | Qué contiene | ¿Cambia por marca/producto? |
|---|---|---|
| **Núcleo creador** | Voz, tipografía, grilla, safe zones, componentes, estructuras de carrusel, firma `{{HANDLE}}` | No. Es lo que hace reconocible la cuenta |
| **Tema de vertical** | Paleta, iconografía, fotografía, reglas de claims | Sí. Hoy: **Suplementos**. Mañana: Hogar, Ropa, etc. |
| **Acento de producto** | Un color secundario por producto dentro del tema | Sí. Ashwagandha, Magnesio, Omega-3 |

Regla: un carrusel de hogar o ropa debe verse "de la misma cuenta" que uno de suplementos. Lo que cambia es el color y la foto, no la estructura ni la voz.

---

## 2. Esencia de marca (serie "Sin humo")

| Elemento | Definición |
|---|---|
| **Qué es** | Suplementos explicados por alguien que los toma, lee la etiqueta y no te vende humo |
| **Para quién** | Personas de 22–40 que entrenan o quieren cuidarse, ven suplementos en todos lados y no saben cuál sirve para qué ni cuándo tomarlo |
| **Trabajo del contenido** | Que en 7 slides alguien entienda qué es un producto, cómo se toma y si encaja con su rutina. La venta es la consecuencia, no el inicio |
| **Promesa** | Claro, honesto y útil. Si algo no está demostrado, se dice |
| **Personalidad** | El amigo que entrena, leyó la letra chica y te lo cuenta en 30 segundos |
| **Lo que no somos** | Gurú fitness, médico, vendedor de milagros, cuenta de memes |

**Tagline principal:** Suplementos, explicados sin humo.

**Taglines alternativos (rotar en CTA):**
- Lo que tomo, cuándo y por qué.
- Primero la etiqueta, después el carrito.
- Menos promesas, más letra chica.

---

## 3. Voz y tono

### 3.1 Principios

| Principio | Cómo se ve | Ejemplo |
|---|---|---|
| **Simple** | Una idea por slide. Frases de menos de 15 palabras. Cero tecnicismos sin traducir | "Bisglicinato = magnesio unido a un aminoácido. Ya está." |
| **Cercano** | Primera persona, "tú", tono de conversación | "Yo lo tomo con la cena. Te cuento por qué." |
| **Honesto** | Se dice lo que no se sabe y para quién no es | "La ashwagandha no tiene beneficios aprobados en la UE. Por eso aquí no te prometo ninguno." |
| **Concreto** | Números, momentos del día, cantidades reales de la etiqueta | "Mira los mg de EPA + DHA, no los 1000 mg de aceite." |
| **Sin presión** | El CTA invita, no apura | "Si encaja contigo, está en el carrito." |

### 3.2 Idioma

- Español neutro con **tú**. Nunca "vos", nunca "vosotros".
- Vocabulario que funcione en España sin sonar forzado: móvil, euros, comprar, tomar.
- Evitar chilenismos (po, cachai, bacán, al tiro), argentinismos y "coger".
- Sentence case en todo: solo mayúscula inicial. Nada de TÍTULOS EN MAYÚSCULAS.
- Números en cifra (3, no "tres"). Unidades con espacio: 250 mg, 2 cápsulas.

### 3.3 Palabras

| Usar | Evitar |
|---|---|
| contribuye a (solo con claim autorizado) | cura, trata, previene, elimina |
| según la etiqueta | milagro, brutal, increíble, top |
| yo lo tomo / mi rutina | "tienes que", "debes" |
| para quién no es | 100 % natural sin efectos secundarios |
| letra chica, etiqueta, dosis | ansiedad, insomnio, depresión, testosterona |
| hábito, rutina, momento del día | quema grasa, detox, desinflama |
| consulta con un profesional | "recomendado por médicos" (salvo que sea real y demostrable) |

### 3.4 Reescrituras de referencia

| Antes (no) | Después (sí) |
|---|---|
| "¡¡El magnesio que te va a cambiar la vida!! 🔥🔥" | "El magnesio contribuye a disminuir el cansancio y la fatiga. Lo que importa es cuánto trae de verdad." |
| "Ashwagandha para el estrés y dormir increíble" | "Ashwagandha: qué es, cómo se toma y quién debería saltársela." |
| "El mejor omega-3 del mercado" | "Cómo comparar omega-3 en 10 segundos: mira EPA + DHA por dosis." |
| "Corre que se acaba la oferta" | "Si te encaja, lo dejo en el carrito." |

---

## 4. Sistema visual

### 4.1 Paleta del tema Suplementos

Dirección: verde de bosque profundo en vez del verde menta genérico de farmacia, con un amarillo polen como único acento cálido. El fondo es un verde hoja muy pálido, no crema.

| Token | Nombre | Hex | Rol |
|---|---|---|---|
| `--bosque` | Bosque | `#1E3A2C` | Texto principal, fondos oscuros, slides de impacto |
| `--musgo` | Musgo | `#4F7A52` | Texto secundario, iconos, bordes de tabla |
| `--hoja` | Hoja | `#EEF2E6` | Fondo por defecto de slides |
| `--blanco` | Blanco | `#FFFFFF` | Bloques de contenido sobre Hoja |
| `--polen` | Polen | `#F2D366` | Acento único: cápsula de dato clave, CTA, veredicto |
| `--linea` | Línea | `#CBD5C0` | Separadores y bordes finos |
| `--alerta` | Alerta | `#B8462E` | Solo para "mito", "para quién no es" y advertencias |

**Contrastes verificados (WCAG):**

| Combinación | Ratio aprox. | Uso permitido |
|---|---|---|
| Bosque sobre Hoja | 11:1 | Todo |
| Bosque sobre Polen | 8:1 | Todo |
| Polen sobre Bosque | 8:1 | Titulares y cifras |
| Musgo sobre Hoja | 4,6:1 | Texto ≥ 40 px |
| Blanco sobre Alerta | 5,5:1 | Etiquetas de advertencia |

**Proporción por slide:** 70 % Hoja/Blanco · 25 % Bosque · 5 % Polen. El Polen nunca ocupa más de un elemento por slide.

### 4.2 Acentos de producto

Cada producto suma un color propio que aparece solo en: la franja superior de la portada, el icono del producto y el borde de la cápsula de producto. El resto del sistema no cambia.

| Producto | Token | Hex | Lógica |
|---|---|---|---|
| Ashwagandha | `--raiz` | `#9C6B43` | Raíz, tierra, origen botánico |
| Magnesio | `--noche` | `#3E4A7A` | Mineral, momento de la noche en la rutina |
| Omega-3 | `--marea` | `#2C7385` | Mar, pescado azul |

### 4.3 Tipografía (Google Fonts)

| Rol | Fuente | Peso | Por qué |
|---|---|---|---|
| Titulares y cifras | **Bricolage Grotesque** | 700–800, width 90 % | Carácter propio y cercano, se lee bien grande en móvil |
| Texto, tablas, disclaimers | **Atkinson Hyperlegible Next** | 400 / 700 | Diseñada para máxima legibilidad. En contenido de salud, que se lea bien es parte del mensaje |

Fallback: `system-ui, -apple-system, "Segoe UI", sans-serif`.

**Escala para lienzo 1080 × 1920:**

| Estilo | Fuente | Tamaño | Interlineado | Tracking |
|---|---|---|---|---|
| Hook (portada) | Bricolage 800 | 128 px | 1.0 | -2 % |
| Título de slide | Bricolage 800 | 88 px | 1.05 | -1 % |
| Cifra destacada | Bricolage 800 | 200 px | 0.9 | -3 % |
| Subtítulo | Bricolage 700 | 56 px | 1.15 | 0 |
| Texto | Atkinson 400 | 46 px | 1.35 | 0 |
| Texto en tabla | Atkinson 400/700 | 40 px | 1.3 | 0 |
| Disclaimer / fuente | Atkinson 400 | 32 px | 1.3 | 0 |
| Firma `{{HANDLE}}` | Atkinson 700 | 32 px | 1 | 0 |

**Reglas tipográficas:**
- Nada de texto por debajo de 32 px.
- Máximo 2 pesos por slide.
- No destacar una sola palabra en otro color dentro del titular. Si algo es clave, va en su propia cápsula Polen.
- Sin etiquetas en mayúsculas sobre los títulos.
- Alineación a la izquierda siempre. Centrado solo en la cifra destacada.

### 4.4 Lienzo, grilla y safe zones

- **Formato:** 1080 × 1920 px (9:16), modo foto de TikTok.
- **Largo del carrusel:** 6–9 slides. Nunca más de 10.
- **Márgenes:** 88 px laterales.
- **Grilla:** 6 columnas, gutter 24 px.
- **Ritmo vertical:** múltiplos de 8 px. Espacio entre bloques: 48 px. Entre título y texto: 32 px.

**Safe zones (la interfaz de TikTok tapa estas áreas):**

| Zona | Reservado | Qué puede ir |
|---|---|---|
| Superior | 0–180 px | Solo franja de color de producto en portada |
| Derecha | 160 px | Nada de texto |
| Inferior | últimos 440 px (1480–1920) | Solo fondo o foto. El disclaimer y la firma van justo encima, entre 1420 y 1480 px |

```
┌──────────────────────────┐ 0
│ franja producto (portada)│
├──────────────────────────┤ 180
│ ┌────────────────────┐   │
│ │                    │   │
│ │   ZONA DE CONTENIDO│ ◄─┼─ 160 px libres a la derecha
│ │   88 px margen     │   │
│ │                    │   │
│ │                    │   │
│ └────────────────────┘   │
│ disclaimer / firma       │ 1420–1480
├──────────────────────────┤ 1480
│  zona UI TikTok (caption,│
│  botones, carrito)       │
└──────────────────────────┘ 1920
```

### 4.5 Elemento firma: la cápsula

El único recurso gráfico protagonista del sistema. Es un contenedor con forma de cápsula (radio 999 px) dividido en dos mitades:

- Mitad izquierda **Bosque** con el concepto ("Dosis", "Cuándo", "Veredicto").
- Mitad derecha **Polen** con el dato ("2 cápsulas", "con la cena", "Encaja si…").
- Alto: 120 px. Texto: Atkinson 700, 44 px.
- Máximo **una cápsula por slide**. Es el dato que alguien debería recordar si solo mira esa slide.

```
╭──────────────┬───────────────────╮
│   Cuándo     │   con la cena     │
╰──────────────┴───────────────────╯
   Bosque           Polen
```

Variantes:
- **Cápsula de producto:** borde de 6 px en el acento del producto, fondo Blanco, nombre del producto dentro.
- **Cápsula de alerta:** mitad izquierda en Alerta con "Ojo", mitad derecha en Blanco.

### 4.6 Otros componentes

| Componente | Especificación |
|---|---|
| **Bloque de contenido** | Fondo Blanco sobre Hoja, radio 32 px, padding 56 px, sin sombra |
| **Tabla comparativa** | Encabezado en Bosque con texto Blanco, filas alternas Blanco/Hoja, bordes Línea 2 px, radio exterior 32 px. Máximo 4 columnas × 5 filas |
| **Timeline del día** | Línea vertical Musgo 4 px, nodos circulares de 40 px. Iconos sol / plato / pesa / luna. Es una secuencia real, así que aquí sí van números |
| **Mito / Realidad** | Dos bloques apilados. Mito: borde izquierdo 12 px Alerta. Realidad: borde izquierdo 12 px Bosque |
| **Checklist** | Casillas cuadradas de 48 px, radio 10 px, check en Bosque |
| **Indicador de avance** | Puntos de 14 px abajo a la izquierda (en 1400 px), activo en Bosque, resto en Línea. Solo de slide 2 en adelante |
| **Firma** | `{{HANDLE}}` en Atkinson 700 32 px, color Musgo, alineada a la izquierda en la base de la zona de contenido |

### 4.7 Iconografía

- Estilo línea, trazo 4 px, extremos redondeados, color Bosque o Musgo.
- Tamaño base 72 px; en timeline 40 px.
- Set fijo: sol (mañana), plato (con comida), pesa (entreno), luna (noche), vaso (agua), lupa (etiqueta), escudo (para quién no es), carrito (CTA).
- Prohibido: pastillas 3D flotando, moléculas brillantes, corazones con estetoscopio, emojis como iconos dentro del diseño.

### 4.8 Fotografía

| Sí | No |
|---|---|
| El bote real de HSN en mi mano, en la cocina, en la mochila del gym | Fotos de stock de gente sonriendo con ensalada |
| Luz natural, de día, sombras suaves | Flash, filtros saturados, viñetas |
| Producto recortado sobre Hoja con sombra de contacto corta | Degradados de fondo, brillos, reflejos falsos |
| Primer plano de la etiqueta (para slides de "cómo leerla") | Antes/después corporal |
| Cápsulas reales en la palma, escala honesta | Cápsulas agrandadas o renders |

Regla de foto: máximo 2 slides con foto por carrusel (portada y CTA). El resto es diseño.

---

## 5. Claims y cumplimiento (no negociable)

Contexto: en la UE (Reglamento 1924/2006) un complemento alimenticio solo puede comunicar beneficios de salud que estén en la lista de declaraciones autorizadas, y no puede decir que cura, trata o previene enfermedades. Esto aplica también a creadores que cobran o ganan comisión, aunque sea "mi experiencia". TikTok Shop además rechaza contenido de suplementos con promesas exageradas o antes/después.

> No es asesoría legal. Ante duda, se usa la versión más conservadora o se elimina la frase.

### 5.1 Lo que se puede decir por producto

| Producto | Claims autorizados (usar literal) | Condición |
|---|---|---|
| **Magnesio** | Contribuye a disminuir el cansancio y la fatiga · al funcionamiento normal del sistema nervioso · al funcionamiento normal de los músculos · a la función psicológica normal · al metabolismo energético normal · al mantenimiento de los huesos y dientes en condiciones normales · al equilibrio electrolítico | El producto debe aportar al menos 56,25 mg de magnesio por dosis diaria (15 % VRN). Verificar en la etiqueta HSN |
| **Omega-3** | El EPA y el DHA contribuyen al funcionamiento normal del corazón · El DHA contribuye a mantener el funcionamiento normal del cerebro · El DHA contribuye a mantener la visión en condiciones normales | Corazón: 250 mg de EPA + DHA al día. Cerebro y visión: 250 mg de DHA al día. Verificar en la etiqueta |
| **Ashwagandha** | **Ninguno.** No hay declaraciones de salud autorizadas para ashwagandha en la UE | Solo información descriptiva: qué es, origen ayurvédico, tipos de extracto, cómo leer la etiqueta, cómo se toma según el fabricante, para quién no es |

Siempre añadir en la frase que el efecto lo da el nutriente, no la marca: "El magnesio contribuye a…", no "HSN Magnesio te ayuda a…".

### 5.2 Prohibido en cualquier slide o caption

- Nombrar enfermedades o trastornos: ansiedad, depresión, insomnio, hipertensión, colesterol, artritis, etc.
- Testosterona, libido, fertilidad, rendimiento sexual (frecuentes en ashwagandha: cero).
- Pérdida de peso, quema de grasa, "desinflama", "detox".
- "Sin efectos secundarios", "100 % seguro", "apto para todos".
- Antes/después corporal o de analíticas.
- Sustituir medicación o "en vez de ir al médico".
- Testimonios de terceros con beneficios de salud.
- Comparar contra otra marca por nombre. Las comparaciones son entre **formas, formatos o ingredientes** (bisglicinato vs. citrato vs. óxido; aceite de pescado vs. algas), con datos objetivos de etiqueta.
- Inventar dosis, precios o porcentajes. Todo dato sale de la etiqueta o la ficha del producto.

### 5.3 Bloques obligatorios

**Disclaimer (penúltima o última slide, y en la caption):**
> Complemento alimenticio. No sustituye una dieta variada y equilibrada ni un estilo de vida saludable. No superes la dosis diaria recomendada. Si estás embarazada, en lactancia, tomas medicación o tienes alguna condición médica, consulta con un profesional antes de tomarlo.

**Extra para ashwagandha (obligatorio en todo carrusel que la mencione):**
> No recomendada en embarazo ni lactancia. Si tienes problemas de tiroides, hígado o tomas medicación, consulta antes con tu médico.

**Identificación publicitaria:**
- Activar el ajuste de contenido de marca / publicidad de TikTok en cada publicación.
- `#publi` como primer hashtag de la caption.
- Si el producto fue regalado o hay comisión, decirlo en una línea: "Trabajo con HSN en TikTok Shop y gano comisión si compras desde aquí."

---

## 6. Estructuras de carrusel

Cada tipo tiene un código para pedirlo a Claude Design. Slides numeradas = orden fijo.

### A. Comparación de formas — `COMP`
Ejemplo: formas de magnesio. Omega-3 de pescado vs. de algas.

| # | Slide | Componente | Contenido |
|---|---|---|---|
| 1 | Portada | Hook + foto producto + franja acento | Pregunta o tensión concreta |
| 2 | El problema | Bloque de contenido | Por qué la gente se confunde (una frase) |
| 3–5 | Una forma por slide | Título + 3 líneas + cápsula de dato | Qué es, cuánto aporta según etiqueta, para quién encaja |
| 6 | Resumen | Tabla comparativa | Forma · Aporte por dosis · Formato · Precio por dosis |
| 7 | La que uso yo | Foto mano + cápsula Veredicto | Motivo objetivo (formato, dosis, precio), no un efecto de salud |
| 8 | Cierre | CTA + disclaimer + firma | Invitación al carrito |

### B. Cuándo tomarlo — `CUANDO`

| # | Slide | Componente | Contenido |
|---|---|---|---|
| 1 | Portada | Hook | "¿De mañana o de noche?" |
| 2 | Lo que dice la etiqueta | Foto etiqueta + cápsula Dosis | Dosis y modo de uso del fabricante |
| 3 | Mi día | Timeline del día | Dónde lo meto en mi rutina (hábito, no beneficio) |
| 4 | Con o sin comida | Bloque + icono plato | Lo que indica el fabricante (ej. omega-3 con comida) |
| 5 | Errores comunes | Checklist (3 ítems) | Pasarse de dosis, olvidarlo, tomarlo sin leer la etiqueta |
| 6 | Para quién no es | Cápsula de alerta + bloque | Contraindicaciones de la etiqueta |
| 7 | Cierre | CTA + disclaimer + firma | |

### C. Por qué tomarlo — `PORQUE`
Solo para Magnesio y Omega-3. Para ashwagandha usar `QUEES`.

| # | Slide | Componente | Contenido |
|---|---|---|---|
| 1 | Portada | Hook | |
| 2 | Qué es | Bloque | Definición en 2 líneas |
| 3 | Para qué sirve | Cifra destacada o bloque | Claim autorizado literal (sección 5.1) |
| 4 | El número que importa | Cifra destacada + cápsula | mg de magnesio elemental / mg de EPA + DHA |
| 5 | De dónde lo sacas con comida | Bloque + iconos | Alimentos fuente, sin alarmismo |
| 6 | Cuándo tiene sentido un suplemento | Checklist | Situaciones generales, sin diagnosticar |
| 7 | Cierre | CTA + disclaimer + firma | |

### D. Qué es (solo descriptivo) — `QUEES`
Para ashwagandha o cualquier producto sin claims autorizados.

| # | Slide | Componente | Contenido |
|---|---|---|---|
| 1 | Portada | Hook | "Ashwagandha: lo que deberías saber antes de comprarla" |
| 2 | Qué es | Bloque + icono raíz | Planta de la tradición ayurvédica, se usa la raíz |
| 3 | Tipos de extracto | Tabla | Polvo de raíz vs. extracto estandarizado, % de withanólidos según etiqueta |
| 4 | Cómo leer la etiqueta | Foto etiqueta + 3 flechas | Extracto, mg por cápsula, dosis diaria |
| 5 | Para quién no es | Cápsula de alerta + bloque | Embarazo, lactancia, tiroides, hígado, medicación |
| 6 | Cómo la integro yo | Timeline | Momento y hábito, sin efectos |
| 7 | Cierre | CTA + disclaimer extra + firma | |

### E. Mito / Realidad — `MITO`

| # | Slide | Componente |
|---|---|---|
| 1 | Portada | Hook: "4 cosas que se dicen del omega-3" |
| 2–5 | Un mito por slide | Mito / Realidad apilados |
| 6 | Resumen | Checklist de lo que sí importa |
| 7 | Cierre | CTA + disclaimer + firma |

### F. Mi rutina — `RUTINA`

| # | Slide | Componente |
|---|---|---|
| 1 | Portada | Foto de los botes en la encimera + hook |
| 2 | Mi contexto | Bloque: entreno, horario, por qué uso suplementos (sin beneficios de salud) |
| 3–5 | Un producto por slide | Cápsula de producto + cápsula Cuándo |
| 6 | Timeline del día completo | Timeline |
| 7 | Lo que no tomo y por qué | Bloque |
| 8 | Cierre | CTA + disclaimer + firma |

### G. Cómo leer la etiqueta — `ETIQUETA`

| # | Slide | Componente |
|---|---|---|
| 1 | Portada | Hook: "Así leo la etiqueta de un suplemento en 10 segundos" |
| 2 | La etiqueta completa | Foto etiqueta |
| 3–5 | Un dato por slide | Recorte de etiqueta + cifra destacada |
| 6 | Checklist rápido | Checklist (4 ítems) |
| 7 | Cierre | CTA + disclaimer + firma |

---

## 7. Banco de hooks

Máximo 10 palabras en portada. Todos cumplen la sección 5.

| Producto | Hook | Tipo |
|---|---|---|
| Magnesio | Tu magnesio dice 500 mg. No son 500 mg de magnesio. | `ETIQUETA` |
| Magnesio | Bisglicinato, citrato, óxido. ¿Cuál es cuál? | `COMP` |
| Magnesio | Magnesio: ¿de mañana o de noche? | `CUANDO` |
| Magnesio | Cansancio y magnesio: lo que sí está aprobado | `PORQUE` |
| Omega-3 | En el omega-3, el número grande no es el importante | `ETIQUETA` |
| Omega-3 | 3 errores tomando omega-3 que veo todo el rato | `MITO` |
| Omega-3 | Omega-3 de pescado o de algas: diferencias reales | `COMP` |
| Omega-3 | Si casi no comes pescado azul, mira esto | `PORQUE` |
| Ashwagandha | Ashwagandha: lo que nadie te cuenta antes de comprarla | `QUEES` |
| Ashwagandha | Quién debería saltarse la ashwagandha | `QUEES` |
| Ashwagandha | Polvo de raíz o extracto: qué estás comprando | `QUEES` |
| General | Lo que tomo cuando entreno 5 días a la semana | `RUTINA` |
| General | Gasté dinero en el suplemento equivocado. Para que tú no. | `ETIQUETA` |
| General | 3 suplementos, 3 momentos del día | `RUTINA` |
| General | Antes de añadir esto al carrito, lee la etiqueta | `ETIQUETA` |

---

## 8. Caption y CTA

**Estructura de caption (máx. 300 caracteres antes de hashtags):**
1. Una línea que amplía el hook.
2. Una línea de valor ("Guárdalo para cuando vayas a comprar").
3. CTA suave.
4. Línea de comisión.
5. Disclaimer corto.
6. Hashtags (5–7, `#publi` primero).

**Plantilla:**
```
{{línea que amplía el hook}}
Guárdalo para la próxima vez que compres {{producto}}.
Si te encaja, lo dejo en el carrito 🛒
Trabajo con HSN en TikTok Shop y gano comisión si compras desde aquí.
Complemento alimenticio. No sustituye una dieta equilibrada. Consulta con un profesional si tienes dudas.
#publi #suplementos #{{producto}} #HSN #rutinasaludable #gym
```

**CTA de la última slide (rotar):**

| CTA | Cuándo usarlo |
|---|---|
| Si te encaja, está en el carrito 🛒 | Por defecto |
| Guárdalo y míralo antes de comprar | Carruseles `ETIQUETA` y `COMP` |
| ¿Cuál quieres que compare después? | Para generar comentarios |
| Primero la etiqueta, después el carrito | Cierre de serie |

---

## 9. Instrucciones para Claude Design

**Cómo pedir un carrusel:**
```
Carrusel {{TIPO}} sobre {{PRODUCTO}} de HSN.
Hook: "{{hook}}" (o elige uno de la sección 7).
Datos de etiqueta: {{dosis, mg por cápsula, EPA/DHA, forma, extracto}}.
Foto: {{sí/no, cuál}}.
Slides: {{6–9}}.
```

**Reglas de generación:**
1. Aplicar núcleo creador + tema Suplementos + acento del producto.
2. Lienzo 1080 × 1920, respetar safe zones de la sección 4.4.
3. Una idea por slide, máximo 30 palabras por slide (portada: 10).
4. Una cápsula Polen por slide como máximo.
5. Ningún dato numérico que no venga en el pedido. Si falta, dejar `[DATO ETIQUETA]` visible.
6. Pasar cada frase por la sección 5 antes de entregar. Si un texto roza un claim no autorizado, reescribir en descriptivo.
7. Disclaimer y firma en la última slide siempre. Disclaimer extra si aparece ashwagandha.
8. Para producción masiva: mantener fijas posiciones de título, cápsula, firma e indicador entre carruseles. Lo que varía es el contenido, no el layout.

---

## 10. Checklist de QA antes de publicar

| Check | ✓ |
|---|---|
| Hook de 10 palabras o menos y legible en la miniatura | ☐ |
| Ningún texto en safe zones (derecha 160 px, inferior 440 px) | ☐ |
| Ningún texto menor a 32 px | ☐ |
| Una sola cápsula Polen por slide | ☐ |
| Todos los datos coinciden con la etiqueta actual de HSN | ☐ |
| Claims solo de la tabla 5.1, en su forma literal | ☐ |
| Cero enfermedades, testosterona, peso, antes/después | ☐ |
| Comparaciones entre formas, no entre marcas | ☐ |
| Disclaimer en última slide y caption (+ extra si es ashwagandha) | ☐ |
| Contenido de marca activado en TikTok + `#publi` primero | ☐ |
| Precio confirmado en la ficha el mismo día, o sin precio | ☐ |
| Sin chilenismos, sin voseo, sin "vosotros" | ☐ |

---

## 11. Pendiente de definir

| Pendiente | Por qué importa |
|---|---|
| Nombre de cuenta `{{HANDLE}}` | Va en todas las slides |
| Normas de HSN para creadores (uso de logo, claims propios, mensajes clave) | Pueden ser más restrictivas que este documento; si existen, mandan ellas |
| Fotos propias de los 3 productos (bote, etiqueta, mano) | Sin foto real el contenido pierde la credibilidad de "lo tomo yo" |
| Etiquetas actuales de los 3 productos | Fuente única de datos para dosis y cantidades |
| Siguiente vertical (Hogar, Ropa) | Crear su tema en la sección 4 sin tocar el núcleo |
