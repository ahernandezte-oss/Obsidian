# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 20/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261020_RECURSION_COMPLETA_Y_SISTEMAS_DE_PEANO.md`
> - **Fecha de transcripción:** 20/10/2026 (`DDMMAA` = `201026`)
> - **Tema principal:** RECURSIÓN COMPLETA (depende de varios valores anteriores), SISTEMAS DE PEANO (todo modelo es una copia de $\mathbb N$) y arranque del capítulo de sistemas numéricos: construcción de $\mathbb Z$ y $\mathbb Q$ como cocientes.
> - **Continuidad:** toma de `261015_RECURSION_SIMPLE_Y_PARAMETRICA` la recursión simple ($3.32$), la paramétrica y el teorema "orden de pertenencia = orden de la suma" (§2.H de aquella). **No repite** nada de eso: aquí solo se cita. Cierra la parte de $\mathbb N$ y abre el capítulo 4.
> - **Fuente:** transcripción de clase. Lo agregado o corregido por mí va marcado con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261020_RECURSION_COMPLETA_Y_SISTEMAS_DE_PEANO` §2.B».

**📎 Prerrequisitos:** recursión simple ($3.32$: dado $a\in A\neq\emptyset$ y $G:\mathbb N\times A\to A$ existe única $F:\mathbb N\to A$ con $F(0)=a$ y $F(m^{+})=G(m,F(m))$), recursión paramétrica, sucesor $n^{+}$, unión de funciones, $\bigcup_{n}n=\mathbb N$.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿De cuántos valores anteriores depende la regla?**
   - solo del inmediatamente anterior → **recursión simple** (§2.H de `151026`).
   - del anterior **y un parámetro fijo** → **paramétrica** (§2.G de `151026`).
   - de **dos o más** valores anteriores, o de "todos los anteriores" → **recursión completa** (§2.B, algoritmo §4.A).
2. **Paso 1 — ¿Aparecen "sucesión", "segmento", "restricción $F\restriction n$"?** → es señal de recursión completa: la regla de paso vive en el **conjunto de sucesiones** (§2.A).
3. **Paso 2 — ¿Piden "está bien definida" una $G$ sobre sucesiones?** → la $G$ debe estar definida sobre **todas** las sucesiones, no solo las que aparecen en el ejemplo (§3.2).
4. **Paso 3 — ¿Aparecen "axiomas de Peano", "sistema de Peano", "modelo de $\mathbb N$", "copia de los naturales"?** → §2.C y algoritmos §4.C–§4.D.
5. **Paso 4 — ¿Piden probar que un objeto **es** una copia de $\mathbb N$?** → dos vías: exhibir un sistema de Peano (§4.C) o exhibir un buen orden sin máximo con acotados con máximo (`151026` §4.I). Las dos valen; la primera es la de esta clase.
6. **Paso 5 — ¿Clases de equivalencia en $\mathbb N\times\mathbb N$ o $\mathbb Z\times(\mathbb Z\setminus\{0\})$?** → construcción de $\mathbb Z$ y $\mathbb Q$ (§2.D–§2.E) y, si hay que sumar o multiplicar, **buena definición** (§4.E).
7. **Paso 6 — ¿"campo ordenado", "conjunto de positivos", "supremo", "completo"?** → §2.F.
8. **Paso 7 — ¿Piden "el cardinal de $\mathbb R$" o comparar cardinales?** → ❌ **no se puede todavía** con los axiomas del curso: hace falta elección (§3.1).

**Tabla de decisión:**

| Si el enunciado dice… | Herramienta | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "depende de los dos anteriores", "Fibonacci", "suma de todos los anteriores" | **Recursión completa** | $F(n)=G(F\restriction n)$ | **§2.B** · §4.A |
| "defina la función de paso para la recursión", "encuentre la $G$" | **Soporte en sucesiones** | $\bar G(n,H)=H\cup\{(n,G(H))\}$ si $\mathrm{dom}\,H=n$ | **§2.B** · §4.A |
| "sucesión finita", "$H:n\to B$", "segmento de la sucesión" | **Conjunto de sucesiones** | $\mathrm{Seq}(B)=\bigcup_{n\in\mathbb N}{}^{n}B$ | **§2.A** |
| "axiomas de Peano", "modelo de los naturales", "$(A,e,S)$" | **Sistema de Peano** | (P1) $e\notin\operatorname{ran}S$, (P2) $S$ inyectiva, (P3) inducción | **§2.C** · §4.C |
| "todo sistema de Peano es una copia", "biyección entre $\mathbb N$ y $A$" | **Isomorfismo de Peano** | $F(0)=e$, $F(n^{+})=S(F(n))$ | **§2.C** · §4.D |
| "los naturales son un subconjunto de $\mathbb Z$" | **Copia, no subconjunto** | $\mathbb N_{\mathbb Z}=\{[n,0]:n\in\mathbb N\}$ | **§2.D** · §3.5 |
| "$(a,b)\sim(c,d)$", "número entero como par", "anillo" | **$\mathbb Z$ como cociente** | $(a,b)\sim(c,d)\iff a+d=b+c$ | **§2.D** · §4.E |
| "$a/b$", "fracción equivalente", "campo" | **$\mathbb Q$ como cociente** | $(a,b)\sim(c,d)\iff a\cdot d=b\cdot c$ | **§2.E** · §4.E |
| "demuestre que la suma no depende del representante" | **Buena definición** | tomar otros representantes y usar $\sim$ | **§4.E** |
| "campo ordenado", "positivos", "monotonía" | **Conjunto de positivos** | $a<b\iff b-a\in P$ | **§2.F** · §3.6 |
| "propiedad del supremo", "completo", "denso" | **Incompletitud de $\mathbb Q$** | $A=\{x\in\mathbb Q: x^{2}<2\}$ no tiene supremo | **§2.F** · §4.F |

**Frases literales del profe → método:**

- «La recursión completa es cuando depende de más que solo el anterior: de los dos anteriores, de los tres, de lo que sea.» → la regla de paso mira **un segmento** de la sucesión, no una casilla (§2.B).
- «Funciona trabajando en el conjunto de sucesiones.» → el truco entero es cambiar de conjunto: de $B$ a ${}^{\mathbb N}B$ (§2.B, paso 2 de §4.A).
- «No se le olvide que cada una de estas es una función, no una pareja ordenada.» → $(1,1,2)$ es $\{(0,1),(1,1),(2,2)\}$: una **función**, y por eso se puede restringir y unir (§2.A).
- «Esa $G$ tiene que estar definida de forma arbitraria para cualquiera.» → la $G$ del soporte es total sobre las sucesiones; por eso se parte en dos casos con la condición $\mathrm{dom}\,H=n$ (§3.2).
- «Cero no es sucesor de nadie.» → es (P1) de Peano, y es exactamente lo que falla en el paso $m=0$ de la inyectividad (§4.D).
- «Ser un campo ordenado no es que usted defina un orden total: es que exista un conjunto de positivos.» → no se ordena por decreto; se ordena con $P$ (§2.F, §3.6).

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Sucesiones: el conjunto donde vive la recursión completa

**Sucesión finita de longitud $n$** en $B$: una función $H:n\to B$. **Sucesión infinita**: una función $H:\mathbb N\to B$.

$$
\mathrm{Seq}(B)=\bigcup_{n\in\mathbb N}{}^{n}B,\qquad {}^{\mathbb N}B=\{\,H\mid H:\mathbb N\to B\,\}
$$

**🔤 Diccionario:**
- ${}^{n}B$: conjunto de todas las funciones $n\to B$; sus elementos son las sucesiones **finitas** de longitud $n$.
- $\mathrm{Seq}(B)$: todas las sucesiones finitas, de cualquier longitud.
- ${}^{\mathbb N}B$: todas las sucesiones infinitas.
- $H$: una sucesión; **es una función**, es decir un conjunto de parejas ordenadas, no una tupla.
- $\mathrm{dom}\,H$: la longitud de $H$; si $\mathrm{dom}\,H=n$ entonces $H=(H(0),\dots,H(n^{-1}))$.
- $H\restriction n$: el segmento inicial de longitud $n$ de $H$; sigue siendo una función.

**Tabla de notaciones equivalentes** (misma función, tres formas de escribirla):

| Como parejas | Como función | Como tupla |
|---|---|---|
| $\emptyset$ | $0\to B$ | $(\ )$ |
| $\{(0,1)\}$ | $H(0)=1$ | $(1)$ |
| $\{(0,1),(1,1)\}$ | $H(0)=1$, $H(1)=1$ | $(1,1)$ |
| $\{(0,1),(1,1),(2,2)\}$ | $H(0)=1,H(1)=1,H(2)=2$ | $(1,1,2)$ |

### B. Recursión completa

**Enunciado.** Sea $B\neq\emptyset$ y sea $G:\mathrm{Seq}(B)\to B$ una función dada (la **regla de paso**). Entonces existe una única $F:\mathbb N\to B$ tal que:

$$
F(n)=G\big(F\restriction n\big)\qquad\text{para todo } n\in\mathbb N
$$

**Construcción (el soporte).** Se trabaja en ${}^{\mathbb N}B$ (que no es vacío) con el valor inicial $a=\emptyset$ y la función:

$$
\bar G:\mathbb N\times{}^{\mathbb N}B\to{}^{\mathbb N}B,\qquad
\bar G(n,H)=\begin{cases}\emptyset & \text{si } \mathrm{dom}\,H\neq n\\[2pt] H\cup\big\{\big(n,\,G(H)\big)\big\} & \text{si } \mathrm{dom}\,H=n\end{cases}
$$

Por recursión simple ($3.32$) existe una única $L:\mathbb N\to{}^{\mathbb N}B$ con:

$$
L(0)=\emptyset\qquad\text{y}\qquad L(n^{+})=\bar G\big(n,L(n)\big)
$$

y la función buscada es la unión:

$$
F=\bigcup_{n\in\mathbb N}L(n),\qquad F\restriction n=L(n),\qquad F(n)=G\big(L(n)\big)
$$

**🔤 Diccionario:**
- $B$: conjunto de valores (no vacío).
- $G$: regla de paso **a nivel de elemento**: recibe **una sucesión finita completa** y devuelve **un** elemento de $B$.
- $\bar G$: regla de paso **a nivel de sucesión** (el soporte que exige $3.32$): recibe un índice $n$ y una sucesión $H$ y devuelve una sucesión, que es $H$ con **una pareja más**.
- $L$: la recursión simple que da el teorema; **no es** la función final: es la que produce las sucesiones $L(0)=\emptyset$, $L(1)=(F(0))$, $L(2)=(F(0),F(1))$, …
- $F$: la función buscada, unión de todas las $L(n)$.
- La condición $\mathrm{dom}\,H\neq n\Rightarrow\emptyset$ es el **caso basura**: mantiene a $\bar G$ total, aunque en la construcción solo se aplique a las $H$ que tienen $\mathrm{dom}=n$.

➕ **Por qué el caso basura no estorba:** la recursión simple solo evalúa $\bar G(n,L(n))$ y, por inducción, $\mathrm{dom}\,L(n)=n$; entonces **siempre** se toma la segunda rama. El caso basura existe para que $\bar G$ esté definida en **todo** $\mathbb N\times{}^{\mathbb N}B$, como exige el teorema, y no solo en las parejas que aparecen.

---

### C. Sistemas de Peano

**Definición.** Un **sistema de Peano** es una tripleta $(A,e,S)$ con $A$ un conjunto, $e\in A$ y $S:A\to A$ una función (definida en todo $A$) tal que:

$$
\text{(P1)}\quad e\notin\operatorname{ran}S
$$

$$
\text{(P2)}\quad S(a)=S(b)\ \Longrightarrow\ a=b\qquad\text{($S$ inyectiva)}
$$

$$
\text{(P3)}\quad \forall B\subseteq A:\ \Big(e\in B\ \wedge\ S(B)\subseteq B\Big)\ \Longrightarrow\ B=A
$$

**Teorema $3.37$.** $(\mathbb N,\,0,\,\sigma)$ con $\sigma(n)=n^{+}$ es un sistema de Peano.

**Teorema (todo sistema de Peano es una copia).** Si $(A,e,S)$ es un sistema de Peano, existe una **única** función $F:\mathbb N\to A$ con

$$
F(0)=e\qquad\text{y}\qquad F(n^{+})=S\big(F(n)\big)
$$

y además $F$ es **biyectiva**; por tanto $F$ es un isomorfismo entre $(\mathbb N,0,\sigma)$ y $(A,e,S)$.

**🔤 Diccionario:**
- $A$: el conjunto del modelo; sus elementos hacen el papel de "números".
- $e$: el elemento que hace el papel de **cero** (no tiene por qué ser el $\emptyset$).
- $S$: la función que hace el papel de **sucesor**; debe estar definida en todo $A$.
- (P1): el "cero" no es siguiente de nadie.
- (P2): dos elementos distintos no pueden tener el mismo siguiente.
- (P3): **inducción**: el único subconjunto que contiene a $e$ y es cerrado bajo $S$ es todo $A$.
- $S(B)\subseteq B$ ("cerrado bajo $S$"): si $a\in B$ entonces $S(a)\in B$.

**Transporte de estructura (lo que se gana):** como $F$ es biyectiva, se copian la suma, el producto y el orden a $A$:

$$
a+_{A}b:=F\big(F^{-1}(a)+F^{-1}(b)\big),\qquad a\cdot_{A}b:=F\big(F^{-1}(a)\cdot F^{-1}(b)\big)
$$

$$
a\le_{A}b:\iff F^{-1}(a)\le F^{-1}(b)
$$

y el sistema $(A,e,S,+_A,\cdot_A,\le_A)$ se comporta exactamente como $(\mathbb N,0,\sigma,+,\cdot,\le)$.

---

### D. Los enteros $\mathbb Z$ como cociente

$$
\mathbb Z=\big(\mathbb N\times\mathbb N\big)\big/\!\sim,\qquad (a,b)\sim(c,d)\iff a+d=b+c
$$

$$
[(a,b)]+[(c,d)]=[(a+c,\ b+d)],\qquad [(a,b)]\cdot[(c,d)]=[(a\cdot c+b\cdot d,\ a\cdot d+b\cdot c)]
$$

$$
0_{\mathbb Z}=[(0,0)],\qquad 1_{\mathbb Z}=[(1,0)]
$$

**Copia de $\mathbb N$ dentro de $\mathbb Z$ (sistema de Peano):**

$$
\mathbb N_{\mathbb Z}=\big\{[n,0]\ :\ n\in\mathbb N\big\},\qquad S_{\mathbb Z}\big([n,0]\big)=[n^{+},0]=[n,0]+[1,0]
$$

**Orden en $\mathbb Z$:**

$$
a\le b\iff\exists c\in\mathbb N_{\mathbb Z}\ \ (b=a+c)
$$

**🔤 Diccionario:**
- $(a,b)$: pareja de naturales que representa la **diferencia** $a-b$ (o $b-a$).
- $\sim$: relación de equivalencia entre parejas (es un ejercicio probarlo); cada **clase** es un entero.
- $[(a,b)]$: clase de equivalencia; se escribe con corchetes porque *no* es la pareja.
- $0_{\mathbb Z}=[(0,0)]$, $1_{\mathbb Z}=[(1,0)]$: **no** son $\emptyset$ ni $\{0\}$.
- $\mathbb N_{\mathbb Z}$: la copia de los naturales dentro de $\mathbb Z$; sus elementos son **clases**, no naturales.
- $S_{\mathbb Z}$: el "sucesor" de los enteros, que coincide con sumar $1_{\mathbb Z}$.
- En el orden: $c$ recorre la **copia** de los naturales, no $\mathbb N$ directamente.

**Propiedades que quedan (teorema $3.40$ y ejercicio):** la suma y el producto **no dependen del representante**; $(\mathbb Z,+,\cdot)$ es un **anillo conmutativo con unidad**, con neutro $0_{\mathbb Z}$ y unidad $1_{\mathbb Z}$; $\mathbb Z$ **no tiene mínimo ni máximo** y no es acotado.

---

### E. Los racionales $\mathbb Q$ como cociente

$$
\mathbb Q=\Big(\mathbb Z\times\big(\mathbb Z\setminus\{0_{\mathbb Z}\}\big)\Big)\Big/\!\sim,\qquad (a,b)\sim(c,d)\iff a\cdot d=b\cdot c
$$

$$
[(a,b)]+[(c,d)]=[(a\cdot d+b\cdot c,\ b\cdot d)],\qquad [(a,b)]\cdot[(c,d)]=[(a\cdot c,\ b\cdot d)]
$$

$$
0_{\mathbb Q}=[(0,1)],\qquad 1_{\mathbb Q}=[(1,1)]
$$

**Copias:** $\mathbb Z_{\mathbb Q}=\{[m,1]:m\in\mathbb Z\}$ y $\mathbb N_{\mathbb Q}=\{[n,1]:n\in\mathbb N_{\mathbb Z}\}$, con $S_{\mathbb Q}([x,1])=[x+1,1]$.

**Positivos:**

$$
\mathbb Q^{+}=\big\{[(a,b)]\ :\ a,b\in\mathbb Z^{+}\big\}
$$

**🔤 Diccionario:**
- $(a,b)$: pareja (numerador, denominador) con $b\neq 0_{\mathbb Z}$; el **denominador nunca es la clase del cero**.
- $\sim$: igualdad de fracciones "cruzada": $a\cdot d=b\cdot c$.
- $[(a,b)]$: el racional; las fracciones equivalentes son la **misma** clase.
- $0_{\mathbb Q}=[(0,1)]$, $1_{\mathbb Q}=[(1,1)]$.
- $\mathbb Z^{+}$: los enteros positivos (los $>0_{\mathbb Z}$).
- $\mathbb Q^{+}$: los racionales positivos; sirven para definir el orden (§2.F).

**Propiedades (teorema $3.47$ y ejercicios):** suma y producto bien definidos; $(\mathbb Q,+,\cdot)$ es un **campo**; $\mathbb Q$ es **denso** (entre dos racionales hay otro), **no** es acotado superiormente y **no** tiene la propiedad del supremo; todo racional $r$ se escribe $r=m\cdot n^{-1}$ (teorema $3.53$).

---

### F. Campo ordenado y propiedad del supremo

**Campo ordenado.** Un campo $(K,+,\cdot)$ con un conjunto $P\subseteq K$ (los **positivos**) tal que:

$$
\text{(O1)}\quad 0\notin P
$$

$$
\text{(O2)}\quad a,b\in P\ \Longrightarrow\ a+b\in P\ \ \wedge\ \ a\cdot b\in P
$$

$$
\text{(O3)}\quad \forall a\neq 0:\ \ a\in P\ \ \vee\ \ -a\in P
$$

y el orden **se define** con $P$:

$$
a<b\iff b-a\in P
$$

**Propiedad del supremo (completitud).** Todo $A\subseteq K$ **no vacío** y **acotado superiormente** tiene **supremo** en $K$.

**🔤 Diccionario:**
- $P$: conjunto de positivos; **no** es el conjunto de los "números mayores que $0$" (el $0$ todavía no se ha comparado con nada): es el objeto que **crea** el orden.
- (O1): el cero no es positivo; sirve para que $<$ sea irreflexivo.
- (O2): los positivos son cerrados bajo suma y producto; con esto se obtiene la **monotonía**.
- (O3): tricotomía: todo elemento no nulo cae de un lado o del otro.
- $a<b\iff b-a\in P$: la diferencia decide el orden; en $\mathbb N$ la versión análoga era $a\in b\iff\exists c\,(b=a+c)$ (`151026` §2.H).
- supremo: la **menor** de las cotas superiores; si existe y pertenece al conjunto es su máximo.
- $\mathbb Q$ cumple (O1)–(O3) pero **no** la propiedad del supremo: es un campo ordenado **incompleto**.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Qué no se puede probar todavía

| Afirmación | ¿Se puede en este punto del curso? |
|---|---|
| "el cardinal de $A$ es $n$" (con $A$ finito) | sí, más adelante: $A\approx n$ |
| "el cardinal de $\mathbb N$", "el cardinal de $\mathbb R$" | ❌ **no**: con los axiomas del curso todavía no se define cardinal |
| "$\mathbb R$ no es numerable" | se probará con equipotencia y dominancia, y hará falta el **axioma de elección** |
| "$\mathbb Z$ tiene tales elementos", "$\mathbb N\subseteq\mathbb Z$" | ⚠️ depende de la **construcción**: en este curso $\mathbb N\not\subseteq\mathbb Z$ (solo hay copia) |

**Regla:** en este curso todo depende de la construcción elegida. "Los naturales son subconjunto de los enteros" es verdad en el curso de cálculo (allí los naturales se definen **dentro** de $\mathbb R$), pero **no** aquí.

### 3.2 Las trampas de la recursión completa

| Error | Por qué está mal | Corrección |
|---|---|---|
| escribir $F(n)=G(F)$ | $G$ espera una **sucesión**, no una función infinita | $F(n)=G(F\restriction n)$ |
| usar la misma letra para $G$ y $\bar G$ | son de tipos distintos: una devuelve elemento, la otra sucesión | $G:\mathrm{Seq}(B)\to B$ y $\bar G:\mathbb N\times{}^{\mathbb N}B\to{}^{\mathbb N}B$ |
| definir $\bar G$ solo en las sucesiones del ejemplo | $3.32$ exige que $\bar G$ esté definida en **todo** $\mathbb N\times{}^{\mathbb N}B$ | añadir la rama $\mathrm{dom}\,H\neq n\Rightarrow\emptyset$ |
| creer que $L(n)$ es la respuesta | $L(n)$ es una **sucesión**; la respuesta es su unión | $F=\bigcup_{n}L(n)$ |
| olvidar probar $\mathrm{dom}\,L(n)=n$ | sin eso, $\bar G$ podría tomar la rama basura y $F(n)$ saldría mal | inducción (§4.B) |

### 3.3 Los tres tipos de recursión (tabla de desambiguación)

| | Recursión simple | Recursión paramétrica | Recursión completa |
|---|---|---|---|
| Depende de | el valor anterior | el valor anterior + un parámetro | un segmento entero |
| Soporte | $G:\mathbb N\times A\to A$ | $G:P\times\mathbb N\times A\to A$ | $G:\mathrm{Seq}(B)\to B$ |
| Se prueba con | $3.32$ | $3.32$ por cada parámetro | $3.32$ sobre ${}^{\mathbb N}B$ |
| Ejemplo | $p^{m}$ con $p$ fijo | $p+m$, $p\cdot m$ | Fibonacci |

### 3.4 Peano: qué condición se usa en cada paso

| Al probar | Se usa |
|---|---|
| $F$ inyectiva, caso $m=0$ | **(P1)** $e\notin\operatorname{ran}S$ |
| $F$ inyectiva, caso $m\neq0$ | **(P2)** $S$ inyectiva + minimalidad en $\mathbb N$ |
| $F$ sobreyectiva | **(P3)** inducción sobre el rango |
| $(\mathbb N,0,\sigma)$ es Peano | $n^{+}\neq 0$, $n^{+}=m^{+}\Rightarrow n=m$, inducción |

### 3.5 Copia $\neq$ subconjunto

| Objeto | Contiene a $\mathbb N$ | Cómo se "mete" $\mathbb N$ |
|---|---|---|
| $\mathbb N$ | — | ya está |
| $\mathbb Z=pares/\!\sim$ | ❌ no | $\mathbb N_{\mathbb Z}=\{[n,0]\}$: sistema de Peano |
| $\mathbb Q=enteros/\!\sim$ | ❌ no | $\mathbb N_{\mathbb Q}=\{[n,1]\}$ con $n\in\mathbb N_{\mathbb Z}$ |
| $\mathbb R$ (cortaduras) | ❌ no | copia, vía cortaduras de la forma $\{q: q<n\}$ |

**Regla:** "copia" = hay un isomorfismo; "subconjunto" = hay contenencia literal. Nunca uses $\subseteq$ donde solo hay isomorfismo.

### 3.6 Por qué el orden se define con positivos (y por qué en $\mathbb N$ no hacía falta)

1. En $\mathbb N$, con $a\le b\iff\exists c\,(b=a+c)$, **no hay inversos**: la ecuación $b=a+c$ separa de verdad, y la relación es orden.
2. En un **campo** (con inversos) la misma fórmula se vuelve trivial: si hay inversos, cualquiera alcanza a cualquiera y la relación se vuelve total, es decir no informativa. Lo mismo pasa con "ser par" en $\mathbb Q$: todos son pares.
3. **El truco:** restringir el $c$ a un subconjunto, $c\in P$. Ahí sí la relación corta el campo en dos mitades y se obtiene la **monotonía**.
4. **Un orden total no basta:** $\mathbb C$ admite orden lexicográfico total y **no** es campo ordenado, porque ese orden no es compatible con el producto. "Campo ordenado" no significa "tiene un orden total".

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Definir una función por recursión completa

1. **Escribir el borrador**: los primeros valores a mano ($1,1,2,3,5,\dots$), y mirar de qué parte del segmento anterior depende cada valor.
2. **Decidir el tipo de $G$**: $G:\mathrm{Seq}(B)\to B$, es decir recibe la sucesión **completa** $F\restriction n$ y devuelve **un** elemento.
3. **Definir $G$ por casos**, usando solo $\mathrm{dom}\,H$, los índices y los valores $H(i)$ ya calculados (nunca $F$).
4. **Declarar el soporte**: $B\neq\emptyset$, $a=\emptyset$, y $\bar G(n,H)=H\cup\{(n,G(H))\}$ si $\mathrm{dom}\,H=n$, $\emptyset$ si no.
5. **Aplicar el teorema**: existe única $L:\mathbb N\to{}^{\mathbb N}B$; definir $F=\bigcup_{n}L(n)$.
6. **Verificar** tres valores con la definición de $G$ y comprobar que coinciden con los del borrador.

**Plantilla (Fibonacci).** $B=\mathbb N$ y

$$
G(H)=\begin{cases}1 & \text{si } \mathrm{dom}\,H=0\\ 1 & \text{si } \mathrm{dom}\,H=1\\ H(n^{-})+H(n^{- -}) & \text{si } n=\mathrm{dom}\,H\geq 2\end{cases}
$$

Por el teorema existe única $F:\mathbb N\to\mathbb N$ con $F(n)=G(F\restriction n)$. Valores: $F(0)=G(\emptyset)=1$; $F(1)=G((1))=1$; $F(2)=G((1,1))=1+1=2$; $F(3)=G((1,1,2))=1+2=3$; $F(4)=G((1,1,2,3))=2+3=5$. Coincide con $1,1,2,3,5,8,13,21,34$. ✔️

➕ **Variante "suma de todos los anteriores":** $G(\emptyset)=1$ y $G(H)=1+\sum_{i\in\mathrm{dom}H}H(i)$ si $\mathrm{dom}\,H\neq 0$. Da $1,2,4,8,16,\dots$: cada término es el total de los anteriores más uno. ✔️

### B. Probar por inducción que $\mathrm{dom}\,L(n)=n$ (dentro de la prueba)

1. **Enunciar** la propiedad: $P(n)\ := \ \mathrm{dom}\,L(n)=n$.
2. **Base $n=0$:** $L(0)=\emptyset$ y $\mathrm{dom}\,\emptyset=0$.
3. **Paso:** suponer $P(n)$. Como $\mathrm{dom}\,L(n)=n$, el soporte toma la **segunda** rama: $L(n^{+})=L(n)\cup\{(n,G(L(n)))\}$.
4. **Calcular el dominio** de la unión: $\mathrm{dom}\,L(n^{+})=n\cup\{n\}=n^{+}$ (aquí se usa $n\notin n$).
5. **Cerrar** por inducción.

**Plantilla:** $L(0)=\emptyset$ (dominio $0$); $L(1)=\emptyset\cup\{(0,G(\emptyset))\}$ (dominio $1$); $L(2)=L(1)\cup\{(1,G(L(1)))\}$ (dominio $2$). Cada paso añade exactamente la pareja de índice $n$. ✔️

### C. Probar que $(A,e,S)$ es un sistema de Peano

1. **Verificar los tipos:** $A$ conjunto, $e\in A$, $S:A\to A$ con **todo** $A$ como dominio.
2. **Probar (P1):** para todo $a\in A$, $S(a)\neq e$ (por contradicción o por cálculo directo).
3. **Probar (P2):** tomar $S(a)=S(b)$ y deducir $a=b$ (normalmente usando la cancelación en el objeto concreto).
4. **Probar (P3):** tomar $B\subseteq A$ con $e\in B$ y $S(B)\subseteq B$, y mostrar $B=A$ (por inducción sobre los elementos, o por contradicción con el mínimo del complemento si $A$ hereda un buen orden).
5. **Concluir:** por el teorema de §2.C, $A$ es una **copia** de $\mathbb N$ (y hay isomorfismo único).

**Plantilla ($\mathbb N_{\mathbb Z}$ dentro de $\mathbb Z$):** $A=\{[n,0]:n\in\mathbb N\}$, $e=[0,0]$, $S([n,0])=[n^{+},0]$. (P1) $[n^{+},0]=[0,0]$ obligaría a $n^{+}+0=0+n$, falso. (P2) si $[n^{+},0]=[m^{+},0]$ entonces $n^{+}=m^{+}$ y $n=m$, luego $[n,0]=[m,0]$. (P3) todo subconjunto que contenga $[0,0]$ y sea cerrado bajo $S$ contiene todas las clases $[k,0]$ por inducción en $\mathbb N$. ✔️

### D. Construir el isomorfismo $\mathbb N\to(A,e,S)$

1. **Soporte:** $a=e$ y $G:\mathbb N\times A\to A$, $G(n,x)=S(x)$ (solo usa la **segunda** componente, así que es recursión simple y no hace falta la completa).
2. **Aplicar $3.32$:** existe única $F:\mathbb N\to A$ con $F(0)=e$ y $F(n^{+})=S(F(n))$.
3. **Inyectividad, montaje:** definir $H=\{n\in\mathbb N:\ \exists m\in n,\ F(m)=F(n)\}$ (el conjunto de los índices con un choque anterior).
4. **Suponer** $H\neq\emptyset$ y tomar $n=\min H$; entonces existe $m\in n$ con $F(m)=F(n)$, y como $n\neq0$ hay $k$ con $n=k^{+}$.
5. **Caso $m=0$:** $e=F(0)=F(n)=S(F(k))$, y eso contradice (P1).
6. **Caso $m\neq0$:** hay $t$ con $m=t^{+}$; entonces $S(F(t))=F(m)=F(n)=S(F(k))$, y por (P2) $F(t)=F(k)$; además $t\in k$, porque $t^{+}=m\in n=k^{+}$ da $m\le k$ y $m\neq n$ descarta $t=k$; luego $k\in H$ con $k<n$, contra la minimalidad.
7. **Concluir** $H=\emptyset$, es decir $F$ inyectiva; **sobreyectividad:** $\operatorname{ran}F$ contiene $e$ y es cerrado bajo $S$ ($S(F(m))=F(m^{+})$), así que por (P3) $\operatorname{ran}F=A$.
8. **Cerrar:** $F$ biyectiva, y transportar orden y operaciones con $F^{\pm1}$ (§2.C).

**Plantilla:** $A=\mathbb N_{\mathbb Z}$, $e=[0,0]$, $S([n,0])=[n^{+},0]$. Entonces $F(n)=[n,0]$, que es biyectiva: la inyectividad es la de $n\mapsto[n,0]$ y la sobreyectividad es por definición de $\mathbb N_{\mathbb Z}$. ✔️

### E. Probar que una operación en $\mathbb Z$ o $\mathbb Q$ está bien definida

1. **Escribir** la operación sobre representantes (parejas), no sobre clases.
2. **Tomar** otros representantes de las **mismas** clases: $(a,b)\sim(a',b')$ y $(c,d)\sim(c',d')$, es decir las igualdades que da $\sim$.
3. **Calcular** la operación con los nuevos representantes y **comparar** con la anterior mediante $\sim$.
4. **Justificar cada igualdad** con las propiedades de $\mathbb N$ o $\mathbb Z$ (asociativa, conmutativa, distributiva, cancelativa).
5. **Concluir** que la clase del resultado no depende de los representantes, y por tanto la operación está bien definida.

**Plantilla (suma en $\mathbb Q$):** si $(a,b)\sim(a',b')$ y $(c,d)\sim(c',d')$, entonces $ab'=a'b$ y $cd'=c'd$. Hay que ver $(ad+bc,\ bd)\sim(a'd'+b'c',\ b'd')$, es decir $(ad+bc)b'd'=bd(a'd'+b'c')$; desarrollando, el lado izquierdo es $ab'dd'+bb'cd'$ y el derecho $a'bdd'+bc'dd'$, y las dos igualdades de partida convierten cada producto. ✔️

### F. Probar que $\mathbb Q$ no tiene la propiedad del supremo

1. **Elegir** el conjunto testigo: $A=\{x\in\mathbb Q:\ x>0\ \wedge\ x^{2}<2\}$.
2. **Verificar** que $A\neq\emptyset$ (contiene a $1$) y que es acotado superiormente (por $2$).
3. **Suponer** que existe $s=\sup A$ en $\mathbb Q$; entonces $s>0$ y una de tres: $s^{2}<2$, $s^{2}=2$ o $s^{2}>2$.
4. **Descartar $s^{2}<2$:** construir $s+\varepsilon$ con $\varepsilon$ suficientemente pequeño y $(s+\varepsilon)^{2}<2$, que estaría en $A$ y supera a $s$ (contra supremancia).
5. **Descartar $s^{2}>2$:** construir $s-\varepsilon$ que sigue siendo cota superior, menor que $s$ (contra minimalidad).
6. **Descartar $s^{2}=2$:** en $\mathbb Q$ no hay raíz de $2$ (si $s=m\cdot n^{-1}$ con $s^{2}=2$, entonces $m^{2}=2n^{2}$ contradice la unicidad de la factorización en primos).
7. **Concluir:** ningún $s\in\mathbb Q$ es el supremo; $\mathbb Q$ es incompleto, y **eso** es lo que las cortaduras de Dedekind van a arreglar.

**Plantilla:** $A=\{x\in\mathbb Q: x^{2}<2,\ x>0\}$ no tiene supremo en $\mathbb Q$: para cualquier candidato $s$ se construye un elemento de $A$ mayor o una cota superior menor. En $\mathbb R$ el supremo es $\sqrt{2}$, que es justo el "hueco" que se rellena con la cortadura. ✔️

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Distinguí recursión simple / paramétrica / completa antes de escribir nada?
- [ ] ¿Separé la $G$ (devuelve elemento) de la $\bar G$ (devuelve sucesión)?
- [ ] ¿Definí $\bar G$ en **todo** $\mathbb N\times{}^{\mathbb N}B$, incluida la rama $\mathrm{dom}\,H\neq n$?
- [ ] ¿Escribí $F(n)=G(F\restriction n)$ y no $F(n)=G(F)$?
- [ ] ¿Probé $\mathrm{dom}\,L(n)=n$ antes de usar la segunda rama?
- [ ] ¿Recuerdo que una sucesión **es** una función (y por eso se restringe y se une)?
- [ ] ¿En Peano verifiqué que $S$ está definida en **todo** $A$ y que $e\in A$?
- [ ] ¿Usé (P1), (P2), (P3) en el paso correcto de la prueba (§3.4)?
- [ ] ¿Escribí "copia" y no "subconjunto" al pasar de $\mathbb N$ a $\mathbb Z$ o $\mathbb Q$?
- [ ] ¿En las operaciones de cociente probé la buena definición antes de operar?
- [ ] ¿Recordé que el orden de un campo se define con los **positivos**, no con un orden total cualquiera?
- [ ] ¿Evité hablar de cardinales de conjuntos infinitos (§3.1)?
- [ ] ¿Toda la matemática en $...$ en línea y en bloque con $$, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Dónde está |
|---|---|
| **Unicidad** de la función de la recursión completa | la construcción quedó hecha; el cierre es inducción sobre $n$ (§2.B) |
| Propiedades de suma, producto, potenciación y del orden en $\mathbb N$ | tarea: todas por inducción |
| Divisibilidad y las relaciones de orden que da cada operación ("cada operación define un orden") | ejercicio de la clase |
| Probar que $\sim$ en $\mathbb Z$ y en $\mathbb Q$ son relaciones de equivalencia, y las propiedades de anillo y campo | ejercicios ($3.40$, $3.47$) |
| $\mathbb Z$ no tiene mínimo ni máximo; $\mathbb Q$ es denso y no acotado | ejercicios |
| Dos formas de definir el orden en $\mathbb Q$ (con el orden de $\mathbb Z$ o con $\mathbb Q^{+}$) y probar que coinciden | ejercicio |
| **Cortaduras de Dedekind** y construcción de $\mathbb R$ | siguiente clase |
| "El único campo ordenado completo es isomorfo a $\mathbb R$" | teorema final del capítulo, pendiente |
