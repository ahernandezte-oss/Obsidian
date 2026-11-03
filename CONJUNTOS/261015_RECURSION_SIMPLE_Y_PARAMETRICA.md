# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 15/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261015_RECURSION_SIMPLE_Y_PARAMETRICA.md`
> - **Fecha de transcripción:** 15/10/2026 (`AAMMDD` = `261015`)
> - **Tema principal:** RECURSIÓN — antecesor, recursión finita e infinita, teoremas de restricción ($3.29$ y $3.30$), existencia y unicidad de la recursión finita ($3.31$), teorema de la recursión simple ($3.32$), recursión paramétrica y su uso para definir suma, multiplicación, potenciación y factorial.
> - **Continuidad:** esta clase es **anterior** en el calendario a `261029_CARDINALIDAD_Y_FINITUD` y a `261103_CONTABLES_SELECCION_Y_PRODUCTO`. No repite nada de ellas, pero es la máquina que ambas usan: el cardinal finito $\lvert A\rvert$, los conteos por bloques y las sucesiones de apoyo salen de aquí.
> - **Fuente:** transcripción de clase. Lo agregado o corregido por mí va marcado con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261015_RECURSION_SIMPLE_Y_PARAMETRICA` §2.F».

**📎 Prerrequisitos:** naturales de von Neumann ($0=\emptyset$, $n^{+}=n\cup\{n\}$, antecesor $n^{-}=\bigcup n$), inducción, transitividad de los naturales ($m\in n\Rightarrow m\subseteq n$), y la idea intuitiva "el siguiente se calcula con el anterior".

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Sobre qué dominio va la función?** Es la pregunta que decide todo:
   - dominio $n\in\mathbb N$ (finito) → **recursión finita** (§2.B, unicidad §2.E).
   - dominio $\mathbb N$ → **recursión infinita / simple** (§2.F).
   - dominio $P\times\mathbb N$ (hay un parámetro fijo) → **recursión paramétrica** (§2.G).
2. **Paso 1 — ¿Piden "está bien definida" o "defina la función"?** → hay que exhibir el **soporte**: un $a\in A$ y una $G$ **que no use la función que se está definiendo** (§2.F, algoritmo §4.A).
3. **Paso 2 — ¿Aparece un parámetro ("sumar con $3$", "multiplicar por $k$", "fijo $p$")?** → no repitas la recursión $k$ veces: **paramétrica** (§2.G, algoritmo §4.B).
4. **Paso 3 — ¿Piden cortar o restringir una recursión ya construida?** → **$3.29$** si la original es infinita, **$3.30$** si la original es finita (§2.D, algoritmo §4.F).
5. **Paso 4 — ¿Piden unicidad o "demuestre que son la misma función"?** → restringir a $n$ y usar $3.31$ (§2.E, algoritmo §4.E). **No** se prueba paso a paso.
6. **Paso 5 — ¿Piden unir recursiones en una sola función?** → verificar **compatibilidad dos a dos** y usar el teorema de unión de funciones (§2.C, algoritmo §4.G).
7. **Paso 6 — ¿Aparece el antecesor, $\bigcup n$, el máximo de $n$, o $n$ como dominio que "no se toca"?** → §2.A.
8. **Paso 7 — ¿Comparan el orden de pertenencia con el orden de la suma ("$n\in m$", "$m=n+c$")?** → §2.H, algoritmo §4.H.
9. **Paso 8 — ¿Buen orden sin máximo, acotados con máximo, isomorfismo con $\mathbb N$?** → §2.G (aplicación) y algoritmo §4.I.

**Tabla de decisión:**

| Si el enunciado dice… | Herramienta | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "defina $f$ por recursión", "$f(0)=a$, $f(n^{+})=$…", "pruebe que está bien definida" | **Recursión simple** | $F(0)=a$, $F(m^{+})=G(m,F(m))$ | **§2.F** · §4.A |
| "para cada $k$ fijo", "la suma con $k$", "multiplicar por $k$" | **Recursión paramétrica** | $F(p,0)=H(p)$, $F(p,m^{+})=G(p,m,F(p,m))$ | **§2.G** · §4.B |
| "existe una única recursión con dominio $n$" | **Teorema $3.31$** | $\forall n\in\mathbb N\ \exists!\,F:n\to A$ recursión | **§2.E** · §4.D |
| "restrinja la recursión a $n$", "corte en $n$", "la cola de la recursión" | **Teoremas $3.29$ / $3.30$** | $F\restriction n$ sigue siendo recursión | **§2.D** · §4.F |
| "demuestre que dos recursiones coinciden", "es única" | **Unicidad por restricción** | $J\restriction n=H_{n}$ para todo $n$ | **§2.E** · §4.E |
| "compatibles dos a dos", "la unión de las funciones", "$\bigcup\operatorname{ran}$" | **Pegado de funciones** | $\bigcup\mathcal F$ es función si son compatibles | **§2.C** · §4.G |
| "antecesor", "$n\setminus\{n^{-}\}$", "$\bigcup n$", "el máximo de $n$" | **Antecesor** | $n^{-}=\bigcup n=\max n$ para $n\neq 0$ | **§2.A** |
| "el orden de pertenencia es el orden usual", "$m=n+c$", "$n\in m$" | **Orden $\in$ = orden de la suma** | $n\subseteq m\iff\exists c\,(m=n+c)$ | **§2.H** · §4.H |
| "buen orden sin máximo", "todo acotado superiormente tiene máximo", "isomorfismo con $\mathbb N$", "segmento final" | **Recursión sobre un buen orden** | $F(m^{+})=\min\{x\in A: x>F(m)\}$ | **§2.G** · §4.I |
| "factorial", "$0!=1$, $(n^{+})!=n^{+}\cdot n!$" | **Recursión simple** (aquí sí alcanza) | $a=1$, $G(m,z)=m^{+}\cdot z$ | **§2.F** · §4.A |
| "Fibonacci", "$f(n)$ depende de $f(n-1)$ **y** $f(n-2)$" | ❌ **No es recursión simple** | hace falta **recursión completa** | **§3.5** |

**Frases literales del profe → método:**

- «Cuando usted piensa en armar la recursión es usted dice: primero tengo a vacío.» → **el caso $n=0$ se trata aparte y su única función es $\emptyset$** (§3.2).
- «La $G$ tiene que ser una función limpiecita. No puedo usar recursión para formar recursión.» → **la $G$ del soporte no puede mencionar la función que se está definiendo** (§2.F, §3.3).
- «Usted nunca presenta eso: usted hace un borrador.» → primero el borrador del paso $n\mapsto n^{+}$, después se oculta el contador y se escribe la $G$ (§4.A, pasos 2–4).
- «Ya lo hice para uno, lo hice para otro. No. Eso es inducción.» → para el dominio $\mathbb N$ completo **no** se enumera: se prueba $\exists!$ para cada $n$ y se **une** (§2.F).
- «Si no hay máximo, ese segmento siempre es distinto de vacío.» → buena ordenación + ausencia de máximo $\Rightarrow$ el mínimo del segmento final existe (§2.G).
- «El sobreyectivo lleva apellido: una misma función puede ser sobre o no dependiendo de lo que yo le coloque.» → ser "sobre" **no** es propiedad de la función sola: depende del codominio declarado (§3.4).

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Antecesor y las cuentas con $n$ como dominio

**Definición.** Para $n\in\mathbb N$ con $n\neq 0$, sea $n^{-}$ el único $k\in\mathbb N$ tal que $k^{+}=n$.

Cálculo práctico (dos vías, dan lo mismo):

$$
n^{-}=\bigcup n=\max n\qquad (n\neq 0)
$$

**🔤 Diccionario:**
- $n$: natural de von Neumann, $n=\{0,1,\dots,n^{-}\}$, con $n$ elementos.
- $n^{+}$: sucesor, $n^{+}=n\cup\{n\}$.
- $n^{-}$: antecesor; **solo existe si $n\neq 0$**.
- $\bigcup n$: unión de todos los elementos de $n$; como $n$ es transitivo, coincide con el máximo.
- $\max n$: máximo de $n$ como conjunto ordenado por $\in$; es $n^{-}$.

**Propiedades de uso inmediato:**

$$
(n^{-})^{+}=n,\qquad n^{-}\in n,\qquad n\notin n,\qquad n^{-}\subsetneq n
$$

$$
m\in n^{-}\ \Longrightarrow\ m^{+}\in n
$$

**🔤 Diccionario:**
- La tercera, $n\notin n$, es la que **prohíbe** poner $n$ en el dominio de la recursión de tamaño $n$.
- La última, $m\in n^{-}\Rightarrow m^{+}\in n$, justifica que la condición (2) de una recursión de tamaño $n$ corra solo sobre $n^{-}$: si $m^{+}\in n$ entonces $m\in n^{-}$, y ese $m$ ya está en el dominio.

**Por qué el dominio es $n$ y no $n^{+}$ (lo que el profe dejó anotado para las pruebas):** si $\mathrm{dom}\,F=n$ y quisiéramos evaluar $F$ en $n$, sería $F(n)$, pero $n\notin n$. La última pareja que sí se puede exigir es la de índice $n^{-}$, y su valor $F(n^{-})$ es justamente el que produce $F\big((n^{-})^{+}\big)=F(n)$, que ya se sale del dominio. Por eso la condición (2) se escribe «para todo $m\in n^{-}$».

---

### B. Recursión finita e infinita (definiciones)

Sea $A\neq\emptyset$, $a\in A$ y $G:\mathbb N\times A\to A$.

**B1. Recursión finita de $(a,G)$ con dominio $n$.** Una función $F:n\to A$ tal que:

$$
\begin{aligned}
&n=0:\quad F=\emptyset\ \text{(no hay condiciones)}\\
&n\neq 0:\quad F(0)=a\quad\text{y}\quad F(m^{+})=G\big(m,F(m)\big)\ \ \text{para todo } m\in n^{-}
\end{aligned}
$$

**B2. Recursión infinita de $(a,G)$.** Una función $F:\mathbb N\to A$ tal que:

$$
F(0)=a\qquad\text{y}\qquad F(m^{+})=G\big(m,F(m)\big)\ \ \text{para todo } m\in\mathbb N
$$

**🔤 Diccionario:**
- $A$: conjunto de valores (codominio); **no vacío**, porque hay que escoger $a$.
- $a$: valor inicial, la imagen de $0$; es el "primer dato".
- $G$: función de paso, $G:\mathbb N\times A\to A$; recibe el índice $m$ y el valor anterior $F(m)$ y devuelve el siguiente.
- $F$: la función que se define; su dominio es $n$ (finito) o $\mathbb N$ (infinito).
- $n^{-}$: antecesor de $n$ (§2.A); si $n=0$, el conjunto $n^{-}$ no existe y el caso se separa.
- $m^{+}$: sucesor del índice, el "siguiente".

➕ **Forma compacta equivalente** (la del libro, sin separar el caso $0$): $F:\mathrm{dom}\,F\to A$ con $\mathrm{dom}\,F\subseteq\mathbb N$ es recursión si (i) $0\in\mathrm{dom}\,F\Rightarrow F(0)=a$ y (ii) $m^{+}\in\mathrm{dom}\,F\Rightarrow F(m^{+})=G(m,F(m))$. Con esta forma, $\emptyset$ es recursión de tamaño $0$ sin discutir nada.

---

### C. Pegado de funciones (la herramienta de todas las pruebas)

**C1. Compatibilidad dos a dos.** Una familia $\mathcal F$ de funciones es **compatible dos a dos** si para todos $F,G\in\mathcal F$:

$$
F\restriction(\mathrm{dom}\,F\cap\mathrm{dom}\,G)=G\restriction(\mathrm{dom}\,F\cap\mathrm{dom}\,G)
$$

**C2. Teorema de unión.** Si $\mathcal F$ es compatible dos a dos, entonces $\bigcup\mathcal F$ es una función, y además:

$$
\mathrm{dom}\Big(\bigcup\mathcal F\Big)=\bigcup_{F\in\mathcal F}\mathrm{dom}\,F,\qquad \operatorname{ran}\Big(\bigcup\mathcal F\Big)=\bigcup_{F\in\mathcal F}\operatorname{ran}F
$$

**C3. Criterio de contenencia de la unión.** Para todo conjunto $B$:

$$
\Big(\forall A\in\mathcal C:\ A\subseteq B\Big)\iff\bigcup\mathcal C\subseteq B
$$

**C4. La unión de los naturales no tiene máximo.**

$$
\bigcup_{n\in\mathbb N}n=\mathbb N
$$

**🔤 Diccionario:**
- $\mathcal F$: familia de funciones (en la práctica, $\{\text{las recursiones de tamaño } n\}$).
- $F\restriction X$: restricción de $F$ a $X$, es decir $F\cap (X\times\operatorname{ran}F)$.
- $\mathrm{dom}$, $\operatorname{ran}$: dominio y rango (imagen).
- "Compatible dos a dos": donde dos funciones comparten dominio, **coinciden**; por eso al unirlas no hay dos imágenes para un mismo elemento.
- $\bigcup\mathcal C$: unión de la colección $\mathcal C$.
- C4: se usa para concluir $\mathrm{dom}\,F=\mathbb N$: si ningún natural es el máximo, la unión cubre todo $\mathbb N$.

---

### D. Teoremas de restricción: $3.29$ y $3.30$

**$3.29$ (bajar de infinita a finita).** Si $F:\mathbb N\to A$ es recursión infinita de $(a,G)$, entonces para todo $n\in\mathbb N$:

$$
F\restriction n\ \text{es recursión finita de }(a,G)\text{ con dominio } n
$$

**$3.30$ (bajar de finita a finita).** Si $F:n\to A$ es recursión finita de $(a,G)$ y $m\in n$, entonces:

$$
F\restriction m\ \text{es recursión finita de }(a,G)\text{ con dominio } m
$$

**🔤 Diccionario:**
- Restringir = **recortar el dominio**, no cambiar la regla: las parejas que quedan son las mismas.
- $n\in m$ y $n\subseteq m$: en los naturales, $n\in m\iff n\subsetneq m$ (orden de pertenencia).
- El caso $n=0$ de $3.29$ es $F\restriction 0=\emptyset$, que es recursión de tamaño $0$ por definición (B1).

➕ **Por qué $3.30$ sale también de $3.31$:** $F\restriction m$ cumple (1) y (2) (verificación directa, porque $m\subseteq n$), y $3.31$ dice que la recursión de tamaño $m$ es **única**; luego $F\restriction m$ es *esa*.

---

### E. Teorema $3.31$ — existencia y unicidad de la recursión finita

$$
\forall n\in\mathbb N\ \ \exists!\,F\ \Big(F:n\to A\ \text{es recursión de }(a,G)\Big)
$$

Se prueba por **inducción sobre $n$**; el paso se construye **pegando una pareja**:

$$
H_{n^{+}}=H_{n}\cup\Big\{\big(n,\ G\big(n^{-},\,H_{n}(n^{-})\big)\big)\Big\}\qquad (n\neq 0)
$$

$$
H_{1}=\{(0,a)\}
$$

**🔤 Diccionario:**
- $H_{n}$: la única recursión de tamaño $n$ (notación del profe; es la misma $F$ de §2.B restringida a tamaño $n$).
- $H_{n^{+}}$: la de tamaño $n+1$; **contiene** a la anterior y añade **una sola** pareja.
- La pareja añadida tiene primer componente $n$ (el nuevo índice) y segundo componente el valor que exige la regla (2) evaluada en el antecesor.
- Si $n=0$ se usa $H_{1}=\{(0,a)\}$: con la regla (2) no hay nada que verificar porque $1^{-}=0$ y $0\notin 0$.

---

### F. Teorema $3.32$ — recursión simple (el teorema que se usa)

$$
\exists!\,F\ \Big(F:\mathbb N\to A\ \text{es recursión infinita de }(a,G)\Big)
$$

Construcción de la prueba (es el esqueleto que hay que saber reproducir):

$$
F=\bigcup_{n\in\mathbb N}H_{n}=\bigcup\operatorname{ran}(L),\qquad L:\mathbb N\to{}^{\mathbb N}A,\ \ L(n)=H_{n}
$$

$$
\mathrm{dom}\,F=\bigcup_{n\in\mathbb N}n=\mathbb N,\qquad \operatorname{ran}F\subseteq A
$$

**🔤 Diccionario:**
- $L$: función que a cada $n$ le asigna la recursión $H_{n}$ de tamaño $n$; está **bien definida** porque $3.31$ garantiza que esa $H_{n}$ existe y es única.
- ${}^{\mathbb N}A$: conjunto de todas las funciones $\mathbb N\to A$ (las sucesiones en $A$); ahí viven las $H_{n}$.
- $F$: la unión de todas las $H_{n}$; es la recursión infinita buscada.
- $\bigcup_{n}n=\mathbb N$: por C4 (ningún natural es máximo).

---

### G. Recursión paramétrica

Sean $A\neq\emptyset$, $P\neq\emptyset$ (conjunto de **parámetros**), $H:P\to A$ y $G:P\times\mathbb N\times A\to A$. Entonces:

$$
\exists!\,F:P\times\mathbb N\to A\ \text{tal que}\quad F(p,0)=H(p)\quad\text{y}\quad F(p,m^{+})=G\big(p,m,F(p,m)\big)
$$

➕ **Por qué existe:** para cada $p\in P$ fijo, $H(p)\in A$ y $G_{p}(m,z)=G(p,m,z)$ son un soporte válido; por $3.32$ existe una única $F_{p}:\mathbb N\to A$ que es recursión de $(H(p),G_{p})$. Se meten todas en una bolsa:

$$
F=\Big\{\big((p,m),\,F_{p}(m)\big)\ :\ p\in P,\ m\in\mathbb N\Big\}
$$

y la unicidad es inmediata: dos candidatas $F,F'$ dan, para cada $p$, dos recursiones de $(H(p),G_{p})$, que coinciden por $3.32$.

**🔤 Diccionario:**
- $P$: conjunto de parámetros; en la suma es $\mathbb N$ (el sumando de la izquierda).
- $p$: parámetro fijo dentro de la recursión; **se mantiene constante** mientras corre $m$.
- $H$: dato inicial **dependiente del parámetro**, $H(p)=F(p,0)$.
- $G$: regla de paso; ahora recibe también el parámetro, $G(p,m,z)$.
- $F$: la función de dos variables; se usa "currificada" como $m\mapsto F(p,m)$.

**Las cuatro operaciones salen de aquí:**

| Operación | $P$ | $H(p)$ | $G(p,m,z)$ | Queda |
|---|---|---|---|---|
| Suma | $\mathbb N$ | $p$ (identidad) | $z^{+}$ | $p+m$ |
| Multiplicación | $\mathbb N$ | $0$ | $z+p$ | $p\cdot m$ |
| Potenciación | $\mathbb N$ | $1$ | $z\cdot p$ | $p^{m}$ |
| Factorial (sin parámetro) | — | $a=1$ | $m^{+}\cdot z$ | $m!$ |

**🔤 Diccionario:**
- $z$: el valor anterior $F(p,m)$, es decir el "acumulador".
- En la **suma**, $G$ **ignora** $m$; en el **factorial**, $G$ **sí usa** $m$: por eso no se puede decir que $G$ dependa siempre solo del acumulador.
- La potenciación y el factorial quedaron como tarea (§6).

---

### H. El orden de pertenencia es el orden de la suma

Para todos $m,n\in\mathbb N$:

$$
n\subseteq m\iff\exists c\in\mathbb N\ \ (m=n+c)
$$

$$
n\in m\iff\exists c\in\mathbb N\ \ (m=n+c^{+})
$$

**🔤 Diccionario:**
- $n\subseteq m$: orden por $\in/\subseteq$ (von Neumann), el que trae la construcción de $\mathbb N$.
- $m=n+c$: orden por la suma, el "de toda la vida" ($n$ es menor o igual que $m$ si a $n$ se le puede sumar algo para llegar a $m$).
- La segunda línea es la versión **estricta**: $n<m$ pide que lo que se suma sea **distinto de cero**, y todo natural no nulo es de la forma $c^{+}$.
- La equivalencia dice que **no hay dos órdenes**: el de la construcción y el usual son el mismo.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Qué te da cada teorema (mapa de bolsillo)

| Objeto que tengo | Qué puedo afirmar | Teorema |
|---|---|---|
| recursión infinita $F$ | toda restricción $F\restriction n$ es recursión finita | $3.29$ |
| recursión finita $F:n\to A$ | $F\restriction m$ es recursión finita para $m\in n$ | $3.30$ |
| tamaño $n$ | existe **una y solo una** recursión de tamaño $n$ | $3.31$ |
| tamaño $n^{+}$ y su restricción a $n$ | la restricción es exactamente $H_{n}$ | $3.31$ + $3.30$ |
| soporte $(a,G)$ con $a\in A\neq\emptyset$ | existe **una y solo una** recursión en $\mathbb N$ | $3.32$ |
| soporte $(H,G)$ con parámetros | existe **una y solo una** recursión en $P\times\mathbb N$ | §2.G |
| familia de recursiones compatible dos a dos | la unión es función y su dominio es la unión de dominios | §2.C |

### 3.2 Las cuatro trampas del $0$

1. **El caso $n=0$ siempre se separa.** Ahí no hay condiciones que verificar y la única función $0\to A$ es $F=\emptyset$.
2. **$0\notin 0$.** Por eso la condición (1) no se puede pedir para $n=0$: el $0$ no está en el dominio.
3. **$0$ no tiene antecesor.** Nunca escribas $0^{-}$: no existe.
4. **La recursión de tamaño $0$ es vacía siempre**, sea cual sea $A$ y sea cual sea $G$.

### 3.3 La regla del soporte (la que más se falla)

1. La $G$ se escribe **sin usar la función que se está definiendo**. «La $G$ tiene que ser una función limpiecita.»
2. Sí puede usar: el índice $m$, el acumulador $z$, el parámetro $p$, y **cualquier operación ya definida antes** (suma para definir multiplicación, multiplicación para definir potenciación).
3. El "borrador" (la fórmula con $F$ dentro) sirve para descubrir $G$, **no** se presenta como definición: se oculta el contador y se escribe la $G$ final.
4. Si la $G$ que sale depende solo de $z$ y no de $m$ (caso suma), es correcto; **no** es un error.

### 3.4 Errores típicos (y por qué están mal)

| Lo que se escribe | Por qué está mal |
|---|---|
| $\mathrm{dom}\,F=n^{+}$ para la recursión de tamaño $n$ | $n\notin n$; el índice $n$ no pertenece al dominio que se quiere |
| $F(m^{+})=G(m,F(m))$ «para todo $m\in n$» | si $m=n$ entonces $m^{+}=n^{+}\notin n$; el cuantificador correcto es $m\in n^{-}$ |
| «$G(m,z)=F(m)^{+}$» | la $G$ no puede usar $F$: es definición circular |
| probar unicidad evaluando pareja por pareja en todo $\mathbb N$ | infinitas verificaciones; se restringe a $n$ y se usa $3.31$ |
| unir recursiones sin verificar compatibilidad | la unión podría tener dos imágenes para un mismo índice y dejaría de ser función |
| «$F$ es sobreyectiva» sin declarar codominio | ser sobre depende del codominio: la misma función puede serlo o no |

### 3.5 El límite: recursión simple **no** alcanza para todo

| Función | Depende de | Alcanza con |
|---|---|---|
| $p+m$, $p\cdot m$, $p^{m}$ | índice $m$ y valor anterior $F(m)$ | **recursión simple / paramétrica** ✔ |
| $m!$ | $m$ y el anterior | **recursión simple** ✔ |
| Fibonacci $f(n)=f(n^{-})+f(n^{- -})$ | **dos** valores anteriores | ❌ pide **recursión completa** (quedó para otra clase) |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Definir una función sobre $\mathbb N$ por recursión simple

1. **Identificar** el conjunto de valores $A$ y el valor inicial $a$ (el caso base: qué vale en $0$).
2. **Escribir el borrador:** la ecuación que se *quiere*, con $F$ a la derecha incluida.
3. **Aislar la $G$:** borrar el contador y quedarse con una regla que reciba $(m,z)$ y devuelva el siguiente valor, **sin mencionar $F$**.
4. **Declarar** explícitamente $A\neq\emptyset$, $a\in A$ y $G:\mathbb N\times A\to A$ (verificar que $G$ cae en $A$).
5. **Citar $3.32$:** existe una única $F:\mathbb N\to A$ con $F(0)=a$ y $F(m^{+})=G(m,F(m))$.
6. **Verificar** con los dos primeros valores calculados a mano ($n=0$ y $n=1$) y, si se pide una fórmula cerrada, probarla por inducción.

**Plantilla:** «sumar $3$ a la izquierda». $A=\mathbb N$, $a=3$, $G(m,z)=z^{+}$ (ignora $m$). Por $3.32$ existe única $F_{3}:\mathbb N\to\mathbb N$ con $F_{3}(0)=3$ y $F_{3}(m^{+})=F_{3}(m)^{+}$. Valores: $F_{3}(0)=3$, $F_{3}(1)=4$, $F_{3}(2)=5$. Es $F_{3}(m)=3+m$ (se confirma por inducción). ✔️

### B. Definir con parámetro (recursión paramétrica)

1. **Reconocer** que la recursión se repite para cada valor de un parámetro (el sumando de la izquierda, el factor de la izquierda).
2. **Fijar** $P$ (conjunto de parámetros), $A$ (valores) y escribir los dos datos: $H(p)$ (valor en $0$ para el parámetro $p$) y $G(p,m,z)$ (regla de paso).
3. **Aplicar §2.G:** existe una única $F:P\times\mathbb N\to A$.
4. **Presentar** el resultado en la notación habitual ($p+m$, $p\cdot m$, $p^{m}$) y verificar $p+0=p$ y $p+m^{+}=(p+m)^{+}$.
5. **Registrar** qué propiedades faltan probar (conmutatividad, asociatividad): se prueban por inducción, no aquí.

**Plantilla:** multiplicación. $H(p)=0$, $G(p,m,z)=z+p$. Resultado: $F(p,0)=0$ y $F(p,m^{+})=F(p,m)+p$, es decir $p\cdot m$. Chequeo: $p\cdot 1=F(p,1)=F(p,0)+p=0+p=p$. ✔️

### C. Verificar que una función es recursión (las dos condiciones)

1. **Identificar** el tamaño: ¿dominio $0$, dominio $n\neq 0$ o dominio $\mathbb N$?
2. **Si el dominio es $0$:** ya está, $\emptyset$ es recursión; no hay nada que probar.
3. **Si el dominio es $n\neq 0$:** probar $F(0)=a$ y después, para $m\in n^{-}$ arbitrario, $F(m^{+})=G(m,F(m))$; usar que $m\in n^{-}\Rightarrow m^{+}\in n$ para que $F(m^{+})$ esté definido.
4. **Si el dominio es $\mathbb N$:** lo mismo pero para todo $m\in\mathbb N$.
5. **Cerrar** con la frase «luego $F$ satisface (1) y (2), es decir es recursión de $(a,G)$ con dominio …».

**Plantilla:** $F=\{(0,a),(1,G(0,a))\}$ con dominio $2$. (1) $F(0)=a$ ✔. (2) $2^{-}=1$, luego $m\in\{0\}$, es decir $m=0$: $F(0^{+})=F(1)=G(0,a)=G(0,F(0))$ ✔. Es recursión de tamaño $2$. ✔️

### D. Probar existencia por inducción (construir $H_{n^{+}}$)

1. **Enunciar** la propiedad $P(n)$: «existe una única recursión de tamaño $n$».
2. **Base $n=0$:** la única función $0\to A$ es $\emptyset$ (unicidad por vacuidad de dominios iguales).
3. **Paso:** suponer $P(n)$ con recursión $H_{n}$ y separar dos casos.
4. **Caso $n=0$:** definir $H_{1}=\{(0,a)\}$; verificar (1) y la unicidad porque $0$ es el único elemento del dominio.
5. **Caso $n\neq 0$:** definir $H_{n^{+}}=H_{n}\cup\{(n,\,G(n^{-},H_{n}(n^{-})))\}$; como $n\notin\mathrm{dom}\,H_{n}$, la unión es función y $H_{n^{+}}(n)=G(n^{-},H_{n}(n^{-}))$.
6. **Verificar (1) y (2)** en $H_{n^{+}}$: (1) porque $0\in n\subseteq n^{+}$ y ahí coincide con $H_{n}$; (2) separando $m\in n^{-}$ de $m=n^{-}$ (para $m=n^{-}$ se usa la pareja añadida).
7. **Unicidad:** dada $J$ de tamaño $n^{+}$, $J\restriction n$ es recursión de tamaño $n$ ($3.30$), luego $=H_{n}$; y $J(n)$ queda forzado por (2). Luego $J=H_{n^{+}}$.

**Plantilla:** $A=\mathbb N$, $a=0$, $G(m,z)=z^{+}$, desde $H_{1}=\{(0,0)\}$: $H_{2}=\{(0,0),(1,1)\}$, $H_{3}=\{(0,0),(1,1),(2,2)\}$. Cada paso añade la pareja $(n,n)$, y la regla (2) obliga a que sea exactamente esa. ✔️

### E. Probar unicidad de una recursión infinita (por restricción)

1. **Suponer** otra $J:\mathbb N\to A$ que cumple (1) y (2).
2. **Restringir** $J$ a cada $n$: por $3.29$/$3.30$, $J\restriction n$ es recursión de tamaño $n$.
3. **Aplicar $3.31$:** hay una sola de tamaño $n$, luego $J\restriction n=H_{n}$.
4. **Concluir** $H_{n}\subseteq J$ para todo $n$, es decir $\bigcup_{n}H_{n}\subseteq J$.
5. **Cerrar** con la igualdad: $\bigcup_{n}H_{n}=F$ y ambos tienen dominio $\mathbb N$ (si $J\not\subseteq F$, una pareja $(x,y)\in J\setminus F$ tendría $x\in\mathbb N$, y como $x+1\in\mathbb N$ existiría $H_{x+1}$ con esa misma pareja, contradiciendo que $H_{x+1}\subseteq F$).

**Plantilla:** con $F_{3}(0)=3$, $F_{3}(m^{+})=F_{3}(m)^{+}$, cualquier $J$ con esas dos condiciones tiene $J\restriction n=F_{3}\restriction n$ para todo $n$; uniendo, $J=F_{3}$. ✔️

### F. Probar que una restricción es recursión ($3.29$ / $3.30$)

1. **Verificar primero** que la restricción tiene el dominio pedido: $\mathrm{dom}(F\restriction n)=n$ (porque $n\subseteq\mathrm{dom}\,F$).
2. **Caso $n=0$:** $F\restriction 0=\emptyset$, recursión de tamaño $0$ por definición.
3. **Caso $n\neq 0$:** probar $F\restriction n(0)=F(0)=a$.
4. **Probar (2):** tomar $m\in n^{-}$; entonces $m^{+}\in n$ (por §2.A), luego ambos lados se calculan dentro de $F$ y la igualdad es la de $F$.
5. **Cerrar** citando el número del teorema que se usó y el dominio obtenido.

**Plantilla:** $F:\mathbb N\to A$ recursión, $n=2$: $\mathrm{dom}(F\restriction 2)=2$; $F\restriction 2(0)=a$; para $m\in 1$, $m=0$ y $F\restriction 2(1)=F(1)=G(0,F(0))=G(0,F\restriction 2(0))$. Recursión de tamaño $2$. ✔️

### G. Unir recursiones en una sola función (prueba de $3.32$)

1. **Definir** $L(n)=H_{n}$ y decir por qué está bien definida ($3.31$: existe y es única).
2. **Tomar dos elementos** del rango: $H_{n}$ y $H_{m}$; por tricotomía de $\mathbb N$ hay tres casos.
3. **Caso $n=m$:** son la misma función.
4. **Caso $m\in n$:** $\mathrm{dom}\,H_{n}\cap\mathrm{dom}\,H_{m}=n\cap m=m$; hay que ver $H_{n}\restriction m=H_{m}$: el lado izquierdo es recursión de tamaño $m$ ($3.30$) y por $3.31$ es la única, o sea $H_{m}$.
5. **Caso $n\in m$:** análogo, intercambiando papeles.
6. **Unir:** por §2.C, $F=\bigcup_{n}H_{n}$ es función, $\mathrm{dom}\,F=\bigcup_{n}n=\mathbb N$ y $\operatorname{ran}F\subseteq A$.
7. **Verificar (1) y (2) de $F$** y cerrar con la unicidad (§4.E).

**Plantilla:** $H_{2}=\{(0,0),(1,1)\}$, $H_{3}=\{(0,0),(1,1),(2,2)\}$; $1\in 2$, y $H_{2}\restriction 1=\{(0,0)\}=H_{1}$, compatible; $H_{2}\cup H_{3}=H_{3}$. La unión de todas da la identidad en $\mathbb N$. ✔️

### H. Probar $n\subseteq m\iff\exists c\,(m=n+c)$

1. **Fijar** $n$ y hacer **inducción sobre $m$** (la variable que crece por sucesor, porque la suma está definida por recursión en su segundo argumento).
2. **Base $m=0$:** $0=n+c$ solo si $n=0$ y $c=0$ (si $c=d^{+}$ el resultado es un sucesor, nunca $0$); y $n\subseteq 0$ solo si $n=0$. Ambas equivalen a $n=0$.
3. **Paso:** suponer la equivalencia para $m$ y probarla para $m^{+}$, separando los dos casos de $n\subseteq m^{+}$, es decir $n\subseteq m$ o $n=m^{+}$.
4. **Dirección $\Rightarrow$:** si $n\subseteq m$, por hipótesis $m=n+c$ y entonces $m^{+}=n+c^{+}$; si $n=m^{+}$, entonces $m^{+}=n+0$.
5. **Dirección $\Leftarrow$:** si $m^{+}=n+c$, separar $c=0$ (queda $n=m^{+}$) y $c=d^{+}$ (queda $m^{+}=(n+d)^{+}$, luego $m=n+d$ y la hipótesis da $n\subseteq m\subseteq m^{+}$).
6. **Cerrar** con inducción: vale para todo $m$; y como $n$ era arbitrario, para todos $m,n$.

**Plantilla:** $n=2$, $m=5$: $2\subseteq 5$ y $5=2+3$ con $c=3=2^{+}$. Estricto: $2\in 5$ y $5=2+c^{+}$ con $c=2$. ✔️

### I. Construir el isomorfismo $\mathbb N\to A$ (buen orden sin máximo)

1. **Verificar las hipótesis:** $(A,<)$ bien ordenado, **sin máximo**, y todo subconjunto no vacío acotado superiormente tiene máximo.
2. **Elegir el soporte:** $a=\min A$ y $G(n,b)=\min\{x\in A:\ b<x\}$.
3. **Justificar que $G$ está bien definida:** el segmento final abierto de $b$ es **no vacío** (no hay máximo) y tiene mínimo (buen orden).
4. **Aplicar $3.32$:** existe una única $F:\mathbb N\to A$ con $F(0)=\min A$ y $F(m^{+})=\min\{x>F(m)\}$.
5. **Probar que es estrictamente creciente:** $F(m^{+})$ pertenece al segmento $\{x>F(m)\}$, luego $F(m^{+})>F(m)$; de ahí **inyectiva**.
6. **Probar que es sobreyectiva** por contradicción: si $b\notin\operatorname{ran}F$, entonces $b$ es cota superior estricta de $\operatorname{ran}F$ (inducción: $b>F(0)$ porque $F(0)=\min A$; y $b>F(m)\Rightarrow b\ge\min\{x>F(m)\}=F(m^{+})$, con igualdad imposible porque $b$ no es imagen); luego $\operatorname{ran}F$ es acotado y no vacío, tiene máximo $c=F(k)$, pero $F(k^{+})>c$ contradice la maximalidad.
7. **Concluir:** $F$ es biyectiva, estrictamente creciente con inversa creciente, es decir un **isomorfismo de orden** $\mathbb N\to A$.

**Plantilla:** $A=\mathbb N\times\{0\}$ con el orden lexicográfico, sin máximo, acotados con máximo. $F(0)=(0,0)$, $F(m^{+})$ = siguiente par. Resultado: $F(m)=(m,0)$, isomorfismo. ✔️

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Separé el caso $n=0$ antes de escribir cualquier condición?
- [ ] ¿Usé $n^{-}$ solo cuando $n\neq 0$, y puse el cuantificador sobre $n^{-}$ y no sobre $n$?
- [ ] ¿El dominio de la recursión de tamaño $n$ es $n$ (nunca $n^{+}$)?
- [ ] ¿La $G$ que presento **no menciona** la función que estoy definiendo?
- [ ] ¿Declaré $A\neq\emptyset$ y $a\in A$ antes de aplicar $3.32$?
- [ ] ¿Para la unicidad restringí a $n$ y cité $3.31$, en vez de verificar pareja por pareja?
- [ ] ¿Antes de unir funciones verifiqué compatibilidad dos a dos?
- [ ] ¿Justifiqué $\mathrm{dom}\,F=\mathbb N$ con $\bigcup_{n}n=\mathbb N$ (no hay máximo)?
- [ ] ¿Si el ejercicio pide Fibonacci avisé que la recursión simple no alcanza (§3.5)?
- [ ] ¿Toda la matemática en $...$ en línea y en bloque con $$, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Dónde está |
|---|---|
| **Recursión completa** (necesaria para Fibonacci) | anunciada para la próxima clase; §3.5 |
| **Sistemas de Peano** | el isomorfismo de §4.I "sirve para hacer algo más adelante": los sistemas de Peano |
| Definir la **potenciación** con sus funciones soporte | tarea asignada (§2.G, tabla) |
| Demostrar las **propiedades** de suma, multiplicación, potenciación (conmutativa, asociativa, distributiva, cancelativa) | tarea: todas por inducción, "porque salieron por recursividad" |
| La otra dirección del teorema del orden (§2.H) | se probó fijando la **otra** variable y usando conmutatividad y asociatividad de la suma |
