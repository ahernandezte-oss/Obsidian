# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 10/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261110_CONSECUENCIAS_DEL_AXIOMA_DE_ELECCION.md`
> - **Fecha de transcripción:** 10/11/2026 (`AAMMDD` = `261110`)
> - **Tema principal:** CONSECUENCIAS DEL AXIOMA DE ELECCIÓN — cierre de $\text{AC}\Rightarrow\textbf{6.9}$ (Tukey) por **doble $F$-inducción** + comparabilidad de cardinales, Dedekind, copia de $\mathbb{N}$, unión numerable y absorción de contables.
> - **Continuidad:** retoma el pendiente de 📘 `261105_AXIOMA_DE_ELECCION` §6 (el paso «$I_{0}$ es cadena»). **No repite** las 11 formas ni sus esquemas: los cita.
> - **Fuente:** transcripción de clase. Lo agregado o completado por mí va con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261110_CONSECUENCIAS_DEL_AXIOMA_DE_ELECCION` §2.C (comparabilidad)».

**📎 Prerrequisitos que se dan por sabidos:**
- Las 11 formas equivalentes y sus esquemas de prueba 📘 `261105_AXIOMA_DE_ELECCION` §2.A–§2.C.
- Carácter finito, teorema de la cadena y producto generalizado 📘 `261103_CONTABLES_SELECCION_Y_PRODUCTO` §2.E y §2.H.
- Finitud, cardinal finito $\lvert A\rvert$, $\mathbb{N}$ de von Neumann y $\mathbb{N}\times\mathbb{N}\approx\mathbb{N}$ 📘 `261029_CARDINALIDAD_Y_FINITUD` y `261103_CONTABLES_SELECCION_Y_PRODUCTO`.
- Notación: $A\approx B$ (equipotencia), $A\preccurlyeq B$ (dominancia: existe inyección $A\to B$), $A\prec B$ (dominancia estricta).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Es el cierre de una equivalencia o una consecuencia?** Si el enunciado dice «probar que $\text{AC}\Rightarrow\textbf{6.9}$» o «familia de carácter finito», es el cierre de §2.A. Si dice «usando el axioma de elección, probar que…», es una consecuencia: tabla de abajo.
2. **Paso 1 — ¿Qué objeto hay que comparar o construir?** Aplicar la tabla: cada tesis tiene **una** herramienta exacta.
3. **Paso 2 — ¿Dónde entra la elección?** Marcarla **antes** de escribir la prueba: elección finita = teorema; una sola elección = no es AC; infinitas elecciones simultáneas = AC (§3.1). Si la prueba es «$\text{AC}\Rightarrow X$», **no** se puede volver a usar AC dentro: sería circular.
4. **Paso 3 — ¿Se usa 6.7 / 6.9 o solo HCC?** Casi todas las consecuencias de hoy pasan por **HCC** (§2.C), que a su vez sale de **6.7**. Verificar la hipótesis exacta de 6.7: la unión de **toda** cadena debe quedar dentro del conjunto.

**Tabla de decisión:**

| Si el enunciado pide… | Consecuencia | Herramienta | 👉 Ir a |
|---|---|---|---|
| cerrar «$\text{AC}\Rightarrow\textbf{6.9}$», «$I_{0}$ es cadena» | Tukey | doble $F$-inducción ($J$ y $G_{B}$) | **§2.A** · §4.A |
| «$f$ sobreyectiva $\Rightarrow$ comparar $A$ y $B$» | 6.4 | inversa derecha inyectiva | **§2.B** · §4.B |
| «¿cuál es más grande?», «$A\preccurlyeq B$ o $B\preccurlyeq A$» | **HCC** | 6.7 sobre inyecciones parciales | **§2.C** · §4.B |
| «$A$ infinito $\Rightarrow$ $A$ equipotente a un subconjunto propio» | Dedekind | copiar el sucesor de $\mathbb{N}$ en $E$ | **§2.D** · §4.C |
| «todo infinito contiene un enumerable» | copia de $\mathbb{N}$ | HCC | **§2.E** |
| «unión numerable de numerables» | $\mathbb{N}\times\mathbb{N}\approx\mathbb{N}$ | suryección $\mathbb{N}\times\mathbb{N}\to\bigcup A_{n}$ + **6.2** | **§2.F** · §4.D |
| «$A$ infinito y $B$ contable $\Rightarrow$ mismo tamaño» | absorción | huecos de $\mathbb{N}$ copiados en $E$ | **§2.G** · §4.E |
| «¿esta prueba usa el axioma?» | detector | tabla §3.1 | **§3.1** |

**Frases literales del profe → método:**

- «Escoger arbitrariamente, pero no solamente escoger uno: **infinitas elecciones**.» → el AC es sobre elecciones **simultáneas** de una familia infinita (§3.1).
- «Ya para el caso finito ya está probado que la elección… no necesitábamos el axioma.» → familia finita $\Rightarrow$ inducción, nunca AC.
- «¿Dónde uso la elección? Escoger el $k_{j}$… escogió una por cada uno.» → elegir **una** biyección no es AC; elegir **una para cada** $n$, sí (§2.F).
- «Ojo, dónde se usa elección y dónde no se usa elección.» → marcarlo explícitamente (§3.1).
- «A los naturales… allá cuadra las cosas y se vuelve.» → **transportar** una estructura por una biyección (§2.D, §2.G).
- «Si usted usa la elección en la misma prueba [de $\text{AC}\Rightarrow X$], está usando lo que quiere probar.» → prohibido en el ejercicio de 6.10 ⇒ AC.
- «La esencia: mandar los naturales a un subconjunto propio y dejar quieto el resto.» → receta de Dedekind y de la absorción.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS

### A. Cierre de $\text{AC}\Rightarrow\textbf{6.9}$: $I_{0}$ es una cadena

**Contexto.** $H$ familia **no vacía** de **carácter finito**, ordenada por $\subseteq$. Se supone que **no** hay maximal:

$$
A_{B}:=\left\{\,E\in H:\ B\subsetneq E\,\right\}\neq\emptyset
\qquad\left(\text{para todo } B\in H\right)
$$

Por **AC**, sea $F$ una selectora sobre $\{A_{B}\}_{B\in H}$:

$$
F(B)\in A_{B}
\qquad\Longrightarrow\qquad
B\subsetneq F(B),\quad F(B)\in H
$$

**$F$-inductivo.** $I\subseteq H$ es $F$-inductivo si:

$$
\emptyset\in I
\qquad\wedge\qquad
B\in I\ \Rightarrow\ F(B)\in I
\qquad\wedge\qquad
C\subseteq I\ \text{cadena}\ \Rightarrow\ \bigcup C\in I
$$

$H$ es $F$-inductivo (el carácter finito da $\bigcup C\in H$). Y

$$
I_{0}:=\bigcap\left\{\,R\subseteq H:\ R\ \text{es } F\text{-inductivo}\,\right\}
$$

es el **menor** $F$-inductivo y es $F$-inductivo.

**Objetivo.** Probar que $I_{0}$ es **cadena**. Entonces $U:=\bigcup I_{0}\in I_{0}$, luego $F(U)\in I_{0}$, luego $F(U)\subseteq U$; pero $U\subsetneq F(U)$: contradicción. Luego $H$ tiene maximal y queda probado **6.9**.

**Las dos piezas de la doble inducción** (para $B\in I_{0}$):

$$
J:=\left\{\,B\in I_{0}:\ \forall\,D\in I_{0}\ \left(D\subsetneq B\ \Rightarrow\ F(D)\subseteq B\right)\,\right\}
$$

$$
G_{B}:=\left\{\,C\in I_{0}:\ C\subseteq B\ \vee\ F(B)\subseteq C\,\right\}
$$

> **🔤 Diccionario:**
> - $A_{B}$: los elementos de $H$ que **extienden propiamente** a $B$; su no vacuidad es la negación de «$B$ es maximal».
> - $F$: **selectora** de esa familia; produce un elemento estrictamente mayor que cada $B$.
> - $I_{0}$: **intersección** de todos los $F$-inductivos; el «menor» conjunto cerrado bajo $\emptyset$, $F$ y uniones de cadenas.
> - $J$: los $B$ que **absorben** hacia dentro a todo $D$ estrictamente menor.
> - $G_{B}$: los $C$ **comparables** con $B$ en el sentido débil: uno contiene al otro, o $F(B)$ ya cayó dentro de $C$.

**Las seis verificaciones (esto es toda la prueba):**

| Verificación | Qué se hace | Por qué funciona |
|---|---|---|
| $G_{1}$: $\emptyset\in G_{B}$ | $\emptyset\in I_{0}$ y $\emptyset\subseteq B$ | se cumple la primera alternativa |
| $G_{2}$: $C\in G_{B}\Rightarrow F(C)\in G_{B}$ | $F(C)\in I_{0}$; si $C\subsetneq B$, $F(C)\subseteq B$ porque $B\in J$; si $C=B$, $F(C)=F(B)$; si $F(B)\subseteq C$, entonces $F(B)\subseteq C\subsetneq F(C)$ | los tres subcasos caen en $G_{B}$ |
| $G_{3}$: $C\subseteq G_{B}$ cadena $\Rightarrow\bigcup C\in G_{B}$ | $\bigcup C\in I_{0}$; si todo $C'\in C$ cumple $C'\subseteq B$, entonces $\bigcup C\subseteq B$; si algún $C'$ cumple $F(B)\subseteq C'$, entonces $F(B)\subseteq\bigcup C$ | las dos alternativas se conservan en la unión |
| $J_{1}$: $\emptyset\in J$ | $\emptyset\in I_{0}$; no existe $D\subsetneq\emptyset$ | implicación vacía |
| $J_{2}$: $B\in J\Rightarrow F(B)\in J$ | dado $D\subsetneq F(B)$: como $D\in G_{B}=I_{0}$, $D\subseteq B$ o $F(B)\subseteq D$; lo segundo es imposible; si $D=B$, $F(D)=F(B)$; si $D\subsetneq B$, $B\in J$ da $F(D)\subseteq B\subsetneq F(B)$ | en ambos casos $F(D)\subseteq F(B)$ |
| $J_{3}$: $C\subseteq J$ cadena $\Rightarrow\bigcup C\in J$ | con $U:=\bigcup C$ y $D\subsetneq U$: cada $C'\in C$ está en $G_{D}=I_{0}$, así que $C'\subseteq D$ o $F(D)\subseteq C'$; si todas $C'\subseteq D$, entonces $U\subseteq D$, absurdo; luego alguna cumple $F(D)\subseteq C'\subseteq U$ | se usa $G_{D}$, no $G_{B}$ |

**Cierre.**

$$
\begin{aligned}
G_{B}\ \text{es } F\text{-inductivo}
&\Longrightarrow I_{0}\subseteq G_{B}
&&\left(I_{0}\ \text{es el menor } F\text{-inductivo}\right)\\
G_{B}\subseteq I_{0}
&&&\left(\text{definición de } G_{B}\right)\\
&\Longrightarrow G_{B}=I_{0}
&&\\
J\ \text{es } F\text{-inductivo}
&\Longrightarrow I_{0}\subseteq J\ \Longrightarrow\ J=I_{0}
&&\left(\text{mismo argumento}\right)
\end{aligned}
$$

**$I_{0}$ es cadena.** Dados $B,B'\in I_{0}=G_{B}$:

$$
\begin{aligned}
B'\in G_{B}
&\Longrightarrow B'\subseteq B\ \vee\ F(B)\subseteq B'
&&\left(\text{definición de } G_{B}\right)\\
F(B)\subseteq B'
&\Longrightarrow B\subsetneq F(B)\subseteq B'
&&\left(B\subsetneq F(B)\right)\\
&\Longrightarrow B\subseteq B'
&&
\end{aligned}
$$

Luego dos elementos cualesquiera son comparables. **Contradicción final:**

$$
\begin{aligned}
U:=\bigcup I_{0}\in I_{0}
&\Longrightarrow F(U)\in I_{0}
&&\left(I_{0}\ F\text{-inductivo}\right)\\
&\Longrightarrow F(U)\subseteq U
&&\left(U\ \text{es la unión de } I_{0}\right)\\
U\in H
&\Longrightarrow U\subsetneq F(U)
&&\left(F(U)\in A_{U}\right)
\end{aligned}
$$

Absurdo: se cayó en «suponer que no hay maximal». Queda probado **6.9**.

> **🔤 Diccionario del cierre:**
> - **doble $F$-inducción:** una $F$-inducción ($J$) dentro de otra ($I_{0}$); $G_{B}$ es la pieza que se prueba **mientras** se prueba $J_{2}$.
> - **absorber:** que $F$ no saque a $D$ fuera de $B$; es lo que hace que $B$ «se comporte como cadena».
> - **$I_{0}=J=G_{B}$:** las tres igualdades son el resultado de aplicar **minimalidad** de $I_{0}$, no de contar elementos.

---

### B. Sobreyectiva $\Rightarrow$ dominancia (consecuencia de 6.4)

$$
F:A\twoheadrightarrow B
\qquad\Longrightarrow\qquad
B\preccurlyeq A
$$

**Prueba.** Por **6.4**, existe $H:B\to A$ con $F\circ H=\operatorname{id}_{B}$. Entonces $H$ es inyectiva:

$$
\begin{aligned}
H(b_{1})=H(b_{2})
&\Longrightarrow F\left(H(b_{1})\right)=F\left(H(b_{2})\right)
&&\left(\text{aplico } F\right)\\
&\Longrightarrow b_{1}=b_{2}
&&\left(F\circ H=\operatorname{id}_{B}\right)
\end{aligned}
$$

> **🔤 Diccionario:** $F:A\twoheadrightarrow B$ = sobreyectiva; $H$ = **inversa a la derecha**; $\operatorname{id}_{B}$ = identidad en $B$. Una inversa a la derecha siempre es inyectiva; una inversa a la izquierda siempre es sobreyectiva.

---

### C. Comparabilidad de cardinales (HCC)

$$
\forall\,A\,\forall\,B:\qquad A\preccurlyeq B\ \ \vee\ \ B\preccurlyeq A
$$

**Prueba (6.7 sobre inyecciones parciales).**

$$
H:=\left\{\,f\ \mid\ \operatorname{dom}f\subseteq A,\ \ \operatorname{ran}f\subseteq B,\ \ f\ \text{inyectiva}\,\right\}\subseteq\mathcal{P}(A\times B)
$$

$$
\begin{aligned}
\emptyset\in H
&&&\left(\text{la función vacía es inyectiva}\right)\\
C\subseteq H\ \text{cadena}
&\Longrightarrow \bigcup C\in H
&&\left(\text{unión de funciones compatibles; inyectiva}\right)\\
\exists\,f\in H\ \text{maximal}
&&&\left(\textbf{6.7}\right)
\end{aligned}
$$

Si $\operatorname{dom}f\subsetneq A$ y $\operatorname{ran}f\subsetneq B$, se escogen $a\in A\setminus\operatorname{dom}f$ y $b\in B\setminus\operatorname{ran}f$, y

$$
\widehat f:=f\cup\{(a,b)\}\in H,
\qquad f\subsetneq\widehat f
$$

contradice la maximalidad. Por tanto:

| Caso | Qué se obtiene | Conclusión |
|---|---|---|
| $\operatorname{dom}f=A$ | $f:A\to B$ inyectiva | $A\preccurlyeq B$ |
| $\operatorname{ran}f=B$ | $f:\operatorname{dom}f\to B$ biyectiva | $B\approx\operatorname{dom}f\subseteq A$, luego $B\preccurlyeq A$ |

> **🔤 Diccionario:**
> - **inyección parcial:** función inyectiva definida solo en un trozo de $A$ y con valores en un trozo de $B$.
> - **compatibles:** dos funciones que coinciden en la intersección de sus dominios; en una cadena por $\subseteq$, dos cualesquiera lo son.
> - **$\widehat f$:** la extensión de $f$ con **una** pareja nueva; $b\notin\operatorname{ran}f$ garantiza que sigue siendo inyectiva.
> - **HCC:** «hipótesis de comparabilidad de cardinales»; no afirma que exista un orden total sobre «todos los conjuntos» (ese conjunto no existe), sino que **cada par** es comparable.

---

### D. Infinito $\iff$ Dedekind-infinito

**Definiciones.**

$$
A\ \text{finito}\iff\exists\,n\in\mathbb{N}:\ A\approx n
\qquad\qquad
A\ \text{infinito}\iff\neg\left(A\ \text{finito}\right)
$$

$$
A\ \text{Dedekind-infinito}\iff\exists\,B\subsetneq A:\ B\approx A
$$

Equivalentemente (➕): **todo** subconjunto propio está estrictamente dominado, $B\subsetneq A\Rightarrow B\prec A$; es la negación de ser equipotente a un subconjunto propio.

**Teorema.** $A$ infinito $\iff$ $A$ Dedekind-infinito. La dirección $\Leftarrow$ no usa AC; la $\Rightarrow$ usa **HCC**.

**Prueba de $\Rightarrow$.** Por **HCC**, $\mathbb{N}\preccurlyeq A$ o $A\preccurlyeq\mathbb{N}$.

- Si $A\preccurlyeq\mathbb{N}$: como $A$ es infinito, $A\approx\mathbb{N}$ (➕ todo subconjunto infinito de $\mathbb{N}$ es equipotente a $\mathbb{N}$). Sea $\psi:\mathbb{N}\to A$ una biyección; entonces $A\setminus\{\psi(0)\}$ es propio y $\approx A$ (transporta $\mathbb{N}\approx\mathbb{N}\setminus\{0\}$).
- Si $\mathbb{N}\preccurlyeq A$: sea $h:\mathbb{N}\to A$ inyectiva y $E:=\operatorname{ran}h\approx\mathbb{N}$. Se define

$$
g:A\to A,
\qquad
g(x):=
\begin{cases}
h(n+1), & x=h(n)\in E\\[2pt]
x, & x\in A\setminus E
\end{cases}
$$

$g$ es biyectiva de $A$ sobre $A\setminus\{h(0)\}\subsetneq A$:

$$
\begin{aligned}
g\ \text{inyectiva}
&&&\left(\text{sucesor inyectivo en } E,\ \text{identidad fuera}\right)\\
g\left[A\right]=A\setminus\{h(0)\}
&&&\left(\text{cada } h(n),\ n\ge 1,\ \text{viene de } h(n-1)\right)
\end{aligned}
$$

**Prueba de $\Leftarrow$.** Si $A\approx B\subsetneq A$ y $A$ fuera finito, $A\approx n$; entonces $B\subseteq A$ con $B\approx n$, imposible para un subconjunto propio de un finito (📘 `261029_CARDINALIDAD_Y_FINITUD`).

> **🔤 Diccionario:**
> - $n\in\mathbb{N}$: el natural de von Neumann $n=\{0,\dots,n-1\}$; $A\approx n$ = «$A$ tiene $n$ elementos».
> - **Dedekind-infinito:** tener un subconjunto **propio** del mismo tamaño.
> - $h(n+1)$: el **desplazamiento** (sucesor) copiado de $\mathbb{N}$ a $E$; deja libre $h(0)$.
> - **transportar:** llevar una función conocida de $\mathbb{N}$ a $E$ mediante la biyección $h$; la identidad fuera de $E$ no estorba.

---

### E. Todo conjunto infinito contiene una copia de $\mathbb{N}$

$$
A\ \text{infinito}
\qquad\Longrightarrow\qquad
\mathbb{N}\preccurlyeq A
$$

**Prueba.** Por **HCC**, $\mathbb{N}\preccurlyeq A$ o $A\preccurlyeq\mathbb{N}$. En el segundo caso, $A$ infinito y dominado por $\mathbb{N}$ dan $A\approx\mathbb{N}$, y entonces $\mathbb{N}\preccurlyeq A$ igualmente.

> **🔤 Diccionario:** «copia de $\mathbb{N}$» = subconjunto $E\subseteq A$ con $E\approx\mathbb{N}$; la inyección $h:\mathbb{N}\to A$ es la que la produce.

---

### F. Unión numerable de conjuntos enumerables

$$
\left\{A_{n}\right\}_{n\in\mathbb{N}},\quad A_{n}\approx\mathbb{N}\ \ \forall n
\qquad\Longrightarrow\qquad
\bigcup_{n\in\mathbb{N}}A_{n}\approx\mathbb{N}
$$

**Prueba (con AC explícito).** Para cada $n$,

$$
F_{n}:=\left\{\,f:\mathbb{N}\to A_{n}\ \mid\ f\ \text{biyectiva}\,\right\}\neq\emptyset
\qquad\left(A_{n}\approx\mathbb{N}\right)
$$

Por **6.2** (producto cartesiano; el profe lo numeró 6.3 en esta clase), existe una **elección simultánea** $(f_{n})_{n\in\mathbb{N}}$ con $f_{n}\in F_{n}$. Se define

$$
F:\mathbb{N}\times\mathbb{N}\to\bigcup_{n\in\mathbb{N}}A_{n},
\qquad
F(n,m):=f_{n}(m)
$$

$F$ es **sobreyectiva**: si $x\in\bigcup_{n}A_{n}$, entonces $x\in A_{n}$ para algún $n$ y $x=f_{n}(m)$ para algún $m$. Luego

$$
\bigcup_{n}A_{n}\preccurlyeq\mathbb{N}\times\mathbb{N}\approx\mathbb{N}
\qquad\left(\text{Cantor; ver } 261103\right)
$$

y como contiene a $A_{0}\approx\mathbb{N}$, es infinito; por tanto $\bigcup_{n}A_{n}\approx\mathbb{N}$.

> **🔤 Diccionario:**
> - $F_{n}$: el conjunto de **todas** las biyecciones $\mathbb{N}\to A_{n}$; es no vacío y es un conjunto (➕ vive en $\mathcal{P}(\mathbb{N}\times A_{n})$).
> - $(f_{n})_{n}$: una **familia** de biyecciones, una por cada $n$; aquí está el AC (infinitas elecciones).
> - $F(n,m)=f_{n}(m)$: el «autobús $n$, asiento $m$»; la doble indexación evita contar de más.
> - **disyuntar:** si los $A_{n}$ no son disjuntos, se reemplazan por $B_{n}:=\{n\}\times A_{n}$; siguen siendo enumerables, son disjuntos dos a dos y $\bigcup B_{n}\approx\bigcup A_{n}$.

> ⚠️ **La prueba de Hilbert falla por dos motivos.** (1) Supone que los $A_{n}$ son **disjuntos dos a dos**: un mismo elemento puede viajar en dos autobuses. (2) Al elegir la biyección de cada $A_{n}$ con $\mathbb{N}$ hace **infinitas elecciones** sin decirlo. El arreglo es disyuntar con $\{n\}\times A_{n}$ **y** usar 6.2 para elegir las $f_{n}$.

---

### G. Absorción de un conjunto contable

$$
A\ \text{infinito},\quad B\ \text{contable}
\qquad\Longrightarrow\qquad
A\cup B\approx A
$$

**Prueba.** Sea $C:=B\setminus A$; entonces $A\cup B=A\cup C$ y $C$ es contable. Por §2.E, existe $E\subseteq A$ con $E\approx\mathbb{N}$. Entonces $E\cup C$ es contable, luego $E\approx E\cup C$: sea $\varphi:E\to E\cup C$ biyectiva. Se define

$$
g:A\to A\cup C,
\qquad
g(x):=
\begin{cases}
\varphi(x), & x\in E\\[2pt]
x, & x\in A\setminus E
\end{cases}
$$

$$
\begin{aligned}
g\ \text{inyectiva}
&&&\left(\varphi\ \text{inyectiva},\ \operatorname{id}\ \text{inyectiva},\ \text{imágenes disjuntas}\right)\\
g\left[A\right]=\left(E\cup C\right)\cup\left(A\setminus E\right)=A\cup C
&&&\left(\text{sobre } A\cup C\right)
\end{aligned}
$$

Así $A\cup B\approx A$.

**Corolario.** $\mathbb{R}=\mathbb{Q}\cup\left(\mathbb{R}\setminus\mathbb{Q}\right)$, con $\mathbb{Q}$ enumerable y $\mathbb{R}\setminus\mathbb{Q}$ infinito; por tanto

$$
\mathbb{R}\setminus\mathbb{Q}\approx\mathbb{R}
$$

> **🔤 Diccionario:**
> - **contable:** finito o enumerable; **enumerable:** equipotente a $\mathbb{N}$.
> - $C=B\setminus A$: la parte **nueva** de $B$; se usa $C$ y no $B$ para que la identidad fuera de $E$ no choque con elementos de $B$ que ya estaban en $A$.
> - $E$: la copia de $\mathbb{N}$ dentro de $A$; es donde se «abren huecos» para meter $C$.
> - $\varphi$: biyección que reacomoda $E$ para que quepa $E\cup C$; lo que sobra de $A$ se queda quieto con la identidad.
> - **absorber:** el conjunto grande no cambia de tamaño al agregarle un contable.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Detector: ¿esta prueba usa el axioma de elección?

| Situación | ¿Usa AC? | Por qué |
|---|---|---|
| Escoger **un** elemento de **un** conjunto no vacío | No | es el testigo de la definición de no vacío |
| Escoger uno de cada uno de **finitos** conjuntos no vacíos | No | elección finita es **teorema** (inducción) |
| Escoger uno de cada uno de **infinitos** conjuntos no vacíos | **Sí** | es exactamente AC |
| Elegir **una** biyección entre $\mathbb{N}$ y $A$ | No | es una sola elección |
| Elegir **una biyección para cada** $n$ | **Sí** | infinitas elecciones simultáneas (§2.F) |
| Usar **6.4**, **6.7**, **6.9**, **HCC** | **Sí** (indirecto) | todas equivalen a AC |
| Probar «$\text{AC}\Rightarrow X$» usando AC en la prueba | **Error** | circular: usa lo que quiere probar |

### 3.2 Trampas (todas aparecieron en clase)

| Error | Correcto |
|---|---|
| «$A\preccurlyeq\mathbb{N}$ y $A$ infinito $\Rightarrow A\prec\mathbb{N}$» | No: los subconjuntos infinitos de $\mathbb{N}$ son $\approx\mathbb{N}$. Lo que **no** puede pasar es $A\prec\mathbb{N}$ (eso lo haría finito) |
| «HCC dice que $\preccurlyeq$ es un orden total sobre todos los conjuntos» | No existe el conjunto de todos los conjuntos; HCC es **para cada par** $A,B$ |
| «infinito = no se puede contar» | infinito = **no** equipotente a ningún $n\in\mathbb{N}$ |
| «Dedekind-infinito es lo mismo sin AC» | Sin AC solo hay finito $\Rightarrow$ Dedekind-finito; la vuelta usa **HCC** |
| «la unión numerable de numerables no necesita AC» | La prueba de Hilbert lo usa al elegir las biyecciones; con 6.2 se vuelve válida |
| «para la absorción hay que suponer $A\cap B=\emptyset$» | No: se usa $C=B\setminus A$. Con $B$ entero, la identidad en $A\setminus E$ **choca** con $B\cap(A\setminus E)$ |
| «una inyección $A\to A$ no sobreyectiva contradice que $A$ sea finito» | No: justamente es la definición de Dedekind-infinito; con AC equivale a infinito |
| «el maximal de 6.9 hay que construirlo» | No: lo da el lema; solo se construye la contradicción que prueba que existe |

### 3.3 Reglas de bolsillo

1. **AC = elecciones simultáneas de una familia infinita.** Una elección no es AC; infinitas, sí.
2. **Familia finita $\Rightarrow$ nunca citar AC.** Es inducción (📘 `261103` §3.4).
3. **HCC es el sustituto de «¿cuál es más grande?»** cuando no se puede hablar del conjunto de todos los cardinales.
4. **HCC se prueba con 6.7**, no con Zorn «a mano»: el orden es $\subseteq$ sobre inyecciones parciales y la cadena se cierra con la unión.
5. **Para Dedekind: copiar el sucesor.** Se elige $E\approx\mathbb{N}$, se desplaza dentro de $E$ y se deja la identidad fuera. El subconjunto propio es $A\setminus\{h(0)\}$.
6. **Para la absorción: los mismos huecos.** Se abre espacio dentro de $E$ y se mete $C=B\setminus A$ (no $B$ entero); el resto de $A$ no se toca.
7. **Toda prueba de «unión numerable» debe exhibir la suryección $\mathbb{N}\times\mathbb{N}\to\bigcup A_{n}$ y decir de dónde salieron las $f_{n}$.**
8. **$\mathbb{N}$ es el laboratorio:** toda función inyectiva no sobreyectiva de $\mathbb{N}$ en sí mismo (sucesor, pares, impares) se copia a cualquier conjunto infinito por una biyección.
9. **En el cierre de 6.9, la igualdad clave es $G_{B}=I_{0}$ por minimalidad**, no por doble contenencia construida a mano.
10. **No mezclar los órdenes:** $J$ y $G_{B}$ se ordenan por $\subseteq$; el maximal de 6.9 también. La cadena de $I_{0}$ es una cadena **de conjuntos**, no de índices.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Cerrar una prueba por doble $F$-inducción ($\text{AC}\Rightarrow\textbf{6.9}$)

1. **Suponer que no hay maximal** y montar, con AC, la selectora $F$ de las extensiones propias $A_{B}$.
2. **Definir $I_{0}$** como intersección de los $F$-inductivos y probar que es $F$-inductivo.
3. **Definir $J$** (los $B$ que absorben a todo $D\subsetneq B$) y **$G_{B}$** (los $C$ comparables con $B$).
4. **Probar las tres condiciones de $G_{B}$**; en $G_{2}$ se usa $B\in J$.
5. **Concluir $G_{B}=I_{0}$** por minimalidad, y luego **$J=I_{0}$**.
6. **Comparar dos elementos** $B,B'\in I_{0}$ usando $G_{B}=I_{0}$.
7. **Cerrar:** $U=\bigcup I_{0}\in I_{0}$, $F(U)\in I_{0}$, $F(U)\subseteq U$, pero $U\subsetneq F(U)$: contradicción.

**Plantilla (el paso que decide la comparación):**
$$
B'\in G_{B}=I_{0}
\ \Longrightarrow\ B'\subseteq B\ \vee\ F(B)\subseteq B'
\ \Longrightarrow\ B'\subseteq B\ \vee\ B\subseteq B'
$$

### B. Probar comparabilidad (HCC)

1. **Definir** $H$ = inyecciones parciales $A\to B$, ordenadas por $\subseteq$.
2. **$\emptyset\in H$** (función vacía).
3. **Cadena $\Rightarrow$ unión en $H$**: funciones compatibles, unión inyectiva.
4. **Aplicar 6.7** y tomar $f$ maximal.
5. **Si $\operatorname{dom}f\neq A$ y $\operatorname{ran}f\neq B$**, extender con una pareja $(a,b)$ y contradecir.
6. **Concluir**: $\operatorname{dom}f=A$ da $A\preccurlyeq B$; $\operatorname{ran}f=B$ da $B\preccurlyeq A$.

**Plantilla (extensión):**
$$
a\in A\setminus\operatorname{dom}f,\quad b\in B\setminus\operatorname{ran}f
\ \Longrightarrow\
\widehat f=f\cup\{(a,b)\}\in H,\quad f\subsetneq\widehat f
$$

### C. Probar $A$ infinito $\Rightarrow$ Dedekind-infinito

1. **HCC:** $\mathbb{N}\preccurlyeq A$ o $A\preccurlyeq\mathbb{N}$.
2. **Caso $A\preccurlyeq\mathbb{N}$:** $A\approx\mathbb{N}$; usar $\mathbb{N}\approx\mathbb{N}\setminus\{0\}$.
3. **Caso $\mathbb{N}\preccurlyeq A$:** tomar $h:\mathbb{N}\to A$ inyectiva y $E=\operatorname{ran}h$.
4. **Definir $g$**: sucesor dentro de $E$, identidad fuera.
5. **Verificar** que $g$ es biyectiva de $A$ sobre $A\setminus\{h(0)\}$.

**Plantilla:**
$$
g(x)=h(n+1)\ \text{si } x=h(n);\qquad g(x)=x\ \text{si } x\notin E
$$

### D. Probar que una unión numerable de enumerables es enumerable

1. **Verificar** $A_{n}\approx\mathbb{N}$ para todo $n$.
2. **Disyuntar** si hace falta: $B_{n}=\{n\}\times A_{n}$.
3. **Elegir** una biyección $f_{n}:\mathbb{N}\to A_{n}$ para cada $n$ (**6.2**; aquí está el AC).
4. **Definir** $F(n,m)=f_{n}(m)$.
5. **Probar que $F$ es sobreyectiva** sobre $\bigcup A_{n}$.
6. **Concluir** $\bigcup A_{n}\preccurlyeq\mathbb{N}\times\mathbb{N}\approx\mathbb{N}$ y, por ser infinito, $\approx\mathbb{N}$.

**Plantilla:**
$$
x\in\bigcup_{n}A_{n}
\ \Longrightarrow\ \exists\,n\ \exists\,m:\ x=f_{n}(m)
\ \Longrightarrow\ x=F(n,m)
$$

### E. Absorber un contable

1. **Tomar** $E\subseteq A$ con $E\approx\mathbb{N}$ (§2.E) y poner $C:=B\setminus A$.
2. **Verificar** que $E\cup C$ es contable y $E\approx E\cup C$; sea $\varphi$ la biyección.
3. **Definir** $g=\varphi$ en $E$ y $g=\operatorname{id}$ en $A\setminus E$.
4. **Verificar** que $g$ es biyectiva de $A$ sobre $A\cup C=A\cup B$.

**Plantilla:** $\mathbb{R}=\mathbb{Q}\cup(\mathbb{R}\setminus\mathbb{Q})$ con $\mathbb{Q}$ enumerable $\Rightarrow\mathbb{R}\setminus\mathbb{Q}\approx\mathbb{R}$.

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Marqué **dónde** se usa AC y dónde no?
- [ ] ¿En la prueba de $\text{AC}\Rightarrow X$ evité usar AC (nada de 6.4, 6.7, 6.9, HCC dentro)?
- [ ] ¿En 6.9 verifiqué que $H$ es **no vacía** y de **carácter finito**?
- [ ] ¿En $G_{2}$ usé $B\in J$ y distinguí $C\subsetneq B$, $C=B$ y $F(B)\subseteq C$?
- [ ] ¿En $J_{3}$ usé $G_{D}$ (no $G_{B}$) y descarté el caso «todas $C'\subseteq D$»?
- [ ] ¿En HCC verifiqué que la unión de una cadena de inyecciones parciales sigue siendo inyectiva?
- [ ] ¿En Dedekind verifiqué que $g$ cae **exactamente** en $A\setminus\{h(0)\}$?
- [ ] ¿En la unión numerable exhibí la suryección y dije de dónde salieron las $f_{n}$?
- [ ] ¿En la absorción comprobé que las imágenes de $E$ y $A\setminus E$ son disjuntas?
- [ ] ¿Toda la matemática va en $...$ y en bloque con doble dólar, sin bloques de código?
- [ ] ¿Las fórmulas dentro de tablas usan $\lvert$, $\mid$ y $\frac$ (nunca barras sueltas)?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Estado |
|---|---|
| **Cierre de $\text{AC}\Rightarrow\textbf{6.9}$** | **Cerrado** en esta clase: $I_{0}$ es cadena por doble $F$-inducción y se llega a la contradicción final |
| **Ejercicio: $\textbf{6.10}\Rightarrow\text{AC}$** | Asignado; debe hacerse **sin** usar AC en la prueba (si se usa, es circular) |
| **6.6 $\Leftrightarrow$ 6.7** | Sigue como ejercicio (venía de `261105` §6) |
| **Prueba de Hilbert del hotel infinito** | Se mostró la idea y sus dos fallas; queda como ejercicio «rescatarla» con disjunción + 6.2 |
| **Ejemplo de cálculo** | Enunciado sin prueba: una función estrictamente creciente tiene **finitas o numerables** discontinuidades (no una cantidad no numerable); sirve como ejemplo de uso de AC |
| **Consecuencias en otras teorías** | Solo mencionadas (topología, álgebra, teoría de representaciones): «se salen de lo que queremos aquí» |
| **Tercer corte** | Esta clase abre el bloque de consecuencias tras cerrar las equivalencias |
