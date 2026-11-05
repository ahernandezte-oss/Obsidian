# 📘 CHEATSHEET — CEDO · 26/10/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261026_VARIACION_PARAMETROS.md`
> - **Tema principal:** Variación de parámetros para EDO lineales de orden $n$ — Wronskiano + regla de Cramer
> - **Fecha de clase:** 26/10/2026
> - **Fuente:** transcripción `Cedo 26` (clase del 26/10/2026) + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261026_VARIACION_PARAMETROS` §2.D»
> - **Complemento:** los tres casos de $y_h$ están en `261102_EDO_ORDEN_SUPERIOR` §2.B; la reducción de orden en `261104_OSTROGRADSKY_LIOUVILLE`.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Es homogénea?**
- Sí ($g(x) = 0$) → **no hace falta** variación de parámetros: solo $y_h$. 👉 §3 Caso 0
- No → Paso 1.

**Paso 1 — ¿Sirve coeficientes indeterminados o hay que ir a variación de parámetros?**

| $g(x)$ | Conviene | Motivo |
|---|---|---|
| Polinomio, $e^{ax}$, $\sin$, $\cos$ o combinaciones | Coeficientes indeterminados (más rápido) | No hay integrales |
| $\tan x$, $\sec x$, $\ln x$, $\sqrt{x}$, $\frac{1}{x}$, $\frac{1}{x+2}$ | **Variación de parámetros** | No hay conjetura posible |

**Paso 2 — ¿De qué orden es la EDO?**
- Orden $2$ → Wronskiano $2\times2$, dos fórmulas ya resueltas. 👉 §2.E · §4.2
- Orden $n$ → sistema de $n$ ecuaciones y Cramer con $W$ de $n\times n$. 👉 §2.C · §2.D · §4.1

### Tabla de decisión

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| $g(x) = 0$ | Solo homogénea | $y = C_1y_1 + \cdots + C_ny_n$ | §2.A · §3 Caso 0 |
| $g(x)$ con $\tan$, $\sec$, $\ln$, $\sqrt{\phantom{x}}$, $\frac{1}{x}$ | **Variación de parámetros** | $C_i' = \frac{W_i}{W}$ | §2.D · §4.1 |
| $g(x)$ polinomio / exponencial / seno / coseno | Coeficientes indeterminados | conjetura | §3 Caso 2 |
| Orden $2$ | Dos fórmulas directas | $C_1' = -\frac{y_2g}{W}$, $C_2' = \frac{y_1g}{W}$ | §2.E · §4.2 |
| Orden $3$ o $4$ | Determinante reducido por cofactores | $W_i$ con ceros | §3 Caso 5 |
| Wronskiano $= 0$ | Caso singular | no es conjunto fundamental | §3 Caso 1 |
| La EDO no está normalizada | Dividir por el coeficiente principal | $y^{(n)} + \cdots = g$ | §3 Caso 3 |

### Frases literales del profesor (transcripción del 26/10)

- "Solución es **superposición**: $C_1f_1 + C_2f_2 + \cdots + C_nf_n$… $f_1, f_2$ se llaman **soluciones fundamentales**".
- "Variación de las constantes: cambiamos $C_1$ por $C_1(x)$, $C_2$ por $C_2(x)$".
- "Por método de **Cramer**, yo recomiendo a usted **trabajar solo con Wronskiano**" → no resolver el sistema a mano.
- "**Wronskiano igual a cero, caso singular**… Wronskiano siempre distinto de cero".
- "Si grado tres, Wronskiano $3\times3$; si grado cuatro… **reducir determinante por cofactores por fila**, con ceros, más fácil".

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Estructura de la solución y superposición

$$
y = y_h + y_p, \qquad y_h = C_1y_1 + C_2y_2 + \cdots + C_ny_n
$$

**🔤 Diccionario:**
- $y_h$: solución homogénea (complementaria).
- $y_p$: solución particular que aporta el método.
- $y_1, \ldots, y_n$: **soluciones fundamentales** de la homogénea (linealmente independientes).
- $C_1, \ldots, C_n$: constantes arbitrarias; su número es el orden de la EDO.

### B. Wronskiano

$$
W = \begin{vmatrix} y_1 & y_2 & \cdots & y_n \\ y_1' & y_2' & \cdots & y_n' \\ \vdots & \vdots & \ddots & \vdots \\ y_1^{(n-1)} & y_2^{(n-1)} & \cdots & y_n^{(n-1)} \end{vmatrix}
$$

**Caso $2\times2$:**

$$
W = \begin{vmatrix} y_1 & y_2 \\ y_1' & y_2' \end{vmatrix} = y_1y_2' - y_1'y_2
$$

**🔤 Diccionario:**
- $W$: determinante wronskiano del conjunto fundamental.
- $y_i^{(k)}$: derivada $k$-ésima de la solución $i$.
- $W \neq 0$ en el intervalo ⇒ $\{y_1,\ldots,y_n\}$ es conjunto fundamental.

### C. Variación de parámetros: el cambio de constantes a funciones

Se reemplaza cada constante por una función de $x$:

$$
y_p = C_1(x)\,y_1 + C_2(x)\,y_2 + \cdots + C_n(x)\,y_n
$$

Las funciones se determinan imponiendo el sistema de **$n$ condiciones**:

$$
\begin{cases}
C_1'y_1 + C_2'y_2 + \cdots + C_n'y_n = 0 \\[2pt]
C_1'y_1' + C_2'y_2' + \cdots + C_n'y_n' = 0 \\[2pt]
\quad\vdots \\[2pt]
C_1'y_1^{(n-2)} + \cdots + C_n'y_n^{(n-2)} = 0 \\[2pt]
C_1'y_1^{(n-1)} + \cdots + C_n'y_n^{(n-1)} = g(x)
\end{cases}
$$

**Lectura del sistema:** las primeras $n-1$ filas son **ceros** (se eligen así para simplificar); solo la **última** lleva $g(x)$. La matriz de coeficientes es exactamente el Wronskiano.

**🔤 Diccionario:**
- $C_i(x)$: nuevas incógnitas; sustituyen a las constantes $C_i$.
- $C_i'$: derivada de la incógnita; es lo que se despeja.
- $g(x)$: término independiente **normalizado** (coeficiente principal $1$).
- Las $n-1$ condiciones con $0$: eliminación de las derivadas intermedias de $y_p$.

### D. Regla de Cramer con el Wronskiano

$$
C_i' = \frac{W_i}{W}
$$

donde $W_i$ es el Wronskiano con la **columna $i$ reemplazada** por $(0, 0, \ldots, 0, g(x))^{T}$:

$$
W_1 = \begin{vmatrix} 0 & y_2 & \cdots & y_n \\ 0 & y_2' & \cdots & y_n' \\ \vdots & \vdots & & \vdots \\ g & y_2^{(n-1)} & \cdots & y_n^{(n-1)} \end{vmatrix}, \qquad W_2 = \begin{vmatrix} y_1 & 0 & \cdots & y_n \\ y_1' & 0 & \cdots & y_n' \\ \vdots & \vdots & & \vdots \\ y_1^{(n-1)} & g & \cdots & y_n^{(n-1)} \end{vmatrix}
$$

Después se integra:

$$
C_i(x) = \int \frac{W_i}{W}\,dx
$$

**🔤 Diccionario:**
- $W_i$: Wronskiano modificado (columna $i$ cambiada por ceros y $g$).
- El $g(x)$ va **siempre en la última fila** de la columna sustituida.
- $C_i(x)$: se obtiene integrando; las constantes de integración se absorben en $y_h$ (§3 Caso 7).

### E. Orden 2: las dos fórmulas ya resueltas

Con $y'' + p(x)y' + q(x)y = g(x)$ e $y_1, y_2$ fundamentales:

$$
W = y_1y_2' - y_1'y_2
$$

$$
C_1' = \frac{\begin{vmatrix} 0 & y_2 \\ g & y_2' \end{vmatrix}}{W} = -\frac{y_2\,g(x)}{W}, \qquad C_2' = \frac{\begin{vmatrix} y_1 & 0 \\ y_1' & g \end{vmatrix}}{W} = \frac{y_1\,g(x)}{W}
$$

**🔤 Diccionario:** mismos símbolos que §2.B y §2.D; el signo menos del $C_1'$ viene del desarrollo del determinante $2\times2$.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

| Caso | Situación | Qué hacer | 👉 Ir a |
|---|---|---|---|
| **Caso 0** | $g(x) = 0$ | No aplicar variación de parámetros: solo $y_h$ | §2.A |
| **Caso 1** | $W = 0$ | Caso singular: no es conjunto fundamental, **recalcular** | §2.B |
| **Caso 2** | $g$ es admisible (polinomio, $e^{ax}$, seno, coseno) | Usar coeficientes indeterminados: **más rápido** | `261102_EDO_ORDEN_SUPERIOR` §2.E |
| **Caso 3** | La EDO no está normalizada | Dividir por el coeficiente principal antes de todo | §2.C |
| **Caso 4** | Orden $n$ | $n$ incógnitas $C_i'$ y $n$ ecuaciones; solo la última lleva $g$ | §2.C |
| **Caso 5** | Orden $\geq 3$ | Reducir el determinante por **cofactores** usando la fila con más ceros | §2.D |
| **Caso 6** | La integral no es elemental | Se deja **indicada**: la solución sigue siendo válida | §4.1 |
| **Caso 7** | Aparecen constantes al integrar | Se absorben en las $C_1, \ldots, C_n$ de $y_h$: no se duplican | §4.1 paso 6 |
| **Caso 8** | $g$ no admisible ($\tan$, $\sec$, $\ln$, $\frac{1}{x}$) | Es el único camino: variación de parámetros | §4.1 |

**Reglas de oro (bolsillo):**
1. **Variación de parámetros sirve para toda $g(x)$**; coeficientes indeterminados solo para las admisibles.
2. El Wronskiano **debe** ser distinto de cero: es la hipótesis del método.
3. Las primeras $n-1$ condiciones son **ceros**; solo la última fila lleva $g(x)$.
4. **No** se resuelve el sistema a mano: se aplica Cramer con el Wronskiano (recomendación del profesor).
5. Las $C_i(x)$ encontradas sustituyen a las constantes del **mismo** $y_h$; no se suman constantes nuevas.
6. Verificar siempre $y_p$ sustituyendo en la EDO.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Variación de parámetros (orden $n$)

1. **Normalizar** la EDO: dejar el coeficiente de $y^{(n)}$ igual a $1$.
2. **Resolver la homogénea** y escribir $y_h = C_1y_1 + \cdots + C_ny_n$ con $n$ soluciones fundamentales.
3. **Calcular el Wronskiano** $W$ de $\{y_1, \ldots, y_n\}$ y comprobar $W \neq 0$.
4. **Reemplazar** $C_i$ por $C_i(x)$ y plantear el sistema de §2.C (ceros arriba, $g$ en la última fila).
5. **Aplicar Cramer**: $C_i' = \frac{W_i}{W}$ con cada $W_i$ de §2.D.
6. **Integrar** cada $C_i'$ y **absorber** las constantes en las $C_i$ de $y_h$.
7. **Escribir** $y = y_h + y_p$ y verificar sustituyendo.

**Plantilla (ejemplo de clase, orden 2):** $y'' + y = \tan x$

1. Ya está normalizada: $g(x) = \tan x$; **no** es admisible ⇒ variación de parámetros.
2. Homogénea: $\lambda^{2} + 1 = 0 \Rightarrow \lambda = \pm i$ ⇒

$$
y_h = C_1\cos x + C_2\sin x, \qquad y_1 = \cos x,\quad y_2 = \sin x
$$

3. Wronskiano:

$$
W = \begin{vmatrix} \cos x & \sin x \\ -\sin x & \cos x \end{vmatrix} = \cos^{2}x + \sin^{2}x = 1 \neq 0 \;\checkmark
$$

4. Cambio de constantes: $y_p = C_1(x)\cos x + C_2(x)\sin x$.
5. Cramer:

$$
C_1' = \frac{\begin{vmatrix} 0 & \sin x \\ \tan x & \cos x \end{vmatrix}}{1} = -\sin x\,\tan x = -\frac{\sin^{2}x}{\cos x}
$$

$$
C_2' = \frac{\begin{vmatrix} \cos x & 0 \\ -\sin x & \tan x \end{vmatrix}}{1} = \cos x\,\tan x = \sin x
$$

6. Integrando:

$$
C_1(x) = \int\left(\cos x - \sec x\right)dx = \sin x - \ln\left\vert\sec x + \tan x\right\vert
$$

$$
C_2(x) = \int\sin x\,dx = -\cos x
$$

7. Particular y solución:

$$
y_p = \left(\sin x - \ln\left\vert\sec x + \tan x\right\vert\right)\cos x + \left(-\cos x\right)\sin x = -\cos x\,\ln\left\vert\sec x + \tan x\right\vert
$$

$$
y = C_1\cos x + C_2\sin x - \cos x\,\ln\left\vert\sec x + \tan x\right\vert
$$

**Comprobación de la integral de $C_1$:** $\dfrac{\sin^{2}x}{\cos x} = \dfrac{1-\cos^{2}x}{\cos x} = \sec x - \cos x$, y $\int\sec x\,dx = \ln\left\vert\sec x + \tan x\right\vert$.

### 4.2 Atajo de orden 2 y caso orden $\geq 3$

**Orden 2:** no hace falta plantear el sistema. Se usan directamente

$$
C_1' = -\frac{y_2\,g}{W}, \qquad C_2' = \frac{y_1\,g}{W}, \qquad C_i(x) = \int C_i'\,dx
$$

**Orden $3$ o $4$:**
1. Escribir el Wronskiano $n\times n$.
2. Formar cada $W_i$ cambiando la columna $i$ por ceros y $g$ al final.
3. **Reducir por cofactores** eligiendo la fila o columna con más ceros (la columna sustituida suele ser la mejor).
4. Aplicar $C_i' = \frac{W_i}{W}$ e integrar.

**Plantilla mínima (orden 3):** con $y_1, y_2, y_3$ conocidas y $g(x)$,

$$
C_1' = \frac{1}{W}\begin{vmatrix} 0 & y_2 & y_3 \\ 0 & y_2' & y_3' \\ g & y_2'' & y_3'' \end{vmatrix}, \quad
C_2' = \frac{1}{W}\begin{vmatrix} y_1 & 0 & y_3 \\ y_1' & 0 & y_3' \\ y_1'' & g & y_3'' \end{vmatrix}, \quad
C_3' = \frac{1}{W}\begin{vmatrix} y_1 & y_2 & 0 \\ y_1' & y_2' & 0 \\ y_1'' & y_2'' & g \end{vmatrix}
$$

Después se integra cada uno y se suma $y_p = C_1y_1 + C_2y_2 + C_3y_3$.

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
- [ ] ¿Se copió el espejo a `F:\NOTES\NOTAS DE CLASE\CEDO` con hash SHA256 idéntico?

---

**Cita rápida:** 📘 Cheatsheet `261026_VARIACION_PARAMETROS` — cita el bloque (`§2.D`, `§3 Caso 5`, `§4.2`…) al resolver.
