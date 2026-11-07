# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 05/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261105_AXIOMA_DE_ELECCION.md`
> - **Fecha de transcripción:** 05/11/2026 (`AAMMDD` = `261105`)
> - **Tema principal:** AXIOMA DE ELECCIÓN — las 11 formas equivalentes (AC, 6.1–6.10) y los **esquemas de prueba** para pasar de una a otra.
> - **Continuidad:** NO repite `261029_CARDINALIDAD_Y_FINITUD` (Cantor, punto fijo, Cantor–Bernstein, finitud) ni `261103_CONTABLES_SELECCION_Y_PRODUCTO` (contables, selectora, carácter finito, producto generalizado). Los **cita**.
> - **Fuente:** transcripción de clase. Lo agregado o completado por mí va con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261105_AXIOMA_DE_ELECCION` §2.A (forma 6.9)».

**📎 Prerrequisitos que se dan por sabidos:**
- **Función selectora:** $g:\mathcal A\setminus\{\emptyset\}\to\bigcup\mathcal A$ con $g(A)\in A$ 📘 `261103_CONTABLES_SELECCION_Y_PRODUCTO` §2.D.
- **Elección finita es teorema** (inducción, sin axioma) 📘 `261103_CONTABLES_SELECCION_Y_PRODUCTO` §2.D y §3.4.
- **Carácter finito** y su teorema de la cadena 📘 `261103_CONTABLES_SELECCION_Y_PRODUCTO` §2.E.
- **Producto generalizado** $\prod_{i\in I}A_{i}$ 📘 `261103_CONTABLES_SELECCION_Y_PRODUCTO` §2.H.
- **Buen orden**, cota superior, maximal, cadena.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿La familia es finita?** Si sí, **no uses ningún axioma**: es inducción (📘 `-031126` §2.D). El Axioma de Elección solo aparece con familias **infinitas**.
2. **Paso 1 — ¿Qué hay que producir?** Aplicar la tabla de abajo: cada cosa que se pide (una selectora, un maximal, una cadena maximal, un buen orden, una inversa a la derecha, una función dentro de una relación) tiene **una forma exacta** que lo produce.
3. **Paso 2 — ¿Vas en el sentido $\text{AC}\Rightarrow X$ o en el sentido $X\Rightarrow\text{AC}$?**
   - $\text{AC}\Rightarrow X$: **aplica** el axioma a la familia adecuada (esquema §4.A).
   - $X\Rightarrow\text{AC}$: **construye fragmentos** y toma el maximal (esquema §4.B). Es el molde largo.
4. **Paso 3 — ¿Se usa Zorn / Tukey / Hausdorff?** Verifica la hipótesis **exacta** de la forma elegida (§3.2). El 90 % de los errores es confundir sus hipótesis.
5. **Paso 4 — ¿La tesis es una equivalencia?** Entonces son **dos** direcciones, y la flecha del diagrama es de **un solo sentido** (§3.5).

**Tabla de decisión:**

| Si el enunciado pide… | Forma | Enunciado base | 👉 Ir a |
|---|---|---|---|
| "escoger un elemento de cada conjunto" (familia arbitraria) | **AC** | $\forall\,\mathcal A\ \exists\,g$ selectora | **§2.A** · §4.A |
| lo mismo, pero solo sobre $\mathcal P(A)$ | **6.1** | $\mathcal P(A)\setminus\{\emptyset\}$ tiene selectora | **§2.A** · §4.A |
| "el producto de una familia de no vacíos es no vacío" | **6.2** | $\prod_{i\in I}A_{i}\neq\emptyset$ | **§2.A** · §4.A |
| "un conjunto que corta a cada $A_{i}$ en **un solo** punto" | **6.3** | $\exists B:\ \lvert B\cap A_{i}\rvert=1$ | **§2.A** · **§2.C** |
| "inversa a la derecha" de una sobreyectiva | **6.4** | $F$ sobre $\Rightarrow\exists H:FH=\mathrm{id}$ | **§2.A** · §4.F |
| "dentro de una relación hay una función con el mismo dominio" | **6.5** | $R\subseteq A\times B$ | **§2.A** · §4.F |
| "toda cadena acotada superiormente $\Rightarrow$ hay maximal" | **6.6 Zorn** | hipótesis: cadena $\Rightarrow$ cota **en** $A$ | **§2.A** · §4.D |
| ordenado **por $\subseteq$**, con $\bigcup$ de cada cadena **dentro** del conjunto $\Rightarrow$ maximal | **6.7** | $\bigcup C\in B$ para toda cadena $C$ | **§2.A** · §4.B |
| "cadena maximal" | **6.8 Hausdorff** | todo orden tiene cadena $\subseteq$-maximal | **§2.A** · §4.E |
| "familia de carácter finito $\Rightarrow$ maximal" | **6.9 Tukey** | familia **no vacía** de carácter finito | **§2.A** · §4.E |
| "todo conjunto se puede bien ordenar" | **6.10 Zermelo** | $\exists$ buen orden en $A$ | **§2.A** · §4.G |

**Frases literales del profe → método:**

- «Si yo coloco cualquiera de estos como axioma, todos los demás son consecuencias.» → las 11 formas son **una sola cosa dicha de 11 maneras**; puedes escoger la más cómoda.
- «Cada una de estas pruebas no va a usar ninguno de los anteriores: para probar la 6.8 solo uso la 6.9 y la teoría construida.» → cada flecha del diagrama se prueba **desde cero**, sin encadenar las otras 10.
- «Es la única [forma] que no le pide sobre cualquier conjunto sino sobre el conjunto de partes: es una versión más débil.» → 6.1 es AC restringido a $\mathcal P(A)$.
- «¿Quién sería el mejor $H$?» → la restricción: siempre que puedas **restringir** una selectora grande a un dominio más pequeño, hazlo (§2.C, truco 2).
- «El truco es que $\{i\}\times A_{i}$ sí son disjuntos dos a dos.» → para usar 6.3 sobre una familia **no** disjunta.
- «Yo no estoy utilizando el axioma de elección: utilicé selectoras para conjuntos **finitos**, y para productos finitos no necesito axioma.» → de dónde sale que el teorema de la cadena es gratis.
- «Suponga que su dominio **no** es $S$: existe $b\in S\setminus\operatorname{dom}f$, le agrego la pareja y contradigo la maximalidad.» → el molde §4.B completo.
- «Es maximal **con la contenencia**: no está contenida en ninguna otra.» → maximal $\neq$ máximo.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Formas, mapa y trucos)

### A. Las 11 formas equivalentes

| # | Enunciado |
|---|---|
| **AC** | **Todo** conjunto $\mathcal{A}$ tiene función selectora: $\exists\,g:\mathcal{A}\setminus\{\emptyset\}\to\bigcup\mathcal{A}$ con $g(A)\in A$ |
| **6.1** | Todo **conjunto de partes** tiene función selectora: existe $g:\mathcal{P}(A)\setminus\{\emptyset\}\to\bigcup\mathcal{P}(A)=A$ con $g(B)\in B$ |
| **6.2** | Si $\{A_{i}\}_{i\in I}$ es una familia **no vacía** (índices $I\neq\emptyset$, indexación inyectiva) de conjuntos **no vacíos**, entonces $\prod_{i\in I}A_{i}\neq\emptyset$ |
| **6.3** | Si $\{A_{i}\}_{i\in I}$ es una familia no vacía de conjuntos no vacíos **dos a dos disjuntos**, existe $B\subseteq\bigcup_{i\in I}A_{i}$ tal que $B\cap A_{i}$ es **unitario** para todo $i\in I$ |
| **6.4** | Toda función **sobreyectiva** $F:A\to B$ tiene **inversa a la derecha**: $\exists H:B\to A$ con $F\circ H=\operatorname{id}_{B}$ |
| **6.5** | Toda **relación** $R\subseteq A\times B$ contiene una **función** $f\subseteq R$ con $\operatorname{dom}f=\operatorname{dom}R$ |
| **6.6** | **Lema de Zorn:** si $(A,\le)$ es un orden donde **toda cadena está acotada superiormente** (cota en $A$), entonces $A$ tiene un elemento **maximal** |
| **6.7** | **Zorn por contenencia:** si $(B,\subseteq)$ cumple que $\bigcup C\in B$ para **toda** cadena $C\subseteq B$, entonces $B$ tiene un elemento **$\subseteq$-maximal** |
| **6.8** | **Principio maximal de Hausdorff:** todo conjunto ordenado tiene una **cadena maximal** (bajo $\subseteq$) |
| **6.9** | **Lema de Tukey:** toda familia **no vacía** $H$ de **carácter finito** tiene un elemento **$\subseteq$-maximal** |
| **6.10** | **Teorema de Zermelo:** todo conjunto se puede **bien ordenar** |

> **🔤 Diccionario:**
> - **selectora:** la función que "escoge uno" de cada miembro de la colección.
> - **$\mathcal P(A)\setminus\{\emptyset\}$:** las partes no vacías (el vacío se excluye siempre: de él no se escoge).
> - **$\prod_{i\in I}A_{i}\neq\emptyset$:** existe **una** función $f$ con $f(i)\in A_{i}$ para todo $i$ (§2.H de `-031126`).
> - **dos a dos disjuntos:** $A_{i}\cap A_{j}=\emptyset$ si $i\neq j$.
> - **unitario:** con exactamente un elemento.
> - **cota superior de $C$:** $a\in A$ con $c\le a$ para todo $c\in C$. Ojo: la cota debe estar **en el conjunto**.
> - **maximal:** no existe $a'$ con $a<a'$. **No** es lo mismo que máximo (que exige $a'\le a$ para todo $a'$).
> - **cadena:** subconjunto totalmente ordenado por la restricción del orden.
> - **carácter finito:** $X\in H\iff$ todo subconjunto finito de $X$ está en $H$ 📘 `-031126` §2.E.
> - **bien orden:** todo subconjunto no vacío tiene mínimo.

### B. El mapa de implicaciones

$$
\begin{aligned}
\text{AC}
&\Longrightarrow \textbf{6.1} &&\left(\text{todo } \mathcal P(A) \text{ es un conjunto}\right)\\
\textbf{6.1}
&\Longrightarrow \text{AC} &&\left(\text{restringir la selectora de } \mathcal P(A)\right)\\
\text{AC}
&\Longrightarrow \textbf{6.3} &&\left(\text{selectora sobre la familia; el rango sirve de } B\right)\\
\textbf{6.3}
&\Longrightarrow \textbf{6.2} &&\left(\text{disyuntar con } \{i\}\times A_{i}\right)\\
\textbf{6.2}
&\Longrightarrow \textbf{6.5} &&\left(\text{familias } K_{a}=R[\{a\}]\right)\\
\textbf{6.5}
&\Longrightarrow \text{AC} &&\left(R=\{(x,y):x\in a,\ y\in x\}\right)\\
\text{AC}
&\Longrightarrow \textbf{6.4} &&\left(\text{selectora sobre las fibras } F^{-1}(b)\right)\\
\textbf{6.4}
&\Longrightarrow \textbf{6.3} &&\left(\text{la proyección } p(x)=\text{índice único}\right)\\
\textbf{6.9}
&\Longrightarrow \textbf{6.8} &&\left(\text{las cadenas tienen carácter finito}\right)\\
\textbf{6.8}
&\Longrightarrow \textbf{6.6} &&\left(\text{cadena maximal + cota} \Rightarrow \text{maximal}\right)\\
\textbf{6.7}
&\Longrightarrow \text{AC} &&\left(\text{fragmentos de selectora, maximal} \Rightarrow \operatorname{dom}=\text{todo}\right)\\
\textbf{6.9}
&\Longrightarrow \textbf{6.10} &&\left(A^{*} \text{ de buenos órdenes} + \text{yuxtaposición}\right)\\
\textbf{6.10}
&\Longrightarrow \text{AC} &&\left(g(a)=\min a\right)\\
\text{AC}
&\Longrightarrow \textbf{6.9} &&\left(\text{inductivos } + \text{ intersección mínima } Y_{0}\right)
\end{aligned}
$$

**Cerrando el ciclo** AC → 6.1 → AC, AC → 6.3 → 6.2 → 6.5 → AC, AC → 6.4 → 6.3, 6.9 → 6.8 → 6.6, 6.7 → AC, 6.9 → 6.10 → AC, y AC → 6.9, **las 11 quedan conectadas**: por eso son equivalentes.

> **🔤 Diccionario del mapa:**
> - Cada renglón es **una flecha** y su paréntesis es **el truco** que la produce (no la prueba completa).
> - Las que quedan sin renglón (6.6 ↔ 6.7 y 6.8 ↔ 6.9 en el otro sentido) se obtienen **componiendo** flechas ya probadas: si $X\Rightarrow Y$ y $Y\Rightarrow\text{AC}$, entonces $Y\Rightarrow X$ **no** sale de ahí; se prueba aparte o se usa la cadena larga.

> ➕ **Nota de rigor:** que un ciclo de implicaciones dé **equivalencia** exige que las flechas estén **en el sentido correcto**: si se probó $X\Rightarrow Y$ y $Y\Rightarrow X$, hay equivalencia; si solo se probaron flechas de ida alrededor del ciclo, entonces el ciclo **sí** produce las vueltas, es decir $X\Rightarrow Y\Rightarrow\cdots\Rightarrow X$, que es una equivalencia. Lo que **no** se puede es leer una flecha al revés sin haberla probado.

### C. Los seis trucos internos (el motor de todas las pruebas)

#### Truco 1 — Disyuntar una familia (`6.3 ⇒ 6.2`)

$$
\left(A_{i}\right)_{i\in I}\ \longmapsto\ \left(\{i\}\times A_{i}\right)_{i\in I}
$$

$$
\begin{aligned}
(i,x)\in\{i\}\times A_{i}\ \wedge\ (j,y)\in\{j\}\times A_{j}\ \wedge\ (i,x)=(j,y)
&\Longrightarrow i=j &&\left(\text{igualdad de parejas, 1.ª componente}\right)\\
&\Longrightarrow \left(\{i\}\times A_{i}\right)\cap\left(\{j\}\times A_{j}\right)=\emptyset\ \text{si } i\neq j &&\left(\text{definición de disjuntos}\right)
\end{aligned}
$$

**Para qué:** 6.3 exige disjunción; la familia original puede tener conjuntos **iguales** ($A_{i}=A_{j}$), así que no sirve tal cual. La pareja $\{i\}\times A_{i}$ guarda el índice y **fuerza** la disjunción.

#### Truco 2 — Autoindexar y restringir

$$
\mathcal{A}\ \text{se indexa por sí mismo:}\quad A_{X}:=X\ \ (X\in\mathcal{A})
\qquad\qquad
g\restriction\left(\mathcal{A}\setminus\{\emptyset\}\right)
$$

**Para qué:** pasar de una selectora sobre un dominio grande a una sobre el dominio que necesitas. Es el truco de `6.1 ⇒ AC` y de `AC ⇒ 6.4`.

#### Truco 3 — Cadena de funciones $\Rightarrow$ la unión es función

$$
\begin{aligned}
&F,G\in C\ \text{y } C \text{ cadena} &&\left(F\subseteq G\ \vee\ G\subseteq F\right)\\
&\Longrightarrow\ F,G\ \text{son compatibles (coinciden en su dominio común)} &&\left(\text{la contenencia entre funciones es extensión de dominios}\right)\\
&\Longrightarrow\ \bigcup C\ \text{es función} &&\left(\text{unión de funciones compatibles dos a dos}\right)\\
&\Longrightarrow\ \operatorname{dom}\left(\bigcup C\right)=\bigcup_{F\in C}\operatorname{dom}F &&\left(\text{dominio de la unión}\right)
\end{aligned}
$$

**Para qué:** es el paso que hace que el conjunto de fragmentos cumpla la hipótesis de 6.7, y el que prueba que el conjunto de cadenas tiene carácter finito.

#### Truco 4 — Yuxtaposición (extender un buen orden)

Dado $(B_{0},\le_{0})$ bien ordenado y $x\notin B_{0}$, se define en $B_{0}\cup\{x\}$:

$$
b\le'b\iff\left(b,b\in B_{0}\ \wedge\ b\le_{0}b'\right)\ \vee\ \left(b\in B_{0}\ \wedge\ b'=x\right)\ \vee\ \left(b=x=b'\right)
$$

$$
\begin{aligned}
\le'\ \text{extiende a}\ \le_{0}
&\iff \le_{0}\ \subseteq\ \le' &&\left(\text{se conservan todas las comparaciones viejas}\right)\\
\le'\ \text{es buen orden}
&\iff \text{lo es } \le_{0}\ \text{y } x \text{ queda de último, solo} &&\left(\text{agregar un máximo a un buen orden da buen orden} ➕\right)
\end{aligned}
$$

**Para qué:** contradecir la maximalidad en `6.9 ⇒ 6.10`.

#### Truco 5 — Fragmentos maximales (el molde `X ⇒ AC`)

$$
\begin{aligned}
H&:=\left\{\,f\ \middle|\ \operatorname{dom}f\subseteq S,\ \ \operatorname{ran}f\subseteq\bigcup S,\ \ f(x)\in x\ \ \forall x\in\operatorname{dom}f\,\right\} &&\left(\text{selectoras parciales}\right)\\
H&\neq\emptyset &&\left(\emptyset\in H,\ \text{condición vacía}\right)\\
C\subseteq H\ \text{cadena}&\Longrightarrow\bigcup C\in H &&\left(\text{truco 3}\right)\\
\exists\,f\in H\ \text{maximal} &&\left(\textbf{6.7}\right)\\
\operatorname{dom}f=S &&\left(\text{si no: } b\in S\setminus\operatorname{dom}f,\ k\in b,\ f\cup\{(b,k)\} \text{ contradice la maximalidad}\right)
\end{aligned}
$$

**Para qué:** es la prueba de `6.7 ⇒ AC`, y el mismo molde sirve para casi cualquier `X ⇒ AC`.

#### Truco 6 — El conjunto de cadenas tiene carácter finito

$$
M:=\left\{\,X\subseteq A \;\middle|\; X\ \text{es cadena en } (A,\le)\,\right\}
$$

$$
\begin{aligned}
X\in M
&\Longleftarrow \text{todo finito } Y\subseteq X\ \text{está en } M &&\left(\text{a probar}\right)\\
a,b\in X
&\Longrightarrow \{a,b\}\subseteq X\ \text{es finito} &&\left(\text{dos elementos}\right)\\
&\Longrightarrow \{a,b\}\in M\ \text{(es cadena)} &&\left(\text{hipótesis}\right)\\
&\Longrightarrow a\le b\ \vee\ b\le a &&\left(\text{ser cadena de dos elementos}\right)\\
&\Longrightarrow X\ \text{es cadena, es decir } X\in M &&\left(\text{definición de cadena}\right)
\end{aligned}
$$

La otra dirección es inmediata: **todo subconjunto de una cadena es cadena**. Con las dos, $M$ es de carácter finito, y **6.9** le da una cadena $\subseteq$-maximal: eso es **6.8**.

> **🔤 Diccionario de los trucos:**
> - **compatibles:** dos funciones que coinciden en la intersección de sus dominios. La contenencia entre funciones **es** compatibilidad.
> - **$\operatorname{ran}f$:** rango (imagen) de $f$.
> - **selectoras parciales:** funciones que cumplen la condición de selectora **solo** en su dominio, que puede ser un trozo de $S$.
> - **yuxtaponer:** pegar un elemento **al final** del orden.
> - **$Y\subseteq X$ finito:** los subconjuntos finitos son los "testigos" que el carácter finito permite revisar.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Las tres confusiones que cuestan el parcial

| Confusión | Correcto |
|---|---|
| **maximal = máximo** | **maximal:** nadie estrictamente mayor. **máximo:** es $\ge$ que todos. En un orden parcial un maximal puede no ser máximo; un máximo sí es maximal |
| **cota superior = elemento del conjunto** | La cota de una cadena **debe estar en $A$** (por eso 6.7 lo exige explícitamente con $\bigcup C\in B$) |
| **cadena maximal = cadena con todos los elementos** | **cadena maximal:** cadena que no está contenida propiamente en otra cadena. No es "la cadena más grande del universo" |

### 3.2 La hipótesis exacta de cada forma (esto es lo que se verifica, no lo que se "siente")

| Forma | Hipótesis que hay que verificar | Conclusión |
|---|---|---|
| **6.6 Zorn** | $(A,\le)$ orden; **toda** cadena $C\subseteq A$ tiene cota superior **en $A$** | $\exists$ maximal |
| **6.7 Zorn-$\subseteq$** | $(B,\subseteq)$; **toda** cadena $C\subseteq B$ cumple $\bigcup C\in B$ | $\exists$ $\subseteq$-maximal |
| **6.8 Hausdorff** | $(A,\le)$ orden cualquiera (¡nada más!) | $\exists$ cadena maximal |
| **6.9 Tukey** | $H\neq\emptyset$ **y** $H$ de carácter finito | $\exists$ $\subseteq$-maximal |
| **6.10 Zermelo** | $A$ conjunto cualquiera | $\exists$ buen orden sobre $A$ |

### 3.3 Reglas de bolsillo

1. **Sin infinito no hay axioma.** Producto finito de no vacíos $\neq\emptyset$, elección finita, unión finita: todo eso es **teorema** 📘 `-031126` §3.4.
2. **El vacío se quita siempre.** AC se enuncia sobre $\mathcal A\setminus\{\emptyset\}$; si algún miembro es vacío, no hay selectora posible.
3. **6.1 es AC debilitado** (solo conjuntos de partes). Por eso `6.1 ⇒ AC` necesita **restringir** (truco 2), no aplicar.
4. **Para usar 6.3, la familia debe ser disjunta.** Si no lo es, **disyúntala** con $\{i\}\times A_{i}$ (truco 1). Nunca supongas disjunción.
5. **En el molde $X\Rightarrow\text{AC}$**, el paso final **siempre** es: "si el dominio no es todo, agrego un par más y contradigo la maximalidad" (truco 5).
6. **En Zorn el elemento maximal no se construye**: sale del lema. Lo único construible es la cota superior.
7. **La unión de una cadena de conjuntos no está, en general, en el conjunto**: por eso hace falta 6.7, que lo pone como **hipótesis**. Sin esa hipótesis, Zorn-$\subseteq$ es falso.
8. **Hausdorff + "toda cadena acotada" = Zorn.** Es literalmente el `6.8 ⇒ 6.6`: la cadena maximal, al ser acotada, tiene un elemento por encima de todos sus miembros, y ese es maximal.
9. **6.9 $\Rightarrow$ 6.8** no usa AC: solo el carácter finito del conjunto de cadenas y Tukey. Por eso la prueba es corta.
10. **Tukey es el atajo para "quiero un objeto maximal definido por condiciones finitas"**: cadenas, conjuntos linealmente independientes, familias compatibles, subconjuntos con cierta cerradura.
11. **Zermelo: el buen orden que se obtiene no se conoce.** La prueba da **existencia** (por maximalidad de un buen orden parcial), no una fórmula.
12. **Un ciclo de flechas da equivalencia, pero solo en el sentido en que están dibujadas.** Si probaste $X\Rightarrow Y$ y usas el ciclo para concluir $Y\Rightarrow X$, tienes que haber pasado por flechas que **todas** vayan en el sentido del recorrido.

### 3.4 Por qué NO usar cada forma (restricciones)

| Forma | Por qué NO |
|---|---|
| **6.6 Zorn** | Si las cadenas **no** tienen cota en el conjunto, no aplica. Ejemplo típico: $(\mathbb{Q},\le)$ no cumple Zorn porque $\mathbb{Q}$ no tiene maximal (¡y sí, sus cadenas están acotadas en $\mathbb{R}$, pero la cota **no está** en $\mathbb{Q}$!) |
| **6.7** | Si $\bigcup C\notin B$ para alguna cadena, no aplica: el resultado es **falso** sin esa hipótesis |
| **6.9 Tukey** | Si la familia **no** es de carácter finito, no aplica. Y si $H=\emptyset$, tampoco hay maximal: la no vacuidad es hipótesis |
| **6.3** | Exige disjunción; sin ella ni siquiera tiene sentido "el" punto de intersección |
| **6.4** | Exige **sobre**yectividad: sin ella las fibras pueden ser vacías |
| **6.5** | El dominio de la función debe ser **todo** $\operatorname{dom}R$: si solo pides $\operatorname{dom}f\subseteq\operatorname{dom}R$, no necesitas nada (toma $\emptyset$) |
| **6.10** | No dice **cómo** es el buen orden; si el ejercicio pide el orden explícito, Zermelo no sirve |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Probar $\text{AC}\Rightarrow X$ (aplicar el axioma)

1. **Identificar la familia** a la que hay que aplicarlo (los "conjuntos de los que hay que escoger algo").
2. **Verificar que sus miembros son no vacíos** (casi siempre es donde se usa la hipótesis de $X$).
3. **Quitar el vacío**: trabajar en $\mathcal A\setminus\{\emptyset\}$.
4. **Aplicar** AC y obtener $g$.
5. **Construir con $g$** el objeto que pide la tesis.

**Plantilla (`AC ⇒ 6.4`):**
$$
K_{b}:=F^{-1}(b)\neq\emptyset\ \ \left(F\ \text{sobre}\right)
\Longrightarrow\ \exists\,g\ \text{selectora de } \{K_{b}\}_{b\in B}
\Longrightarrow\ H(b):=g\left(K_{b}\right)\in K_{b}
\Longrightarrow\ F\left(H(b)\right)=b
$$

### B. Probar $X\Rightarrow\text{AC}$ (fragmentos + maximalidad)

1. **Fijar** $S$: el conjunto donde hay que escoger (normalmente $S=s_{0}\setminus\{\emptyset\}$).
2. **Definir $H$** = "fragmentos": funciones parciales que cumplen **localmente** la condición deseada.
3. **$H\neq\emptyset$**: la función vacía siempre está (condición vacía).
4. **$H$ cumple la hipótesis de tu forma $X$**: para 6.7, probar que la unión de toda cadena de fragmentos es un fragmento (truco 3).
5. **Tomar el maximal** $f$ que da $X$.
6. **Probar que el dominio es todo**: si falta $b\in S$, es no vacío, se escoge $k\in b$ y $f\cup\{(b,k)\}$ es fragmento y **contiene propiamente** a $f$: contradicción.

**Plantilla (el paso 6, que es el que decide la prueba):**
$$
\begin{aligned}
\operatorname{dom}f\neq S
&\Longrightarrow \exists\,b\in S\setminus\operatorname{dom}f &&\left(\text{diferencia no vacía}\right)\\
&\Longrightarrow b\neq\emptyset &&\left(S=s_{0}\setminus\{\emptyset\}\right)\\
&\Longrightarrow \exists\,k\in b &&\left(\text{no vacío}\right)\\
&\Longrightarrow f\cup\{(b,k)\}\in H\ \wedge\ f\subsetneq f\cup\{(b,k)\} &&\left(\text{sigue siendo fragmento}\right)\\
&\Longrightarrow \text{contradicción con la maximalidad}
\end{aligned}
$$

### C. Probar una forma a partir de otra (encadenar)

1. **Localiza** en §2.B las dos formas.
2. **Si hay flecha directa**, hazla: es la prueba corta (normalmente 3 líneas).
3. **Si no**, busca un **camino** en el mapa (componer flechas).
4. **Escribe cada eslabón** con su truco entre paréntesis.

**Plantilla (`6.4 ⇒ 6.3`):**
$$
\begin{aligned}
p:\bigcup_{i\in I}A_{i}\to I,\quad p(x):=j\ \text{tal que}\ x\in A_{j}
&\quad\left(\text{bien definida: los } A_{i} \text{ son disjuntos}\right)\\
p\ \text{es sobreyectiva}
&\quad\left(\text{cada } A_{i}\neq\emptyset \text{ aporta un elemento}\right)\\
\Longrightarrow \exists\,g:I\to\bigcup A_{i}\ \text{inversa a la derecha}
&\quad\left(\textbf{6.4}\right)\\
\Longrightarrow B:=\operatorname{ran}g\ \text{cumple}\ B\cap A_{i}=\{g(i)\}
&\quad\left(p\left(g(i)\right)=i\ \Rightarrow\ g(i)\in A_{i}\right)
\end{aligned}
$$

### D. Aplicar el lema de Zorn (6.6)

1. **Declarar** el orden $(A,\le)$.
2. **Tomar una cadena arbitraria** $C\subseteq A$.
3. **Construir una cota superior** $a_{C}\in A$ (existe por hipótesis; hay que **exhibirla**).
4. **Verificar** $c\le a_{C}$ para todo $c\in C$.
5. **Concluir** que existe un maximal (y **no** que existe máximo).

**Plantilla:** $A=$ ideales propios de un anillo, $\le\,=\,\subseteq$. Cadena $C$ ⟹ $\bigcup C$ es ideal propio ⟹ es cota. Zorn ⟹ hay ideal maximal.

### E. Aplicar Tukey (6.9) o Hausdorff (6.8)

1. **Reconoce** si el objeto es "definido por condiciones finitas" (carácter finito) o si es "una cadena maximal".
2. **Para Tukey:** probar **(i)** todo subconjunto de un elemento de $H$ está en $H$; **(ii)** si todos los finitos de $X$ están en $H$, entonces $X\in H$.
3. **Para Hausdorff:** pasa al conjunto $M$ de cadenas, prueba su carácter finito (truco 6) y aplica 6.9.
4. **Verifica no vacuidad** de $H$ ($\emptyset$ casi siempre sirve).

**Plantilla (carácter finito del conjunto de cadenas):**
$$
X\in M\iff \forall\,Y\subseteq X\ \text{finito}:\ Y\in M
\qquad\left(\text{los pares } \{a,b\}\subseteq X \text{ deciden}\right)
$$

### F. Obtener inversa a la derecha / función dentro de una relación

1. **Sobreyectiva:** define las fibras, verifica no vacías, selectora, $H(b)=g(F^{-1}(b))$.
2. **Relación:** si $\operatorname{dom}R=\emptyset$, $f=\emptyset$ ya sirve; si no, la familia $\{R[\{a\}]\}_{a\in\operatorname{dom}R}$ es de no vacíos ⇒ selectora ⇒ $f\subseteq R$ con el mismo dominio.
3. **Verifica** $\operatorname{dom}f=\operatorname{dom}R$ y $f\subseteq R$: esas son **las dos** condiciones.

**Plantilla:** $R=\{(a,b):a<b\}$ en $\mathbb{N}$; $\operatorname{dom}R=\mathbb{N}$; una $f\subseteq R$ con el mismo dominio es $f(a)=a+1$ (¡y no necesita axioma en este caso, porque hay fórmula explícita!).

### G. Bien ordenar un conjunto (Zermelo, 6.10)

1. **Definir** $A^{*}$: los pares $(B,\le_{B})$ con $B\subseteq A$ y $\le_{B}$ buen orden.
2. **Ordenar** $A^{*}$ por **extensión**: $(B,\le)\sqsubseteq(B',\le')$ si $\le\subseteq\le'$.
3. **Cota para cada cadena:** la unión de los buenos órdenes de la cadena (ejercicio previo: unión de buenos órdenes encajados es buen orden).
4. **Zorn** ⇒ existe $(B_{0},\le_{0})$ maximal.
5. **$B_{0}=A$:** si $x\in A\setminus B_{0}$, **yuxtaponer** $x$ al final (truco 4) da un buen orden mayor: contradicción.
6. **Concluir:** $\le_{0}$ bien ordena $A$.

**Plantilla:** $A=\mathbb{R}$: Zermelo garantiza que existe **algún** buen orden, no que sea el usual (el usual **no** es buen orden: $(0,1)$ no tiene mínimo).

### H. Probar un caso finito SIN axioma

1. **Reconoce** que la familia es finita (o que el producto es de finitos factores).
2. **Induce** sobre el cardinal (📘 `-031126` §4.D).
3. **No cites AC**: si lo citas, el profesor lo marca como error conceptual.
4. **Cierra** con el teorema de elección finita.

**Plantilla:** producto finito de no vacíos $\neq\emptyset$: inducción sobre el número de factores; el paso agrega un factor tomando un elemento de él (elección finita ya probada).

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Verifiqué que la familia es **infinita** antes de invocar el axioma (si es finita, es teorema)?
- [ ] ¿Quité el vacío del dominio de la selectora?
- [ ] ¿En 6.3 disyunté la familia con $\{i\}\times A_{i}$ en vez de suponerla disjunta?
- [ ] ¿En Zorn exhibí la cota **dentro del conjunto** para una cadena **arbitraria**?
- [ ] ¿En Tukey verifiqué las **dos** direcciones del carácter finito y la no vacuidad?
- [ ] ¿Distingo maximal de máximo, y cadena maximal de cadena con todos los elementos?
- [ ] ¿En el molde $X\Rightarrow\text{AC}$ cerré con "el dominio es todo"?
- [ ] ¿Cada flecha del diagrama la probé **sin** usar las otras 10?
- [ ] ¿Las cadenas tienen el conector correcto ($\Rightarrow$ cuando el paso no es reversible)?
- [ ] ¿Toda la matemática en $...$ y en bloque con doble dólar, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Estado |
|---|---|
| **AC ⇒ 6.9 (Tukey)** | Se alcanzó a montar el andamiaje: inductivos, $Y_{0}=$ intersección de los inductivos, $Y_{0}$ cadena, contradicción final ($\bigcup Y_{0}\subsetneq F(\bigcup Y_{0})\subseteq\bigcup Y_{0}$). **Se retoma la próxima clase** |
| **6.6 ⇔ 6.7** (los dos sentidos) | Uno es directo (6.7 es caso particular de Zorn con $\le\,=\,\subseteq$); el otro quedó como ejercicio |
| **Consecuencias** de las equivalencias | El profe anunció que vienen después: "eso ya no entra en el parcial" |
| Aplicaciones mencionadas (topología, álgebra) | Solo nombradas: "se salen de lo que queremos aquí" |
