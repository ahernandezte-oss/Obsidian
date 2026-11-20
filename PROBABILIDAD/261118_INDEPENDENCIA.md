# 📘 CHEATSHEET — PROBABILIDAD · 18/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261118_INDEPENDENCIA.md`
> - **Fecha de transcripción:** 18/11/2026 (`AAMMDD` = `261118`)
> - **Tema principal:** INDEPENDENCIA DE VARIABLES ALEATORIAS + cierre recuperado de 5.1 (soporte no rectangular, CDF por trozos, condicional con densidad)
> - **Fuentes:** transcripción de la clase del 18/11 + Liliana Blanco, cap. 5 (§5.1, Ejemplos 5.20–5.22, y §5.2). Lo recuperado del libro va marcado con `📕`; lo inferido, con `➕`.
> - **Continuidad:** viene de `261111_VECTORES_ALEATORIOS`. El **§0** explica el puente: qué cerró la clase anterior, qué falta en medio y dónde retoma esta.
> - **Formato de las plantillas:** cadena de igualdades con justificación por renglón (§4.0).
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261118_INDEPENDENCIA` §2.A».

---

## 🧭 0. PUENTE DESDE `261111` HASTA AQUÍ

**Mapa de continuidad:**

| Tramo | Qué se vio | Dónde está |
|---|---|---|
| Clase 11/11 — §5.1 | Vector aleatorio, f.p.m.c. conjunta, f.d.a.c. conjunta, densidad conjunta, marginales, TFC | 📘 `261111_VECTORES_ALEATORIOS` §2.A–§2.E |
| Clase 11/11 — cierre | De $f$ a $F$ con soporte rectangular $(0,1)^2$ y marginales $f_X=2x$, $f_Y=3y^2$ | 📘 `261111` §4.E–§4.F |
| ⬜ **HUECO** (libro §5.1, Ejemplos 5.20–5.22) | **Soporte no rectangular** (triángulo), **CDF por trozos**, **condicional con densidad** | 📘 **esta cheatsheet §2.C** + §4.E–§4.F |
| Clase 18/11 — §5.2 | Independencia: urna con/sin reemplazo, definición, criterios, densidad continua, $P(XY>1)$ | 📘 **esta cheatsheet §2.A–§2.B** + §4.A–§4.D |

**Por qué existe el hueco.** La clase del 11/11 cerró con: «hoy nos perdimos ver como 20 páginas del capítulo». Esas páginas son el final de §5.1 (Ejemplos 5.20, 5.21 y 5.22) y es justo el tramo que esta transcripción ya no repite: la clase del 18/11 **abre §5.2 directamente** con la urna de 3 rojas y 6 azules.

**El conector, en tres frases:**
1. La 261111 enseñó a integrar $f$ cuando el soporte es un **rectángulo** (constantes como límites).
2. El hueco enseña qué cambia cuando el soporte es una **recta o un triángulo** (límites que dependen de la otra variable) y cómo se parte $F$ en trozos.
3. La 261118 usa exactamente eso para separar los dos casos: **conjunta = producto de marginales** (independientes) vs. **conjunta ≠ producto** (dependientes).

> ⚠️ No hay teoría nueva entre ambos puntos: §5.2 empieza con la Definición 5.23, que es lo primero que formaliza esta clase. Lo único que faltaba era el **cierre técnico de §5.1** (§2.C).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Me piden decidir si dos variables son independientes?** → §2.A–§2.B y §4.A–§4.D.
2. **Paso 1 — ¿Los datos son una tabla (discretas) o una $f(x,y)$ (continuas)?** → el criterio cambia: sumas vs. integrales.
3. **Paso 2 — ¿El soporte es rectangular o una curva/triángulo?** → si no es rectangular, primero geometría (§2.C), después integral.
4. **Paso 3 — ¿Piden $P$ de una región con frontera curva ($xy>1$) o lineal ($x\le 3y$)?** → partir la integral donde cambia la frontera (§4.D y §4.E).

| Si el enunciado dice… | Objeto | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "¿son independientes?" con tabla de doble entrada | **criterio discreto** | $p(x,y)=p_X(x)p_Y(y)$ | **§2.B** + **§4.A** |
| "se extrae **con** reemplazo" | **independientes por diseño** | $P(A\cap B)=P(A)P(B)$ | **§2.B** + **§4.A** |
| "se extrae **sin** reemplazo" | **dependientes por diseño** | $P(A\cap B)=P(A)P(B\mid A)$ | **§2.B** + **§4.B** |
| "¿son independientes?" y dan $f(x,y)$ | **criterio continuo** | $f(x,y)=f_X(x)f_Y(y)$ | **§2.A** + **§4.C** |
| "la densidad **factoriza**: $f=h(x)g(y)$" | **teorema de factorización** | $h(x)g(y)$ | **§2.A** + **§3 Regla 5** |
| $F(x,y)=F_X(x)F_Y(y)$ | **criterio con la f.d.a.c.** | producto de acumuladas | **§2.A** |
| "halle $k$" y el soporte es un triángulo | **normalización con geometría** | $\iint_D k=1$ | **§2.C.1** + **§4.E** |
| "halle $F(x,y)$" con densidad $x+y$ o soporte triangular | **CDF por trozos** | $\int_{-\infty}^{x}\int_{-\infty}^{y}f$ | **§2.C.2** + **§4.F** |
| "calcule $P(X<\tfrac12\mid Y>6)$" con $f$ conjunta | **condicional con densidad** | $\frac{P(A\cap B)}{P(B)}$ | **§2.C.3** + 📘 `261111` §4.H |
| "calcule $P(XY>1)$" con $f$ conjunta | **región con curva** | $\iint_{\{xy>1\}}f$ | **§4.D** |
| "calcule $P(X\le 3Y)$" con soporte triangular | **región con recta** | $\iint_{\{x\le3y\}}f$ | **§4.E** |

> 🗣️ **Frases del profe (literales) → método**
> - "Para todo $x,y$ que pertenecen al producto cartesiano de los respectivos recorridos, si $P(X=x,Y=y)=P(X=x)P(Y=y)$, entonces las variables son independientes." → criterio discreto (§2.B).
> - "La independencia implica que la función de distribución acumulada se pueda factorizar como el producto de las individuales. Y lo contrario también es cierto." → §2.A.
> - "Si al menos una no cumple, ya no son independientes." → §3 Regla 3.
> - "Las marginales no deben cambiar [al cambiar el mecanismo de extracción]." → §3 Regla 4.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Independencia: definición y equivalencias

- **Definición (Def. 5.23):** $X$ e $Y$ definidas sobre el mismo $(\Omega,\mathcal{F},P)$ son **estadísticamente (o estocásticamente) independientes** si
$$
P(X\in A,\ Y\in B)=P(X\in A)\,P(Y\in B)\qquad\forall A,B\in\mathcal{B}_1
$$
- **Equivalencia con la f.d.a.c.:**
$$
F(x,y)=F_X(x)\,F_Y(y)\quad\forall x,y\ \Longleftrightarrow\ X,Y\ \text{independientes}
$$
- **Criterio discreto:**
$$
p(x,y)=p_X(x)\,p_Y(y)\qquad\forall x\in R_X,\ y\in R_Y
$$
- **Criterio continuo:**
$$
f(x,y)=f_X(x)\,f_Y(y)\qquad\forall x,y
$$
- **Teorema de factorización:** si existen $h(x)\ge0$ y $g(y)\ge0$ (no necesariamente densidades) con
$$
f(x,y)=h(x)\,g(y)\qquad\forall x,y
$$
entonces $X$ e $Y$ son independientes (y el soporte resulta rectangular).
- **➕ Extensión a $n$ variables:**
$$
P(X_1\in A_1,\dots,X_n\in A_n)=\prod_{i=1}^{n}P(X_i\in A_i)\qquad\forall A_i\in\mathcal{B}_1
$$

> **🔤 Diccionario:**
> - $A,B$: borelianos **arbitrarios** (intervalos, uniones, semirrectas), no solo de la forma $(-\infty,x]$.
> - $F$: f.d.a.c. conjunta; $F_X,F_Y$: acumuladas marginales.
> - $p$: función de masa conjunta; $p_X,p_Y$: marginales.
> - $f$: densidad conjunta; $f_X,f_Y$: densidades marginales.
> - $h,g$: funciones no negativas cualesquiera; la igualdad debe valer en **todo** el plano (por eso obliga a soporte rectangular).

---

### B. Decidir independencia: criterio operativo

| Situación | Qué se compara | Si falla una sola vez… |
|---|---|---|
| **Discretas** (tabla) | $p(x,y)$ de cada celda vs. $p_X(x)\,p_Y(y)$ de sus márgenes | ya son **dependientes** |
| **Continuas** ($f$) | $f(x,y)$ vs. $f_X(x)f_Y(y)$ en todo el soporte | ya son **dependientes** |
| **Con la f.d.a.c.** | $F(x,y)$ vs. $F_X(x)F_Y(y)$ | ya son **dependientes** |
| **Factoriza** $f=h(x)g(y)$ | la igualdad en todo el plano (soporte rectangular) | si el soporte no es rectangular, **dependientes** |

- **Regla práctica del mecanismo de extracción:**
$$
\text{con reemplazo}\ \Rightarrow\ \text{independientes},\qquad \text{sin reemplazo}\ \Rightarrow\ \text{dependientes}
$$
(no es un teorema universal, pero es el patrón del curso y de los dos ejemplos de la urna).
- **➕ FGM de la suma:** si $X,Y$ son independientes y $Z=X+Y$,
$$
m_Z(t)=m_X(t)\,m_Y(t)
$$

> **🔤 Diccionario:**
> - "una sola falla basta": la independencia es una condición **universal** ($\forall x,y$); un contraejemplo la rompe.
> - Las **marginales no cambian** al pasar de con reemplazo a sin reemplazo: las probabilidades de la primera extracción son las mismas. Lo que cambia es la **conjunta**.
> - $m_Z$: FGM de la suma; el producto de FGM solo vale si hay independencia.

---

### C. 📕 Cierre de §5.1 (lo que quedó en el hueco)

#### C.1 Densidad en soporte no rectangular (Ejemplo 5.22)

- **Receta:** con $f(x,y)=k$ sobre un triángulo, el valor de $k$ es
$$
k=\frac{1}{\text{área}(D)}
$$
- **Caso del libro:** $D=\{0\le x\le2,\ 0\le y\le1,\ 2y\le x\}$.
$$
k=1,\qquad f_X(x)=\frac{x}{2}\ (0<x<2),\qquad f_Y(y)=2-2y\ (0<y<1)
$$
- **f.d.a.c. por trozos** (cambia de fórmula al cruzar la recta $x=2y$):
$$
F(x,y)=\begin{cases}
0 & x<0\ \text{o}\ y<0\\
xy-y^{2} & 0\le x\le2,\ 0\le y\le\frac{x}{2}\\
\frac{x^{2}}{4} & 0\le x\le2,\ \frac{x}{2}\le y\\
2y-y^{2} & x\ge2,\ 0\le y\le1\\
1 & x\ge2,\ y\ge1
\end{cases}
$$
- **Región con recta:** $P(X\le3Y)$. La recta $x=3y$ corta al soporte y obliga a partir la integral en $y=\frac{2}{3}$ (§4.E).

> **🔤 Diccionario:**
> - $D$: soporte (conjunto donde $f>0$); aquí un triángulo, no un rectángulo.
> - $2y\le x$: frontera del soporte; es la recta que hay que respetar en **cada** límite de integración.
> - $k$: constante de normalización; con $f$ constante vale $1/\text{área}$.

#### C.2 CDF por trozos (Ejemplo 5.21)

- **Caso del libro:** $f(x,y)=x+y$ si $0<x<1,\ 0<y<1$; $0$ en otro caso.
$$
F(x,y)=\begin{cases}
0 & x<0\ \text{o}\ y<0\\
\frac{x^{2}y+xy^{2}}{2} & 0\le x<1,\ 0\le y<1\\
\frac{x^{2}+x}{2} & 0\le x<1,\ y\ge1\\
\frac{y^{2}+y}{2} & x\ge1,\ 0\le y<1\\
1 & x\ge1,\ y\ge1
\end{cases}
$$
$$
f_X(x)=x+\frac12\ (0<x<1),\qquad f_Y(y)=y+\frac12\ (0<y<1)
$$
- **Regla de las 5 zonas:** las fronteras son $x=0$, $x=1$, $y=0$, $y=1$. Fuera del cuadrado $F=0$; dentro, $F$ es la integral desde la esquina; a la derecha/arriba del cuadrado, $F$ ya **no crece** con esa variable.

> **🔤 Diccionario:**
> - "por trozos": una fórmula distinta en cada zona del plano; hay que **elegir la zona** antes de integrar.
> - En $x\ge1$ o $y\ge1$ la integral se topa con el borde del soporte y se congela.
> - $f_X=x+\frac12$: no es $x$; la marginal integra la $y$ y la $y$ aporta $\frac12$.

#### C.3 Condicional con densidad conjunta (Ejemplo 5.20)

- **Caso del libro:** $f(x,y)=\frac{4x}{y^{3}}$ si $0<x<1,\ y>1$; $0$ en otro caso.
$$
f_X(x)=2x,\qquad f_Y(y)=\frac{2}{y^{3}}\ (y>1),\qquad P\left(X<\tfrac12\ \mid\ Y>6\right)=\frac14
$$
- **Método:** ya está en 📘 `261111` §4.H (numerador sobre $A\cap B$, denominador con la marginal). Aquí solo se recupera el ejemplo: como $f=(2x)\left(\frac{2}{y^{3}}\right)$, las variables son **independientes** y la condicional vale $P\left(X<\frac12\right)=\frac14$.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — La independencia se verifica en TODO el soporte.** No basta un punto; hay que recorrer todas las celdas o todo el soporte.

**🟢 Regla 2 — Una sola falla ⇒ dependientes.** La condición es universal; con un contraejemplo se cierra el problema (así lo hizo el profe con $p(0,0)$ en la urna sin reemplazo).

**🟢 Regla 3 — Con reemplazo ⇒ independientes; sin reemplazo ⇒ dependientes.** Es el patrón de los dos ejemplos de la urna y la forma más rápida de anticipar el resultado antes de calcular.

**🟢 Regla 4 — Las marginales no cambian con el mecanismo.** Cambia la **conjunta**, no las marginales: en las dos urnas $P(X=0)=P(Y=0)=\frac23$.

**🟢 Regla 5 — Factorizar no siempre es independencia.** $f=h(x)g(y)$ debe valer en **todo** el plano; si el soporte es un triángulo, la factorización falla o fuerza a que las funciones se anulen, y las variables son dependientes.

**🟢 Regla 6 — El soporte manda los límites.** En $D=\{2y\le x\}$ los límites son $y\in[0,x/2]$ (al integrar en $y$) o $x\in[2y,2]$ (al integrar en $x$). Nunca $[0,1]$ por costumbre.

**🟢 Regla 7 — Región con curva: partir donde cambia la frontera.** Para $P(XY>1)$ con $X\in(0,2)$, $Y>1$: la integral se ordena como $y\in[1,\infty)$, $x\in[1/y,2]$ (§4.D), o se parte en $x=1$ si se integra primero en $y$.

**🟢 Regla 8 — $k$ con $f$ constante = $1/\text{área}$.** Si $D$ es un triángulo, calcula el área y listo; no hace falta integrar dos veces.

**🟢 Regla 9 — Verificación rápida (4 chequeos).**
1. ¿La tabla suma $1$? ¿La $f$ integra $1$?
2. ¿Cada marginal suma/integra $1$?
3. ¿Comparé **todas** las celdas / todo el soporte?
4. ¿La condicional quedó en $[0,1]$?

**⚠️ Trampas típicas**
- Comparar $p(0,0)$ con $p_X(0)+p_Y(0)$ (suma) en vez de con el **producto**.
- Declarar independencia tras verificar **una** celda que coincide.
- Olvidar que sin reemplazo la segunda probabilidad es **condicional** ($\frac58$, no $\frac68$).
- Integrar $P(XY>1)$ sobre todo $(0,2)\times(1,\infty)$ sin la restricción $x>1/y$.
- En el triángulo, usar $x\in[0,2]$ y $y\in[0,1]$ independientes (eso sería el rectángulo, no $D$).

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 📏 4.0 Protocolo de escritura: la cadena

Toda cuenta se escribe como **cadena de igualdades**:

1. **Una igualdad por renglón.** El primero enuncia la cantidad; los demás empiezan con `=`.
2. **Cada renglón lleva su justificación** entre paréntesis.
3. **No se salta ningún paso**: suma, primitiva, evaluación y simplificación se ven escritas.
4. **El último renglón es el resultado** (con decimal si aplica).

**Patrón mínimo:**
$$
\begin{aligned}
2^{3} &= 8 && \text{(evaluar la potencia)}\\
&= 2(4) && \text{(factorizar: }8=2\cdot4\text{)}
\end{aligned}
$$

---

### 🎲 A. Tabla conjunta CON reemplazo (discreto)

1. **Fija** el tamaño del espacio: $9$ balotas, $6$ azules, $3$ rojas.
2. **Asigna** la probabilidad de cada extracción (no cambia entre extracciones).
3. **Multiplica** para cada celda $(x,y)$.
4. **Agrega** marginales y verifica que sumen $1$.
5. **Decide:** compara celda a celda con el producto de marginales.

**Plantilla ($X=0$ si la 1.ª es azul, $Y=0$ si la 2.ª es azul):**
$$
\begin{aligned}
p(0,0) &= P(\text{azul}_1)\,P(\text{azul}_2) && \text{(reemplazo: independientes)}\\
&= \frac{6}{9}\cdot\frac{6}{9} && \text{(6 azules de 9)}\\
&= \frac{36}{81} && \text{(multiplicar)}\\
&= \frac{4}{9} && \text{(simplificar)}
\end{aligned}
$$

| $X\backslash Y$ | $0$ | $1$ | $p_X(x)$ |
|---|---|---|---|
| $0$ | $\frac49$ | $\frac29$ | $\frac23$ |
| $1$ | $\frac29$ | $\frac19$ | $\frac13$ |
| $p_Y(y)$ | $\frac23$ | $\frac13$ | $1$ |

Chequeo ($\forall$ celdas): $\frac49=(\frac23)^2$, $\frac29=\frac23\cdot\frac13$, $\frac29=\frac13\cdot\frac23$, $\frac19=(\frac13)^2$ → **independientes**.

---

### 📦 B. Tabla conjunta SIN reemplazo (discreto)

1. **Fija** el espacio inicial (9) y el nuevo espacio tras la primera extracción (8).
2. **Condiciona** la segunda probabilidad: quedan $5$ azules o $2$ rojas.
3. **Multiplica** en cada celda y llena la tabla.
4. **Verifica** la suma ($1$) y que las marginales **no** cambiaron.
5. **Decide:** basta **una** celda que no coincida con el producto.

**Plantilla:**
$$
\begin{aligned}
p(0,0) &= P(\text{azul}_1)\,P(\text{azul}_2\mid\text{azul}_1) && \text{(sin reemplazo)}\\
&= \frac{6}{9}\cdot\frac{5}{8} && \text{(quedan 5 azules de 8)}\\
&= \frac{30}{72} && \text{(multiplicar)}\\
&= \frac{5}{12} && \text{(simplificar)}
\end{aligned}
$$

| $X\backslash Y$ | $0$ | $1$ | $p_X(x)$ |
|---|---|---|---|
| $0$ | $\frac{5}{12}$ | $\frac14$ | $\frac23$ |
| $1$ | $\frac14$ | $\frac1{12}$ | $\frac13$ |
| $p_Y(y)$ | $\frac23$ | $\frac13$ | $1$ |

Chequeo de una celda:
$$
\begin{aligned}
p(0,0) &= \frac{5}{12} && \text{(tabla sin reemplazo)}\\
&\neq \frac{4}{9} && \text{(producto }p_X(0)p_Y(0)\text{)}
\end{aligned}
$$
Una falla ⇒ **dependientes** (no hace falta revisar las demás).

---

### 🔍 C. Independencia con densidad conjunta (continuo)

1. **Verifica** que $f$ integre $1$ (y anota el soporte).
2. **Halla** $f_X$ y $f_Y$ integrando la otra variable.
3. **Multiplica** y compara con $f$.
4. **Revisa** que el soporte sea rectangular.
5. **Concluye** por igualdad en todo el soporte.

**Plantilla ($f(x,y)=\frac{3x^{2}}{8y^{2}}$, $0<x<2$, $y>1$):**
$$
\begin{aligned}
\int_{0}^{2}\!\!\int_{1}^{\infty}\frac{3x^{2}}{8y^{2}}\,dy\,dx &= \frac{3}{8}\left(\int_{0}^{2}x^{2}\,dx\right)\left(\int_{1}^{\infty}\frac{dy}{y^{2}}\right) && \text{(factoriza)}\\
&= \frac{3}{8}\cdot\frac{8}{3}\cdot 1 && \text{(integrar cada una)}\\
&= 1 && \text{(simplificar)}
\end{aligned}
$$
$$
\begin{aligned}
f_X(x) &= \int_{1}^{\infty}\frac{3x^{2}}{8y^{2}}\,dy && \text{(marginal: en }y\text{)}\\
&= \frac{3x^{2}}{8}\left[-\frac{1}{y}\right]_{1}^{\infty} && \text{(primitiva)}\\
&= \frac{3x^{2}}{8}(0+1) && \text{(evaluar límites)}\\
&= \frac{3x^{2}}{8},\qquad 0<x<2 && \text{(simplificar)}
\end{aligned}
$$
$$
\begin{aligned}
f_Y(y) &= \int_{0}^{2}\frac{3x^{2}}{8y^{2}}\,dx && \text{(marginal: en }x\text{)}\\
&= \frac{3}{8y^{2}}\left[\frac{x^{3}}{3}\right]_{0}^{2} && \text{(primitiva)}\\
&= \frac{3}{8y^{2}}\cdot\frac{8}{3} && \text{(evaluar)}\\
&= \frac{1}{y^{2}},\qquad y>1 && \text{(simplificar)}
\end{aligned}
$$
$$
\begin{aligned}
f_X(x)f_Y(y) &= \frac{3x^{2}}{8}\cdot\frac{1}{y^{2}} && \text{(marginales)}\\
&= \frac{3x^{2}}{8y^{2}} && \text{(multiplicar)}\\
&= f(x,y) && \text{(coincide en todo el soporte)}
\end{aligned}
$$
Soporte rectangular $(0,2)\times(1,\infty)$ y coincidencia total → **independientes**.

---

### 🎯 D. Región con curva: $P(XY>1)$

1. **Dibuja** el soporte y la curva $y=1/x$.
2. **Traduce** $XY>1$ a $x>1/y$ (o $y>1/x$).
3. **Ordena** la integral para que los límites sean funciones de una sola variable.
4. **Integra** y verifica que el resultado esté en $[0,1]$.

**Plantilla (mismo $f$):** como $y>1$, se tiene $1/y<1<2$, entonces
$$
\begin{aligned}
P(XY>1) &= \int_{1}^{\infty}\!\!\int_{1/y}^{2}\frac{3x^{2}}{8y^{2}}\,dx\,dy && \text{(región: }x>1/y,\ y>1\text{)}\\
&= \int_{1}^{\infty}\frac{3}{8y^{2}}\left[\frac{x^{3}}{3}\right]_{1/y}^{2}dy && \text{(integrar en }x\text{)}\\
&= \int_{1}^{\infty}\frac{1}{8y^{2}}\left(8-\frac{1}{y^{3}}\right)dy && \text{(evaluar extremos)}\\
&= \int_{1}^{\infty}\left(\frac{1}{y^{2}}-\frac{1}{8y^{5}}\right)dy && \text{(distribuir)}\\
&= \left[-\frac{1}{y}+\frac{1}{32y^{4}}\right]_{1}^{\infty} && \text{(primitivas)}\\
&= 0-\left(-1+\frac{1}{32}\right) && \text{(evaluar límites)}\\
&= \frac{31}{32}=0{,}96875 && \text{(sumar)}
\end{aligned}
$$

---

### 🔺 E. 📕 Densidad en triángulo: $k$, marginales y $P(X\le3Y)$

1. **Describe** $D$ con sus desigualdades y dibújalo.
2. **Normaliza:** $\iint_D k=1$ (si $f$ es constante, $k=1/\text{área}$).
3. **Marginal en $x$:** integra $y$ desde $0$ hasta la frontera $x/2$.
4. **Marginal en $y$:** integra $x$ desde la frontera $2y$ hasta $2$.
5. **Región con recta:** parte la integral donde la recta corta al soporte.

**Plantilla ($D=\{0\le x\le2,\ 0\le y\le1,\ 2y\le x\}$):**
$$
\begin{aligned}
1 &= \int_{0}^{1}\!\!\int_{2y}^{2} k\,dx\,dy && \text{(normalización)}\\
&= k\int_{0}^{1}(2-2y)\,dy && \text{(integrar en }x\text{)}\\
&= k\left[2y-y^{2}\right]_{0}^{1} && \text{(primitiva)}\\
&= k(2-1) && \text{(evaluar)}\\
&= k && \text{(simplificar)}
\end{aligned}
$$
$$
\begin{aligned}
f_X(x) &= \int_{0}^{x/2}1\,dy && \text{(}y\text{ de }0\text{ a }x/2\text{)}\\
&= \frac{x}{2},\qquad 0<x<2 && \text{(evaluar)}
\end{aligned}
$$
$$
\begin{aligned}
f_Y(y) &= \int_{2y}^{2}1\,dx && \text{(}x\text{ de }2y\text{ a }2\text{)}\\
&= 2-2y,\qquad 0<y<1 && \text{(evaluar)}
\end{aligned}
$$
$$
\begin{aligned}
P(X\le3Y) &= \int_{0}^{2/3}\!\!\int_{2y}^{3y}1\,dx\,dy+\int_{2/3}^{1}\!\!\int_{2y}^{2}1\,dx\,dy && \text{(partir en }y=2/3\text{)}\\
&= \int_{0}^{2/3}y\,dy+\int_{2/3}^{1}(2-2y)\,dy && \text{(integrar en }x\text{)}\\
&= \left[\frac{y^{2}}{2}\right]_{0}^{2/3}+\left[2y-y^{2}\right]_{2/3}^{1} && \text{(primitivas)}\\
&= \frac{2}{9}+\frac{1}{9} && \text{(evaluar)}\\
&= \frac13 && \text{(sumar)}
\end{aligned}
$$

---

### 🧱 F. 📕 CDF por trozos

1. **Marca** las fronteras del soporte ($x=0,1$; $y=0,1$; o la recta del soporte).
2. **Elige** la zona en la que cae $(x,y)$ antes de integrar.
3. **Integra** desde $-\infty$ hasta $(x,y)$, topando con las fronteras.
4. **Congela**: si $x$ o $y$ ya pasó el borde, $F$ deja de crecer en esa dirección.
5. **Verifica** $F\to0$ y $F\to1$.

**Plantilla ($f(x,y)=x+y$ en $(0,1)^2$):** para $0\le x<1,\ 0\le y<1$,
$$
\begin{aligned}
F(x,y) &= \int_{0}^{x}\!\!\int_{0}^{y}(u+v)\,dv\,du && \text{(definición de }F\text{)}\\
&= \int_{0}^{x}\left[uv+\frac{v^{2}}{2}\right]_{0}^{y}du && \text{(integrar en }v\text{)}\\
&= \int_{0}^{x}\left(uy+\frac{y^{2}}{2}\right)du && \text{(evaluar)}\\
&= \frac{x^{2}y}{2}+\frac{xy^{2}}{2} && \text{(integrar en }u\text{)}
\end{aligned}
$$
Fuera del cuadrado, los otros cuatro trozos de §2.C.2. Marginales: $f_X(x)=x+\frac12$, $f_Y(y)=y+\frac12$.

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿Comparé con el **producto** de marginales y no con la suma?
- [ ] ¿Revisé **todas** las celdas o todo el soporte (no solo una)?
- [ ] ¿En la urna sin reemplazo usé la probabilidad **condicional** de la segunda extracción?
- [ ] ¿Las marginales quedaron iguales en las dos urnas?
- [ ] ¿El soporte es rectangular? Si no, ¿lo usé para los límites?
- [ ] ¿Partí la integral donde la recta o la curva cambia la frontera?
- [ ] ¿Verifiqué que la conjunta suma/integra $1$?
- [ ] ¿Escribí la cuenta como **cadena** (un paso por renglón) con su justificación?
