# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 29/10/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261029_ESPACIO_NULO_Y_CARACTERIZACIONES_DE_LI.md` |
| **Tema principal** | Caracterizaciones de LI/LD, teorema $n\le m$, espacio nulo y solución general $p+N(A)$ |
| **Fecha base** | 29/10/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261029` + teoría estándar (Grossman cap. 2) |
| **Cómo citarla** | «📘 Cheatsheet `261029_ESPACIO_NULO_Y_CARACTERIZACIONES_DE_LI` §2.E» |
| **Notación** | $v_1,\dots,v_n\in\mathbb{R}^m$ · $A$ matriz $m\times n$ · $N(A)$ espacio nulo · $p$ solución particular · $\alpha_i$ coeficientes · pivote/columna pivote |
| **No repite** | definición de Gen y enlace con $AX=B$ → `261027`; subespacio, base, coordenadas y dimensión → `261103` |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿Es LI/LD, o es el conjunto solución de un sistema?**
- LI/LD → §2.A–§2.C · §4.1, §4.2.
- Conjunto solución $Ax=b$ / $Ax=0$ → espacio nulo → §2.E, §2.F · §4.4, §4.5.

**Paso 1 — ¿Qué pide exactamente?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "¿Son LI?" | Sistema homogéneo + pivotes | $A\alpha=0$ solo trivial | §2.A · §4.1 |
| "¿$n$ vectores en $\mathbb{R}^m$ pueden ser LI?" | Comparar $n$ con $m$ | LI $\Rightarrow n\le m$ | §2.B · §3 Caso 1 |
| "¿Son LD?" | Buscar combinación no trivial | algún $v_i$ es CL de los otros | §2.C · §4.2 |
| "¿La representación es única?" | Usar que el conjunto es LI | dos representaciones ⇒ coeficientes iguales | §2.D · §4.3 |
| "Halle el espacio nulo" | Resolver $Ax=0$ | $N(A)=\{x: Ax=0\}$ | §2.E · §4.4 |
| "¿$x\in N(A)$?" | Multiplicar | calcular $Ax$ y ver si da $0$ | §2.E · §4.4 |
| "Halle todas las soluciones de $Ax=b$" | Particular + nulo | $S=p+N(A)$ | §2.F · §4.5 |
| "¿Es subespacio?" | 2 cerraduras | 🔗 `261103` §2.B | — |

**Frases literales del profe → método**
- *"Solo tiene una solución trivial"* → caracterización de LI.
- *"Tiene $n$ columnas pivote"* → LI en términos de pivotes.
- *"Si $n$ es mayor que $m$, no pueden ser LI"* → teorema $n\le m$.
- *"Al menos un vector es combinación lineal de los otros"* → caracterización de LD.
- *"El espacio nulo son todos los $x$ tales que $Ax=0$"* → definición.
- *"Es igual a la solución particular más el espacio nulo"* → solución general.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Caracterizaciones de LI
Para $v_1,\dots,v_n\in\mathbb{R}^m$ con $A$ la matriz de columnas $v_i$, son equivalentes:
1. $\{v_1,\dots,v_n\}$ es LI.
2. $\alpha_1v_1+\dots+\alpha_nv_n=0\Rightarrow\alpha_1=\dots=\alpha_n=0$.
3. $A\alpha=0$ tiene **solo** la solución trivial.
4. $A$ tiene **$n$ columnas pivote**.
5. Si $A$ es cuadrada: $\det A\neq0$.

**🔤 Diccionario:** $A$ matriz $m\times n$ de columnas $v_i$ · $\alpha$ vector de coeficientes · columna pivote = columna con el primer $1$ de una fila escalonada.

### B. Teorema $n\le m$
$$\{v_1,\dots,v_n\}\subseteq\mathbb{R}^m \text{ LI}\;\Rightarrow\; n\le m$$
Contrapositiva: $n>m\Rightarrow$ el conjunto es LD.

**🔤 Diccionario:** $n$ número de vectores · $m$ número de componentes (filas) · no puede haber más vectores independientes que componentes · en $\mathbb{R}^3$ a lo sumo $3$ vectores LI.

### C. Caracterización de LD

| Afirmación | Condición |
|---|---|
| Un solo vector: LD | $\iff v=0$ |
| Dos o más vectores: LD | $\iff$ algún $v_i$ es CL de los demás |
| Ordenados: LD | $\iff$ algún $v_i$ con $i\ge2$ es CL de los anteriores |
| Contiene al $0$ | $\Rightarrow$ LD |
| Contiene un subconjunto LD | $\Rightarrow$ LD |
| Subconjunto de un LI | $\Rightarrow$ LI |

**🔤 Diccionario:** "algún $v_i$" = **al menos uno**, no todos · CL = combinación lineal.

### D. Unicidad de la representación
Si $\{v_1,\dots,v_n\}$ es LI, cada $v\in\operatorname{Gen}\{v_1,\dots,v_n\}$ se escribe de forma **única**:
$$v=\sum_{i=1}^{n}\alpha_iv_i=\sum_{i=1}^{n}\beta_iv_i\;\Rightarrow\;\alpha_i=\beta_i\ \ \forall i$$
**🔤 Diccionario:** $\alpha_i,\beta_i$ dos representaciones · la unicidad falla si el conjunto es LD.

### E. Espacio nulo
$$N(A)=\big\{x\in\mathbb{R}^n : Ax=0\big\}$$
- Es **subespacio** de $\mathbb{R}^n$: $x_1,x_2\in N(A)\Rightarrow A(x_1+x_2)=0$; $\;A(cx_1)=0$.
- Las columnas de $A$ son LI $\iff N(A)=\{0\}$.

**🔤 Diccionario:** $N(A)$ núcleo o espacio nulo · $0$ siempre está en $N(A)$ · $N(A)=\{0\}$ se llama nulo trivial.

### F. Solución general de $Ax=b$
Si $p$ es **una** solución de $Ax=b$, entonces
$$S=\big\{x : Ax=b\big\}=p+N(A)=\big\{p+n : n\in N(A)\big\}$$
**🔤 Diccionario:** $p$ solución particular · $N(A)$ soluciones del homogéneo · si $b\neq0$, $S$ **no** es subespacio (no contiene al $0$).

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — LI y tamaño:** LI $\Rightarrow n\le m$. Con $n>m$ se responde LD sin calcular.
- **Caso 1 — No confundir "alguno" con "todos":** LD pide que **al menos uno** sea CL de los otros.
- **Caso 2 — Vector cero:** cualquier conjunto con el $0$ es LD.
- **Caso 3 — Hereda:** subconjunto de LI es LI; superconjunto de LD es LD.
- **Caso 4 — Unicidad:** solo con conjuntos LI; con LD hay infinitas representaciones.
- **Caso 5 — Nulo trivial:** $N(A)=\{0\}\iff$ columnas de $A$ LI.
- **Caso 6 — Solución no homogénea:** $S=p+N(A)$ no es subespacio si $b\neq0$.
- **Caso 7 — Geometría:** 2 vectores no nulos LD $\iff$ misma recta por el origen; 3 en $\mathbb{R}^3$ LD $\iff$ mismo plano por el origen.
- **Caso 8 — Para refutar subespacio:** basta un contraejemplo (falla una cerradura o $0\notin$).

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Decidir LI
1. Formar $A$ con los vectores como columnas.
2. Si es cuadrada, calcular $\det A$.
3. Si es rectangular, escalonar y contar columnas pivote.
4. $n$ pivotes ⇔ LI.

**Plantilla** ($(1,2,3)$, $(0,1,4)$, $(5,6,0)$):
$$\det\begin{pmatrix}1&0&5\\2&1&6\\3&4&0\end{pmatrix}=1(0-24)-0+5(8-3)=-24+25=1\neq0$$
LI.

### 4.2 Decidir LD exhibiendo la combinación
1. Buscar si un vector es múltiplo o combinación de los otros.
2. Exhibir los coeficientes no triviales.

**Plantilla** ($(1,2)$ y $(3,6)$):
$$(3,6)=3(1,2)\;\Rightarrow\;3(1,2)-1(3,6)=(0,0)$$
coeficientes $(3,-1)$ no todos nulos ⇒ LD.

### 4.3 Probar unicidad
1. Suponer dos representaciones.
2. Restar y usar que el conjunto es LI.
3. Concluir igualdad de coeficientes.

**Plantilla** ($\{v_1,v_2\}$ LI, $v=\alpha_1v_1+\alpha_2v_2=\beta_1v_1+\beta_2v_2$):
$$(\alpha_1-\beta_1)v_1+(\alpha_2-\beta_2)v_2=0\;\Rightarrow\;\alpha_1=\beta_1,\ \alpha_2=\beta_2$$

### 4.4 Calcular el espacio nulo
1. Plantear $Ax=0$.
2. Escalonar.
3. Despejar las variables básicas en función de las libres.
4. El resultado es $N(A)$.

**Plantilla** ($A=\begin{pmatrix}2&-1\\-4&2\end{pmatrix}$):
$$2x-y=0\;\Rightarrow\;y=2x$$
$$N(A)=\Big\{t(1,2)\ :\ t\in\mathbb{R}\Big\}$$
Verificación: $A\binom{1}{2}=\binom{2-2}{-4+4}=\binom{0}{0}$.

### 4.5 Solución general de $Ax=b$
1. Hallar una solución particular $p$.
2. Hallar $N(A)$.
3. Escribir $S=p+N(A)$.

**Plantilla** (misma $A$, $b=(3,-6)$):
$$p=\binom{0}{-3}:\quad A p=\binom{3}{-6}$$
$$S=\binom{0}{-3}+t\binom{1}{2}=\binom{t}{-3+2t}$$
Verificación: $2t-(-3+2t)=3$ y $-4t+2(-3+2t)=-6$.

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Comparé $n$ con $m$ antes de calcular?
- [ ] ¿Conté las columnas pivote (no las filas)?
- [ ] ¿Verifiqué si el conjunto contiene al $0$?
- [ ] ¿Para unicidad usé que el conjunto es LI?
- [ ] ¿$N(A)$ lo expresé con variables libres?
- [ ] ¿La solución general quedó como $p+N(A)$?
- [ ] ¿Recordé que $p+N(A)$ no es subespacio si $b\neq0$?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
