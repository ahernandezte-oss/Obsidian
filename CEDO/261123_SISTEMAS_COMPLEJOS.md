# 📘 CHEATSHEET — CEDO · 23/11/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261123_SISTEMAS_COMPLEJOS.md`
> - **Tema principal:** Sistemas lineales homogéneos con **autovalores complejos** ($\alpha \pm \beta i$)
> - **Fecha de clase:** 23/11/2026
> - **Fuente:** apuntes manuscritos del 23/11/2026 + transcripciones `语音 261123_141137` y `语音 261123_143459` + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261123_SISTEMAS_COMPLEJOS` §2.C»
> - **Métodos hermanos:** `261111_SISTEMAS_AUTOVALORES` (reales distintos) · `261109_SISTEMAS_LINEALES` (eliminación)
> - **Ruta del curso (según el profesor):** sistemas **no homogéneos** (teorema de Fredholm) → forma no canónica → transformada de Laplace · **parcial: miércoles 9 de diciembre**

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Es un sistema de EDO lineales de coeficientes constantes?**
- No → EDO escalar (👉 `261102_EDO_ORDEN_SUPERIOR` §1) o sistema no lineal.
- Sí → Paso 1.

**Paso 1 — ¿El sistema es homogéneo?**
- Sí, $\dot{\vec x} = A\vec x$ → Paso 2.
- No, hay un término $\vec b(t)$ → ➕ teorema de Fredholm / variación de parámetros. 👉 §2.E

**Paso 2 — Resuelve la característica y mira el discriminante.**

| Discriminante | Autovalores | Qué hacer | 👉 Ir a |
|---|---|---|---|
| $> 0$ | reales distintos | caso dictado el 11/11 | `261111` §4.1 |
| $= 0$ | reales repetidos | ➕ aún no dictado (autovector generalizado) | §3 Caso 3 |
| $< 0$ | **complejos $\alpha \pm \beta i$** | **esta cheatsheet** | §3 Caso 1 |
| mezcla | reales + complejos | superposición | §3 Caso 2 |

### Tabla de decisión

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| $\dot{\vec x} = A\vec x$ con $A$ numérica | autovalores | $\det\left(A-\lambda I\right) = 0$ | §2.A · §4.1 |
| el discriminante sale negativo | par conjugado | $\lambda = \alpha \pm \beta i$ | §2.A |
| hay que construir el autovector | sistema homogéneo complejo | $\left(A-\lambda I\right)\vec v = \vec 0$ | §4.1 |
| aparece $e^{\left(\alpha+\beta i\right)t}$ | **fórmula de Euler** | $e^{\alpha t}\left(\cos \beta t + i\sin \beta t\right)$ | §2.B |
| se pide la **solución real** | parte real + parte imaginaria | $\vec x = C_1\operatorname{Re} + C_2\operatorname{Im}$ | §2.C · §4.2 |
| hay $\lambda$ reales **y** complejos | superposición | suma de las dos familias | §3 Caso 2 |
| el sistema es **no homogéneo** | compatibilidad | ➕ §2.E | §2.E |

### Frases literales del profesor (23/11)

- "Caso complejo: **trabajamos solo con la raíz positiva**" → no se resuelve dos veces; el conjugado no aporta información nueva.
- "Solo con raíz $3+2i$ siempre."
- "Las fórmulas sí complejas, pero la **solución es real**."
- "**Mínimo siempre entero**" → al elegir el parámetro del autovector, tomar enteros.
- "Los estudiantes escriben la solución **en forma completa**" → no se deja solo la parte real.
- "Escribe **teorema de Fredholm**."

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Ecuación característica y raíces complejas

$$
\det\left(A-\lambda I\right) = 0 \;\Rightarrow\; \lambda = \alpha \pm \beta i, \qquad \beta = \sqrt{-\Delta}
$$

**🔤 Diccionario:** $A$ matriz de coeficientes del sistema · $\lambda$ autovalor · $\alpha$ parte real · $\beta$ parte imaginaria (se toma $\beta>0$) · $\Delta$ discriminante de la característica.

**Atajo $2\times2$:**

$$
\lambda^{2} - \left(\operatorname{tr}A\right)\lambda + \det A = 0
$$

**🔤 Diccionario:** $\operatorname{tr}A$ traza (suma de la diagonal principal) · $\det A$ determinante de la matriz de coeficientes.

### B. Fórmula de Euler

$$
e^{\left(\alpha+\beta i\right)t} = e^{\alpha t}\left(\cos \beta t + i\sin \beta t\right)
$$

**🔤 Diccionario:** $\alpha$ parte real del autovalor · $\beta$ parte imaginaria · $t$ variable independiente. La exponencial real $e^{\alpha t}$ multiplica a **ambas** funciones trigonométricas.

### C. De la solución compleja a la solución real

Con $\vec v = \vec u + i\vec w$ (parte real $\vec u$, parte imaginaria $\vec w$):

$$
\vec x(t) = C_1 e^{\alpha t}\left(\vec u\cos\beta t - \vec w\sin\beta t\right) + C_2 e^{\alpha t}\left(\vec u\sin\beta t + \vec w\cos\beta t\right)
$$

**🔤 Diccionario:** $\vec u$ parte real del autovector · $\vec w$ parte imaginaria del autovector · $C_1, C_2$ constantes reales · el factor $e^{\alpha t}$ aparece en los dos bloques.

Forma operativa equivalente (la que se usa al calcular):

$$
\vec x(t) = C_1\operatorname{Re}\left[\vec v\,e^{\lambda t}\right] + C_2\operatorname{Im}\left[\vec v\,e^{\lambda t}\right]
$$

**🔤 Diccionario:** $\operatorname{Re}$ parte real · $\operatorname{Im}$ parte imaginaria · se calcula **primero** $\vec v\,e^{\lambda t}$ completo y **después** se separa.

### D. Autovector complejo

$$
\left(A-\lambda I\right)\vec v = \vec 0, \qquad \lambda = \alpha + \beta i
$$

**🔤 Diccionario:** $\vec v$ autovector (entradas complejas) · el sistema tiene infinitas soluciones: una recta compleja.

**Regla de elección:** fijar una componente en $1$ y despejar el resto; si salen fracciones, multiplicar el vector completo por el denominador. El profesor pide **enteros** cuando se pueda.

### E. ➕ Teorema de Fredholm (sistema no homogéneo)

Si una combinación de las filas de $A$ da cero, la **misma** combinación del término independiente también debe dar cero; si no, el sistema **no tiene solución**.

$$
\sum_i c_i\,(\text{fila}_i) = \vec 0 \;\Rightarrow\; \text{exigir } \sum_i c_i\,b_i = 0
$$

**🔤 Diccionario:** $c_i$ coeficientes de la combinación lineal · $b_i$ componentes del término independiente · si la condición falla, no hay solución (incompatible).

### F. ➕ Casos todavía no dictados (para cuando lleguen)

| Caso | Qué falta | Se resuelve con |
|---|---|---|
| $\lambda$ real repetido | un segundo vector independiente | autovector generalizado: $\left(A-\lambda I\right)\vec w = \vec v$ |
| sistema no homogéneo | una solución particular | variación de parámetros matricial o Fredholm |
| forma no canónica | reducir el orden del sistema | eliminación (👉 `261109` §4.1) |

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### Caso 1 — Un par complejo (el caso dictado)

Autovalores $\alpha \pm \beta i$; se trabaja **solo** con $\alpha+\beta i$:

$$
\vec x = C_1\operatorname{Re}\left[\vec v e^{\lambda t}\right] + C_2\operatorname{Im}\left[\vec v e^{\lambda t}\right]
$$

Aporta **dos** constantes, aunque se haya resuelto con un solo autovalor.

### Caso 2 — Mezcla de reales y complejos (superposición)

$$
\vec x = \underbrace{C_1\vec v_1e^{\lambda_1 t}}_{\text{parte real}} + \underbrace{C_2\operatorname{Re}\left[\vec v e^{\lambda t}\right] + C_3\operatorname{Im}\left[\vec v e^{\lambda t}\right]}_{\text{par complejo}}
$$

**🔤 Diccionario:** $\lambda_1$ autovalor real · $\lambda = \alpha+\beta i$ autovalor complejo · el número total de constantes iguala el orden del sistema.

### Caso 3 — ➕ Autovalor real repetido (aún no dictado)

Si $\left(A-\lambda I\right)\vec v = \vec 0$ devuelve un solo vector independiente, hace falta $\vec w$ con $\left(A-\lambda I\right)\vec w = \vec v$. La solución es

$$
\vec x = C_1\vec v e^{\lambda t} + C_2\left(\vec w + \vec v\,t\right)e^{\lambda t}
$$

### Reglas de oro

| # | Regla | Por qué |
|---|---|---|
| 1 | **Solo la raíz positiva** $\alpha+\beta i$ | el conjugado da la misma información |
| 2 | **Enteros** en el autovector | evita fracciones y errores de signo |
| 3 | **Euler antes de separar** | primero $\vec v\,e^{\lambda t}$, después $\operatorname{Re}$ e $\operatorname{Im}$ |
| 4 | **Separar en cada componente** | $x(t)$ e $y(t)$ necesitan su propio $\operatorname{Re}$ e $\operatorname{Im}$ |
| 5 | **Solución completa** | dos constantes por par complejo |
| 6 | **Verificar** $A\vec v = \lambda\vec v$ | con el vector complejo, en 10 segundos |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Sistema $2\times2$ con autovalores complejos

1. Escribir $A$ y calcular $\operatorname{tr}A$ y $\det A$.
2. Característica: $\lambda^{2} - \left(\operatorname{tr}A\right)\lambda + \det A = 0$.
3. Si $\Delta < 0$: $\lambda = \alpha \pm \beta i$ con $\beta = \sqrt{-\Delta}$.
4. **Tomar solo** $\lambda = \alpha + \beta i$.
5. Construir $A - \lambda I$ (entradas complejas).
6. Resolver la **primera fila**: una ecuación, dos incógnitas → fijar la primera componente en $1$.
7. Escribir $\vec v = \binom{1}{v_2}$ con $v_2$ complejo.
8. Calcular $\vec v\,e^{\lambda t}$ y aplicar Euler.
9. Separar $\operatorname{Re}$ e $\operatorname{Im}$ de **cada** componente.
10. Solución general: $C_1\operatorname{Re} + C_2\operatorname{Im}$.

**Plantilla mínima (ejemplo de clase):**

$$
\dot x = 4x - y, \qquad \dot y = 5x + 2y
$$

$$
\left|A-\lambda I\right| = \left(4-\lambda\right)\left(2-\lambda\right) + 5 = \lambda^{2} - 6\lambda + 13 = 0 \;\Rightarrow\; \lambda = 3 \pm 2i
$$

Con $\lambda = 3+2i$:

$$
\left(A-\lambda I\right) = \begin{pmatrix} 1-2i & -1 \\ 5 & -1-2i \end{pmatrix} \;\Rightarrow\; \left(1-2i\right)\alpha - \beta = 0 \;\Rightarrow\; \vec v = \begin{pmatrix} 1 \\ 1-2i \end{pmatrix}
$$

$$
\vec v\,e^{\lambda t} = \begin{pmatrix} 1 \\ 1-2i \end{pmatrix} e^{3t}\left(\cos 2t + i\sin 2t\right)
$$

$$
\operatorname{Re} = e^{3t}\begin{pmatrix} \cos 2t \\ \cos 2t + 2\sin 2t \end{pmatrix}, \qquad \operatorname{Im} = e^{3t}\begin{pmatrix} \sin 2t \\ \sin 2t - 2\cos 2t \end{pmatrix}
$$

$$
\boxed{\begin{aligned} x(t) &= C_1e^{3t}\cos 2t + C_2e^{3t}\sin 2t \\ y(t) &= C_1e^{3t}\left(\cos 2t + 2\sin 2t\right) + C_2e^{3t}\left(\sin 2t - 2\cos 2t\right) \end{aligned}}
$$

### 4.2 Sistema $3\times3$ con un real y un par complejo

1. Característica por cofactores; buscar la raíz real por Ruffini ($\pm1, \pm2, \pm3, \pm6$).
2. Factorizar: $\lambda_1$ real y $\lambda_{2,3} = \alpha \pm \beta i$.
3. Autovector real de $\lambda_1$ (👉 `261111` §4.1).
4. Con $\lambda = \alpha+\beta i$: resolver $\left(A-\lambda I\right)\vec v = \vec 0$ usando **dos** filas y despejando las componentes complejas.
5. Escribir $\vec v\,e^{\lambda t}$, aplicar Euler y separar.
6. Total: **tres** constantes.

**Plantilla mínima (ejemplo de clase):**

$$
A = \begin{pmatrix} 3 & -3 & 1 \\ 3 & -2 & 2 \\ -1 & 2 & 0 \end{pmatrix} \;\Rightarrow\; \lambda^{3} - \lambda^{2} + 2 = 0 \;\Rightarrow\; \lambda = -1, \quad \lambda = 1 \pm i
$$

$$
\lambda = -1: \quad \vec v_1 = \begin{pmatrix} 1 \\ 1 \\ -1 \end{pmatrix} \qquad\qquad \lambda = 1+i: \quad \vec v = \begin{pmatrix} 2 \\ 1-i \\ -1-i \end{pmatrix}
$$

### 4.3 Verificación

| Qué | Cómo |
|---|---|
| Autovector complejo | comprobar $A\vec v = \lambda\vec v$ multiplicando componente a componente |
| Solución real | sustituir $x(t)$ en su propia ecuación |
| Número de constantes | debe igualar el orden del sistema |

---

## ✅ 5. CHECKLIST FINAL

Antes de cerrar el ejercicio:

- [ ] El discriminante se calculó **bien** (revisar el signo del término independiente del determinante).
- [ ] Usé **solo** la raíz $\alpha+\beta i$.
- [ ] El autovector quedó con **enteros** (o con el mínimo denominador común).
- [ ] Apliqué **Euler antes** de separar partes.
- [ ] Separé $\operatorname{Re}$ e $\operatorname{Im}$ en **cada** componente, no solo en una.
- [ ] La solución tiene **dos** constantes por par complejo.
- [ ] Verifiqué $A\vec v = \lambda\vec v$.
- [ ] No dejé la solución "a medias" (el profesor lo marcó como error típico).

---

## ⚠️ 6. TRAMPAS DE ESTA CLASE

| Trampa | Consecuencia | Antídoto |
|---|---|---|
| Resolver también con $\alpha-\beta i$ | trabajo duplicado | regla 1 |
| Dejar el autovector con fracciones | errores de signo al multiplicar | multiplicar por el denominador |
| Separar $\operatorname{Re}$/$\operatorname{Im}$ **antes** de multiplicar por $\vec v$ | resultado falso | regla 3 |
| Separar solo en $x(t)$ y copiar en $y(t)$ | segunda componente incorrecta | regla 4 |
| Escribir solo la parte real | falta una constante | regla 5 |
| Sumar $e^{\alpha t}$ solo a una parte | mezcla de escalas | va en **todos** los términos |
