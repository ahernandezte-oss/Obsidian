# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 19/11/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261119_MATRIZ_DE_TRANSICION_Y_NULIDAD.md` |
| **Tema principal** | Teo 19–22: independencia vía coordenadas, matriz de transición y su inversa, espacio nulo y nulidad |
| **Fecha base** | 19/11/2026 (Clase 14 · Nakos) |
| **Fuente** | PDF `Class_191126.pdf` (diapositivas Clase 14) + teoría estándar |
| **Cómo citarla** | «📘 Cheatsheet `261119_MATRIZ_DE_TRANSICION_Y_NULIDAD` §2.B» |
| **Notación** | $V$ de $\dim n$ · $\mathcal{B},\mathcal{B}'$ bases ordenadas · $[v]_{\mathcal{B}}$ coordenadas · $P$ matriz de transición · $\nu(A)$ espacio nulo · nulidad |
| **No repite** | vector de coordenadas y cambio de base por sistemas → `261117`; LI/LD, base y dimensión → `261110` |
| **🔔 Sincronización** | Copia espejo en `02_NOTAS_OBSIDIAN/ALGEBRA` + push por git el 2026-11-19 ✅ |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿La pregunta es de coordenadas o de matrices?**
- Base $\to$ base: construir $P$, aplicar $P$ o $P^{-1}$ → §2.B–§2.D.
- Matriz $A$ con incógnitas $x$: resolver $Ax=0$ → §2.E–§2.G.

**Paso 1 — Tabla de decisión**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "¿$p_1,p_2,p_3$ son LI en $P_2$?" | Teo 19: pasar a coordenadas | $\{[u_i]_{\mathcal{B}}\}$ LI en $\mathbb{R}^n$ | §2.A · §4.1 |
| "Matriz de transición de $\mathcal{B}$ a $\mathcal{B}'$" | Columnas $[v_i]_{\mathcal{B}'}$ | $P=([v_1]_{\mathcal{B}'}\ \cdots\ [v_n]_{\mathcal{B}'})$ | §2.B · §4.2 |
| "Transición de $\mathcal{B}'$ a $\mathcal{B}$" | Corolario 21 | $P^{-1}$ | §2.C · §4.3 |
| "Dado $[v]_{\mathcal{B}}$, halle $[v]_{\mathcal{B}'}$" | Multiplicar por $P$ | $[v]_{\mathcal{B}'}=P[v]_{\mathcal{B}}$ | §2.B · §4.3 |
| "Halle $\nu(A)$ y una base" | Resolver $Ax=0$ | forma paramétrica | §2.E · §4.4 |
| "¿Cuál es la nulidad de $A$?" | Teo 22 | nº de variables libres | §2.F · §4.4 |
| "¿$\nu(A)$ es subespacio de $\mathbb{R}^m$?" | Definición | $\nu(A)\subseteq\mathbb{R}^n$ | §2.E · §3 Caso 5 |
| "¿$Ax=0$ tiene solución no trivial?" | Nulidad $>0$ | variable libre $\Rightarrow$ no trivial | §2.F · §4.4 |
| "¿$P$ es invertible? ¿Es única?" | Teo 20 | $P$ invertible y única | §2.B |

**Frases de las diapositivas → método**
- *"$[v]_{\mathcal{B}}$ depende de la base y del orden de sus elementos"* → siempre base **ordenada**.
- *"La matriz $P$ del teorema 20 se llama matriz de transición"* → $P$ va de $\mathcal{B}$ a $\mathcal{B}'$.
- *"$P^{-1}$ es la matriz de transición de $\mathcal{B}'$ a $\mathcal{B}$"* → Corolario 21.
- *"La nulidad de $A$ es igual a la cantidad de variables libres de $Ax=0$"* → Teo 22.
- *"Los vectores de la combinación forman una base para $\nu(A)$"* → algoritmo de §4.4.
- *"Cada parámetro aparece en una componente distinta"* → los vectores de la base de $\nu(A)$ son LI.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Teorema 19 — independencia vía coordenadas
$$\{u_1,\dots,u_m\}\ \text{LI en } V\iff \{[u_1]_{\mathcal{B}},\dots,[u_m]_{\mathcal{B}}\}\ \text{LI en }\mathbb{R}^n$$
Demostración en una línea: como $[0]_{\mathcal{B}}=0$, el Teorema 18 da
$$c_1u_1+\dots+c_mu_m=0\iff c_1[u_1]_{\mathcal{B}}+\dots+c_m[u_m]_{\mathcal{B}}=0$$
Las dos ecuaciones tienen **las mismas soluciones**; luego la trivial es única en una si y solo si lo es en la otra.

**🔤 Diccionario:** $\mathcal{B}$ base de $V$ · $[u_i]_{\mathcal{B}}$ vector columna de coordenadas · "mismas soluciones" = mismos $c_1,\dots,c_m$ en ambos sistemas.

### B. Teorema 20 — matriz de transición
Sean $\mathcal{B}=\{v_1,\dots,v_n\}$ y $\mathcal{B}'=\{v'_1,\dots,v'_n\}$ bases de $V$, y sea
$$P=([v_1]_{\mathcal{B}'}\ \cdots\ [v_n]_{\mathcal{B}'})$$
Entonces $P$ es **invertible**, es **única** y para todo $v\in V$:
$$[v]_{\mathcal{B}'}=P\,[v]_{\mathcal{B}}$$
**🔤 Diccionario:** $P$ matriz de transición (o de cambio de base) **de $\mathcal{B}$ a $\mathcal{B}'$** · columnas = coordenadas de los vectores de la base vieja $\mathcal{B}$ en la base nueva $\mathcal{B}'$ · $P$ es $n\times n$.

### C. Corolario 21 — la transición inversa
$$\text{Si } P \text{ es la transición de } \mathcal{B} \text{ a } \mathcal{B}',\qquad P^{-1}\ \text{es la transición de } \mathcal{B}' \text{ a } \mathcal{B}$$
**🔤 Diccionario:** $P^{-1}$ existe porque $P$ es invertible (Teo 20) · no se calcula "a mano" si ya se conoce la otra dirección: es su inversa.

### D. Cómo construir $P$ (dos rutas equivalentes) ➕
1. **Por columnas:** resolver $n$ sistemas, uno por cada $v_i$, y escribir $[v_i]_{\mathcal{B}'}$.
2. **Por matrices de coordenadas estándar:** $P=M_{\mathcal{B}'}^{-1}M_{\mathcal{B}}$, donde $M_{\mathcal{B}}$ tiene por columnas las coordenadas estándar de los $v_i$ (y análogo $M_{\mathcal{B}'}$).
Si $\mathcal{B}$ es la base estándar, $M_{\mathcal{B}}=I$ y $P=M_{\mathcal{B}'}^{-1}$; si $\mathcal{B}'$ es la estándar, $P=M_{\mathcal{B}}$.

**🔤 Diccionario:** $M_{\mathcal{B}}$ matriz cuyas columnas son los $v_i$ en la base estándar · $M_{\mathcal{B}'}^{-1}$ inversa de la matriz análoga para $\mathcal{B}'$ · la ruta 2 es la versión matricial de la ruta 1.

### E. Espacio nulo y nulidad
$$\nu(A)=\{\,x\in\mathbb{R}^n:\ Ax=0\,\}$$
$\nu(A)$ es subespacio de $\mathbb{R}^n$ y su dimensión se llama **nulidad** de $A$:
$$\operatorname{nulidad}(A)=\dim\nu(A)$$
**🔤 Diccionario:** $A$ matriz $m\times n$ · $x$ vector columna de $n$ componentes · $\nu(A)$ espacio nulo (kernel) · nulidad = dimensión de $\nu(A)$ · $\nu(A)\neq\varnothing$ siempre ($x=0$).

### F. Teorema 22 — nulidad = variables libres
$$\operatorname{nulidad}(A)=\text{número de variables libres de } Ax=0$$
➕ Equivalente operativo: $\operatorname{nulidad}(A)=n-\#\text{pivotes}$ (las columnas no pivote son las variables libres).

**🔤 Diccionario:** variable libre = columna sin pivote en la forma escalonada · $n$ = número de columnas (incógnitas), **no** de filas · #pivotes = columnas pivote.

### G. Base del espacio nulo (forma paramétrica)
Si la solución general de $Ax=0$ es
$$x=t_1w_1+\dots+t_kw_k$$
entonces $\{w_1,\dots,w_k\}$ es base de $\nu(A)$ y $k=\operatorname{nulidad}(A)$.

**🔤 Diccionario:** $t_i$ parámetros (variables libres) · $w_i$ vectores que acompañan a cada parámetro · son LI porque cada $t_i$ aparece en una componente distinta.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Dirección de $P$:** $P$ va **de $\mathcal{B}$ a $\mathcal{B}'$** y sus columnas están en $\mathcal{B}'$. Al revés es $P^{-1}$ (Cor 21).
- **Caso 1 — Base estándar:** si $\mathcal{B}$ es la estándar, $[v]_{\mathcal{B}}=v$ y $P=M_{\mathcal{B}'}^{-1}$ (las columnas de $P$ son $[e_i]_{\mathcal{B}'}$).
- **Caso 2 — Orden:** cambiar el orden de una base cambia $P$ y las coordenadas.
- **Caso 3 — $P$ invertible:** siempre, porque sus columnas son coordenadas de una base; si al calcularla no es invertible, hay error.
- **Caso 4 — Verificación:** $P[v]_{\mathcal{B}}$ debe dar $[v]_{\mathcal{B}'}$ y $P^{-1}[v]_{\mathcal{B}'}$ debe devolver $[v]_{\mathcal{B}}$.
- **Caso 5 — $\nu(A)\subseteq\mathbb{R}^n$:** $n$ = columnas. Poner $\mathbb{R}^m$ es el error clásico.
- **Caso 6 — Nulidad 0:** $\nu(A)=\{0\}$; $Ax=0$ solo tiene la solución trivial y las columnas de $A$ son LI.
- **Caso 7 — Nulidad y consistencia:** nulidad $>0$ ⇒ hay soluciones no triviales de $Ax=0$; no dice nada de $Ax=b$ con $b\neq0$.
- **Caso 8 — #libres = $n-\#$pivotes:** nunca $m-\#$pivotes; $m$ son filas.
- **Caso 9 — Base de $\nu(A)$:** un vector por variable libre; el parámetro debe quedar "solo" en una componente para que sean LI.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Decidir LI con coordenadas (Teo 19)
1. Elegir una base de $V$ (usualmente la estándar).
2. Escribir $[u_i]_{\mathcal{B}}$ como columnas de una matriz.
3. Escalonar y contar pivotes.
4. $n$ pivotes (columnas) ⇒ LI; menos ⇒ LD. Volver a $V$ con Teo 19.

**Plantilla** ($p_1=1-x^2$, $p_2=-1+x$, $p_3=1+x+x^2$ en $P_2$):
$$[p_1]=(1,0,-1),\quad [p_2]=(-1,1,0),\quad [p_3]=(1,1,1)$$
$$\begin{pmatrix}1&-1&1\\0&1&1\\-1&0&1\end{pmatrix}\sim\begin{pmatrix}1&-1&1\\0&1&1\\0&0&3\end{pmatrix}\ \Rightarrow\ 3\ \text{pivotes}$$
$$\Rightarrow\ \text{coordenadas LI}\ \Rightarrow\ \{p_1,p_2,p_3\}\ \text{es LI y ademas base de } P_2$$

### 4.2 Construir la matriz de transición (Teo 20)
1. Escribir cada $v_i$ de $\mathcal{B}$ como combinación de los $v'_j$ de $\mathcal{B}'$.
2. Esos coeficientes, en columna, son la columna $i$ de $P$.
3. Verificar que $P$ sea invertible.
4. Comprobar con un $v$ conocido: $[v]_{\mathcal{B}'}=P[v]_{\mathcal{B}}$.

**Plantilla** ($\mathcal{B}$ estándar de $\mathbb{R}^2$, $\mathcal{B}'=\{(1,1),(-1,1)\}$):
$$e_1=(1,0)=\frac{1}{2}(1,1)-\frac{1}{2}(-1,1),\qquad e_2=(0,1)=\frac{1}{2}(1,1)+\frac{1}{2}(-1,1)$$
$$P=\begin{pmatrix}1/2&1/2\\-1/2&1/2\end{pmatrix}$$

### 4.3 Usar $P$ y $P^{-1}$ (Cor 21)
1. Identificar en qué dirección vas: $\mathcal{B}\to\mathcal{B}'$ usa $P$; $\mathcal{B}'\to\mathcal{B}$ usa $P^{-1}$.
2. Multiplicar el vector de coordenadas.
3. Verificar recomponiendo el vector en la base estándar.

**Plantilla** (misma $P$, $v=(4,-2)$):
$$[v]_{\mathcal{B}'}=P\begin{pmatrix}4\\-2\end{pmatrix}=\begin{pmatrix}1\\-3\end{pmatrix}$$
$$P^{-1}=\begin{pmatrix}1&-1\\1&1\end{pmatrix},\qquad P^{-1}\begin{pmatrix}1\\-3\end{pmatrix}=\begin{pmatrix}4\\-2\end{pmatrix}=[v]_{\mathcal{B}}$$
$$\text{Comprobación: }1(1,1)-3(-1,1)=(4,-2)$$

### 4.4 Base del espacio nulo y nulidad (Teo 22)
1. Escalonar $A$ y llevar $Ax=0$ a forma escalonada reducida.
2. Marcar columnas pivote y variables libres.
3. Despejar las variables pivote en función de las libres.
4. Escribir la solución general como combinación de los parámetros.
5. Los vectores que acompañan a cada parámetro son base de $\nu(A)$; su número es la nulidad.

**Plantilla** ($A$ de $4\times5$ con RREF dada):
$$\begin{pmatrix}1&0&4&0&1\\0&1&2&0&1\\0&0&0&1&0\\0&0&0&0&0\end{pmatrix},\qquad x_3=s,\ x_5=r$$
$$x=\begin{pmatrix}-4s-r\\-2s-r\\s\\0\\r\end{pmatrix}=r\begin{pmatrix}-1\\-1\\0\\0\\1\end{pmatrix}+s\begin{pmatrix}-4\\-2\\1\\0\\0\end{pmatrix}$$
$$\text{Base de }\nu(A)=\{(-1,-1,0,0,1),\ (-4,-2,1,0,0)\},\qquad \operatorname{nulidad}=2=5-3$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿La base está ordenada y anoté cuál es $\mathcal{B}$ y cuál $\mathcal{B}'$?
- [ ] ¿Las columnas de $P$ están en la base **nueva** $\mathcal{B}'$?
- [ ] ¿Verifiqué $P[v]_{\mathcal{B}}=[v]_{\mathcal{B}'}$?
- [ ] ¿Calculé $P^{-1}$ (o la usé) para la dirección contraria?
- [ ] ¿$\nu(A)$ lo puse en $\mathbb{R}^n$ (columnas) y no en $\mathbb{R}^m$?
- [ ] ¿Conté variables libres = $n-$pivotes?
- [ ] ¿La base de $\nu(A)$ tiene tantos vectores como la nulidad?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
