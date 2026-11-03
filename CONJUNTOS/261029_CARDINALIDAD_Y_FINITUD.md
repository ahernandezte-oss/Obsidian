# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 29/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261029_CARDINALIDAD_Y_FINITUD.md`
> - **Fecha de transcripción:** 29/10/2026 (`DDMMAA` = `291026`)
> - **Tema principal:** CARDINALIDAD — potenciación cardinal (5.4) · dominancia (5.6) · Cantor (5.8) · punto fijo de conjuntos · Cantor–Bernstein–Schröder (5.11) · finitud y cardinal finito
> - **Fuente:** transcripción de clase (clase completa). Lo que **no** viene de la transcripción va marcado con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261029_CARDINALIDAD_Y_FINITUD` §2.D».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Qué le están pidiendo: igualdad de tamaño, desigualdad de tamaño, o un conteo?**
   - Igualdad de tamaño (existe biyección) → **equipotencia** $A\approx B$ (§2.A · §4.A).
   - Desigualdad de tamaño (existe inyección y no biyección) → **dominancia** $A\preccurlyeq B$ / $A\prec B$ (§2.B · §4.B).
   - Conteo de funciones o de subconjuntos → **potenciación / conjunto de partes** (§2.A · §2.C · §4.C).
2. **Paso 1 — ¿Aparecen números naturales?** Si el enunciado nombra $\mathbb{N}$, un natural $n$, "finito", "número de elementos" o $\lvert A\rvert$ → **§2.E**, y la demostración se hace por **inducción** sobre el natural (§4.H).
3. **Paso 2 — ¿Es una prueba de imposibilidad ("no existe", "no puede ser", "es estricta")?** → **diagonal de Cantor** (§2.C · §4.D) o **contradicción con la minimalidad** del natural (§3.7).
4. **Paso 3 — ¿Solo tiene inyecciones, una en cada sentido?** → **Cantor–Bernstein–Schröder** (§2.D · §4.F).
5. **Paso 4 — ¿Le dan una función $F:\mathcal{P}(A)\to\mathcal{P}(A)$ creciente?** → **lema de punto fijo** (§2.D · §4.E).

**Tabla de decisión:**

| Si el enunciado dice…                                                                                     | Herramienta                          | Fórmula base                                                              | 👉 Ir a                    |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------ | ------------------------------------------------------------------------- | -------------------------- |
| "son equipotentes", "mismo cardinal", "misma cantidad de elementos", "demuestre que existe una biyección" | **Equipotencia**                     | $A\approx B\iff\exists\,f:A\to B$ biyectiva                               | **§2.A** · §4.A            |
| "existe $f$ inyectiva de $A$ en $B$", "$A\subseteq B$", "$\mathcal{P}(A)$"                                | **Dominancia**                       | $A\preccurlyeq B\iff\exists\,f:A\to B$ inyectiva                          | **§2.B** · §4.B            |
| "dominancia estricta", "hay inyección pero no biyección", "tiene más elementos que"                       | **Dominancia estricta**              | $A\prec B\iff A\preccurlyeq B$ y $A\not\approx B$                         | **§2.B** · §4.B            |
| "cuántas funciones van de $A$ en $B$"                                                                     | **Potenciación cardinal**            | $\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}$           | **§2.A** · §4.C            |
| "cuántos subconjuntos tiene", "conjunto de partes", $\mathcal{P}(A)$ con $\lvert A\rvert$ conocido        | **Conjunto de partes**               | $\left\lvert\mathcal{P}(A)\right\rvert=2^{\lvert A\rvert}$                | **§2.C** · **§2.E** · §4.C |
| "ningún conjunto es equipotente con su conjunto de partes"                                                | **Teorema de Cantor (5.8)**          | $A\prec\mathcal{P}(A)$                                                    | **§2.C** · §4.D            |
| "hay una inyección de $A$ en $B$ y una de $B$ en $A$"                                                     | **Cantor–Bernstein–Schröder (5.11)** | $A\preccurlyeq B\ \wedge\ B\preccurlyeq A\Rightarrow A\approx B$          | **§2.D** · §4.F            |
| "sea $F:\mathcal{P}(A)\to\mathcal{P}(A)$ creciente con $\subseteq$"                                       | **Punto fijo de conjuntos**          | $F(X)\subseteq F(Y)$ si $X\subseteq Y$                                    | **§2.D** · §4.E            |
| "es finito", "cuántos elementos tiene", "$\lvert A\rvert$", "cardinal de $A$"                             | **Cardinal finito**                  | $A$ finito $\iff\exists\,n\in\mathbb{N}:A\preccurlyeq n$                  | **§2.E** · §4.G            |
| "todo subconjunto propio está dominado estrictamente", "ningún subconjunto propio equipotente"            | **Finitud de Dedekind / naturales**  | $B\subsetneq A\Rightarrow B\prec A$                                       | **§2.E** · §3.5            |
| "hay $f:A\to A$ inyectiva y no sobreyectiva"                                                              | **Infinitud**                        | $f$ inyectiva no sobre $\Rightarrow A$ infinito                           | **§2.E** · **§3.6**        |
| "conjuntos disjuntos, únase y cuéntese", "$\lvert A\cup B\rvert$"                                         | **Aritmética de cardinales finitos** | $\lvert A\cup B\rvert=\lvert A\rvert+\lvert B\rvert-\lvert A\cap B\rvert$ | **§2.E** · §4.G            |

**Frases literales del profe → método:**

- «No igualdad de conjunto, sino de **equipotencia**.» → las propiedades 5.4 se escriben con $\approx$, nunca con $=$.
- «Yo prefiero esta notación porque cuando escriba $3^{4}$ la pregunta es si estoy diciendo la potencia de números naturales o las funciones que van de $4$ a $3$.» → usar $B^{A}$ para funciones y nunca confundirlo con la potencia numérica.
- «La dominancia es **estricta** cuando $A$ domina a $B$ pero no es equipotente.» → para $\prec$ hay que exhibir inyección **y** negar la biyección.
- «Cojo los que están contenidos en su imagen y los que contienen a su imagen: interseco y uno.» → así se construyen el mínimo y el máximo punto fijo (§2.D).
- «El truco es quitar la pareja que no sirve y meter la que sobraba.» → teorema del antecesor (§2.E, T1).
- «Parece una prueba constructiva, pero calcular ese punto fijo no es fácil.» → CBS da existencia, no una fórmula cerrada para $D$.
- «Vamos a definir cardinal **solamente para el caso finito** y dejar pendiente los cardinales infinitos.» → todo lo cuantitativo de esta clase vive en $n\in\mathbb{N}$.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Equipotencia y potenciación cardinal

**Definición (equipotencia):**

$$
A\approx B \iff \exists\,f:A\to B \text{ biyectiva}
$$

**Conjunto de funciones** (notación del curso, preferida):

$$
B^{A}:=\{\,f \mid f:A\to B\,\}
$$

**Propiedades de la potenciación cardinal (teorema 5.4):**

$$
A^{B\cup C}\approx A^{B}\times A^{C}\qquad\text{(si }B\cap C=\emptyset\text{)}
$$

$$
(A\times B)^{C}\approx A^{C}\times B^{C}
$$

$$
\left(A^{B}\right)^{C}\approx A^{B\times C}
$$

**Correspondencia con la potenciación numérica** (indica qué teorema esperar):

| Potencia numérica | Potenciación cardinal | Condición |
|---|---|---|
| $x^{m+n}=x^{m}x^{n}$ | $A^{B\cup C}\approx A^{B}\times A^{C}$ | $B\cap C=\emptyset$ |
| $(xy)^{m}=x^{m}y^{m}$ | $(A\times B)^{C}\approx A^{C}\times B^{C}$ | — |
| $\left(x^{m}\right)^{n}=x^{mn}$ | $\left(A^{B}\right)^{C}\approx A^{B\times C}$ | — |

**Conteo de funciones (caso finito):**

$$
\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}
$$

> **🔤 Diccionario:**
> - $A,B,C$: conjuntos cualesquiera (no necesariamente finitos, no necesariamente de números).
> - $A\approx B$: "$A$ es equipotente con $B$"; existe biyección entre ellos. **No** significa $A=B$.
> - $f:A\to B$ biyectiva: inyectiva (uno a uno) y sobreyectiva (todo $B$ es imagen).
> - $B^{A}$: conjunto de **todas** las funciones de $A$ en $B$ (en varios libros se escribe ${}^{A}B$).
> - $A\times B$: producto cartesiano (parejas ordenadas).
> - $\lvert A\rvert$: cardinal de $A$; en esta clase existe **solo** si $A$ es finito.
> - $B\cap C=\emptyset$: condición obligatoria en la primera propiedad (exponentes disjuntos).

---

### B. Dominancia cardinal

**Definición (dominancia):**

$$
A\preccurlyeq B \iff \exists\,f:A\to B \text{ inyectiva}
$$

**Dominancia estricta:**

$$
A\prec B \iff A\preccurlyeq B \ \wedge\ A\not\approx B
$$

**Propiedades (5.6):**

| # | Propiedad | Por qué vale |
|---|---|---|
| 1 | $A\preccurlyeq A$ | la identidad es inyectiva |
| 2 | $A\subseteq B\Rightarrow A\preccurlyeq B$ | la inclusión $i:A\to B$, $i(x)=x$, es inyectiva |
| 3 | $A\subseteq\mathcal{P}(A)$ vía $a\mapsto\{a\}$ | el singleton es inyectivo |
| 4 | $\emptyset\preccurlyeq A$ | $\emptyset\subseteq A$ y la inclusión es inyectiva |
| 5 | $A\preccurlyeq B$ y $B\preccurlyeq C\Rightarrow A\preccurlyeq C$ | composición de inyectivas es inyectiva |
| 6 | $A\preccurlyeq B\iff\exists\,D\subseteq B$ con $A\approx D$ | se toma $D=f[A]$ (rango) y se restringe el codominio |
| 7 | $A\approx D$ y $D\subseteq B\Rightarrow A\preccurlyeq B$ | se compone la biyección con la inclusión |
| 8 | $A\preccurlyeq B\iff A\approx D$ para algún $D\subseteq B$ | combina 6 con la restricción al rango |
| 9 | $A\approx B\Rightarrow A\preccurlyeq B$ y $B\preccurlyeq A$ | toda biyección es inyectiva (el recíproco es 5.11) |

> **🔤 Diccionario:**
> - $A\preccurlyeq B$: "$A$ es dominado por $B$" / "$B$ domina a $A$". La letra tipo $c$ recuerda que es **dominancia cardinal**, no otro orden.
> - $A\prec B$: dominancia **estricta** (inyectiva existe, biyectiva no existe).
> - $f[A]$: imagen directa de $A$ por $f$; es el conjunto de llegada real (rango) de $f$.
> - $D$: subconjunto del codominio que copia a $A$ dentro de $B$.
> - $i(x)=x$: **inclusión**; es la identidad con codominio cambiado a un conjunto mayor.

---

### C. Conjunto de partes y teorema de Cantor (5.8)

**Conjunto de partes:**

$$
\mathcal{P}(A)=\{\,X \mid X\subseteq A\,\}
$$

**Inyección natural de $A$ en $\mathcal{P}(A)$:**

$$
g:A\to\mathcal{P}(A),\qquad g(a)=\{a\}
$$

**Teorema de Cantor (5.8):**

$$
A\prec\mathcal{P}(A)\qquad\text{(ningún conjunto es equipotente con su conjunto de partes)}
$$

**Conjunto diagonal de la demostración** (para $f:A\to\mathcal{P}(A)$ cualquiera):

$$
X=\{\,x\in A \mid x\notin f(x)\,\}
$$

> **🔤 Diccionario:**
> - $\mathcal{P}(A)$: conjunto de todos los subconjuntos de $A$ (conjunto de partes).
> - $X\subseteq A$: $X$ es subconjunto de $A$.
> - $g(a)=\{a\}$: manda cada elemento a su **singleton**; es inyectiva, por eso $A\preccurlyeq\mathcal{P}(A)$.
> - $f(x)$: aquí $f(x)$ es un **conjunto** (un elemento de $\mathcal{P}(A)$), por eso tiene sentido preguntar si $x\in f(x)$.
> - $X$: subconjunto "diagonal"; depende de $f$ y **no puede** estar en la imagen de $f$.
> - $\notin$: "no pertenece".

---

### D. Lema de punto fijo y teorema de Cantor–Bernstein–Schröder (5.11)

**Definición (función creciente con $\subseteq$):**

$$
X\subseteq Y\ \Rightarrow\ F(X)\subseteq F(Y)
$$

**Lema de punto fijo (de conjuntos).** Si $F:\mathcal{P}(A)\to\mathcal{P}(A)$ es creciente, entonces:

$$
T:=\bigcap\{\,X\subseteq A \mid F(X)\subseteq X\,\}\quad\text{y}\quad T':=\bigcup\{\,X\subseteq A \mid X\subseteq F(X)\,\}
$$

cumplen $F(T)=T$ y $F(T')=T'$, y además $T$ es el **mínimo** punto fijo y $T'$ el **máximo** punto fijo (con el orden $\subseteq$).

**Lema previo a Cantor–Bernstein.** Si $f:A\to B$ y $g:B\to A$ son inyectivas, entonces existe $D\subseteq A$ tal que:

$$
A\setminus D=g\left[\,B\setminus f[D]\,\right]
$$

Se obtiene como punto fijo de la función creciente:

$$
h:\mathcal{P}(A)\to\mathcal{P}(A),\qquad h(X)=A\setminus g\left[\,B\setminus f[X]\,\right]
$$

**Teorema de Cantor–Bernstein–Schröder (5.11):**

$$
f:A\to B \text{ inyectiva}\ \wedge\ g:B\to A \text{ inyectiva}\ \Longrightarrow\ A\approx B
$$

**Biyectiva construida** (con $D$ el punto fijo del lema anterior):

$$
\Phi:A\to B,\qquad
\Phi(x)=
\begin{cases}
f(x), & x\in D\\[2pt]
g^{-1}(x), & x\in A\setminus D
\end{cases}
$$

donde $g^{-1}:A\setminus D\to B\setminus f[D]$ es la inversa de $g$ restringida a $B\setminus f[D]$.

> **🔤 Diccionario:**
> - $F,h$: funciones que reciben y devuelven **subconjuntos** de $A$ ($\mathcal{P}(A)\to\mathcal{P}(A)$).
> - $T$: intersección de todos los $X$ que **contienen** a su imagen; es el punto fijo mínimo.
> - $T'$: unión de todos los $X$ que **están contenidos** en su imagen; es el punto fijo máximo.
> - Punto fijo: $F(T)=T$ (el conjunto es igual a su imagen).
> - $A\setminus D$: diferencia (los elementos de $A$ que no están en $D$).
> - $f[D]$: imagen directa del conjunto $D$ (no de un elemento).
> - $g^{-1}$: inversa de $g$ restringida; existe porque $g$ es inyectiva sobre $B\setminus f[D]$ y su imagen es exactamente $A\setminus D$.
> - $\subseteq$: es **orden parcial** en $\mathcal{P}(A)$, **no total**; por eso hay mínimo y máximo de los puntos fijos, pero los puntos fijos intermedios no se comparan entre sí.

---

### E. Finitud, infinitud y cardinal finito

**Las dos definiciones clásicas:**

| Definición | Enunciado | Qué busca |
|---|---|---|
| **Kuratowski** (la del curso) | $A$ finito $\iff \exists\,n\in\mathbb{N}: A\approx n$ | medir con números naturales |
| **Dedekind** | $A$ **infinito** $\iff$ algún subconjunto propio de $A$ es equipotente con $A$ | definir finitud **sin** usar $\mathbb{N}$ |

**Definición del curso (cardinal finito):**

$$
A \text{ finito} \iff \exists\,n\in\mathbb{N}\ \text{tal que}\ A\preccurlyeq n
\qquad\qquad
A \text{ infinito} \iff \text{ningún natural domina a } A
$$

$$
\lvert A\rvert := \text{el único } n\in\mathbb{N} \text{ con } A\approx n
$$

**Teoremas sobre naturales usados en la clase:**

| # | Enunciado | Idea de la prueba |
|---|---|---|
| **T1** (antecesor) | Si $f:A\to n$ es inyectiva y **no** sobreyectiva ($n\in\mathbb{N}$), existe $h:A\to n-1$ inyectiva | si $n-1\notin\operatorname{ran}f$ se deja la misma $f$; si $n-1\in\operatorname{ran}f$ se **quita esa pareja** y se manda su preimagen al elemento que sobraba |
| **T2** | $A\subsetneq n\Rightarrow A\prec n$ (ningún subconjunto propio de un natural es equipotente con él) | inducción sobre $n$; para $B\subseteq n+1$ propio hay tres casos: $B\subsetneq n$, $B=n$, $n\in B$; los tres dan contradicción con el truco de quitar parejas |
| **T3** | $m,n\in\mathbb{N}$ y $m\approx n\Rightarrow m=n$ | si $m\neq n$, uno pertenece al otro y sería un natural equipotente con un subconjunto propio (contradice T2) |
| **T4** | Si $A\prec n$, existe $k\in n$ con $A\approx k$ | $k=\min\{m\in\mathbb{N}: A\preccurlyeq m\}$; si $f:A\to k$ no fuera sobre, T1 daría $A\preccurlyeq k-1$, contradiciendo la minimalidad |
| **T5** | Si $m\in n$, ninguna $f:n\to m$ es inyectiva | la inclusión $m\to n$ es inyectiva y con 5.11 habría biyección, contradiciendo T2 |

**Propiedades del cardinal finito:**

$$
A\approx B \iff \lvert A\rvert=\lvert B\rvert
\qquad
\lvert n\rvert=n
\qquad
B\subseteq A \Rightarrow \lvert B\rvert\le\lvert A\rvert
$$

$$
f:A\to\lvert A\rvert \text{ inyectiva} \Longrightarrow f \text{ es biyectiva}
\qquad(\text{principio del palomar})
$$

$$
B\subsetneq A \Rightarrow \lvert B\rvert<\lvert A\rvert
\qquad
A \text{ finito} \Rightarrow \text{ningún subconjunto propio es equipotente con } A
$$

**Aritmética de cardinales finitos:**

$$
\lvert A\cup B\rvert=\lvert A\rvert+\lvert B\rvert-\lvert A\cap B\rvert
$$

$$
\mathcal{A} \text{ finita, elementos dos a dos disjuntos} \Longrightarrow \left\lvert\bigcup\mathcal{A}\right\rvert=\sum_{X\in\mathcal{A}}\lvert X\rvert
$$

$$
\left\lvert\mathcal{P}(A)\right\rvert=2^{\lvert A\rvert}
\qquad
\left\lvert B^{A}\right\rvert=\lvert B\rvert^{\lvert A\rvert}
\qquad
\mathcal{P}(A)\approx 2^{A}
$$

$$
A \text{ finito},\ a\in A \Longrightarrow \left\lvert A\setminus\{a\}\right\rvert=\lvert A\rvert-1
$$

> **🔤 Diccionario:**
> - $n\in\mathbb{N}$: un número natural visto como conjunto ($0=\emptyset$, $n+1=n\cup\{n\}$).
> - $n-1=\bigcup n$: **antecesor** de $n$; para $n=0$ se tiene $\bigcup\emptyset=\emptyset$ (y entonces $A=\emptyset$).
> - $A\subsetneq n$: subconjunto propio (contenido y distinto).
> - $A\preccurlyeq n$: "un natural domina a $A$"; es la definición de finito que usa el curso.
> - $\lvert A\rvert$: cardinal de $A$; **existe solo si $A$ es finito**, y es único por T3.
> - $\operatorname{ran}f$: rango o imagen de $f$.
> - $\min$: mínimo de un conjunto de naturales (existe siempre que el conjunto no sea vacío, por buen orden).
> - $2^{A}$: conjunto de funciones de $A$ en $\{0,1\}$; se identifica con $\mathcal{P}(A)$ por la función característica.
> - $\sum_{X\in\mathcal{A}}\lvert X\rvert$: suma de los cardinales de los conjuntos de la colección $\mathcal{A}$.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Tres símbolos que no se confunden

| Símbolo | Significa | Se prueba con | No confundir con |
|---|---|---|---|
| $A=B$ | igualdad de conjuntos | doble contenencia $A\subseteq B$ y $B\subseteq A$ | $\approx$ (pueden ser equipotentes y distintos) |
| $A\approx B$ | equipotencia (mismo cardinal) | **una** biyección | igualdad; $3^{4}$ como número |
| $A\preccurlyeq B$ | dominancia | **una** inyección | biyección (no se pide sobre) |
| $A\prec B$ | dominancia estricta | inyección **y** negación de biyección | $\preccurlyeq$ |

### 3.2 Reglas de bolsillo

1. **$\approx$ nunca se escribe con $=$.** Las propiedades 5.4 son equipotencias, no igualdades de conjuntos.
2. **Primera propiedad 5.4 exige $B\cap C=\emptyset$.** Sin exponentes disjuntos no se aplica.
3. **Estricta = falta la sobreyectividad.** Para $\prec$ hay que probar que **no** existe biyección (normalmente por contradicción).
4. **Cantor da una jerarquía infinita:** $A\prec\mathcal{P}(A)\prec\mathcal{P}(\mathcal{P}(A))\prec\cdots$; nunca hay "el conjunto más grande".
5. **Dos definiciones de finitud no son gratis equivalentes.** Kuratowski $\Rightarrow$ Dedekind se prueba en el curso; el recíproco necesita una parte débil del **axioma de elección** (elección numerable). Sin elección existen conjuntos finitos de Dedekind que no son finitos de Kuratowski `➕`.
6. **El curso no usa Dedekind.** Se define finito con naturales porque ahí se tienen las dos herramientas fuertes: **inducción** y **recursión**.
7. **Contradicción por minimalidad:** si aparece un natural "más pequeño que domina", se toma el mínimo y se aplica T1 para bajar uno más → contradicción (así se prueba T4 y el cardinal).
8. **Punto fijo: intersección = mínimo, unión = máximo.** Si $T=T'$ el punto fijo es único.
9. **$\subseteq$ no es orden total** en $\mathcal{P}(A)$: los puntos fijos existen (mínimo y máximo) aunque los intermedios no se comparen.
10. **$\mathcal{P}(A)$ infinito $\Rightarrow A$ infinito** (pues $A\preccurlyeq\mathcal{P}(A)$ y la dominancia es transitiva; si $A$ fuera finito, $\mathcal{P}(A)$ también).
11. **Inyectiva no sobre sobre el mismo conjunto $\Rightarrow$ infinito.** La función sucesor en $\mathbb{N}$ es el ejemplo canónico (inyectiva, no sobreyectiva).
12. **Palomar:** en conjuntos finitos, inyectiva $A\to A$ ya es biyectiva; en infinitos, no.

### 3.3 Los tres casos del "truco de quitar parejas"

| Situación con $f:A\to n$ inyectiva no sobre | Acción |
|---|---|
| El elemento que falta ($n-1$) **no** está en el rango | se conserva la **misma** $f$ y se restringe el codominio a $n-1$ |
| $n-1$ **sí** está en el rango, y algo sobra | se **quita** la pareja $\left(a_{0},\,n-1\right)$ y se envía $a_{0}$ al elemento que sobraba |
| Se necesita bajar dos niveles | se quitan **dos** parejas (máximo) y se añade **una** |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Demostrar $A\approx B$ (equipotencia)

1. **Construir** explícitamente una función $f:A\to B$.
2. **Inyectividad:** suponer $f(x)=f(y)$ y deducir $x=y$.
3. **Sobreyectividad:** dado $b\in B$, exhibir $x\in A$ con $f(x)=b$ (o construir la inversa).
4. **Verificar** que dominio y codominio son los del enunciado.

**Plantilla:** $A=\mathbb{N}$, $B=\{2k : k\in\mathbb{N}\}$. Sea $f(k)=2k$. (2) $2x=2y\Rightarrow x=y$. (3) Si $b\in B$, $b=2k$ y $f(k)=b$. Luego $\mathbb{N}\approx B$ y $B\subsetneq\mathbb{N}$.

### B. Demostrar $A\preccurlyeq B$ o $A\prec B$

1. **Elegir la inyección:** identidad, inclusión, singleton, restricción al rango, o composición de inyectivas.
2. **Probar inyectividad** (paso 2 del algoritmo A).
3. **Si piden estricta**, suponer que existe biyección y **llegar a contradicción** (Cantor, minimalidad de un natural, T2).
4. **Verificar** que no se usó sobreyectividad innecesariamente.

**Plantilla:** $A\subseteq B$. La inclusión $i:A\to B$, $i(x)=x$, es inyectiva, luego $A\preccurlyeq B$. Para estricta con $B=n$ natural y $A\subsetneq n$: si $A\approx n$, $n$ sería equipotente con un subconjunto propio, contra T2.

### C. Contar funciones y subconjuntos

1. **Identificar** cuántos elementos tiene el dominio ($m$) y el codominio ($k$).
2. **Funciones:** cada elemento del dominio elige libremente su imagen → $k^{m}$.
3. **Subconjuntos:** cada elemento decide "entra / no entra" → $2^{m}$.
4. **Verificar** con un caso pequeño (p. ej. $m=3$: $2^{3}=8$ subconjuntos).

**Plantilla:** funciones de un conjunto de $4$ elementos en uno de $3$: $3\cdot3\cdot3\cdot3=3^{4}=81$. Subconjuntos de un conjunto de $3$: $2^{3}=8$.

### D. Demostrar el teorema de Cantor ($A\prec\mathcal{P}(A)$)

1. **Dominancia:** $g(a)=\{a\}$ es inyectiva → $A\preccurlyeq\mathcal{P}(A)$.
2. **Suponer** que existe $f:A\to\mathcal{P}(A)$ **sobreyectiva**.
3. **Definir** $X=\{x\in A: x\notin f(x)\}$; como $X\subseteq A$, $X\in\mathcal{P}(A)$.
4. **Usar la sobreyectividad:** existe $b\in A$ con $f(b)=X$.
5. **Dicotomía:** si $b\in X$ entonces $b\notin f(b)=X$ (contradicción); si $b\notin X$ entonces $b\in f(b)=X$ (contradicción).
6. **Concluir:** no hay sobreyección, luego no hay biyección, luego $A\prec\mathcal{P}(A)$.

**Plantilla:** con $A=\{1,2\}$ y $f(1)=\{1,2\}$, $f(2)=\emptyset$, resulta $X=\{x: x\notin f(x)\}=\{2\}$, y $\{2\}$ no está en la imagen.

### E. Aplicar el lema de punto fijo

1. **Verificar crecimiento:** $X\subseteq Y\Rightarrow F(X)\subseteq F(Y)$ (imagen directa y complemento invierten/mantienen el orden en el sentido correcto).
2. **Escribir** $T=\bigcap\{X: F(X)\subseteq X\}$ (no vacío: $A$ siempre está) y $T'=\bigcup\{X: X\subseteq F(X)\}$.
3. **Doble contenencia para $F(T)=T$:** como $T\subseteq X$ para cada $X$ de la familia, $F(T)\subseteq F(X)\subseteq X$, luego $F(T)\subseteq T$. Después, $F(T)\subseteq T\Rightarrow F(F(T))\subseteq F(T)$, así que $F(T)$ está en la familia y $T\subseteq F(T)$.
4. **Para $T'$** el argumento es el mismo "hacia el otro lado": cada $X$ de la familia cumple $X\subseteq T'$, luego $F(X)\subseteq F(T')$ y $X\subseteq F(X)\subseteq F(T')$, de donde $T'\subseteq F(T')$; y $T'\subseteq F(T')$ da $F(T')\subseteq F(F(T'))$, así que $F(T')\subseteq T'$.
5. **Extremos:** cualquier punto fijo $S$ cumple $S\subseteq F(S)$, luego $S\subseteq T'$, y $F(S)\subseteq S$, luego $T\subseteq S$. Así $T$ es mínimo y $T'$ máximo.

**Plantilla:** $A=\{1,2\}$, $F(X)=X\cup\{1\}$. Creciente. $T=\bigcap\{X: X\cup\{1\}\subseteq X\}=\{1\}$ y $F(\{1\})=\{1\}$: punto fijo.

### F. Demostrar $A\approx B$ con Cantor–Bernstein–Schröder

1. **Exhibir** $f:A\to B$ inyectiva y $g:B\to A$ inyectiva.
2. **Construir** $h(X)=A\setminus g\left[B\setminus f[X]\right]$ y comprobar que es creciente.
3. **Tomar** el punto fijo $D$ de $h$: entonces $A\setminus D=g\left[B\setminus f[D]\right]$.
4. **Definir** $\Phi(x)=f(x)$ si $x\in D$; $\Phi(x)=g^{-1}(x)$ si $x\in A\setminus D$.
5. **Verificar:** dominios disjuntos (es función), rangos disjuntos $f[D]$ y $B\setminus f[D]$ (es inyectiva), y $f[D]\cup\left(B\setminus f[D]\right)=B$ (es sobreyectiva).
6. **Concluir** $A\approx B$. Anotar que la prueba es constructiva pero **calcular $D$ no es fácil**.

**Plantilla:** $A=[0,1]$, $B=[0,2]$, $f(x)=x$ inyectiva, $g(x)=x/2$ inyectiva. CBS garantiza $[0,1]\approx[0,2]$ sin exhibir la biyección a mano.

### G. Calcular un cardinal finito

1. **Escribir** el conjunto como operación de conjuntos: unión, diferencia, producto, partes, conjunto de funciones.
2. **Sustituir** cada pieza por su cardinal (si es finita).
3. **Aplicar** la fórmula correspondiente (inclusión–exclusión, suma de disjuntos, $2^{m}$, $k^{m}$).
4. **Verificar** que el resultado es un natural y que respeta $\lvert B\rvert\le\lvert A\rvert$ cuando $B\subseteq A$.

**Plantilla:** $\lvert A\rvert=5$, $\lvert B\rvert=4$, $\lvert A\cap B\rvert=2$ → $\lvert A\cup B\rvert=5+4-2=7$; y $\left\lvert\mathcal{P}(A\cap B)\right\rvert=2^{2}=4$.

### H. Inducción sobre el cardinal (para propiedades de finitos)

1. **Formular** $P(n)$: "para todo $A$ con $\lvert A\rvert=n$, se cumple …".
2. **Base $n=0$:** $A=\emptyset$; verificar el caso (si $\mathcal{P}(\emptyset)$ es finito, se cumple trivialmente).
3. **Paso inductivo:** sea $\lvert B\rvert=n+1$; elegir $b\in B$ y aplicar la hipótesis a $B\setminus\{b\}$, que tiene cardinal $n$ (usar $\left\lvert B\setminus\{b\}\right\rvert=\lvert B\rvert-1$).
4. **Recomponer** con la fórmula de unión disjunta, porque $B=\left(B\setminus\{b\}\right)\cup\{b\}$ y la unión es disjunta.
5. **Cerrar:** la propiedad vale para todo natural, luego para todo conjunto finito.

**Plantilla (probar $\left\lvert\mathcal{P}(A)\right\rvert=2^{\lvert A\rvert}$):** $n=0$: $\mathcal{P}(\emptyset)=\{\emptyset\}$, cardinal $1=2^{0}$. Paso: $B$ con $\lvert B\rvert=n+1$, $b\in B$. Los subconjuntos de $B$ se parten en los que **no** contienen $b$ (son $\mathcal{P}\left(B\setminus\{b\}\right)$, cardinal $2^{n}$ por hipótesis) y los que **sí** lo contienen (biyectivos con los anteriores vía $X\mapsto X\cup\{b\}$, también $2^{n}$). Total: $2^{n}+2^{n}=2^{n+1}$.

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Distingo $A=B$, $A\approx B$, $A\preccurlyeq B$, $A\prec B$ antes de empezar?
- [ ] ¿En 5.4 verifiqué $B\cap C=\emptyset$?
- [ ] ¿Para $\prec$ probé **también** que no hay biyección?
- [ ] ¿En Cantor usé $X=\{x: x\notin f(x)\}$ y la sobreyectividad para llegar a la dicotomía?
- [ ] ¿En punto fijo probé crecimiento, $F(T)=T$ y $F(T')=T'$ por doble contenencia?
- [ ] ¿En CBS verifiqué dominios disjuntos y rangos disjuntos?
- [ ] ¿Usé solo naturales para cardinales (los infinitos **no** están definidos en esta clase)?
- [ ] ¿Justifiqué la unicidad de $\lvert A\rvert$ con T3?
- [ ] ¿Toda la matemática en $...$ en línea y $$…$$ en bloque, sin bloques de código?
- [ ] ¿Cada fórmula tiene su diccionario justo debajo?
