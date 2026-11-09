# 📘 CHEATSHEET — CEDO · 14/10/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261014_NO_LINEALES_ORDEN_SUPERIOR.md`
> - **Tema principal:** Ecuaciones diferenciales **no lineales** de orden superior — reducción de orden por cambio de variable
> - **Fecha de clase:** 14/10/2026
> - **Fuente:** transcripción `语音 261014_140133` (clase del 14/10/2026) + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261014_NO_LINEALES_ORDEN_SUPERIOR` §2.B»
> - **Alcance:** esta clase desarrolla **el Caso 1 y el Caso 2**. El profesor anunció **cuatro casos** para el tema; los otros dos quedan ⏳ pendientes.
> - **Complemento:** las EDO **lineales** (coeficientes constantes y variables) están en `261102_EDO_ORDEN_SUPERIOR` y `261104_OSTROGRADSKY_LIOUVILLE`.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Es lineal?**
- Sí (la incógnita $y$ y sus derivadas aparecen a la primera potencia, sin productos entre ellas) → **no es este tema**. 👉 `261102_EDO_ORDEN_SUPERIOR` §1
- No (aparecen $y^2$, $(y')^2$, $e^{y}$, $y\,y''$, $\sqrt{y'}$…) → Paso 1.

**Paso 1 — ¿Qué variable **falta** en la ecuación?** (esto decide el caso)

| Falta… | Caso | Cambio |
|---|---|---|
| Falta $y$ (solo hay derivadas, tal vez con $x$) | **Caso 1** | $y' = z(x)$ |
| Falta $x$ (hay $y$ y derivadas, sin $x$) | **Caso 2** | $y' = p(y)$ |
| No falta ninguna | ⏳ fuera de esta clase | — |

**Paso 2 — ¿Cuánto hay que bajar?** La reducción baja **un orden** por cambio. Orden $n$ con Caso 1 → orden $n-1$ en $z$. Para volver a $y$ hay que integrar $n$ veces ⇒ **$n$ constantes**.

### Tabla de decisión

| Si el enunciado dice… | Caso / método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| No aparece $y$, solo $y'$, $y''$, … (con o sin $x$) | Caso 1: $y' = z$ | $y^{(k)} = z^{(k-1)}$ | §2.B · §4.1 |
| No aparece $x$; sí $y$, $y'$, $y''$ | Caso 2: $y' = p(y)$ | $y'' = p\frac{dp}{dy}$ | §2.C · §4.2 |
| Orden $3$ sin $x$ | Caso 2 (necesita $y'''$) | $y''' = p\left(\frac{dp}{dy}\right)^{2} + p^{2}\frac{d^{2}p}{dy^{2}}$ | §2.C |
| Orden $2$ sin $y$ | Caso 1 | $z' = f(x,z)$ | §4.1 |
| La ecuación trae $y^{2}$, $(y')^{2}$, $e^{y}$, $y\,y''$ | No lineal: **este tema** | — | §2.A |
| Tras el cambio queda una EDO de primer orden separable | Integrar y **contar constantes** | — | §3 Caso 1 |
| Aparece una raíz al despejar $p$ | Elevar al cuadrado o cambiar variable, $\pm$ | — | §3 Caso 3 |

### Frases literales del profesor (transcripción del 14/10)

- "Esta cuestión es más complicada… **no hay teoría general**. Pero yo doy a ustedes métodos… podemos buscar soluciones analíticas en cuadratura" → no hay método general; hay **dos cambios** que funcionan en casos reconocibles.
- "Para resolver ecuaciones no lineales… **bajar grado**, bajar grado hasta ecuación de primer orden" → el objetivo es siempre **bajar el orden**.
- "**No hay simetría**, por favor, escribir bien" → al derivar $y'''$ en el Caso 2, no hay patrón simétrico; hay que hacer el producto con cuidado.
- "Todos las constantes **siempre del lado derecho**" → al integrar, las constantes se acumulan a la derecha.
- "Si usted tiene acá **raíz**, necesita quitar raíz siempre" → cuando aparece $\sqrt{\phantom{x}}$, conviene un cambio que la elimine.
- "Necesita **condición** e **intervalo de existencia**" → comprobar los denominadores y el dominio al final.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Forma general de una EDO no lineal de orden $n$

$$
F\left(x,\, y,\, y',\, y'',\, \ldots,\, y^{(n)}\right) = 0
$$

**Solución general:** depende de $n$ constantes.

$$
y = y\left(x;\, C_1, C_2, \ldots, C_n\right)
$$

**🔤 Diccionario:**
- $F$: función arbitraria (no lineal) de sus argumentos.
- $y^{(k)}$: derivada $k$-ésima de $y$.
- $n$: orden de la ecuación; coincide con el **número de constantes** de la solución general.
- $C_1, \ldots, C_n$: constantes arbitrarias.

### B. Caso 1 — falta $y$ (solo derivadas)

**Condición de uso:** la ecuación **no contiene $y$**, solo $y'$, $y''$, …, eventualmente con $x$.

$$
F\left(x,\, y',\, y'',\, \ldots,\, y^{(n)}\right) = 0
$$

**Cambio:** se llama $z$ a la primera derivada que aparece.

$$
y' = z(x) \;\Longrightarrow\; y'' = z', \quad y''' = z'', \quad \ldots, \quad y^{(n)} = z^{(n-1)}
$$

La EDO pasa de orden $n$ en $y$ a orden $n-1$ en $z$. Si además **tampoco aparece $x$**, se repite el mismo cambio sobre $z$.

**🔤 Diccionario:**
- $z(x)$: nueva incógnita; es $y'$, no $y$.
- $y^{(n)} = z^{(n-1)}$: regla de conversión (baja un orden cada derivada).
- La solución final se obtiene integrando $n$ veces $z$.

### C. Caso 2 — falta $x$ (ecuación autónoma)

**Condición de uso:** la ecuación **no contiene $x$** explícitamente, pero sí $y$ y sus derivadas.

$$
F\left(y,\, y',\, y'',\, \ldots,\, y^{(n)}\right) = 0
$$

**Cambio:** se toma $p$ como función de $y$, no de $x$.

$$
y' = p(y), \qquad p' = \frac{dp}{dy}
$$

$$
y'' = p\,\frac{dp}{dy}
$$

$$
y''' = p\left(\frac{dp}{dy}\right)^{2} + p^{2}\frac{d^{2}p}{dy^{2}}
$$

**Advertencia de notación:** aquí $p'$ significa $\frac{dp}{dy}$, **no** $\frac{dp}{dx}$. Derivar respecto de $x$ exige la regla de la cadena: $\frac{d}{dx} = p\frac{d}{dy}$.

**🔤 Diccionario:**
- $p(y)$: nueva incógnita; es $y'$ pero vista como función de $y$.
- $\frac{dp}{dy}$: derivada de $p$ respecto de **$y$** (no de $x$).
- $p\frac{dp}{dy}$: el término $y''$ expresado con la nueva variable.
- $y'''$: se obtiene derivando $p\frac{dp}{dy}$ respecto de $x$ y aplicando la cadena; **no** es simétrico con los anteriores.

### D. Cómo se obtiene la lista de derivadas (regla de la cadena) ➕

Cada derivada respecto de $x$ se convierte en derivada respecto de $y$ multiplicando por $\frac{dy}{dx} = p$:

$$
\frac{d}{dx} = \frac{dy}{dx}\cdot\frac{d}{dy} = p\,\frac{d}{dy}
$$

Aplicándolo dos veces:

$$
y''' = \frac{d}{dx}\left(p\frac{dp}{dy}\right) = p\frac{d}{dy}\left(p\frac{dp}{dy}\right) = p\left[\frac{dp}{dy}\cdot\frac{dp}{dy} + p\frac{d^{2}p}{dy^{2}}\right]
$$

**🔤 Diccionario:** $\frac{d}{dx}$: derivada respecto de la variable independiente · $\frac{d}{dy}$: derivada respecto de la incógnita · $p$: factor que aparece siempre al cambiar de variable.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

| Caso | Situación | Qué hacer | 👉 Ir a |
|---|---|---|---|
| **Caso 1** | Tras el cambio queda una EDO de primer orden | Resolverla y **acumular todas las constantes a la derecha** | §4.1 |
| **Caso 2** | Aparece $\sqrt{\phantom{x}}$ al despejar $p$ | Elevar al cuadrado o cambiar variable para eliminar la raíz | §3 Caso 3 |
| **Caso 3** | Hay que elegir el signo al sacar raíz | Aparece $\pm$; **son dos familias** de soluciones, no un error | §4.2 |
| **Caso 4** | La integral final no es de tabla | Usar cambio de variable o partes; si no es elemental, dejarla **indicada** | §4.2 |
| **Caso 5** | Al integrar aparecen constantes absorbibles | Se puede redefinir $2C_1 \rightarrow C_1$: **no cambia** la familia | §4.2 |
| **Caso 6** | Hay denominadores con $y$ o con $x$ | Imponer la condición y dar el **intervalo de existencia** | §3 Regla 4 |
| **Caso 7** | Se pide la solución general | Debe tener **exactamente $n$ constantes**; si faltan, se perdió una integración | §2.A |

**Reglas de oro (bolsillo):**
1. **El orden solo baja con un cambio de variable.** No hay fórmula cerrada para lo no lineal.
2. **Falta $y$ → $y' = z$.** Falta $x$ → $y' = p(y)$. Es la única decisión del método.
3. **Cuenta las constantes**: tantas como el orden. El profesor insiste en esto.
4. **Condición e intervalo de existencia:** si aparece $\frac{1}{C_1}$, $1 - C_1x$, $\ln\left(\vert\ldots\vert\right)$ o una raíz, hay que decir dónde es válida la solución.
5. **La solución puede quedar en forma implícita** ($G(y) = Kx + C_2$). Es válido: no siempre se despeja $y$.
6. Si al sustituir **no desaparece** una de las variables, el caso está mal elegido: revisar el Paso 1.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Caso 1 — falta $y$ (cambio $y' = z$)

1. **Verificar** que la ecuación no contiene $y$ (§1, Paso 1).
2. **Cambiar** $y' = z$ y escribir las derivadas superiores como $z', z'', \ldots$
3. **Reescribir** la EDO: ahora es de orden $n-1$ en $z$.
4. Si **tampoco hay $x$**, repetir el cambio sobre $z$ (§3 Caso 1).
5. **Resolver** la EDO de primer orden resultante (normalmente separable).
6. **Volver a $y$**: integrar $y' = z$ tantas veces como haga falta.
7. **Contar** las constantes (deben ser $n$) y dar el intervalo de existencia.

**Plantilla (ejemplo de clase):** $x^{2}y'' = \left(y'\right)^{2}$

1. No aparece $y$ → **Caso 1**.
2. $y' = z \Rightarrow y'' = z'$.
3. $x^{2}z' = z^{2}$.
4. Es separable: $\dfrac{dz}{z^{2}} = \dfrac{dx}{x^{2}}$.
5. Integrando: $-\dfrac{1}{z} = -\dfrac{1}{x} + C_1 \Rightarrow \dfrac{1}{z} = \dfrac{1}{x} - C_1 = \dfrac{1 - C_1x}{x}$.
6. Despejando: $z = \dfrac{x}{1 - C_1x}$, y como $z = y'$, se integra: $\dfrac{dy}{dx} = \dfrac{x}{1-C_1x}$.
7. Con $u = 1 - C_1x$: $y = \dfrac{1}{C_1^{2}}\Big[1 - C_1x - \ln\left\vert 1 - C_1x\right\vert\Big] + C_2$.

**Comprobación:** $y' = \dfrac{x}{1-C_1x}$ y $y'' = \dfrac{1}{\left(1-C_1x\right)^{2}}$, luego $x^{2}y'' = \dfrac{x^{2}}{\left(1-C_1x\right)^{2}} = \left(y'\right)^{2}$ ✔

**Variante orden 3 (mismo método, dos cambios):** $y''' = \left(y''\right)^{2}$ → con $z = y''$ queda $z' = z^{2}$, de donde $z = -\dfrac{1}{x+C_1}$; integrando dos veces más, $y = -\left(x+C_1\right)\ln\left\vert x+C_1\right\vert + \left(x+C_1\right) + C_2x + C_3$.

### 4.2 Caso 2 — falta $x$ (cambio $y' = p(y)$)

1. **Verificar** que la ecuación no contiene $x$.
2. **Cambiar** $y' = p(y)$ y escribir $y'' = p\dfrac{dp}{dy}$ (y $y'''$ si hace falta, §2.C).
3. **Reescribir** la EDO: ahora es de primer orden en $p$ como función de $y$.
4. **Resolver** para $p$ (separable en los casos de clase).
5. **Volver a $y$**: $\dfrac{dy}{dx} = p(y)$ → separar e integrar.
6. **Contar** constantes y comprobar el dominio.

**Plantilla (ejemplo de clase):** $2y\,y'' = \left(y'\right)^{2} + 1$

1. No aparece $x$ → **Caso 2**.
2. $y' = p$, $y'' = p\dfrac{dp}{dy}$.
3. $2y\,p\dfrac{dp}{dy} = p^{2} + 1$.
4. Separando: $\dfrac{2p\,dp}{p^{2}+1} = \dfrac{dy}{y}$.
5. Integrando: $\ln\left(p^{2}+1\right) = \ln y + \ln C_1 \Rightarrow p^{2}+1 = C_1y$.
6. Sacando raíz: $p = \pm\sqrt{C_1y - 1}$, y como $p = \dfrac{dy}{dx}$: $\dfrac{dy}{\sqrt{C_1y-1}} = \pm\,dx$.
7. Integrando: $\dfrac{2}{C_1}\sqrt{C_1y-1} = \pm\left(x + C_2\right)$, es decir $y = \dfrac{C_1}{4}\left(x+C_2\right)^{2} + \dfrac{1}{C_1}$.

**Comprobación:** $y' = \dfrac{C_1}{2}\left(x+C_2\right)$ y $y'' = \dfrac{C_1}{2}$, luego $2y\,y'' = C_1\left[\dfrac{C_1}{4}\left(x+C_2\right)^{2} + \dfrac{1}{C_1}\right] = \dfrac{C_1^{2}}{4}\left(x+C_2\right)^{2} + 1 = \left(y'\right)^{2}+1$ ✔

**Variante con integral no elemental:** $y'' = e^{y}$ → con $y' = p$ queda $p\dfrac{dp}{dy} = e^{y}$, de donde $p^{2} = 2\left(e^{y}+C_1\right)$. La solución se deja en forma implícita: $\displaystyle\int\frac{dy}{\sqrt{2\left(e^{y}+C_1\right)}} = \pm\left(x + C_2\right)$ (§3 Caso 4).

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿El archivo se llama `AAMMDD_TEMA.md`, con la fecha de la clase primero?
- [ ] ¿La ficha del archivo está en el título (nombre, tema, fecha, fuente, cómo citarla)?
- [ ] ¿Las 5 secciones están en orden y con sus emojis-marcador?
- [ ] ¿La tabla del Radar tiene 4 columnas y «👉 Ir a» apunta a un bloque real en todas las filas?
- [ ] ¿Cada fórmula tiene su diccionario justo debajo?
- [ ] ¿Toda la matemática usa `$...$` en línea y `$$...$$` en bloque, sin bloques de código?
- [ ] ¿En tablas se usó `\frac` (no `\dfrac`) y `\vert`/`\mid` (no barras verticales sueltas)?
- [ ] ¿Hay una plantilla mínima por algoritmo y ningún ejemplo decorativo?
- [ ] ¿Está marcado con ➕ lo que se añadió y no venía de la clase?
- [ ] ¿Se copió el espejo a `/storage/emulated/0/Download/arvhicos/02_NOTAS_OBSIDIAN/CEDO` con hash SHA256 idéntico?
- [ ] ¿Quedó registrado que los **Casos 3 y 4** del tema siguen ⏳ pendientes?

---

**Cita rápida:** 📘 Cheatsheet `261014_NO_LINEALES_ORDEN_SUPERIOR` — cita el bloque (`§2.B`, `§3 Caso 3`, `§4.2`…) al resolver.
