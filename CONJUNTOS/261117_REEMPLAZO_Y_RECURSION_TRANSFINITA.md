# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 17/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261117_REEMPLAZO_Y_RECURSION_TRANSFINITA.md`
> - **Fecha de transcripción:** 17/11/2026 (`AAMMDD` = `261117`)
> - **Tema principal:** AXIOMA DE REEMPLAZO Y RECURSIÓN TRANSFINITA — consecuencias del reemplazo, norma de un buen orden (todo buen orden ≅ único ordinal), recursión sobre buenos órdenes y sobre ordinales, inducción transfinita y funcionales sobre la clase $\mathbf{Ord}$.
> - **Continuidad:** retoma el reemplazo que se **introdujo** en 📘 `261112_NUMEROS_ORDINALES` §2.G y el teorema de representación que allí quedó **enunciado** (§6). **No repite** la teoría de ordinales: la usa y la cita.
> - **Fuente:** transcripción de clase. Lo agregado o completado por mí va con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261117_REEMPLAZO_Y_RECURSION_TRANSFINITA` §2.C (recursión transfinita)».

**📎 Prerrequisitos que se dan por sabidos:**
- **Ordinales**: definición, propiedades, sucesor/límite, mínimo y supremo 📘 `261112` §2.C–§2.F.
- **Reemplazo**: propiedad funcional y esquema 📘 `261112` §2.G (aquí se usa en serio).
- **Comparabilidad de buenos órdenes**: dados dos buenos órdenes, o son isomorfos, o uno es isomorfo a un segmento inicial del otro ➕ (usado en §2.B).
- **Recursión simple en $\omega$** con función de paso $G:\mathbb{N}\times A\to A$ 📘 `261015` §2.E.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Qué hay que producir?** Si es **un conjunto** a partir de otro, es **reemplazo** (§2.A). Si es **una función definida paso a paso**, es **recursión** (§2.C–§2.D).
2. **Paso 1 — ¿La recursión es sobre $\omega$ o sobre un buen orden arbitrario?** Sobre $\omega$ (o un ordinal) → §2.D. Sobre un buen orden del que no se conoce el orden → §2.C.
3. **Paso 2 — ¿Hay que definir sobre *todos* los ordinales?** Entonces no se puede usar reemplazo sobre $\mathbf{Ord}$: se define **por niveles** y se prueba consistencia (§2.F).
4. **Paso 3 — ¿Hay que probar una propiedad de todos los ordinales?** → **inducción transfinita** (§2.E). Si la propiedad se parte en $0$, sucesor y límite, usar la forma **por pasos**.
5. **Paso 4 — ¿Se pide el ordinal de un buen orden?** → **norma** (§2.B). Recordar: el ordinal va **siempre con $\in$**; si se cambia el orden, cambia el ordinal.

**Tabla de decisión:**

| Si el enunciado pide… | Concepto | Herramienta | 👉 Ir a |
|---|---|---|---|
| «demuestre que este conjunto existe» | reemplazo | imagen de un conjunto por propiedad funcional | **§2.A** · §4.A |
| «todo buen orden es isomorfo a un único ordinal» | norma | reemplazo $+$ comparabilidad | **§2.B** · §4.B |
| «defina $F$ por recursión sobre un buen orden» | recursión | restricciones $F\restriction A_{<a}$ | **§2.C** · §4.C |
| «$f(0)=a$, $f(n+1)=\varphi(f(n))$» | recursión en $\omega$ | propiedad funcional sobre funciones | **§2.D** · §4.D |
| «pruebe $P(\alpha)$ para todo ordinal $\alpha$» | inducción | fuerte o por pasos | **§2.E** · §4.E |
| «defina una operación para todo ordinal» | funcional sobre $\mathbf{Ord}$ | definir por niveles y pegar | **§2.F** · §4.F |
| «¿este axioma sobra?» | consecuencias | separación y pares son teoremas | **§2.A** |

**Frases literales del profe → método:**

- «La propiedad funcional lleva el **germen de la función**, solo que no la defino como función porque no puedo.» → no hay conjunto de todos los conjuntos (§2.A).
- «El reemplazo **no forma conjuntos de la nada**: yo ya tengo que tener algo formado y reemplazo ese algo.» → siempre hay un conjunto de partida (§2.A).
- «El ordinal **siempre va con la pertenencia**; si le cambia el orden, cambia el ordinal.» → $\omega$ con otro orden ya no es $\omega$ (§2.B).
- «Trabajo con **pedazos de funciones**, no directamente con la función que estoy armando.» → el truco de la recursión (§2.C).
- «La inducción transfinita es la misma de los naturales, solo que el orden es la pertenencia.» → §2.E.
- «Sobre la clase ordinal **no puedo usar reemplazo**, porque no existe el conjunto de todos los ordinales.» → §2.F.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS

### A. Axioma de reemplazo y sus consecuencias

$$
P(a,b)\ \text{es funcional}
\iff
\forall\,a\ \exists!\,b:\ P(a,b)
$$

$$
\text{Reemplazo (forma de imagen):}\qquad
(\forall A)\left[\left((\forall a\in A)(\exists!\,b)\,P(a,b)\right)\ \Longrightarrow\ (\exists B)(\forall y)\left(y\in B\iff(\exists a\in A)\,P(a,y)\right)\right]
$$

> ⚠️ **Forma débil (no usar para separación).** La versión «existe $B$ tal que $(\forall a\in A)(\exists b\in B)\,P(a,b)$» solo dice que $B$ **contiene** las imágenes; con ella no se puede probar que $B$ sea exactamente el conjunto buscado. La forma de **imagen** es la que se usa en todo el tema (y la que exige el ejercicio de separación).

**Lo que se deriva** (➕: la clase lo discute; aquí queda cerrado):

| Axioma | ¿Sale de Reemplazo? | Cómo |
|---|---|---|
| **Separación** (comprensión) | **Sí** | con $A$ y $P$: $F(x)=x$ si $P(x)$, $F(x)=a_{0}$ si no ($a_{0}\in A$ con $P$); si no hay tal $a_{0}$, el conjunto es $\emptyset$ |
| **Pares** $\{a,b\}$ | **Sí**, con Partes $+$ Vacío $+$ Extensión | dominio $\mathcal{P}(\mathcal{P}(\emptyset))=\{\emptyset,\{\emptyset\}\}$; $F(\emptyset)=a$, $F(\{\emptyset\})=b$ |
| **Unión** $\bigcup A$ | **No** por esta vía | la propiedad «$x\in Y$» **no es funcional**: hay muchos $Y$ |
| **Vacío** | No | garantiza que hay al menos un conjunto |
| **Extensión** | No | se necesita para que «único» tenga sentido |

> **🔤 Diccionario:**
> - **funcional:** a cada $a$ le toca **exactamente un** $b$; es una fórmula con dos variables, no un conjunto de parejas.
> - **esquema:** hay un axioma por cada fórmula $P$, no uno solo.
> - **imagen:** $B=\{b:\exists a\in A,\ P(a,b)\}$; el reemplazo dice que es un conjunto.
> - **separación:** $\{x\in A:P(x)\}$; ya no hace falta pedirla como axioma.

---

### B. Norma de un buen orden: todo buen orden $\cong$ único ordinal

$$
\text{Para todo buen orden }(A,<)\ \ \exists!\,\alpha\ \text{ordinal}:\ (A,<)\cong(\alpha,\in)
$$

Ese $\alpha$ se llama **norma** (o **tipo de orden**) de $(A,<)$; se escribe $\operatorname{ot}(A,<)$ ➕.

**Ejemplos.** $(\omega,\in)$ tiene norma $\omega$. El mismo conjunto $\omega$ con el orden $1<2<3<\cdots<0$ (el $0$ al final) tiene norma $\omega+1$: **cambia el orden, cambia la norma**.

**Unicidad.** Si $\alpha,\beta$ son ordinales y $f:(\alpha,\in)\to(\beta,\in)$ es isomorfismo, entonces $f(\gamma)=\gamma$ para todo $\gamma\in\alpha$ (inducción transfinita: $f[\gamma]=\gamma$ y $f(\gamma)=\min(\beta\setminus\gamma)$; eso obliga a $\gamma\in\beta$ y $f(\gamma)=\gamma$), luego $\alpha\subseteq\beta$; simétricamente $\beta\subseteq\alpha$; por tanto $\alpha=\beta$.

**Existencia.** Sea $A\neq\emptyset$ (si $A=\emptyset$, la norma es $0$).

$$
B:=\left\{\,a\in A:\ \exists\,\gamma\ \text{ordinal},\ \left(A_{<a},<\right)\cong(\gamma,\in)\,\right\}
\qquad\left(B\neq\emptyset:\ \text{el mínimo de } A \text{ da } \emptyset\cong 0\right)
$$

El $\gamma$ de cada $a\in B$ es **único** (por la unicidad). Con la propiedad funcional

$$
P(a,\gamma):\quad
\left[a\in B\ \wedge\ \left(A_{<a},<\right)\cong(\gamma,\in)\right]
\ \vee\
\left[a\notin B\ \wedge\ \gamma=\emptyset\right]
$$

el reemplazo aplicado a $B$ da

$$
H:=\left\{\,\gamma_{a}:\ a\in B\,\right\}\ \text{es un conjunto de ordinales}
\qquad\Longrightarrow\qquad
\alpha:=\left(\bigcup H\right)+1\notin H
$$

Se comparan $(A,<)$ y $(\alpha,\in)$; de las tres alternativas:

| Alternativa | Qué se concluye |
|---|---|
| $A\cong\alpha$ | listo: la norma es $\alpha$ |
| $A\cong\alpha_{<\beta}$ | listo: la norma es $\beta$ |
| $\alpha\cong A_{<a}$ | **imposible**: daría $a\in B$ y $\alpha=\gamma_{a}\in H$ |

> **🔤 Diccionario:**
> - $A_{<a}$: segmento inicial de $A$ en $a$.
> - $\gamma_{a}$: el ordinal que corresponde al segmento $A_{<a}$.
> - **norma:** el ordinal «hecho a la medida» del buen orden; depende del **orden**, no solo del conjunto.
> - $\alpha=(\bigcup H)+1$: el ordinal que se sale de $H$ (no existe el conjunto de todos los ordinales).

**Consecuencia con Zermelo.** Todo conjunto se puede bien ordenar, luego **todo conjunto tiene una norma**. Pero el buen orden de Zermelo no se conoce: de $\mathbb{R}$ o de $\mathcal{P}(\mathbb{R})$ se sabe que **existe** un ordinal, no cuál es.

---

### C. Recursión transfinita sobre un buen orden

**Definición.** Dada una propiedad funcional $\varphi$ y un buen orden $(A,<)$, una **$\varphi$-recursión** en $A$ es

$$
F:\operatorname{dom}F=A
\qquad\wedge\qquad
\forall\,a\in A:\ \varphi\left(F\restriction A_{<a},\ F(a)\right)
$$

**Los cuatro resultados** (en este orden se prueba la existencia):

| Resultado | Enunciado | Por qué |
|---|---|---|
| **Unicidad** | a lo más hay una $\varphi$-recursión en $A$ | si $F\neq G$, se toma $a_{0}=\min\{a:F(a)\neq G(a)\}$; en $A_{<a_{0}}$ coinciden, y $\varphi$ da el mismo valor |
| **Restricción** | si $F$ es recursión en $A$ y $B$ es segmento inicial de $A$, entonces $F\restriction B$ es recursión en $B$ | $B_{<b}=A_{<b}$ para $b\in B$ |
| **Extensión** | si **todo** segmento inicial de $A$ tiene recursión, entonces $A$ tiene recursión | ver los dos casos abajo |
| **Existencia** | para todo $\varphi$ funcional y todo buen orden $A$, hay una recursión | $H=\{a:A_{<a}\ \text{tiene recursión}\}$ es inductivo y $H=A$ |

**Extensión, caso con máximo.** Si $m=\max A$ y $F$ es la recursión en $A_{<m}$, sea $z$ el único con $\varphi(F,z)$:

$$
G:=F\cup\left\{(m,z)\right\}
\qquad\Longrightarrow\qquad
G\ \text{es recursión en } A
$$

**Extensión, caso sin máximo.** Para cada $a\in A$ sea $F_{a}$ la recursión en $A_{<a}$. Por reemplazo,

$$
\mathcal{C}:=\left\{\,F_{a}:\ a\in A\,\right\}\ \text{es un conjunto}
\qquad\wedge\qquad
a<b\ \Longrightarrow\ F_{a}=F_{b}\restriction A_{<a}\ \Longrightarrow\ F_{a}\subseteq F_{b}
$$

luego $\mathcal{C}$ es una cadena de funciones compatibles, $G:=\bigcup\mathcal{C}$ es función, $\operatorname{dom}G=\bigcup_{a}A_{<a}=A$ y $G\restriction A_{<b}=F_{b}$; por tanto $G$ es recursión.

> **🔤 Diccionario:**
> - $F\restriction B$: restricción de $F$ al conjunto $B$.
> - **recursión:** función total en $A$ cuyo valor en $a$ depende **solo** de los valores anteriores (el segmento $A_{<a}$).
> - **compatibles:** dos funciones que coinciden en la intersección de sus dominios; una cadena por $\subseteq$ lo es.
> - **truco central:** $\varphi$ **actúa sobre funciones** (las restricciones), no sobre elementos sueltos.

---

### D. Recursión en $\omega$ con solo una propiedad funcional

$$
\varphi\ \text{funcional},\ a\ \text{conjunto}
\ \Longrightarrow\
\exists!\,F:\omega\to V:\quad F(0)=a\ \wedge\ \forall n\in\omega\ \varphi\left(F(n),F(n+1)\right)
$$

**Cómo se obtiene de §2.C (el truco).** Se aplica la recursión transfinita a $A=\omega$ con la propiedad funcional auxiliar

$$
\Phi(X,Y):\quad
\begin{cases}
Y=a, & X\ \text{no es función con dominio sucesor}\\[2pt]
\varphi\left(X(m),Y\right), & X\ \text{función y } \operatorname{dom}X=m+1
\end{cases}
$$

$\Phi$ es funcional. Su recursión $F$ cumple $F(0)=a$ (porque $F\restriction\emptyset=\emptyset$) y, para $n+1$, como $F\restriction(n+1)$ es función con dominio $n+1$,

$$
\varphi\left(F(n),F(n+1)\right)
\qquad\left(\text{se evalúa el máximo del dominio}\right)
$$

**Diferencia con la recursión de `261015`:** allí hacía falta un **conjunto de llegada** $A$ y una función de paso $G:\mathbb{N}\times A\to A$. Aquí **no**: basta $\varphi$, y la «función» se construye sobre las restricciones.

| Ejemplo | $\varphi(x,y)$ | $a$ | Resultado |
|---|---|---|---|
| Potencias iteradas | $y=\mathcal{P}(x)$ | $\omega$ | $\omega,\ \mathcal{P}(\omega),\ \mathcal{P}(\mathcal{P}(\omega)),\dots$ (el rango es conjunto) |
| Sucesores | $y=x\cup\{x\}$ | $\omega$ | $\omega,\ \omega+1,\ \omega+2,\dots$; su unión es $\omega+\omega$, un ordinal **límite** |

> **🔤 Diccionario:**
> - $V$: la clase de todos los conjuntos (no se escribe «$F:\omega\to V$» en la práctica; solo indica que los valores son conjuntos).
> - $\Phi$: propiedad funcional **auxiliar**; su variable es una **función** (la restricción), no un número.
> - $\operatorname{dom}X=m+1$: el dominio es un ordinal sucesor; su máximo es $m$.

---

### E. Inducción transfinita

**Forma fuerte (completa).** Si

$$
\forall\,\alpha\ \text{ordinal}:\quad \left(\forall\,\beta\in\alpha:\ P(\beta)\right)\ \Longrightarrow\ P(\alpha)
$$

entonces $P(\alpha)$ para **todo** ordinal $\alpha$.

**Prueba.** Si falla para algún $\delta$, el conjunto $H=\{\beta\in\delta:\neg P(\beta)\}$ es no vacío; sea $\gamma=\min H$. Todo $\beta\in\gamma$ cumple $P$, luego $P(\gamma)$ por la hipótesis; pero $\gamma\in H$, contradicción.

**Forma por pasos** (la «simple» de los naturales):

$$
P(0)
\qquad\wedge\qquad
\forall\,\alpha:\ \left(P(\alpha)\Rightarrow P(\alpha+1)\right)
\qquad\wedge\qquad
\forall\,\lambda\ \text{límite}:\ \left(\forall\,\beta\in\lambda:\ P(\beta)\right)\Rightarrow P(\lambda)
$$

implica $P(\alpha)$ para todo $\alpha$. La tercera cláusula solo se pide en los **límites**: en un sucesor $\alpha=\gamma+1$ basta $P(\gamma)$.

**Inducción en un buen orden** (la que usa §2.C): si $H\subseteq A$ cumple

$$
\forall\,a\in A:\ \left(A_{<a}\subseteq H\ \Rightarrow\ a\in H\right)
\qquad\Longrightarrow\qquad
H=A
$$

> **🔤 Diccionario:**
> - **antecesores** de $\alpha$: los $\beta\in\alpha$; «para todo anterior» es «para todo $\beta\in\alpha$».
> - **límite:** ordinal sin máximo (§2.E de `261112`); $0$ también es límite.
> - La forma fuerte **no** pide casos base: el caso $\alpha=0$ es la implicación con antecedente vacío.

---

### F. Funcionales sobre la clase ordinal

**Problema.** No existe el conjunto de todos los ordinales: no se puede aplicar reemplazo a $\mathbf{Ord}$.

**Solución por niveles.** Para cada ordinal $\alpha$, sea $G_{\alpha}$ la única $\varphi$-recursión en $(\alpha,\in)$ (existe por §2.C). Se define

$$
\sigma(\alpha):=\ \text{el único } z\ \text{con}\ \varphi\left(G_{\alpha},z\right)
\qquad(\alpha\ \text{ordinal})
$$

**Consistencia.** Para todo ordinal $\lambda$:

$$
\sigma\restriction\lambda=G_{\lambda}
\qquad\left(\text{es la única recursión en } \lambda\right)
$$

En efecto, se prueba por inducción en $\alpha$ que $\sigma\restriction\alpha$ es una $\varphi$-recursión en $\alpha$. Para $\alpha=0$ es $\emptyset$. Si vale para todo $\beta<\alpha$: para cada $\beta<\alpha$, por unicidad $\sigma\restriction\beta=G_{\beta}$, y $\sigma(\beta)$ es el único $z$ con $\varphi(\sigma\restriction\beta,z)$; luego $\varphi\left((\sigma\restriction\alpha)\restriction\beta,\ \sigma(\beta)\right)$ se cumple. Así $\sigma\restriction\alpha$ es recursión en $\alpha$, y por unicidad $\sigma\restriction\alpha=G_{\alpha}$. En particular, para $\lambda$: $\sigma\restriction\lambda=G_{\lambda}$.

**Consecuencia.** $\sigma$ está bien definida sobre **todos** los ordinales y es única; se llama **funcional sobre la clase ordinal**. No es una función (su dominio no es un conjunto), pero **cada restricción** $\sigma\restriction\lambda$ sí es un conjunto.

> **🔤 Diccionario:**
> - $G_{\alpha}$: la recursión en el ordinal $\alpha$ (un conjunto, para cada $\alpha$).
> - $\sigma(\alpha)$: el valor «global» en $\alpha$; se calcula con la recursión local $G_{\alpha}$.
> - **por niveles:** se define para cada $\alpha$ por separado y luego se prueba que las definiciones **pegan** bien.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Las confusiones que cuestan el parcial

| Confusión | Correcto |
|---|---|
| **propiedad funcional = función** | No: no tiene dominio-conjunto. Es una fórmula $\varphi(a,b)$ con $\exists!$; su «imagen» se forma con reemplazo |
| **reemplazo crea conjuntos de la nada** | No: **siempre** parte de un conjunto $A$ ya formado |
| **la unión se saca con reemplazo** | No: «$x\in Y$» no es funcional (muchos $Y$). La unión sigue siendo axioma |
| **norma = cardinal** | No: la norma es un **ordinal** y depende del **orden**. $\omega$ y $\omega$ con $0$ al final tienen el mismo cardinal y distinta norma |
| **recursión = definir la función de golpe** | No: se construyen **restricciones** $F\restriction A_{<a}$ y se pegan |
| **en la recursión se usa $F(a-1)$** | Solo si $a$ es sucesor. En general se usa **todo** el segmento $F\restriction A_{<a}$ |
| **inducción transfinita necesita caso base** | La forma **fuerte** no: el caso $0$ es la implicación vacía. La forma **por pasos** sí pide $P(0)$ |
| **se puede usar reemplazo sobre $\mathbf{Ord}$** | No: $\mathbf{Ord}$ no es conjunto. Se define por niveles (§2.F) |

### 3.2 Reglas de bolsillo

1. **Antes de escribir «sea $f$ la función definida por recursión»,** verifica que existe: §2.C la construye por restricciones.
2. **Toda recursión se prueba primero única y después existente**; la unicidad es la que permite pegar los pedazos.
3. **El paso recursivo usa el segmento inicial completo**, no el «anterior»: así funciona también en los límites.
4. **Si el buen orden es desconocido** (Zermelo), solo se puede afirmar **existencia**; no se puede calcular.
5. **La norma de $(\alpha,\in)$ es $\alpha$**; la de $(\omega,\text{otro orden})$ puede ser $\omega+1$, $\omega+\omega$, etc.
6. **Para definir sobre $\mathbf{Ord}$: nunca reemplazo global**; se define $\sigma(\alpha)$ con la recursión local y se prueba $\sigma\restriction\lambda=G_{\lambda}$.
7. **Separación y pares ya no son axiomas** si se tiene reemplazo (con las piezas indicadas en §2.A); **unión sí** sigue siendo axioma.
8. **En la inducción por pasos**, la cláusula de límites es la que evita saltarse $\omega,\omega\cdot2,\dots$.
9. **$\omega+\omega$ existe** gracias a §2.D: es $\bigcup\{F(n)\}$, y es un ordinal límite; con eso se sigue $\omega\cdot2+1,\dots$
10. **No confundir $\bigcup H$ con el ordinal de $H$**: en §2.B se usa $\bigcup H$ solo para **salirse** de $H$.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Usar el reemplazo para formar un conjunto

1. **Identificar el conjunto de partida** $A$ (nunca «todos los conjuntos»).
2. **Escribir $\varphi(a,b)$** y probar que es funcional ($\exists!$).
3. **Aplicar reemplazo**: existe $B$ con la imagen.
4. **Describir $B$** explícitamente y usarlo.

**Plantilla ($B=C\cup A$ del taller):**

$$
\varphi(x,y):\ y=x\cup C
\ \Longrightarrow\
\{y:\exists x\in A,\ y=x\cup C\}\ \text{es conjunto}
$$

### B. Probar que un buen orden tiene norma

1. **Si $A=\emptyset$**: norma $0$.
2. **Definir** $B=\{a\in A:A_{<a}\cong\text{algún ordinal}\}$ y verificar $B\neq\emptyset$ (el mínimo).
3. **Usar unicidad** para que la asignación $a\mapsto\gamma_{a}$ sea funcional.
4. **Reemplazo** sobre $B$: $H=\{\gamma_{a}\}$ es conjunto de ordinales.
5. **Salirse de $H$**: $\alpha=(\bigcup H)+1\notin H$.
6. **Comparar** $(A,<)$ con $(\alpha,\in)$; descartar la alternativa $\alpha\cong A_{<a}$ por $\alpha\notin H$.

**Plantilla (el paso que cierra):**

$$
\alpha\cong A_{<a}
\ \Longrightarrow\
a\in B\ \wedge\ \gamma_{a}=\alpha
\ \Longrightarrow\
\alpha\in H
\ \Longrightarrow\ \text{contradicción}
$$

### C. Probar que existe una recursión en $A$

1. **Unicidad** (si hay dos, mínimo del conjunto donde difieren).
2. **Restricción** a segmentos iniciales.
3. **Extensión**:
   - con máximo: pegar la pareja $(\max A,z)$;
   - sin máximo: reemplazo sobre $\{F_{a}\}$, unión de la cadena.
4. **Existencia:** $H=\{a:A_{<a}\ \text{tiene recursión}\}$; $H\neq\emptyset$ (mínimo) e inductivo; por inducción en el buen orden, $H=A$; aplicar extensión.

**Plantilla (caso sin máximo):**

$$
G=\bigcup_{a\in A}F_{a}
\qquad\wedge\qquad
G\restriction A_{<b}=F_{b}
\qquad\Longrightarrow\qquad
G\ \text{es recursión en } A
$$

### D. Definir por recursión en $\omega$ con propiedad funcional

1. **Escribir** $\varphi(x,y)$ y verificar $\exists!$.
2. **Elegir** $a$ (= valor en $0$).
3. **Definir** la propiedad auxiliar $\Phi$ sobre funciones (§2.D).
4. **Recursión transfinita en $\omega$**: existe única $F$.
5. **Verificar** $F(0)=a$ y $\varphi(F(n),F(n+1))$.
6. **Formar el rango** de $F$ (reemplazo) si se necesita el conjunto de valores.

**Plantilla ($\omega+\omega$):**

$$
F(0)=\omega,\quad F(n+1)=F(n)\cup\{F(n)\}
\ \Longrightarrow\
\omega+\omega:=\bigcup_{n\in\omega}F(n)\ \text{es ordinal límite}
$$

### E. Probar por inducción transfinita

1. **Forma fuerte:** tomar $\alpha$ arbitrario, suponer $P(\beta)$ para **todo** $\beta\in\alpha$, probar $P(\alpha)$.
2. **Forma por pasos:** probar $P(0)$; $P(\alpha)\Rightarrow P(\alpha+1)$; y para **límite** $\lambda$, $(\forall\beta\in\lambda)P(\beta)\Rightarrow P(\lambda)$.
3. **Cerrar:** «por inducción transfinita, $P(\alpha)$ para todo ordinal $\alpha$».

**Plantilla (fuerte):**

$$
\begin{aligned}
\neg P(\delta)
&\Longrightarrow H=\{\beta\in\delta:\neg P(\beta)\}\neq\emptyset
&&\left(\text{testigo}\right)\\
&\Longrightarrow \gamma:=\min H\ \text{existe}
&&\left(\delta\ \text{bien ordenado}\right)\\
&\Longrightarrow \left(\forall\beta\in\gamma\right)P(\beta)\ \wedge\ \neg P(\gamma)
&&\left(\text{minimalidad}\right)\\
&\Longrightarrow \text{contradicción con la hipótesis}
&&\left(\text{paso inductivo}\right)
\end{aligned}
$$

### F. Definir un funcional sobre la clase $\mathbf{Ord}$

1. **Para cada $\alpha$**, tomar la única recursión $G_{\alpha}$ en $(\alpha,\in)$.
2. **Definir** $\sigma(\alpha)=$ el único $z$ con $\varphi(G_{\alpha},z)$.
3. **Probar consistencia** por inducción: $\sigma\restriction\lambda=G_{\lambda}$.
4. **Usar** $\sigma$ como si fuera una función, sabiendo que **cada restricción** es un conjunto.

**Plantilla:**

$$
\sigma(0)=z_{0},\qquad
\sigma(\alpha)=z\ \text{donde}\ \varphi\left(\sigma\restriction\alpha,z\right)
\qquad\left(\text{misma forma que la recursión}\right)
$$

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Verifiqué que $\varphi$ es **funcional** ($\exists!$) antes de aplicar reemplazo?
- [ ] ¿Dejé claro **cuál es el conjunto de partida** $A$?
- [ ] ¿En la norma usé **unicidad** para que $\gamma_{a}$ esté bien definido?
- [ ] ¿Descarté la alternativa $\alpha\cong A_{<a}$ con $\alpha\notin H$?
- [ ] ¿En la recursión usé **segmentos iniciales** y no «el anterior»?
- [ ] ¿Probé **unicidad** antes de pegar restricciones?
- [ ] ¿En el caso sin máximo usé **reemplazo** para formar $\{F_{a}\}$?
- [ ] ¿En inducción transfinita distinguí forma **fuerte** de forma **por pasos**?
- [ ] ¿Evité aplicar reemplazo a la clase $\mathbf{Ord}$?
- [ ] ¿Toda la matemática va en $...$ y en bloque con doble dólar, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Estado |
|---|---|
| **Aritmética ordinal** (suma, producto, exponenciación) | Se definirá con el funcional sobre $\mathbf{Ord}$; **próxima clase** |
| **Demostración completa de la recursión en $\omega$** | Se esbozó (reducida a la transfinita); queda como ejercicio de reescritura |
| **Ejercicio: separación y pares como teoremas** | Asignado: probar que con reemplazo dejan de ser axiomas |
| **Taller** | El profe preguntó por el taller al final; sigue pendiente de entrega |
| **Norma de $\mathbb{R}$** | Existe por Zermelo, pero **no se conoce**; solo se sabe que existe |
