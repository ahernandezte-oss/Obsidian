# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 26/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261126_SUMA_ORDINAL.md`
> - **Fecha de transcripción:** 26/11/2026 (`AAMMDD` = `261126`)
> - **Tema principal:** ARITMÉTICA ORDINAL I — **suma ordinal**: definición por recursión, propiedad funcional que la soporta, cálculo y propiedades (ordinal, neutro izquierdo, representación, asociatividad, no conmutatividad).
> - **Continuidad:** retoma la **recursión transfinita** y el **funcional sobre $\mathbf{Ord}$** de 📘 `261117_REEMPLAZO_Y_RECURSION_TRANSFINITA` §2.C–§2.F, y los **ordinales/límites** de 📘 `261112_NUMEROS_ORDINALES` §2.E. **No repite** esas pruebas: las usa y las cita.
> - **Fuente:** transcripción de clase. Lo agregado o completado por mí va con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261126_SUMA_ORDINAL` §2.C (definición de $\alpha+\beta$)».

**📎 Prerrequisitos que se dan por sabidos:**
- Ordinal, sucesor $\alpha+1=\alpha\cup\{\alpha\}$, límite, unión de un conjunto de ordinales 📘 `261112` §2.C–§2.F.
- Recursión transfinita en un buen orden y funcional sobre la clase ordinal 📘 `261117` §2.C–§2.F.
- Reemplazo en forma de imagen 📘 `261117` §2.A.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Es cálculo, definición o propiedad?** Calcular $\alpha+\beta$ → §2.C + §4.A. Definir una operación → §2.A + §4.D. Probar una propiedad → inducción (§2.F) + §4.B.
2. **Paso 1 — ¿Dónde está el ordinal «difícil»?** La recursión se hace **sobre el segundo** argumento ($\beta$); $\alpha$ queda **fijo** como parámetro. Si el ordinal raro está a la izquierda, primero calcula por la derecha y usa propiedades.
3. **Paso 2 — ¿El segundo argumento es $0$, sucesor o límite?** Son las tres cláusulas de la definición (§2.C). En límite se calcula una **unión**, no un sucesor.
4. **Paso 3 — ¿Piden una propiedad para todo $\beta$?** Inducción transfinita sobre $\beta$. La definición viene en tres partes, así que la **simple** es la opción natural (§2.F).
5. **Paso 4 — ¿Piden asociatividad o una identidad con un límite?** Antes del álgebra va la **representación** $\alpha+\beta=\alpha\cup\{\alpha+\gamma:\gamma<\beta\}$ y el **lema de continuidad** (§2.E).

**Tabla de decisión:**

| Si el enunciado pide… | Objeto | Herramienta | 👉 Ir a |
|---|---|---|---|
| «calcule $1+\omega$», «$\omega+\omega$» | suma en un límite | $\alpha+\lambda=\bigcup_{\delta<\lambda}(\alpha+\delta)$ | **§2.C** · §4.A |
| «pruebe que $\alpha+\beta$ es un ordinal» | buena definición | inducción simple sobre $\beta$ | **§2.E.1** · §4.B |
| «pruebe $0+\alpha=\alpha$» | neutro izquierdo | inducción (sucesor y límite) | **§2.E.3** · §4.B |
| «pruebe que $\alpha+\beta=\alpha\cup\{\alpha+\gamma:\gamma<\beta\}$» | representación | inducción sobre $\beta$ | **§2.E.4** · §4.E |
| «¿es asociativa?» | asociatividad | representación $+$ lema de límites | **§2.E.6** · §4.E |
| «¿es conmutativa?» | contraejemplo | $1+\omega=\omega\neq\omega+1$ | **§2.E.7** · §3.1 |
| «encuentre la propiedad funcional que soporta esta recursión» | borrador | restringir y tabular imágenes | **§2.B** · §4.C |
| «defina una operación sobre todos los ordinales» | funcional sobre $\mathbf{Ord}$ | fijar parámetro $+$ recursión global | **§2.A** · §4.D |

**Frases literales del profe → método:**

- «**Fijo el $\alpha$** y hago recursión sobre $\beta$.» → el parámetro se congela; la recursión va en el segundo argumento (§2.C).
- «El teorema dice: **dado $\varphi$, $F$ es única**. No dice que dada $F$, $\varphi$ sea única.» → dos propiedades funcionales distintas pueden dar la misma recursión en un ordinal y diferir en otro (§2.B, trampa 3).
- «$1+\omega=\omega$, pero $\omega+1=\omega$ sucesor: **no es conmutativa**.» → el orden de los sumandos cambia el resultado (§2.E.7).
- «Al sumar, $\alpha$ queda **contenido**: nunca se pierde.» → $\alpha\subseteq\alpha+\beta$ (§2.E.4).
- «La recursión es **conteo** y la suma es conteo; por eso en los naturales es conmutativa.»
- «Si la definición viene en **tres partes**, la inducción natural también.» → inducción simple (§2.F).

---

## 🛠️ 2. CAJA DE HERRAMIENTAS

### 0. Definiciones para desenvolver (qué probar con cada una)

> La columna 3 quita las abreviaturas; la 4 es la lista de chequeo cuando el parcial dice «pruebe que…» o «use que…».

| Término | Definición (📘) | Se desenvuelve como | Para usarla hay que probar |
|---|---|---|---|
| **Suma ordinal** $\alpha+\beta$ | §2.C | tres cláusulas: $\beta=0$, $\beta=\gamma+1$, $\beta=\lambda$ límite | que $\beta$ caiga en **una sola** cláusula; en límite, calcular la unión |
| **Recursión transfinita en $\alpha$** | `261117` §2.C | $\operatorname{dom}F=\alpha$ y $(\forall\delta<\alpha)\,\varphi(F\restriction\delta,F(\delta))$ | (i) $F$ función con dominio $\alpha$; (ii) la condición en cada $\delta$ |
| **Funcional sobre $\mathbf{Ord}$** | `261117` §2.F | $\Sigma(\alpha)$ definido por niveles; único **sobre los ordinales** | que cada restricción $\Sigma\restriction\lambda$ sea la recursión local |
| **Ordinal límite** | `261112` §2.E | ordinal sin máximo ($0$ también es límite) | exhibir que no es sucesor / que no hay máximo |
| **Representación de la suma** | §2.E.4 | $\alpha+\beta=\alpha\cup\{\alpha+\gamma:\gamma<\beta\}$ | inducción en $\beta$ ($0$, sucesor, límite) |

---

### A. Recursión sobre la clase ordinal (con parámetro)

$$
\text{Dada } \varphi \text{ funcional,}\quad
(\exists!\,\Sigma)\ \text{funcional sobre } \mathbf{Ord}:\quad
(\forall\alpha\ \text{ordinal})\ \varphi\left(\Sigma\restriction\alpha,\ \Sigma(\alpha)\right)
$$

«Único sobre los ordinales» significa: si $\Sigma'$ también cumple, entonces $\Sigma(\alpha)=\Sigma'(\alpha)$ para **todo** ordinal $\alpha$; fuera de los ordinales pueden diferir.

**Con parámetro.** Si se fija un ordinal $\gamma$, se aplica el teorema a una propiedad funcional $\varphi_{\gamma}$ (que menciona a $\gamma$) y se obtiene un funcional $\sigma_{\gamma}$. Así se define una operación binaria sin salir de $\mathbf{Ord}$.

> **🔤 Diccionario:**
> - $\Sigma$: propiedad funcional global; **no** es una función (su dominio sería la clase de todos los ordinales, que no es conjunto).
> - $\Sigma\restriction\alpha$: restricción a un conjunto (el ordinal $\alpha$); eso **sí** es función.
> - $\gamma$: parámetro fijo; en la suma será el sumando de la izquierda.

---

### B. El «borrador»: encontrar la propiedad funcional que soporta una recursión

**Problema típico.** «Pruebe que existe $F$ con $F(0)=\omega$ y $F(n+1)=F(n)+1$.» El teorema de recursión exige una propiedad funcional $\varphi$; hay que **fabricarla**.

**Receta.**
1. Escribe las **restricciones** que la $F$ deseada tendría: $F\restriction0=\emptyset$, $F\restriction1=\{(0,\omega)\}$, $F\restriction2=\{(0,\omega),(1,\omega+1)\}$, …
2. Tabula lo que **quieres** que reciba cada restricción: $\emptyset\mapsto\omega$, $\{(0,\omega)\}\mapsto\omega+1$, …
3. Generaliza por casos: $\emptyset$; función con dominio $n+1$ ($n\in\omega$); el resto.
4. Completa el resto con **cualquier** valor único (por ejemplo $\emptyset$), para que $\varphi$ esté definida en todo el universo.
5. Aplica el teorema; después **verifica** que la $F$ obtenida cumple las ecuaciones.

$$
\varphi(X,Y):\quad
\begin{cases}
Y=\omega, & X=\emptyset\\[2pt]
Y=X(n)+1, & X\ \text{función},\ \operatorname{dom}X=n+1,\ n\in\omega\\[2pt]
Y=\emptyset, & X\neq\emptyset\ \text{y no ocurre que } X\ \text{sea función con dominio } n+1
\end{cases}
$$

Con esta $\varphi$, la recursión sobre $\omega$ da $F(n)=\omega+n$. **Si se cambia $\varphi$, cambia la recursión**: por ejemplo, usando $X\left(\bigcup\operatorname{dom}X\right)+1$ en vez de $X(n)$, la cláusula de sucesor vale para **todo** ordinal sucesor (no solo los naturales), así que la recursión ya no se detiene en $\omega$ y produce otra $F$ sobre $\omega+\omega$.

> **🔤 Diccionario:**
> - **borrador:** cálculo previo con las restricciones; no es la prueba, es el diseño de $\varphi$.
> - $X(n)$: valor de la función $X$ en $n$; solo tiene sentido si $n\in\operatorname{dom}X$.
> - $\bigcup\operatorname{dom}X$: el máximo del dominio cuando el dominio es un ordinal sucesor.

---

### C. Definición de la suma ordinal

**Se fija $\alpha$** (parámetro) y se define por recursión sobre $\beta$:

$$
\alpha+0:=\alpha
\qquad
\alpha+(\beta+1):=(\alpha+\beta)+1
\qquad
\alpha+\lambda:=\bigcup_{\delta<\lambda}(\alpha+\delta)
\quad(\lambda\ \text{límite},\ \lambda\neq0)
$$

**La propiedad funcional que la soporta** (con $\gamma$ fijo):

$$
\varphi_{\gamma}(X,Y):\quad
\begin{cases}
Y=\gamma, & X=\emptyset\\[2pt]
Y=X\left(\bigcup\operatorname{dom}X\right)+1, & X\ \text{función},\ \operatorname{dom}X\ \text{sucesor}\\[2pt]
Y=\bigcup\operatorname{ran}X, & X\ \text{función},\ \operatorname{dom}X\ \text{límite}\neq0\\[2pt]
Y=\emptyset, & \text{en los demás casos}
\end{cases}
$$

El teorema de §2.A da un único $\sigma_{\gamma}$ sobre $\mathbf{Ord}$; se define

$$
\alpha+\beta:=\sigma_{\alpha}(\beta)
$$

**Por qué las tres cláusulas son exactamente estas:** $\sigma_{\gamma}(0)=\gamma$ es el caso base; en un sucesor, $\bigcup\operatorname{dom}X$ es el máximo (el $\beta$ anterior) y se le aplica el sucesor; en un límite no hay máximo, y lo que queda es la unión de todas las imágenes anteriores.

> **🔤 Diccionario:**
> - $\alpha+\beta$: ordinal «$\alpha$ seguido de $\beta$»; **no** es la unión de conjuntos $\alpha\cup\beta$ (§3.1).
> - $\bigcup\operatorname{ran}X$: unión de todas las imágenes ya calculadas; en un límite es el supremo.
> - $\sigma_{\alpha}$: funcional con parámetro $\alpha$; sus valores sobre ordinales **son** $\alpha+\beta$.
> - $\operatorname{ran}X$: rango (conjunto de imágenes) de $X$.

---

### D. Cálculo: ejemplos y reglas

| Cálculo | Resultado | Por qué |
|---|---|---|
| $3+5$ | $8$ | cinco sucesores desde $3$ |
| $\omega+1$ | $\omega\cup\{\omega\}$ | cláusula sucesor |
| $\omega+n$ | $n$-ésimo sucesor de $\omega$ | inducción en $n$ |
| $0+\omega$ | $\omega$ | $0+\lambda=\bigcup_{\delta<\lambda}\delta=\lambda$ |
| $1+\omega$ | $\omega$ | $\bigcup_{n<\omega}(1+n)=\omega$ |
| $2+\omega$ | $\omega$ | ídem |
| $\omega+\omega$ | $\omega\cdot2$ (el «gorrito») | $\bigcup_{n<\omega}(\omega+n)$ |
| $(\omega+\omega)+1$ | $\omega\cdot2+1$ | cláusula sucesor |

**Regla de cálculo.** Si el segundo sumando es **límite**, el resultado es el **supremo** $\bigcup_{\delta<\lambda}(\alpha+\delta)$, no un sucesor. Si $\alpha$ es finito, $\alpha+\lambda=\lambda$ para todo límite $\lambda$ (el primero queda absorbido: $1+\omega=\omega$); si $\alpha$ ya es infinito, el supremo es mayor ($\omega+\omega=\omega\cdot2$).

> **🔤 Diccionario:** $n<\omega$ = natural; $\omega\cdot2$: nombre provisional de $\omega+\omega$ (la multiplicación se define después).

---

### E. Propiedades de la suma

**E.1 — $\alpha+\beta$ es un ordinal.** Inducción simple sobre $\beta$:

$$
\begin{aligned}
\beta=0 &: \alpha+0=\alpha\ \text{es ordinal} &&(\text{hipótesis})\\
\beta=\gamma+1 &: \alpha+(\gamma+1)=(\alpha+\gamma)+1\ \text{es sucesor de un ordinal} &&(\text{HI }+\ \text{sucesor de ordinal es ordinal})\\
\beta=\lambda\ \text{límite} &: \alpha+\lambda=\bigcup_{\delta<\lambda}(\alpha+\delta)\ \text{es unión de un conjunto de ordinales} &&(\text{reemplazo }+\ \text{§2.F de } 261112)
\end{aligned}
$$

**E.2 — En los naturales coincide con la suma usual.** Si $n,m\in\omega$, la suma ordinal $n+m$ es el mismo natural que la suma de `261020`; se prueba por inducción en $m$ (solo hay caso sucesor, porque un natural no es límite).

**E.3 — Neutro por la izquierda: $0+\alpha=\alpha$.**

$$
0+0=0;\qquad
0+(\beta+1)=(0+\beta)+1=\beta+1;\qquad
0+\lambda=\bigcup_{\delta<\lambda}(0+\delta)=\bigcup_{\delta<\lambda}\delta=\lambda
$$

La última igualdad usa que $\lambda$ es límite: todo $\delta<\lambda$ cumple $\delta+1<\lambda$, luego $\lambda\subseteq\bigcup\lambda$; la otra contenencia es transitividad.

**E.4 — Representación: $\alpha+\beta=\alpha\cup\{\alpha+\gamma:\gamma<\beta\}$.** Inducción en $\beta$:

$$
\begin{aligned}
\beta=0 &: \alpha\cup\emptyset=\alpha &&\\
\beta=\gamma+1 &: (\alpha+\gamma)\cup\{\alpha+\gamma\}=\alpha\cup\{\alpha+\delta:\delta<\gamma+1\} &&(\text{hipótesis inductiva})\\
\beta=\lambda\ \text{límite} &: \bigcup_{\delta<\lambda}\left(\alpha\cup\{\alpha+\gamma:\gamma<\delta\}\right)=\alpha\cup\{\alpha+\gamma:\gamma<\lambda\} &&(\lambda\ \text{límite})
\end{aligned}
$$

Consecuencias directas: $\alpha\subseteq\alpha+\beta$; y si $\beta>0$, entonces $\alpha<\alpha+\beta$ (porque $\alpha=\alpha+0$ está en el conjunto de la derecha).

**E.5 — Continuidad en el segundo argumento (lema).** Si $\lambda$ es límite:

$$
\alpha+(\beta+\lambda)=\bigcup_{\gamma<\lambda}\left(\alpha+(\beta+\gamma)\right)
$$

Prueba: $\beta+\lambda=\bigcup_{\gamma<\lambda}(\beta+\gamma)$ es límite; usando E.4 dos veces,

$$
\alpha+(\beta+\lambda)=\alpha\cup\left\{\alpha+\xi:\xi<\beta+\lambda\right\}
=\bigcup_{\gamma<\lambda}\left(\alpha\cup\{\alpha+\xi:\xi<\beta+\gamma\}\right)
=\bigcup_{\gamma<\lambda}\left(\alpha+(\beta+\gamma)\right)
$$

**E.6 — Asociatividad: $(\alpha+\beta)+\gamma=\alpha+(\beta+\gamma)$.** Inducción en $\gamma$:

$$
\begin{aligned}
\gamma=0 &: (\alpha+\beta)+0=\alpha+\beta=\alpha+(\beta+0) &&\\
\gamma=\delta+1 &: ((\alpha+\beta)+\delta)+1=(\alpha+(\beta+\delta))+1=\alpha+((\beta+\delta)+1) &&(\text{HI})\\
\gamma=\lambda\ \text{límite} &: \bigcup_{\delta<\lambda}((\alpha+\beta)+\delta)=\bigcup_{\delta<\lambda}(\alpha+(\beta+\delta))=\alpha+(\beta+\lambda) &&(\text{HI}+E.5)
\end{aligned}
$$

**E.7 — No conmutatividad.**

$$
1+\omega=\bigcup_{n<\omega}(1+n)=\omega
\qquad\text{mientras que}\qquad
\omega+1=\omega\cup\{\omega\}\neq\omega
$$

Por tanto $1+\omega\neq\omega+1$.

> **🔤 Diccionario:**
> - **límite:** ordinal sin máximo; en la unión se recorren **todos** los anteriores.
> - **representación:** $\alpha+\beta$ es $\alpha$ junto con las copias $\alpha+\gamma$ para $\gamma<\beta$; por eso «sumar por la derecha pega copias de $\alpha$ al final».
> - **continuidad:** en un límite, la suma conmuta con el supremo por la derecha.

---

### F. Inducción: simple o completa

| | Inducción **simple** (por pasos) | Inducción **completa** (fuerte) |
|---|---|---|
| Hipótesis | $P(0)$; $P(\gamma)\Rightarrow P(\gamma+1)$; $(\forall\delta<\lambda)P(\delta)\Rightarrow P(\lambda)$ | $(\forall\beta<\alpha)P(\beta)\Rightarrow P(\alpha)$ |
| Cuándo usarla | la definición viene en **tres cláusulas** (como la suma) | la definición no separa casos, o el paso necesita **varios** anteriores |
| Costo | hay que probar $P(0)$ aparte | el caso $0$ sale de la implicación vacía |

> **🔤 Diccionario:** $(\forall\delta<\lambda)$ = «para todo ordinal anterior a $\lambda$». En un sucesor, la simple solo usa el **inmediato anterior**; en un límite usa **todos**.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Las confusiones que cuestan el parcial

| Confusión | Correcto |
|---|---|
| «La suma ordinal es conmutativa» | **No**: $1+\omega=\omega\neq\omega+1$. En los naturales sí coincide, pero eso no se extiende |
| «$\alpha+\beta=\alpha\cup\beta$» | **No**: $\alpha+\beta=\alpha\cup\{\alpha+\gamma:\gamma<\beta\}$; es un ordinal, no la unión de conjuntos |
| «$\alpha+\lambda$ es un sucesor» | En un límite **no hay anterior**: es el supremo $\bigcup_{\delta<\lambda}(\alpha+\delta)$ |
| «Puedo cancelar a la derecha» | **No**: $1+\omega=2+\omega=\omega$. La cancelación válida es por la **izquierda** ($\alpha+\beta=\alpha+\gamma\Rightarrow\beta=\gamma$), y se prueba después |
| «Dado $F$, la $\varphi$ es única» | El teorema da: **dado $\varphi$**, $F$ es única. Distintas $\varphi$ pueden coincidir en un ordinal y diferir en otro |
| «$0$ no es límite» | $0$ **sí** es límite (no es sucesor); pero en la definición de suma se usa la primera cláusula |
| «La inducción simple no sirve para límites» | Sí sirve: la tercera cláusula es exactamente el caso límite |

### 3.2 Reglas de bolsillo

1. **Fija el parámetro** y haz recursión en el **segundo** argumento; si el ordinal raro está a la izquierda, calcula por la derecha y usa propiedades.
2. **Tres cláusulas ⇒ inducción simple**; si el paso necesita varios anteriores, usa la completa.
3. **En un límite, une**: $\alpha+\lambda=\bigcup_{\delta<\lambda}(\alpha+\delta)$; nunca pongas un sucesor.
4. **La representación E.4 es la navaja suiza**: sirve para contenencia, para monotonía y para asociatividad.
5. **Sumar algo positivo agranda**: $\beta>0\Rightarrow\alpha<\alpha+\beta$.
6. **No canceles por la derecha**; el contraejemplo es $1+\omega=2+\omega$.
7. **Naturales:** la suma ordinal coincide con la usual; úsalo para calcular $1+n$ dentro de un límite.
8. **Unión no acotada de naturales:** $\bigcup_{n<\omega}(k+n)=\omega$ para cualquier $k$ natural; por eso $k+\omega=\omega$.
9. **El funcional $\sigma_{\alpha}$ no es función**: es una propiedad funcional sobre $\mathbf{Ord}$; solo sus restricciones son conjuntos.
10. **Antes de escribir la prueba**, haz el **borrador** de la propiedad funcional (§2.B); sin él, la existencia no está justificada.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Calcular $\alpha+\beta$

1. **Mira $\beta$**: ¿$0$, sucesor o límite?
2. **$\beta=0$**: resultado $\alpha$.
3. **$\beta=\gamma+1$**: calcula $\alpha+\gamma$ y aplica sucesor.
4. **$\beta$ límite**: calcula el patrón $\alpha+\delta$ para $\delta<\beta$ y toma la **unión**. Da $\beta$ si $\alpha$ es finito ($1+\omega=\omega$); si $\alpha$ ya es infinito, da un supremo mayor ($\omega+\omega$).

**Plantilla ($1+\omega$):**

$$
1+\omega=\bigcup_{n<\omega}(1+n)=\bigcup_{n<\omega}(n+1)=\omega
\qquad(\text{unión no acotada de naturales})
$$

### B. Probar una propiedad $P(\beta)$ de $\alpha+\beta$

1. **Fija $\alpha$** (parámetro) y enuncia $P(\beta)$.
2. **Inducción simple:** $P(0)$; $P(\gamma)\Rightarrow P(\gamma+1)$; $(\forall\delta<\lambda)P(\delta)\Rightarrow P(\lambda)$.
3. **En el límite**, forma el conjunto $\{\alpha+\delta:\delta<\lambda\}$ por **reemplazo** y usa que la unión de ordinales es ordinal.
4. **Cierra** con «por inducción transfinita, $P(\beta)$ para todo ordinal $\beta$».

**Plantilla ($0+\alpha=\alpha$):** $0+0=0$; $0+(\beta+1)=(0+\beta)+1=\beta+1$; $0+\lambda=\bigcup_{\delta<\lambda}\delta=\lambda$.

### C. Encontrar la propiedad funcional que soporta una recursión

1. **Escribe las restricciones** $F\restriction0,F\restriction1,F\restriction2,\dots$
2. **Tabula** qué imagen quieres para cada restricción.
3. **Generaliza por casos** ($\emptyset$ / dominio sucesor / dominio límite / resto).
4. **Completa** el resto con un valor único.
5. **Aplica** el teorema y verifica las ecuaciones.

**Plantilla:** §2.B (la $\varphi$ de $F(0)=\omega$, $F(n+1)=F(n)+1$).

### D. Definir una operación binaria sobre $\mathbf{Ord}$

1. **Fija el parámetro** $\gamma$.
2. **Escribe** la propiedad funcional $\varphi_{\gamma}$ con las tres cláusulas.
3. **Aplica** el teorema de §2.A: existe $\sigma_{\gamma}$, única sobre ordinales.
4. **Define** $\gamma+\beta:=\sigma_{\gamma}(\beta)$.
5. **Prueba** que el resultado es ordinal (E.1).

**Plantilla:** §2.C.

### E. Probar asociatividad (o una identidad con límites)

1. **Prueba la representación** E.4 por inducción.
2. **Prueba el lema de continuidad** E.5 usando E.4 dos veces.
3. **Induce en $\gamma$**: base, sucesor y límite; en el límite aplica E.5.
4. **Cierra** la igualdad de ordinales.

**Plantilla:** §2.E.6.

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Fijé $\alpha$ y dejé la recursión en $\beta$?
- [ ] ¿Clasifiqué $\beta$ en $0$, sucesor o límite antes de calcular?
- [ ] ¿En un límite usé **unión** y no sucesor?
- [ ] ¿Justifiqué que $\{\alpha+\delta:\delta<\lambda\}$ es un conjunto (reemplazo)?
- [ ] ¿Usé la representación E.4 cuando necesitaba contenencias?
- [ ] ¿En asociatividad usé el lema E.5 en el caso límite?
- [ ] ¿Evité cancelar por la derecha?
- [ ] ¿Escribí las tres cláusulas de la inducción (simple) o la hipótesis fuerte (completa)?
- [ ] ¿Toda la matemática va en $...$ y en bloque con doble dólar, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Estado |
|---|---|
| **Multiplicación ordinal** | Próxima clase; se definirá por recursión igual que la suma |
| **Exponenciación ordinal** | Próxima clase |
| **Cancelación por la izquierda** | Enunciada; **no** probada |
| **Monotonía con el orden** | Enunciada («la del orden, pero al contrario»); pendiente: $\alpha<\beta\Rightarrow\gamma+\alpha<\gamma+\beta$ y $\alpha\le\beta\Rightarrow\alpha+\gamma\le\beta+\gamma$ |
| **Aritmética ordinal completa** | Falta producto, potenciación y sus leyes |
