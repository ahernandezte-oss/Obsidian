# 🧠 PREFERENCIAS — PLANTILLA EXTRAÍBLE (genérica)

> **⚙️ PROTOCOLO DE ESTE ARCHIVO (léelo, asistente):**
> 1. **Leer** este archivo al inicio de CADA tarea en este workspace.
> 2. **Aplicar** las reglas al generar cheatsheets y al resolver ejercicios.
> 3. **Actualizar** este archivo cuando el usuario corrija algo o exprese un gusto nuevo: añadir fila a la bitácora (§5) con fecha, sin borrar lo anterior.
> 4. **No borrar** observaciones pasadas: si algo cambia, marca la anterior como `(obsoleta)` y añade la nueva.
> 5. Si hay conflicto entre reglas, gana la **más reciente** (fecha más nueva en la bitácora).
> 6. Esta es una **versión genérica** pensada para copiarse a otros workspaces de otras materias. Cada bloque marcado con 🔧 **PERSONALIZAR** debe adaptarse a la materia del workspace.

**Archivo:** `PREFERENCIAS.md` · **Origen:** `PREFERENCIAS_EXTRAIBLE.md` · **Versión:** 2
**Workspace:** `01_WORKSPACES/CONJUNTOS` (Android: `/storage/emulated/0/Download/arvhicos/01_WORKSPACES/CONJUNTOS`; en Windows era `F:\WORKSPACES\CONJUNTOS`)
**Materia:** Introducción a la teoría de conjuntos (Probabilidad, CEDO y Álgebra se cursan pero **no** se trabajan en este espacio)
**Bóveda de Obsidian (copia obligatoria y publicación):** `02_NOTAS_OBSIDIAN/CONJUNTOS` — repo git `github.com/ahernandezte-oss/Obsidian`; protocolo en `PROMPT_SYNC_OBSIDIAN.md`
**Leyenda de confianza:** ✅ confirmado por el usuario · 🔶 inferido (validar) · ⏳ por preguntar

---

## 0. PERFIL RÁPIDO

- ✅ **Idioma:** español neutro (clases y material en español). Responder en español.
- ✅ **Estilo cognitivo:** visual + algorítmico; aprende con pasos numerados, tablas y contrastes.
- ✅ **Punto débil declarado:** confunde conceptos parecidos → priorizar **tablas "A vs B"** y **reglas de desambiguación**.
- ✅ **Objetivo:** material copiable a mano en **30–40 min** para parciales/tareas.
- ✅ **Prefiere "reglas de oro"** (criterios de bolsillo) antes que definiciones largas.
- ✅ **Agnóstico al modelo:** las preferencias no dependen del modelo que esté respondiendo.

---

## 1. CHEATSHEETS — CÓMO LAS QUIERE

### 1.1 Estructura fija (respetar el orden)
1. **Título** del tema.
2. **§1 PROTOCOLO DE IDENTIFICACIÓN ("El Radar")** → decisión en orden (Paso 0, Paso 1…) + tabla "si… → método" + frases literales del profe (si existen transcripciones).
3. **§2 CAJA DE HERRAMIENTAS** → fórmulas + **diccionario pegado a cada bloque**.
4. **§3 REGLAS DE ORO / CASOS ESPECIALES**.
5. **§4 ALGORITMOS DE RESOLUCIÓN** → pasos numerados + 1 plantilla canónica por método.

### 1.2 Reglas de estilo (✅)
- **Cero metáforas.** Lenguaje operativo.
- **Cero ejemplos decorativos.** Solo la **plantilla mínima** dentro del algoritmo (1 por método).
- **No incluir soluciones de ejercicios de tarea.**
- **Todo algorítmico:** "1. Identifica… 2. Extrae… 3. Aplica…".
- **Diccionario de símbolos para toda fórmula**, inmediatamente debajo (nunca al final del documento).
- **Frases literales del profe** entre comillas → método.
- **Tablas** para: casos, conjeturas, criterios de decisión, símbolos.
- **Emojis-marcador:** 📘 título · 🧭 radar · 🛠️ herramientas · 🔄 reglas · 🚀 algoritmos · 🔤 diccionario.
- **Markdown + LaTeX** con `$...$` inline y `$$...$$` en bloque.
- **Compacto**: que se copie rápido a mano.

### 1.3 Prohibido (❌)
- ❌ Metáforas / analogías.
- ❌ Ejemplos largos o ejercicios resueltos puntuales dentro de la cheatsheet.
- ❌ Diccionario al final del documento.
- ❌ Teoría "de libro" sin uso operativo.

### 1.4 Formato de entrega
- ✅ Entregar la cheatsheet **inline en el chat** (para copiar) **Y** guardada como `.md`.
- ✅ **Dos pasos distintos:** (1) *generar* el `.md` en el workspace; (2) *publicar* en la bóveda siguiendo `PROMPT_SYNC_OBSIDIAN.md` (`fetch` → `rebase origin/main` → `commit` solo de la materia → `push origin main` → verificar que SHA256 local == SHA256 en `origin/main` y `HEAD == origin/main`). Copiar el archivo a Obsidian **no** lo publica.
- ✅ Solo `.md`, sin PDF.
- ✅ Presentar el archivo con la tarjeta nativa (`present`) cuando aplique.

### 1.6 NOMENCLATURA DEL ARCHIVO ✅ (convención real de la bóveda)
- Formato: `<AAMMDD>_<TEMA_EN_MAYUSCULAS>.md` — **la fecha va primero**, año-mes-día a dos dígitos (`26` = 2026).
- El tema va en MAYÚSCULAS con `_` entre palabras, y describe el **contenido de la clase**, no la materia.
- La fecha es la de la **transcripción**, no la de hoy.
- Ejemplos reales: `261029_CARDINALIDAD_Y_FINITUD.md` · `261103_CONTABLES_SELECCION_Y_PRODUCTO.md` · `261105_AXIOMA_DE_ELECCION.md`.
- La **ficha del archivo** dentro del documento repite el nombre exacto y la marca `AAMMDD` = `261105`.
- Dos copias idénticas: maestro en `01_WORKSPACES/CONJUNTOS` y copia en `02_NOTAS_OBSIDIAN/CONJUNTOS`. Se copian con `cp` y se verifica SHA256. Después se **publica** según `PROMPT_SYNC_OBSIDIAN.md`.
- ⚠️ Si el editor re-guarda un archivo cambiando **finales de línea** (LF ↔ CRLF), el hash cambia **sin** que cambie el contenido: en ese caso se normaliza copiando el maestro sobre la copia, no se reconstruye a mano. *(Obsolescencia de rutas: `F:\WORKSPACES\...` y `F:\NOTES\...` eran las de Windows; en Android son las rutas de arriba.)*

### 1.7 Esqueleto reutilizable

# 📘 CHEATSHEET: <TEMA>

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)
- Pregunta de decisión en orden (Paso 0, Paso 1…).
- Tabla: "Si el enunciado dice… → usa…".
- Frases literales del profe → método.

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)
### A. <Concepto 1>
<fórmula>
**🔤 Diccionario:** <cada símbolo>
### B. <Concepto 2>
...

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES
- Caso límite 1…
- Caso límite 2…

## 🚀 4. ALGORITMOS DE RESOLUCIÓN
### <Método 1>
1. … 2. … 3. …
**Plantilla:** <ejemplo mínimo en pasos>
### <Método 2>
1. … 2. … 3. …
**Plantilla:** <ejemplo mínimo en pasos>

---

## 2. RESOLUCIÓN DE EJERCICIOS — SU MÉTODO

1. **Identificar** el modelo/método (Radar) **antes** de calcular.
2. **Extraer parámetros** y ajustar unidades.
3. **Traducir** el texto a lenguaje matemático (ej.: "al menos" → $1 - P(X \le k-1)$).
4. **Paso a paso**, sin saltar el cálculo intermedio.
5. **Verificar** al final (sustitución, condiciones, unidades, conteo de constantes/parámetros).

Reglas adicionales:
- Quiere saber **por qué NO** usar un método (restricciones), no solo cuándo sí.
- Prefiere **tabla de casos** a explicaciones largas.
- Si hay ambigüedad, mostrar el **criterio de decisión explícito**.

### 2.1 Modo pedagógico (para practicar ejercicios)
No basta con dar el resultado. Reglas:
1. **Emojis como marcadores de paso** (🧭 radar · 🔍 verificación · 🧩 traducción · 🚦 clasificación · 🏗️ construcción · ✅ check · ⚠️ trampas · 🧠 "cómo lo replicas" · 📌 respuesta final). Los emojis EJEMPLIFICAN lo que ocurre en cada paso.
2. **Referenciar la cheatsheet en cada paso** ("📘 Cheatsheet §2.B, caso 1") para ligar teoría ↔ acción.
3. **Mostrar CÓMO lo hace** y luego CÓMO lo replica él (algoritmo mental), no solo el cálculo.
4. **Verificación final** de la solución, paso a paso, para entrenar autocontrol.
5. **Señalar trampas** típicas **del ejercicio que se está resolviendo**. NO incluir variantes contrafactuales ("qué cambiaría si el enunciado fuera otro"): el foco es solo el enunciado actual.
6. Avanzar **un ejercicio a la vez**; esperar a que el usuario diga "siguiente".
7. **Solo chat.** La resolución de ejercicios se entrega **únicamente inline en el chat**: NO crear `.md` por ejercicio, NO usar `present` para ejercicios. El `.md` es solo para cheatsheets.
8. **Exactitud ante todo:** revisar cada cálculo, cada signo y cada resultado antes de responder; cero errores.
9. **Bloques 🧠 "¿de dónde sale esto?"**: después de cada paso no obvio, explicar en una o dos líneas **de dónde surge la idea** (qué definición o teorema la fuerza y por qué no otra). Es su formato favorito para aprender; mantenerlo siempre.
10. **Está APRENDIENDO con los ejercicios** (en clase muchas veces no puede atender): cada solución debe ser **autosuficiente**, con las definiciones desplegadas y sin dar por sabido ningún paso del material.

### 2.2 FORMATO MATEMÁTICO — REGLA ESTRICTA ✅
- ❌ **Prohibido** usar bloques de código (comillas invertidas) para escribir fórmulas o variables.
- ✅ Toda expresión matemática **en línea** va entre un solo signo de dólar: `$...$`.
- ✅ Las ecuaciones **en bloque** o pasos grandes van entre doble signo de dólar, cada delimitador en su propia línea: `$$...$$`.
- Los bloques de código quedan reservados **exclusivamente** para código de programación real.

### 2.3 ESTRUCTURA OBLIGATORIA DE UNA DEMOSTRACIÓN ✅
Toda demostración se entrega con este esqueleto, sin saltarse ningún bloque:

```
HIPÓTESIS  → qué me dan (con las definiciones ya desplegadas)
TESIS      → qué debo probar, escrita en forma de regla (implicación, igualdad, cuantificador)
DEMOSTRACIÓN → pasos numerados; cada paso lleva [JUSTIFICACIÓN] al lado
CONCLUSIÓN → qué quedó probado y cómo se usa
```

Reglas asociadas:
1. **Anunciar la forma lógica de la tesis antes de escribir el primer paso** ("la tesis es una igualdad de conjuntos, luego se prueba por doble contenencia").
2. **Marcar el origen de cada técnica**: de qué definición/teorema sale el paso y por qué no otro. Nunca un paso "que aparece de la nada".
3. Si el intento del estudiante falla, **diagnosticar el error exacto** (qué objeto o variable está mal, y por qué la afirmación es falsa — con contraejemplo si aplica) **antes** de mostrar lo correcto.
4. Incluir, cuando haga falta, la tabla **"forma de la tesis → regla que la produce"** para entrenar la elección del método.
5. Toda definición que se use debe estar escrita **antes** de su primer uso; si no se ha definido, no se usa.

### 2.4 ESTILO DE CADENA — cadenas de igualdades y equivalencias ✅
Es su forma natural de resolver y de leer. Toda cuenta o deducción se escribe como **cadena vertical**:

1. **Una relación por línea**, y la línea siguiente **empieza con el conector** ($=$, $\iff$, $\Rightarrow$, $\subseteq$, $\approx$, $\preccurlyeq$).
2. **Justificación al final de cada línea**, entre paréntesis: qué definición, hipótesis o teorema produce ese eslabón.
3. **No se salta el álgebra intermedio**: cada distribución, cancelación, sustitución o agrupación es una línea propia con su "por qué".
4. **$\iff$ solo si el paso es reversible**; si no lo es, $\Rightarrow$. Nunca mezclarlos sin marcarlo.
5. **Cadenas mixtas** ($\approx$, $\preccurlyeq$, $\subseteq$, $=$) permitidas solo si cada eslabón se justifica y el tipo se conserva o se justifica el cambio por transitividad.
6. **Cierre explícito:** la cadena termina con "por tanto …" y la tesis escrita tal cual.
7. Puedo reconocer formas a mitad de la cadena y decirlo ("reconozco la forma original", "vuelvo a la forma explícita").
8. **Alineación visual:** usar `\begin{aligned}...\end{aligned}` en un solo bloque para que los conectores ($=$, $\iff$, $\Rightarrow$, $\preccurlyeq$) queden **alineados** uno detrás de otro. Una cadena alineada y legible vale más que muchas líneas sueltas.
9. **No todo es $\iff$:** se elige el conector por legibilidad **y** por la fuerza real del paso. Si se lee mejor como reducción ("basta probar…"), se escribe así, con $\Leftarrow$ o en palabras.
10. **Cada eslabón cierra con su porqué en el paréntesis**, nunca en un párrafo aparte.

Ejemplo canónico (el que le gusta):

$$
y_1'' = -y_1 \quad\left(\text{reconozco la forma original}\right)
$$

$$
y_1''' = -y_1' \quad\left(\text{derivo la igualdad anterior}\right)
$$

$$
y_1'''-2y_1''+2y_1' = -y_1'-2\left(-y_1\right)+2y_1' \quad\left(\text{sustituyo } y_1'' \text{ y } y_1'''\right)
$$

| Conector | Se usa cuando |
|---|---|
| $=$ | igualdad de objetos del mismo tipo |
| $\iff$ | el paso vale en las dos direcciones |
| $\Rightarrow$ | el paso vale en una sola dirección |
| $\subseteq$ | contenencia entre conjuntos |
| $\approx$ | equipotencia entre conjuntos |
| $\preccurlyeq$ | dominancia cardinal |

---

## 3. NOTACIÓN Y CONVENCIONES

- Usar la notación de la clase/libro del curso; si el profe usa una convención, respetarla.
- Títulos de sección en **MAYÚSCULAS**.
- Pasos numerados con `1. 2. 3.`.
- ✅ **Nombres de archivo de cheatsheet:** `<AAMMDD>_<TEMA_PRINCIPAL>.md` — **la fecha va primero** para que el orden alfabético coincida con el orden cronológico de las clases. Ejemplo: `261015_RECURSION_SIMPLE_Y_PARAMETRICA.md`. (Reemplaza la convención anterior `<TEMA>-<DDMMAA>.md`, que queda **obsoleta**.)
- 🔧 **PERSONALIZAR — convenciones por materia.** Plantilla sugerida:

| Materia | Convenciones acordadas |
|---|---|
| Cálculo / EDO | $y, y', y^{(n)}$; raíz característica **$\lambda$** (no $m$) |
| Probabilidad | $\lambda$ = tasa, $r$ = forma, $a,b$ = límites del intervalo |
| Álgebra | 🔧 PERSONALIZAR |
| Teoría de conjuntos | $A\approx B$ = equipotencia (nunca $=$, nunca "mismo cardinal" antes de definirlo) · $A\preccurlyeq B$ / $A\prec B$ = dominancia / dominancia estricta · $B^{A}=\{f \mid f:A\to B\}$ (no ${}^{A}B$) · $\mathcal{P}(A)$ = conjunto de partes · $\lvert A\rvert$ = cardinal (solo definido para finitos) · naturales de von Neumann: $0=\emptyset$, $n+1=n\cup\{n\}$, antecesor $\bigcup n$ |

---

## 4. FLUJO DE TRABAJO / ARCHIVOS

- ✅ Trabajar en el workspace activo (🔧 PERSONALIZAR ruta).
- ✅ Los libros de la carpeta suelen estar **vacíos (0 bytes)** → no depender de ellos; usar transcripciones de clase + teoría estándar del curso.
- ✅ Entregar cheatsheet **inline en el chat** **Y** guardada como `.md`.
- ✅ Entregar resoluciones de ejercicios **solo inline en el chat** (sin `.md`, sin `present`).
- ✅ Presentar archivos con la tarjeta nativa (`present`) solo cuando el archivo sea un entregable real (cheatsheet, guía).

---

## 5. BITÁCORA DE OBSERVACIONES

> Copiar las filas que apliquen al workspace nuevo y añadir las propias a partir de aquí. No borrar filas antiguas.

| Fecha | Tipo | Observación | Fuente |
|---|---|---|---|
| — | ✅ Confirmado | Quiere cheatsheet "Radar → Herramientas → Reglas → Algoritmos" con diccionario por fórmula. | Petición explícita. |
| — | ✅ Confirmado | Le sirven "plantillas" resueltas dentro de cada algoritmo (1 por método). | Aceptó las plantillas. |
| — | ✅ Confirmado | Material en español (clases grabadas y transcritas). | Transcripciones de clase. |
| — | ✅ Confirmado | Español neutro. | Respuesta directa. |
| — | ✅ Confirmado | Cheatsheets solo en `.md` (sin PDF). | Respuesta directa. |
| — | ✅ Confirmado | En práctica de ejercicios: máximo nivel pedagógico, emojis que ejemplifican cada paso, referenciar la cheatsheet en cada acción y explicar cómo replicar el procedimiento. | Petición explícita. |
| — | ✅ Confirmado | **Ejercicios: solo inline en el chat.** No crear `.md` ni usar `present` para resoluciones. | Corrección directa del usuario. |
| — | ✅ Confirmado | **No incluir sección "qué cambiaría si el enunciado fuera otro".** Foco total en el enunciado actual. | Corrección directa del usuario. |
| — | ✅ Confirmado | Exigencia de **cero errores**: revisar derivadas, signos, cálculos y resultados antes de responder. | Corrección directa del usuario. |
| — | ✅ Confirmado | **Prohibido usar bloques de código (comillas invertidas) para fórmulas o variables.** Inline `$...$`, bloque `$$...$$`. | Corrección directa del usuario. |
| — | 🔶 Inferido | Prefiere emojis como marcadores de sección y tablas densas. | Cheatsheets aceptadas. |
| — | 🔶 Inferido | Resolver ejercicios **de a uno** y esperar "siguiente". | Práctica sostenida de tareas. |
| — | 🔶 Inferido | Mantener las preferencias agnósticas al modelo (puede cambiar de modelo a mitad de sesión). | Observado en sesión. |
| 02/11/2026 | ✅ Confirmado | Las cheatsheets de **conjuntos** se guardan en `F:\NOTES\NOTAS DE CLASE\CONJUNTOS` (bóveda de Obsidian), además de la copia maestra en el workspace. | Petición explícita. |
| 02/11/2026 | ✅ Confirmado | La copia para Obsidian se hace **copiando el archivo** (nunca reescribiéndolo) y se verifica con SHA256; ambos hashes deben coincidir. | `PROMPT_CHEATSHEETS.md` §1 + verificación en sesión. |
| 02/11/2026 | ✅ Confirmado **(obsoleta desde 03/11/2026)** | Nomenclatura de archivo: `<TEMA_PRINCIPAL>-<DDMMAA>.md` con la fecha de la **transcripción**, no la de hoy; sin el prefijo del nombre de la materia. | `PROMPT_CHEATSHEETS.md`. |
| 02/11/2026 | ✅ Confirmado | En tablas Markdown: usar `\lvert A\rvert` en vez de barras simples (rompen la celda) y `\frac` en vez de `\dfrac` (MathJax de Obsidian). | `PROMPT_CHEATSHEETS.md` §2. |
| 02/11/2026 | ✅ Confirmado | Marcar con `➕` todo lo que se agregue y no venga de la transcripción de clase. | `PROMPT_CHEATSHEETS.md`. |
| 02/11/2026 | ✅ Confirmado | **Demostraciones con estructura HIPÓTESIS → TESIS → DEMOSTRACIÓN → CONCLUSIÓN**, y las definiciones escritas antes de usarlas (ver §2.3). | Corrección directa del usuario. |
| 02/11/2026 | ✅ Confirmado | **Explicar de dónde sale cada razonamiento**: qué definición/teorema lo obliga y por qué no otro; nada de pasos que aparecen de la nada. | Corrección directa del usuario. |
| 02/11/2026 | ✅ Confirmado | Cuando su intento falla, **diagnosticar el error exacto** (variable u objeto equivocado; contraejemplo si la afirmación es falsa) antes de mostrar la versión correcta. | Corrección directa del usuario. |
| 02/11/2026 | 🔶 Inferido | Añadir la tabla "forma de la tesis → regla que la produce" para elegir el método sin adivinar. | Derivado de su pregunta "¿cómo se me ocurriría?". |
| 03/11/2026 | ✅ Confirmado | **Cada cheatsheet cubre SOLO lo nuevo de su transcripción.** No repetir temas de cheatsheets anteriores: se citan por nombre y sección (`📘 ...-291026 §2.C`). | Petición explícita. |
| 03/11/2026 | ✅ Confirmado | La cheatsheet abre con una línea de **continuidad** (qué toma de cheatsheets previas) y cierra con **lo que quedó abierto/pendiente** en clase. | Petición explícita + práctica aceptada. |
| 03/11/2026 | ✅ Confirmado | **Le gusta resolver en CADENA** (igualdades / $\iff$ / $\Rightarrow$, con justificación al final de cada línea). Toda cuenta o deducción se escribe así (ver §2.4). | Petición explícita con ejemplo. |
| 03/11/2026 | ✅ Confirmado | Cadenas **alineadas visualmente** (`aligned`), y **no** forzar $\iff$: usar el conector que de verdad corresponda y el que se lea mejor (ver §2.4). | Corrección directa del usuario. |
| 03/11/2026 | ✅ Confirmado | Mantener **siempre** los bloques 🧠 "de dónde sale esto" (ver §2.1, regla 9). | Petición explícita. |
| 03/11/2026 | ✅ Confirmado | Aprende la materia **resolviendo ejercicios** (en clase no alcanza a atender): las soluciones deben ser autosuficientes y docentes (ver §2.1, regla 10). | Declaración explícita. |
| 03/11/2026 | ✅ Confirmado | Si la maestra y la copia de Obsidian **divergen**, se conserva la **versión más reciente** (por fecha de modificación) y se sincroniza la otra copiándola; se verifica con SHA256. | Corrección directa del usuario. |
| 03/11/2026 | ✅ Confirmado | **Nomenclatura de archivo: `<AAMMDD>_<TEMA_PRINCIPAL>.md`, la fecha PRIMERO** (`261015_RECURSION_SIMPLE_Y_PARAMETRICA.md`), para que el orden alfabético sea el orden de las clases. Reemplaza `<TEMA>-<DDMMAA>.md`. Se renombraron las 6 cheatsheets existentes (maestra + bóveda) y se actualizaron las citas internas. | Corrección directa del usuario. |
| 05/11/2026 | ✅ Confirmado | Al crear una cheatsheet nueva: renombrarla **de una vez** con el patrón `<AAMMDD>_<TEMA>.md` (fecha primero) y escribir ese mismo nombre en la ficha interna y en las citas. Ya no usar `<TEMA>-<DDMMAA>.md`. | Convención vigente de la bóveda. |
| 05/11/2026 | ✅ Confirmado | Si al comparar maestro y copia el SHA256 difiere, **primero verificar finales de línea** (LF vs CRLF): contenido igual + finales distintos ⇒ el hash cambia sin que cambie nada. Se normaliza copiando el maestro sobre la copia. | Verificado en `261103_...` (548 CR de diferencia, 0 bytes de contenido). |
| 03/11/2026 | ✅ Confirmado | La **tarjeta de la ficha** mantiene la fecha legible (`DD/MM/AAAA`) y además el código `AAMMDD` que va en el nombre. | Derivado de la nueva convención. |
| 10/11/2026 | ✅ Confirmado | La bóveda de Obsidian es un **repo git** (`02_NOTAS_OBSIDIAN`, remoto GitHub `main`): copiar el `.md` **no** lo publica. Tras copiar: `fetch` → `rebase origin/main` → `commit` (solo la carpeta de la materia) → `push`; verificar SHA256 local == SHA256 en `origin/main` y `HEAD == origin/main`. Prohibido `--force`, `--amend` sobre publicado y mezclar materias en un commit. | `PROMPT_SYNC_OBSIDIAN.md` (CEDO) + ejecución verificada. |

---

## 6. RESPUESTAS CONFIRMADAS

- ✅ **Idioma:** español neutro.
- ✅ **Cheatsheets:** solo `.md`, con diccionario por fórmula.
- ✅ **Ejercicios:** solo en el chat, sin `.md`, de a uno, sin secciones contrafactuales.
- ✅ **Matemática:** formato estricto `$...$` / `$$...$$`, sin bloques de código.
- 🔧 **PERSONALIZAR:** materias activas del workspace, convenciones de notación y cualquier respuesta ya confirmada para esa materia.
