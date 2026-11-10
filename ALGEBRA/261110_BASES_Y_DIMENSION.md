# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 10/11/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261110_BASES_Y_DIMENSION.md` |
| **Tema principal** | Teoremas 7–13: caracterizaciones de LD, base, existencia de base, unicidad de representación, Steinitz y dimensión |
| **Fecha base** | 10/11/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261110` + apuntes (Teoremas 7–13) + Grossman cap. 4–5 |
| **Cómo citarla** | «📘 Cheatsheet `261110_BASES_Y_DIMENSION` §2.H» |
| **Notación** | $V$ espacio vectorial · $\mathcal{B}$ base · $\operatorname{Gen}S$ · LI/LD · $0_V$ cero del espacio · $P_n$ polinomios de grado $\le n$ · $M_{mn}$ matrices · $E_{ij}$ matriz unidad · $\dim V$ |
| **No repite** | definición de subespacio y 10 axiomas → `261103` §2.A–C; LI/LD en $\mathbb{R}^n$ con matriz → `261029`; espacios abstractos → `261105` |
| **🔔 Sincronización** | Copia espejo en `02_NOTAS_OBSIDIAN/ALGEBRA` + push por git el 2026-11-10 ✅ |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿Qué me piden: decidir, probar o refutar?**
- **Decidir** (¿LI o LD?, ¿es base?) → definición o teoremas → §4.1, §4.3.
- **Probar** (demostrar que es base) → 2 condiciones: LI **y** genera → §4.3.
- **Refutar** (mostrar que **no** es base) → un solo contraejemplo basta → §4.4.
- **Contar** (¿cuántos vectores LI caben?) → Steinitz → §4.5.

**Paso 1 — Tabla de decisión**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "¿Es LI o LD?" | Sistema homogéneo | $\alpha_1v_1+\dots+\alpha_kv_k=0_V$ | §2.A · §4.1 |
| "¿Alguno es combinación lineal de los anteriores?" | Teorema 7.3: reordenar con $v_1\ne0_V$ | $v_i\in\operatorname{Gen}\{v_1,\dots,v_{i-1}\}$ | §2.B · §4.2 |
| "El conjunto contiene al $\vec0$" | Teorema 8.1 | LD inmediato | §2.C · §3 Caso 5 |
| "¿Es base de $V$?" | LI + genera | las dos condiciones | §2.E · §4.3 |
| "¿La representación es única?" | Teorema 11 | $v=\sum c_iv_i$ con $c_i$ únicos | §2.G |
| "Refutar que es base" | Contraejemplo | LD con coeficientes, o $v\notin\operatorname{Gen}$ | §3 Caso 4 · §4.4 |
| "¿Cuántos vectores LI caben?" | Teorema 12 (Steinitz) | LI $\Rightarrow m\le n$ | §2.H · §4.5 |
| "¿Todas las bases miden lo mismo?" | Teorema 13 | $\dim V=n$ | §2.I |
| "¿Cuál es $\dim V$?" | Contar una base | $\dim V=\vert\mathcal{B}\vert$ | §2.I |
| "¿Existe base?" | Teorema 10 (no se demuestra) | todo E.V. tiene base | §2.E |
| "En $\dim n$ tengo $n$ vectores" | Atajo: basta 1 condición | LI $\Rightarrow$ base; genera $\Rightarrow$ base | §3 Caso 3 |

**Frases literales del profe → método**
- *"El primero no puede ser cero"* → para el Teorema 7.3 reordena la lista y pon al frente un vector no nulo.
- *"Es un poco más fuerte"* → la forma con "anteriores" exige más que "alguno de los otros".
- *"Existe un $i$ mayor o igual que dos"* → el vector redundante nunca es el primero.
- *"Ningún elemento es combinación lineal de los demás"* → así se prueba LI.
- *"El cardinal de la base es la dimensión"* → cuenta elementos de la base, no coeficientes.
- *"No necesariamente cualquier tres polinomios son base de $P_2$"* → LI sola no basta.
- *"Si es falso, exhiba un elemento que no se puede generar"* → contraejemplo concreto.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. LI / LD (definición operativa)
$$\{v_1,\dots,v_k\}\ \text{es LI}\iff \alpha_1v_1+\dots+\alpha_kv_k=0_V\ \Rightarrow\ \alpha_1=\dots=\alpha_k=0$$
$$\text{es LD}\iff \exists\,(\alpha_1,\dots,\alpha_k)\ne(0,\dots,0):\ \alpha_1v_1+\dots+\alpha_kv_k=0_V$$

**🔤 Diccionario:** $v_i$ vectores del conjunto · $\alpha_i$ escalares incógnita · $0_V$ cero del espacio (polinomio nulo, matriz cero, función nula) · solución **trivial** = todos los $\alpha_i=0$ · LD = existe solución no trivial.

### B. Teorema 7 — cuándo un vector es combinación de los otros
1. $S=\{v\}$: $\ S$ LD $\iff v=0_V$.
2. $S=\{v_1,\dots,v_k\}$, $k\ge2$: $\ S$ LD $\iff$ algún $v_i$ es combinación lineal de los **restantes**.
3. $S=\{v_1,\dots,v_k\}$, $k\ge2$, con $v_1\ne0_V$: $\ S$ LD $\iff$ existe $i\ge2$ tal que $v_i$ es combinación lineal de los **anteriores** $v_1,\dots,v_{i-1}$.

➕ Lectura: (3) localiza el vector redundante. Si el primero es nulo, el conjunto ya es LD por el Teorema 8.1 y se reordena la lista para aplicar (3) con otro vector no nulo al frente.

**🔤 Diccionario:** $i\ge2$ índice del vector redundante · "anteriores" = $v_1,\dots,v_{i-1}$ (todos, no alguno) · "restantes" = todos los demás.

### C. Teorema 8 — consecuencias inmediatas
| Parte | Enunciado | Atajo |
|---|---|---|
| 1 | Todo conjunto que contiene a $\vec0$ es LD | ver el $\vec0$ ⇒ LD |
| 2 | Dos vectores son LD $\iff$ uno es múltiplo escalar del otro | proporcionales ⇒ LD |
| 3 | Si $S$ contiene un subconjunto LD, entonces $S$ es LD | al conjunto LD le **sobra** algo |
| 4 | Todo subconjunto de un conjunto LI es LI | al conjunto LI le **falta** algo |

**🔤 Diccionario:** subconjunto LD contenido ⇒ el grande hereda la dependencia · subconjunto de un LI ⇒ el pequeño hereda la independencia · "múltiplo escalar" = $u=c\,v$ con $c\in\mathbb{R}$.

### D. Teorema 9 — unicidad y extensión
Sea $S=\{v_1,\dots,v_n\}$ LI en $V$:
1. Todo $v\in\operatorname{Gen}S$ se escribe de forma **única**: si $v=\sum c_iv_i=\sum d_iv_i$, entonces $c_i=d_i$ para todo $i$.
2. Si $v\notin\operatorname{Gen}S$, entonces $S\cup\{v\}=\{v_1,\dots,v_n,v\}$ es LI.

**🔤 Diccionario:** $c_i,d_i$ dos representaciones del mismo $v$ · $\operatorname{Gen}S$ conjunto de todas las combinaciones lineales · la parte 2 dice que agregar un vector "nuevo" no rompe la independencia.

### E. Base (definición) y Teorema 10
$$\mathcal{B}\subseteq V\ \text{es base de } V\ (V\ne\{0\})\iff \mathcal{B}\ \text{es LI}\ \wedge\ \operatorname{Gen}\mathcal{B}=V$$
**Convención:** la única base de $\{0\}$ es $\varnothing$.
**Teorema 10:** todo espacio vectorial tiene al menos una base (su demostración no se ve en el curso).

**🔤 Diccionario:** $\mathcal{B}$ base (calligráfica) · LI = independencia · $\operatorname{Gen}\mathcal{B}=V$ = genera todo el espacio · base de $\{0\}$ = conjunto vacío, por convención.

### F. Bases estándar y dimensiones ya calculadas
| Espacio | Base estándar | $\dim$ |
|---|---|---|
| $\mathbb{R}^n$ | $\{e_1,\dots,e_n\}$ | $n$ |
| $P_n$ | $\{1,x,\dots,x^n\}$ | $n+1$ |
| $M_{mn}$ | $\{E_{ij}: 1\le i\le m,\ 1\le j\le n\}$ | $mn$ |
| $P$ (todos los polinomios) | $\{1,x,x^2,\dots\}$ | $\infty$ |
| $\{0\}$ | $\varnothing$ | $0$ |

**🔤 Diccionario:** $e_i$ vector con $1$ en la posición $i$ y $0$ en el resto · $E_{ij}$ matriz con $1$ en la entrada $(i,j)$ y $0$ en las demás · $M_{22}$ tiene $2\cdot2=4$ matrices $E_{ij}$ · $M_{34}$ tiene $3\cdot4=12$ · $P$ no admite base finita.

### G. Teorema 11 — unicidad de representación
$$\mathcal{B}=\{v_1,\dots,v_n\}\ \text{es base de } V\iff \forall v\in V\ \exists!\,(c_1,\dots,c_n):\ v=c_1v_1+\dots+c_nv_n$$

**🔤 Diccionario:** $\exists!$ = existe y es única · $(c_1,\dots,c_n)$ = coordenadas $[v]_{\mathcal{B}}$ · la unicidad es lo que permite definir coordenadas sin ambigüedad.

### H. Teorema 12 — intercambio de Steinitz
$$\text{Si } V=\operatorname{Gen}\{w_1,\dots,w_n\}\ \wedge\ S\subseteq V\ \wedge\ \vert S\vert>n\ \Rightarrow\ S\ \text{es LD}$$
Equivalentemente: **todo subconjunto LI de $V$ tiene a lo sumo $n$ elementos**.

**🔤 Diccionario:** $n$ = número de generadores de $V$ · $\vert S\vert$ = cardinalidad de $S$ · "a lo sumo $n$" = máximo $n$ vectores LI · es una cota **superior** para LI y **inferior** para generadores.

### I. Teorema 13 — la dimensión está bien definida
$$\text{Si } V \text{ tiene una base con } n \text{ elementos, toda base de } V \text{ tiene } n \text{ elementos}$$

$$\dim V=\vert\mathcal{B}\vert \quad \text{numero de elementos de cualquier base}$$

**🔤 Diccionario:** $\dim V$ dimensión · $n$ cardinal común de todas las bases · no depende de la base elegida · $\dim\{0\}=0$ · $\dim P=\infty$.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Orden en el Teorema 7.3:** la lista se puede reordenar. Si $v_1=0$, muévelo al final y pon al frente otro vector no nulo; el teorema exige $v_1\ne0$.
- **Caso 1 — Un solo vector:** $\{v\}$ es LD $\iff v=\vec0$. Un vector no nulo siempre es LI.
- **Caso 2 — Dos vectores:** LD $\iff$ uno es múltiplo del otro. Tres o más: hay que resolver el sistema.
- **Caso 3 — Atajo de dimensión:** si $\dim V=n$ y tengo $n$ vectores, **basta una** condición: LI $\Rightarrow$ base; generan $\Rightarrow$ base. ➕ (justificado por Teoremas 12 y 13)
- **Caso 4 — Refutar base:** dos vías. (a) son LD: exhibir coeficientes no triviales; (b) no generan: exhibir un vector concreto fuera del generado.
- **Caso 5 — "Contiene al cero":** LD inmediato, sin cuentas. También: contener un LD ⇒ LD; ser subconjunto de un LI ⇒ LI.
- **Caso 6 — "LI pero no genera":** típico con 2 vectores en $P_2$: alcanzan solo grado $\le1$, no $x^2$.
- **Caso 7 — Unicidad:** si hay dos representaciones distintas, el conjunto **no** es LI (y por tanto no es base).
- **Caso 8 — Cardinal vs. coeficientes:** la dimensión cuenta **vectores** de la base, no coordenadas ni entradas.
- **Caso 9 — $P$ completo:** la base estándar es infinita ⇒ espacio de dimensión infinita; no se cuenta con un número.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Decidir LI o LD
1. Plantear $\alpha_1v_1+\dots+\alpha_kv_k=0_V$.
2. Igualar coeficientes (polinomios), entradas (matrices) o valores (funciones).
3. Resolver el sistema homogéneo.
4. Solo la solución trivial ⇒ LI; alguna no trivial ⇒ LD.

**Plantilla** ($v_1=(1,0,0)$, $v_2=(0,1,0)$, $v_3=(2,3,0)$ en $\mathbb{R}^3$):
$$\alpha v_1+\beta v_2+\gamma v_3=(\alpha+2\gamma,\ \beta+3\gamma,\ 0)=(0,0,0)$$
$$\gamma=1\ \Rightarrow\ \alpha=-2,\ \beta=-3\ \text{es solución no trivial}\ \Rightarrow\ \text{LD}$$

### 4.2 Escribir un vector como combinación de los anteriores
1. Ordenar la lista y ubicar el primer vector no nulo.
2. Tomar $v_i$ con $i\ge2$ y plantear $v_i=c_1v_1+\dots+c_{i-1}v_{i-1}$.
3. Resolver para $c_1,\dots,c_{i-1}$.
4. Concluir $v_i\in\operatorname{Gen}\{v_1,\dots,v_{i-1}\}$.

**Plantilla** (misma lista anterior):
$$v_3=(2,3,0)=2(1,0,0)+3(0,1,0)=2v_1+3v_2$$
$$\Rightarrow\ v_3\in\operatorname{Gen}\{v_1,v_2\}\ \Rightarrow\ \text{la lista es LD por el Teorema 7.3}$$

### 4.3 Probar que $\mathcal{B}$ es base (las 2 condiciones)
1. Verificar LI: plantear $\sum c_iv_i=0_V$ y mostrar $c_i=0$.
2. Verificar que genera: dado un elemento genérico, despejar los coeficientes.
3. Concluir base y leer su dimensión.

**Plantilla** ($\mathcal{B}=\{1+x,\ -1+x,\ x^2\}$ en $P_2$):
$$\alpha(1+x)+\beta(-1+x)+\gamma x^2=(\alpha-\beta)+(\alpha+\beta)x+\gamma x^2=0$$
$$\alpha-\beta=0,\quad \alpha+\beta=0,\quad \gamma=0\ \Rightarrow\ \alpha=\beta=\gamma=0\ \Rightarrow\ \text{LI}$$
$$a_0+a_1x+a_2x^2:\quad \gamma=a_2,\ \ \alpha+\beta=a_1,\ \ \alpha-\beta=a_0$$
$$\alpha=\frac{a_0+a_1}{2},\quad \beta=\frac{a_1-a_0}{2}\ \Rightarrow\ \text{genera } P_2$$
$$\Rightarrow\ \mathcal{B}\ \text{es base de } P_2,\qquad \dim P_2=3$$

### 4.4 Refutar que es base
1. Intentar LI: si aparece una combinación nula con coeficientes no triviales ⇒ LD, no es base.
2. Si es LI, intentar generar un elemento concreto: si no se puede ⇒ no genera, no es base.
3. Cerrar con un contraejemplo explícito.

**Plantilla** ($S_1=\{1+x,\ -1+x,\ 2x\}$ y $S_2=\{1+x,\ -1+x\}$ en $P_2$):
$$(1+x)+(-1+x)-(2x)=0\quad\text{con coeficientes }(1,1,-1)\ne(0,0,0)\ \Rightarrow\ S_1\ \text{es LD}$$
$$\alpha(1+x)+\beta(-1+x)=(\alpha-\beta)+(\alpha+\beta)x\ \text{tiene grado}\le1\ \Rightarrow\ x^2\notin\operatorname{Gen}S_2$$
$$\Rightarrow\ S_1\ \text{no es base por ser LD},\qquad S_2\ \text{no es base porque no genera}$$

### 4.5 Usar Steinitz para acotar vectores
1. Contar los generadores $n$ de $V$.
2. Contar los vectores del conjunto candidato $S$.
3. Si $\vert S\vert>n$ ⇒ $S$ es LD (no puede ser base).
4. Corolario: en $\dim n$, $n$ vectores LI ya son base.

**Plantilla** ($V=\mathbb{R}^2=\operatorname{Gen}\{(1,0),(0,1)\}$, $n=2$; $S=\{(1,0),(0,1),(1,1)\}$):
$$\vert S\vert=3>2=n\ \Rightarrow\ S\ \text{es LD}$$
$$(1,1)=(1,0)+(0,1)\quad\text{verifico el contraejemplo}$$

### 4.6 Probar que al agregar un vector fuera del generado sigue LI (Teorema 9.2)
1. Suponer $\alpha_1v_1+\dots+\alpha_nv_n+\gamma v=0$ con $v\notin\operatorname{Gen}S$.
2. Si $\gamma\ne0$, despejar $v$ como combinación de $S$ ⇒ contradicción.
3. Entonces $\gamma=0$ y, como $S$ es LI, $\alpha_i=0$.
4. Concluir que $S\cup\{v\}$ es LI.

**Plantilla** ($S=\{(1,0,0),(0,1,0)\}$ en $\mathbb{R}^3$, $v=(0,0,1)$):
$$\gamma\ne0\ \Rightarrow\ v=-\frac{\alpha_1}{\gamma}v_1-\frac{\alpha_2}{\gamma}v_2\in\operatorname{Gen}S\quad\text{contradiccion}$$
$$\gamma=0\ \Rightarrow\ \alpha_1v_1+\alpha_2v_2=0\ \Rightarrow\ \alpha_1=\alpha_2=0\ \Rightarrow\ S\cup\{v\}\ \text{es LI}$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Identifiqué si me piden decidir, probar o refutar?
- [ ] ¿Para LI/LD resolví el sistema homogéneo y no solo "miré"?
- [ ] ¿En el Teorema 7.3 reordené para que $v_1\ne0$?
- [ ] ¿Para base comprobé LI **y** que genera?
- [ ] ¿Si refuto, di coeficientes o un vector concreto fuera del generado?
- [ ] ¿Usé Steinitz para no calcular de más cuando $\vert S\vert>n$?
- [ ] ¿Conté los elementos de la base y no los coeficientes?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
