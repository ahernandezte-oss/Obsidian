# 📘 CHEATSHEET — CEDO · 24/10/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261024_ECUACION_EULER.md`
> - **Tema principal:** Ecuación de **Euler** (ecuación equidimensional, lineal con coeficientes variables)
> - **Fecha de clase:** 24/10/2026
> - **Fuente:** transcripción `Cedo 24` (clase del 24/10/2026) + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261024_ECUACION_EULER` §2.B»
> - **Complemento:** coeficientes **constantes** en `261102_EDO_ORDEN_SUPERIOR`; coeficientes variables **sin** simetría en `261104_OSTROGRADSKY_LIOUVILLE`.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Los coeficientes son constantes?**
- Sí (números) → **no** es esta ecuación → característica normal. 👉 §3 Caso 0 · `261102_EDO_ORDEN_SUPERIOR` §2.B
- No (aparecen $x$, $x^2$, $x^3$…) → Paso 1.

**Paso 1 — ¿La potencia de $x$ coincide con el orden de la derivada?** (la **simetría**)

| Término que aparece | Potencia de $x$ | Orden de la derivada |
|---|---|---|
| $x^{2}y''$ | $2$ | $2$ |
| $xy'$ | $1$ | $1$ |
| $y$ | $0$ | $0$ |

- **Coinciden todos** → **ecuación de Euler** (este tema). 👉 §2.A · §4.1
- **No coinciden** (por ejemplo $x^{2}y'' - 2xy' + 2y$ sí coincide, pero $(x^{2}+1)y'' - 2xy'$ no) → no es Euler → reducción de orden. 👉 `261104_OSTROGRADSKY_LIOUVILLE` §4.1

**Paso 2 — ¿Cómo se resuelve?**
- Sustituir $y = x^{\lambda}$ (**recomendado**). 👉 §2.B · §4.1
- O cambiar $x = e^{t}$ (transforma en coeficientes constantes, pero el profesor **no lo recomienda**). 👉 §2.C · §4.2

### Tabla de decisión

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| Coeficientes numéricos constantes | Característica (NO este tema) | $a_n\lambda^n + \cdots + a_0 = 0$ | §3 Caso 0 |
| $x^{n}y^{(n)} + \cdots + a_1xy' + a_0y = 0$ | **Euler** con $y = x^{\lambda}$ | $y^{(k)} = \lambda(\lambda-1)\cdots(\lambda-k+1)x^{\lambda-k}$ | §2.B · §4.1 |
| Ecuación de Euler de orden 2 | Caso según raíces | ver tabla de §2.D | §2.D |
| Raíces reales distintas | Caso 1 | $C_1x^{\lambda_1} + C_2x^{\lambda_2}$ | §3 Caso 1 |
| Raíz real repetida | Caso 2 (aparece $\ln x$) | $x^{\lambda}\left(C_1 + C_2\ln x\right)$ | §3 Caso 2 |
| Raíces complejas $\alpha\pm\beta i$ | Caso 3 | $x^{\alpha}\left[C_1\cos(\beta\ln x) + C_2\sin(\beta\ln x)\right]$ | §3 Caso 3 |
| Las potencias de $x$ **no** coinciden | No es Euler | — | §3 Caso 5 |
| Se pide el intervalo de validez | Dominio | $x > 0$ (por $\ln x$ y $x^{\lambda}$) | §3 Caso 4 |

### Frases literales del profesor (transcripción del 24/10)

- "Ecuación lineal pero coeficientes no constantes, pero **caso especial**. Miro, N, N, grados son iguales. N-1, N-1, **simetría**" → la potencia de $x$ iguala al orden de la derivada.
- "No es cómodo trabajar con exponente… **yo no recomiendo** usted utilizar este cambio. **Mejor polinómico**" → preferir $y = x^{\lambda}$ antes que $x = e^{t}$.
- "**Ecuación característica**, lo mismo para ecuación lineal con coeficientes constantes" → mismos tres casos, pero con potencias $x^{\lambda}$ en vez de exponenciales.
- "Si $M = 3$, usted tiene acá **logaritmo cuadrado**" → a mayor multiplicidad, más potencias de $\ln x$.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Forma general de la ecuación de Euler

**Condición de uso:** cada potencia de $x$ es igual al orden de la derivada que acompaña.

$$
a_n x^{n}y^{(n)} + a_{n-1}x^{n-1}y^{(n-1)} + \cdots + a_1 x y' + a_0 y = 0
$$

**🔤 Diccionario:**
- $a_n, \ldots, a_0$: constantes reales.
- $x^{n}, x^{n-1}, \ldots, x$: potencias cuyo exponente **coincide** con el orden de la derivada.
- $y^{(n)}$: derivada $n$-ésima.
- $n$: orden de la ecuación; número de constantes de la solución general.

### B. Sustitución recomendada: $y = x^{\lambda}$

$$
y = x^{\lambda}, \qquad y' = \lambda x^{\lambda-1}, \qquad y'' = \lambda\left(\lambda-1\right)x^{\lambda-2}
$$

$$
y^{(k)} = \lambda\left(\lambda-1\right)\left(\lambda-2\right)\cdots\left(\lambda-k+1\right)x^{\lambda-k}
$$

Al sustituir, **todos** los términos quedan con factor $x^{\lambda}$ y se cancela. Queda la **ecuación característica de Euler**:

$$
a_n\,\lambda\left(\lambda-1\right)\cdots\left(\lambda-n+1\right) + \cdots + a_2\,\lambda\left(\lambda-1\right) + a_1\lambda + a_0 = 0
$$

**Caso orden $2$ (el más frecuente):**

$$
a_2\,\lambda\left(\lambda-1\right) + a_1\lambda + a_0 = 0
$$

**🔤 Diccionario:**
- $\lambda$: exponente que se busca (el análogo de la raíz característica de coeficientes constantes).
- $x^{\lambda}$: forma propuesta de la solución.
- $\lambda(\lambda-1)(\lambda-2)\cdots$: producto descendente; para $y''$ es $\lambda(\lambda-1)$, para $y'''$ es $\lambda(\lambda-1)(\lambda-2)$.
- $x^{\lambda} \neq 0$ para $x > 0$, por eso se puede cancelar.

### C. Cambio alternativo: $x = e^{t}$, es decir $t = \ln x$

**Condición de uso:** misma ecuación de Euler; convierte una EDO de coeficientes variables en una de **coeficientes constantes**.

$$
x\,\frac{dy}{dx} = \frac{dy}{dt}
$$

$$
x^{2}\,\frac{d^{2}y}{dx^{2}} = \frac{d^{2}y}{dt^{2}} - \frac{dy}{dt}
$$

En general, el operador $x\frac{d}{dx}$ se convierte en $\frac{d}{dt}$.

**🔤 Diccionario:**
- $t = \ln x$: nueva variable independiente; exige $x > 0$.
- $\frac{dy}{dt}$, $\frac{d^{2}y}{dt^{2}}$: derivadas respecto de $t$.
- Vuelta al final: $t \rightarrow \ln x$.

⚠️ **El profesor no lo recomienda:** "no es cómodo trabajar con exponente… mejor polinómico". Se deja aquí como alternativa de comprobación.

### D. Las tres soluciones según las raíces (ecuación de Euler)

| Caso | Raíces de la característica | Solución |
|---|---|---|
| **1** | Reales y distintas $\lambda_1 \neq \lambda_2$ | $C_1x^{\lambda_1} + C_2x^{\lambda_2}$ |
| **2** | Real $\lambda$ con multiplicidad $k$ | $x^{\lambda}\Big[C_1 + C_2\ln x + C_3\left(\ln x\right)^{2} + \cdots + C_k\left(\ln x\right)^{k-1}\Big]$ |
| **3** | Complejas $\alpha \pm \beta i$ | $x^{\alpha}\Big[C_1\cos\left(\beta\ln x\right) + C_2\sin\left(\beta\ln x\right)\Big]$ |

**Comparación con coeficientes constantes:** es la misma tabla con dos sustituciones.

$$
e^{\lambda x} \;\longrightarrow\; x^{\lambda}, \qquad x \;\longrightarrow\; \ln x
$$

**🔤 Diccionario:**
- $\lambda_1, \lambda_2$: raíces de la ecuación característica de Euler.
- $\alpha, \beta$: parte real e imaginaria de la raíz compleja.
- $k$: multiplicidad de la raíz repetida; el paréntesis lleva potencias de $\ln x$ hasta $(\ln x)^{k-1}$.
- $\ln x$: sustituye a la $x$ que aparecía como factor en el caso repetido de coeficientes constantes.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

| Caso | Situación | Qué hacer | 👉 Ir a |
|---|---|---|---|
| **Caso 0** | Coeficientes constantes | No es Euler: característica normal | §1 Paso 0 |
| **Caso 1** | Raíces reales distintas | $C_1x^{\lambda_1} + C_2x^{\lambda_2}$ | §2.D |
| **Caso 2** | Raíz real repetida | Aparece $\ln x$ multiplicando a $x^{\lambda}$ | §2.D · §4.1 |
| **Caso 3** | Raíces complejas $\alpha \pm \beta i$ | $\ln x$ **dentro** del seno y del coseno | §2.D |
| **Caso 4** | Dominio | La solución vale para $x > 0$; con $x<0$ se usa $\vert x\vert$ | §2.B |
| **Caso 5** | Las potencias de $x$ no coinciden con los órdenes | No es Euler: no aplicar $x^{\lambda}$ | §1 Paso 1 |
| **Caso 6** | Orden $\geq 3$ | El producto descendente crece: $\lambda(\lambda-1)(\lambda-2)\cdots$ | §2.B |
| **Caso 7** | Multiplicidad $\geq 3$ | Aparecen $(\ln x)^{2}$, $(\ln x)^{3}$, … | §2.D |

**Reglas de oro (bolsillo):**
1. **Regla de simetría:** potencia de $x$ = orden de la derivada. Si falla un solo término, no es Euler.
2. La ecuación característica de Euler sale de **sustituir $x^{\lambda}$**, no de copiar los coeficientes.
3. **No** aparecen exponenciales en la solución: aparecen potencias $x^{\lambda}$.
4. El $\ln x$ es el "equivalente" del factor $x$ del caso repetido: raíz doble → $x^{\lambda}\left(C_1 + C_2\ln x\right)$.
5. Número de constantes = orden de la ecuación.
6. Para comprobar, se puede rehacer con $x = e^{t}$ (§2.C): debe dar lo mismo.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Euler por sustitución $y = x^{\lambda}$ (recomendado)

1. **Verificar la simetría** (§1, Paso 1).
2. **Proponer** $y = x^{\lambda}$ y escribir $y', y'', \ldots$ con la fórmula de §2.B.
3. **Sustituir** en la EDO y sacar factor común $x^{\lambda}$ (se cancela porque $x>0$).
4. **Igualar a cero** el corchete → ecuación característica de Euler.
5. **Resolver** la característica y clasificar en Caso 1, 2 o 3 (§2.D).
6. **Escribir** la solución con potencias $x^{\lambda}$ (no exponenciales).
7. **Contar** constantes e indicar el dominio $x > 0$.

**Plantilla (ejemplo de clase):** $x^{2}y'' - 4xy' + 6y = 0$

1. Simetría: $x^{2}$ con $y''$, $x$ con $y'$, $x^{0}$ con $y$ ✔ es Euler.
2. $y = x^{\lambda}$, $y' = \lambda x^{\lambda-1}$, $y'' = \lambda\left(\lambda-1\right)x^{\lambda-2}$.
3. Sustituyendo:

$$
\lambda\left(\lambda-1\right)x^{\lambda} - 4\lambda x^{\lambda} + 6x^{\lambda} = 0
$$

4. Sacando $x^{\lambda}$:

$$
\lambda^{2} - \lambda - 4\lambda + 6 = 0 \;\Rightarrow\; \lambda^{2} - 5\lambda + 6 = 0
$$

5. Discriminante $= 25 - 24 = 1$, raíces:

$$
\lambda = \frac{5 \pm 1}{2} \;\Rightarrow\; \lambda_1 = 3,\quad \lambda_2 = 2
$$

6. Caso 1, raíces reales distintas:

$$
y = C_1x^{3} + C_2x^{2}
$$

**Variantes del mismo algoritmo (cambia solo el paso 5):**

- **Raíz doble:** $x^{2}y'' - xy' + y = 0$ → $\lambda^{2} - 2\lambda + 1 = 0$ → $\left(\lambda-1\right)^{2} = 0$ → $\lambda = 1$ doble →

$$
y = \left(C_1 + C_2\ln x\right)x
$$

- **Raíces complejas:** $x^{2}y'' + xy' + y = 0$ → $\lambda^{2} + 1 = 0$ → $\lambda = \pm i$ → $\alpha = 0$, $\beta = 1$ →

$$
y = C_1\cos\left(\ln x\right) + C_2\sin\left(\ln x\right)
$$

### 4.2 Euler por cambio $x = e^{t}$ (alternativo, para comprobar)

1. **Verificar** que es Euler.
2. **Cambiar** $x = e^{t}$ y usar §2.C para reescribir $xy'$ y $x^{2}y''$.
3. **Resolver** la EDO resultante, que ya tiene **coeficientes constantes**.
4. **Volver** a $x$ sustituyendo $t = \ln x$ en todos los $t$ y $e^{t}$.
5. **Comprobar** que coincide con §4.1.

**Plantilla mínima:** $x^{2}y'' - xy' + y = 0$ con $x = e^{t}$

1. $xy' = \dot{y}$ y $x^{2}y'' = \ddot{y} - \dot{y}$.
2. La EDO queda $\ddot{y} - \dot{y} - \dot{y} + y = 0$, es decir $\ddot{y} - 2\dot{y} + y = 0$.
3. Característica $m^{2} - 2m + 1 = 0 \Rightarrow m = 1$ doble → $y = \left(A + Bt\right)e^{t}$.
4. Volviendo: $t = \ln x$ y $e^{t} = x$ →

$$
y = \left(A + B\ln x\right)x \; \checkmark
$$

**🔤 Diccionario:** $\dot{y}$: derivada respecto de $t$ · $m$: raíz característica de la EDO transformada (coeficientes constantes) · $A, B$: constantes.

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

## 📎 APÉNDICE ➕ — CONTEXTO DE CLASE: APLICACIÓN A SISMOS

> No es método de resolución. Se registra porque el profesor dedicó la última parte de la clase a este modelo, y sirve para reconocer de dónde salen las EDO no lineales del tema `261014_NO_LINEALES_ORDEN_SUPERIOR`.

**Ley de Gutenberg–Richter** (empírica, con más de 100 años de datos):

$$
\log_{10} N = A - B\,m
$$

**🔤 Diccionario:**
- $N$: número de sismos con magnitud en un intervalo fijo.
- $m$: magnitud del sismo.
- $A$: productividad sísmica de la región (constante empírica).
- $B$: relación entre sismos de gran magnitud y de magnitud menor (constante empírica).

**Clasificación por profundidad** (la que el profesor marcó como importante):

| Tipo | Profundidad |
|---|---|
| Superficial (*shallow*) | $< 30\ \mathrm{km}$ |
| Intermedio | $30$–$300\ \mathrm{km}$ |
| Profundo | $> 300\ \mathrm{km}$ |

**Puntos que el profesor señaló:**
- La teoría del rebote elástico solo funciona a poca profundidad; a más de $300\ \mathrm{km}$ la mecánica de fluidos **no** alcanza.
- Los procesos sismogénicos son **no lineales** (agrupamiento o *clustering*): no hay teoría general, y por eso se usan métodos de reducción como los del tema no lineal.
- Para riesgo sísmico se necesitan tiempos de emergencia muy cortos (del orden de segundos en edificios altos).

---

**Cita rápida:** 📘 Cheatsheet `261024_ECUACION_EULER` — cita el bloque (`§2.B`, `§3 Caso 2`, `§4.1`…) al resolver.
