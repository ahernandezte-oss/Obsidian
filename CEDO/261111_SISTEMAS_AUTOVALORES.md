# 📘 CHEATSHEET — CEDO · 11/11/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261111_SISTEMAS_AUTOVALORES.md`
> - **Tema principal:** Sistemas lineales de EDO resueltos por **autovalores y autovectores** (forma matricial)
> - **Fecha de clase:** 11/11/2026
> - **Fuente:** apuntes manuscritos del 11/11/2026 + transcripción `语音 261111_141502` + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261111_SISTEMAS_AUTOVALORES` §2.D»
> - **Método hermano:** el mismo sistema se puede resolver por **eliminación** (`261109_SISTEMAS_LINEALES`). El ejemplo 2×2 de esta clase es **el mismo** de aquella.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Es un sistema de varias EDO acopladas?**
- No → EDO escalar. 👉 `261102_EDO_ORDEN_SUPERIOR` §1
- Sí → Paso 1.

**Paso 1 — ¿Qué método?** (los dos sirven; el profesor da ambos)

| Situación | Método | Ventaja | 👉 Ir a |
|---|---|---|---|
| Se piden **solo** las funciones y el sistema es $2\times2$ o $3\times3$ | **Autovalores** (matricial) | Más rápido y ordenado | §4.1 |
| Conviene despejar una incógnita o hay coeficientes variables | **Eliminación** | Reduce a una EDO de orden $n$ | `261109_SISTEMAS_LINEALES` §4.1 |

**Paso 2 — ¿Qué tipo de autovalores salen?**
- **Reales y distintos** → es el **único caso que el profesor explicó**. 👉 §2.D · §4.1
- Repetidos o complejos → no se dictaron en clase. ➕ §2.F

### Tabla de decisión

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| Sistema lineal homogéneo de coeficientes constantes | Forma matricial | $\vec\gamma' = A\vec\gamma$ | §2.A · §2.B |
| Se pide la solución como **vector** | Autovalores | $\vec\gamma = \vec\gamma_0e^{\lambda t}$ | §2.C |
| Autovalores reales distintos | Caso 1 (dictado) | $\sum_i C_i\vec v_i e^{\lambda_i t}$ | §2.D · §4.1 |
| Sistema $2\times2$ | Determinante $2\times2$ | $\lambda^2 - \left(\text{tr}A\right)\lambda + \det A = 0$ | §4.1 |
| Sistema $3\times3$ | Determinante $3\times3$ | reducir por cofactores | §4.2 |
| Autovalores repetidos o complejos | ➕ no dictado en clase | ver §2.F | §2.F |
| Ya se resolvió por eliminación | Comprobar equivalencia | mismas $\lambda$ | §4.1 |

### Frases literales del profesor (transcripción del 11/11)

- "Cada sistema podemos presentar de **forma vectorial**… más fácil trabajar, más rápido".
- "Lambda es **autovalor**, gamma es **autovector**" → en una EDO escalar solo hay $\lambda$; en un sistema hay $\lambda$ **y** vector.
- "**Escribí la solución** [la forma general] **y después** ya… buscamos los autovectores" → orden recomendado.
- "Mi recomendación: presentar en forma **por componentes**. No necesita Cramer, no necesita Gauss… solo perder tiempo".
- "Yo explico **solo el primer caso**, raíces reales distintas. No dije para multiplicidad, no dije para complejo".
- "Si $\alpha_1 = 1$, $\alpha_2 = 3$… **mínimo siempre entero**, si puede".

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Forma matricial del sistema

$$
\frac{d\vec\gamma}{dt} = A\,\vec\gamma, \qquad \vec\gamma(t) = \begin{pmatrix} \gamma_1(t) \\ \gamma_2(t) \\ \vdots \\ \gamma_n(t) \end{pmatrix}, \qquad A = \begin{pmatrix} a_{11} & \cdots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{n1} & \cdots & a_{nn} \end{pmatrix}
$$

Escrito por componentes:

$$
\gamma_i' = \sum_{j=1}^{n} a_{ij}\,\gamma_j, \qquad i = 1, \ldots, n
$$

**🔤 Diccionario:**
- $\vec\gamma(t)$: vector solución; cada componente es una función del **tiempo** $t$.
- $A$: matriz de coeficientes constantes.
- $a_{ij}$: fila $i$, columna $j$ de $A$.
- $\gamma_i'$: derivada respecto de $t$ (nunca respecto de $\gamma$).

### B. Problema de autovalores

Se propone una solución exponencial con forma de vector:

$$
\vec\gamma = \vec\gamma_0\,e^{\lambda t}
$$

Al sustituir en $A\vec\gamma = \vec\gamma'$:

$$
A\,\vec\gamma_0\,e^{\lambda t} = \lambda\,\vec\gamma_0\,e^{\lambda t}
$$

y como $e^{\lambda t} \neq 0$ se cancela:

$$
A\,\vec\gamma_0 = \lambda\,\vec\gamma_0
$$

$$
\left(A - \lambda I\right)\vec\gamma_0 = \vec 0
$$

**🔤 Diccionario:**
- $\vec\gamma_0$: vector constante (el autovector).
- $\lambda$: autovalor.
- $I$: matriz identidad del mismo tamaño que $A$.
- $\left(A - \lambda I\right)$: se resta $\lambda$ **solo a la diagonal**.
- Para que exista $\vec\gamma_0 \neq \vec 0$ el sistema tiene que ser singular → §2.C.

### C. Ecuación característica

$$
\det\left(A - \lambda I\right) = 0
$$

**Caso $2\times2$** (forma rápida):

$$
\lambda^{2} - \left(\text{tr}\,A\right)\lambda + \det A = 0
$$

**🔤 Diccionario:**
- $\det$: determinante.
- $\text{tr}\,A = a_{11} + a_{22}$: traza (suma de la diagonal).
- Las raíces de esta ecuación son los **autovalores**; son las mismas que salen por el método de eliminación.

### D. Solución general — caso 1: autovalores reales y distintos (el dictado)

$$
\vec\gamma(t) = C_1\vec\alpha\,e^{\lambda_1 t} + C_2\vec\beta\,e^{\lambda_2 t} + \cdots + C_n\vec\delta\,e^{\lambda_n t}
$$

Escrito por componentes en $2\times2$:

$$
\vec\gamma(t) = C_1\begin{pmatrix}\alpha_1\\ \alpha_2\end{pmatrix}e^{\lambda_1 t} + C_2\begin{pmatrix}\beta_1\\ \beta_2\end{pmatrix}e^{\lambda_2 t}
$$

**🔤 Diccionario:**
- $\lambda_1, \ldots, \lambda_n$: autovalores, raíces de §2.C.
- $\vec\alpha, \vec\beta, \ldots, \vec\delta$: autovectores, uno por autovalor.
- $\alpha_1, \alpha_2$: componentes del autovector $\vec\alpha$ (no son constantes de integración).
- $C_1, C_2, \ldots$: constantes arbitrarias; su número es la dimensión del sistema.

### E. Cómo se calcula el autovector (por componentes)

Para cada $\lambda_i$ se resuelve $\left(A - \lambda_i I\right)\vec v = \vec 0$ escribiendo **una ecuación por fila**:

$$
\begin{cases}
\left(a_{11} - \lambda_i\right)\alpha_1 + a_{12}\alpha_2 + \cdots = 0 \\
a_{21}\alpha_1 + \left(a_{22} - \lambda_i\right)\alpha_2 + \cdots = 0 \\
\quad\vdots
\end{cases}
$$

**Reglas prácticas:**
1. Las filas suelen ser **proporcionales**: basta usar una o dos.
2. Se elige un valor cómodo para una componente y se despeja el resto.
3. **Normalizar a enteros**, y si se puede, al más pequeño.
4. El autovector está determinado **salvo constante**: $\vec v$ y $k\vec v$ son válidos.

**🔤 Diccionario:**
- $\alpha_1, \alpha_2, \ldots$: componentes del autovector para el autovalor $\lambda_1$.
- "Salvo constante": el vector se puede multiplicar por cualquier número $\neq 0$.

### F. ➕ Casos no dictados (para consulta)

| Caso | Autovalores | Solución |
|---|---|---|
| **2** | Real $\lambda$ repetido, con un solo autovector $\vec v$ | $\vec\gamma = \left(C_1 + C_2t\right)\vec v\,e^{\lambda t} + C_2\vec w\,e^{\lambda t}$ |
| **3** | Complejos $\alpha \pm \beta i$, autovector $\vec u \pm i\vec w$ | $\vec\gamma = e^{\alpha t}\left[C_1\left(\vec u\cos\beta t - \vec w\sin\beta t\right) + C_2\left(\vec u\sin\beta t + \vec w\cos\beta t\right)\right]$ |

**🔤 Diccionario:** $\vec w$: autovector generalizado (caso 2), o parte imaginaria del autovector (caso 3) · el resto igual que en §2.D.

⚠️ El profesor advirtió que **solo el caso 1** fue desarrollado en clase.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

| Caso | Situación | Qué hacer | 👉 Ir a |
|---|---|---|---|
| **Caso 0** | Sistema homogéneo | No hay solución particular | §2.A |
| **Caso 1** | Autovalores reales y distintos | Es el caso dictado: $\sum C_i\vec v_ie^{\lambda_it}$ | §2.D |
| **Caso 2** | Filas proporcionales al buscar el autovector | Es normal: usar solo una ecuación | §2.E |
| **Caso 3** | El autovector sale con fracciones | Multiplicar todo el vector por el denominador | §2.E |
| **Caso 4** | Se pide comprobar | Sustituir en $\vec\gamma' = A\vec\gamma$ | §4.1 paso 7 |
| **Caso 5** | Autovalores repetidos o complejos | Caso no dictado: ver §2.F | §2.F |
| **Caso 6** | El sistema es $4\times4$ o mayor | El determinante crece: reducir por cofactores | §4.2 |
| **Caso 7** | Coincide con un sistema ya resuelto por eliminación | Los $\lambda$ deben ser idénticos: sirve de control | §4.1 |

**Reglas de oro (bolsillo):**
1. **$\lambda$ sale del determinante**; el **autovector sale de $\left(A-\lambda I\right)\vec v = \vec 0$**. Son dos cálculos distintos.
2. Escribe la **forma general antes** de calcular (recomendación del profesor): así sabes cuántos vectores necesitas.
3. El número de autovectores **es igual a la dimensión** del sistema (en el caso 1).
4. Los autovalores **no cambian** según el método: son los de la matriz. Si por eliminación salieron otros, hubo error.
5. El autovector se puede escalar: $\left(1,3\right)$ y $\left(3,9\right)$ son el mismo. Se prefiere el de enteros más pequeños.
6. No hace falta Cramer ni Gauss: se resuelve **por componentes**.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Sistema $2\times2$ por autovalores

1. **Escribir** $A$ y el sistema $\vec\gamma' = A\vec\gamma$.
2. **Escribir la forma general** de la solución (§2.D) con las incógnitas $\lambda$ y los vectores.
3. **Ecuación característica** $\det\left(A-\lambda I\right)=0$ y hallar las raíces.
4. **Verificar** que son reales y distintas (caso 1).
5. Para cada $\lambda_i$: **resolver** $\left(A-\lambda_iI\right)\vec v = \vec 0$ por componentes.
6. **Normalizar** cada autovector a enteros pequeños.
7. **Armar** la solución y **verificar** sustituyendo en el sistema.

**Plantilla (ejemplo de clase):**

$$
A = \begin{pmatrix} 2 & 1 \\ 3 & 4 \end{pmatrix}, \qquad
\begin{cases}
\gamma_1' = 2\gamma_1 + \gamma_2 \\
\gamma_2' = 3\gamma_1 + 4\gamma_2
\end{cases}
$$

1. Forma general:

$$
\vec\gamma = C_1\begin{pmatrix}\alpha_1\\ \alpha_2\end{pmatrix}e^{\lambda_1 t} + C_2\begin{pmatrix}\beta_1\\ \beta_2\end{pmatrix}e^{\lambda_2 t}
$$

2. Ecuación característica:

$$
\det\begin{pmatrix} 2-\lambda & 1 \\ 3 & 4-\lambda \end{pmatrix} = \left(2-\lambda\right)\left(4-\lambda\right) - 3 = 0
$$

$$
= 8 - 6\lambda + \lambda^{2} - 3 = \lambda^{2} - 6\lambda + 5 = 0
$$

3. Raíces:

$$
\lambda = \frac{6 \pm \sqrt{36 - 20}}{2} = \frac{6 \pm 4}{2} \;\Rightarrow\; \lambda_1 = 5,\quad \lambda_2 = 1
$$

4. Autovector para $\lambda_1 = 5$:

$$
A - 5I = \begin{pmatrix} -3 & 1 \\ 3 & -1 \end{pmatrix}
$$

$$
-3\alpha_1 + \alpha_2 = 0 \;\Rightarrow\; \alpha_2 = 3\alpha_1
$$

Con $\alpha_1 = 1$: $\vec\alpha = \begin{pmatrix}1\\3\end{pmatrix}$.

5. Autovector para $\lambda_2 = 1$:

$$
A - I = \begin{pmatrix} 1 & 1 \\ 3 & 3 \end{pmatrix}
$$

$$
\beta_1 + \beta_2 = 0 \;\Rightarrow\; \beta_2 = -\beta_1
$$

Con $\beta_1 = 1$: $\vec\beta = \begin{pmatrix}1\\-1\end{pmatrix}$.

6. Solución general:

$$
\vec\gamma(t) = C_1\begin{pmatrix}1\\3\end{pmatrix}e^{5t} + C_2\begin{pmatrix}1\\-1\end{pmatrix}e^{t}
$$

7. **Verificación** en la segunda ecuación, con $\gamma_1 = C_1e^{5t}+C_2e^{t}$ y $\gamma_2 = 3C_1e^{5t}-C_2e^{t}$:

$$
\gamma_2' = 15C_1e^{5t} - C_2e^{t}
$$

$$
3\gamma_1 + 4\gamma_2 = 3\left(C_1e^{5t}+C_2e^{t}\right) + 4\left(3C_1e^{5t}-C_2e^{t}\right) = 15C_1e^{5t} - C_2e^{t} \;\checkmark
$$

🧩 **Coincidencia con el método de eliminación:** en `261109_SISTEMAS_LINEALES` §4.1 el mismo sistema dio $x = C_1e^{5t}+C_2e^t$, $y = 3C_1e^{5t}-C_2e^t$ y $\lambda^2-6\lambda+5=0$. **Los autovalores son los mismos por los dos caminos**: es el mejor control de que ambos métodos están bien.

### 4.2 Sistema $3\times3$ por autovalores

1. **Escribir** $A$ ($3\times3$) y la forma general con tres vectores.
2. **Ecuación característica**: $\det\left(A-\lambda I\right) = 0$, desarrollando el determinante por cofactores.
3. **Hallar las tres raíces** (Ruffini o factorización; 👉 `261102_EDO_ORDEN_SUPERIOR` §2.C).
4. Para **cada** $\lambda_i$: plantear $\left(A-\lambda_iI\right)\vec v = \vec 0$.
5. **Resolver por componentes**: con tres incógnitas suelen bastar dos ecuaciones; las demás son proporcionales.
6. **Normalizar** y armar la solución.
7. **Verificar** sustituyendo en las tres ecuaciones.

**Resultado de clase (ejemplo $3\times3$):**

La ecuación característica dio tres raíces **reales y distintas**:

$$
\lambda_1 = -1, \qquad \lambda_2 = 1, \qquad \lambda_3 = 2
$$

Forma de la solución general:

$$
\vec\gamma(t) = C_1\begin{pmatrix}\alpha_1\\ \alpha_2\\ \alpha_3\end{pmatrix}e^{-t} + C_2\begin{pmatrix}\beta_1\\ \beta_2\\ \beta_3\end{pmatrix}e^{t} + C_3\begin{pmatrix}\delta_1\\ \delta_2\\ \delta_3\end{pmatrix}e^{2t}
$$

**Control de consistencia:** con estas raíces, la matriz debe cumplir

$$
\text{tr}\,A = \lambda_1+\lambda_2+\lambda_3 = 2, \qquad \det A = \lambda_1\lambda_2\lambda_3 = -2
$$

y su polinomio característico es $\lambda^{3} - 2\lambda^{2} - \lambda + 2$.

**Autovectores:** se calculan con el mismo procedimiento del §4.1 (resolver $\left(A-\lambda_iI\right)\vec v = \vec 0$ por componentes y normalizar a enteros).

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
- [ ] ¿Se copió el espejo a la bóveda y se hizo **commit + push** con hash verificado?
- [ ] ¿Quedó marcado ⏳ lo que no se pudo recuperar?

---

**Cita rápida:** 📘 Cheatsheet `261111_SISTEMAS_AUTOVALORES` — cita el bloque (`§2.D`, `§3 Caso 5`, `§4.1`…) al resolver.
