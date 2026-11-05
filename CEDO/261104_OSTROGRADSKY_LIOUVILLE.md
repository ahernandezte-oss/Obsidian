# 📘 CHEATSHEET — CEDO · 04/11/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261104_OSTROGRADSKY_LIOUVILLE.md`
> - **Tema principal:** Fórmula de Ostrogradsky–Liouville (reducción de orden) para EDO lineales de **coeficientes variables**
> - **Fecha de clase:** 04/11/2026
> - **Fuente:** apuntes de clase del 04/11/2026 (2 páginas) + transcripción `语音 261104_140534` + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261104_OSTROGRADSKY_LIOUVILLE` §2.B»
> - **Complemento:** los casos de coeficientes constantes están en `261102_EDO_ORDEN_SUPERIOR`.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Los coeficientes son constantes?**
- Sí (números) → **NO** se usa este método → ecuación característica. 👉 §3 Caso 0 · cheatsheet `261102_EDO_ORDEN_SUPERIOR` §2.B
- No (aparecen $x$, $x^2$, $e^x$, $\ln x$, $\frac{1}{x}$…) → Paso 1.

**Paso 1 — ¿El enunciado entrega al menos UNA solución particular $y_1$?**
- Sí → aplicar Ostrogradsky–Liouville. 👉 §2.B · §4.1
- No → el método **no se puede aplicar todavía**: hay que proponer $y_1$ y verificarla. 👉 §3 Caso 1 · §4.2

**Paso 2 — ¿De qué orden es la EDO?**
- Orden $2$ → una sola integral. 👉 §4.1
- Orden $n$ con $n-1$ soluciones conocidas → reducción sucesiva. 👉 §2.E · §4.3

### Tabla de decisión

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| Coeficientes numéricos constantes | Ecuación característica (NO este tema) | $a_n\lambda^n + \cdots + a_0 = 0$ | §3 Caso 0 |
| Coeficientes variables **y te dan $y_1$** | Ostrogradsky–Liouville (orden 2) | $y_2 = y_1\int\frac{e^{-\int p\,dx}}{y_1^{2}}dx$ | §2.B · §4.1 |
| Coeficientes variables **sin** $y_1$ | Primero proponer y verificar $y_1$ | polinomio, $x^n$, $e^{\lambda x}$ | §3 Caso 1 · §4.2 |
| La EDO viene sin normalizar | Dividir por $a_0(x)$ antes de todo | $p = \frac{a_1}{a_0}$ | §2.A · §3 Caso 2 |
| Orden $3$ con **dos** soluciones conocidas | Reducción sucesiva | $W_n = Ce^{-\int p_1 dx}$ | §2.E · §4.3 |
| Orden $3$ con **una** solución conocida | No alcanza: falta otra | — | §3 Caso 6 |
| Coeficientes variables y término independiente $\neq 0$ | Homogénea primero, luego variación de parámetros | $y = y_h + y_p$ | §3 Caso 8 |

### Frases literales del profesor (transcripción del 04/11)

- "Necesita conocer una solución particular. Si no conozco una solución particular, no podemos aplicar" → **hace falta $y_1$**.
- "No hay métodos generales para buscar solución particular" → **$y_1$ se propone y se verifica**, no se deduce.
- "Es la fórmula de Ostrogradsky–Liouville" → **reducción de orden vía Wronskiano**.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Forma normalizada y coeficiente $p(x)$

$$
a_0(x)\,y'' + a_1(x)\,y' + a_2(x)\,y = 0
$$

$$
y'' + p(x)\,y' + q(x)\,y = 0, \qquad p(x) = \frac{a_1(x)}{a_0(x)}, \qquad q(x) = \frac{a_2(x)}{a_0(x)}
$$

**Condición de uso:** $a_0(x) \neq 0$ en el intervalo de trabajo.

**🔤 Diccionario:**
- $a_0(x), a_1(x), a_2(x)$: coeficientes de la EDO tal como viene en el enunciado.
- $p(x)$: coeficiente normalizado de $y'$; es el único dato que entra en la fórmula de Ostrogradsky–Liouville.
- $q(x)$: coeficiente normalizado de $y$; **no** aparece en la fórmula de $y_2$ (solo sirve para verificar).
- $x$: variable independiente.

### B. Fórmula de Ostrogradsky–Liouville (Wronskiano)

$$
\begin{vmatrix} y_1 & y_2 \\ y_1' & y_2' \end{vmatrix} = C\,e^{-\int p(x)\,dx}
$$

De ahí, despejando $y_2$:

$$
y_2 = y_1\int \frac{e^{-\int p(x)\,dx}}{y_1^{2}}\,dx
$$

**Cómo se lee:** el Wronskiano de las dos soluciones **nunca es arbitrario**; está fijado por $p(x)$. Con $y_1$ conocida queda una ecuación de primer orden para $y_2$.

**🔤 Diccionario:**
- $y_1$: solución particular conocida (dato del enunciado o propuesta y verificada).
- $y_2$: la solución que se busca.
- $C$: constante que multiplica al Wronskiano; se elige cómoda (normalmente $C = 1$) porque $y_2$ se usa como generador del espacio solución.
- $e^{-\int p\,dx}$: factor de Liouville, calculado con el $p(x)$ de §2.A.
- $\int p(x)\,dx$: se calcula **sin** constante de integración.

### C. Reducción de orden por sustitución $y = u\,y_1$

$$
y_1\,u'' + \left(2y_1' + p\,y_1\right)u' = 0
$$

$$
u' = \frac{C}{y_1^{2}}\,e^{-\int p\,dx}
$$

**Cómo se usa:** al sustituir $y = uy_1$ desaparece el término en $u$ (no aparece $u$ solo), la EDO baja a primer orden en $u'$, y de ahí se integra dos veces.

**🔤 Diccionario:**
- $u = u(x)$: el factor que falta para llegar a la segunda solución, $y = uy_1$.
- $u'$: incógnita real del problema reducido (aparece una EDO de primer orden).
- $2y_1' + py_1$: coeficiente que acompaña a $u'$.

### D. De dónde sale la fórmula (identidad de Liouville) ➕

Se parte de $W = y_1y_2' - y_1'y_2$ y se deriva:

$$
W' = y_1y_2'' - y_1''y_2
$$

Sustituyendo $y'' = -py' - qy$ en los dos términos y agrupando:

$$
W' = -p\left(y_1y_2' - y_1'y_2\right) = -p\,W
$$

que es una EDO separable de primer orden:

$$
W = C\,e^{-\int p(x)\,dx}
$$

Y como

$$
\left(\frac{y_2}{y_1}\right)' = \frac{y_1y_2' - y_2y_1'}{y_1^{2}} = \frac{W}{y_1^{2}}
$$

integrando sale la fórmula de §2.B. **Consecuencia práctica:** $q(x)$ no influye en $W$; solo $p(x)$ lo hace.

**🔤 Diccionario:** $W'$ = derivada del Wronskiano · $C$ = constante de integración · el resto igual que en §2.A y §2.B.

### E. Orden $n$ (Abel generalizado)

Con la EDO normalizada

$$
y^{(n)} + p_1(x)\,y^{(n-1)} + \cdots + p_n(x)\,y = 0
$$

el Wronskiano de $n$ soluciones cumple

$$
W_n = C\,e^{-\int p_1(x)\,dx}, \qquad p_1(x) = \frac{a_{n-1}(x)}{a_n(x)}
$$

**Uso con $n-1$ soluciones conocidas:** se sustituyen $y_1, \ldots, y_{n-1}$ en el determinante $n\times n$ y se expande por la **última columna** (la de $y_n$); queda una EDO de primer orden para $y_n$.

**🔤 Diccionario:**
- $p_1$: coeficiente normalizado de $y^{(n-1)}$, es decir el del segundo término de mayor orden.
- $a_n, a_{n-1}$: coeficientes de $y^{(n)}$ y de $y^{(n-1)}$ tal como vienen en el enunciado.
- $W_n$: determinante $n \times n$ de las $n$ soluciones y sus derivadas hasta orden $n-1$.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

| Caso | Situación | Qué hacer | 👉 Ir a |
|---|---|---|---|
| **Caso 0** | Coeficientes constantes | **No** usar este método: ecuación característica | §1 Paso 0 |
| **Caso 1** | No dan ninguna solución $y_1$ | Proponer $y_1$ (polinomio, $x^n$, $e^{\lambda x}$, $\sin$, $\cos$) y **verificar sustituyendo** | §4.2 |
| **Caso 2** | La EDO no está normalizada | Dividir todo por $a_0(x)$ **antes** de calcular $p$ | §2.A |
| **Caso 3** | $\int p\,dx$ da un logaritmo | El factor $e^{-\int p\,dx}$ se simplifica a un polinomio | §4.1 paso 4 |
| **Caso 4** | Aparece la constante $C$ | Elegirla cómoda ($C = 1$): no cambia el espacio solución | §2.B |
| **Caso 5** | La $y_2$ obtenida no verifica la EDO | $y_1$ no era solución o se normalizó mal: revisar antes de integrar | §4.1 paso 7 |
| **Caso 6** | Orden $n$ con menos de $n-1$ soluciones | No se puede cerrar: faltan datos | §2.E |
| **Caso 7** | La integral no es elemental | Se deja **indicada**: la solución general sigue siendo válida | §4.1 paso 5 |
| **Caso 8** | Término independiente $\neq 0$ | Resolver la homogénea con este método y luego variación de parámetros | cheatsheet `261102_EDO_ORDEN_SUPERIOR` §2.F |

**Reglas de oro (bolsillo):**
- **Sin $y_1$ no hay método.** Es la restricción declarada por el profesor.
- El método **no** depende de $q(x)$, solo de $p(x)$.
- Si al sustituir $y = uy_1$ **aparece** un término en $u$ (no en $u'$), hubo un error: ese término debe anularse por construcción.
- La $y_2$ que sale de la fórmula es el **generador** del espacio solución: se puede multiplicar por cualquier constante.
- Verificar siempre $y_2$ en la EDO **antes** de darla por buena: una $y_1$ mal propuesta produce una $y_2$ que no verifica.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Ostrogradsky–Liouville (orden 2, con $y_1$ dada)

1. **Normalizar**: dividir por $a_0(x)$ y leer $p(x) = \frac{a_1}{a_0}$ (§2.A).
2. **Verificar $y_1$**: sustituirla en la EDO y comprobar que da $0$.
3. **Calcular** $\int p\,dx$ (sin constante).
4. **Calcular** el factor de Liouville $e^{-\int p\,dx}$ y simplificarlo.
5. **Aplicar** $y_2 = y_1\int\frac{e^{-\int p\,dx}}{y_1^{2}}dx$.
6. **Escribir** $y = C_1y_1 + C_2y_2$.
7. **Verificar**: $y_2$ en la EDO y $W \neq 0$.

**Plantilla (ejemplo de clase):** $\left(x^{2}+1\right)y'' - 2xy' + 2y = 0$ con $y_1 = x$.

1. $a_0 = x^{2}+1$ → $p = \dfrac{-2x}{x^{2}+1}$.
2. $y_1 = x$: $y_1' = 1$, $y_1'' = 0$ → $\left(x^{2}+1\right)0 - 2x\left(1\right) + 2x = 0$ ✔
3. $\int p\,dx = \int\dfrac{-2x}{x^{2}+1}dx = -\ln\left(x^{2}+1\right)$.
4. $e^{-\int p\,dx} = e^{\ln\left(x^{2}+1\right)} = x^{2}+1$.
5. $y_2 = x\int\dfrac{x^{2}+1}{x^{2}}dx = x\int\left(1+\dfrac{1}{x^{2}}\right)dx = x\left(x-\dfrac{1}{x}\right) = x^{2}-1$.
6. $y = C_1x + C_2\left(x^{2}-1\right)$.
7. $W = x\left(2x\right) - 1\left(x^{2}-1\right) = x^{2}+1 \neq 0$ ✔ y coincide con $e^{-\int p\,dx}$ ✔

### 4.2 Cómo proponer $y_1$ cuando no la dan

1. **Probar** un polinomio del grado que pida la EDO: $y = ax^{2}+bx+c$ para orden $2$.
2. **Sustituir** y **agrupar por potencias** de $x$ (esto convierte la EDO en un sistema algebraico).
3. **Resolver** el sistema de coeficientes.
4. Si el sistema es **incompatible** para todo coeficiente, cambiar de propuesta (probó $y = x^n$ y no encajó → pasar a polinomio completo).
5. **Verificar** la $y_1$ encontrada antes de usarla.
6. Recién entonces aplicar §4.1.

**Plantilla (ejemplo de clase):** $\left(1-2x^{2}\right)y'' + 2y' + 4y = 0$, propuesta $y = ax^{2}+bx+c$.

1. $y' = 2ax+b$, $y'' = 2a$.
2. Sustituir: $\left(1-2x^{2}\right)\left(2a\right) + 2\left(2ax+b\right) + 4\left(ax^{2}+bx+c\right) = 0$.
3. Agrupar: $x^{2} \rightarrow -4a + 4a = 0$ (se anula sola); $x \rightarrow 4a + 4b$; constante $\rightarrow 2a + 2b + 4c$.
4. Sistema: $4a+4b = 0 \Rightarrow a=-b$ · $2a+2b+4c = 0 \Rightarrow c = 0$.
5. Elegir $a = 1$, $b = -1$, $c = 0$ → $y_1 = x^{2}-x$.
6. Verificación: $y_1' = 2x-1$, $y_1'' = 2$ → $\left(1-2x^{2}\right)2 + 2\left(2x-1\right) + 4\left(x^{2}-x\right) = 2-4x^{2}+4x-2+4x^{2}-4x = 0$ ✔

⚠️ **Aviso:** probar $y = x^{n}$ solo funciona cuando **todas** las potencias encajan en un mismo $n$. Si al agrupar quedan ecuaciones incompatibles, esa propuesta no sirve y hay que pasar al polinomio completo.

### 4.3 Orden $n$ con $n-1$ soluciones conocidas ➕

1. **Normalizar**: $y^{(n)} + p_1y^{(n-1)} + \cdots = 0$ y leer $p_1 = \frac{a_{n-1}}{a_n}$.
2. **Verificar** cada $y_1, \ldots, y_{n-1}$ en la EDO.
3. **Calcular** $W_n = Ce^{-\int p_1 dx}$ (§2.E).
4. **Plantear** el determinante $n\times n$ con las $n-1$ columnas conocidas y la última columna $\left(y_n, y_n', \ldots, y_n^{(n-1)}\right)$.
5. **Expandir por la última columna** → queda una EDO de primer orden para $y_n$.
6. **Resolver** e integrar.
7. **Verificar** $y_n$ y $W_n \neq 0$.

**Plantilla mínima:** orden $3$ con $y_1, y_2$ conocidas y $p_1$ calculado.

$$
\begin{vmatrix} y_1 & y_2 & y_3 \\ y_1' & y_2' & y_3' \\ y_1'' & y_2'' & y_3'' \end{vmatrix} = Ce^{-\int p_1 dx}
$$

Se desarrolla por la tercera columna: cada cofactor multiplica a $y_3$, $y_3'$ o $y_3''$, y eso da la EDO lineal de primer orden que hay que resolver.

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
- [ ] ¿**No** se incluyó la solución de los ejercicios propuestos para la tarea?

---

**Cita rápida:** 📘 Cheatsheet `261104_OSTROGRADSKY_LIOUVILLE` — cita el bloque (`§2.B`, `§3 Caso 1`, `§4.1`…) al resolver.
