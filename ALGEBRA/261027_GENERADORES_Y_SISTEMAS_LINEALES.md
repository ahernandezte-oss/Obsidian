# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 27/10/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261027_GENERADORES_Y_SISTEMAS_LINEALES.md` |
| **Tema principal** | Espacio generado y su enlace con $AX=B$; independencia lineal (enfoque de esta clase) |
| **Fecha base** | 27/10/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261027` + teoría estándar (Grossman cap. 2) |
| **Cómo citarla** | «📘 Cheatsheet `261027_GENERADORES_Y_SISTEMAS_LINEALES` §2.B» |
| **Notación** | $v_1,\dots,v_k$ generadores · $\alpha_i$ escalares · $\operatorname{Gen}\{\dots\}$ espacio generado · $A$ matriz de columnas $v_i$ · $b$ vector de términos · LD/LI |
| **Complementa** | `261103_ESPACIOS_VECTORIALES` tiene el desarrollo **completo** de Gen, LI/LD, base y dimensión; aquí **no se repite**: solo el puente con sistemas y la lectura geométrica |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿Me preguntan si un vector pertenece, o si un conjunto es LI/LD?**
- "¿$b$ está en el generado?" → resolver $AX=b$ → §2.B · §4.1.
- "¿Qué genera este conjunto?" → contar direcciones independientes → §2.A · §4.2.
- "¿Son LI o LD?" → sistema homogéneo → §2.D · §4.4.

**Paso 1 — ¿Qué pide exactamente?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "¿$b\in\operatorname{Gen}\{v_1,\dots,v_k\}$?" | Resolver el sistema | $b\in\operatorname{Gen}\iff AX=b$ tiene solución | §2.B · §4.1 |
| "¿Generan todo $\mathbb{R}^n$?" | Matriz cuadrada invertible | $\det A\neq0$ ⇒ $\operatorname{Gen}=\mathbb{R}^n$ | §2.B · §4.2 |
| "¿Qué genera?" (recta, plano o todo) | Contar vectores LI | 1 ⇒ recta · 2 LI ⇒ plano · $n$ LI ⇒ todo | §2.A · §4.2 |
| "Reduzca el conjunto generador" | Eliminar un vector que es combinación | teorema de reducción | §2.C · §4.3 |
| "¿Son LI o LD?" | Sistema homogéneo $A\alpha=0$ | $\det A\neq0$ ⇒ LI | §2.D · §4.4 |
| "Dos vectores: ¿son LD?" | Múltiplo / ángulo | LD $\iff$ uno es múltiplo $\iff\theta\in\{0,\pi\}$ | §2.D · §4.4 |
| "¿$\operatorname{Gen}$ es subespacio?" | Verificar cerraduras | $u+v$ y $\alpha u$ siguen en Gen | §2.E |

**Frases literales del profe → método**
- *"El espacio generado son todas las combinaciones lineales"* → definición.
- *"Ver si ese sistema tiene solución"* → pertenencia al generado es consistencia.
- *"Si es consistente para cualquier $B$, el generado es todo $\mathbb{R}^m$"* → lectura de la invertibilidad.
- *"Si uno es combinación lineal de los otros, el generador permanece igual"* → reducción.
- *"No se puede sacar el generado de un generado"* → solo combinaciones de un conjunto **finito**.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Espacio generado
$$\operatorname{Gen}\{v_1,\dots,v_k\}=\Big\{\alpha_1v_1+\dots+\alpha_kv_k\ :\ \alpha_i\in\mathbb{R}\Big\}$$
**🔤 Diccionario:** $v_i$ generadores · $\alpha_i$ escalares · siempre contiene al $0$ (todos $\alpha_i=0$) y a cada $v_i$ ($\alpha_i=1$, resto $0$) · nunca es vacío.

**Lectura geométrica:** $\operatorname{Gen}\{v\}$ = múltiplos de $v$ (recta) · dos vectores no múltiplos = plano · $\operatorname{Gen}\{e_1,\dots,e_n\}=\mathbb{R}^n$ · $\operatorname{Gen}\{e_1,e_3\}$ en $\mathbb{R}^3$ = plano $xz$.

### B. Enlace con sistemas $AX=B$
Con $A$ la matriz cuyas **columnas** son $v_1,\dots,v_k$:
$$b\in\operatorname{Gen}\{v_1,\dots,v_k\}\iff AX=b \text{ es consistente}$$
- $A$ cuadrada con $\det A\neq0$ ⇒ solución única para todo $b$ ⇒ $\operatorname{Gen}=\mathbb{R}^n$.
- $A$ no invertible ⇒ puede haber **infinitas** o **ninguna** solución: hay que escalonar y mirar la consistencia.

**🔤 Diccionario:** $A$ matriz de columnas $v_i$ · $X$ vector de coeficientes $\alpha_i$ · $b$ vector consultado · "consistente" = tiene al menos una solución.

### C. Reducción del conjunto generador
$$\text{si } v_i \text{ es combinación lineal del resto}\;\Rightarrow\;\operatorname{Gen}\{v_1,\dots,v_k\}=\operatorname{Gen}\{\dots\text{ sin }v_i\}$$
**Prueba (doble inclusión):** $\supseteq$ es inmediata; para $\subseteq$ se escribe $v_i=\sum_{j\neq i}c_jv_j$ y se sustituye dentro de una combinación arbitraria. 🔗 desarrollo completo en `261103` §2.E.

**🔤 Diccionario:** "combinación lineal del resto" = existen $c_j$ con $v_i=\sum_{j\neq i}c_jv_j$ · quitar ese vector no cambia el conjunto generado.

### D. Independencia lineal (definición)
$$\text{LD: }\exists\,\alpha_i \text{ no todos cero con } \alpha_1v_1+\dots+\alpha_kv_k=0$$
$$\text{LI: } \alpha_1v_1+\dots+\alpha_kv_k=0 \Rightarrow \alpha_1=\dots=\alpha_k=0$$
**Criterio matricial:** con $A$ de columnas $v_i$,
- $A$ cuadrada: $\det A\neq0\Rightarrow$ LI; $\det A=0\Rightarrow$ LD.
- $A$ rectangular: escalonar; si queda columna sin pivote ⇒ LD.

**🔤 Diccionario:** $\alpha_i$ coeficientes · "no trivial" = algún $\alpha_i\neq0$ · para dos vectores: LD $\iff$ uno es múltiplo del otro $\iff$ ángulo $0$ o $\pi$. 🔗 desarrollo en `261103` §2.F.

### E. El generado es subespacio
$$u,v\in\operatorname{Gen}\Rightarrow u+v\in\operatorname{Gen},\qquad \alpha u\in\operatorname{Gen}$$
**🔤 Diccionario:** $u,v$ combinaciones lineales de los $v_i$ · sumar o escalar solo cambia los coeficientes, no la forma.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Nunca vacío:** $\operatorname{Gen}$ contiene al $0$ y a cada generador por construcción.
- **Caso 1 — Pertenecer = sistema consistente:** no se decide "mirando", se resuelve $AX=b$.
- **Caso 2 — Un solo vector:** $\operatorname{Gen}\{v\}$ = recta (múltiplos de $v$).
- **Caso 3 — Dos vectores:** si uno es múltiplo del otro ⇒ recta; si no ⇒ plano.
- **Caso 4 — En $\mathbb{R}^n$:** $n$ vectores LI ⇒ generan todo; menos de $n$ ⇒ no.
- **Caso 5 — $\det=0$ no descarta la pertenencia:** el sistema puede tener infinitas soluciones (sí pertenece) o ninguna (no pertenece).
- **Caso 6 — Reducción:** solo se elimina un vector que sea combinación de los **otros**.
- **Caso 7 — Gen de un Gen:** no se define; solo combinaciones de un conjunto finito.
- **Caso 8 — Homogéneo:** siempre tiene la solución trivial; LD ⟺ hay solución no trivial.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Pertenencia al generado
1. Armar $A$ con los generadores como columnas.
2. Plantear $AX=b$.
3. Resolver (inversa si $A$ cuadrada invertible; si no, escalonar).
4. Con solución ⇒ pertenece; sin solución ⇒ no pertenece.

**Plantilla** ($b=(2,3)$, generadores $(1,2)$ y $(3,5)$):
$$A=\begin{pmatrix}1&3\\2&5\end{pmatrix},\qquad \det A=5-6=-1\neq0$$
$$X=A^{-1}b\;\Rightarrow\;c_1=-1,\;c_2=1$$
$$(2,3)=-(1,2)+(3,5)\;\Rightarrow\;(2,3)\in\operatorname{Gen}$$

### 4.2 Decidir qué genera un conjunto
1. Contar los vectores.
2. Verificar independencia (determinante o pivotes).
3. Traducir: 1 ⇒ recta · 2 LI ⇒ plano · $n$ LI en $\mathbb{R}^n$ ⇒ todo.

**Plantilla:** $\{(1,2),(3,5)\}$, $\det=-1\neq0$ ⇒ dos direcciones independientes ⇒ $\operatorname{Gen}=\mathbb{R}^2$.

### 4.3 Reducir el conjunto generador
1. Ver si algún vector es combinación de los otros.
2. Eliminarlo.
3. Repetir hasta que ninguno sea combinación.

**Plantilla:** $\{(1,2),(2,4)\}$: $(2,4)=2(1,2)$ ⇒
$$\operatorname{Gen}\{(1,2),(2,4)\}=\operatorname{Gen}\{(1,2)\}\ \text{una recta}$$

### 4.4 Decidir LI o LD
1. Escribir $A\alpha=0$ con columnas los vectores.
2. Si $A$ es cuadrada, calcular $\det A$.
3. $\det A\neq0$ ⇒ LI; $\det A=0$ ⇒ LD (escalonar para exhibir la combinación).

**Plantilla** ($(2,3,2)$, $(8,-6,5)$, $(-4,3,1)$):
$$\det\begin{pmatrix}2&8&-4\\3&-6&3\\2&5&1\end{pmatrix}=-126\neq0\;\Rightarrow\;\text{LI}$$

### 4.5 Dos vectores
1. Ver si uno es múltiplo del otro.
2. Si lo es ⇒ LD (y el ángulo es $0$ o $\pi$); si no ⇒ LI.

**Plantilla:** $(1,2)$ y $(2,4)$: $(2,4)=2(1,2)$ ⇒ LD, ángulo $0$.

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Traduje "pertenece al generado" a "el sistema tiene solución"?
- [ ] ¿Revisé si la matriz es cuadrada antes de usar determinante?
- [ ] ¿Con $\det=0$ escaloné para ver si hay infinitas o ninguna?
- [ ] ¿Conté bien las direcciones independientes?
- [ ] ¿Al reducir solo eliminé un vector que era combinación de los otros?
- [ ] ¿Recordé que el generado nunca es vacío?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
