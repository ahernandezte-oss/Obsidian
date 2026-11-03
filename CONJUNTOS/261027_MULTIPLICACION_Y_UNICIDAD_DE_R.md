# 📘 CHEATSHEET — TEORÍA DE CONJUNTOS · 27/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261027_MULTIPLICACION_Y_UNICIDAD_DE_R.md`
> - **Fecha de transcripción:** 27/10/2026 (`AAMMDD` = `261027`)
> - **Tema principal:** MULTIPLICACIÓN DE REALES (primero solo en $\mathbb R^{+}$, después ley de signos), $\mathbb R$ como **campo ordenado completo** y **teorema de unicidad**: todo campo ordenado completo es isomorfo a $\mathbb R$. Al final, **adelanto** de equipotencia, dominancia y $\mathcal P(A)\approx2^{A}$.
> - **Continuidad:** cierra lo que `261022_CORTADURAS_Y_REALES` dejó abierto (§3.6 de aquella: "falta la multiplicación"). Usa de allí la suma, el opuesto aditivo (§2.H), la unión $=$ ínfimo (§2.D) y el **lema de aproximación** (§2.G). Usa de `261020_RECURSION_COMPLETA_Y_SISTEMAS_DE_PEANO` los sistemas de Peano (§2.C). **No repite** nada de esas dos: solo lo cita.
> - **Cuidado con el solapamiento:** el bloque final de equipotencia es el **inicio** del tema que `261029_CARDINALIDAD_Y_FINITUD` desarrolla completo (§2.A–§2.B). Aquí solo se registra lo nuevo de esta clase (§2.I).
> - **Fuente:** transcripción de clase. Lo agregado o corregido por mí va marcado con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261027_MULTIPLICACION_Y_UNICIDAD_DE_R` §2.C».

**📎 Prerrequisitos:** $\mathbb R$ con la suma es grupo abeliano; $\mathbb R^{+}$ es cerrado bajo la suma; orden por contenencia inversa ($A\le B\iff B\subseteq A$); $\inf M=\bigcup M$; lema de aproximación de `221026` §2.G; sistemas de Peano de `201026` §2.C.

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Los dos factores son positivos?**
   - sí → se usa el **producto de cortaduras positivas** (§2.A).
   - no → **no** se puede usar: hay que pasar a la multiplicación por signos (§2.D).
2. **Paso 1 — ¿Aparece un producto de subconjuntos "tal cual"?** → ⚠️ solo sirve si ambos son positivos; en otro caso el resultado deja de ser cortadura (§3.1).
3. **Paso 2 — ¿Piden el neutro multiplicativo o que "el $1$ real" multiplica bien?** → doble contenencia con el argumento "no es cota inferior, luego está dentro" (§2.B, §4.A).
4. **Paso 3 — ¿Piden inverso multiplicativo de un real positivo?** → definición **por casos** (racional / irracional) y después $A\cdot A^{-1}=1_{\mathbb R}$ con el lema de aproximación (§2.C, §4.C).
5. **Paso 4 — ¿Producto de reales de signos cualesquiera?** → árbol de signos + ley de signos heredada de la distributividad (§2.D, §4.B).
6. **Paso 5 — ¿Piden "$\mathbb R$ es campo ordenado completo"?** → lista de axiomas uno por uno (§2.E, §4.D).
7. **Paso 6 — ¿Piden "el único campo ordenado completo"?** → isomorfismo: copias de $\mathbb N,\mathbb Z,\mathbb Q$, cortaduras en el campo, ínfimo (§2.F–§2.H, §4.E).
8. **Paso 7 — ¿Aparecen "equipotente", "dominancia", "$2^{A}$", "función característica"?** → §2.I (adelanto) y el desarrollo completo en `261029_CARDINALIDAD_Y_FINITUD`.

**Tabla de decisión:**

| Si el enunciado dice… | Herramienta | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "$A,B$ reales **positivos**", "$A\cdot B$" | **Producto de cortaduras** | $A\cdot B=\{a\cdot b: a\in A,\ b\in B\}$ | **§2.A** · §4.A |
| "$A\cdot 1_{\mathbb R}$", "neutro multiplicativo" | **Neutro** | $A\cdot1_{\mathbb R}=A$ | **§2.B** · §4.A |
| "$S_p\cdot S_q$", "el producto de reales racionales" | **Producto de segmentos** | $S_p\cdot S_q=S_{p\cdot q}$ | **§2.B** |
| "distributiva", "para que sea anillo" | **Distributividad** | $A\cdot(B+C)=A\cdot B+A\cdot C$ | **§2.B** |
| "$A^{-1}$", "inverso multiplicativo", "grupo abeliano sin el cero" | **Inverso por casos** | racional: $S_{r^{-1}}$ · irracional: $\{x^{-1}: x\in A^{\complement}\cap\mathbb Q^{+}\}$ | **§2.C** · §4.C |
| "$(-3)\cdot2$", "ley de signos", "producto de negativos" | **Multiplicación por signos** | $(-A)\cdot B=-(A\cdot B)$ | **§2.D** · §4.B |
| "campo ordenado completo" | **Axiomas** | grupo $+$, grupo $\cdot$ sin $0$, distributiva, positivos, supremo | **§2.E** · §4.D |
| "el único campo ordenado completo", "salvo isomorfismo" | **Isomorfismo** | $G(a+b)=G(a)+G(b)$, $G(ab)=G(a)G(b)$, $G(P)=P'$ | **§2.F–§2.H** · §4.E |
| "todo campo ordenado tiene copia de $\mathbb N$" | **$F$-inductivo** | $N_F=\bigcap\{B\ \text{F-inductivo}\}$ | **§2.G** |
| "equipotente", "$\approx$", "biyección" | **Equipotencia** | $\exists f:A\to B$ biyectiva | **§2.I** |
| "dominado por", "$\preccurlyeq$", "inyectiva" | **Dominancia** | $\exists f:A\to B$ inyectiva | **§2.I** |
| "$\mathcal P(A)$", "$2^{A}$", "función característica" | **Característica** | $B\mapsto\chi_B$ | **§2.I** · §4.F |

**Frases literales del profe → método:**

- «Yo no puedo definir la cortadura de esa manera.» → el producto de dos cortaduras cualesquiera **no** es cortadura; por eso se restringe a positivos (§2.A, §3.1).
- «Restringir el conjunto de trabajo.» → primero $\mathbb R^{+}$, después se extiende por signos (§2.D).
- «Es la ley de signos por definición… no, es porque yo me he enterado que es así.» → la ley de signos **se descubre** imponiendo la distributividad (§3.2).
- «Si $A\cdot0$ no es $0$, entonces la multiplicación no distribuye a la suma.» → $A\cdot0=0$ es consecuencia de la distributividad, no un capricho (§3.6).
- «Tengo muchos casos: tres, tres, tres, 27 casos.» → las propiedades generales se prueban **por casos de signo**, y primero se matan los de cero (§2.D).
- «Usted coge la primera parte del curso de cálculo diferencial y la pega acá.» → la unicidad se prueba reconstruyendo $\mathbb N\subseteq\mathbb Z\subseteq\mathbb Q$ dentro del campo (§2.G).

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Producto de cortaduras positivas

Para $A,B\in\mathbb R^{+}$ (reales positivos):

$$
A\cdot B:=\{a\cdot b\ :\ a\in A,\ b\in B\}
$$

**Teorema.** Si $A,B$ son reales positivos, entonces $A\cdot B$ es un número real **positivo**.

**🔤 Diccionario:**
- $\mathbb R^{+}$: los reales **estrictamente** contenidos en $0_{\mathbb R}$, es decir los mayores que cero (`221026` §2.F).
- $a\cdot b$: producto **en $\mathbb Q$**, porque $a,b$ son racionales.
- Positivo: todo elemento de $A\cdot B$ es positivo, así que $0\notin A\cdot B$; de ahí que el resultado quede contenido en $0_{\mathbb R}$.
- La razón de restringir: los productos de negativos "arrastran" todos los racionales negativos y el conjunto deja de ser cortadura (§3.1).
- (C3) usa que $a>0$ tiene inverso **en $\mathbb Q$**: se cancela $a$ multiplicando por $a^{-1}$.

### B. Propiedades en $\mathbb R^{+}$

$$
A\cdot B=B\cdot A,\qquad (A\cdot B)\cdot C=A\cdot(B\cdot C),\qquad A\cdot(B+C)=A\cdot B+A\cdot C
$$

$$
A\cdot1_{\mathbb R}=A,\qquad S_p\cdot S_q=S_{p\cdot q}\quad (p,q\in\mathbb Q^{+})
$$

$$
A\le_{\mathbb R}B,\ C>0\ \Longrightarrow\ A\cdot C\le_{\mathbb R}B\cdot C
$$

**🔤 Diccionario:**
- $1_{\mathbb R}=S_1=\{x\in\mathbb Q: x>1\}$: neutro multiplicativo (y es positivo).
- $S_p\cdot S_q=S_{p\cdot q}$: la multiplicación de los **reales racionales** es la copia de la de $\mathbb Q$.
- Conmutativa y asociativa: "salen fáciles" porque se heredan de $\mathbb Q$.
- **Distributiva: no es fácil**, es la que hay que probar; es también la que obliga a la ley de signos (§3.2).
- Monotonía: multiplicar por un positivo **conserva** el orden; para $C<0$ lo invierte (§3.3).

### C. Inverso multiplicativo (solo para positivos)

$$
A^{-1}:=\begin{cases} S_{r^{-1}} & \text{si } A=S_r\ \text{es racional}\\[2pt] \big\{x^{-1}\ :\ x\in A^{\complement}\cap\mathbb Q^{+}\big\} & \text{si } A\ \text{es irracional}\end{cases}
$$

$$
A\cdot A^{-1}=1_{\mathbb R}\qquad (A>0)
$$

**🔤 Diccionario:**
- $\mathbb Q^{+}$: los racionales positivos; se intersecta con el complemento para no meter negativos (si se invierte un negativo el orden se rompe y el conjunto deja de mirar "hacia arriba").
- $x^{-1}$: inverso **en $\mathbb Q$**.
- Caso irracional: se invierten los racionales positivos que quedaron **fuera** de $A$; al invertir, lo que estaba "antes del hueco" pasa a estar "después", y por eso resulta una cortadura hacia arriba.
- **Por qué por casos:** si se aplica la fórmula del irracional a un real racional se obtiene un conjunto con mínimo, y un número real no puede tener mínimo (`221026` §2.B).
- $A\cdot A^{-1}=1_{\mathbb R}$ se prueba por doble contenencia; la contenencia difícil usa el lema de aproximación de `221026` §2.G con $T=x-1$.
- Con esto, $(\mathbb R^{+},\cdot)$ es **grupo abeliano**; y $(\mathbb R\setminus\{0_{\mathbb R}\},\cdot)$ también, por la ley de signos.

### D. Multiplicación en todos los reales: ley de signos

$$
A\cdot B:=\begin{cases}
A\cdot B & \text{si } A,B>0\\
0_{\mathbb R} & \text{si } A=0_{\mathbb R}\ \text{o}\ B=0_{\mathbb R}\\
-\big(A\cdot(-B)\big) & \text{si } A>0>B\\
-\big((-A)\cdot B\big) & \text{si } A<0<B\\
(-A)\cdot(-B) & \text{si } A,B<0
\end{cases}
$$

**Consecuencias (se prueban por casos de signo):**

$$
(-1_{\mathbb R})\cdot A=-A,\qquad (-A)\cdot B=-(A\cdot B),\qquad (-A)\cdot(-B)=A\cdot B
$$

**🔤 Diccionario:**
- $-A$: el opuesto aditivo de `221026` §2.H.
- $A>0$ significa $A\subseteq0_{\mathbb R}$ estrictamente; $A<0$ significa $0_{\mathbb R}\subsetneq A$.
- Las tres identidades son **para todos** los reales, no solo para los de signo fijo: se prueban caso por caso (nueve casos, de los cuales los de cero se descartan primero).
- La definición está **forzada**: cualquier otra que se quiera poner rompe la distributividad (§3.2).
- $\cdot$ y $-$: $-A\cdot B$ se lee $-(A\cdot B)$; el signo menos es de la suma, nunca "de la multiplicación".

### E. $\mathbb R$ es campo ordenado completo

$$
\text{campo: }(\mathbb R,+,\cdot)\ \text{con distributiva},\qquad +:\ \text{grupo abeliano},\qquad \cdot:\ \text{grupo abeliano en } \mathbb R\setminus\{0_{\mathbb R}\}
$$

$$
\text{ordenado: }\mathbb R^{+}\neq\emptyset,\quad 0\notin\mathbb R^{+},\quad \mathbb R^{+}+\mathbb R^{+}\subseteq\mathbb R^{+},\quad \mathbb R^{+}\cdot\mathbb R^{+}\subseteq\mathbb R^{+}
$$

$$
A<B\iff\exists\,C>0\ \ (A+C=B)\qquad\text{(orden dado por los positivos)}
$$

$$
\text{completo: }M\subseteq\mathbb R,\ M\neq\emptyset,\ M\ \text{acotado superiormente}\ \Longrightarrow\ \exists\sup M
$$

**🔤 Diccionario:**
- "Campo" son **dos** grupos abelianos más la distributiva que los **ensambla**; sin distributiva no hay campo, solo dos estructuras sueltas.
- $\mathbb R\setminus\{0_{\mathbb R}\}$: el cero se quita porque no tiene inverso multiplicativo.
- Los positivos son el puente entre las operaciones y el orden: dan la monotonía.
- El supremo ya está: ínfimo por unión (`221026` §2.D) y supremo por opuestos (`221026` §2.J).

### F. Isomorfismo de campos (ordenados)

$$
G:\mathbb R\to F\ \text{es isomorfismo de campos}\iff\ G\ \text{biyectiva},\quad G(a+b)=G(a)+G(b),\quad G(a\cdot b)=G(a)\cdot G(b)
$$

$$
G\ \text{es isomorfismo de campos ordenados}\iff G\ \text{además cumple}\ G\big(\mathbb R^{+}\big)=F^{+}
$$

**🔤 Diccionario:**
- $F$: otro campo (ordenado, completo) que se quiere comparar con $\mathbb R$.
- $G$ biyectiva: es lo que hace que la comparación sea "copia", no solo "parecido".
- $G(a+b)=G(a)+G(b)$: las sumas de un lado van a las sumas del otro.
- $G(ab)=G(a)G(b)$: lo mismo con el producto.
- $G(\mathbb R^{+})=F^{+}$: los positivos a los positivos; con eso el orden se transporta y no hay que probarlo aparte.
- Isomorfismo de **orden** solo: bastaría $a\le b\Leftrightarrow G(a)\le G(b)$; el de campos ordenados pide las tres cosas.

### G. Copias de $\mathbb N$, $\mathbb Z$ y $\mathbb Q$ en un campo ordenado $F$

$$
B\subseteq F\ \text{es } F\text{-inductivo}:\iff 0_F\in B\ \wedge\ \big(a\in B\Rightarrow a+1_F\in B\big)
$$

$$
N_F:=\bigcap\{\,B\subseteq F:\ B\ \text{es } F\text{-inductivo}\,\}
$$

$$
n_F:=\underbrace{1_F+\cdots+1_F}_{n\ \text{veces}},\qquad Z_F=\{a-b:\ a,b\in N_F\},\qquad \mathbb Q_F=\Big\{\frac{a}{b}:\ a\in Z_F,\ b\in Z_F\setminus\{0_F\}\Big\}
$$

**🔤 Diccionario:**
- $0_F$, $1_F$: el cero y el uno **del campo $F$**; no son $0$ ni $1$ de $\mathbb N$ ni de $\mathbb R$.
- $F$-inductivo: la versión "del campo" de conjunto inductivo; el sucesor se reemplaza por **sumar $1_F$**.
- $N_F$: el menor $F$-inductivo; es la "copia de $\mathbb N$" candidata.
- $N_F$ es infinito **si el campo está ordenado** (los $n_F$ son todos distintos), y entonces $(N_F,0_F,+1_F)$ es un **sistema de Peano** (`201026` §2.C) y $N_F\approx\mathbb N$.
- En un campo **no ordenado** esto falla: en $\mathbb Z_3$, $N_F=\{0,1,2\}=\mathbb Z_3$ porque $2+1=0$; no es copia de $\mathbb N$.
- $Z_F$ y $\mathbb Q_F$: copias de los enteros y de los racionales construidas **dentro** de $F$ (con las operaciones de $F$).
- $\mathbb Q_F$ es denso en $F$ y $N_F$ no es acotado en $F$: de ahí que todo elemento esté entre dos enteros consecutivos.

### H. Cortadura de un elemento del campo y la función de isomorfismo

Para $a\in F$:

$$
C_a:=\{q\in\mathbb Q_F:\ a<q\}\subseteq\mathbb Q_F
$$

$$
G:\mathbb R\to F,\qquad G(r):=\inf_F\big(G_3[C_r]\big),\qquad G_3:\mathbb Q_{\mathbb R}\to\mathbb Q_F\ \text{(isomorfismo)}
$$

**🔤 Diccionario:**
- $C_a$: la cortadura que el elemento $a$ **define** dentro del campo; se toma solo sobre los racionales del campo ($\mathbb Q_F$), que son los que se pueden transportar.
- $C_r$: la cortadura de $r\in\mathbb R$ según `221026` §2.B (un conjunto de racionales).
- $G_3[C_r]$: la imagen de esa cortadura por el isomorfismo entre los dos racionales; queda dentro de $F$.
- $G_3[C_r]$ no es vacío y está acotado inferiormente en $F$, así que tiene ínfimo **porque $F$ es completo**; ese ínfimo es $G(r)$.
- $\{C_a: a\in F\}$ cumple las cuatro condiciones de `221026` §2.B, **con una diferencia**: la cuarta es contenencia y no igualdad, porque las cotas inferiores se toman sobre todo $F$ y no solo sobre $\mathbb Q_F$.
- $G$ es estrictamente creciente (se prueba metiendo un racional entre dos reales por densidad de $\mathbb Q_F$), luego inyectiva y respeta positivos; la sobreyectividad se prueba con el mismo truco al revés.

### I. Adelanto: equipotencia, dominancia y $\mathcal P(A)\approx2^{A}$

$$
A\approx B:\iff\exists\,f:A\to B\ \text{biyectiva}\qquad\text{(equipotencia)}
$$

$$
A\preccurlyeq B:\iff\exists\,f:A\to B\ \text{inyectiva}\qquad\text{(dominancia)}
$$

$$
H:\mathcal P(A)\to 2^{A},\qquad H(B)=\chi_B,\qquad \chi_B(a)=\begin{cases}1 & \text{si } a\in B\\ 0 & \text{si } a\notin B\end{cases}
$$

$$
A\approx B\ \Longrightarrow\ \mathcal P(A)\approx\mathcal P(B),\qquad A\approx D\ \wedge\ B\approx E\ \Longrightarrow\ A\times B\approx D\times E,\quad B^{A}\approx E^{D}
$$

**🔤 Diccionario:**
- $2$: el natural $2=\{0,1\}$; por eso $2^{A}$ es el conjunto de **funciones** $A\to\{0,1\}$, no la potencia numérica.
- $\chi_B$: **función característica** de $B$; "dónde está cada elemento" codificado con $0$ y $1$.
- $H$ biyectiva: inyectiva porque $\chi_B=\chi_C\Rightarrow B=C$; sobreyectiva porque $f\mapsto f^{-1}[\{1\}]$ deshace.
- $g\circ h\circ f^{-1}$: la fórmula general para transportar una función por dos biyecciones; es el molde de todos los transportes.
- Estos temas se desarrollan completos en `261029_CARDINALIDAD_Y_FINITUD` §2.A–§2.B: aquí solo queda registrado el punto de partida.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### 3.1 Por qué el producto de cortaduras solo funciona con positivos

| Situación | Qué pasa con $A\cdot B=\{ab\}$ |
|---|---|
| $A,B$ positivos | el resultado es cortadura: todo producto es positivo y "mira hacia arriba" |
| algún factor negativo | el producto empieza a producir todos los racionales negativos |
| resultado | deja de ser una cortadura (recoge "hacia $-\infty$") ⇒ **hay que definir por signos** |

**Regla:** el producto de subconjuntos es una definición **válida** para positivos y **solo** para positivos. Para el resto se usa el árbol de §2.D.

### 3.2 La ley de signos está obligada por la distributividad

$$
(-3+3)\cdot2=0\ \Longrightarrow\ (-3)\cdot2+3\cdot2=0\ \Longrightarrow\ (-3)\cdot2=-(3\cdot2)
$$

1. Se quiere que la multiplicación **distribuya** sobre la suma (es la propiedad que ensambla el campo).
2. Entonces $(-A)\cdot B$ queda **forzado** a ser $-(A\cdot B)$; no es una regla mnemotécnica.
3. Y $A\cdot0=0$ también se deduce: $A\cdot0+A\cdot0=A\cdot(0+0)=A\cdot0$, y se cancela en el grupo.
4. Consecuencia práctica: en los ejercicios, "signos iguales dan positivo" se **justifica** con distributividad, no con la intuición.

### 3.3 Qué se hereda y qué hay que probar

| Propiedad | ¿Se hereda de $\mathbb Q$? | Comentario |
|---|---|---|
| conmutativa y asociativa (producto) | ✅ | "salen fáciles": misma definición sobre productos |
| distributiva | ❌ | hay que probarla; usa el orden y la densidad |
| neutro $1_{\mathbb R}$ | ❌ | doble contenencia con "no es cota inferior" |
| inverso multiplicativo | ❌ | definición por casos + lema de aproximación |
| monotonía del orden al multiplicar | ❌ | se prueba con distributiva; **se invierte** si el factor es negativo |
| opuesto aditivo | ✅ ya estaba | `221026` §2.H |
| supremo | ✅ ya estaba | `221026` §2.J |

### 3.4 Trampas típicas (y por qué están mal)

| Lo que se escribe | Por qué está mal |
|---|---|
| $A\cdot B=\{ab\}$ para reales cualesquiera | no es cortadura en general (§3.1) |
| $A^{-1}$ con la fórmula del irracional en un racional | da un conjunto con mínimo: no es real (§2.C) |
| "$-A\cdot B=A\cdot(-B)$" sin decir qué signo tiene $A$ | es cierto, pero hay que probarlo por casos |
| probar la distributiva "por conmutatividad" | la distributiva no se deduce de la conmutatividad |
| usar $A\cdot0_{\mathbb R}=0_{\mathbb R}$ como definición | es consecuencia de la distributividad: **se demuestra** |
| afirmar que $N_F$ de cualquier campo es copia de $\mathbb N$ | falso: en $\mathbb Z_3$ es todo el campo (§2.G) |

### 3.5 Campos: los dos casos patológicos

| Campo | Qué pasa | Consecuencia |
|---|---|---|
| campo con un solo elemento | $0_F=1_F$ | es el **único** campo donde pasa |
| campo con más de un elemento | $0_F\neq1_F$ | se prueba con $A\cdot0=0$ y la distributiva |
| $\mathbb Z_3$ | $2+1=0$; $N_F=\mathbb Z_3$ | $N_F$ finito: **no** es copia de $\mathbb N$ |
| campo **ordenado** | $N_F$ infinito, $0_F\notin$ positivos | $N_F$ es sistema de Peano ⇒ copia de $\mathbb N$ |

**Regla:** la frase "todo campo ordenado tiene copia de $\mathbb N$" necesita la palabra **ordenado**; sin ella es falsa.

### 3.6 Qué aporta cada axioma al producto

| Axioma | Para qué sirve en la práctica |
|---|---|
| asociativa y conmutativa | reordenar productos sin miedo |
| neutro $1_{\mathbb R}$ | escribir $A=A\cdot1$ |
| inverso | cancelar: $A\cdot B=A\cdot C\Rightarrow B=C$ si $A\neq0$ |
| distributiva | **ensambla** suma y producto: es la única que las relaciona |
| positivos | da la monotonía del orden |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### A. Probar que $A\cdot B$ es un número real (positivos)

1. **(C1):** como $A,B\neq\emptyset$, tomar $a\in A$, $b\in B$; entonces $a\cdot b\in A\cdot B$.
2. **(C2):** probar $0\notin A\cdot B$: si $0=a\cdot b$, en $\mathbb Q$ se tendría $a=0$ o $b=0$, y como $A,B$ son positivos (todos sus elementos $>0$), es imposible.
3. **(C3) por contradicción:** si $x=a\cdot b$ fuera el mínimo, entonces $a\cdot b\le a'\cdot b'$ para todos $a',b'$; tomando $a'=a$ queda $b\le b'$ para todo $b'\in B$, o sea $b=\min B$: contradicción.
4. **(C4):** sea $r\notin A\cdot B$; si $r$ no fuera cota inferior, habría $a\in A$, $b\in B$ con $r\ge a\cdot b$; como $b>0$ tiene inverso en $\mathbb Q$, $r\cdot b^{-1}\ge a$, así que $r\cdot b^{-1}$ **no** es cota inferior de $A$, luego $r\cdot b^{-1}\in A$; entonces $r=(r\cdot b^{-1})\cdot b\in A\cdot B$: contradicción.
5. **Concluir:** $A\cdot B$ es número real; y como $0\notin A\cdot B$, todos sus elementos son positivos, luego $A\cdot B\subseteq0_{\mathbb R}$, es decir es **positivo**.

**Plantilla:** $1_{\mathbb R}\cdot2_{\mathbb R}=\{x\cdot y: x>1,\ y>2\}=\{z: z>2\}=2_{\mathbb R}$, que es positivo. ✔️

### B. Multiplicar dos reales de signo cualquiera

1. **Determinar el signo** de cada factor: positivo ($\subseteq0_{\mathbb R}$ estricto), cero ($=0_{\mathbb R}$) o negativo ($\supsetneq0_{\mathbb R}$).
2. **Si alguno es cero:** el producto es $0_{\mathbb R}$ (consecuencia de la distributividad).
3. **Si los dos son positivos:** producto directo de cortaduras (§2.A).
4. **Si hay uno positivo y uno negativo:** oponer el negativo, multiplicar los dos positivos y poner el signo menos: $A\cdot B=-(A\cdot(-B))$.
5. **Si los dos son negativos:** oponer los dos y multiplicar: $A\cdot B=(-A)\cdot(-B)$.
6. **Verificar** el signo del resultado contra la ley de signos y, si se pide, probar las identidades por casos.

**Plantilla:** $A<0<B$. Entonces $-A>0$ y $A\cdot B=-((-A)\cdot B)$; como $(-A)\cdot B>0$, el producto $A\cdot B$ es negativo. ✔️

### C. Definir y probar el inverso multiplicativo

1. **Distinguir el caso:** ¿$A=S_r$ es real racional o $A$ es irracional? (ver `221026` §2.E).
2. **Caso racional:** $A^{-1}=S_{r^{-1}}$; ya es cortadura y $S_r\cdot S_{r^{-1}}=S_1=1_{\mathbb R}$ por §2.B.
3. **Caso irracional:** $A^{-1}=\{x^{-1}: x\in A^{\complement}\cap\mathbb Q^{+}\}$; probar (C1)–(C4) como cortadura.
4. **Probar $A^{-1}$ positivo:** si $x\in A^{\complement}\cap\mathbb Q^{+}$ entonces $x^{-1}>0$.
5. **Probar $A\cdot A^{-1}=1_{\mathbb R}$** por doble contenencia; en la difícil usar el lema de aproximación (`221026` §2.G) con $T=X-1$.
6. **Cerrar:** $(\mathbb R^{+},\cdot)$ es grupo abeliano; y con la ley de signos, $(\mathbb R\setminus\{0_{\mathbb R}\},\cdot)$ también.

**Plantilla:** $A=2_{\mathbb R}=S_2$ (racional): $A^{-1}=S_{1/2}$. Chequeo: $S_2\cdot S_{1/2}=S_{1}=1_{\mathbb R}$. ✔️

### D. Verificar que $\mathbb R$ es campo ordenado completo

1. **Grupo aditivo:** conmutativa, asociativa, neutro $0_{\mathbb R}$, opuesto $-A$ (`221026` §2.F, §2.H).
2. **Grupo multiplicativo:** conmutativa, asociativa, neutro $1_{\mathbb R}$, inverso $A^{-1}$ para $A\neq0_{\mathbb R}$ (§2.B, §2.C).
3. **Distributiva:** §2.B para positivos y §2.D para el resto (por casos).
4. **Positivos:** $\mathbb R^{+}\neq\emptyset$, $0_{\mathbb R}\notin\mathbb R^{+}$, cerrado bajo $+$ y bajo $\cdot$.
5. **Orden:** $A<B\iff\exists C>0\ (A+C=B)$, y es total y compatible con las operaciones.
6. **Completitud:** ínfimo por unión y supremo por opuestos (`221026` §2.D, §2.J).
7. **Concluir:** $(\mathbb R,+,\cdot,\le)$ es **campo ordenado completo**.

**Plantilla (chequeo rápido de positivos):** $1_{\mathbb R}\in\mathbb R^{+}$ (es $\subseteq0_{\mathbb R}$ estricto) y $1_{\mathbb R}+1_{\mathbb R}=2_{\mathbb R}\in\mathbb R^{+}$: cerrado bajo suma. ✔️

### E. Probar que un campo ordenado completo $F$ es isomorfo a $\mathbb R$

1. **Copias dentro de $F$:** definir $N_F$ (menor $F$-inductivo), probar que es sistema de Peano (usando que $F$ es ordenado) ⇒ $N_F\approx\mathbb N$; construir $Z_F$ y $\mathbb Q_F$.
2. **Propiedades del campo:** $\mathbb Q_F$ es denso en $F$ y $N_F$ no es acotado; todo $a\in F$ queda entre dos enteros consecutivos de $F$.
3. **Definir** $C_a=\{q\in\mathbb Q_F: a<q\}$ y verificar que cumple las cuatro condiciones de cortadura (la cuarta solo como contenencia).
4. **Definir** $G(r)=\inf_F G_3[C_r]$, donde $G_3:\mathbb Q_{\mathbb R}\to\mathbb Q_F$ es el isomorfismo entre los racionales. El ínfimo existe por completitud de $F$.
5. **Buena definición y positivos:** $G_3[C_r]$ es no vacío y acotado inferiormente; y $G(r)>0_F$ si y solo si $r>0$.
6. **Inyectividad:** probar que $G$ es estrictamente creciente; para comparar dos reales se **meten racionales en el medio** (densidad), y solo a esos se les aplica $G_3$.
7. **Sobreyectividad:** dado $A\in F$, tomar $C_A\subseteq\mathbb Q_F$, transportarlo a $\mathbb Q_{\mathbb R}$ por $G_3^{-1}$, tomar el ínfimo $r\in\mathbb R$ y probar $G(r)=A$ (misma técnica de meter racionales en el medio).
8. **Operaciones:** $G(A+B)=G(A)+G(B)$ y $G(A\cdot B)=G(A)\cdot G(B)$ se reducen a que la cortadura de una suma es la suma de cortaduras, y lo análogo para el producto de positivos; después se extiende por signos.
9. **Concluir:** $G$ es isomorfismo de campos ordenados; por tanto todo campo ordenado completo es una copia de $\mathbb R$.

**Plantilla (el paso clave):** para ver $G(r)<G(s)$ con $r<s$, se toma $q\in\mathbb Q$ con $r<q<s$ (densidad). Entonces $q\in C_r$ y $q\notin C_s$; al aplicar $G_3$ se obtiene $G_3(q)\in G_3[C_r]$ y $G_3(q)\notin G_3[C_s]$, y como $G(r)$ es ínfimo de lo primero y $G(s)$ de lo segundo, $G(r)\le G_3(q)<G(s)$. ✔️

### F. Construir la biyección $\mathcal P(A)\to2^{A}$

1. **Definir** $H(B)=\chi_B$ con $\chi_B(a)=1$ si $a\in B$ y $0$ si $a\notin B$.
2. **Buena definición:** $\chi_B$ tiene dominio $A$ y codominio $\{0,1\}$, así que está en $2^{A}$.
3. **Inyectividad:** si $\chi_B=\chi_C$, entonces para cada $a\in A$: $a\in B\iff\chi_B(a)=1\iff\chi_C(a)=1\iff a\in C$; luego $B=C$.
4. **Sobreyectividad:** dada $f\in2^{A}$, tomar $B=f^{-1}[\{1\}]$; entonces $\chi_B(a)=1\iff a\in B\iff f(a)=1$, luego $\chi_B=f$.
5. **Concluir:** $H$ es biyectiva y $\mathcal P(A)\approx2^{A}$.

**Plantilla:** $A=\{1,2\}$. Subconjuntos: $\emptyset,\{1\},\{2\},\{1,2\}$. Características: $(0,0),(1,0),(0,1),(1,1)$: cuatro funciones, cuatro subconjuntos. ✔️

### G. Transportar una equipotencia

1. **Fijar** las biyecciones: $f:A\to D$ y $g:B\to E$.
2. **Unión disjunta:** si $A\cap B=\emptyset$ y $D\cap E=\emptyset$, $f\cup g:A\cup B\to D\cup E$ es biyectiva (dominios disjuntos ⇒ es función; y es inyectiva y sobreyectiva por partes).
3. **Producto cartesiano:** $h(a,b)=(f(a),g(b))$ es biyectiva $A\times B\to D\times E$ (componente a componente).
4. **Funciones:** $h\mapsto g\circ h\circ f^{-1}$ es biyectiva $B^{A}\to E^{D}$; la inversa es $k\mapsto g^{-1}\circ k\circ f$.
5. **Al revés:** $k\mapsto g^{-1}\circ k\circ f$ devuelve todo, así que el transporte es reversible.
6. **Verificar el dominio:** al componer importa que $f^{-1}$ exista y que los dominios y codominios encajen ($A\to B\to E\leftarrow D$).

**Plantilla:** $A=\{1\}$, $B=\{a,b\}$, $D=\{7\}$, $E=\{x,y\}$ con $f(1)=7$, $g(a)=x$, $g(b)=y$. Entonces $B^{A}$ tiene $2$ funciones y $E^{D}$ tiene $2$; el transporte $h\mapsto g\circ h\circ f^{-1}$ las empareja una a una. ✔️

---

## ✅ 5. CHECKLIST FINAL

- [ ] ¿Verifiqué que los dos factores son **positivos** antes de usar $A\cdot B=\{ab\}$?
- [ ] ¿En (C2) del producto probé que $0\notin A\cdot B$ (y no solo que el producto no es vacío)?
- [ ] ¿En (C3) cancelé con $a^{-1}$ usando que $a>0$ es racional no nulo?
- [ ] ¿Al definir $A^{-1}$ distinguí el caso racional del irracional?
- [ ] ¿Usé el lema de aproximación (`221026` §2.G) con $T$ **racional positivo**?
- [ ] ¿Justifiqué la ley de signos con la distributividad y no con la intuición?
- [ ] ¿Al probar propiedades generales, maté primero los casos con cero?
- [ ] ¿Recordé que el cero **no** tiene inverso multiplicativo y por eso se quita del grupo?
- [ ] ¿En el isomorfismo verifiqué las **tres** cosas (suma, producto, positivos) más la biyección?
- [ ] ¿Escribí "campo **ordenado**" cuando uso que $N_F$ es copia de $\mathbb N$?
- [ ] ¿En $\mathcal P(A)\approx2^{A}$ usé $2=\{0,1\}$ y funciones, no la potencia numérica?
- [ ] ¿Toda la matemática en $...$ en línea y en bloque con $$, sin bloques de código?

---

## 🔗 6. LO QUE QUEDÓ ABIERTO EN CLASE

| Pendiente | Dónde está |
|---|---|
| Las **27 combinaciones de casos** en las propiedades de la multiplicación general (conmutativa, asociativa, distributiva) | §2.D: se resumen matando primero los casos con cero |
| $A+(-A)=0_{\mathbb R}$ para la resta y las identidades $(-A)\cdot B=-(A\cdot B)$, $(-A)\cdot(-B)=A\cdot B$ | ejercicios (dos de los tres) |
| Detalles de la sobreyectividad de $G$ en el teorema de unicidad | esbozados en §2.H y §4.E; el profe los dio "esquemáticos" |
| Modelos alternativos de $\mathbb R$ (cortaduras, sucesiones de Cauchy, vía $\mathbb Q^{+}\cup\{0\}\to\mathbb R^{+}\cup\{0\}$) | §2.F: todos isomorfos por el teorema de unicidad |
| **Equipotencia y dominancia** en serio: reflexiva, simétrica, transitiva; $\mathcal P(A)\approx2^{A}$; transportes | §2.I (inicio) y `261029_CARDINALIDAD_Y_FINITUD` §2.A–§2.B (completo) |
| No se puede definir **cardinal** con los siete axiomas actuales | hace falta añadir dos axiomas más; §2.I |
| Ejercicios sueltos de la pizarra sobre $\bigcup\mathcal C$ transitivo y uniones de productos | quedaron sin enunciar con claridad en la transcripción |
