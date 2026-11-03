# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 22/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261022_CORTADURAS_Y_REALES.md`
> - **Fecha de transcripción:** 22/10/2026 (`DDMMAA` = `221026`)
> - **Tema principal:** CORTADURAS DE DEDEKIND (versión "hacia arriba") y construcción de $\mathbb R$: definición de número real con cuatro condiciones, orden por contenencia inversa, unión = ínfimo, reales racionales e irracionales, suma, lema de aproximación, opuesto aditivo y paso al supremo.
> - **Continuidad:** toma de `261020_RECURSION_COMPLETA_Y_SISTEMAS_DE_PEANO` las construcciones de $\mathbb Z$ y $\mathbb Q$ (§2.D–§2.E) y la noción de campo ordenado con conjunto de positivos (§2.F). Aquí **no se repiten**: solo se citan. Esta clase es la continuación directa de esa.
> - **Fuente:** transcripción de clase. Lo agregado o corregido por mí va marcado con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261022_CORTADURAS_Y_REALES` §2.B».

**📎 Prerrequisitos:** $\mathbb Q$ es un campo ordenado denso y arquimediano (`201026` §2.E–§2.F); $\mathbb Z$ no es acotado en $\mathbb Q$; en un campo ordenado hay copias de $\mathbb N$, de $\mathbb Z$ y de $\mathbb Q$.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿El objeto es un subconjunto de $\mathbb Q$?** Entonces, si es un número real, es una **cortadura**; si es un elemento de $\mathbb Q$, es un racional. **Nunca mezcles los dos órdenes** (§3.2).
2. **Paso 1 — ¿Piden "demuestre que $A$ es un número real"?** → verificar las **cuatro condiciones** (§2.B, algoritmo §4.A).
3. **Paso 2 — ¿Piden "no tiene mínimo"?** → dos vías: dar un elemento menor que cualquier $x$ (punto medio, o $x-\varepsilon$) o contradecir suponiendo mínimo (§4.B).
4. **Paso 3 — ¿Piden "todo elemento del complemento es cota inferior"?** → tomar $y\notin A$ y $x\in A$ arbitrarios y comparar (§4.C).
5. **Paso 4 — ¿Un conjunto de números reales, ínfimo o supremo?** → $\inf M=\bigcup M$ (§2.D, §4.D); para supremo, opuestos (§4.J).
6. **Paso 5 — ¿"Racional" o "irracional"?** → mirar el **máximo del complemento** (§2.E, §4.E).
7. **Paso 6 — ¿Suma, neutro, opuesto, orden?** → §2.F, §2.G, §2.H, §2.I.
8. **Paso 7 — ¿Aparece "campo ordenado" y se afirma que algo es exclusivo de $\mathbb R$?** → ⚠️ **no**: densidad y arquimediano valen en todo campo ordenado (§3.1).
9. **Paso 8 — ¿Piden la multiplicación?** → todavía **no** está definida en esta clase: es lo que falta (§3.6, §6).

**Tabla de decisión:**

| Si el enunciado dice… | Herramienta | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "sea $A$ un número real", "verifique que es cortadura" | **4 condiciones** | $A\neq\emptyset$, $A^{\complement}\neq\emptyset$, sin mínimo, $A^{\complement}\subseteq$ cotas inferiores | **§2.B** · §4.A |
| "segmento final de $r$", "el $1$ real", "el $0$ real" | **Real racional** | $S_r=\{x\in\mathbb Q: x>r\}$ | **§2.B** · §2.E |
| "$\sqrt2$", "un real irracional", "un hueco" | **Real irracional** | $\{x\in\mathbb Q: x>0,\ x^{2}>2\}$ | **§2.E** · §4.E |
| "$A\subseteq B$", "el mayor está contenido en el menor" | **Orden por contenencia inversa** | $A\le B\iff B\subseteq A$ | **§2.C** · §3.2 |
| "cotas inferiores de $A$" | **Igualdad con el complemento** | $\{$cotas inferiores de $A\}=A^{\complement}$ | **§2.B** · §4.C |
| "$\bigcup M$", "ínfimo de $M$", "conjunto acotado inferiormente" | **Unión = ínfimo** | $\inf M=\bigcup M$ | **§2.D** · §4.D |
| "supremo de $M$" | **Opuestos** | $\sup M=-\inf(-M)$ | **§2.J** · §4.J |
| "$A+B$", "la suma de dos reales" | **Suma de subconjuntos** | $A+B=\{a+b: a\in A,\ b\in B\}$ | **§2.F** · §4.F |
| "$A+0$", "neutro", "doble contenencia" | **Neutro** | $A+0_{\mathbb R}=A$ | **§2.F** · §4.G |
| "$a-b<T$", "acercar un elemento a su complemento", "distancia cero" | **Lema de aproximación** | $\exists a\in A,\ b\in A^{\complement}:\ a-b<T$ | **§2.G** · §4.H |
| "$-A$", "opuesto aditivo", "grupo abeliano" | **Opuesto por casos** | racional: $S_{-r}$ · irracional: $\{-x: x\in A^{\complement}\}$ | **§2.H** · §4.I |
| "$A\le B$", "$B-A$ positivo", "monotonía en $\mathbb R$" | **Orden por positivos** | $A\le B\iff B-A\in\mathbb R^{+}$ | **§2.I** |
| "denso", "arquimediano", "mediana" | **Todo campo ordenado** | copia de $\mathbb Q$ $\Rightarrow$ denso y arquimediano | **§3.1** |

**Frases literales del profe → método:**

- «En vez de trabajar con dos conjuntos, va a trabajar con uno solo.» → la cortadura es **hacia arriba**: se guarda $A$ y el complemento se reconstruye (§2.B).
- «¿Para qué le pongo la condición de que no tenga mínimo? Para no tener que hacer una clase de equivalencia.» → (C3) elimina la duplicación $\{x<r\}$ / $\{x\le r\}$ (§3.3).
- «El mayor queda contenido en el menor.» → chip invertido del orden (§2.C, §3.2).
- «Si $A$ está contenido en $B$, ¿quién es mayor? $A$.» → la misma regla, dicha con nombres: $A\subseteq B\Rightarrow A\ge B$ (§3.2).
- «Uno primero prueba esta desigualdad y después prueba la densidad… porque es al revés.» → el punto medio **no** se justifica citando densidad (§4.B).
- «Usted coge uno aquí y uno allá, y la distancia entre él y su complemento es cero.» → contenido del lema de aproximación (§2.G).
- «De aquí para allá se pueden meter cosas en el medio; de aquí para allá no.» → al trabajar hacia atrás en las desigualdades del $\varepsilon$ (§4.B).

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Notación: complemento y segmentos

$$
A^{\complement}:=\mathbb Q\setminus A\qquad\text{(solo en este capítulo)}
$$

$$
S_r:=\{x\in\mathbb Q:\ x>r\}\qquad (r\in\mathbb Q)
$$

**🔤 Diccionario:**
- $A^{\complement}$: **no** es el complemento absoluto: es el complemento **con respecto a $\mathbb Q$**. No existe el "conjunto de todos los conjuntos", así que el complemento necesita universo, y aquí el universo es $\mathbb Q$.
- $S_r$: segmento final (abierto) de $r$ en $\mathbb Q$; es el conjunto de los racionales **estrictamente mayores** que $r$.
- Todos los reales de este capítulo son subconjuntos de $\mathbb Q$; por eso "pertenece a $A$" y "está a la derecha de $A$" son la misma información vista de dos maneras.

### B. Número real: las cuatro condiciones

$A$ es un **número real** si $A\subseteq\mathbb Q$ y:

$$
\text{(C1)}\quad A\neq\emptyset
$$

$$
\text{(C2)}\quad A^{\complement}\neq\emptyset
$$

$$
\text{(C3)}\quad A\ \text{no tiene mínimo}
$$

$$
\text{(C4)}\quad A^{\complement}\subseteq\{\text{cotas inferiores de }A\}
$$

y el conjunto de los reales es $\mathbb R=\{A\subseteq\mathbb Q: A\ \text{cumple (C1)–(C4)}\}$.

**Consecuencia central (la que se usa en todas las pruebas):**

$$
\{\text{cotas inferiores de }A\}=A^{\complement}
$$

**🔤 Diccionario:**
- (C1): hay al menos un racional **dentro** de $A$; sin esto no habría número.
- (C2): hay al menos un racional **fuera** de $A$; sin esto $A$ sería todo $\mathbb Q$ (no habría "corte").
- (C3): sin mínimo, $A$ es "abierto por la izquierda"; es lo que evita tener dos cortaduras para el mismo punto.
- (C4): todo lo que quedó fuera está **por debajo** de todo lo que quedó dentro; esto convierte a $A$ en una separación de $\mathbb Q$ en dos mitades.
- Cota inferior de $A$: un racional $y$ con $y<x$ para todo $x\in A$.
- El paso de (C4) a la **igualdad** usa (C3): si una cota inferior estuviera en $A$, sería el mínimo de $A$.

### C. Orden en $\mathbb R$: contenencia inversa

$$
A\le_{\mathbb R}B\iff B\subseteq A
$$

$$
A<_{\mathbb R}B\iff B\subsetneq A
$$

**🔤 Diccionario:**
- $B\subseteq A$: **el mayor contiene al menor**; el que "está más a la derecha" tiene menos racionales.
- $A\le B$ no se escribe con $\le$ de $\mathbb Q$: en este capítulo $\le$ de $\mathbb Q$ se reserva para los elementos, y para los reales se usa $\subseteq$ (o $\le_{\mathbb R}$ marcado).
- Es orden **total** en $\mathbb R$ (aunque $\subseteq$ no sea total en $\mathcal P(\mathbb Q)$): se prueba con la tricotomía de $\mathbb Q$ (§4.D).
- ➕ El orden resultante es **denso y sin extremos**: $\mathbb R$ no tiene máximo ni mínimo.

### D. Unión = ínfimo

$$
M\subseteq\mathbb R,\ M\neq\emptyset,\ M\ \text{acotado inferiormente}\ \Longrightarrow\ \bigcup M\ \text{es número real}
$$

$$
\inf M=\bigcup M
$$

**🔤 Diccionario:**
- $M$: conjunto de **números reales** (o sea, un subconjunto de $\mathcal P(\mathbb Q)$); sus elementos son cortaduras.
- $\bigcup M$: unión de conjuntos de racionales; es un subconjunto de $\mathbb Q$ y resulta ser cortadura.
- "Acotado inferiormente en $\mathbb R$": existe $B\in\mathbb R$ con $B\subseteq A$ para todo $A\in M$; por el orden invertido, $B$ es **menor** que todos.
- $\inf M$: el mayor de los minorantes; con el orden invertido se obtiene **uniendo** (el mayor es el que contiene más).
- La intersección también daría el supremo, pero es mucho más difícil probar que es cortadura: por eso el camino es ínfimo **y después** opuestos (§2.J).

### E. Reales racionales y reales irracionales

$$
A\ \text{es racional}\iff A^{\complement}\ \text{tiene máximo}
$$

y en ese caso, si $r=\max A^{\complement}$, entonces $A=S_r$:

$$
A\ \text{racional}\ \Longrightarrow\ A=\{x\in\mathbb Q: x>r\}
$$

$$
A\ \text{es irracional}\iff A^{\complement}\ \text{no tiene máximo}
$$

**🔤 Diccionario:**
- $\max A^{\complement}$: el racional que queda justo en el borde; es el "número" que la cortadura representa cuando ese número es racional.
- En un real racional, el borde está **fuera** de $A$ (por (C3): $A$ no tiene mínimo, y el borde es exactamente el mínimo que se le quitó).
- En un real irracional **no hay borde**: el complemento se acerca al hueco sin alcanzarlo.
- Todo número real **negativo** contiene un racional negativo (se prueba con la copia de $\mathbb Q$ en $\mathbb R$).

### F. Suma de reales y neutro

$$
A+B:=\{a+b\ :\ a\in A,\ b\in B\}
$$

$$
A+0_{\mathbb R}=A,\qquad 0_{\mathbb R}=\{x\in\mathbb Q:\ x>0\}
$$

$$
1_{\mathbb R}=\{x\in\mathbb Q:\ x>1\}
$$

**🔤 Diccionario:**
- $A+B$: suma de subconjuntos de $\mathbb Q$ (todas las combinaciones); no hace falta que $A$ y $B$ sean reales para **definirla**, solo para que el resultado sea real.
- $0_{\mathbb R}$: los racionales **estrictamente positivos**; es una cortadura, no el racional $0$.
- $1_{\mathbb R}$: los racionales mayores que $1$; nótese que $1\in A$ es falso: el racional $1$ **no pertenece** al real $1$.
- La suma hereda de $\mathbb Q$: conmutativa, asociativa y neutro $0_{\mathbb R}$.
- $\mathbb R^{+}=\{A\in\mathbb R: A\subsetneq 0_{\mathbb R}\}$ (los mayores que cero); $\mathbb R^{-}$ los menores; $\mathbb R=\mathbb R^{-}\cup\{0_{\mathbb R}\}\cup\mathbb R^{+}$.

### G. Lema de aproximación (la distancia es cero)

Sean $A\in\mathbb R$, $T\in\mathbb Q$ con $T>0$, $c\in A^{\complement}$ y $a_0\in A$. Entonces existen $b\in A^{\complement}$ y $a\in A$ con:

$$
a-b<T
$$

Construcción de la prueba (la que hay que saber reproducir):

$$
\frac{a_0-c}{n}<T\ \ \text{para algún } n\in\mathbb N\ (\text{arquimediano})
$$

$$
H=\Big\{k\in\mathbb N:\ c+\frac{a_0-c}{n}\,k\in A\Big\},\qquad s=\min H,\qquad s\geq 1
$$

$$
a=c+\frac{a_0-c}{n}\,s\in A,\qquad b=c+\frac{a_0-c}{n}\,(s-1)\in A^{\complement},\qquad a-b=\frac{a_0-c}{n}<T
$$

**🔤 Diccionario:**
- $c$: un racional a la **izquierda** de la cortadura (fuera de $A$); $a_0$: uno de la **derecha** (dentro de $A$).
- $\frac{a_0-c}{n}$: paso del "barrido" que va de $c$ a $a_0$ en $n$ pasos iguales.
- $H$: los pasos en los que el barrido ya entró en $A$; **no vacío** porque el último paso ($k=n$) cae en $a_0\in A$; $0\notin H$ porque $c\notin A$.
- $s$: el **primer** paso que entra; existe porque $H\subseteq\mathbb N$ tiene mínimo.
- $s\geq1$ porque $0\notin H$; de ahí que $s-1\in\mathbb N$ esté definido.
- $a-b$: la distancia entre los dos puntos hallados; el lema dice que se puede hacer **tan pequeña como se quiera**.
- Se usa para el opuesto aditivo (§2.H), no para la suma.

### H. Opuesto aditivo por casos

$$
-A:=\begin{cases} S_{-r} & \text{si } A=S_r\ \text{es racional}\\[2pt] \{-x:\ x\in A^{\complement}\} & \text{si } A\ \text{es irracional}\end{cases}
$$

$$
A+(-A)=0_{\mathbb R}
$$

**🔤 Diccionario:**
- Caso racional: se niega el **borde** $r$ y se toma el segmento final correspondiente; así $-S_r=S_{-r}$.
- Caso irracional: se niegan los elementos del **complemento**; al negarlos, quedan a la derecha del hueco y forman la cortadura.
- **Por qué no vale una sola fórmula:** con la fórmula del irracional aplicada a un racional se obtendría $\{w\in\mathbb Q: w\geq-r\}$, que **tiene mínimo** y por tanto **no es un número real** (violaría (C3)).
- $-A$ es cerrado hacia arriba: si $w\in-A$ y $w'>w$, entonces $w'\in-A$ (porque los complementos son cerrados hacia abajo).
- "$-(-A)=A$", "$-(A+B)=(-A)+(-B)$": no se prueban con cortaduras, se heredan de la estructura de grupo.

### I. El orden de $\mathbb R$ es el orden de los positivos

$$
A\le_{\mathbb R}B\iff B-A\in\mathbb R^{+}\iff B\subseteq A
$$

$$
A<_{\mathbb R}B\iff B-A\in\mathbb R^{+}\ \text{estricto}
$$

**🔤 Diccionario:**
- $B-A$: se define como $B+(-A)$ (la resta es suma del opuesto).
- $\mathbb R^{+}$: los reales **contenidos estrictamente** en $0_{\mathbb R}$, o sea los mayores que cero.
- La equivalencia dice que el orden por contenencia (el de la construcción) **coincide** con el orden por positivos (el de la definición abstracta de campo ordenado de `201026` §2.F).
- $A\le B$ y $B\subseteq A$ son **la misma afirmación**; nunca uses las dos en el mismo renglón sin decirlo.

### J. Del ínfimo al supremo

$$
M\ \text{acotado superiormente}\ \Longrightarrow\ \sup M=-\inf(-M),\qquad -M:=\{-A:\ A\in M\}
$$

**🔤 Diccionario:**
- $-M$: el conjunto de los opuestos; si $M$ está acotado **superiormente**, entonces $-M$ está acotado **inferiormente**.
- $\inf(-M)$: existe por §2.D (unión).
- $-\inf(-M)$: el supremo buscado; la negación invierte el orden y convierte ínfimo en supremo.
- Así se obtiene la propiedad del supremo **sin** volver a probar las cuatro condiciones por intersección.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Lo que NO es exclusivo de $\mathbb R$

| Propiedad | ¿Solo $\mathbb R$? | Dónde vale |
|---|---|---|
| densidad (entre dos hay otro) | ❌ | en **todo campo ordenado** (en particular $\mathbb Q$) |
| arquimediano ($\forall x\ \exists n\in\mathbb N: x<n$) | ❌ | en **todo campo ordenado** (porque $\mathbb Z$ no es acotado) |
| orden total | ❌ | en todo campo ordenado |
| propiedad del **supremo** | ✅ | solo en $\mathbb R$ (campo ordenado **completo**) |
| existencia de $\sqrt2$ | ✅ | solo en $\mathbb R$ ($\mathbb Q$ tiene huecos) |

**Cadena que se usa:** todo campo ordenado tiene copia de $\mathbb N$ $\Rightarrow$ copia de $\mathbb Z$ $\Rightarrow$ copia de $\mathbb Q$; como $\mathbb Z$ no es acotado, sale el arquimediano. **Regla:** nunca justifiques un paso con "densidad de $\mathbb R$" si todavía no tienes $\mathbb R$: usa la copia de $\mathbb Q$ o la desigualdad directa.

### 3.2 El chip invertido (tabla de traducción)

| Afirmación en $\mathbb Q$ | Traducción a $\mathbb R$ |
|---|---|
| $r<s$ | $S_r\supsetneq S_s$ (el menor **contiene** al mayor) |
| $A\subseteq B$ | $A\ge_{\mathbb R}B$ |
| $A<_{\mathbb R}B$ | $B\subsetneq A$ |
| elementos de $A$ | racionales **mayores** que el número |
| $A^{\complement}$ | racionales **menores o iguales** al número (y son las cotas inferiores) |

**Regla:** en este capítulo $\le$ y $<$ se reservan para **elementos de $\mathbb Q$**; para reales se escribe contenencia. Escribir "$A\le B$" sin aclarar es la fuente número uno de errores.

### 3.3 Para qué sirve cada condición

| Condición | Qué evita | Qué permite |
|---|---|---|
| (C1) $A\neq\emptyset$ | el "número" vacío | tener un $a_0\in A$ para el barrido (§2.G) |
| (C2) $A^{\complement}\neq\emptyset$ | que $A=\mathbb Q$ | tener un $c\notin A$; sin esto falla también la unión (§2.D) |
| (C3) sin mínimo | dos cortaduras para el mismo racional | la **igualdad** cotas inferiores $=A^{\complement}$ |
| (C4) complemento $\subseteq$ cotas inferiores | conjuntos "con agujeros" dentro | orden total y estructura de corte |

**Contraejemplo de (C2):** si se unen **todos** los reales, la unión es $\mathbb Q$ y su complemento es $\emptyset$: deja de ser cortadura. Lo que impide que pase es el **acotamiento inferior** (§2.D).

### 3.4 Trampas típicas (y por qué están mal)

| Lo que se escribe | Por qué está mal |
|---|---|
| $A^{\complement}$ como complemento absoluto | no existe el conjunto universal: el complemento es siempre respecto de $\mathbb Q$ |
| "$1_{\mathbb R}$ contiene al racional $1$" | $1_{\mathbb R}=\{x\in\mathbb Q: x>1\}$; el $1$ está fuera |
| $-A=\{-x: x\in A^{\complement}\}$ para todo $A$ | en un real racional da un conjunto con mínimo: no es cortadura (§2.H) |
| "no tiene mínimo, luego es denso" | el punto medio $\frac{x+1}{2}$ se justifica por la **desigualdad**, no por densidad (§4.B) |
| probar que $\bigcup M$ es real sin acotamiento | sin cota inferior, $\bigcup M=\mathbb Q$ y falla (C2) |
| usar la intersección para el supremo | es cierto, pero mucho más difícil: el camino es ínfimo + opuestos (§2.J) |

### 3.5 Aritmética de lo racional y lo irracional

| Suma | Resultado |
|---|---|
| real racional + real racional | real **racional** |
| real racional + real irracional | real **irracional** |
| real irracional + real irracional | **no se sabe** en general |

**Nota:** lo mismo pasa con el producto. Saber si $\pi+e$ o $\pi\cdot e$ son racionales es un problema abierto; solo se sabe que **al menos uno** de los dos es irracional.

### 3.6 Qué falta para tener un campo

| Estructura | Estado en esta clase |
|---|---|
| $(\mathbb R,+)$ grupo abeliano | ✅ probado: conmutativa, asociativa, neutro $0_{\mathbb R}$, opuesto $-A$ |
| orden total compatible con la suma | ✅ probado (§2.I) |
| multiplicación | ❌ **pendiente** (siguiente clase); ahí se define con el truco de separar signos |
| propiedad del supremo | ✅ ínfimo probado; supremo por opuestos (§2.J) |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Probar que $A\subseteq\mathbb Q$ es un número real

1. **Verificar (C1):** exhibir un racional concreto dentro de $A$.
2. **Verificar (C2):** exhibir un racional concreto **fuera** de $A$ (ojo: debe ser racional, no real).
3. **Verificar (C3):** ver §4.B.
4. **Verificar (C4):** ver §4.C.
5. **Cerrar** diciendo «por (C1)–(C4), $A$ es un número real» e indicar cuál es.

**Plantilla ($1_{\mathbb R}=\{x\in\mathbb Q: x>1\}$).** (C1) $2>1$ y $2\in\mathbb Q$, luego $2\in1_{\mathbb R}$, no es vacío. (C2) $1\le1$, luego $1\notin1_{\mathbb R}$: complemento no vacío. (C3) si $x\in1_{\mathbb R}$ entonces $\frac{x+1}{2}\in\mathbb Q$, $1<\frac{x+1}{2}<x$, luego $\frac{x+1}{2}\in1_{\mathbb R}$ y es menor que $x$: no hay mínimo. (C4) si $y\notin1_{\mathbb R}$ entonces $y\le1<x$ para todo $x\in1_{\mathbb R}$: $y$ es cota inferior. ✔️

### B. Probar que una cortadura no tiene mínimo

1. **Elegir la vía:** (i) dado $x\in A$ construir otro menor, o (ii) suponer $\min A$ y contradecir.
2. **En la vía (i):** construir el candidato (punto medio $\frac{x+m}{2}$, o $x-\varepsilon$ con $\varepsilon>0$) y probar **tres cosas**: está en $\mathbb Q$, está en $A$, y es menor que $x$.
3. **Verificar que $\varepsilon$ es racional y positivo:** todos los datos tienen que ser racionales; nunca uses un real.
4. **En la vía (ii):** si $m=\min A$, entonces $m\in A$ y $m\le x$ para todo $x\in A$; derivar una contradicción con la definición de $A$.
5. **Cerrar:** «para todo $x\in A$ existe $x'\in A$ con $x'<x$; por tanto $A$ no tiene mínimo».

**Plantilla ($\sqrt2=\{x\in\mathbb Q: x>0,\ x^{2}>2\}$).** Sea $x\in A$; entonces $x>1$ (si $0<x\le1$ entonces $x^{2}\le1<2$). Sea

$$
\varepsilon=\frac{x^{2}-2}{x^{2}-2+2x}\in\mathbb Q,\qquad 0<\varepsilon<1
$$

Entonces $x-\varepsilon>0$ y $(x-\varepsilon)^{2}=x^{2}-2x\varepsilon+\varepsilon^{2}>2+\varepsilon^{2}>2$, luego $x-\varepsilon\in A$ y $x-\varepsilon<x$. No hay mínimo. ✔️

**Nota:** el $\varepsilon$ se **descubre** trabajando hacia atrás desde $(x-\varepsilon)^{2}>2$; en la presentación solo aparece el resultado.

### C. Probar la cuarta condición (complemento $\subseteq$ cotas inferiores)

1. **Tomar** $y\notin A$ arbitrario y $x\in A$ arbitrario.
2. **Traducir** $y\notin A$ a una desigualdad usando la definición concreta de $A$.
3. **Encadenar** $y\le(\text{borde})<x$ o $y<\ldots<x$; el objetivo es $y<x$.
4. **Cerrar:** «como $x\in A$ era arbitrario, $y$ es cota inferior de $A$».

**Plantilla ($1_{\mathbb R}$):** $y\notin1_{\mathbb R}$ significa $y\le1$; si $x\in1_{\mathbb R}$ entonces $x>1$; luego $y\le1<x$. ✔️

### D. Probar que $\bigcup M$ es un número real (y es el ínfimo)

1. **(C1):** como $M\neq\emptyset$, hay $A\in M$; como $A$ es real, $A\neq\emptyset$; entonces $\bigcup M\neq\emptyset$.
2. **(C2):** como $M$ es acotado inferiormente, hay $B\in\mathbb R$ con $B\subseteq A$ para todo $A\in M$; por (C2) para $B$ existe $h\notin B$; ese $h$ no puede estar en ningún $A$ (si estuviera, $h\in A\subseteq B$), luego $h\notin\bigcup M$.
3. **(C3) por contradicción:** si $r=\min\bigcup M$, entonces $r\in T$ para algún $T\in M$; como $r\le s$ para todo $s\in\bigcup M$, en particular $r\le s$ para todo $s\in T$; luego $r=\min T$, contra (C3) de $T$.
4. **(C4):** si $y\notin\bigcup M$ e $y$ fuera mayor que algún $z\in\bigcup M$, entonces $z\in B$ para algún $B\in M$ y $y\notin B$; como $B$ es real, $y$ es cota inferior de $B$, luego $y<z$, contradicción.
5. **Concluir:** $\bigcup M\in\mathbb R$ y, por el orden invertido, $\inf M=\bigcup M$.

**Plantilla:** $M=\{1_{\mathbb R},\,2_{\mathbb R}\}$ con $2_{\mathbb R}=\{x: x>2\}$. $\bigcup M=\{x>1\}=1_{\mathbb R}$, que es el **menor** de los dos y por tanto el ínfimo. ✔️

### E. Decidir si un real es racional o irracional

1. **Escribir** el complemento explícitamente: $A^{\complement}=\{y\in\mathbb Q: y\le a,\ y^{2}\le2,\ \dots\}$.
2. **Buscar el candidato a máximo:** el "borde" del hueco.
3. **Si el borde es racional y está en el complemento:** el real es racional y $A=S_r$.
4. **Si el borde no es racional:** probar que el complemento **no** tiene máximo (misma técnica de $\varepsilon$ del §4.B, pero con signos cambiados, y descartando primero el caso negativo usando que $1\in A^{\complement}$).
5. **Concluir** el tipo y usar la propiedad correspondiente (por ejemplo, el opuesto de §2.H).

**Plantilla:** $\sqrt2^{\complement}=\{y\in\mathbb Q: y\le0\}\cup\{y: 0<y,\ y^{2}\le2\}$. Si tuviera máximo, sería positivo (porque $1$ está en el complemento); sea $y$ ese máximo con $y^{2}\le2$; se construye $y+\delta$ con $\delta$ pequeño y $(y+\delta)^{2}\le2$, que sigue en el complemento y es mayor: contradicción. No hay máximo: $\sqrt2$ es **irracional**. ✔️

### F. Probar que $A+B$ es un número real

1. **(C1):** tomar $a\in A$, $b\in B$; entonces $a+b\in A+B$.
2. **(C2):** tomar $c\notin A$, $d\notin B$; entonces $c<a$ y $d<b$ para todos $a,b$, luego $c+d<a+b$; así $c+d\notin A+B$.
3. **(C3) por contradicción:** si $r=\min(A+B)$ con $r=a+b$, entonces $a+b\le a'+b'$ para todos $a',b'$; tomando $a'=a$ queda $b\le b'$ para todo $b'\in B$, o sea $b=\min B$: contradicción.
4. **(C4):** si $w\notin A+B$ y $w$ **no** fuera cota inferior, habría $a\in A$, $b\in B$ con $w\ge a+b$; entonces $w-a\ge b$; si $w-a\in B$ se tendría $w=a+(w-a)\in A+B$ (contradicción), así que $w-a\notin B$ y por (C4) de $B$ sería $w-a<b$ (contradicción).
5. **Concluir:** $A+B\in\mathbb R$.

**Plantilla:** $1_{\mathbb R}+2_{\mathbb R}=\{x+y: x>1,\ y>2\}=\{z: z>3\}=3_{\mathbb R}$. ✔️

### G. Probar que $0_{\mathbb R}$ es neutro

1. **Doble contenencia.** Primer lado: sea $x\in A$; como $A$ no tiene mínimo, existe $y\in A$ con $y<x$; entonces $x-y>0$, o sea $x-y\in0_{\mathbb R}$; escribir $x=(x-y)+y\in0_{\mathbb R}+A$.
2. **Segundo lado:** sea $x=a+r$ con $a\in A$, $r>0$; entonces $a<x$, así que $x$ **no** es cota inferior de $A$; como las cotas inferiores son $A^{\complement}$, $x\notin A^{\complement}$, luego $x\in A$.
3. **Concluir** $A+0_{\mathbb R}=A$ y, por conmutatividad, es neutro a ambos lados.

**Plantilla:** $2_{\mathbb R}+0_{\mathbb R}=\{x+y: x>2,\ y>0\}=\{z: z>2\}=2_{\mathbb R}$. ✔️

### H. Usar el lema de aproximación (acercar al complemento)

1. **Fijar** los datos: $A\in\mathbb R$, $T>0$ racional, $c\notin A$, $a_0\in A$.
2. **Aplicar arquimediano** a $\frac{a_0-c}{T}>0$: existe $n\in\mathbb N$ con $\frac{a_0-c}{n}<T$.
3. **Definir** $H=\{k\in\mathbb N: c+\frac{a_0-c}{n}k\in A\}$ y probar $H\neq\emptyset$ ($k=n$) y $0\notin H$.
4. **Tomar** $s=\min H$ (existe: $H$ es subconjunto no vacío de $\mathbb N$); como $0\notin H$, $s\ge1$.
5. **Definir** $a=c+\frac{a_0-c}{n}s$ (está en $A$) y $b=c+\frac{a_0-c}{n}(s-1)$ (no está en $A$), y calcular $a-b=\frac{a_0-c}{n}<T$.
6. **Usar** el par $(a,b)$ en la prueba del opuesto (§4.I).

**Plantilla:** $A=1_{\mathbb R}$, $c=1$, $a_0=3$, $T=\frac12$. Se necesita $\frac{3-1}{n}<\frac12$, o sea $n>4$: tómese $n=5$, paso $\frac{2}{5}$. Entonces $H=\{k\in\mathbb N: 1+\frac25k>1\}=\{k: k\geq1\}$, así que $s=1$ (el primer paso ya entra), $a=1+\frac25=\frac75\in A$ y $b=1\notin A$; y $a-b=\frac25<\frac12$. ✔️

### I. Probar $A+(-A)=0_{\mathbb R}$

1. **Caso racional:** si $A=S_r$, entonces $-A=S_{-r}$ y por §4.F se tiene $S_r+S_{-r}=S_0=0_{\mathbb R}$.
2. **Caso irracional — primera contenencia:** si $x=v+w$ con $v\in A$ y $w\in-A$, entonces $w=-u$ con $u\in A^{\complement}$; como $u$ es cota inferior, $u<v$, luego $x=v-u>0$, o sea $x\in0_{\mathbb R}$.
3. **Segunda contenencia:** sea $x>0$ racional; aplicar el lema (§2.G) con $T=x$: existen $a\in A$, $b\in A^{\complement}$ con $a-b<x$. Entonces $a+(-b)\in A+(-A)$ y $a+(-b)<x$; como $-A$ es cerrado hacia arriba, $x\in A+(-A)$.
4. **Concluir** la igualdad y con ella que $(\mathbb R,+)$ es grupo abeliano.

**Plantilla:** con $A=2_{\mathbb R}=S_2$ (real racional, $r=2$), la fórmula del caso racional da $-A=S_{-2}=\{w\in\mathbb Q: w>-2\}$, que es un número real. Y $S_2+S_{-2}=\{x+y: x>2,\ y>-2\}=\{z: z>0\}=0_{\mathbb R}$. ✔️

### J. Pasar de ínfimo a supremo

1. **Tomar** $M\subseteq\mathbb R$ no vacío y acotado **superiormente**.
2. **Formar** $-M=\{-A: A\in M\}$; verificar que es no vacío y acotado **inferiormente** (el acotamiento superior de $M$ se convierte en minorante de $-M$).
3. **Aplicar §2.D:** $\inf(-M)=\bigcup(-M)$.
4. **Definir** $s=-\inf(-M)$ y probar que es el supremo: $s$ es cota superior de $M$ ($s\ge A$ para todo $A\in M$) y es la menor de ellas.
5. **Cerrar:** «todo $M$ no vacío y acotado superiormente tiene supremo», es decir, $\mathbb R$ es **completo**.

**Plantilla:** $M=\{1_{\mathbb R},\,2_{\mathbb R}\}$, acotado superiormente (por $1_{\mathbb R}$). Entonces $-M=\{-1_{\mathbb R},\,-2_{\mathbb R}\}$, cuyo ínfimo es $-2_{\mathbb R}$ (porque $-2_{\mathbb R}\subseteq-1_{\mathbb R}$, es decir $-2<-1$); luego $\sup M=-\inf(-M)=2_{\mathbb R}$, que es el mayor de los dos. ✔️

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Distinguí números **reales** (subconjuntos de $\mathbb Q$) de **racionales** (elementos de $\mathbb Q$) en todo el ejercicio?
- [ ] ¿Escribí $A^{\complement}$ sabiendo que es complemento **respecto de $\mathbb Q$**?
- [ ] ¿Verifiqué las cuatro condiciones, cada una por separado y con un testigo concreto?
- [ ] ¿Recordé que el orden es la **contenencia inversa** ($A\le B\iff B\subseteq A$)?
- [ ] ¿Para "no tiene mínimo" usé la desigualdad y **no** cité densidad?
- [ ] ¿En la cuarta condición tomé $y$ **fuera** de $A$ y $x$ **dentro** y comparé en el orden de $\mathbb Q$?
- [ ] ¿Usé que cotas inferiores $=A^{\complement}$ (y no solo la contenencia)?
- [ ] ¿Antes de probar $\bigcup M$ real verifiqué que $M$ es no vacío y **acotado inferiormente**?
- [ ] ¿Definí $-A$ **por casos** (racional / irracional)?
- [ ] ¿Usé el lema de aproximación solo donde se necesita (opuesto), y con $T$ **racional** positivo?
- [ ] ¿Reservé $\le$ y $<$ para elementos de $\mathbb Q$ y $\subseteq$ para reales?
- [ ] ¿Evité decir que la densidad o el arquimediano son exclusivos de $\mathbb R$?
- [ ] ¿Toda la matemática en $...$ en línea y en bloque con $$, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Dónde está |
|---|---|
| **Multiplicación** de reales (se define separando signos; el producto de subconjuntos "no sirve tal cual") | siguiente clase; §3.6 |
| $\mathbb R$ es **campo ordenado completo** | falta la multiplicación; el orden y el ínfimo ya están |
| $\mathbb N_{\mathbb R}$ (los segmentos finales de naturales) forman un **sistema de Peano** | ejercicio |
| $\mathbb N_{\mathbb R}$ **no es acotado** superiormente en $\mathbb R$ | ejercicio |
| "El único campo ordenado completo es isomorfo a $\mathbb R$" | teorema de cierre del capítulo |
| Existencia de irracionales: probar que $\sqrt2^{\complement}$ no tiene máximo | ejercicio (§4.E) |
| El complemento de $\sqrt2$ no tiene máximo, y el de un real racional sí | ejercicios |
| Propiedad del supremo completa | esquema en §2.J; se cierra con la multiplicación |
