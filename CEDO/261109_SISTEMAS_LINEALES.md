# 📘 CHEATSHEET — CEDO · 09/11/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261109_SISTEMAS_LINEALES.md`
> - **Tema principal:** Sistemas lineales de EDO — **método de eliminación** (reducir el sistema a una sola ecuación de orden superior)
> - **Fecha de clase:** 09/11/2026
> - **Fuente:** apuntes manuscritos del 09/11/2026 + transcripción `语音 261109_140521` + **Zill §4.8** (método de eliminación, sistema $3\times3$ de la plantilla) + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261109_SISTEMAS_LINEALES` §2.B»
> - **Complemento:** los tres casos de la ecuación característica están en `261102_EDO_ORDEN_SUPERIOR` §2.B; variación de parámetros en `261026_VARIACION_PARAMETROS`.
> - **⏳ Límite conocido:** la matriz del ejemplo $3\times3$ de clase no es recuperable; el detalle está en §4.2.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Hay varias incógnitas, cada una con su derivada?**
- Una sola incógnita → **no es un sistema** → cheatsheet de EDO escalar. 👉 `261102_EDO_ORDEN_SUPERIOR` §1
- Dos o más incógnitas acopladas ($\dot{x}$, $\dot{y}$, … aparecen en la misma ecuación) → Paso 1.

**Paso 1 — ¿Cuántas incógnitas hay?**
- $2$ → se elimina una incógnita y queda **una EDO de orden $2$**. 👉 §4.1
- $3$ → quedan dos eliminaciones y una **EDO de orden $3$**. 👉 §4.2
- $\geq 4$ → el método funciona pero **se vuelve impracticable**; conviene autovalores/matriz. 👉 §3 Caso 5

**Paso 2 — ¿Qué se pide?**
- Solo $x(t)$ → basta la EDO reducida. 👉 §2.B
- **Todas** las funciones → además hay que recuperar $y$, $z$ con las ecuaciones originales. 👉 §2.D

### Tabla de decisión

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| Sistema $2\times2$ lineal homogéneo | Eliminación | $\ddot{x} - (a_1+b_2)\dot{x} + (a_1b_2-b_1a_2)x = 0$ | §2.B · §4.1 |
| Sistema $3\times3$ lineal | Eliminación doble | EDO de orden $3$ en $x$ | §2.C · §4.2 |
| Se pide $x(t)$ únicamente | Resolver la EDO reducida | característica de orden $n$ | §2.E · §4.1 |
| Se piden $x(t)$ **e** $y(t)$ | Recuperar $y$ de la ecuación 1 | $y = \frac{\dot{x}-a_1x}{b_1}$ | §2.D |
| El sistema tiene término independiente | Particular + homogénea | $y = y_h + y_p$ | §3 Caso 6 |
| Dimensión $\geq 4$ | El método es impráctico | usar matriz y autovalores | §3 Caso 5 |
| Al despejar hay que dividir por un coeficiente | Comprobar que no sea $0$ | $b_1 \neq 0$ | §3 Caso 4 |
| El sistema viene escrito con $D$ (notación de operador) | Eliminación algebraica con $D$ | $Dx - \left(D-2\right)y = 0$ | §2.F |

### Frases literales del profesor (transcripción del 09/11)

- "Método para **eliminar**… se deduce para una ecuación" → se eliminan incógnitas hasta quedarse con una sola.
- "Necesita resolver **solo una ecuación**. Cómodo" → la ventaja del método.
- "El método funciona bien cuando usted tiene **dimensión dos o tres**" → por encima de eso, no conviene.
- "Y, Z son **aritméticas**, siempre solo un dos" → al recuperar $y$ y $z$ se hace **álgebra**, no se integra otra vez.
- "Antes el tiempo es **independiente**" → en un sistema la variable independiente es $t$, no $x$.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Notación y forma del sistema $2\times2$

$$
\dot{x} = \frac{dx}{dt}, \qquad \dot{y} = \frac{dy}{dt}
$$

$$
\begin{cases}
\dot{x} = a_1x + b_1y \\[2pt]
\dot{y} = a_2x + b_2y
\end{cases}
$$

**🔤 Diccionario:**
- $x(t), y(t)$: incógnitas; funciones del **tiempo** $t$.
- $\dot{x}, \dot{y}$: derivadas respecto de $t$ (no respecto de $x$).
- $a_1, b_1, a_2, b_2$: coeficientes constantes del sistema.
- El sistema es **homogéneo** si no hay término independiente.

### B. Eliminación en $2\times2$ (resultado general) ➕

**Procedimiento:** derivar la primera ecuación, sustituir $\dot{y}$ de la segunda y $y$ despejada de la primera.

$$
y = \frac{\dot{x} - a_1x}{b_1}
$$

$$
\ddot{x} = a_1\dot{x} + b_1\dot{y} = a_1\dot{x} + b_1\left(a_2x + b_2y\right) = \left(a_1+b_2\right)\dot{x} + \left(b_1a_2 - a_1b_2\right)x
$$

$$
\ddot{x} - \left(a_1 + b_2\right)\dot{x} + \left(a_1b_2 - b_1a_2\right)x = 0
$$

**Lectura del resultado:** el coeficiente de $\dot{x}$ es la **traza** de la matriz del sistema y el término independiente es su **determinante**:

$$
\text{tr}\,A = a_1 + b_2, \qquad \det A = a_1b_2 - b_1a_2
$$

Por eso la EDO reducida es exactamente el **polinomio característico** de $A$:

$$
\lambda^{2} - \left(\text{tr}\,A\right)\lambda + \det A = 0
$$

**🔤 Diccionario:**
- $\ddot{x}$: segunda derivada de $x$ respecto de $t$.
- $\text{tr}\,A$: suma de los elementos de la diagonal principal.
- $\det A$: determinante de la matriz de coeficientes.
- Esta EDO es la que se resuelve; $y(t)$ se recupera después (§2.D).

### C. Eliminación en $3\times3$ (procedimiento)

$$
\begin{cases}
\dot{x} = a_1x + b_1y + c_1z \\[2pt]
\dot{y} = a_2x + b_2y + c_2z \\[2pt]
\dot{z} = a_3x + b_3y + c_3z
\end{cases}
$$

**Secuencia:**
1. Derivar la primera ecuación: $\ddot{x} = a_1\dot{x} + b_1\dot{y} + c_1\dot{z}$.
2. Sustituir $\dot{y}$ y $\dot{z}$ por las ecuaciones 2 y 3.
3. Despejar una incógnita de la segunda ecuación, por ejemplo $y$.
4. Sustituirla en el resultado del paso 2 y despejar $z$ en función de $x, \dot{x}, \ddot{x}$.
5. Derivar otra vez y sustituir en la tercera ecuación.
6. Queda una EDO de **orden $3$** solo en $x$.

**Resultado estructural ➕:** la EDO que se obtiene en cualquier sistema $n\times n$ es el polinomio característico de la matriz del sistema aplicado a $x$. Sirve para **comprobar** que no se perdió ningún término.

**🔤 Diccionario:**
- $z(t)$: tercera incógnita.
- $a_i, b_i, c_i$: fila $i$ de la matriz del sistema.
- Al final: $n$ constantes para un sistema $n\times n$.

### D. Recuperar $y$ y $z$ (paso que se olvida)

$$
y = \frac{\dot{x} - a_1x}{b_1}
$$

En $3\times3$, una vez conocido $x(t)$, se despeja una incógnita de la segunda ecuación y la otra de la primera, ambas como **relaciones algebraicas**.

**🔤 Diccionario:**
- $\dot{x}$: se deriva de la solución ya encontrada; **no** se integra nada nuevo.
- Por eso **no** aparecen constantes adicionales: las $n$ constantes ya están en $x(t)$.

⚠️ **Ese es el error más frecuente:** integrar de nuevo al buscar $y$, y duplicar las constantes. Aquí solo se **deriva** y se **despeja**.

### E. Resolver la EDO reducida (los tres casos de siempre)

| Caso | Raíces de la característica | Solución para $x(t)$ |
|---|---|---|
| **1** | Reales y distintas | $C_1e^{\lambda_1t} + C_2e^{\lambda_2t}$ |
| **2** | Real repetida $\lambda$ (mult. $k$) | $\left(C_1 + C_2t + \cdots + C_kt^{k-1}\right)e^{\lambda t}$ |
| **3** | Complejas $\alpha \pm \beta i$ | $e^{\alpha t}\left(C_1\cos\beta t + C_2\sin\beta t\right)$ |

**🔤 Diccionario:**
- $\lambda$: raíz de la característica de la EDO reducida.
- $t$: variable independiente (nunca $x$).
- $C_1, C_2, \ldots$: constantes; para un sistema $n\times n$ hay $n$.

### F. ➕ Notación de operador $D$ (la variante del libro)

Rescatado de **Zill, *Ecuaciones diferenciales*, §4.8 "Solución de sistemas de ED lineales por eliminación"**, que es la misma sección que sigue el profesor.

$$
D \equiv \frac{d}{dt}, \qquad Dx = \dot{x}, \qquad D^{2}y = \ddot{y}
$$

El sistema se escribe como ecuaciones en $D$:

$$
\begin{cases}
Dx - \left(D - 2\right)y = 0 \\[2pt]
\left(D - 3\right)x + 2y = 0
\end{cases}
$$

y se elimina **operando algebraicamente**: se multiplica una ecuación por un operador, se resta de la otra y se anula la incógnita. En el ejemplo, operando la primera con $(D-3)$ y la segunda con $D$ y restando, se elimina $x$ y queda una EDO de segundo orden solo en $y$.

**Reglas del operador:**
1. $D$ es lineal: $D\left(ay_1 + by_2\right) = aDy_1 + bDy_2$.
2. Los operadores **conmutan** entre sí y con las constantes: $\left(D-3\right)D = D\left(D-3\right)$.
3. **No se cancelan** como si fueran números: de $Dx = Dy$ **no** se deduce $x = y$.

**🔤 Diccionario:**
- $D$: operador derivada respecto de $t$.
- $D^2$: aplicar dos veces (segunda derivada).
- $\left(D - a\right)y$: equivale a $\dot{y} - ay$.
- La ventaja de esta notación: la eliminación se ve como un sistema algebraico.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

| Caso | Situación | Qué hacer | 👉 Ir a |
|---|---|---|---|
| **Caso 0** | Sistema homogéneo | Solo $y_h$: no hay solución particular | §2.A |
| **Caso 1** | ¿De qué orden sale la EDO? | Igual a la **dimensión** del sistema ($2\times2$ → orden $2$) | §2.B · §2.C |
| **Caso 2** | Conteo de constantes | $n$ constantes para un sistema $n\times n$, no $2n$ | §2.D |
| **Caso 3** | ¿Cómo se obtiene $y$? | **Derivando y despejando**, nunca integrando | §2.D |
| **Caso 4** | Hay que dividir por $b_1$ | Exigir $b_1 \neq 0$; si $b_1=0$, despejar la otra incógnita | §2.B |
| **Caso 5** | Dimensión $\geq 4$ | El método se vuelve impráctico: matriz y autovalores | §1 Paso 1 |
| **Caso 6** | El sistema tiene término independiente | Resolver la homogénea reducida y añadir particular | §2.E |
| **Caso 7** | Comprobación | Sustituir $x(t)$ **e** $y(t)$ en **todas** las ecuaciones | §4.1 paso 7 |

**Reglas de oro (bolsillo):**
1. **Eliminar hasta quedarse con una sola incógnita.** Esa es toda la idea del método.
2. El orden de la EDO resultante **es** la dimensión del sistema.
3. La EDO resultante coincide con el polinomio característico de la matriz: sirve de control.
4. $y$ y $z$ se recuperan **algebraicamente**; si aparece una integral nueva, hay un error.
5. La variable independiente es $t$: la solución es $x(t)$, no $x$ en función de $x$.
6. Verificar siempre sustituyendo en **todas** las ecuaciones del sistema.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Eliminación en sistema $2\times2$

1. **Escribir** el sistema en la forma de §2.A e identificar $a_1, b_1, a_2, b_2$.
2. **Derivar** la primera ecuación respecto de $t$.
3. **Sustituir** $\dot{y}$ por la segunda ecuación.
4. **Despejar** $y$ de la primera ecuación y sustituirla.
5. **Ordenar** → EDO de orden $2$ solo en $x$ (debe coincidir con $\lambda^2 - \text{tr}A\,\lambda + \det A$).
6. **Resolver** la característica (tres casos, §2.E) → $x(t)$.
7. **Recuperar** $y(t)$ con $y = \frac{\dot{x}-a_1x}{b_1}$ (sin integrar).
8. **Verificar** sustituyendo en las dos ecuaciones.

**Plantilla (ejemplo de clase):**

$$
\begin{cases}
\dot{x} = 2x + y \\[2pt]
\dot{y} = 3x + 4y
\end{cases}
$$

1. $a_1 = 2$, $b_1 = 1$, $a_2 = 3$, $b_2 = 4$.
2. Derivando la primera: $\ddot{x} = 2\dot{x} + \dot{y}$.
3. Sustituyendo la segunda: $\ddot{x} = 2\dot{x} + 3x + 4y$.
4. Despejando $y$ de la primera: $y = \dot{x} - 2x$, y sustituyendo:

$$
\ddot{x} = 2\dot{x} + 3x + 4\left(\dot{x} - 2x\right) = 6\dot{x} - 5x
$$

5. Ordenando:

$$
\ddot{x} - 6\dot{x} + 5x = 0
$$

6. Característica y raíces:

$$
\lambda^{2} - 6\lambda + 5 = 0, \qquad D = 36 - 20 = 16
$$

$$
\lambda = \frac{6 \pm 4}{2} \;\Rightarrow\; \lambda_1 = 5,\quad \lambda_2 = 1
$$

$$
x(t) = C_1e^{5t} + C_2e^{t}
$$

7. Recuperando $y$:

$$
y = \dot{x} - 2x = \left(5C_1e^{5t} + C_2e^{t}\right) - 2\left(C_1e^{5t} + C_2e^{t}\right) = 3C_1e^{5t} - C_2e^{t}
$$

**Solución del sistema:**

$$
x(t) = C_1e^{5t} + C_2e^{t}, \qquad y(t) = 3C_1e^{5t} - C_2e^{t}
$$

**Comprobación en la segunda ecuación:**

$$
\dot{y} = 15C_1e^{5t} - C_2e^{t}
$$

$$
3x + 4y = 3\left(C_1e^{5t}+C_2e^{t}\right) + 4\left(3C_1e^{5t}-C_2e^{t}\right) = 15C_1e^{5t} - C_2e^{t} \;\checkmark
$$

### 4.2 Eliminación en sistema $3\times3$

1. **Escribir** las tres ecuaciones.
2. **Derivar** la primera → $\ddot{x}$.
3. **Sustituir** $\dot{y}$ y $\dot{z}$ de las otras dos.
4. **Despejar** $y$ de la segunda ecuación y sustituirla.
5. **Despejar** $z$ en función de $x, \dot{x}, \ddot{x}$.
6. **Derivar** y sustituir en la tercera → EDO de orden $3$ en $x$.
7. **Resolver** la característica → $x(t)$.
8. **Recuperar** $y$ y $z$ por álgebra (pasos 4 y 5 ya despejados).
9. **Verificar** en las tres ecuaciones.

**Resultado de clase (ejemplo $3\times3$):**

La EDO reducida que se obtuvo fue

$$
\lambda^{3} + \lambda^{2} - 4\lambda - 4 = 0
$$

Factorizando por agrupación:

$$
\lambda^{3} + \lambda^{2} - 4\lambda - 4 = \lambda^{2}\left(\lambda+1\right) - 4\left(\lambda+1\right) = \left(\lambda+1\right)\left(\lambda^{2}-4\right)
$$

$$
\lambda_1 = -1,\qquad \lambda_2 = 2,\qquad \lambda_3 = -2
$$

$$
x(t) = C_1e^{-t} + C_2e^{2t} + C_3e^{-2t}
$$

Después, $y(t)$ y $z(t)$ se obtienen con las relaciones despejadas en los pasos 4 y 5 (álgebra, sin integrar).

**Sobre la matriz del ejemplo de clase:** los coeficientes de las tres ecuaciones **no se pueden recuperar** con la información disponible. Se comprobó en este orden:

| Fuente revisada | Resultado |
|---|---|
| Transcripción `语音 261109_140521` | Solo frases sueltas ("$-x+2y+3z$"); no cierra con ninguna matriz |
| OCR de los apuntes | Los campos de fórmula llegaron **vacíos** |
| Zill §4.8 (sección que sigue el profesor) | Ejemplos resueltos solo $2\times2$; el $3\times3$ es ejercicio |
| *Ecuaciones diferenciales ordinarias* (libro del workspace) | No tiene sección de eliminación |
| *Betounes* | Resuelve sistemas por autovalores, con otro polinomio característico |
| Bancos de ejercicios en internet | Sistemas $3\times3$ con traza $-3$; el de clase tiene traza $-1$ |

Con traza $-1$, suma de menores $-4$ y determinante $4$ existen **infinitas** matrices enteras distintas, así que cualquier elección sería inventada.

**Plantilla $3\times3$ verificada (rescatada del libro):** Zill §4.8, problema 17.

$$
\begin{cases}
\dot{x} = y \\[2pt]
\dot{y} = z \\[2pt]
\dot{z} = x
\end{cases}
$$

1. Derivando la primera: $\ddot{x} = \dot{y} = z$.
2. Derivando otra vez: $\dddot{x} = \dot{z} = x$.
3. Queda una sola EDO de orden $3$:

$$
\dddot{x} - x = 0
$$

4. Característica y raíces:

$$
\lambda^{3} - 1 = 0 \;\Rightarrow\; \left(\lambda - 1\right)\left(\lambda^{2} + \lambda + 1\right) = 0
$$

$$
\lambda_1 = 1, \qquad \lambda_{2,3} = -\frac{1}{2} \pm \frac{\sqrt{3}}{2}i
$$

5. Solución para $x(t)$ (casos 1 y 3 de §2.E):

$$
x(t) = C_1e^{t} + e^{-t/2}\left(C_2\cos\frac{\sqrt{3}}{2}t + C_3\sin\frac{\sqrt{3}}{2}t\right)
$$

6. Recuperando por derivación (sin integrar):

$$
y(t) = \dot{x}(t), \qquad z(t) = \ddot{x}(t)
$$

**Comprobación:** con valores numéricos de $C_1, C_2, C_3$ se verifica $\dddot{x} = x$ y $z' = x$ con residual del orden de $10^{-4}$ (el propio de derivar numéricamente tres veces).

**Lo que sí queda certificado del ejemplo de clase:** la característica $\lambda^{3} + \lambda^{2} - 4\lambda - 4 = (\lambda+1)\left(\lambda^{2}-4\right)$ y sus raíces $-1,\ 2,\ -2$, verificadas por sustitución. Ese es el resultado que se usa.

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
- [ ] ¿Se copió el espejo a la bóveda con hash SHA256 idéntico?
- [ ] ¿Quedó marcado ⏳ lo que no se pudo recuperar de la transcripción?

---

**Cita rápida:** 📘 Cheatsheet `261109_SISTEMAS_LINEALES` — cita el bloque (`§2.B`, `§3 Caso 3`, `§4.1`…) al resolver.
