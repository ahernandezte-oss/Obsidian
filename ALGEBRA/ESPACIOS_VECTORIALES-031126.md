# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 03/11/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `ESPACIOS_VECTORIALES-031126.md` |
| **Tema principal** | Espacios vectoriales (subespacios, base, coordenadas, dimensión) |
| **Fecha base** | 03/11/2026 (transcripción de clase 13) |
| **Fuente** | Transcripción clase 13 + apuntes `Vectorial_spaces_1.pdf` (sec. 4.1–4.4) |
| **Cómo citarla** | «📘 Cheatsheet `ESPACIOS_VECTORIALES-031126` §2.B» |
| **Notación** | vectores $u,v,w$ · escalares $c,a,b,\alpha,\beta\in\mathbb{R}$ · generador $\operatorname{Gen}\{\dots\}$ · base $\mathcal{B}$ · coordenadas $[v]_{\mathcal{B}}$ · dimensión $\dim V$ |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿El objeto es subconjunto de un espacio conocido, o es el espacio "completo"?**
- Subconjunto ($W\subseteq \mathbb{R}^n$, $W\subseteq P_n$, …) → pregunta de **SUBESPACIO** (2 cerraduras).
- Espacio completo (matrices, polinomios, funciones…) → pregunta de **ESPACIO VECTORIAL** (10 axiomas).

**Paso 1 — ¿Qué pide el enunciado?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "Demuestre que $W$ es un **subespacio**" | Verificar 2 cerraduras | $u+v\in W$ y $cu\in W$ | §2.A · §4.1 |
| "Demuestre que $V$ es un **espacio vectorial**" | Verificar 10 axiomas | $A_1\!-\!A_5$, $M_1\!-\!M_5$ | §2.C · §4.2 |
| "Demuestre que $\mathcal{B}$ es una **base**" | LI + genera (o usar $\dim$) | $\mathcal{B}$ LI y $\operatorname{Gen}(\mathcal{B})=V$ | §2.G · §4.3 |
| "Halle las **coordenadas** de $v$ en $\mathcal{B}$" | Resolver combinación lineal $= v$ | $v=\sum c_i v_i$, $[v]_{\mathcal{B}}$ | §2.H · §4.4 |
| "Halle $\dim V$ / $\dim W$" | Hallar una base y contar | $\dim =$ nº elementos de una base | §2.I · §4.5 |
| "¿Son **LI o LD**?" | Sistema homogéneo $c_1v_1+\dots=0$ | pivotes / determinante | §2.F · §4.6 |
| "¿**Genera** a $V$?" | Todo $v\in V$ es combinación lineal | $V=\operatorname{Gen}\{\dots\}$ | §2.E · §4.3 |
| "¿Este conjunto es subespacio?" (rápido) | ¿Contiene al $0$? | $0\notin W \Rightarrow$ no subespacio | §3 Caso 1 |

**Frases literales del profe → método**
- *"Es cerrado bajo la suma y bajo el producto por escalar"* → subespacio (2 condiciones).
- *"Siempre un subespacio debe contener el cero… porque alfa puede ser cero"* → verifica $0\in W$ primero.
- *"Son LI y generan todo el subespacio"* → base (2 condiciones).
- *"El determinante es diferente de cero… o llevarlo a Gauss-Jordan y ver que haya pivotes"* → LI.
- *"Para verificar que algo no es un subespacio, bastaría con una que no se cumpla"* → contraejemplo.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Subespacio de $\mathbb{R}^n$ (definición)
$V\subseteq\mathbb{R}^n$, $V\neq\varnothing$, es **subespacio** si:
1. $u,v\in V \Rightarrow u+v\in V$ (cerrado bajo la suma).
2. $c\in\mathbb{R},\ u\in V \Rightarrow cu\in V$ (cerrado bajo producto por escalar).

**🔤 Diccionario:** $V$ subconjunto candidato · $u,v$ vectores de $V$ · $c$ escalar real · $u+v$ suma · $cu$ producto por escalar · $\Rightarrow$ "entonces".

### B. Subespacio de un espacio vectorial (Teorema 4 — criterio)
$W\subseteq V$, $W\neq\varnothing$, es **subespacio** de $V$ $\Leftrightarrow$
1. $u,v\in W \Rightarrow u+v\in W$
2. $c\in\mathbb{R},\ u\in W \Rightarrow cu\in W$

> Solo las 2 cerraduras: $W$ **hereda** las demás propiedades por ser subconjunto de $V$.

**🔤 Diccionario:** $W$ subconjunto candidato · $V$ espacio vectorial "grande" · $\Leftrightarrow$ "si y solo si" (ssi).

### C. Espacio vectorial (10 axiomas)
$V\neq\varnothing$ con suma "$+$" y producto por escalar es **espacio vectorial real** si cumple:

| Suma | Multiplicación por escalar |
|---|---|
| $(A_1)$ $u+v\in V$ (cerradura) | $(M_1)$ $cu\in V$ (cerradura) |
| $(A_2)$ $u+v=v+u$ (conmutativa) | $(M_2)$ $c(u+v)=cu+cv$ (distributiva) |
| $(A_3)$ $(u+v)+w=u+(v+w)$ (asociativa) | $(M_3)$ $(c+d)u=cu+du$ (distributiva) |
| $(A_4)$ $\exists\,0:\ u+0=u$ (neutro) | $(M_4)$ $c(du)=(cd)u$ (asociativa mixta) |
| $(A_5)$ $\exists\,(-u):\ u+(-u)=0$ (opuesto) | $(M_5)$ $1u=u$ (neutro escalar) |

**🔤 Diccionario:** $u,v,w$ elementos de $V$ (vectores, matrices, polinomios, funciones…) · $c,d\in\mathbb{R}$ escalares · $0$ neutro (cero) de $V$ · $-u$ opuesto aditivo.

### D. Teorema 3 — propiedades básicas
$$0u=0,\qquad c\,0=0,\qquad cu=0 \Rightarrow (c=0 \text{ o } u=0),\qquad (-c)u=-(cu)$$

**🔤 Diccionario:** $0u$ escalar $0$ por vector · $c\,0$ escalar por vector cero · $cu=0$ producto nulo · $-(cu)$ opuesto del producto.

### E. Generador (Gen)
$$\operatorname{Gen}\{v_1,\dots,v_k\}=\{c_1v_1+\dots+c_kv_k\ :\ c_i\in\mathbb{R}\}$$
- **Teorema 1 / 5:** $\operatorname{Gen}\{v_1,\dots,v_k\}$ es subespacio (el **menor** que contiene a $\{v_1,\dots,v_k\}$).
- **Teorema 6:** si un $v_i$ es combinación lineal del resto, se elimina sin cambiar el generador.

**🔤 Diccionario:** $v_i$ vectores generadores · $c_i$ escalares (coeficientes) · combinación lineal = $\sum c_i v_i$.

### F. Independencia lineal (LI) / Dependencia (LD)
$\{v_1,\dots,v_n\}$ es **LI** $\Leftrightarrow$ la ecuación $c_1v_1+\dots+c_nv_n=0$ tiene **solo** la solución trivial $c_1=\dots=c_n=0$.
Es **LD** $\Leftrightarrow$ existe solución no trivial (algún $c_i\neq 0$).

- **Teorema 8:** contiene al $0$ $\Rightarrow$ LD · 2 vectores LD $\Leftrightarrow$ uno es múltiplo del otro · subconjunto de un LI es LI · sobreconjunto de un LD es LD.
- **Teorema 7:** LD $\Leftrightarrow$ algún vector es combinación lineal de los restantes.

**🔤 Diccionario:** $c_i$ incógnitas escalares · $0$ vector cero · trivial = todos los $c_i=0$.

### G. Base
$\mathcal{B}=\{v_1,\dots,v_k\}$ es **base** de $V\neq\{0\}$ $\Leftrightarrow$
1. $\mathcal{B}$ es **LI**, y
2. $\mathcal{B}$ **genera** a $V$ ($\operatorname{Gen}(\mathcal{B})=V$).

**Bases estándar:** $\mathbb{R}^n\to\{e_1,\dots,e_n\}$ · $P_n\to\{1,x,\dots,x^n\}$ · $M_{mn}\to\{E_{11},\dots,E_{mn}\}$ · $D_n\to\{E_{11},\dots,E_{nn}\}$.
**Convención:** la base del subespacio $\{0\}$ es $\varnothing$ (vacío).

**🔤 Diccionario:** $\mathcal{B}$ base (calligráfica) · $e_i$ vector con $1$ en la posición $i$ y $0$ en el resto · $E_{ij}$ matriz con $1$ en $(i,j)$ y $0$ en el resto.

### H. Coordenadas (Teorema 2 / 11 — unicidad)
Si $\mathcal{B}=\{v_1,\dots,v_k\}$ es base de $V$, para todo $v\in V$ existen escalares **únicos** $c_1,\dots,c_k$ con
$$v=c_1v_1+\dots+c_kv_k \quad\Rightarrow\quad [v]_{\mathcal{B}}=\begin{pmatrix}c_1\\ \vdots \\ c_k\end{pmatrix}$$
- En la **base estándar**, $[v]_{\mathcal{B}}=v$.

**🔤 Diccionario:** $[v]_{\mathcal{B}}$ vector de coordenadas de $v$ en $\mathcal{B}$ · $c_i$ coordenadas · únicos = quedan determinados (por ser LI).

### I. Dimensión
$$\dim V=\text{nº de elementos de una base de }V,\qquad \dim\{0\}=0$$
- **Teorema 13:** todas las bases de $V$ tienen el mismo nº de elementos.
- Valores: $\dim\mathbb{R}^n=n$ · $\dim P_n=n+1$ · $\dim M_{mn}=mn$ · $\dim P=\infty$ · $\dim F(\mathbb{R})=\infty$.
- **Teorema 14:** $S$ con $m$ vectores: LI $\Rightarrow m\le n$; genera $\Rightarrow m\ge n$.
- **Teorema 17:** $W\subseteq V \Rightarrow \dim W\le\dim V$; $\dim W=\dim V \Leftrightarrow W=V$.

**🔤 Diccionario:** $\dim$ dimensión · $n$ nº de elementos de una base (dimensión finita) · $m$ nº de vectores del conjunto $S$.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Triviales:** $\{0\}$ y $V$ siempre son subespacios. Los demás son subespacios **propios**.
- **Caso 1 — Contiene al cero:** todo subespacio contiene al $0$. Si $0\notin W$ $\Rightarrow$ $W$ **no** es subespacio.
- **Caso 2 — Recta:** recta por el origen $=\operatorname{Gen}\{u\}$ ($u\neq 0$) → subespacio. Recta que **no** pasa por el origen → **no** subespacio.
- **Caso 3 — Plano:** plano por el origen $=\operatorname{Gen}\{u,v\}$ ($u,v$ no colineales) → subespacio. Plano sin origen → **no** subespacio.
- **Caso 4 — Cero:** $\{0\}$ tiene base $\varnothing$ y $\dim\{0\}=0$.
- **Caso 5 — Invertibles:** las matrices invertibles **no** forman subespacio (la matriz cero no es invertible).
- **Caso 6 — Vector cero:** todo conjunto que contiene al vector $0$ es **LD**.
- **Caso 7 — Dos vectores:** 2 vectores son LD $\Leftrightarrow$ uno es múltiplo escalar del otro.
- **Caso 8 — Atajo de dimensión:** en espacio de $\dim n$, $n$ vectores LI $\Rightarrow$ base; $n$ vectores generadores $\Rightarrow$ base (basta 1 condición). ➕
- **Caso 9 — Subespacios de $\mathbb{R}^2$/$\mathbb{R}^3$:** $\mathbb{R}^2$: $\{0\}$, rectas por origen, $\mathbb{R}^2$. $\mathbb{R}^3$: $\{0\}$, rectas por origen, planos por origen, $\mathbb{R}^3$.
- **Caso 10 — Funciones:** $C(\mathbb{R})$ (continuas) es subespacio de $F(\mathbb{R})$: suma y múltiplo escalar de continuas es continua.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Verificar que $W$ es subespacio
1. Verificar $W\neq\varnothing$ (normalmente $0\in W$).
2. Tomar $u,v\in W$ arbitrarios y probar $u+v\in W$ (cerradura suma).
3. Tomar $u\in W$, $c\in\mathbb{R}$, y probar $cu\in W$ (cerradura escalar).

**Plantilla** (ortogonales a $a$ fijo, ej. 28):
$$W=\{u : a\cdot u=0\},\ a \text{ fijo en } \mathbb{R}^3$$

$$\begin{aligned}
u,v\in W &\Rightarrow a\cdot u=0,\ a\cdot v=0 &&\text{(definición de } W\text{)} \\
a\cdot(u+v) &= a\cdot u + a\cdot v = 0+0 = 0 &&\text{(producto punto distributivo)} \\
&\Rightarrow u+v\in W &&\text{(cerradura suma)} \\[2pt]
a\cdot(cu) &= c\,(a\cdot u)=c\cdot 0=0 &&\text{(producto punto + escalar)} \\
&\Rightarrow cu\in W &&\text{(cerradura escalar)}
\end{aligned}$$

### 4.2 Verificar que $V$ es espacio vectorial
1. Definir la suma "$+$" y el producto por escalar del espacio.
2. Verificar $A_1$–$A_5$ (suma).
3. Verificar $M_1$–$M_5$ (escalar).
> Para **subconjuntos** no se hace esto: solo las 2 cerraduras (§4.1).

### 4.3 Verificar que $\mathcal{B}$ es base
1. **LI:** resolver $c_1v_1+\dots+c_nv_n=0$ y concluir $c_i=0$ (matriz → determinante $\neq 0$, o Gauss-Jordan → $n$ pivotes).
2. **Genera:** todo $v\in V$ se escribe como combinación lineal de $\mathcal{B}$.
   - **Atajo (si $\dim V=n$ y hay $n$ vectores):** basta LI (o basta genera). ➕
3. Concluir: $\mathcal{B}$ es base.

**Plantilla** ($S=\{(1,0,0),(0,1,0)\}$):
- ¿Base de $\mathbb{R}^3$? **No**: no genera, porque $(0,0,1)\notin\operatorname{Gen}S$.
- ¿Base de $V=\{(x,y,0)\}$? **Sí**: LI y genera.
$$\alpha(1,0,0)+\beta(0,1,0)=(0,0,0)\Rightarrow\alpha=\beta=0\ \text{(LI)};\qquad (x,y,0)=x(1,0,0)+y(0,1,0)\ \text{(genera)}$$

### 4.4 Hallar coordenadas $[v]_{\mathcal{B}}$
1. Plantear $v=c_1v_1+\dots+c_kv_k$.
2. Igualar componente a componente (o resolver $Ac=v$ con $A$ = columnas de $\mathcal{B}$).
3. La solución única es $[v]_{\mathcal{B}}=(c_1,\dots,c_k)$.

**Plantilla** ($v=(4,0,-4)$, $\mathcal{B}=\{(1,1,-1),(0,1,2),(-2,1,0)\}$):
$$(4,0,-4)=2(1,1,-1)-1(0,1,2)-1(-2,1,0)\quad\Rightarrow\quad [v]_{\mathcal{B}}=\begin{pmatrix}2\\-1\\-1\end{pmatrix}$$

### 4.5 Hallar la dimensión
1. Encontrar una base (LI + genera).
2. Contar sus elementos $\Rightarrow \dim$.

**Plantilla:** $V=\operatorname{Gen}\{(1,1,1),(2,1,-1),(1,0,-2)\}$.
$$(1,0,-2)=(2,1,-1)-(1,1,1)\Rightarrow V=\operatorname{Gen}\{(1,1,1),(2,1,-1)\}$$
Son LI (no múltiplos) $\Rightarrow$ base con 2 elementos $\Rightarrow \dim V=2$.

### 4.6 Verificar LI / LD
1. Plantear $c_1v_1+\dots+c_nv_n=0$.
2. Resolver (Gauss-Jordan / determinante).
3. Solo trivial $\Rightarrow$ LI; existe no trivial $\Rightarrow$ LD.

**Plantilla** ($\{(1,0,0),(0,1,0)\}$):
$$\alpha(1,0,0)+\beta(0,1,0)=(\alpha,\beta,0)=(0,0,0)\Rightarrow\alpha=\beta=0\ \Rightarrow\ \text{LI}$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Verifiqué $0\in W$ antes de declarar "subespacio"?
- [ ] ¿Para "base" comprobé las 2 cosas (LI **y** genera), o usé el atajo de dimensión?
- [ ] ¿Para coordenadas confirmé unicidad (LI) y resolví el sistema?
- [ ] ¿Distinguí producto punto ($\cdot$) de producto por escalar (sin punto)?
- [ ] ¿$\dim\{0\}=0$ y base de $\{0\}=\varnothing$?
- [ ] ¿"No pasa por el origen" $\Rightarrow$ no es subespacio?
- [ ] ¿Matrices invertibles $\Rightarrow$ no subespacio (cero no invertible)?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
