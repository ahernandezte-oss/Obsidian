# 📘 CHEATSHEET — CEDO · 02/11/2026

> **📇 Ficha del archivo**
> - **Archivo:** `EDO_ORDEN_SUPERIOR-021126.md`
> - **Tema principal:** EDO lineales de orden superior con coeficientes constantes — coeficientes indeterminados + variación de parámetros
> - **Fecha base:** 02/11/2026
> - **Fuente:** `Tarea1-2.Parcial-2.ED.pdf` (22 ejercicios) + teoría estándar de coeficientes constantes (Zill, Boyce–DiPrima)
> - **Cómo citarla al resolver:** «📘 Cheatsheet `EDO_ORDEN_SUPERIOR-021126` §2.E»
> - **Notación:** la raíz característica se denota **$\lambda$** (no $m$).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Es homogénea?**
- Si $g(x) = 0$ → **homogénea** → solo ecuación característica, no hay solución particular. 👉 §2.B, §4.1
- Si $g(x) \neq 0$ → **no homogénea** → sigue al Paso 1.

**Paso 1 — ¿Qué método para la parte particular?** Mira $g(x)$ (el lado derecho).

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| $g(x) = 0$ | Homogénea (solo característica) | $a_n\lambda^n + \cdots + a_1\lambda + a_0 = 0$ | §2.B · §4.1 |
| $g(x)$ es polinomio, $e^{ax}$, $\sin(ax)$, $\cos(ax)$, o producto/suma de estos | Coeficientes indeterminados | $y_p$ según la tabla de conjeturas | §2.E · §4.2 |
| $g(x)$ trae $\tan x$, $\sec x$, $\ln x$, $\sqrt{x}$, $\frac{1}{x}$ | Variación de parámetros | $u_i' = \frac{W_i}{W}$ | §2.F · §4.3 |
| El polinomio característico es de grado $\geq 3$ y no hay raíz evidente | Ruffini ➕ | división sintética por $(\lambda - r)$ | §2.C · §4.1 paso 2 |
| Una raíz $\lambda$ se repite $k$ veces | Raíz repetida (Caso 0) | $(C_1 + C_2x + \cdots + C_kx^{k-1})e^{\lambda x}$ | §2.B caso 2 · §3 Caso 0 |
| Aparecen $\alpha \pm \beta i$ | Complejas conjugadas (Caso 1) | $e^{\alpha x}(C_1\cos\beta x + C_2\sin\beta x)$ | §2.B caso 3 · §3 Caso 1 |
| La conjetura de $y_p$ ya aparece en $y_h$ | Choque (Caso 2) | multiplicar el bloque por $x$ | §2.E regla del conjunto · §3 Criterio del choque |
| Falta el término $y$ o alguna derivada | Factorizar $\lambda$ (Caso 4) | $\lambda = 0$ es raíz → aporta constante | §3 Caso 4 · §3 Criterio del choque |
| $g(x)$ trae un polinomio (por ejemplo $2x$) | Probar $\lambda_0 = 0$ | si $P(0) = 0$ hay choque → $x^m$ | §2.E columna $\lambda_0$ · §3 |
| $g(x)$ trae $\sin(bx)$ o $\cos(bx)$ | Seno y coseno **siempre juntos** (Caso 7) | $A\cos bx + B\sin bx$ | §2.E · §3 Caso 7 |

**Frases literales del profesor (para identificar el método):**
- "no tiene integrales, no tiene nada, la metodología muy fácil" → **coeficientes indeterminados**.
- "si tiene f(x) por tangente x, no podemos" → **variación de parámetros**.
- "si tiene sobre raíces, no podemos" → **variación de parámetros**.
- "variación de las constantes funciona para todos, no importa" → **variación de parámetros**.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Forma general y estructura de la solución

$$
a_n y^{(n)} + a_{n-1}y^{(n-1)} + \cdots + a_1y' + a_0y = g(x)
$$

$$
y = y_h + y_p, \qquad y_h = C_1y_1 + C_2y_2 + \cdots + C_ny_n
$$

**🔤 Diccionario:**
- $y,\ y',\ y^{(n)}$: función, primera derivada, $n$-ésima derivada.
- $a_n, \ldots, a_0$: coeficientes constantes (números).
- $g(x)$: término no homogéneo (lado derecho).
- $y_h$: solución homogénea (complementaria).
- $y_p$: solución particular.
- $y_1, \ldots, y_n$: soluciones fundamentales (linealmente independientes).
- $C_1, \ldots, C_n$: constantes arbitrarias; su número es igual al orden de la EDO.

### B. Solución homogénea — ecuación característica

$$
a_n\lambda^n + a_{n-1}\lambda^{n-1} + \cdots + a_1\lambda + a_0 = 0
$$

| Caso | Raíces de la característica | Solución homogénea $y_h$ |
|---|---|---|
| **1** | Reales y distintas $\lambda_1, \ldots, \lambda_n$ | $C_1e^{\lambda_1 x} + C_2e^{\lambda_2 x} + \cdots + C_ne^{\lambda_n x}$ |
| **2** | Real $\lambda$ con multiplicidad $k$ | $(C_1 + C_2x + \cdots + C_kx^{k-1})e^{\lambda x}$ |
| **3** | Complejas $\alpha \pm \beta i$ | $e^{\alpha x}(C_1\cos\beta x + C_2\sin\beta x)$ |

**Fórmula de Euler:**

$$
e^{(\alpha \pm \beta i)x} = e^{\alpha x}\left(\cos\beta x \pm i\sin\beta x\right)
$$

**🔤 Diccionario:**
- $\lambda$: raíz de la ecuación característica.
- $\alpha$: parte real de la raíz compleja.
- $\beta$: parte imaginaria de la raíz compleja.
- $k$: multiplicidad (cuántas veces se repite la raíz).
- $i$: unidad imaginaria ($i^2 = -1$).
- $e$: constante de Euler (≈ $2{,}71828$).

### C. ➕ Ruffini (división sintética) — para bajar el grado del polinomio

Sirve cuando ya se conoce una raíz $r$ y se quiere el cociente. Se divide $P(\lambda)$ entre $(\lambda - r)$.

**Pasos:**
1. Escribe los coeficientes de mayor a menor grado; rellena con $0$ los grados que falten.
2. A la izquierda pon $r$. Si divides por $\lambda + r$, usa $-r$.
3. Baja el primer coeficiente tal cual.
4. Multiplícalo por $r$, escríbelo bajo el siguiente coeficiente y **suma**. Repite.
5. El **último** número es el residuo $= P(r)$. Si es $0$, $r$ es raíz. Los demás son los coeficientes del **cociente** (un grado menos).

**Plantilla:** $P(\lambda) = \lambda^3 - 2\lambda^2 - 5\lambda + 6$ con $r = 1$.

| Fila | $\lambda^3$ | $\lambda^2$ | $\lambda^1$ | Término libre |
|---|---|---|---|---|
| Coeficientes de $P(\lambda)$ | $1$ | $-2$ | $-5$ | $6$ |
| $r = 1$ (multiplicar y sumar) | — | $1$ | $-1$ | $-6$ |
| **Resultado** | $\mathbf{1}$ | $\mathbf{-1}$ | $\mathbf{-6}$ | $\mathbf{0}$ (residuo) |

Cociente: $\lambda^2 - \lambda - 6 = (\lambda - 3)(\lambda + 2)$. Raíces: $\lambda = 1,\ 3,\ -2$.

**Qué probar:** divisores del término independiente ($\pm 1, \pm 2, \pm 3, \ldots$).

**🔤 Diccionario:** $r$: raíz que se prueba · $P(\lambda)$: polinomio característico · residuo: valor $P(r)$, debe dar $0$.

### D. Wronskiano (independencia lineal)

$$
W = \begin{vmatrix}
y_1 & y_2 & \cdots & y_n \\
y_1' & y_2' & \cdots & y_n' \\
\vdots & \vdots & \ddots & \vdots \\
y_1^{(n-1)} & y_2^{(n-1)} & \cdots & y_n^{(n-1)}
\end{vmatrix}
$$

- $W \neq 0$ → $\{y_1, \ldots, y_n\}$ es **conjunto fundamental** (linealmente independientes) ✔
- $W = 0$ → dependientes → **caso singular**, no sirven → recalcular.

**Caso $2\times 2$:**

$$
W = y_1y_2' - y_1'y_2
$$

**🔤 Diccionario:** $W$: determinante wronskiano · $y_i^{(j)}$: derivada $j$-ésima de $y_i$ · $\det$: determinante.

### E. Coeficientes indeterminados — familia, conjetura y número de choque

**Tabla única.** Para cada término de $g(x)$: su familia de derivadas, la conjetura de $y_p$ y el número $\lambda_0$ con el que se prueba el choque (§3).

| Término de $g(x)$ | Familia (conjunto de derivadas) | Conjetura $y_p$ | $\lambda_0$ de choque |
|---|---|---|---|
| $x^n$ (polinomio) | $\{x^n, x^{n-1}, \ldots, x, 1\}$ | $A_nx^n + \cdots + A_1x + A_0$ | $\mathbf{0}$ |
| $C e^{ax}$ | $\{e^{ax}\}$ | $A e^{ax}$ | $a$ |
| $C\cos(bx)$ o $C\sin(bx)$ | $\{\cos bx, \sin bx\}$ | $A\cos bx + B\sin bx$ | $bi$ |
| $C e^{ax}\cos(bx)$ o $C e^{ax}\sin(bx)$ | $\{e^{ax}\cos bx, e^{ax}\sin bx\}$ | $e^{ax}\left(A\cos bx + B\sin bx\right)$ | $a + bi$ |
| $x^ne^{ax}$ | $\{x^ne^{ax}, \ldots, x e^{ax}, e^{ax}\}$ | $\left(A_nx^n + \cdots + A_0\right)e^{ax}$ | $a$ |
| $x^n\cos(bx)$ o $x^n\sin(bx)$ | $\{x^n\cos bx, \ldots, \cos bx, \sin bx\}$ | $\left(A_nx^n + \cdots + A_0\right)\cos bx + \left(B_nx^n + \cdots + B_0\right)\sin bx$ | $bi$ |

**Reglas de combinación:** producto de términos → **multiplicar** conjeturas · suma de términos → **sumar** conjeturas.

**Pasos (regla del conjunto):**
1. Localiza cada término de $g(x)$ en la tabla y anota **su familia y su $\lambda_0$**.
2. Si dos términos comparten familia (por ejemplo $e^{3x}\cos x$ y $e^{3x}\sin x$), es **una sola conjetura**, no dos.
3. Prueba el choque con el $\lambda_0$ anotado → criterio en **§3 Criterio del choque**.
4. Si hay choque, multiplica **todo el bloque** por $x^m$ ($m$ = multiplicidad, §3).
5. $y_p$ = suma de las conjeturas, con coeficientes desconocidos.

**🔤 Diccionario:**
- $A, B, C, D, \ldots$: coeficientes desconocidos a determinar (NO son las constantes $C_1, C_2$ de $y_h$).
- $a$: el número que multiplica a $x$ **en el exponente** de $e^{ax}$.
- $b$: el número que multiplica a $x$ **dentro** de $\cos bx$ o $\sin bx$ (frecuencia).
- $n$: grado del polinomio.
- $\lambda_0$: el número complejo con el que se prueba el choque (no es una raíz; es un candidato).

### F. Variación de parámetros (Cramer + Wronskiano)

$$
y_p = u_1y_1 + u_2y_2 + \cdots + u_ny_n, \qquad u_i' = \frac{W_i}{W}
$$

- $W_i$: Wronskiano con la **columna $i$ reemplazada** por $(0, 0, \ldots, 0, g(x))^{T}$.
- **Antes de empezar:** dividir toda la ecuación por el coeficiente de la derivada mayor (dejar el término principal con coeficiente $1$).

**Caso 2.º orden** — con $y'' + p(x)y' + q(x)y = g(x)$ e $y_1, y_2$ fundamentales:

$$
W = y_1y_2' - y_1'y_2, \qquad u_1' = -\frac{y_2\,g(x)}{W}, \qquad u_2' = \frac{y_1\,g(x)}{W}
$$

**🔤 Diccionario:** $u_i$: funciones que reemplazan a las constantes · $W_i$: Wronskiano modificado · $g(x)$: lado derecho ya normalizado · $p(x), q(x)$: coeficientes tras dividir por el término principal.

### G. ➕ Fórmula de operador (evita re-derivar en cada ejercicio)

**Regla general (sirve para cualquier orden).** Sea $L$ el operador de la EDO y $P(\lambda)$ su polinomio característico. Para

$$
y = e^{ax}\left(A\cos bx + B\sin bx\right)
$$

se calcula el número complejo $K_1 + K_2\,i = P(a + bi)$ y entonces

$$
L[y] = e^{ax}\Big[\left(K_1A + K_2B\right)\cos bx + \left(K_1B - K_2A\right)\sin bx\Big]
$$

**Por qué funciona:** $D^{j}\left[e^{\mu x}\right] = \mu^{j}e^{\mu x}$, luego $L\left[e^{\mu x}\right] = P(\mu)e^{\mu x}$. Con $\mu = a+bi$ y tomando parte real sale la fórmula.

**Si hay choque** ($P(a+bi) = 0$) se usa la derivada del polinomio:

$$
L\left[x\,e^{ax}\left(C\cos bx + D\sin bx\right)\right] = e^{ax}\Big[\left(\Phi_1C + \Phi_2D\right)\cos bx + \left(\Phi_1D - \Phi_2C\right)\sin bx\Big],
\qquad \Phi_1 + \Phi_2\,i = P'(a+bi)
$$

**Generalización:** si $\lambda_0$ es raíz de multiplicidad $m$, entonces $L\left[x^me^{\lambda_0 x}\right] = P^{(m)}(\lambda_0)\,e^{\lambda_0 x}$. Esa es la razón por la que la corrección por $x^m$ de la tabla de multiplicidad de §3 funciona.

**Caso 2.º orden, explícito** — con $y'' + py' + qy = g(x)$:

$$
K_1 = a^2 - b^2 + pa + q, \qquad K_2 = 2ab + pb
$$

Derivadas sueltas del caso 2.º orden, si se necesitan:

$$
y' = e^{ax}\Big[\left(aA + bB\right)\cos bx + \left(aB - bA\right)\sin bx\Big]
$$

$$
y'' = e^{ax}\Big[\left((a^2-b^2)A + 2abB\right)\cos bx + \left((a^2-b^2)B - 2abA\right)\sin bx\Big]
$$

**Cómo se usa:** se calculan $K_1$ y $K_2$ **una sola vez** y el sistema de coeficientes sale directo, sin derivar término por término.

**Caso exponencial puro** ($b = 0$, $y_p = Ae^{ax}$): $K_1 = P(a)$, $K_2 = 0$ → $L[y_p] = K_1A\,e^{ax}$.

**🔤 Diccionario:**
- $a$: exponente de la exponencial (coeficiente de $x$ en $e^{ax}$).
- $b$: frecuencia (coeficiente de $x$ en $\cos bx$ y $\sin bx$).
- $p, q$: coeficientes constantes de $y'$ e $y$ en la EDO (con signo).
- $K_1, K_2$: parte real e imaginaria de $P(a+bi)$; son **números**, no las constantes $C_1, C_2$ de $y_h$.
- $\Phi_1, \Phi_2$: parte real e imaginaria de $P'(a+bi)$; se usan cuando hay choque.
- $P^{(m)}$: derivada $m$-ésima del polinomio característico respecto de $\lambda$.
- $A, B$: los coeficientes indeterminados que se despejan.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

| Caso | Situación | Qué hacer | 👉 Ir a |
|---|---|---|---|
| **Caso 0** | Raíz repetida con multiplicidad $k$ | Añadir $x, x^2, \ldots, x^{k-1}$ junto a $e^{\lambda x}$ | §2.B caso 2 |
| **Caso 1** | Raíz compleja $\alpha \pm \beta i$ | Siempre en pares conjugados → $e^{\alpha x}(\cos\beta x, \sin\beta x)$ | §2.B caso 3 |
| **Caso 2** | Choque: la conjetura coincide con $y_h$ | Multiplicar **todo el bloque** por $x$ (por $x^2$ si se repite) | §2.E |
| **Caso 3** | Wronskiano $= 0$ | Caso singular → no es conjunto fundamental → recalcular | §2.D |
| **Caso 4** | Falta el término $y$ o alguna derivada | Factorizar $\lambda$ → $\lambda = 0$ es raíz → aporta constante $C$ | §2.B |
| **Caso 5** | Wronskiano grande ($3\times3$, $4\times4$) | Reducir por **cofactores** por la fila o columna con más ceros | §2.D |
| **Caso 6** | Coeficiente principal $\neq 1$ | Normalizar antes de variación de parámetros | §2.F |
| **Caso 7** | $g(x)$ trae $\sin(bx)$ o $\cos(bx)$ | Escribir **siempre** $A\cos(bx) + B\sin(bx)$, nunca solo uno | §2.E |

**Reglas de oro (bolsillo):**
- El número de constantes de $y$ **debe** ser igual al orden de la EDO.
- Si $3 \pm i$ **no** es raíz de la característica, **no** hay choque con la familia $e^{3x}\cos x$, $e^{3x}\sin x$.
- En coeficientes indeterminados, si tras sustituir los términos con $x$ **no** se cancelan, la corrección por $x$ está mal puesta.
- Nunca borrar un coeficiente de la conjetura antes de sustituir, aunque "parezca" que da $0$: se resuelve y sale solo.

### Cómo se prueba el choque (criterio explícito) ➕

**Por qué se usa un número complejo:** $y_h$ contiene $e^{ax}\cos bx$ y $e^{ax}\sin bx$ **exactamente cuando** $a + bi$ y $a - bi$ son raíces de la ecuación característica. Por eso el choque se pregunta así: ¿es $a + bi$ raíz de $P(\lambda)$?

**Pasos:**
1. Toma el $\lambda_0$ del término en la **última columna de la tabla de §2.E** (polinomio → $0$; $e^{ax}$ → $a$; $\cos bx$ o $\sin bx$ → $bi$; $e^{ax}\cos bx$ → $a+bi$).
2. Evalúa el polinomio característico en ese punto: $P(\lambda_0)$.
3. Si $P(\lambda_0) \neq 0$ → **no hay choque**, la conjetura se deja como está.
4. Si $P(\lambda_0) = 0$ → **hay choque**; cuántas $x$ se multiplican se decide con la tabla de multiplicidad.

#### Multiplicidad: cuántas $x$ se multiplican

| $P(\lambda_0)$ | $P'(\lambda_0)$ | $P''(\lambda_0)$ | Corrección |
|---|---|---|---|
| $\neq 0$ | — | — | **ninguna** (sin choque) |
| $= 0$ | $\neq 0$ | — | multiplicar por $x$ |
| $= 0$ | $= 0$ | $\neq 0$ | multiplicar por $x^2$ |

**Regla general:** se deriva $P$ hasta el primer valor distinto de $0$. Si $P(\lambda_0) = \cdots = P^{(m-1)}(\lambda_0) = 0$ pero $P^{(m)}(\lambda_0) \neq 0$, la multiplicidad es $m$ → se multiplica por $x^m$ (§3 Caso 0).

#### Atajo para el caso polinómico ($\lambda_0 = 0$)

$P(0)$ es el término independiente del polinomio característico, y ese término es exactamente el coeficiente de $y$:

$$
P(0) = a_0
$$

De modo que $P(0) = 0$ equivale a que la EDO **no tenga término en $y$**; en ese caso la constante ya vive en $y_h$ y hay que subir a $x$.

⚠️ **No confundir:** $a$ (sin subíndice) es el exponente de $e^{ax}$; $a_0$ (con subíndice) es el coeficiente de $y$ en la EDO.

#### Ejemplo del cálculo completo

| Paso | Qué se hace | Con $g(x) = e^{3x}\cos x$ y $P(\lambda) = \lambda^2 - 8\lambda + 20$ |
|---|---|---|
| 1 | Tomar $\lambda_0$ de §2.E | término $e^{ax}\cos bx$ con $a = 3$, $b = 1$ → $\lambda_0 = 3 + i$ |
| 2 | Evaluar $P(\lambda_0)$ | $P(3+i) = (3+i)^2 - 8(3+i) + 20 = 4 - 2i$ |
| 3 | Decidir | $P(3+i) \neq 0$ → **no hay choque** → sin $x$ |

**Qué es $P(\lambda_0)$:** es el polinomio característico **evaluado** en $\lambda_0$. $P$ es una función de $\lambda$; al darle un valor devuelve un número. No es una fórmula nueva: es el mismo $P(\lambda)$ de la §2.B.

**Atajo del conjugado:** $P(3+i) \neq 0$ ya decide por los dos, porque con coeficientes reales $P(3-i) = \overline{P(3+i)} \neq 0$.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Algoritmo general (cualquier EDO lineal de coeficientes constantes)
1. **Identifica**: ¿homogénea o no homogénea? (§1, Paso 0).
2. **Ecuación característica** → raíces (usa Ruffini §2.C si el grado es $\geq 3$) → $y_h$ (§2.B, 3 casos).
3. **Particular**: elige el método (§1, Paso 1) → calcula $y_p$.
4. **Suma**: $y = y_h + y_p$.
5. **Verifica**: número de constantes $= n$ y $W \neq 0$.

### 4.2 Coeficientes indeterminados
1. Ecuación característica → raíces → escribe $y_h$.
2. Mira $g(x)$ → escribe la conjetura $y_p$ (§2.E, tabla + regla del conjunto).
3. **Verifica choque**: toma el $\lambda_0$ del término en la tabla de §2.E y evalúa $P(\lambda_0)$; si es $0$, mira la multiplicidad con $P'$ (§3) y multiplica el bloque por $x^m$.
4. Deriva $y_p$ las veces necesarias **y sustituye** en la EDO.
5. **Iguala coeficientes** término a término → sistema → resuelve.
6. $y = y_h + y_p$.
7. Verifica sustituyendo el resultado.

**Plantilla:** $y'' - 2y' - 3y = e^{4x}$
1. $\lambda^2 - 2\lambda - 3 = 0 \Rightarrow (\lambda - 3)(\lambda + 1) = 0 \Rightarrow \lambda = 3,\ -1$.
2. $y_h = C_1e^{3x} + C_2e^{-x}$.
3. $g(x) = e^{4x}$ → $y_p = Ae^{4x}$ (sin choque: $4 \neq 3,\ -1$).
4. $y_p' = 4Ae^{4x}$, $y_p'' = 16Ae^{4x}$ → $16A - 8A - 3A = 1 \Rightarrow 5A = 1 \Rightarrow A = \frac{1}{5}$.
5. $y = C_1e^{3x} + C_2e^{-x} + \frac{1}{5}e^{4x}$.

### 4.3 Variación de parámetros (2.º orden)
1. Ecuación característica → $y_h = C_1y_1 + C_2y_2$.
2. Normalizar: coeficiente de $y''$ igual a $1$ (§3 Caso 6).
3. $W = y_1y_2' - y_1'y_2$.
4. $u_1' = -\frac{y_2 g}{W}$, $u_2' = \frac{y_1 g}{W}$.
5. Integra: $u_1 = \int u_1'\,dx$, $u_2 = \int u_2'\,dx$.
6. $y_p = u_1y_1 + u_2y_2$ → $y = y_h + y_p$.
7. Verifica $W \neq 0$ y el número de constantes.

**Plantilla:** $y'' + y = \tan x$
1. $\lambda^2 + 1 = 0 \Rightarrow \lambda = \pm i \Rightarrow y_h = C_1\cos x + C_2\sin x$.
2. $y_1 = \cos x$, $y_2 = \sin x$, $W = \cos^2x + \sin^2x = 1$.
3. $u_1' = -\sin x\tan x = -\frac{\sin^2x}{\cos x}$, $u_2' = \cos x\tan x = \sin x$.
4. $u_1 = \sin x - \ln\left\vert\sec x + \tan x\right\vert$, $u_2 = -\cos x$.
5. $y = C_1\cos x + C_2\sin x - \cos x\ln\left\vert\sec x + \tan x\right\vert$.

### 4.4 ➕ Variación de parámetros (orden $n$)
1. $y_h = C_1y_1 + \cdots + C_ny_n$ (§2.B).
2. Normalizar el coeficiente del término de mayor orden.
3. Construye $W$ ($n \times n$) y cada $W_i$ (columna $i$ cambiada por $(0, \ldots, 0, g)^T$).
4. $u_i' = \frac{W_i}{W}$ → integra cada $u_i$.
5. $y_p = \sum_{i=1}^{n} u_iy_i$ → $y = y_h + y_p$.
6. Verifica $W \neq 0$.

**Plantilla:** $y''' - y'' - y' + y = g(x)$ con $y_h = C_1e^{x} + C_2xe^{x} + C_3e^{-x}$
1. $y_1 = e^x$, $y_2 = xe^x$, $y_3 = e^{-x}$.
2. Calcular $W$ ($3\times3$) por cofactores (§3 Caso 5).
3. $u_i' = \frac{W_i}{W}$ → integrar.
4. $y_p = u_1e^x + u_2xe^x + u_3e^{-x}$.

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿El archivo se llama `TEMA_PRINCIPAL-DDMMAA.md`, con la fecha correcta y sin el nombre de la materia como prefijo?
- [ ] ¿El título lleva la **ficha del archivo** (nombre, tema, fecha, fuente, cómo citarla)?
- [ ] ¿Están las **5 secciones en orden** y con sus emojis-marcador?
- [ ] ¿La tabla del **Radar tiene 4 columnas** y la columna "👉 Ir a" apunta a un bloque real en todas las filas?
- [ ] ¿Cada fórmula tiene su **diccionario justo debajo**?
- [ ] ¿Toda la matemática usa `$...$` en línea y `$$...$$` en bloque, sin `\( \)` y sin bloques de código?
- [ ] ¿En las tablas se usó `\frac` (no `\dfrac`) y `\mid`/`\vert` (no el carácter de barra vertical)?
- [ ] ¿Hay **una plantilla mínima por algoritmo** y ningún ejemplo decorativo?
- [ ] ¿Está marcado con **➕** todo lo que se añadió y no venía de la fuente?
- [ ] ¿Se copió la versión espejo a `F:\NOTES\NOTAS DE CLASE\CEDO` con **hash SHA256** idéntico?

---

**Cita rápida:** 📘 Cheatsheet `EDO_ORDEN_SUPERIOR-021126` — usa el bloque (`§2.B`, `§3 Caso 2`, `§4.2`…) al resolver cada ejercicio.
