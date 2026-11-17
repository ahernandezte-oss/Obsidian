# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 17/11/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261117_COORDENADAS_Y_CAMBIO_DE_BASE.md` |
| **Tema principal** | Teoremas 14–19: cotas de dimensión, base con una sola condición, ampliar o reducir a base, subespacios, vector de coordenadas, cambio de base y traslado a $\mathbb{R}^n$ |
| **Fecha base** | 17/11/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261117` + apuntes (Teoremas 14–19) + Grossman cap. 4–5 |
| **Cómo citarla** | «📘 Cheatsheet `261117_COORDENADAS_Y_CAMBIO_DE_BASE` §2.G» |
| **Notación** | $V$ espacio vectorial de $\dim n$ · $\mathcal{B}$ base ordenada · $[v]_{\mathcal{B}}$ vector de coordenadas · $M_{mn}$ matrices · $P_n$ polinomios · $E_{ij}$ matriz unidad · $\dim V$ |
| **No repite** | definición de base, Teo 11 (unicidad), Teo 12–13 y LI/LD → `261110`; subespacio → `261103` |
| **🔔 Sincronización** | Copia espejo en `02_NOTAS_OBSIDIAN/ALGEBRA` + push por git el 2026-11-17 ✅ |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿Dónde trabajo?**
- En un espacio abstracto ($P_n$, $M_{mn}$, funciones) → puedo **pasarlo a $\mathbb{R}^n$** con coordenadas (Teo 18–19) → §4.6.
- En $\mathbb{R}^n$ → calcular directo con matriz, Gauss y determinante → §4.1–§4.4.

**Paso 1 — Tabla de decisión**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "Halle $[v]_{\mathcal{B}}$" | Resolver $\mathcal{B}c=v$ | $v=c_1b_1+\dots+c_nb_n$ | §2.F · §4.1 |
| "Con $[v]_{\mathcal{B}}$, halle $v$" | Combinar con la base | $v=\sum c_ib_i$ | §2.F · §4.2 |
| "Cambie de base $\mathcal{B}\to\mathcal{B}'$" | Resolver en $\mathcal{B}'$ o matriz | $[v]_{\mathcal{B}'}=M_{\mathcal{B}'}^{-1}M_{\mathcal{B}}\,[v]_{\mathcal{B}}$ | §2.G · §4.3 |
| "¿Cuántos vectores LI caben?" | Teo 14 y 12 | LI $\Rightarrow m\le n$ | §2.B · §4.4 |
| "$n$ vectores en $\dim n$: ¿es base?" | Teo 15 | LI o genera ⇒ base | §2.C · §4.4 |
| "Complete $S$ a una base" | Teo 16.1 | $m<n$ y LI ⇒ ampliar | §2.D · §4.5 |
| "Reduzca el generador a base" | Teo 16.2 | generador ⇒ contiene base | §2.D · §4.5 |
| "$W\subseteq V$ y $\dim W=n$" | Teo 17 | $\dim W=n\iff W=V$ | §2.E · §3 Caso 5 |
| "LI en $M_{mn}$ o en $P_n$" | Teo 19: pasar a coordenadas | $\{[u_i]_{\mathcal{B}}\}$ LI en $\mathbb{R}^n$ | §2.I · §4.6 |
| "CL en $M_{mn}$ o en $P_n$" | Teo 18: pasar a coordenadas | $[u]_{\mathcal{B}}=\sum c_i[u_i]_{\mathcal{B}}$ | §2.H · §4.6 |
| "¿Cuál es $\dim V$?" | Base estándar | tabla §2.A | §2.A |

**Frases literales del profe → método**
- *"Todas las bases deben tener el mismo número de elementos, por eso la dimensión está bien definida"* → Teo 13; no hay dos dimensiones para un mismo $V$.
- *"Si estoy en $\mathbb{R}^3$ y tengo cinco vectores, son LD"* → Teo 12/14: más vectores que la dimensión no puede ser LI.
- *"Por eso tiene que estar ordenada"* → la base es **ordenada**; cambiar el orden cambia $[v]_{\mathcal{B}}$.
- *"En la base estándar me queda el mismo vector"* → $[a]_{\mathcal{E}}=a$.
- *"Olvídese de eso y llévelo al vector de coordenadas"* → Teo 19 para LI en espacios abstractos.
- *"Yo mando mi espacio vectorial a un $\mathbb{R}^n$"* → la correspondencia $v\mapsto[v]_{\mathcal{B}}$ es biyectiva.
- *"Si son LI, entonces es base"* → Teo 15: con $n$ vectores basta una condición.
- *"Puedo ampliar una base"* / *"contiene una base"* → Teo 16.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Dimensiones ya calculadas
| Espacio | Base estándar | Dimensión |
|---|---|---|
| $\mathbb{R}^n$ | $\{e_1,\dots,e_n\}$ | $n$ |
| $P_n$ | $\{1,x,\dots,x^n\}$ | $n+1$ |
| $M_{mn}$ | $\{E_{ij}: 1\le i\le m,\ 1\le j\le n\}$ | $mn$ |
| $P$ (todos los polinomios) | $\{1,x,x^2,\dots\}$ | $\infty$ |
| $F(\mathbb{R})$ (todas las funciones) | no tiene base finita | $\infty$ |
| $\{0\}$ | $\varnothing$ | $0$ |

**🔤 Diccionario:** $P_n$ polinomios de grado $\le n$ (tiene $n+1$ coeficientes) · $M_{mn}$ matrices de tamaño $m\times n$ · $E_{ij}$ matriz con $1$ en $(i,j)$ y $0$ en el resto · $\dim\{0\}=0$ por convención.

### B. Teorema 14 — cotas de dimensión
$$\text{Si } S\subseteq V,\ \dim V=n,\ \vert S\vert=m:\qquad S\ \text{LI}\ \Rightarrow\ m\le n$$
$$\operatorname{Gen}S=V\ \Rightarrow\ m\ge n$$
**🔤 Diccionario:** $m\le n$ cota **superior** para conjuntos LI · $m\ge n$ cota **inferior** para generadores · si $m>n$, $S$ es LD (Teo 12).

### C. Teorema 15 — una sola condición basta
$$\text{Si } S\subseteq V,\ \dim V=n,\ \vert S\vert=n:$$
$$S\ \text{es LI}\ \Rightarrow\ S\ \text{es base};\qquad \operatorname{Gen}S=V\ \Rightarrow\ S\ \text{es base}$$
**🔤 Diccionario:** "basta una condición" = no hay que probar LI y genera a la vez · exige **conocer** $\dim V$ · es la versión corta de la definición de base.

### D. Teorema 16 — ampliar y reducir
1. Si $S$ es LI y $m<n$, entonces $S$ **se puede ampliar** a una base de $V$.
2. Si $\operatorname{Gen}S=V$, entonces $S$ **contiene** una base de $V$.

**🔤 Diccionario:** ampliar = agregar vectores fuera del generado (Teo 9.2) hasta llegar a $n$ · reducir = quitar vectores que son combinación lineal de los anteriores (Teo 6) · no es un algoritmo automático: hay que verificar cada agregado o quitado.

### E. Teorema 17 — subespacios y dimensión
$$W\ \text{subespacio de } V,\ \dim V=n\ \Rightarrow\ \dim W\le n$$
$$\dim W=n\iff W=V$$
**🔤 Diccionario:** $W$ subespacio (contiene al $0$ y es cerrado) · si $\dim W=n$ no es "parecido" a $V$: es **el mismo** $V$ · si $W\subsetneq V$ entonces $\dim W\le n-1$.

### F. Vector de coordenadas
$$\mathcal{B}=\{b_1,\dots,b_n\}\ \text{base ordenada},\qquad v=c_1b_1+\dots+c_nb_n$$
$$[v]_{\mathcal{B}}=\begin{pmatrix}c_1\\ \vdots\\ c_n\end{pmatrix}$$
Por el Teo 11 los $c_i$ son **únicos**. Si $\mathcal{E}$ es la base estándar, $[a]_{\mathcal{E}}=a$.

**🔤 Diccionario:** $[v]_{\mathcal{B}}$ vector columna de coeficientes · "ordenada" = el orden de $b_1,\dots,b_n$ fija el orden de las componentes · la correspondencia $v\mapsto[v]_{\mathcal{B}}$ es biyectiva entre $V$ y $\mathbb{R}^n$ ➕.

### G. Cambio de base (sistema y forma matricial)
Para pasar de $\mathcal{B}$ a $\mathcal{B}'$, si $M_{\mathcal{B}}$ tiene por columnas las coordenadas estándar de los $b_i$:
$$[v]_{\mathcal{B}'}=M_{\mathcal{B}'}^{-1}M_{\mathcal{B}}\,[v]_{\mathcal{B}},\qquad P=M_{\mathcal{B}'}^{-1}M_{\mathcal{B}}$$
➕ Forma matricial (la clase la resolvió con Gauss sobre el sistema).

**🔤 Diccionario:** $P$ matriz de cambio de base, invertible porque $\mathcal{B},\mathcal{B}'$ son bases · $M_{\mathcal{B}'}^{-1}M_{\mathcal{B}}$ también se obtiene como $([b_1]_{\mathcal{B}'}\ \cdots\ [b_n]_{\mathcal{B}'})$ · si $v$ está en la base estándar, $[v]_{\mathcal{B}'}=M_{\mathcal{B}'}^{-1}v$.

### H. Teorema 18 — la combinación lineal se conserva
$$u\in\operatorname{Gen}\{u_1,\dots,u_m\}\iff [u]_{\mathcal{B}}\in\operatorname{Gen}\{[u_1]_{\mathcal{B}},\dots,[u_m]_{\mathcal{B}}\}$$
$$u=\sum_{i=1}^{m}c_iu_i\iff [u]_{\mathcal{B}}=\sum_{i=1}^{m}c_i[u_i]_{\mathcal{B}}$$
**🔤 Diccionario:** mismos escalares $c_i$ en ambos lados · permite resolver pertenencia al generado en $\mathbb{R}^n$ en vez de en $V$.

### I. Teorema 19 — la independencia se conserva
$$\{u_1,\dots,u_m\}\ \text{es LI en } V\iff \{[u_1]_{\mathcal{B}},\dots,[u_m]_{\mathcal{B}}\}\ \text{es LI en }\mathbb{R}^n$$
**🔤 Diccionario:** $\mathcal{B}$ base de $V$ de dimensión finita · sirve para matrices ($\dim mn$) y polinomios ($\dim n+1$) · se elige $\mathcal{B}$ = base estándar para calcular rápido.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Base ordenada:** cambiar el orden de los vectores cambia las coordenadas. La base es un conjunto **con orden fijo**.
- **Caso 1 — Base estándar:** $[a]_{\mathcal{E}}=a$; por eso las coordenadas "coinciden" con el vector solo en esa base.
- **Caso 2 — Vector vs. coordenadas:** $v$ no cambia al cambiar de base; cambia su **representación** $[v]_{\mathcal{B}}$.
- **Caso 3 — Atajo Teo 15:** en $\dim n$ con $n$ vectores, verificar **solo LI** (o **solo** genera) ya prueba que es base.
- **Caso 4 — Cotas Teo 14:** $10$ vectores en $\mathbb{R}^k$: si son LI, $k\ge10$; si generan, $k\le10$; si son base, $k=10$.
- **Caso 5 — Teo 17:** $\dim W=n$ con $W\subseteq V$ obliga a $W=V$; no sirve para "casi todo el espacio".
- **Caso 6 — $\{0\}$:** base $\varnothing$, $\dim=0$; un subespacio propio tiene dimensión a lo sumo $n-1$.
- **Caso 7 — Teo 16:** el ampliado debe seguir siendo LI (probar cada agregado); el reducido debe seguir generando.
- **Caso 8 — Teo 18–19:** CL y LI se conservan al pasar a coordenadas; los escalares son los mismos.
- **Caso 9 — Unicidad:** el sistema con la matriz de la base tiene solución **única**; si "no sale", hay error de cuentas (no es que no exista).

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Hallar $[v]_{\mathcal{B}}$
1. Escribir $v=c_1b_1+\dots+c_nb_n$.
2. Formar el sistema (o la matriz aumentada con columnas $b_i$).
3. Resolver por Gauss (o por $M_{\mathcal{B}}^{-1}v$).
4. Leer $[v]_{\mathcal{B}}=(c_1,\dots,c_n)^T$ y verificar.

**Plantilla** ($\mathcal{B}=\{(1,1,0),(0,1,1),(1,0,1)\}$, $v=(3,2,1)$ en $\mathbb{R}^3$):
$$c_1(1,1,0)+c_2(0,1,1)+c_3(1,0,1)=(c_1+c_3,\ c_1+c_2,\ c_2+c_3)=(3,2,1)$$
$$c_1+c_3=3,\quad c_1+c_2=2,\quad c_2+c_3=1$$
$$\Rightarrow\ c_1=2,\quad c_2=0,\quad c_3=1\ \Rightarrow\ [v]_{\mathcal{B}}=(2,0,1)^T$$

### 4.2 Reconstruir $v$ desde $[v]_{\mathcal{B}}$
1. Leer $[v]_{\mathcal{B}}=(c_1,\dots,c_n)^T$.
2. Multiplicar cada $c_i$ por su $b_i$.
3. Sumar y verificar en la base estándar.

**Plantilla** (misma base, $[w]_{\mathcal{B}}=(6,-3,2)^T$):
$$w=6(1,1,0)-3(0,1,1)+2(1,0,1)$$
$$w=(6,6,0)+(0,-3,-3)+(2,0,2)=(8,3,-1)$$

### 4.3 Cambio de base
1. Escribir la matriz $M_{\mathcal{B}'}$ con las coordenadas estándar de los vectores de $\mathcal{B}'$.
2. Calcular $[v]_{\mathcal{B}'}=M_{\mathcal{B}'}^{-1}M_{\mathcal{B}}\,[v]_{\mathcal{B}}$ (si $v$ ya está en la base estándar, $M_{\mathcal{B}}=I$).
3. Verificar recomponiendo $v$ con las nuevas coordenadas.

**Plantilla** ($v=(6,3)$, $\mathcal{B}'=\{(3,2),(1,1)\}$):
$$M_{\mathcal{B}'}=\begin{pmatrix}3&1\\2&1\end{pmatrix},\qquad M_{\mathcal{B}'}^{-1}=\begin{pmatrix}1&-1\\-2&3\end{pmatrix}$$
$$[v]_{\mathcal{B}'}=\begin{pmatrix}1&-1\\-2&3\end{pmatrix}\begin{pmatrix}6\\3\end{pmatrix}=\begin{pmatrix}3\\-3\end{pmatrix}$$
$$\text{Verificación: }3(3,2)-3(1,1)=(6,3)$$

### 4.4 Decidir base con una sola condición (Teo 15) y usar cotas
1. Contar $\vert S\vert=m$ y comparar con $\dim V=n$.
2. Si $m<n$: no puede ser base (Teo 14).
3. Si $m=n$: probar LI (o que genera) y concluir base (Teo 15).
4. Si $m>n$: es LD (Teo 12).

**Plantilla** ($B=\{(1,1,1),(1,1,0),(1,0,0)\}\subseteq\mathbb{R}^3$):
$$\det\begin{pmatrix}1&1&1\\1&1&0\\1&0&0\end{pmatrix}=-1\ne0\ \Rightarrow\ B\ \text{es LI}$$
$$\vert B\vert=3=\dim\mathbb{R}^3\ \Rightarrow\ B\ \text{es base por el Teo 15}$$

### 4.5 Ampliar un LI a base (Teo 16.1) y reducir un generador (Teo 16.2)
1. Verificar que $S$ es LI y contar $m<n$.
2. Agregar vectores fuera de $\operatorname{Gen}S$ (usar Teo 9.2) hasta tener $n$.
3. Eliminar los que resulten combinación lineal de los anteriores.
4. Cerrar con Teo 15: $n$ vectores LI en $\dim n$ ⇒ base.

**Plantilla** ($S=\{x^2-1,\ 3-2x\}\subseteq P_3$, $\dim P_3=4$):
$$S\ \text{es LI por tener grados distintos},\quad m=2<4\ \Rightarrow\ \text{se puede ampliar}$$
$$\text{Agrego }1\text{ y }x^3:\quad \mathcal{B}=\{x^2-1,\ 3-2x,\ 1,\ x^3\}$$
$$\det\begin{pmatrix}-1&3&1&0\\0&-2&0&0\\1&0&0&0\\0&0&0&1\end{pmatrix}=2\ne0\ \Rightarrow\ \mathcal{B}\ \text{es LI}$$
$$\Rightarrow\ \mathcal{B}\ \text{es base de } P_3\ (\text{Teo 15})$$
En cambio, si agrego $x$: $x=-\tfrac12(3-2x)+\tfrac32(1)$, es redundante y se elimina.

### 4.6 Pasar LI o CL a coordenadas (Teo 18–19)
1. Elegir una base de $V$ (usualmente la estándar).
2. Calcular $[u_i]_{\mathcal{B}}$ de cada vector.
3. Decidir LI o CL en $\mathbb{R}^n$ con matriz, determinante o Gauss.
4. Volver a $V$ con Teo 18–19.

**Plantilla** ($S=\{1+x,\ 1-x,\ x^2\}\subseteq P_2$, base $\mathcal{E}=\{1,x,x^2\}$):
$$[1+x]_{\mathcal{E}}=(1,1,0),\quad [1-x]_{\mathcal{E}}=(1,-1,0),\quad [x^2]_{\mathcal{E}}=(0,0,1)$$
$$\det\begin{pmatrix}1&1&0\\1&-1&0\\0&0&1\end{pmatrix}=-2\ne0\ \Rightarrow\ \text{coordenadas LI}$$
$$\Rightarrow\ S\ \text{es LI en } P_2\ \Rightarrow\ S\ \text{es base por Teo 19 y Teo 15}$$
Pertenencia: $p=1+3x+2x^2$ tiene $[p]_{\mathcal{E}}=(1,3,2)$ y
$$(1,3,2)=2(1,1,0)-1(1,-1,0)+2(0,0,1)\ \Rightarrow\ p=2(1+x)-(1-x)+2x^2$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Anoté el **orden** de la base antes de calcular coordenadas?
- [ ] ¿Comprobé el resultado recomponiendo el vector?
- [ ] ¿Usé la base estándar para pasar de abstracto a $\mathbb{R}^n$?
- [ ] ¿Conté $m$ y $n$ antes de decidir base (Teo 14–15)?
- [ ] ¿Si amplío, verifiqué que lo agregado siga siendo LI?
- [ ] ¿Si reduzco, verifiqué que el generador no cambie?
- [ ] ¿Revisé que $\dim W=n$ signifique $W=V$ (Teo 17)?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
