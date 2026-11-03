# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 03/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `CONTABLES_SELECCION_Y_PRODUCTO-031126.md`
> - **Fecha de transcripción:** 03/11/2026 (`DDMMAA` = `031126`)
> - **Tema principal:** CONTABLES · FUNCIONES SELECTORAS (elección finita) · PRODUCTO CARTESIANO GENERALIZADO. Incluye el cierre de cardinales finitos: $\left\lvert B^{A}\right\rvert$, soporte de $A^{B}$ y carácter finito.
> - **Continuidad:** NO repite lo de `CARDINALIDAD_Y_FINITUD-291026` (equipotencia, dominancia, Cantor, punto fijo, Cantor–Bernstein, definición de finito y cardinal). Solo lo **cita**.
> - **Fuente:** transcripción de clase. Lo agregado (o corregido) por mí va marcado con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `CONTABLES_SELECCION_Y_PRODUCTO-031126` §2.F».

**📎 Prerrequisitos (de la cheatsheet anterior):** $A\approx B$ (equipotencia), $A\preccurlyeq B$ / $A\prec B$ (dominancia), $A$ finito $\iff\exists n\in\mathbb N:A\approx n$, $\lvert A\rvert$ = único $n$ con $A\approx n$, Cantor $A\prec\mathcal P(A)$, Cantor–Bernstein $\left(A\preccurlyeq B\wedge B\preccurlyeq A\Rightarrow A\approx B\right)$.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿El enunciado habla de cardinales numéricos ($n$, $\lvert A\rvert$, "$2^{4}$") o de infinitos?**
   - Números concretos → **§2.A / §2.B** (todo se prueba por inducción sobre el cardinal).
   - Infinitos → **§2.F / §2.G** (contable / enumerable / no contable).
2. **Paso 1 — ¿Aparece una función $F:A\to B$ que es sobreyectiva y alguien es finito?** → **§2.B** (sobre + finito $\Rightarrow$ dominancia; sobre + igual cardinal $\Rightarrow$ biyectiva).
3. **Paso 2 — ¿Hay que "escoger un elemento de cada conjunto" de una familia?** → **§2.D** (función selectora) y, si la familia es finita, el teorema de elección finita.
4. **Paso 3 — ¿Una colección cerrada bajo subconjuntos finitos?** → **§2.E** (carácter finito).
5. **Paso 4 — ¿Piden "contable", "enumerable", "no contable"?** → **§2.F** o **§2.G** según la meta.
6. **Paso 5 — ¿Un producto de muchos conjuntos?** → **§2.H** (producto generalizado) y su equivalencia con las funciones selectoras.

**Tabla de decisión:**

| Si el enunciado dice… | Herramienta | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "cuántas funciones van de $A$ en $B$", con $A,B$ finitos | **Cardinal de $B^{A}$** | $\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}$ | **§2.A** · §4.A |
| "$F$ es sobreyectiva", "$B$ es finito", "demuestre que $\lvert B\rvert\le\lvert A\rvert$" | **Sobre $\Rightarrow$ dominancia** | $F$ sobre $\wedge\ B$ finito $\Rightarrow B\preccurlyeq A$ | **§2.B** · §4.B |
| "$F$ sobreyectiva y $\lvert A\rvert=\lvert B\rvert$" | **Sobre + igual cardinal** | $F$ sobre $\Rightarrow F$ inyectiva | **§2.B** · §4.B |
| "$F:n\to m$ con $m<n$, naturales" | **No sobreyección** | $m\in n\Rightarrow F$ no es sobre | **§2.B** · §4.B |
| "orden total" + "finito" + "máximo / mínimo" | **Finito + orden total** | $A$ finito $\wedge$ orden total $\Rightarrow\exists\max,\exists\min$ | **§2.B** |
| "para toda función hay solo finitas entradas distintas de cero", "sucesiones que se anulan", "soporte" | **Soporte** | $\operatorname{sop}(f)=\{b: f(b)\neq\min A\}$ finito | **§2.C** · §4.C |
| "escoger un elemento de cada conjunto", "función selectora / de elección" | **Función selectora** | $g(A)\in A$ para todo $A\in\mathcal A$ | **§2.D** · §4.D |
| "familia finita de conjuntos no vacíos" | **Elección finita** | existe $g$ para toda familia finita | **§2.D** · §4.D |
| "$F$ sobreyectiva y $B$ finito, ¿hay inversa a la derecha?" | **Selectora sobre fibras** | $H(b)=g\left(F^{-1}(b)\right)$ | **§2.D** · §4.D |
| "todo subconjunto finito de $X$ está en $H$" | **Carácter finito** | $X\in H\iff\forall$ finito $Y\subseteq X:\ Y\in H$ | **§2.E** · §4.E |
| "dominado por $\mathbb N$", "contable", "numerable" | **Contable / enumerable** | $A\preccurlyeq\mathbb N$ / $A\approx\mathbb N$ | **§2.F** · §4.F |
| "contable e infinito" | **Contable infinito = enumerable** | $A$ contable $\wedge$ infinito $\Rightarrow A\approx\mathbb N$ | **§2.F** · §4.F |
| "$\mathbb N\times\mathbb N$", "$\mathbb Z$", "$\mathbb Q$", "unión de contables" | **Codificaciones numéricas** | $2^{n+1}3^{m+1}$; pares/impares | **§2.F** · §4.F |
| "$\mathcal P(\mathbb N)$", "$2^{\mathbb N}$", "$\mathbb R$", "no contable" | **No contables** | $\mathbb N\prec\mathcal P(\mathbb N)\approx2^{\mathbb N}\approx\mathbb R$ | **§2.G** · §4.G |
| "producto de una familia $\{A_i\}_{i\in I}$" | **Producto generalizado** | $\prod_{i\in I}A_i=\{f: I\to\bigcup A_i \mid f(i)\in A_i\}$ | **§2.H** · §4.H |

**Frases literales del profe → método:**

- «Ese problema cero aquí esto es uno.» → $\left\lvert\emptyset^{\emptyset}\right\rvert=1$: la única función $\emptyset\to\emptyset$ es la función vacía (base de la inducción de §2.A).
- «Por eso es que le quita la base de cero.» → el teorema $\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}$ se enuncia con $B\neq\emptyset$ y se discute $0^{0}$ aparte.
- «Recuerde que hay indexaciones que no son inyectivas e indexaciones que sí son inyectivas.» → para que los bloques $H_{i}$ sean **disjuntos** hace falta que la enumeración sea inyectiva.
- «La cantidad de entradas que son distintas de cero tiene que ser finita y el resto los manda a cero.» → definición operativa de soporte.
- «Lo único que le pido es que lo que esté dentro de la colección no sea vacío.» → hipótesis exacta de la función selectora ($\mathcal A\setminus\{\emptyset\}$, nunca $\mathcal A$ con elementos vacíos).
- «La unión enumerable de enumerables: ese truco ya no le funciona, porque el producto de infinitos primos se sale de los naturales.» → por qué el paso de finito a infinito **no** es gratis (ahí entra la elección).
- «Todavía no hemos definido cardinal para infinitos: solo equipotencia.» → nunca escribas "el cardinal de $\mathbb R$".

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Cardinal de $B^{A}$ para conjuntos finitos

**Teorema.** Si $A$ y $B$ son finitos y $B\neq\emptyset$:

$$
\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}
$$

**Los tres casos límite (esto es lo que se pregunta en parcial):**

| Caso | Quién es $B^{A}$ | Cardinal |
|---|---|---|
| $A=\emptyset$ (cualquier $B$) | $\emptyset^{\emptyset}=\{\emptyset\}$: **una sola** función | $1=\lvert B\rvert^{0}$ (aquí $0^{0}=1$) |
| $B=\emptyset$, $A\neq\emptyset$ | $\emptyset^{A}=\emptyset$ | $0=0^{\lvert A\rvert}$ |
| $B=\emptyset$, $A=\emptyset$ | $\{\emptyset\}$ | $1=0^{0}$ |

**Corolario inmediato:** $\left\lvert\mathcal P(A)\right\rvert=2^{\lvert A\rvert}$ para $A$ finito, porque $\mathcal P(A)\approx2^{A}$ (§2.C de la cheatsheet anterior).

> **🔤 Diccionario:**
> - $B^{A}$: conjunto de **todas** las funciones $f:A\to B$ (no confundir con la potencia numérica).
> - $\lvert A\rvert,\lvert B\rvert$: cardinales de $A$ y $B$ (solo existen si son finitos).
> - $\emptyset^{\emptyset}=\{\emptyset\}$: la **función vacía** es la única función con dominio $\emptyset$; su cardinal es $1$ y por eso $0^{0}=1$ **en este contexto**.
> - $0^{\lvert A\rvert}$: si el codominio es vacío y el dominio no, no hay ninguna función posible ($0$).

---

### B. Cierre de los cardinales finitos (los cinco hechos que se usan después)

| # | Enunciado | Idea de la prueba |
|---|---|---|
| **B1** | Todo conjunto finito se puede **bien ordenar** | $A\approx n$ transporta el buen orden de $n$ |
| **B2** | Si $F:A\to B$ es **sobre** y $B$ es finito, entonces $B\preccurlyeq A$ | se enumeran los elementos de $B$ y se escoge **una** preimagen de cada uno (aquí se usa §2.D) |
| **B3** | Si $m,n\in\mathbb{N}$ con $m\in n$ (es decir $m<n$) y $F:m\to n$, entonces $F$ **no** es sobreyectiva | si fuera sobre, B2 daría $n\preccurlyeq m$; con la inclusión $m\preccurlyeq n$ y Cantor–Bernstein saldría $m\approx n$, contra "ningún natural es equipotente con un subconjunto propio" |
| **B4** | Si $\lvert A\rvert=\lvert B\rvert$ (finitos) y $F:A\to B$ es **sobre**, entonces $F$ es **inyectiva** (y biyectiva) | si $F(a)=F(c)$ con $a\neq c$, $F$ restringida a $A\setminus\{a\}$ sigue siendo sobre, y $\left\lvert A\setminus\{a\}\right\rvert=\lvert A\rvert-1$; componiendo con las biyecciones a los cardinales se obtiene una sobreyección de un natural **menor** sobre uno **mayor**, contra B3 |
| **B5** | Si $A$ es finito y $F:A\to B$ es cualquier función, entonces $f[A]$ es finito y $\lvert f[A]\rvert\le\lvert A\rvert$ | $A\approx n$, y $f$ compuesta con esa biyección es una sucesión finita; el rango de una sucesión finita de largo $n$ tiene $\le n$ elementos |

**Consecuencia adicional (ejercicio de clase):**

$$
A\ \text{infinito}\ \Longrightarrow\ n\preccurlyeq A\ \text{para todo } n\in\mathbb{N}
$$

> **🔤 Diccionario:**
> - bien ordenado: todo subconjunto no vacío tiene **mínimo**.
> - $A\setminus\{a\}$: $A$ sin el elemento $a$; si $A$ es finito, su cardinal es $\lvert A\rvert-1$.
> - $f[A]$: imagen directa (rango) de $F$.
> - $m\in n$: para naturales de von Neumann equivale a $m<n$.
> - "sobre" = sobreyectiva; "inyectiva" = uno a uno.

---

### C. Soporte de un conjunto de funciones y su buen orden

Sea $A$ con **mínimo** $\min A$ en su orden y $B$ bien ordenado. Para $f\in A^{B}$:

$$
\operatorname{sop}(f)=\left\{\,b\in B \;\middle|\; f(b)\neq\min A\,\right\}
\qquad\qquad
\operatorname{Sop}\left(A^{B}\right)=\left\{\,f\in A^{B} \;\middle|\; \operatorname{sop}(f)\ \text{es finito}\,\right\}
$$

**Orden del soporte** (para $f\neq g$):

$$
f<g \iff f(b)<_{A}g(b),\qquad b=\max\left\{\,c\in B \;\middle|\; f(c)\neq g(c)\,\right\}
$$

**Hechos:**
1. $\{c\in B: f(c)\neq g(c)\}$ es finito (es subconjunto de $\operatorname{sop}(f)\cup\operatorname{sop}(g)$), y como $B$ está bien ordenado y el conjunto es **finito**, ese conjunto **tiene máximo**; por eso el orden está bien definido.
2. El orden así definido es **total** en $\operatorname{Sop}(A^{B})$: si $f\neq g$, el punto máximo donde difieren decide.
3. $\operatorname{Sop}(A^{B})$ con ese orden es un **buen orden**.

> **🔤 Diccionario:**
> - $\min A$: mínimo de $A$ (existe si $A$ está bien ordenado o si $A=\mathbb N$ y el mínimo es $0$).
> - $\operatorname{sop}(f)$: **soporte** de $f$: las entradas donde $f$ **no** vale el mínimo.
> - "de soporte finito": solo finitas entradas son distintas del mínimo; el resto cae en el mínimo.
> - $b$: el punto **más grande** (en el orden de $B$) donde $f$ y $g$ difieren; allí se compara primero.
> - El orden compara "por la cola más significativa", igual que comparar decimales de derecha a izquierda.

---

### D. Función selectora y elección finita

**Definición.** Sea $\mathcal{A}$ una colección de conjuntos. Una **función selectora** de $\mathcal{A}$ es

$$
g:\mathcal{A}\setminus\{\emptyset\}\longrightarrow\bigcup\mathcal{A}
\qquad\text{tal que}\qquad
g(A)\in A\ \ \text{para todo } A\in\mathcal{A}\setminus\{\emptyset\}
$$

**Teorema (elección finita).** Si $\mathcal{A}$ es **finito**, existe función selectora. En particular, si **ningún** elemento de $\mathcal{A}$ es vacío, la selectora está definida sobre todo $\mathcal{A}$.

**Aplicación (inversa a la derecha).** Si $F:A\to B$ es sobreyectiva y $B$ es finito, existe $H:B\to A$ con $F\circ H=\mathrm{id}_{B}$:

$$
H(b)=g\left(F^{-1}(b)\right)
$$

donde $g$ es una selectora de la familia finita de fibras $\left\{F^{-1}(b)\right\}_{b\in B}$.

**Nombres según el tamaño de la familia:**

| Tamaño de $\mathcal{A}$ | Nombre del principio |
|---|---|
| finito | **elección finita** (teorema, no axioma) |
| enumerable ($\approx\mathbb N$) | elección **numerable** |
| arbitrario | **Axioma de Elección** |

> **🔤 Diccionario:**
> - $\mathcal{A}$: colección de conjuntos (un conjunto cuyos elementos son conjuntos).
> - $\bigcup\mathcal{A}$: unión de todos los elementos de $\mathcal{A}$.
> - $g(A)\in A$: el elemento escogido **pertenece** al conjunto del que se escoge (esta es toda la condición).
> - $\mathcal{A}\setminus\{\emptyset\}$: se **quita el vacío** de la colección, porque del vacío no se puede escoger nada.
> - $F^{-1}(b)=\{a\in A: F(a)=b\}$: **fibra** (preimagen) de $b$; es no vacía porque $F$ es sobre.
> - $\mathrm{id}_{B}$: identidad en $B$; $F\circ H=\mathrm{id}_{B}$ es la definición de **inversa a derecha**.

---

### E. Conjuntos de carácter finito

**Definición.** Una colección $H$ es de **carácter finito** si

$$
A\in H \iff \text{todo subconjunto finito de } A \text{ pertenece a } H
$$

**Ejemplo trivial:** $H=\mathcal{P}(X)$ para cualquier $X$ (todo subconjunto de un subconjunto sigue siendo subconjunto).

**Teorema.** Si $H$ es de carácter finito y $\mathcal{F}\subseteq H$ es una **cadena** bajo $\subseteq$ (cualesquiera dos de sus miembros son comparables), entonces

$$
\bigcup\mathcal{F}\in H
$$

> **🔤 Diccionario:**
> - $H$: colección de conjuntos (un "conjunto de conjuntos" con una propiedad de cerradura).
> - $A\in H$: el **conjunto** $A$ es un elemento de la colección $H$.
> - cadena: $\forall X,Y\in\mathcal{F}$: $X\subseteq Y$ o $Y\subseteq X$.
> - $\bigcup\mathcal{F}$: unión de todos los miembros de la cadena.
> - La definición es un **si y solo si**: se usa en las **dos** direcciones (de $A$ a sus finitos y de los finitos a $A$).

---

### F. Contables y enumerables

**Definiciones.**

$$
A\ \text{contable} \iff A\preccurlyeq\mathbb{N}
\qquad\qquad
A\ \text{enumerable} \iff A\approx\mathbb{N}
\qquad\qquad
A\ \text{no contable} \iff A\not\preccurlyeq\mathbb{N}
$$

**Los resultados de la clase:**

| # | Enunciado |
|---|---|
| **F1** | $A$ contable e **infinito** $\Longrightarrow A$ enumerable. Por lo tanto: **contable = finito o enumerable** |
| **F2** | Si $A\preccurlyeq B$ y $B$ es contable, entonces $A$ es contable (transitividad) |
| **F3** | Si $F:A\to B$ es función y $A$ es contable, entonces $f[A]$ es contable |
| **F4** | Si $B\subseteq A$ y $B$ es enumerable, entonces $A$ es **infinito** |
| **F5** | Unión de dos contables es contable; por inducción, unión **finita** de contables es contable |
| **F6** | Si $A$ es contable, entonces $A^{n}$ es contable para todo $n\in\mathbb{N}$ (sucesiones finitas de $A$) |
| **F7** | $A$ enumerable $\Longrightarrow A^{n}$ enumerable (ejercicio) |
| **F8** | Unión **enumerable** de enumerables es contable `➕` (usa elección numerable; el truco de primos **no** sirve, ver §3.4) |
| **F9** `➕` | Si $A\preccurlyeq\mathbb{N}$ y $B\preccurlyeq\mathbb{N}$, entonces $A\times B\preccurlyeq\mathbb{N}$: **producto de dos contables es contable**. Prueba: con $f:A\to\mathbb{N}$ y $h:B\to\mathbb{N}$ inyectivas, $(a,b)\mapsto\left(f(a),h(b)\right)$ es inyectiva en $\mathbb{N}\times\mathbb{N}\approx\mathbb{N}$ |
| **F10** `➕` | $\mathbb{N}\preccurlyeq\mathbb{Z}$ y $\mathbb{N}\preccurlyeq\mathbb{Q}$: la **inclusión** $n\mapsto n$ es inyectiva (§2.B, propiedad 2). Es el eslabón que falta para probar que $\mathbb{Z}$ y $\mathbb{Q}$ son **infinitos** |

**Las tres codificaciones que hay que saber de memoria:**

$$
\mathbb{N}\times\mathbb{N}\approx\mathbb{N}
\qquad\text{con}\qquad
(n,m)\longmapsto 2^{\,n+1}\,3^{\,m+1}
$$

**El par completo de inyecciones (Cantor–Bernstein):**

$$
\iota:\mathbb{N}\to\mathbb{N}\times\mathbb{N},\quad \iota(n)=(n,0)
\qquad\qquad
\Psi:\mathbb{N}\times\mathbb{N}\to\mathbb{N},\quad \Psi(n,m)=2^{\,n+1}3^{\,m+1}
$$

$$
\mathbb{N}\preccurlyeq\mathbb{N}\times\mathbb{N}\ \wedge\ \mathbb{N}\times\mathbb{N}\preccurlyeq\mathbb{N}
\ \Longrightarrow\ \mathbb{N}\times\mathbb{N}\approx\mathbb{N}
\qquad\left(\text{Cantor–Bernstein, §2.D de } -291026\right)
$$

**🧠 Por qué la TFA es imprescindible aquí.** En el número $2^{\,a+1}3^{\,b+1}$ los exponentes **no se ven**. La TFA es el único instrumento que permite **leerlos**:

$$
v_{p}(n):=\text{exponente del primo } p \text{ en la factorización de } n
\qquad\qquad
n=m\iff v_{p}(n)=v_{p}(m)\ \ \forall\,p\ \text{primo}
$$

Como los dos números solo tienen primos $2$ y $3$, basta comparar $v_{2}$ y $v_{3}$. Sin TFA, dos parejas distintas podrían dar el mismo producto y $\Psi$ dejaría de ser inyectiva.

`➕` **Nota sobre el $+1$:** el $+1$ es una **convención** de la clase (hace que la imagen evite el $1$ y que la fórmula sirva aunque $\mathbb{N}$ se tome empezando en $1$). **No** es necesario para la inyectividad: $(n,m)\mapsto2^{\,n}3^{\,m}$ también es inyectiva por TFA. Si copias la fórmula del tablero, mantenla; si usas la otra, la prueba es idéntica.

$$
\mathbb{Z}\ \text{enumerable},\qquad
\mathbb{Q}\ \text{enumerable}
$$

**🧠 De dónde sale cada eslabón:**

| Afirmación | Justificación |
|---|---|
| $\mathbb{Z}=\pi\left[\mathbb{N}\times\mathbb{N}\right]$ | en el curso $\mathbb{Z}=(\mathbb{N}\times\mathbb{N})/\!\sim$ (clases de diferencia) y la proyección $\pi$ es **sobreyectiva** |
| $\mathbb{Z}$ es contable | **F3** aplicado a $\pi$ |
| $\mathbb{N}\subseteq\mathbb{Z}$ (la clase de $(n,0)$ **es** el entero $n$) | por eso la inclusión $n\mapsto n$ es inyectiva ⇒ $\mathbb{N}\preccurlyeq\mathbb{Z}$ (**F10**) |
| $\mathbb{Z}$ es enumerable | **F1**: contable + infinito (infinito porque $\mathbb{N}\preccurlyeq\mathbb{Z}$) |
| $\mathbb{Q}\preccurlyeq\mathbb{Z}\times\mathbb{Z}$ | fracción **irreducible con denominador positivo**: $q\mapsto(p,r)$, inyectiva por unicidad de esa representación |
| $\mathbb{Q}$ es enumerable | **F9** + (a) + **F1** |

$$
A\cup B\ \text{contable}:\quad
x\in A\mapsto 2f(x),\qquad
x\in B\setminus A\mapsto 2g(x)+1
$$

> **🔤 Diccionario:**
> - contable: dominado por $\mathbb N$ (cabe **dentro** de $\mathbb N$).
> - enumerable: equipotente con $\mathbb N$ (se puede **listar** uno a uno, sin repetir ni dejar huecos).
> - no contable: **ninguna** inyección hacia $\mathbb N$.
> - $2^{n+1}3^{m+1}$: codifica la pareja $(n,m)$ como un natural; es inyectiva por **unicidad de la factorización en primos**.
> - $2f(x)$ y $2g(x)+1$: manda $A$ a los **pares** y $B$ a los **impares**, para que no se crucen.
> - $A^{n}$: funciones $n\to A$, es decir, sucesiones finitas de largo $n$ con valores en $A$.

---

### G. Conjuntos no contables y la cadena de $\mathbb R$

$$
\mathbb{N}\prec\mathcal{P}(\mathbb{N})\approx2^{\mathbb{N}}\approx\mathbb{R}
$$

**Itinerario de la cadena (todo lo que hay que escribir):**

1. **Cantor:** $\mathbb{N}\prec\mathcal{P}(\mathbb{N})$ (cheatsheet anterior §2.C). Si $\mathcal P(\mathbb N)$ fuera contable, $\mathbb N$ dominaría a $\mathcal P(\mathbb N)$, contradiciendo la dominancia estricta.
2. **$2^{\mathbb{N}}\approx\mathcal{P}(\mathbb{N})$** por la función característica (cheatsheet anterior §2.C). Luego $2^{\mathbb{N}}$ es **no contable**.
3. **$\mathbb{R}\preccurlyeq\mathcal{P}(\mathbb{N})$:** en el curso los reales son cortaduras de Dedekind, es decir subconjuntos de $\mathbb{Q}$; así $\mathbb{R}\preccurlyeq\mathcal{P}(\mathbb{Q})\approx\mathcal{P}(\mathbb{N})$ (porque $\mathbb{Q}\approx\mathbb{N}$, y $A\approx B\Rightarrow\mathcal{P}(A)\approx\mathcal{P}(B)$ `➕`).
4. **$2^{\mathbb{N}}\preccurlyeq\mathbb{R}$:** la inyección es "$s\mapsto$ el real cuya expansión ternaria es $0{,}s(0)s(1)s(2)\dots$" con dígitos $0$ y $1$ solamente `➕` (en base $2$ **no** es inyectiva: $0{,}1000\dots=0{,}0111\dots$, que es lo que advirtió el profe).
5. **Cantor–Bernstein** cierra: $2^{\mathbb{N}}\approx\mathbb{R}$ y todo lo anterior coincide.
6. **Intervalos:** $\mathbb{R}\approx(0,1)\approx[0,1]\approx$ cualquier intervalo no degenerado.
7. **Irracionales:** $\mathbb{R}\approx\mathbb{R}\setminus\mathbb{Q}$ `➕` (inyección $x\mapsto x+\sqrt{2}$ de $\mathbb{R}$ en los irracionales y la inclusión al revés; Cantor–Bernstein).
8. **$\mathbb{N}^{\mathbb{N}}\approx\mathcal{P}(\mathbb{N})$** `➕`: $\mathcal{P}(\mathbb{N})\approx2^{\mathbb{N}}\preccurlyeq\mathbb{N}^{\mathbb{N}}$ (toda función a $\{0,1\}$ es función a $\mathbb N$), y $\mathbb{N}^{\mathbb{N}}\preccurlyeq\mathcal{P}(\mathbb{N}\times\mathbb{N})\approx\mathcal{P}(\mathbb{N})$ codificando $f\mapsto\left\{\left(n,\ \prod_{i\le n}p_{i}^{\,f(i)+1}\right) : n\in\mathbb{N}\right\}$ (los productos **parciales**, porque el producto infinito se sale de $\mathbb N$).

> **🔤 Diccionario:**
> - $2^{\mathbb{N}}$: todas las **sucesiones de ceros y unos** (funciones $\mathbb N\to\{0,1\}$).
> - $\mathcal{P}(\mathbb{N})$: todos los subconjuntos de $\mathbb N$.
> - cortadura de Dedekind: representación de un real como un subconjunto de $\mathbb{Q}$; por eso $\mathbb{R}\preccurlyeq\mathcal{P}(\mathbb{Q})$.
> - expansión ternaria: escritura en base $3$; con dígitos $0,1$ cada sucesión da un real y codificaciones distintas dan reales distintos.
> - $p_{i}$: el $i$-ésimo primo; los productos parciales deciden $f(0),\dots,f(n)$ de una vez.
> - No existe "el cardinal de $\mathbb R$" en este curso: solo $X\approx Y$ y $X\preccurlyeq Y$.

---

### H. Producto cartesiano generalizado

**Definición (familia indexada).** Dada una familia $\{A_{i}\}_{i\in I}$:

$$
\prod_{i\in I}A_{i}=\left\{\,f:I\to\bigcup_{i\in I}A_{i}\ \middle|\ f(i)\in A_{i}\ \ \text{para todo } i\in I\,\right\}
$$

**Casos que se preguntan:**

| Situación | Producto | Cardinal (si $I$ es finito) |
|---|---|---|
| $I=\emptyset$ | $\prod_{i\in\emptyset}A_{i}=\{\emptyset\}$ (solo la función vacía) | $1$ |
| algún $A_{j}=\emptyset$ | $\emptyset$ | $0$ |
| todos $A_{i}\neq\emptyset$ | $\neq\emptyset$ **solo** con elección | $\prod_{i\in I}\lvert A_{i}\rvert$ |

**Teoremas:**

$$
\prod_{i\in I}A_{i}=\emptyset \iff \exists\,j\in I:\ A_{j}=\emptyset
$$

$$
\prod_{i\in\{0,\dots,n-1\}}A_{i}\ \approx\ A_{0}\times A_{1}\times\cdots\times A_{n-1}\qquad(n\ge2)
$$

$$
\left\{\text{funciones selectoras de }\{A_{i}\}_{i\in I}\right\}\ \approx\ \prod_{i\in I}A_{i}
$$

> **🔤 Diccionario:**
> - $I$: conjunto de **índices**; la indexación $i\mapsto A_{i}$ **no** tiene por qué ser inyectiva (pueden repetirse conjuntos).
> - $\prod_{i\in I}A_{i}$: conjunto de **funciones** que escogen un elemento de cada $A_{i}$.
> - $f(i)\in A_{i}$: la condición que hace la escogencia **coherente** con la familia.
> - La dirección "$\Longleftarrow$" del primer teorema es inmediata; la otra es equivalente al Axioma de Elección.
> - Un elemento de $\prod$ **no** es un par ordenado: es una función. $(x,y)$ y $\{(0,x),(1,y)\}$ son **objetos distintos** y solo están en biyección.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Los tres tamaños de lo "pequeño"

| Concepto | Definición | Se prueba con | Ejemplo |
|---|---|---|---|
| **finito** | $A\approx n$ para algún $n\in\mathbb{N}$ | enumerar y contar | $\{a,b,c\}$, $\mathcal{P}(\{1,2\})$ |
| **contable** | $A\preccurlyeq\mathbb{N}$ | encontrar **una inyección** hacia $\mathbb N$ | $\mathbb Z$, $\mathbb Q$, $\mathbb N\times\mathbb N$ |
| **enumerable** | $A\approx\mathbb{N}$ | inyección **y** que no sea finito (F1) | $\mathbb Q$, $\mathbb Z$, $\mathbb N\times\mathbb N$ |
| **no contable** | $A\not\preccurlyeq\mathbb{N}$ | contradecir la dominancia por $\mathbb N$ (Cantor) | $\mathcal{P}(\mathbb N)$, $\mathbb R$ |

**Regla:** contable = finito **o** enumerable (F1). Nunca digas "contable" queriendo decir "enumerable".

### 3.2 Reglas de bolsillo

1. **$\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}$ exige $B\neq\emptyset$**, o manejar aparte el caso $A=\emptyset$ con $0^{0}=1$. Por eso el profe "le quita la base de cero".
2. **Sobre no es inyectiva en general**, pero sí lo es cuando $\lvert A\rvert=\lvert B\rvert$ y son finitos (B4). En infinitos esto **falla** (el sucesor $\mathbb N\to\mathbb N$ es inyectivo y no sobre).
3. **B3 es la versión finita de "no se puede meter $n+1$ elementos en $n$".** Se usa siempre por contradicción.
4. **El truco de los primos funciona para un número finito de factores.** Con infinitos factores el producto se sale de $\mathbb N$; por eso la unión enumerable de enumerables necesita elección (§3.4).
5. **Para probar que algo es enumerable:** primero contable (inyección a $\mathbb N$), después "no es finito" (porque contiene una copia de $\mathbb N$).
6. **Para probar que algo es no contable:** supón una inyección $A\to\mathbb N$, compón con biyecciones hasta obtener una biyección $\mathbb N\to\mathcal P(\mathbb N)$, y contradice a Cantor.
7. **El vacío se quita, no se asume.** La función selectora vive en $\mathcal A\setminus\{\emptyset\}$; si algún miembro es vacío, la selectora **no existe**.
8. **La elección finita es teorema; la infinita es axioma.** El enunciado del teorema de elección finita **no** menciona axiomas: se prueba por inducción.
9. **Carácter finito se usa en las dos direcciones:** de $X\in H$ hacia sus subconjuntos finitos, y de "todos los finitos están" hacia $X\in H$. En el teorema de la cadena se usan ambas.
10. **Soporte: la comparación empieza por el punto más grande donde difieren.** Ese punto existe porque el conjunto de diferencias es finito y $B$ está bien ordenado.
11. **$I=\emptyset$ en un producto da $1$ elemento, no $0$.** Es el mismo fenómeno que $0^{0}=1$: una sola función vacía.
12. **Un elemento de $\prod_{i\in I}A_i$ es una función**, no una tupla escrita con paréntesis. La tupla es la notación cómoda de esa función.

### 3.3 Los casos límite del producto generalizado

| Familia | Producto | Por qué |
|---|---|---|
| $A_{i}=\mathbb N$, $I$ finito | $\emptyset$-nunca, tiene elementos | hay al menos una elección posible |
| algún $A_{j}=\emptyset$ | $\emptyset$ | ninguna $f$ puede cumplir $f(j)\in\emptyset$ |
| $I=\emptyset$ | $\{\emptyset\}$ | la condición es vacía, la función vacía la cumple |

### 3.4 Dónde se rompe el paso a infinito

| Objeto | Finito | Enumerable (infinito) |
|---|---|---|
| Elección | **teorema** (inducción) | **axioma** (elección numerable) |
| Unión | unión finita de contables es contable | unión enumerable de enumerables: contable **con** elección |
| Codificación con primos | funciona ($p_{0}^{a_{0}+1}\cdots p_{n-1}^{a_{n-1}+1}$) | **no** funciona (producto infinito) |
| $\prod_{i\in I}A_{i}\neq\emptyset$ con todos $A_{i}\neq\emptyset$ | se prueba | es el **Axioma de Elección** |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Probar $\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}$ (finitos)

1. **Inducir sobre $m=\lvert A\rvert$**, dejando $B$ fijo.
2. **Base $m=0$:** $A=\emptyset$, $B^{\emptyset}=\{\emptyset\}$, luego el cardinal es $1=\lvert B\rvert^{0}$.
3. **Paso:** $A$ con $\lvert A\rvert=m+1$; fijar $a_{0}\in A$ y $D=A\setminus\{a_{0}\}$ (con $\lvert D\rvert=m$).
4. **Partir** $B^{A}$ en los bloques $H_{i}=\left\{f: f(a_{0})=b_{i}\right\}$, uno por cada $b_{i}\in B$.
5. **Verificar** que los $H_{i}$ son dos a dos **disjuntos** y que su unión es $B^{A}$ (aquí se usa que la enumeración de $B$ es inyectiva).
6. **Biyección** $H_{i}\approx B^{D}$ por restricción $f\mapsto f\!\restriction\!D$.
7. **Sumar:** $\left\lvert B^{A}\right\rvert=\sum_{i=1}^{\lvert B\rvert}\lvert B\rvert^{m}=\lvert B\rvert\cdot\lvert B\rvert^{m}=\lvert B\rvert^{m+1}$.

**Plantilla:** $A=\{0,1\}$, $B=\{0,1,2\}$. Bloques por el valor en $0$: tres bloques de $3^{1}=3$ funciones cada uno; total $3\cdot3=9=3^{2}$. ✔️

### B. Usar sobreyectividad con conjuntos finitos

1. **Identificar** quién es finito (dominio o codominio).
2. **Si $B$ finito y $F$ sobre** $\Rightarrow$ construir la selectora sobre las fibras y deducir $B\preccurlyeq A$ (B2).
3. **Si además $\lvert A\rvert=\lvert B\rvert$**, concluir inyectividad (B4) por contradicción: quitar un elemento repetido y aplicar B3.
4. **Verificar** que las dos dominancias no se contradicen con B3.

**Plantilla:** $F:3\to\{x,y,z\}$ sobre. Como $\lvert B\rvert=3=\lvert A\rvert$, B4 dice que $F$ es inyectiva; luego $F$ es biyectiva y hay $3!=6$ funciones así.

### C. Decidir si una función está en el soporte

1. **Identificar** $\min A$ (en $\mathbb N$ es $0$).
2. **Calcular** $\operatorname{sop}(f)=\{b: f(b)\neq\min A\}$.
3. **Decidir** si ese conjunto es finito.
4. **Comparar** dos funciones del soporte por el máximo punto de diferencia.

**Plantilla:** $\mathbb N^{\mathbb N}$ con $\min\mathbb N=0$. La constante $1$ no está en el soporte (su soporte es todo $\mathbb N$); la función $n\mapsto n$ tampoco; la función cero sí (soporte $\emptyset$); $f(3)=1$ y $f=0$ en el resto sí (soporte $\{3\}$).

### D. Construir una función selectora

1. **Verificar la hipótesis:** la familia $\mathcal A$ es finita y se trabaja en $\mathcal A\setminus\{\emptyset\}$.
2. **Inducir sobre $\lvert\mathcal A\rvert$.** Base: $\mathcal A\setminus\{\emptyset\}=\emptyset$ ⇒ selectora = función vacía.
3. **Paso:** si $\mathcal A=\{\emptyset\}$ es el caso vacío; si no, existe $b\in\mathcal A$ **no vacío**; escoger $k\in b$; aplicar la hipótesis inductiva a $\mathcal A\setminus\{b\}$.
4. **Pegar:** $g=f\cup\{(b,k)\}$; dominios disjuntos ⇒ es función; cumple $g(A)\in A$ por los dos lados.
5. **Usarla** cuando haga falta escoger: definir el objeto con $g$ y **verificar** la propiedad que se necesita.

**Plantilla:** $F:\{1,2,3\}\to\{x,y\}$ sobre. Fibras: $F^{-1}(x)$, $F^{-1}(y)$, ambas no vacías. Selectora $g$ escoge un representante de cada fibra; $H(x)=g(F^{-1}(x))$, $H(y)=g(F^{-1}(y))$, y $F(H(x))=x$, $F(H(y))=y$: inversa a la derecha. ✔️

### E. Probar que la unión de una cadena está en $H$

1. **Tesis a transformar:** $\bigcup\mathcal F\in H$. Por carácter finito, basta probar que **todo subconjunto finito** de $\bigcup\mathcal F$ está en $H$.
2. **Tomar** $X\subseteq\bigcup\mathcal F$ finito, $\lvert X\rvert=n$, con $X=\{a_{0},\dots,a_{n-1}\}$.
3. **Para cada $i$**, el conjunto $H_{i}=\{F\in\mathcal F: a_{i}\in F\}$ es **no vacío** (porque $a_{i}$ está en la unión) y hay solo $n$ de ellos.
4. **Selectora** sobre $\{H_{0},\dots,H_{n-1}\}$: se obtienen $G_{i}\in\mathcal F$ con $a_{i}\in G_{i}$.
5. **Máximo de la cadena finita:** $\{G_{0},\dots,G_{n-1}\}$ está en una cadena, luego tiene máximo $K$ (finito + total ⇒ hay máximo).
6. **Concluir:** $X\subseteq K$, $K\in\mathcal F\subseteq H$, y como $H$ es de carácter finito, todo subconjunto finito de $K$ está en $H$; en particular $X\in H$.
7. **Cerrar** con la otra dirección del carácter finito: $\bigcup\mathcal F\in H$.

**Plantilla:** $H=\mathcal P(\mathbb N)$, $\mathcal F$ una cadena de subconjuntos. Cualquier $X$ finito contenido en $\bigcup\mathcal F$ está contenido en algún miembro (paso 5), luego $X\in H$; así $\bigcup\mathcal F\in H$. ✔️

### F. Probar que un conjunto es contable / enumerable

1. **Para contable:** construir una **inyección** $A\to\mathbb N$ (o hacia algo ya contable, y usar F2).
2. **Reutilizar** las codificaciones: $2^{n+1}3^{m+1}$ para parejas; pares/impares para uniones; composición para productos.
3. **Para enumerable:** probar contable **y** que $A$ es infinito (o contener un enumerable, F4).
4. **Para sucesiones finitas:** inducir en $n$ usando $A^{n+1}\approx A^{n}\times A$ y que el producto de contables es contable.
5. **Verificar** que la función construida es realmente inyectiva (el punto que siempre se salta).

**Plantilla A — $\mathbb{N}\times\mathbb{N}\approx\mathbb{N}$ (dos inyecciones + Cantor–Bernstein):**

1. $\iota(n)=(n,0)$ es inyectiva $\Rightarrow \mathbb{N}\preccurlyeq\mathbb{N}\times\mathbb{N}$.
2. $\Psi(n,m)=2^{\,n+1}3^{\,m+1}$ es inyectiva, **leyendo los exponentes con la TFA** $\Rightarrow \mathbb{N}\times\mathbb{N}\preccurlyeq\mathbb{N}$.
3. Cantor–Bernstein cierra $\Rightarrow \mathbb{N}\times\mathbb{N}\approx\mathbb{N}$.

⚠️ $\Psi$ **no** es sobreyectiva ($5$ no tiene preimagen). No se necesita.

**Plantilla B — $\mathbb{Q}$ enumerable (cadena completa):**

$$
\mathbb{Q}\ \preccurlyeq\ \mathbb{Z}\times\mathbb{Z}\ \preccurlyeq\ \mathbb{N}\times\mathbb{N}\ \approx\ \mathbb{N}
\quad\left(\text{fracción irreducible};\ \textbf{F9};\ \text{Plantilla A}\right)
$$

$$
\Longrightarrow\ \mathbb{Q}\ \preccurlyeq\ \mathbb{N}
\quad\left(\text{transitividad, \textbf{F2}}\right)
$$

$$
\mathbb{N}\ \preccurlyeq\ \mathbb{Q}\ \wedge\ \mathbb{Q}\ \text{es infinito}
\quad\left(\text{\textbf{F10}};\ \textbf{F4}\right)
$$

$$
\Longrightarrow\ \mathbb{Q}\ \approx\ \mathbb{N}
\quad\left(\textbf{F1}:\ \text{contable + infinito}\right)
$$


### G. Probar que un conjunto es NO contable

1. **Suponer** que existe una inyección $A\to\mathbb N$ (o una biyección $A\to\mathbb N$ si $A$ es infinito).
2. **Componer** con las biyecciones conocidas hasta llegar a $\mathcal P(\mathbb N)\preccurlyeq\mathbb N$.
3. **Contradecir** $\mathbb N\prec\mathcal P(\mathbb N)$ (Cantor).
4. **Alternativa directa** para subconjuntos de $\mathbb R$: comparar con $2^{\mathbb N}$ y usar la cadena de §2.G.

**Plantilla:** $\mathcal P(\mathbb N)$ no contable. Si $\mathcal P(\mathbb N)\approx\mathbb N$, entonces $\mathbb N\approx\mathcal P(\mathbb N)$, contra Cantor. ✔️

### H. Trabajar con $\prod_{i\in I}A_{i}$

1. **Verificar** si $I=\emptyset$ (producto de un elemento) o si algún $A_{i}=\emptyset$ (producto vacío).
2. **Traducir** el elemento del producto: es una **función** $I\to\bigcup A_{i}$ con $f(i)\in A_{i}$.
3. **Para probar $X\approx\prod A_{i}$:** construir $x\mapsto f_{x}$ con $f_{x}(i)=$ la $i$-ésima coordenada, y su inversa.
4. **Para probar que $\prod A_{i}\neq\emptyset$:** con familia **finita**, constructivo; con familia infinita, esto **es** el Axioma de Elección.
5. **Verificar** con el caso $I=\{0,1\}$: el producto está en biyección con $A_{0}\times A_{1}$, no es igual.

**Plantilla:** $I=\{0,1\}$, $A_{0}=\{a\}$, $A_{1}=\{b\}$. El producto es $\left\{\{(0,a),(1,b)\}\right\}$, un conjunto con **un** elemento, equipotente a $\{(a,b)\}$ pero no igual. ✔️

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Distinguí finito / contable / enumerable / no contable antes de empezar?
- [ ] ¿En $\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}$ manejé aparte el caso $A=\emptyset$ ($0^{0}=1$) y el caso $B=\emptyset$?
- [ ] ¿Cuando usé sobreyectividad verifiqué que el conjunto adecuado es **finito** (B2 y B4 fallan en infinitos)?
- [ ] ¿En la selectora trabajé en $\mathcal A\setminus\{\emptyset\}$ y no en $\mathcal A$?
- [ ] ¿En el carácter finito usé las **dos** direcciones del si y solo si?
- [ ] ¿En $\mathbb N\times\mathbb N$ justifiqué la inyectividad con unicidad de la factorización en primos?
- [ ] ¿Para enumerable probé también que el conjunto **no** es finito?
- [ ] ¿Evité escribir "cardinal de $\mathbb R$" (no está definido en el curso)?
- [ ] ¿En el producto generalizado verifiqué $I=\emptyset$ y $A_{i}=\emptyset$?
- [ ] ¿Toda la matemática en $...$ en línea y en bloque con $$, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Dónde está |
|---|---|
| Teorema 5.62 y 5.63: selectora $\approx$ producto | §2.H (enunciados), mandados como ejercicio |
| Unión enumerable de enumerables | §2.F (F8) y §3.4: necesita elección numerable |
| Ejercicios dejados: B1, B2, B5 y "contable e infinito ⇒ enumerable" | §2.B, §2.F |
| Toda la maquinaria de elección | Próxima clase: **Axioma de Elección** |
