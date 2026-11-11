# 📘 CHEATSHEET — PROBABILIDAD · 11/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261111_VECTORES_ALEATORIOS.md`
> - **Fecha de transcripción:** 11/11/2026 (`AAMMDD` = `261111`)
> - **Tema principal:** VECTORES ALEATORIOS — conjuntamente discretos y conjuntamente continuos · f.p.m.c. conjunta · f.d.a.c. conjunta · marginales · densidades marginales · independencia
> - **Fuentes:** transcripción de clase + apuntes del estudiante. Complementos teóricos marcados con `➕` (Liliana Blanco, *Probabilidad*, cap. 5).
> - **Continuidad:** abre el capítulo de vectores. Viene de `261109_NORMAL_Y_APROX_BINOMIAL` (una sola variable, cerrado).
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261111_VECTORES_ALEATORIOS` §2.E».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Hay más de una variable definida sobre el mismo $(\Omega,\mathcal{F},P)$?** → es un **vector aleatorio** $\mathbf{X}=(X_1,\dots,X_n)$ (§2.A). Si es una sola, no aplica esta cheatsheet.
2. **Paso 1 — ¿Todas discretas o todas absolutamente continuas?** → **discreto** (§2.B) o **continuo** (§2.D). La mezcla discreta-continua no se estudia en el curso.
3. **Paso 2 — ¿Qué me piden?** probabilidad de una región, una marginal, la f.d.a.c., una densidad marginal o independencia → fila de la tabla.

| Si el enunciado dice… | Objeto | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "se definen $n$ variables aleatorias sobre el mismo espacio de probabilidad" | **Vector aleatorio** | $\mathbf{X}(\omega)=(X_1(\omega),\dots,X_n(\omega))$ | **§2.A** |
| "tabla de doble entrada", conteo de casos, "se lanza 3 veces…" | **f.p.m.c. conjunta** | $p(\mathbf{x})=P(\mathbf{X}=\mathbf{x})$ | **§2.B** + **§4.A** |
| "halle $P(X=x,\,Y=y)$" con tabla | **celda de la tabla** | $p(x,y)$ | **§2.B** + **§4.A** |
| "halle $P(X\le a,\,Y\le b)$" con tabla | **f.d.a.c. conjunta** | $F(x,y)=\sum_{s\le x}\sum_{t\le y}p(s,t)$ | **§2.C** + **§4.C** |
| "halle la marginal de $X$" con tabla | **suma de fila** | $p_X(x)=\sum_y p(x,y)$ | **§2.B** + **§4.B** |
| dan $f(x,y)$ y piden $P((X,Y)\in C)$ | **densidad conjunta** | $\iint_C f$ | **§2.D** + **§4.D** |
| "verifique que $f$ es función de densidad" | **normalización** | $\iint_{\mathbb{R}^2} f=1$ | **§2.D(a)** + **§4.D** |
| "halle la densidad marginal" con $f(x,y)$ | **integrar la otra variable** | $f_X(x)=\int_{-\infty}^{\infty}f(x,y)\,dy$ | **§2.E** + **§4.E** |
| "halle $F(x,y)$" y dan $f$ | **integral iterada** | $F(x,y)=\int_{-\infty}^{x}\int_{-\infty}^{y}f$ | **§2.D(b)** + **§4.F** |
| "halle $f$" y dan $F$ | **derivada parcial cruzada** | $f=\frac{\partial^2 F}{\partial x\,\partial y}$ | **§2.D(c)** + **§4.F** |
| "halle $F_X$ o $F_Y$" y dan $F$ | **límite** | $F_X(x)=\lim_{y\to\infty}F(x,y)$ | **§2.C** + **§4.C** |
| "¿son independientes?" | **producto** | $f(x,y)=f_X(x)f_Y(y)$ | **§2.F** + **§4.G** |
| "calcule $P(A\mid B)$" con $f$ conjunta | **condicional** | $\frac{P(A\cap B)}{P(B)}$ | **§2.F** + **§4.H** |

> 🗣️ **Frases del profe (literales) → método**
> - "No estamos interesados en el comportamiento individual de cada variable, sino en las relaciones que existen entre las variables." → la conjunta es el objeto central; las marginales son un resumen.
> - "El coseno de este ángulo da las relaciones entre cada par de variables… θ de 90° implica independencia." → la relación lineal se mide con $\rho$ (§2.F); θ = 90° ⇔ $\rho=0$.
> - "Si tengo la conjunta puedo hallar las marginales. Lo contrario no es cierto." → §3 Regla 4.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Vector aleatorio $n$-dimensional

- **Definición:** sean $X_1,\dots,X_n$ v.a.r. sobre el mismo $(\Omega,\mathcal{F},P)$. La función $\mathcal{F}$-$\mathcal{B}_n$-medible
$$
\mathbf{X}:\Omega\longrightarrow\mathbb{R}^n,\qquad \mathbf{X}(\omega):=\left(X_1(\omega),\dots,X_n(\omega)\right)
$$
se llama **vector aleatorio $n$-dimensional**.
- **Recorrido:**
$$
R_{\mathbf{X}}:=\left\{\mathbf{x}\in\mathbb{R}^n:\ \exists\,\omega\in\Omega,\ \mathbf{X}(\omega)=\mathbf{x}\right\}\subseteq\mathbb{R}^n
$$
- **Distribución (medida inducida):**
$$
P_{\mathbf{X}}(B):=P(\mathbf{X}\in B)=P\left(\left\{\omega\in\Omega:\mathbf{X}(\omega)\in B\right\}\right),\qquad B\in\mathcal{B}_n
$$
- **Rectángulo y probabilidad inducida:** con $r_1,\dots,r_n\in\mathbb{R}$,
$$
B=(-\infty,r_1]\times\cdots\times(-\infty,r_n]\in\mathcal{B}_n
\ \Longrightarrow\
P_{\mathbf{X}}(B)=P(X_1\le r_1,\dots,X_n\le r_n)=F(r_1,\dots,r_n)
$$

> **🔤 Diccionario:**
> - $\omega$: resultado del experimento (elemento de $\Omega$).
> - $\mathbf{X}(\omega)$: punto de $\mathbb{R}^n$; $\mathbf{X}$ es la **función** y $\mathbf{x}$ un valor concreto.
> - $X_i$: componente $i$-ésima; es una v.a.r. ordinaria.
> - $\mathcal{F}$-$\mathcal{B}_n$-medible: $\mathbf{X}^{-1}(B)\in\mathcal{F}$ para todo $B\in\mathcal{B}_n$; garantiza que $P_{\mathbf{X}}$ exista.
> - $\mathcal{B}_n=\mathcal{B}(\mathbb{R}^n)$: $\sigma$-álgebra de Borel de $\mathbb{R}^n$, generada por los rectángulos $(-\infty,r_1]\times\cdots\times(-\infty,r_n]$.
> - $P_{\mathbf{X}}$: medida de probabilidad sobre $\mathcal{B}_n$; "distribución del vector".
> - Caso $n=2$: $\mathbf{X}=(X_1,X_2)$ se dibuja como punto $(x_1,x_2)$ del plano; $n=3$ produce un hipercubo (el curso trabaja $n=2$).

---

### B. Vector conjuntamente discreto — f.p.m.c.

- **Definición:** todas las $X_i$ discretas. La función
$$
p(\mathbf{x}):=P(\mathbf{X}=\mathbf{x}),\qquad \mathbf{x}\in R_{\mathbf{X}}
$$
se llama **función de probabilidad de masa conjunta** (f.p.m.c.; el profe dice también "común"). El libro la llama función de densidad del vector discreto.
- **Normalización:**
$$
p(\mathbf{x})\ge 0\ \ \forall\mathbf{x}\in R_{\mathbf{X}},\qquad \sum_{\mathbf{x}\in R_{\mathbf{X}}}p(\mathbf{x})=1
$$
- **Marginal (sumar la otra variable sobre todo su recorrido):**
$$
p_{X_j}(x)=\sum_{x_1}\cdots\sum_{x_{j-1}}\sum_{x_{j+1}}\cdots\sum_{x_n}p(x_1,\dots,x_n)
$$
$$
n=2:\qquad p_X(x)=\sum_{y\in R_Y}p(x,y),\qquad p_Y(y)=\sum_{x\in R_X}p(x,y)
$$

> **🔤 Diccionario:**
> - $R_{\mathbf{X}}\subseteq R_X\times R_Y$: subconjunto del producto cartesiano de los recorridos (en el ejemplo de la moneda coincide y hay $3\times3=9$ celdas, algunas con $0$).
> - $p(x,y)$: probabilidad de la **intersección** $\{X=x\}\cap\{Y=y\}$; nunca es una probabilidad condicional.
> - $p_X,p_Y$: **marginales**; son distribuciones unidimensionales "como si la otra variable no existiera".
> - $\sum_y p(x,y)$: se recorre la **fila** de $x$; $\sum_x p(x,y)$: la **columna** de $y$.

**Estructura de la tabla (siempre la misma):**

| $X\backslash Y$ | $y_1$ | $\cdots$ | $y_m$ | $p_X(x)$ |
|---|---|---|---|---|
| $x_1$ | $p(x_1,y_1)$ | $\cdots$ | $p(x_1,y_m)$ | $\sum_j p(x_1,y_j)$ |
| $\vdots$ | $\vdots$ | $\ddots$ | $\vdots$ | $\vdots$ |
| $x_k$ | $p(x_k,y_1)$ | $\cdots$ | $p(x_k,y_m)$ | $\sum_j p(x_k,y_j)$ |
| $p_Y(y)$ | $\sum_i p(x_i,y_1)$ | $\cdots$ | $\sum_i p(x_i,y_m)$ | $1$ |

---

### C. Función de distribución acumulada conjunta (f.d.a.c.)

- **Definición:** para todo $(x_1,\dots,x_n)\in\mathbb{R}^n$,
$$
F(x_1,\dots,x_n):=P(X_1\le x_1,\ X_2\le x_2,\ \dots,\ X_n\le x_n)
$$
- **Cálculo desde la conjunta:**
$$
\text{discreto:}\quad F(x,y)=\sum_{s\le x}\ \sum_{t\le y}p(s,t)
$$
$$
\text{continuo:}\quad F(x,y)=\int_{-\infty}^{x}\int_{-\infty}^{y}f(u,v)\,dv\,du
$$
- **f.d.a.c. marginal (límites):**
$$
F_{X_j}(x)=\lim_{x_i\to\infty,\ i\ne j}F(x_1,\dots,x_n);\qquad n=2:\quad F_X(x)=\lim_{y\to\infty}F(x,y),\quad F_Y(y)=\lim_{x\to\infty}F(x,y)
$$
- **➕ Propiedades que toda $F$ conjunta cumple (Teo. 5.14):** no decreciente en cada componente; continua a derecha en cada componente; $\lim_{x_i\to-\infty}F=0$; $\lim_{(x_1,\dots,x_n)\to(\infty,\dots,\infty)}F=1$; y la **condición de rectángulo**
$$
\Delta_{a}^{b}F:=F(b_1,b_2)-F(a_1,b_2)-F(b_1,a_2)+F(a_1,a_2)\ \ge 0,\qquad a\le b
$$
- **➕ Probabilidad de un rectángulo a partir de $F$:**
$$
P(a_1<X_1\le b_1,\ a_2<X_2\le b_2)=\Delta_{a}^{b}F
$$

> **🔤 Diccionario:**
> - $F$: probabilidad **acumulada** de la esquina $(-\infty,x]\times(-\infty,y]$; no es una densidad.
> - $\le$ en las dos variables: la f.d.a.c. siempre acumula hacia la izquierda y hacia abajo.
> - $\Delta_a^b F$: suma alternada de las 4 esquinas del rectángulo $(a_1,b_1]\times(a_2,b_2]$; $<$ en el extremo inferior, $\le$ en el superior.
> - $F_{X_j}$: marginal; se obtiene llevando al infinito **todas** las demás componentes.

---

### D. Vector conjuntamente continuo — densidad conjunta

- **Definición:** existen $f\ge 0$ integrable tal que, para todo boreliano $C\subseteq\mathbb{R}^n$,
$$
P(\mathbf{X}\in C)=\int\cdots\int_{C}f(x_1,\dots,x_n)\,dx_1\cdots dx_n
$$
$f$ se llama **función de densidad de probabilidad conjunta**.
- **(a) Normalización:**
$$
\int_{\mathbb{R}^n}f(x_1,\dots,x_n)\,dx_1\cdots dx_n=1
$$
- **(b) f.d.a.c. como integral iterada:**
$$
F(x_1,\dots,x_n)=\int_{-\infty}^{x_1}\cdots\int_{-\infty}^{x_n}f(t_1,\dots,t_n)\,dt_n\cdots dt_1
$$
- **(c) Recuperar $f$ desde $F$ (TFC, caso $n=2$):**
$$
f(x,y)=\frac{\partial^2 F(x,y)}{\partial x\,\partial y}\qquad\text{donde }f\text{ es continua}
$$

> **🔤 Diccionario:**
> - $f(x,y)$: **densidad**; NO es una probabilidad y puede ser mayor que $1$.
> - $f(x,y)\,dx\,dy$: probabilidad (aproximada) de la celdita $[x,x+dx]\times[y,y+dy]$; la probabilidad es el **volumen** bajo la superficie.
> - $C$: región del plano (o de $\mathbb{R}^n$) sobre la que se integra; si $C$ no toca el soporte, la integral es $0$.
> - "conjuntamente continuas": existe **una sola** $f$ que sirve para todos los borelianos a la vez.
> - $P(X=x,\ Y=y)=0$ para todo punto: por eso $\le$ y $<$ son intercambiables en continuo.

---

### E. Densidad marginal

- **Definición (integrar la variable que no interesa):**
$$
f_X(x)=\int_{-\infty}^{\infty}f(x,y)\,dy,\qquad f_Y(y)=\int_{-\infty}^{\infty}f(x,y)\,dx
$$
$$
f_{X_j}(x_j)=\int_{-\infty}^{\infty}\cdots\int_{-\infty}^{\infty}f(x_1,\dots,x_n)\,dx_1\cdots dx_{j-1}\,dx_{j+1}\cdots dx_n
$$
- **Relación con su f.d.a.c. marginal:**
$$
F_X(x)=\int_{-\infty}^{x}f_X(u)\,du,\qquad \frac{d}{dx}F_X(x)=f_X(x)
$$
- **Normalización de la marginal:**
$$
\int_{-\infty}^{\infty}f_X(x)\,dx=1
$$

> **🔤 Diccionario:**
> - $f_X$: densidad **marginal** de $X$; es una densidad unidimensional, la que ya se estudió en el capítulo anterior.
> - $\int_{-\infty}^{\infty}(\cdot)\,dy$: se integra sobre **todo** el recorrido de $Y$, respetando el soporte (si $f=0$ fuera de $0<y<1$, los límites son $0$ y $1$).
> - $F_X$: f.d.a.c. marginal; sale de integrar $f_X$ o de tomar el límite de $F$ (§2.C).
> - La marginal **no** determina la conjunta (§3 Regla 4).

---

### F. Independencia (➕) y puente con la correlación

- **Definición:** $X$ e $Y$ son independientes si
$$
P(X\in A,\ Y\in B)=P(X\in A)\,P(Y\in B)\qquad\forall A,B\in\mathcal{B}_1
$$
- **Criterios equivalentes:**
$$
F(x,y)=F_X(x)F_Y(y)\quad\forall x,y
$$
$$
\text{discreto:}\quad p(x,y)=p_X(x)p_Y(y)\quad\forall x\in R_X,\ y\in R_Y
$$
$$
\text{continuo:}\quad f(x,y)=f_X(x)f_Y(y)\quad\forall x,y
$$
- **Atajo continuo:** $X$ e $Y$ son independientes si $f(x,y)=h(x)\,g(y)$ **y** el soporte es un rectángulo (producto de intervalos).
- **➕ Correlación (lo que el profe llamó "el coseno del ángulo"):**
$$
Cov(X,Y)=E(XY)-E(X)E(Y),\qquad \rho=\frac{Cov(X,Y)}{\sigma_X\sigma_Y},\qquad -1\le\rho\le1
$$
$$
\rho=0\ \Rightarrow\ \text{incorreladas};\qquad \rho=\pm1\ \Leftrightarrow\ Y=aX+b\ \text{c.s.}
$$

> **🔤 Diccionario:**
> - $A,B$: borelianos arbitrarios (intervalos, uniones, etc.), no solo de la forma $(-\infty,x]$.
> - $f(x,y)=h(x)g(y)$: la conjunta **factoriza**; si el soporte no es rectangular, la factorización no basta.
> - $\rho$: mide **relación lineal**; $\rho=0$ (θ = 90°) **no** garantiza independencia en general (sí en la normal bivariada).
> - $Cov$: puede ser negativa; sus unidades son las de $X$ por las de $Y$.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — Discreto ⇔ tabla; continuo ⇔ integral.** Nunca se mezclan: si hay tabla, se suma; si hay $f$, se integra.

**🟢 Regla 2 — Marginal = "borrar" la otra variable.** En discreto se **suma** la fila/columna completa; en continuo se **integra** sobre todo el recorrido de la otra. Los límites los manda el soporte, no la intuición.

**🟢 Regla 3 — El soporte manda.** Fuera del soporte la densidad es $0$; por eso $\int_{-\infty}^{\infty}$ se convierte en $\int_{0}^{1}$ si $0<y<1$. Si la región pedida no corta el soporte, la probabilidad es $0$.

**🟢 Regla 4 — De la conjunta salen las marginales; de las marginales NO sale la conjunta.** Dos conjuntas distintas pueden compartir las mismas marginales. La información de la **dependencia** solo vive en la conjunta.

**🟢 Regla 5 — $F$ conjunta ≠ producto de marginales.** $F(x,y)=F_X(x)F_Y(y)$ es exactamente la independencia (§2.F). En general $F(x,y)\neq F_X(x)F_Y(y)$.

**🟢 Regla 6 — $f$ no es probabilidad.** $f(x,y)$ puede valer $5$; lo que debe valer $1$ es la **integral doble**. En cambio $p(x,y)\le 1$ siempre.

**🟢 Regla 7 — Continuo: da igual $\le$ o $<$; discreto: NO.** En continuo $P(X=x)=0$; en discreto $P(X\le k)\neq P(X<k)$.

**🟢 Regla 8 — Verificación rápida (3 chequeos).**
1. ¿La conjunta suma/integra $1$?
2. ¿Cada marginal suma/integra $1$?
3. ¿$F\to 0$ cuando alguna componente $\to-\infty$ y $F\to 1$ en $(+\infty,\dots,+\infty)$?

**⚠️ Trampas típicas**
- Sumar la marginal sobre **toda** la tabla cuando el enunciado pide $P(X\le a,Y\le b)$: eso es la f.d.a.c., no la marginal.
- Poner $\sum$ donde va $\int$ (o al revés) solo porque el resultado "se ve" razonable.
- Olvidar el soporte y reportar la integral sobre todo $\mathbb{R}^2$.
- Creer que $Cov(X,Y)=0$ prueba independencia.
- Confundir $f_X(x)$ (marginal) con $f(x\mid y)$ (condicional): la condicional se define como $f(x\mid y)=\frac{f(x,y)}{f_Y(y)}$.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 🎲 A. Construir la tabla conjunta (discreto)

1. **Describe** $\Omega$ y asigna $P$ a cada resultado (equiprobable si el experimento es regular).
2. **Define** $X$ e $Y$ con palabras y escribe $R_X$, $R_Y$.
3. **Enumera** los resultados favorables de cada celda $(x,y)$ y cuenta.
4. **Divide** entre $|\Omega|$ y llena la tabla.
5. **Agrega** marginales (sumas) y verifica que el total sea $1$.

**Plantilla (3 lanzamientos de moneda; $X$ = caras en lanzamientos 1-2, $Y$ = caras en lanzamientos 2-3):** $R_X=R_Y=\{0,1,2\}$.

| $X\backslash Y$ | $0$ | $1$ | $2$ | $p_X(x)$ |
|---|---|---|---|---|
| $0$ | $\frac18$ | $\frac18$ | $0$ | $\frac14$ |
| $1$ | $\frac18$ | $\frac14$ | $\frac18$ | $\frac12$ |
| $2$ | $0$ | $\frac18$ | $\frac18$ | $\frac14$ |
| $p_Y(y)$ | $\frac14$ | $\frac12$ | $\frac14$ | $1$ |

Celda $\frac14$: dos tríos favorables, $(C,S,C)$ y $(S,C,S)$ → $\frac{2}{8}$.

---

### 📊 B. Marginal desde la tabla

1. **Fija** el valor de la variable que queda ($x$ o $y$).
2. **Recorre** su fila (o columna) completa, incluidos los ceros.
3. **Suma** y escribe el resultado en la última columna (o fila).
4. **Verifica:** la suma de las marginales debe dar $1$.

**Plantilla:** $p_X(0)=\frac18+\frac18+0=\frac14$; $p_Y(1)=\frac18+\frac14+\frac18=\frac12$.

---

### 🧱 C. f.d.a.c. conjunta desde la tabla (y desde $F$ a marginales)

1. **Corta** el eje $x$ en los valores de $R_X$ y el eje $y$ en los de $R_Y$; cada intervalo $[x_i,x_{i+1})$ es una fila/columna.
2. **Acumula** en cada celda la suma de todas las $p$ con $s\le x$ y $t\le y$.
3. **Llena** la tabla; la esquina inferior derecha debe dar $1$.
4. **Marginal:** si dan $F$ y piden $F_X$, haz $y\to\infty$ (última columna); para $F_Y$, $x\to\infty$ (última fila).
5. **Probabilidad de rectángulo:** si piden $P(a<X\le b,\ c<Y\le d)$, usa $\Delta_a^bF$ (§2.C), no restes a mano.

**Plantilla (misma moneda):**

| $F(x,y)$ | $y<0$ | $0\le y<1$ | $1\le y<2$ | $y\ge2$ |
|---|---|---|---|---|
| $x<0$ | $0$ | $0$ | $0$ | $0$ |
| $0\le x<1$ | $0$ | $\frac18$ | $\frac14$ | $\frac14$ |
| $1\le x<2$ | $0$ | $\frac14$ | $\frac58$ | $\frac34$ |
| $x\ge2$ | $0$ | $\frac14$ | $\frac34$ | $1$ |

Ejemplo de lectura: $P\left(X\le\frac34,\ Y\le\frac13\right)=F\left(\frac34,\frac13\right)=\frac18$ porque $\frac34\in[0,1)$ y $\frac13\in[0,1)$.

---

### 📐 D. Verificar densidad y calcular probabilidad de una región

1. **Verifica** $f\ge0$ y $\iint_{\text{soporte}}f=1$.
2. **Traduce** la región $C$ a desigualdades en $x$ e $y$.
3. **Corta** el soporte con $C$: esos son los límites reales.
4. **Integra** (iterada, el orden que sea más fácil).
5. **Verifica** $0\le P\le1$ y coherencia con el dibujo.

**Plantilla:** $f(x,y)=6xy^{2}$ si $0<x<1,\ 0<y<1$; $0$ en otro caso.
$$
\int_0^1\!\!\int_0^1 6xy^{2}\,dy\,dx=\int_0^1 6x\left[\frac{y^{3}}{3}\right]_0^1dx=\int_0^1 2x\,dx=\left[x^{2}\right]_0^1=1\ \checkmark
$$
$$
P\left(\tfrac12<X\le\tfrac34,\ 0<Y\le\tfrac13\right)=\int_{1/2}^{3/4}\!\!\int_0^{1/3}6xy^{2}\,dy\,dx=\frac{15}{16}\cdot\frac{1}{81}=\frac{5}{432}\approx0{,}01157
$$

---

### 🧮 E. Densidades marginales desde $f(x,y)$

1. **Identifica** el soporte conjunto.
2. **Integra** $f$ respecto de la variable que se elimina, con límites dados por el soporte.
3. **Escribe** la marginal con su propio soporte (¡no lo olvides!).
4. **Verifica** que integre $1$.

**Plantilla (misma $f=6xy^{2}$):**
$$
f_X(x)=\int_0^1 6xy^{2}\,dy=6x\left[\frac{y^{3}}{3}\right]_0^1=2x,\quad 0<x<1
$$
$$
f_Y(y)=\int_0^1 6xy^{2}\,dx=6y^{2}\left[\frac{x^{2}}{2}\right]_0^1=3y^{2},\quad 0<y<1
$$
$$
P\left(\tfrac12<X\le\tfrac34\right)=\int_{1/2}^{3/4}2x\,dx=\left[x^{2}\right]_{1/2}^{3/4}=\frac{9}{16}-\frac{4}{16}=\frac{5}{16}=0{,}3125
$$

---

### 🔁 F. Pasar de $f$ a $F$ y de $F$ a $f$

1. **De $f$ a $F$:** integra $f$ desde $-\infty$ hasta $(x,y)$; parte el resultado según en qué trozo del soporte cae $(x,y)$.
2. **De $F$ a $f$:** deriva $\frac{\partial^2F}{\partial x\,\partial y}$ en la zona interior del soporte.
3. **Verifica** los límites de $F$ (0 y 1) y que $f\ge0$.

**Plantilla ($f=6xy^{2}$ en $(0,1)^2$):** para $0\le x<1,\ 0\le y<1$,
$$
F(x,y)=\int_0^x\!\!\int_0^y 6uv^{2}\,dv\,du=x^{2}y^{3}
$$
$$
F(x,y)=\begin{cases}0 & x<0\ \text{o}\ y<0\\ x^{2}y^{3} & 0\le x<1,\ 0\le y<1\\ y^{3} & x\ge1,\ 0\le y<1\\ x^{2} & 0\le x<1,\ y\ge1\\ 1 & x\ge1,\ y\ge1\end{cases}
$$
Y al revés: $\frac{\partial^2}{\partial x\,\partial y}\left(x^{2}y^{3}\right)=6xy^{2}=f(x,y)$. $\checkmark$

---

### 🔗 G. Decidir independencia

1. **Halla** las marginales (sumando o integrando).
2. **Multiplica** $f_X(x)f_Y(y)$ (o $p_Xp_Y$).
3. **Compara** con la conjunta en **todo** el soporte.
4. **Revisa el soporte:** si no es un rectángulo, son dependientes aunque factorice.
5. **Decide:** iguales en todo el soporte → independientes; un solo punto donde falle → dependientes.

**Plantilla:** $f(x,y)=6xy^{2}=(2x)(3y^{2})=f_X(x)f_Y(y)$ en $(0,1)^2$ (rectángulo) → **independientes**. Por eso $P\left(\frac12<X\le\frac34\mid Y>\frac12\right)=P\left(\frac12<X\le\frac34\right)=\frac{5}{16}$.

---

### 🎯 H. Probabilidad condicional con densidad conjunta

1. **Escribe** $P(A\mid B)=\frac{P(A\cap B)}{P(B)}$.
2. **Numerador:** integra $f$ sobre $A\cap B$ (la intersección manda los límites).
3. **Denominador:** integra la **marginal** de la variable de la condición sobre $B$.
4. **Divide** y verifica $0\le P\le1$.
5. **Atajo:** si son independientes, $P(A\mid B)=P(A)$; no hace falta integrar.

**Plantilla:** $P\left(\frac12<X\le\frac34\ \mid\ Y>\frac12\right)$ con $f=6xy^{2}$.
$$
P(A\cap B)=\frac{5}{16}\cdot\frac78=\frac{35}{128},\qquad P(B)=P\left(Y>\tfrac12\right)=\int_{1/2}^{1}3y^{2}\,dy=\frac78
$$
$$
P(A\mid B)=\frac{35/128}{7/8}=\frac{5}{16}=0{,}3125
$$

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿Es discreto (tabla) o continuo (integral)? ¿Usé el instrumento correcto?
- [ ] ¿Respeté el soporte en los límites de suma/integral?
- [ ] ¿La conjunta suma/integra $1$? ¿Cada marginal también?
- [ ] ¿La marginal la calculé sumando/integrando **todo** el recorrido de la otra variable?
- [ ] ¿Confundí $F(x,y)$ con $p(x,y)$ o con $f(x,y)$?
- [ ] ¿Usé $\Delta_a^bF$ para un rectángulo en vez de restar cuatro números a mano?
- [ ] Si pedían independencia: ¿comparé en **todo** el soporte y revisé que sea rectangular?
- [ ] ¿El resultado está en $[0,1]$ y es coherente con el dibujo de la región?
