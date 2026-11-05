# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 13/10/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261013_DETERMINANTES_Y_MATRICES_ELEMENTALES.md` |
| **Tema principal** | Determinantes, matrices elementales e inversa (repaso parcial 1) |
| **Fecha base** | 13/10/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261013` (revisión de parcial) + teoría estándar (Grossman cap. 2–3) |
| **Cómo citarla** | «📘 Cheatsheet `261013_DETERMINANTES_Y_MATRICES_ELEMENTALES` §2.C» |
| **Notación** | $A,B$ matrices $n\times n$ · $a_{ij}$ entradas · $\det A=\lvert A\rvert$ · $C_{ij}$ cofactor · $M_{ij}$ menor · $A^{-1}$ inversa · $A^{\top}$ traspuesta · $I_n$ identidad · $E$ matriz elemental |
| **Complementa** | `261103_ESPACIOS_VECTORIALES` — **sin repetir temas**: aquí no van subespacios, base, coordenadas ni dimensión |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿La pregunta es de calcular, de decidir o de demostrar?**
- *Calcular* → determinante / inversa / $A$ a partir de elementales → §4.1, §4.3, §4.5.
- *Decidir* → ¿es invertible?, ¿para qué valores de $k$?, discutir sistema → §4.2, §4.4.
- *Demostrar* → propiedad de determinante o por inducción → §4.6.

**Paso 1 — ¿Qué pide exactamente?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "Calcule $\det A$" | Expandir por la fila o columna con **más ceros** | $\det A=\sum_j a_{ij}C_{ij}$ | §2.A · §4.1 |
| "Use la regla de Sarrus" | Solo si es **3×3** | producto de 3 diagonales | §2.A · §3 Caso 1 |
| "¿Es invertible?" | Mirar el determinante | $\det A\neq 0\iff A^{-1}$ existe | §2.C · §3 Caso 2 |
| "Halle $C_{ij}$ / cofactor $(i,j)$" | Quitar fila $i$, columna $j$ y aplicar signo | $C_{ij}=(-1)^{i+j}M_{ij}$ | §2.B · §3 Caso 6 |
| "Halle $A^{-1}$" | Gauss-Jordan $[A\mid I]\to[I\mid A^{-1}]$ | o $A^{-1}=\frac{1}{\det A}\operatorname{adj}A$ | §2.E · §4.3 |
| "¿Para qué $k$ no es invertible?" / "discuta según $k$" | $\det A=0$ o escalonar con parámetro | pivote nulo ⇒ condición sobre $k$ | §2.C, §2.F · §4.4 |
| "$E_3E_2E_1A=I$" / "exprese $A$" | Invertir el producto | $A=(E_k\cdots E_1)^{-1}=E_1^{-1}\cdots E_k^{-1}$ | §2.D · §4.5 |
| "Demuestre $\det(AB)=\det A\det B$" | Tres tipos de elemental + inducción | $\det E$ según el tipo | §2.D, §2.G · §4.6 |
| "Propiedades con $A^{\top}$, simétricas, $AB=AC$…" | Propiedades del determinante / álgebra | tabla §2.C | §3 Casos 4–10 |

**Frases literales del profe → método**
- *"Sarrus solamente se puede hacer para matrices 3×3"* → en 4×4 o más hay que expandir por cofactores.
- *"Si el determinante es diferente de cero… tiene solución única"* → discutir por el determinante.
- *"¿Para qué valores de $k$ la matriz no es invertible?"* → plantear $\det A=0$.
- *"El determinante de $AB$ es el producto de los determinantes"* → propiedad clave.
- *"Tengo que leer bien qué me están preguntando"* → cofactor $(2,3)$ no es el $(3,2)$.
- *"No era el objetivo reemplazar todos los valores"* → resolver en general, no caso por caso.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Determinante por cofactores
Para $A$ de $n\times n$, expandiendo por la **fila $i$**:
$$\det A=\sum_{j=1}^{n}a_{ij}C_{ij}$$
o por la **columna $j$**:
$$\det A=\sum_{i=1}^{n}a_{ij}C_{ij}$$
**Sarrus (solo 3×3):**
$$\det A=a_{11}a_{22}a_{33}+a_{12}a_{23}a_{31}+a_{13}a_{21}a_{32}-a_{13}a_{22}a_{31}-a_{11}a_{23}a_{32}-a_{12}a_{21}a_{33}$$

**🔤 Diccionario:** $a_{ij}$ entrada de la fila $i$, columna $j$ · $C_{ij}$ cofactor de esa posición · $M_{ij}$ menor (determinante que queda al quitar fila $i$ y columna $j$) · $n$ orden de la matriz.

### B. Menor y cofactor; matriz de cofactores y adjunta
$$M_{ij}=\det(\text{matriz sin fila }i\text{ ni columna }j),\qquad C_{ij}=(-1)^{i+j}M_{ij}$$
$$\operatorname{adj}(A)=\big(C_{ij}\big)^{\top}$$

**🔤 Diccionario:** $M_{ij}$ menor · $C_{ij}$ cofactor · $\operatorname{adj}(A)$ adjunta (traspuesta de la matriz de cofactores) · el signo $(-1)^{i+j}$ sigue un patrón de tablero de ajedrez.

### C. Propiedades del determinante

| Propiedad | Fórmula |
|---|---|
| Producto | $\det(AB)=\det A\,\det B$ |
| Traspuesta | $\det(A^{\top})=\det A$ |
| Inversa | $\det(A^{-1})=\dfrac{1}{\det A}$ |
| Escalar | $\det(cA)=c^{\,n}\det A$ (con $A$ de $n\times n$) |
| Identidad | $\det I_n=1$ |
| Fila repetida o proporcional | $\det A=0$ |
| Fila nula | $\det A=0$ |
| Intercambiar dos filas | cambia el signo |
| Sumar múltiplo de una fila a otra | no cambia |
| Triangular | producto de la diagonal |

**🔤 Diccionario:** $c$ escalar · $n$ orden · "proporcional" = una fila es múltiplo de otra · "triangular" = debajo (o arriba) de la diagonal todo es $0$.

### D. Matrices elementales (3 tipos) y su determinante

| Tipo | Operación sobre $I_n$ | $\det E$ | Efecto en $\det(EA)$ |
|---|---|---|---|
| Permutación $P_{ij}$ | intercambia filas $i$ y $j$ | $-1$ | cambia el signo |
| Eliminación $E_{ij}(k)$ | $R_i\to R_i+kR_j$ | $1$ | no cambia |
| Escalamiento $S_i(k)$ | $R_i\to kR_i$ ($k\neq 0$) | $k$ | multiplica por $k$ |

**🔤 Diccionario:** $E$ matriz elemental (una sola operación de fila aplicada a $I_n$) · $k$ escalar no nulo en el escalamiento · toda $E$ es invertible y $E^{-1}$ es del mismo tipo.

### E. Inversa
$$\big[A\mid I\big]\;\longrightarrow\;\big[I\mid A^{-1}\big]\qquad\text{Gauss-Jordan}$$
$$A^{-1}=\frac{1}{\det A}\,\operatorname{adj}(A)\qquad(\det A\neq 0)$$
**🔤 Diccionario:** $[A\mid I]$ matriz aumentada · $\operatorname{adj}(A)$ adjunta · la fórmula exige $\det A\neq 0$.

### F. Sistemas con parámetro (discusión)
Escalonar $[A\mid b]$ y leer los pivotes:
- Aparece una fila $[\,0\ \cdots\ 0\mid c\,]$ con $c\neq 0$ ⇒ **inconsistente**.
- Hay pivote en cada incógnita ⇒ **solución única**.
- Menos pivotes que incógnitas y sin fila inconsistente ⇒ **infinitas soluciones** (variables libres).

**🔤 Diccionario:** pivote = primer $1$ (o entrada no nula) de una fila escalonada · variable libre = columna sin pivote.

### G. Inducción (para demostrar propiedades)
1. **Base:** verificar el caso $n=2$ (o $n=1$).
2. **Hipótesis:** suponer cierto para $n-1$.
3. **Paso:** expandir por una fila/columna que deje el caso $n-1$ y aplicar la hipótesis.

**🔤 Diccionario:** $n$ orden de la matriz · "hipótesis de inducción" = el resultado ya vale para el orden anterior.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Solo cuadradas:** el determinante se define únicamente para matrices cuadradas.
- **Caso 1 — Sarrus 3×3:** vale solo para $3\times3$. En $4\times4$ o más se expande por cofactores; usarla en $4\times4$ es el error clásico.
- **Caso 2 — Invertibilidad:** $A$ invertible $\iff \det A\neq 0$. "No invertible" ⇒ plantear $\det A=0$.
- **Caso 3 — Filas dependientes:** si una fila es combinación lineal de las demás, $\det A=0$.
- **Caso 4 — Escalar:** $\det(cA)=c^{\,n}\det A$, **no** $c\det A$.
- **Caso 5 — Producto nulo:** $AB=0$ **no** implica $A=0$ ni $B=0$; pero $A^{\top}A=0$ sí implica $A=0$ (suma de cuadrados).
- **Caso 6 — Posición del cofactor:** $C_{ij}$ quita fila $i$ y columna $j$ y lleva signo $(-1)^{i+j}$; $C_{23}\neq C_{32}$.
- **Caso 7 — Cuadrado de suma:** $(A+B)^{2}=A^{2}+AB+BA+B^{2}$; solo es $A^{2}+2AB+B^{2}$ si $AB=BA$.
- **Caso 8 — Simétricas:** si $A$ y $B$ son simétricas, $AB$ es simétrica $\iff AB=BA$.
- **Caso 9 — Inversa de simétrica:** $A$ invertible y simétrica ⇒ $A^{-1}$ es simétrica.
- **Caso 10 — Cancelación:** si $A$ es invertible, $AB=AC\Rightarrow B=C$ (multiplicar a izquierda por $A^{-1}$).

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Calcular un determinante
1. Buscar la fila o columna con **más ceros** (o triangular la matriz).
2. Expandir por ella con $C_{ij}=(-1)^{i+j}M_{ij}$.
3. Sumar y simplificar.

**Plantilla** ($A=\begin{pmatrix}2&0&1\\1&3&0\\4&0&5\end{pmatrix}$, expandir por la columna 2):
$$\det A=3\cdot C_{22}=3\cdot(-1)^{2+2}\begin{vmatrix}2&1\\4&5\end{vmatrix}=3\cdot(10-4)=18$$

### 4.2 Decidir si es invertible
1. Calcular $\det A$.
2. Si $\det A\neq 0$ ⇒ invertible; si $\det A=0$ ⇒ no invertible.

**Plantilla:** $A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$, $\det A=4-6=-2\neq0$, luego $A$ es invertible.

### 4.3 Calcular la inversa (Gauss-Jordan)
1. Formar $[A\mid I_n]$.
2. Aplicar operaciones de fila hasta llegar a $[I_n\mid A^{-1}]$.
3. Leer $A^{-1}$ a la derecha.

**Plantilla** ($A=\begin{pmatrix}2&1\\5&3\end{pmatrix}$, $\det A=1$):
$$\big[A\mid I\big]=\begin{pmatrix}2&1&1&0\\5&3&0&1\end{pmatrix}\to\begin{pmatrix}1&0&3&-1\\0&1&-5&2\end{pmatrix}\Rightarrow A^{-1}=\begin{pmatrix}3&-1\\-5&2\end{pmatrix}$$

### 4.4 Discutir un sistema con parámetro
1. Escribir $[A\mid b]$ y escalonar sin fijar el parámetro.
2. Localizar los pivotes que dependen del parámetro.
3. Separar los casos: inconsistente / única / infinitas.

**Plantilla:**
$$x+y=1,\qquad x+ay=b$$
$$\det A=a-1$$
- $a\neq 1$: solución única (para cualquier $b$).
- $a=1,\ b=1$: infinitas soluciones (la segunda ecuación repite la primera).
- $a=1,\ b\neq 1$: inconsistente (queda $0=b-1\neq 0$).

### 4.5 Despejar $A$ de un producto de elementales
1. De $E_k\cdots E_1A=I$, invertir el producto.
2. Usar $(E_k\cdots E_1)^{-1}=E_1^{-1}\cdots E_k^{-1}$.
3. Calcular cada inversa elemental y multiplicar en ese orden.

**Plantilla** ($E_1{:}\ R_2\to R_2-2R_1$, $E_2{:}$ intercambio de filas; $E_2E_1A=I$):
$$A=E_1^{-1}E_2^{-1}=\begin{pmatrix}1&0\\2&1\end{pmatrix}\begin{pmatrix}0&1\\1&0\end{pmatrix}=\begin{pmatrix}0&1\\1&2\end{pmatrix}$$

### 4.6 Demostrar una propiedad del determinante
1. Verificar la base ($n=2$).
2. Suponer válido para $n-1$.
3. Expandir por una fila/columna y aplicar la hipótesis.

**Plantilla** (triangular inferior ⇒ $\det=$ producto de la diagonal, $n=2$):
$$\det\begin{pmatrix}t_{11}&0\\t_{21}&t_{22}\end{pmatrix}=t_{11}t_{22}-0\cdot t_{21}=t_{11}t_{22}$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿La matriz es cuadrada? (si no, no hay determinante)
- [ ] ¿Usé Sarrus solo en $3\times3$?
- [ ] ¿Elegí la fila/columna con más ceros?
- [ ] ¿Revisé el signo $(-1)^{i+j}$ de cada cofactor?
- [ ] ¿"No invertible" lo traduje a $\det A=0$?
- [ ] ¿En $\det(cA)$ usé $c^{n}$?
- [ ] ¿Leí bien la posición del cofactor pedido?
- [ ] ¿En sistemas con parámetro separé los tres casos?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
