# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 05/11/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261105_ESPACIOS_VECTORIALES_ABSTRACTOS.md` |
| **Tema principal** | Espacios vectoriales abstractos: polinomios, matrices y funciones; Gen como menor subespacio; LI/LD fuera de $\mathbb{R}^n$ |
| **Fecha base** | 05/11/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261105` + teoría estándar (Grossman cap. 4–5) |
| **Cómo citarla** | «📘 Cheatsheet `261105_ESPACIOS_VECTORIALES_ABSTRACTOS` §2.C» |
| **Notación** | $V$ espacio vectorial · $P_n$ polinomios de grado $\le n$ · $M_{mn}$ matrices · $\mathcal{B}$ base · $\operatorname{Gen}S$ · LI/LD · $0_V$ cero del espacio |
| **No repite** | definiciones en $\mathbb{R}^n$, base, coordenadas y dimensión → `261103`; caracterizaciones de LI y espacio nulo → `261029`; Gen ↔ $AX=B$ → `261027` |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿En qué espacio estoy trabajando?**
- Polinomios, matrices o funciones → **igualar coeficientes / entradas / usar identidades** → §2.C–§2.D.
- $\mathbb{R}^n$ → usar matriz, pivotes y determinante (🔗 `261029`).

**Paso 1 — ¿Qué pide exactamente?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "¿$V$ es espacio vectorial?" | Verificar los 10 axiomas | A1–A5 y M1–M5 | §2.A · §3 Caso 1 |
| "¿$W$ es subespacio?" | 2 cerraduras | 🔗 `261103` §2.B | — |
| "¿$p\in\operatorname{Gen}\{p_1,p_2\}$?" (polinomios) | Igualar coeficientes | $p=\alpha p_1+\beta p_2$ | §2.C · §4.1 |
| "¿$A\in\operatorname{Gen}\{A_1,A_2\}$?" (matrices) | Igualar entradas | $A=\alpha A_1+\beta A_2$ | §2.C · §4.1 |
| "¿Son LD?" (funciones) | Identidad o evaluar puntos | $\alpha f+\beta g=0$ ∀$x$ | §2.D · §4.2 |
| "¿$\mathcal{B}$ es base de $V$?" | LI + genera | ambas condiciones | §2.E · §4.3 |
| "Demuestre que $\operatorname{Gen}S$ es el menor subespacio" | Doble inclusión | $\operatorname{Gen}S\subseteq W$ | §2.F · §4.4 |
| "Reduzca el generador" | Quitar un vector CL | 🔗 `261103` §2.E | §2.G |
| "¿Es un anillo o un campo?" | Conceptual | el producto es **por escalar** | §2.A · §3 Caso 0 |

**Frases literales del profe → método**
- *"No es la misma definición del anillo"* → en un E.V. no hay producto vector por vector.
- *"Las reglas del juego"* → los 10 axiomas se aceptan, no se demuestran.
- *"Si estamos en los polinomios, este $0$ es el polinomio cero"* → el cero depende del espacio.
- *"Ese se llama el menor subespacio que contiene a $S$"* → $\operatorname{Gen}S$ es el más pequeño.
- *"Puede que sean LI pero no generen todo"* → LI no basta para ser base.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Espacio vectorial abstracto (10 axiomas)

| Suma | Producto por escalar |
|---|---|
| $(A_1)$ $u+v\in V$ | $(M_1)$ $\alpha u\in V$ |
| $(A_2)$ $u+v=v+u$ | $(M_2)$ $\alpha(u+v)=\alpha u+\alpha v$ |
| $(A_3)$ $(u+v)+w=u+(v+w)$ | $(M_3)$ $(\alpha+\beta)u=\alpha u+\beta u$ |
| $(A_4)$ $\exists\,0_V$ neutro | $(M_4)$ $\alpha(\beta u)=(\alpha\beta)u$ |
| $(A_5)$ $\exists\,(-u)$ opuesto | $(M_5)$ $1u=u$ |

**🔤 Diccionario:** $\alpha,\beta\in\mathbb{R}$ escalares · $0_V$ cero del espacio (polinomio nulo, matriz cero, función nula) · **no** es anillo: el producto es escalar × vector, no vector × vector.

**Ejemplos:** $\mathbb{R}^n$ · $M_{mn}$ · $D_n$ diagonales · $P_n$ · $P$ todos los polinomios · $C(\mathbb{R})$ continuas · $C^{1}(\mathbb{R})$ diferenciables · $F(\mathbb{R})$ funciones.

### B. Subespacio (🔗 `261103` §2.B)
$W\subseteq V$ no vacío es subespacio $\iff$ cerrado bajo suma y bajo producto por escalar.

**🔤 Diccionario:** se hereda todo lo demás de $V$ · basta exhibir $0_V\in W$ para la no vacuidad.

### C. Pertenencia al generado en espacios abstractos
$$p\in\operatorname{Gen}\{p_1,p_2\}\iff \exists\,\alpha,\beta\in\mathbb{R}:\ p=\alpha p_1+\beta p_2$$
- **Polinomios:** expandir e **igualar coeficientes** de cada potencia.
- **Matrices:** **igualar entrada por entrada**.
- **Funciones:** usar **identidades** o evaluar en puntos convenientes.

**🔤 Diccionario:** $\alpha,\beta$ escalares reales · si al igualar aparece una contradicción, no pertenece.

### D. LI/LD en espacios abstractos
$$\alpha_1v_1+\dots+\alpha_nv_n=0_V\ \Rightarrow\ \alpha_i=0\ \forall i \;(\text{LI})$$
$$\text{LD}\iff \exists\,\alpha_i \text{ no todos cero con } \sum\alpha_iv_i=0_V$$
**🔤 Diccionario:** el $0_V$ es el cero del espacio · polinomios ⇒ sistema de coeficientes · matrices ⇒ sistema de entradas · funciones ⇒ identidad o puntos.

### E. Base en un espacio abstracto
$$\mathcal{B}\text{ base de }V\iff \mathcal{B}\text{ es LI y }\operatorname{Gen}\mathcal{B}=V$$
Bases estándar: $P_n\to\{1,x,\dots,x^n\}$ · $M_{mn}\to\{E_{ij}\}$ · $D_n\to\{E_{ii}\}$.

**🔤 Diccionario:** LI + genera · LI sin generar ⇒ **no** es base · $E_{ij}$ = matriz con $1$ en $(i,j)$ y $0$ en el resto.

### F. El generado es el menor subespacio
$$\operatorname{Gen}S \text{ es subespacio de } V,\qquad S\subseteq W \Rightarrow \operatorname{Gen}S\subseteq W$$
**🔤 Diccionario:** $W$ cualquier subespacio que contenga a $S$ · el generado es el "más pequeño" en el sentido de la inclusión.

### G. Reducción del generador (🔗 `261103` §2.E)
Si $v_i$ es combinación lineal de los demás, $\operatorname{Gen}\{v_1,\dots,v_k\}=\operatorname{Gen}\{\dots\text{ sin }v_i\}$.

**🔤 Diccionario:** quitar un vector redundante no cambia el conjunto generado.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — E.V. no es anillo ni campo:** no existe producto vector × vector; solo escalar × vector.
- **Caso 1 — Los 10 axiomas son reglas:** no se demuestran, se verifican.
- **Caso 2 — El cero cambia de forma:** polinomio nulo, matriz cero, función nula.
- **Caso 3 — "Vector" es genérico:** matriz, polinomio o función son vectores del espacio.
- **Caso 4 — Polinomios:** igualar coeficientes; cuidado con el grado (en $P_n$ hay $n+1$ coeficientes).
- **Caso 5 — LI no implica base:** falta verificar que genera.
- **Caso 6 — Refutar "genera":** exhibir un elemento concreto que no se alcanza.
- **Caso 7 — Funciones LD:** usar identidades trigonométricas (por ejemplo $\cos^{2}x=\tfrac12+\tfrac12\cos 2x$).
- **Caso 8 — Subespacio en abstracto:** mismas 2 cerraduras que en $\mathbb{R}^n$.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Pertenencia al generado
1. Plantear $p=\alpha p_1+\beta p_2$ (o la combinación que corresponda).
2. Expandir y agrupar por potencias (o entradas).
3. Igualar coeficientes y resolver.
4. Con solución ⇒ pertenece.

**Plantilla** ($p=-1+x^{2}$, $p_1=1+x+x^{3}$, $p_2=-x-x^{2}-x^{3}$):
$$\alpha(1+x+x^{3})+\beta(-x-x^{2}-x^{3})=-1+x^{2}$$
$$\alpha+(\alpha-\beta)x-\beta x^{2}+(\alpha-\beta)x^{3}=-1+0x+1x^{2}+0x^{3}$$
$$\alpha=-1,\quad \alpha-\beta=0,\quad -\beta=1$$
$$\Rightarrow\ \alpha=\beta=-1\ \text{es consistente}\ \Rightarrow\ p\in\operatorname{Gen}$$

### 4.2 Decidir LI o LD
1. Plantear $\alpha_1v_1+\dots+\alpha_nv_n=0_V$.
2. Comparar coeficientes, entradas o valores de la función.
3. Solo la solución trivial ⇒ LI.

**Plantilla** (matrices $A=\begin{pmatrix}1&0\\0&0\end{pmatrix}$, $B=\begin{pmatrix}0&1\\0&0\end{pmatrix}$, $C=\begin{pmatrix}1&1\\0&0\end{pmatrix}$):
$$C=A+B\;\Rightarrow\;A+B-C=0$$
coeficientes $(1,1,-1)$ no todos nulos ⇒ LD.

### 4.3 Decidir si es base
1. Verificar LI.
2. Verificar que genera **todo** el espacio.
3. Si falla una, no es base.

**Plantilla** ($\{1+x+x^{3},\,-x-x^{2}-x^{3}\}$ en $P_3$):
- LI: sí (no son múltiplos).
- Genera: $\alpha=a_0$, $\beta=-a_2$ y deben cumplirse $a_1=a_0+a_2$ y $a_3=a_1$.
- Contraejemplo: $p=1+2x+3x^{2}$ exige $2=1+3=4$, falso.
$$\Rightarrow\ \text{LI pero no genera}\ \Rightarrow\ \text{no es base de }P_3$$

### 4.4 Probar que $\operatorname{Gen}S$ es el menor subespacio
1. Demostrar que $\operatorname{Gen}S$ es subespacio (cerraduras).
2. Tomar un subespacio $W$ con $S\subseteq W$.
3. Ver que cada combinación lineal de $S$ está en $W$.

**Plantilla** ($S\subseteq W$, $W$ subespacio, $v=\sum\alpha_iv_i$ con $v_i\in S$):
$$v_i\in S\subseteq W\;\Rightarrow\;\alpha_iv_i\in W\quad\text{y}\quad\sum\alpha_iv_i\in W$$
$$\Rightarrow\ \operatorname{Gen}S\subseteq W$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Identifiqué de qué espacio es cada $0$?
- [ ] ¿Igualé coeficientes/entradas y no solo "miré"?
- [ ] ¿Revisé si estar en $P_n$ limita el grado?
- [ ] ¿Para base comprobé LI **y** que genera?
- [ ] ¿Si no genera, di un contraejemplo concreto?
- [ ] ¿Usé identidades para funciones?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
