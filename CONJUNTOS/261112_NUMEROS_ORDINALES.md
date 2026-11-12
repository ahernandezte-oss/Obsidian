# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 12/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261112_NUMEROS_ORDINALES.md`
> - **Fecha de transcripción:** 12/11/2026 (`AAMMDD` = `261112`)
> - **Tema principal:** NÚMEROS ORDINALES — tipos de orden, isomorfismos, segmentos iniciales, definición de ordinal, propiedades, sucesor/límite, mínimo y supremo, y el axioma de reemplazo.
> - **Continuidad:** retoma **buenos órdenes** y **yuxtaposición** de 📘 `261105_AXIOMA_DE_ELECCION` §2.A y §2.C (truco 4) y cierra el bloque de equivalencias de `261110`. **No repite** la teoría de cardinalidad: la usa.
> - **Fuente:** transcripción de clase. Lo agregado o completado por mí va con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261112_NUMEROS_ORDINALES` §2.D (propiedades de ordinales)».

**📎 Prerrequisitos que se dan por sabidos:**
- **Buen orden**: todo subconjunto no vacío tiene mínimo 📘 `261105_AXIOMA_DE_ELECCION` §2.A.
- **Yuxtaposición** de buenos órdenes y **unión de buenos órdenes encajados** 📘 `261105` §2.C, truco 4.
- **Cardinalidad**: $A\approx B$, $A\preccurlyeq B$, $\lvert A\rvert$ solo para finitos 📘 `261029_CARDINALIDAD_Y_FINITUD`.
- **A partir de hoy:** $\omega:=\mathbb{N}$ (misma cosa, otro nombre: es el **ordinal** de los naturales).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿La pregunta es de orden o de cardinalidad?** Si pide «cuántos», «isomorfo», «tipo de orden», es **orden** (§2.A–§2.B). Si pide «mismo tamaño», es **cardinalidad** (📘 `261110` §2.C: isomorfo $\neq$ equipotente, §3.1).
2. **Paso 1 — ¿Qué hay que producir o decidir?** Aplicar la tabla: cada tesis tiene **una** herramienta.
3. **Paso 2 — ¿Es un ordinal?** No basta «es un conjunto de ordinales»: hay que verificar **transitividad** y que $\in$ sea **buen orden estricto** (§2.C, §4.C).
4. **Paso 3 — ¿Se compara con $\in$ o con $\subseteq$?** Entre ordinales son **lo mismo** salvo el caso $\alpha=\beta$ (§2.D, regla 7). No mezclar: primero decidir si son iguales.
5. **Paso 4 — ¿Sucesor o límite?** Se decide mirando **si tiene máximo** (§2.E). $0$ también es límite.

**Tabla de decisión:**

| Si el enunciado pide… | Concepto | Herramienta | 👉 Ir a |
|---|---|---|---|
| «¿cuántos buenos órdenes hay en $A$?» | finito | $n!$, todos isomorfos | **§2.A** · §3.2 r.1 |
| «¿son isomorfos estos dos órdenes?» | tipo de orden | máximo + segmentos iniciales | **§2.B** · §4.A |
| «defina / pruebe que $\alpha$ es ordinal» | ordinal | transitivo $+$ $\in$ buen orden | **§2.C** · §4.C |
| «¿$\alpha\in\beta$, $\alpha\subseteq\beta$ o $\alpha=\beta$?» | tricotomía | $\subseteq$ y $\in$ equivalentes | **§2.D** · §4.D |
| «¿es sucesor o límite?» | forma del ordinal | ¿tiene máximo? | **§2.E** · §4.E |
| «$\bigcap X$, $\bigcup X$ de ordinales» | mínimo / supremo | intersección = mín; unión = sup | **§2.F** · §4.D |
| «¿existe el conjunto de todos los ordinales?» | clase propia | no; reemplazo | **§2.G** · §4.E |

**Frases literales del profe → método:**

- «En el caso finito, orden total y buen orden es **exactamente lo mismo**.» → en infinito **no**: $\mathbb{Z}$ y el inverso de $\omega$ son totales y no son buen orden (§2.A).
- «Cada elemento de un ordinal **es su segmento inicial**.» → por eso se usa $\in$: el representante «ya trae» sus predecesores (§2.C).
- «Entre ordinales, la contenencia y la pertenencia **son la misma cosa**.» → $\alpha\subseteq\beta\iff\alpha=\beta\ \vee\ \alpha\in\beta$ (§2.D).
- «Cualquier buen orden es isomorfo a un **único** ordinal.» → es el objetivo del tema; se enuncia en §2.C y se probará después (§6).
- «No existe el conjunto de todos los ordinales.» → es una **clase** propia (§2.F).
- «No lo llamo función, lo llamo **propiedad funcional**.» → no hay conjunto de todos los conjuntos; el reemplazo trabaja con propiedades (§2.G).
- «Los naturales los vamos a representar con la letra $\omega$.» → misma cosa, otro nombre.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS

### A. Buenos órdenes: repaso, conteo y operaciones

**Finito.** En un conjunto finito, **todo orden total es buen orden**. Si $\lvert A\rvert=n$:

$$
\#\{\text{órdenes totales en } A\}=n!
\qquad\wedge\qquad
\text{todos son buen orden}
\qquad\wedge\qquad
\text{todos son isomorfos entre sí}
$$

| $\lvert A\rvert$ | Buenos órdenes | Tipos (clases de isomorfismo) |
|---|---|---|
| $0$ | $1$ (el vacío) | $1$ |
| $1$ | $1$ | $1$ |
| $2$ | $2$ | $1$ |
| $3$ | $6=3!$ | $1$ |
| $n$ | $n!$ | $1$ |

**Infinito.** Orden total $\not\Rightarrow$ buen orden:

$$
(\mathbb{Z},\le)\ \text{es total y NO es buen orden}
\qquad\qquad
(\omega,\ge)\ \text{es total y NO es buen orden (no tiene mínimo)}
$$

**Generar buenos órdenes a partir de otros** (si $A$ y $B$ lo son):

$$
A\oplus B\ \text{(yuxtaposición)}:\quad
a<a'\ \text{en } A,\quad b<b'\ \text{en } B,\quad a<b\ \text{para todo } a\in A,\ b\in B
$$

$$
(a,b)\prec_{v}(a',b')\iff a<a'\ \vee\ \left(a=a'\ \wedge\ b<b'\right)
\qquad\text{(producto vertical)}
$$

$$
(a,b)\prec_{h}(a',b')\iff b<b'\ \vee\ \left(b=b'\ \wedge\ a<a'\right)
\qquad\text{(producto horizontal)}
$$

Los tres son **buen orden** si $A$ y $B$ lo son (➕: el mínimo se busca primero en la coordenada que manda —la primera en $\prec_{v}$, la segunda en $\prec_{h}$— y luego en la fibra). **Iterando** se obtienen órdenes cada vez más largos: $\omega$, $\omega+1$, $\omega+\omega$, $\omega\times\omega$, …

> **🔤 Diccionario:**
> - **orden total:** dos elementos cualesquiera son comparables.
> - **buen orden:** orden total donde **todo** subconjunto no vacío tiene mínimo.
> - $A\oplus B$: «todo $A$ antes de todo $B$»; no es la unión de órdenes, es un orden **nuevo** en $A\cup B$ (con $A\cap B=\emptyset$).
> - $\prec_{v}$: primero manda la **primera** coordenada; $\prec_{h}$: primero manda la **segunda**. Ambos son lexicográficos; no son el mismo orden.
> - **tipo de orden:** la clase de isomorfismo de un buen orden (§2.B).

---

### B. Isomorfismo de órdenes y tipo de orden

$$
f:(A,<_{A})\to(B,<_{B})\ \text{es isomorfismo}
\iff
f\ \text{biyectiva}\ \wedge\ \forall\,a,a'\in A:\ \left(a<_{A}a'\iff f(a)<_{B}f(a')\right)
$$

**Los isomorfismos respetan segmentos iniciales.** Con $A_{<a}:=\{x\in A:x<a\}$:

$$
f\left[A_{<a}\right]=B_{<f(a)}
\qquad\Longrightarrow\qquad
\left(A_{<a},<_{A}\right)\cong\left(B_{<f(a)},<_{B}\right)
$$

**Dos órdenes con el mismo cardinal pueden no ser isomorfos:**

| Orden | Tipo | ¿Tiene máximo? | Segmentos iniciales |
|---|---|---|---|
| $0<1<2<\cdots$ | $\omega$ | no | todos **finitos** |
| $0<1<2<\cdots<\omega$ | $\omega+1$ | sí ($\omega$) | finitos, y $\omega$ |
| $0<1<\cdots<\omega<\omega+1<\cdots$ | $\omega+\omega$ | no | hay **infinitos** sin máximo |
| $0<2<4<\cdots<1<3<5<\cdots$ | $\omega+\omega$ | no | hay **infinitos** sin máximo |

$$
\omega\not\cong\omega+1
\qquad\left(\text{un isomorfismo mandaría el máximo al máximo}\right)
$$

$$
\omega\not\cong\omega+\omega
\qquad\left(\text{en } \omega \text{ todo segmento inicial es finito; en } \omega+\omega \text{ no}\right)
$$

> **🔤 Diccionario:**
> - **isomorfismo de órdenes:** biyección que **preserva y refleja** el orden; su inversa también es isomorfismo.
> - $A_{<a}$: **segmento inicial** determinado por $a$ = todos los estrictamente menores que $a$.
> - **tipo de orden:** lo que queda cuando se olvidan los nombres y solo importa la forma; isomorfos $\iff$ mismo tipo.
> - $\omega+1$: $\omega$ con **un elemento nuevo al final**; $\omega+\omega$: **dos copias** de $\omega$, una detrás de otra.
> - «No isomorfos» **no** significa «distinto cardinal»: los cuatro órdenes de la tabla tienen cardinal $\aleph_0$.

---

### C. Ordinales: definición y representantes

$$
\alpha\ \text{es un ordinal}
\iff
\alpha\ \text{es transitivo}
\ \wedge\
(\alpha,\in)\ \text{es un buen orden estricto}
$$

$$
\alpha\ \text{transitivo}
\iff
\forall\,x\in\alpha:\ x\subseteq\alpha
$$

**La cadena de representantes** (todos con $\in$ como orden):

$$
0:=\emptyset,\qquad
1:=\{0\},\qquad
2:=\{0,1\},\qquad
3:=\{0,1,2\},\qquad
n:=\{0,1,\dots,n-1\}
$$

$$
\omega:=\mathbb{N}=\{0,1,2,\dots\},
\qquad
\omega+1:=\omega\cup\{\omega\}=\{0,1,\dots,\omega\}
$$

$$
\alpha+1:=\alpha\cup\{\alpha\}
\qquad\text{(sucesor de } \alpha\text{)}
$$

**Los ordinales finitos son exactamente los números naturales.** Todo natural es un ordinal, y todo ordinal finito es algún $n$ (➕: un ordinal finito tiene máximo y se desciende hasta $0$).

**Teorema central del tema** (enunciado; la prueba se hará después, §6):

$$
\text{Todo buen orden } (A,<)\ \text{es isomorfo a un } \textbf{único}\ \text{ordinal } \alpha
$$

Es decir: los ordinales son los **representantes canónicos** de los tipos de orden, y $\in$ es el orden entre ellos. Con esto, «contar tipos» se vuelve «comparar ordinales».

> **🔤 Diccionario:**
> - **transitivo:** todo elemento de $\alpha$ es también subconjunto de $\alpha$; equivale a «los elementos de los elementos siguen siendo elementos».
> - $(\alpha,\in)$ **buen orden estricto:** $\in$ es irreflexivo, transitivo, tricotómico, y todo subconjunto no vacío tiene $\in$-mínimo.
> - $n$: el natural de von Neumann; $n$ tiene exactamente $n$ elementos.
> - $\omega$: el conjunto de los naturales **como ordinal**; no es un natural.
> - $\alpha+1$: $\alpha$ con un elemento nuevo, $\alpha$, **al final**; es la yuxtaposición de $\alpha$ y $\{\alpha\}$ (§2.A).
> - **representante:** el ordinal que «hace de modelo» de un tipo de orden.

---

### D. Propiedades básicas de los ordinales

| # | Propiedad | Idea de la prueba |
|---|---|---|
| 1 | $\alpha\notin\alpha$ | $\in$ es irreflexivo en $\alpha$ |
| 2 | $\beta\in\alpha\ \Rightarrow\ \beta$ es ordinal | $\beta\subseteq\alpha$; si $\gamma\in\delta\in\beta$, entonces $\gamma\in\alpha$ y $\gamma\in\beta$ (transitividad de $\in$ en $\alpha$); el buen orden se hereda a $\beta$ |
| 3 | $\alpha$ ordinal $\Rightarrow\ \alpha+1$ ordinal | $\alpha+1$ es transitivo y es la yuxtaposición $\alpha\oplus\{\alpha\}$ |
| 4 | $\beta\in\alpha\ \Rightarrow\ \alpha_{<\beta}=\beta$ | $\beta$ es transitivo y $\beta\subseteq\alpha$ |
| 5 | $\alpha\in\beta\ \Rightarrow\ \alpha\subsetneq\beta$ | transitividad de $\beta$, y $\alpha\neq\beta$ porque $\alpha\notin\alpha$ |
| 6 | $\alpha\subseteq\beta\ \wedge\ \alpha\neq\beta\ \Rightarrow\ \alpha\in\beta$ | se toma $\gamma=\min(\beta\setminus\alpha)$ y se prueba $\gamma=\alpha$ |
| 7 | $\alpha=\beta\ \vee\ \alpha\in\beta\ \vee\ \beta\in\alpha$ | con $\alpha\cap\beta$: si fuera propio de ambos, se pertenecería a sí mismo |
| 8 | $\alpha\subseteq\beta\iff\alpha=\beta\ \vee\ \alpha\in\beta$ | (5) y (6) juntas |

**La 6, en cadena** (es la que más se usa):

$$
\begin{aligned}
\alpha\subseteq\beta,\ \alpha\neq\beta
&\Longrightarrow \beta\setminus\alpha\neq\emptyset
&&\left(\text{diferencia no vacía}\right)\\
&\Longrightarrow \gamma:=\min\left(\beta\setminus\alpha\right)\ \text{existe}
&&\left(\beta\ \text{bien ordenado}\right)\\
\gamma\subseteq\alpha
&&&\left(\text{si } \delta\in\gamma\subseteq\beta \text{ y } \delta\notin\alpha,\ \text{contradice el mínimo}\right)\\
\alpha\subseteq\gamma
&&&\left(\text{si } \delta\in\alpha:\ \delta\in\beta;\ \gamma\in\delta\Rightarrow\gamma\in\alpha,\ \text{absurdo}\right)\\
&\Longrightarrow \alpha=\gamma\in\beta
&&\left(\text{igualdad de conjuntos}\right)
\end{aligned}
$$

> **🔤 Diccionario:**
> - $\alpha_{<\beta}$: segmento inicial de $\alpha$ en $\beta$ = $\{x\in\alpha:x\in\beta\}$.
> - $\min(\beta\setminus\alpha)$: el $\in$-mínimo de la diferencia; existe porque $\beta$ está bien ordenado.
> - **tricotomía:** exactamente una de las tres opciones se cumple (no dos).
> - $\subsetneq$: contenencia propia; en ordinales $\alpha\subsetneq\beta$ equivale a $\alpha\in\beta$.
> - **Corolario (➕):** dos ordinales cualesquiera son comparables por $\subseteq$; en ordinales «ser comparable» y «ser $\in$-comparable» es lo mismo.

---

### E. Ordinales sucesores y ordinales límite

$$
\alpha\ \text{es sucesor}\iff\exists\,\beta:\ \alpha=\beta+1
\qquad\qquad
\alpha\ \text{es límite}\iff\neg\left(\alpha\ \text{es sucesor}\right)
$$

**Caracterización por el máximo:**

$$
\alpha\ \text{es sucesor}\iff\alpha\ \text{tiene máximo}
\qquad\qquad
\alpha\ \text{es límite}\iff\alpha\ \text{no tiene máximo}
$$

Y si $\alpha=\beta+1$, entonces $\beta=\max\alpha$. Por eso:

$$
\alpha=\left(\max\alpha\right)+1
\qquad\left(\text{todo sucesor se reconstruye desde su máximo}\right)
$$

| Ordinal | ¿Sucesor o límite? | Por qué |
|---|---|---|
| $0$ | **límite** | no es sucesor de nadie (no tiene máximo) |
| $1,2,3,\dots$ | sucesores | $n+1=(n)+1$ |
| $\omega$ | **límite** | no tiene máximo: $n<n+1\in\omega$ |
| $\omega+1$ | sucesor | máximo $\omega$ |
| $\omega+\omega$ | **límite** | no tiene máximo |

**$\omega$ es el menor ordinal infinito:** si $\alpha$ es infinito, $\alpha\notin\omega$ (los elementos de $\omega$ son naturales, finitos); por tricotomía, $\alpha=\omega$ o $\omega\in\alpha$, y en ambos casos $\omega\subseteq\alpha$. Todos los ordinales infinitos son $\ge\omega$.

> **🔤 Diccionario:**
> - **sucesor:** el que viene inmediatamente después de otro; se escribe $\beta+1$ o $\beta^{+}$.
> - **límite:** el que **no** es de la forma $\beta+1$. Ojo: $0$ es límite por definición, aunque no sea «infinito».
> - $\max\alpha$: el mayor elemento de $\alpha$ (existe solo si $\alpha$ es sucesor).

---

### F. Conjuntos de ordinales: mínimo, supremo y la clase $\mathbf{Ord}$

$$
X\neq\emptyset\ \text{conjunto de ordinales}
\ \Longrightarrow\
\bigcap X\ \text{es ordinal y}\ \bigcap X=\min X
$$

$$
X\ \text{conjunto de ordinales}
\ \Longrightarrow\
\bigcup X\ \text{es ordinal y}\ \bigcup X=\sup X
$$

$$
\bigcup X\in X\iff \bigcup X=\max X
\qquad\qquad
\alpha\subseteq\bigcup X\ \ \forall\,\alpha\in X
$$

**Todo conjunto de ordinales está bien ordenado por $\in$:** si $X$ es un conjunto de ordinales, $(X,\in)$ es un buen orden; su mínimo es $\bigcap X$ y su supremo $\bigcup X$.

**No existe el conjunto de todos los ordinales.** Para **cualquier** conjunto $X$ de ordinales:

$$
\alpha:=\left(\bigcup X\right)+1\ \text{es ordinal}
\qquad\wedge\qquad
\alpha\notin X
$$

En efecto, si $\alpha\in X$ entonces $\alpha\subseteq\bigcup X$, pero $\bigcup X\in\alpha$; se tendría $\bigcup X\in\bigcup X$, imposible.

**Tampoco existe el conjunto de todos los buenos órdenes**: si existiera, tomando los dominios ($\operatorname{dom}$ es funcional) se obtendría el conjunto de todos los conjuntos, que no existe. Por eso los tipos de orden se representan con ordinales, no con «el conjunto de todos los órdenes».

> **🔤 Diccionario:**
> - $\bigcap X$: intersección de todos los miembros de $X$; es el **mínimo** de $X$ (no solo una cota).
> - $\bigcup X$: unión de todos los miembros; es el **supremo** (mínima cota superior), no necesariamente el máximo.
> - $\sup X$: la menor cota superior; si $\bigcup X\in X$, coincide con $\max X$.
> - **clase propia:** colección que no es conjunto (no se le puede aplicar el axioma de comprensión). Todos los ordinales forman la clase $\mathbf{Ord}$, no un conjunto.

---

### G. Axioma de reemplazo (propiedades funcionales)

$$
P(a,b)\ \text{es funcional}
\iff
\forall\,a\ \exists!\,b:\ P(a,b)
$$

$$
\text{Reemplazo:}\qquad
\forall\,A\ \exists\,B\ \forall\,a\in A\ \exists\,b\in B:\ P(a,b)
$$

Es decir: **la imagen de un conjunto bajo una propiedad funcional es un conjunto**. No se llama «función» porque su dominio sería la clase de todos los conjuntos, que no existe.

| Propiedad funcional $P(a,b)$ | Para qué sirve |
|---|---|
| $b=\mathcal{P}(a)$ | formar $\{\mathcal{P}(n):n\in\omega\}$ |
| $b=a\cup\{a\}$ | construir $\{\omega,\omega+1,\omega+2,\dots\}$ |
| $b=a+1$ si $a$ es ordinal, $b=\emptyset$ si no | definir la sucesión de ordinales a trozos |

Con reemplazo se pueden **empaquetar** $\omega,\omega+1,\omega+2,\dots$ en un conjunto y así definir $\omega+\omega$; sin él no se puede justificar que ese «paquete» sea un conjunto.

> **🔤 Diccionario:**
> - **propiedad funcional:** regla que a cada $a$ le asigna **exactamente un** $b$; se escribe como fórmula, no como conjunto de parejas.
> - **reemplazo:** esquema de axiomas (uno por cada fórmula $P$), no un único axioma.
> - $\exists!$: «existe exactamente uno».
> - $\mathcal{P}(a)$: conjunto de partes de $a$.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Las confusiones que cuestan el parcial

| Confusión | Correcto |
|---|---|
| **orden total = buen orden** | Solo en **finitos**. En infinitos: $\mathbb{Z}$ y $(\omega,\ge)$ son totales y no buen orden |
| **isomorfo = equipotente** | Isomorfo exige biyección **que preserve el orden** (y su inversa). $\omega$ y $\omega+1$ son equipotentes y **no** isomorfos |
| **$\alpha\in\beta$ = $\alpha\subseteq\beta$** | Entre ordinales: $\alpha\in\beta\Rightarrow\alpha\subsetneq\beta$, pero $\alpha\subseteq\beta$ también admite $\alpha=\beta$ |
| **sucesor = límite** | Sucesor $\iff$ tiene máximo. Límite $\iff$ **no** tiene máximo. $0$ es límite |
| **máximo = supremo** | El supremo puede no pertenecer al conjunto ($\omega=\sup\omega$ y $\omega\notin\omega$) |
| **ordinal = conjunto de ordinales** | $\{3,5\}$ es conjunto de ordinales y **no** es ordinal (no es transitivo: $4\in5$ pero $4\notin\{3,5\}$) |
| **$\{\text{todos los ordinales}\}$ es un conjunto** | No: es la clase $\mathbf{Ord}$. Para cualquier conjunto $X$ de ordinales, $(\bigcup X)+1\notin X$ |
| **$\omega$ es un natural** | $\omega$ es el **conjunto** de los naturales; es un ordinal límite, no un natural |

### 3.2 Reglas de bolsillo

1. **Finito:** $n!$ órdenes totales, todos buen orden, **un solo tipo** ($n$).
2. **Para distinguir tipos infinitos** no alcanza el cardinal: usar **máximo** y **segmentos iniciales**.
3. **Segmento inicial** $A_{<a}$: los predecesores de $a$; un isomorfismo lo manda al segmento inicial de $f(a)$.
4. **Ordinal = transitivo $+$ $\in$ buen orden estricto.** Las dos condiciones se verifican por separado.
5. **Todo elemento de un ordinal es ordinal**, y **el sucesor de un ordinal es ordinal**.
6. **Tricotomía:** $\alpha=\beta$, $\alpha\in\beta$ o $\beta\in\alpha$; exactamente una.
7. **$\alpha\subseteq\beta\iff\alpha=\beta\ \vee\ \alpha\in\beta$**: por eso en ordinales $\in$ y $\subseteq$ «son la misma cosa».
8. **$\bigcap X=\min X$ (con $X\neq\emptyset$) y $\bigcup X=\sup X$** para conjuntos de ordinales; si $\bigcup X\in X$, es el máximo.
9. **Sucesor $\iff$ máximo**; **límite $\iff$ sin máximo**; $0$ es límite.
10. **No hay conjunto de todos los ordinales**: para todo conjunto $X$ de ordinales, $(\bigcup X)+1\notin X$. El reemplazo forma imágenes de **conjuntos**, nunca de la clase total.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Decidir si dos buenos órdenes son isomorfos

1. **Cardinalidad:** si no son equipotentes, no hay isomorfismo (pero que lo sean no basta).
2. **Máximo:** ¿tiene máximo uno y el otro no? Entonces **no** son isomorfos.
3. **Segmentos iniciales:** comparar qué tipos de segmentos aparecen (¿todos finitos? ¿alguno infinito? ¿alguno con máximo?).
4. **Bloques:** ver si el orden se parte en tramos (por ejemplo, dos copias de $\omega$).
5. **Si nada difiere**, construir $f$ por recursión: mínimo al mínimo, sucesor al sucesor, supremo al supremo.

**Plantilla ($\omega$ vs $\omega+1$):**

$$
\begin{aligned}
\omega+1\ \text{tiene máximo } \omega
&&&\left(\text{definición de } \omega+1\right)\\
\omega\ \text{no tiene máximo}
&&&\left(n<n+1\in\omega\right)\\
\Longrightarrow\ \omega\not\cong\omega+1
&&&\left(\text{el máximo iría al máximo}\right)
\end{aligned}
$$

### B. Identificar el ordinal (tipo) de un buen orden

1. **Finito** de $n$ elementos: el ordinal es $n$.
2. **Enumerable con máximo**: si es una copia de $\omega$ más un tope, el ordinal es $\omega+1$.
3. **Enumerable sin máximo y con todos los segmentos iniciales finitos**: el ordinal es $\omega$.
4. **Dos tramos de tipo $\omega$**: el ordinal es $\omega+\omega$ (se formaliza con aritmética ordinal, §6).
5. **Verificar** con la tabla de §2.B: máximo y segmentos iniciales identifican el tipo en los casos de clase.

**Plantilla ($0<1<2<\cdots<\text{tope}$):**

$$
n\mapsto n,\qquad \text{tope}\mapsto\omega
\qquad\Longrightarrow\qquad
\text{tipo } \omega+1
$$

### C. Probar que $X$ es un ordinal

1. **Transitividad:** tomar $x\in X$ y probar $x\subseteq X$.
2. **Irreflexividad:** probar que ningún $x\in X$ cumple $x\in x$.
3. **Transitividad de $\in$:** $x\in y\in z\Rightarrow x\in z$ para $x,y,z\in X$.
4. **Tricotomía:** para $x,y\in X$, $x=y$ o $x\in y$ o $y\in x$.
5. **Buen orden:** todo $S\subseteq X$ no vacío tiene $\in$-mínimo.

**Plantilla ($\alpha+1$):**

$$
\begin{aligned}
x\in\alpha+1
&\Longrightarrow x\in\alpha\ \vee\ x=\alpha
&&\left(\text{definición de sucesor}\right)\\
x\in\alpha
&\Longrightarrow x\subseteq\alpha\subseteq\alpha+1
&&\left(\alpha\ \text{transitivo}\right)\\
x=\alpha
&\Longrightarrow x=\alpha\subseteq\alpha+1
&&\\
&\Longrightarrow \alpha+1\ \text{es transitivo}
&&
\end{aligned}
$$

y $\in$ en $\alpha+1$ es la **yuxtaposición** $\alpha\oplus\{\alpha\}$, que es buen orden (§2.A).

### D. Operar con ordinales (mínimo, supremo, comparación)

1. **Intersección:** $\bigcap X$ es un ordinal; probar que está en $X$ (si no, se pertenece a sí mismo) y concluir $\bigcap X=\min X$.
2. **Unión:** $\bigcup X$ es un ordinal; es cota superior de todos y la menor: si $\alpha\subseteq\beta$ para todo $\alpha\in X$, entonces $\bigcup X\subseteq\beta$.
3. **Comparar $\alpha,\beta$:** usar tricotomía; si se quiere $\subseteq$, recordar $\alpha\subseteq\beta\iff\alpha=\beta\ \vee\ \alpha\in\beta$.

**Plantilla ($\bigcap X=\min X$):**

$$
\gamma:=\bigcap X\notin X
\ \Longrightarrow\
\gamma\in\beta\ \ \forall\,\beta\in X
\ \Longrightarrow\
\gamma\in\bigcap X=\gamma
\ \Longrightarrow\ \text{absurdo}
$$

### E. Usar el reemplazo para formar un conjunto de ordinales

1. **Escribir la propiedad funcional** $P(a,b)$ y verificar $\forall a\,\exists! b$.
2. **Elegir el conjunto** $A$ al que se aplica (nunca «todos los conjuntos»).
3. **Concluir** que $B=\{b:\exists a\in A,\ P(a,b)\}$ es un conjunto.
4. **Usar** $B$ para definir el ordinal siguiente (unión, sucesor, supremo).

**Plantilla ($\omega+\omega$):**

$$
P(n,\alpha):\ \alpha=\omega+n\ \ \text{(suma ordinal, §6)}
\qquad\Longrightarrow\qquad
B=\{\omega+n:n\in\omega\}\ \text{es conjunto}
\qquad\Longrightarrow\qquad
\omega+\omega:=\bigcup B
$$

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Distingo **orden total** de **buen orden** (y sé que en finitos coinciden)?
- [ ] ¿Para comparar tipos usé **máximo** y **segmentos iniciales**, no solo el cardinal?
- [ ] ¿Verifiqué **transitividad** y **buen orden** por separado al probar que algo es ordinal?
- [ ] ¿Evité escribir $\alpha\in\alpha$ o suponer que $\bigcup X\in X$?
- [ ] ¿En la tricotomía comprobé que las tres opciones son **excluyentes**?
- [ ] ¿Usé $\alpha\subseteq\beta\iff\alpha=\beta\ \vee\ \alpha\in\beta$ en el sentido correcto?
- [ ] ¿Al decidir sucesor/límite miré el **máximo** (y recordé que $0$ es límite)?
- [ ] ¿En $\bigcap X$ probé que es **mínimo** y no solo cota?
- [ ] ¿En reemplazo verifiqué que la propiedad es **funcional** ($\exists!$)?
- [ ] ¿Toda la matemática va en $...$ y en bloque con doble dólar, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Estado |
|---|---|
| **Todo buen orden $\cong$ único ordinal** | Enunciado como objetivo; **no** se demostró en esta clase |
| **Inducción transfinita** | Mencionada; se trabajará sobre buenos órdenes |
| **Aritmética ordinal** ($\omega+\omega$, $\omega\cdot2$, $\omega^2$) | Pendiente; hace falta para nombrar el tipo de $0,2,4,\dots;1,3,5,\dots$ |
| **Construcción de $\omega+\omega$ como conjunto** | Requiere el **axioma de reemplazo**, introducido al final |
| **Clase $\mathbf{Ord}$** | Visto que no es conjunto (Burali-Forti); falta el desarrollo formal |
| **Axioma de reemplazo** | Definido (propiedad funcional) y ejemplificado; se retoma la próxima clase |
