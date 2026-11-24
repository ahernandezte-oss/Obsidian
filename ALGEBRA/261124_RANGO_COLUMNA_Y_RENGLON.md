# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 24/11/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261124_RANGO_COLUMNA_Y_RENGLON.md` |
| **Tema principal** | Teo 22–25 y 31: nulidad, espacio columna, espacio renglón, rango y teorema del rango |
| **Fecha base** | 24/11/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261124` + apuntes + diapositivas Clase 14 (Nakos) |
| **Cómo citarla** | «📘 Cheatsheet `261124_RANGO_COLUMNA_Y_RENGLON` §2.E» |
| **Notación** | $A$ de $m\times n$ · $\operatorname{Col}(A)\subseteq\mathbb{R}^m$ · $\operatorname{Ren}(A)\subseteq\mathbb{R}^n$ · $\nu(A)$ · rango · nulidad |
| **No repite** | vector de coordenadas y Teo 19 → `261117`/`261119`; nulidad por variables libres → `261119`; base y dimensión → `261110` |
| **🔔 Sincronización** | Copia espejo en `02_NOTAS_OBSIDIAN/ALGEBRA` + push por git el 2026-11-24 ✅ |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿Piden un espacio (Col/Ren) o resolver un sistema?**
- Sistema $Ax=b$ → consistencia y rango → §2.C, §2.G, §4.4.
- Base de un espacio → columnas pivote (Col) o renglones no nulos (Ren) → §4.1, §4.2.

**Paso 1 — Tabla de decisión**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "¿$Ax=b$ tiene solución?" | Teo 23 | $b\in\operatorname{Col}(A)$ | §2.C · §4.4 |
| "Base de $\operatorname{Col}(A)$" | Columnas pivote **de $A$** | $\{a_{p_1},\dots,a_{p_k}\}$ | §2.E · §4.1 |
| "Base de $\operatorname{Ren}(A)$" | Renglones no nulos de la escalonada | Teo 28 | §2.F · §4.2 |
| "Halle el rango de $A$" | Contar pivotes | $\operatorname{rango}=\dim\operatorname{Col}=\dim\operatorname{Ren}$ | §2.G · §4.3 |
| "Halle la nulidad de $A$" | Variables libres | Teo 22 | §2.A · §4.3 |
| "Verifique el teorema del rango" | Suma | $\operatorname{rango}+\operatorname{nulidad}=n$ | §2.H |
| "¿$A\sim B$ conserva $\operatorname{Col}$?" | No; sí conserva $\operatorname{Ren}$ | contraejemplo | §2.D · §3 Caso 1 |
| "¿Son LI en $P_2$ o $M_{22}$?" | Teo 19: coordenadas | $\{[u_i]_{\mathcal{B}}\}$ LI en $\mathbb{R}^n$ | §2.I · §4.5 |
| "¿Es base?" | LI + dimensión | Teo 15 | §4.5 |

**Frases literales del profe → método**
- *"El espacio columna es el generado por sus columnas"* → $\operatorname{Col}(A)=\operatorname{Gen}\{a_1,\dots,a_n\}\subseteq\mathbb{R}^m$.
- *"Tomamos las columnas pivote, pero las de la matriz original"* → nunca las de la escalonada.
- *"Las operaciones entre filas pueden cambiar el espacio de columnas"* → $A\sim B$ no implica $\operatorname{Col}(A)=\operatorname{Col}(B)$.
- *"El espacio renglón no cambia"* → Teo 26; su base son los renglones no nulos de la escalonada.
- *"Rango más nulidad me da el número de columnas"* → Teo 31.
- *"La nulidad es la cantidad de variables libres"* → Teo 22.
- *"Una base no es única"* → escalar los vectores de una base da otra base.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Nulidad (repaso de la clase pasada)
$$\nu(A)=\{x\in\mathbb{R}^n: Ax=0\},\qquad \operatorname{nulidad}(A)=\dim\nu(A)=\#\text{variables libres}$$
Base de $\nu(A)$: llevar $Ax=0$ a RREF, despejar las pivote y escribir $x=t_1w_1+\dots+t_kw_k$.

**🔤 Diccionario:** $t_i$ parámetros (variables libres) · $w_i$ vectores de la base · la base **no es única** (se puede escalar).

### B. Espacio columna y espacio renglón
$$\operatorname{Col}(A)=\operatorname{Gen}\{a_1,\dots,a_n\}\subseteq\mathbb{R}^m,\qquad \operatorname{Ren}(A)=\operatorname{Gen}\{r_1,\dots,r_m\}\subseteq\mathbb{R}^n$$
**🔤 Diccionario:** $a_i$ columnas de $A$ (vectores de $\mathbb{R}^m$) · $r_i$ renglones de $A$ (vectores de $\mathbb{R}^n$) · $\operatorname{Col}$ vive en $\mathbb{R}^m$ y $\operatorname{Ren}$ en $\mathbb{R}^n$.

### C. Teorema 23 — consistencia y espacio columna
$$Ax=b\ \text{es consistente}\iff b\in\operatorname{Col}(A)$$
**🔤 Diccionario:** consistente = tiene al menos una solución · $Ax=x_1a_1+\dots+x_na_n$: $b$ debe ser combinación lineal de las columnas.

### D. Teorema 24 — relaciones de dependencia
$$\text{Si } A\sim B:\quad c_1a_1+\dots+c_na_n=0\iff c_1b_1+\dots+c_nb_n=0$$
**🔤 Diccionario:** $A\sim B$ equivalentes por renglones · las columnas guardan **las mismas** relaciones de dependencia · $\operatorname{Col}(A)\neq\operatorname{Col}(B)$ en general.

### E. Teorema 25 — base del espacio columna
$$\text{Las columnas pivote de } A \text{ forman una base de } \operatorname{Col}(A)$$
**🔤 Diccionario:** columnas pivote = posiciones de los pivotes en la escalonada, tomadas **en $A$** · advertencia: no se usan las columnas de la escalonada.

### F. Teorema 26, 27 y 28 — espacio renglón
$$\text{Si } A\sim B\ \Rightarrow\ \operatorname{Ren}(A)=\operatorname{Ren}(B)$$
Los renglones no nulos de una forma escalonada son LI y forman una base de $\operatorname{Ren}(A)$.

**🔤 Diccionario:** las operaciones elementales son combinaciones lineales de renglones, por eso $\operatorname{Ren}$ no cambia · la base del renglón sí se lee de la escalonada.

### G. Rango
$$\operatorname{rango}(A)=\dim\operatorname{Col}(A)=\dim\operatorname{Ren}(A)=\#\text{columnas pivote}$$
$$\operatorname{rango}(A)=\operatorname{rango}(A^T)\le\min(m,n)$$
**🔤 Diccionario:** $m$ filas · $n$ columnas · el rango nunca supera el número de filas ni el de columnas.

### H. Teorema 31 — teorema del rango
$$\operatorname{rango}(A)+\operatorname{nulidad}(A)=n\quad(\text{número de columnas})$$
**🔤 Diccionario:** $n$ columnas (incógnitas), no filas · los pivotes aportan al rango y las columnas no pivote a la nulidad.

### I. Teorema 19 (repaso) — LI vía coordenadas
$$\{u_1,\dots,u_m\}\ \text{LI en } V\iff \{[u_1]_{\mathcal{B}},\dots,[u_m]_{\mathcal{B}}\}\ \text{LI en }\mathbb{R}^n$$
**🔤 Diccionario:** se elige una base $\mathcal{B}$ (usualmente la estándar) y se decide LI con determinante o con pivotes.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Col vs. Ren:** $\operatorname{Col}(A)$ usa columnas y vive en $\mathbb{R}^m$; $\operatorname{Ren}(A)$ usa renglones y vive en $\mathbb{R}^n$.
- **Caso 1 — $A\sim B$:** conserva $\operatorname{Ren}$ (Teo 26) pero **no** $\operatorname{Col}$. Ejemplo: $\begin{pmatrix}1&1\\1&1\end{pmatrix}\sim\begin{pmatrix}1&1\\0&0\end{pmatrix}$ con $\operatorname{Col}$ distintos.
- **Caso 2 — Base de $\operatorname{Col}$:** identificar pivotes en la escalonada y tomar esas **mismas posiciones** en $A$.
- **Caso 3 — Base de $\operatorname{Ren}$:** leer los renglones no nulos de la escalonada.
- **Caso 4 — Rango:** contar pivotes; $\operatorname{rango}\le\min(m,n)$.
- **Caso 5 — Teo 31:** la suma usa $n$ (columnas). Si $A$ es $4\times6$ con rango $3$, nulidad $=6-3=3$.
- **Caso 6 — Nulidad 0:** $Ax=0$ solo trivial ⇔ columnas LI ⇔ rango $=n$ (Teo 34).
- **Caso 7 — Rango $=m$:** $Ax=b$ consistente para todo $b$ ⇔ $\operatorname{Col}(A)=\mathbb{R}^m$ (Teo 33).
- **Caso 8 — Base no única:** multiplicar por escalares no nulos o combinar preservando LI da otra base.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Base de $\operatorname{Col}(A)$ (Teo 25)
1. Escalonar $A$ y ubicar las columnas pivote.
2. Tomar esas **mismas columnas en $A$** (no en la escalonada).
3. Verificar que son LI; su número es el rango.

**Plantilla** ($A=\begin{pmatrix}1&2&0&1\\2&4&1&3\\3&6&1&4\end{pmatrix}$):
$$\begin{pmatrix}1&2&0&1\\2&4&1&3\\3&6&1&4\end{pmatrix}\sim\begin{pmatrix}1&2&0&1\\0&0&1&1\\0&0&0&0\end{pmatrix}$$
$$\text{Pivotes en las columnas }1,3\ \Rightarrow\ \text{base de }\operatorname{Col}(A)=\{(1,2,3),(0,1,1)\}$$

### 4.2 Base de $\operatorname{Ren}(A)$ (Teo 27–28)
1. Escalonar $A$.
2. Descartar los renglones nulos.
3. Los renglones no nulos son base de $\operatorname{Ren}(A)$.

**Plantilla** (misma $A$):
$$\text{Base de }\operatorname{Ren}(A)=\{(1,2,0,1),\ (0,0,1,1)\}$$

### 4.3 Rango y nulidad (Teo 22 y 31)
1. Escalonar y contar pivotes: ese es el rango.
2. Contar variables libres: esa es la nulidad.
3. Verificar $\operatorname{rango}+\operatorname{nulidad}=n$.

**Plantilla** (misma $A$ de $3\times4$):
$$\operatorname{rango}(A)=2,\qquad \operatorname{nulidad}(A)=4-2=2\ \checkmark$$
$$\nu(A)=\operatorname{Gen}\{(-2,1,0,0),\ (-1,0,-1,1)\}$$

### 4.4 Decidir consistencia (Teo 23 y Teo 32)
1. Escribir $b$ como combinación de las columnas.
2. Resolver; si hay solución, $b\in\operatorname{Col}(A)$.
3. Alternativa: comparar $\operatorname{rango}(A)$ con $\operatorname{rango}([A\mid b])$.

**Plantilla** (misma $A$, con $b=(1,2,4)$):
$$a(1,2,3)+c(0,1,1)=(1,2,4)\ \Rightarrow\ a=1,\ 2a+c=2,\ 3a+c=4$$
$$a=1,\ c=0\ \Rightarrow\ 3\neq4\ \Rightarrow\ b\notin\operatorname{Col}(A)\ \Rightarrow\ \text{inconsistente}$$

### 4.5 Decidir LI y si es base (Teo 19 + Teo 15)
1. Pasar cada vector a coordenadas en una base (estándar si se puede).
2. Formar la matriz por columnas y calcular determinante (o pivotes).
3. $\det\neq0$ (o $n$ pivotes) ⇒ LI; si además $\vert S\vert=\dim V$, es base.

**Plantilla** ($p_1=1+2x$, $p_2=x-x^2$, $p_3=2+x^2$ en $P_2$):
$$[p_1]=(1,2,0),\quad [p_2]=(0,1,-1),\quad [p_3]=(2,0,1)$$
$$\det\begin{pmatrix}1&0&2\\2&1&0\\0&-1&1\end{pmatrix}=-3\neq0\ \Rightarrow\ \text{LI}$$
$$\vert S\vert=3=\dim P_2\ \Rightarrow\ S\ \text{es base de } P_2$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Distinguí si piden $\operatorname{Col}$, $\operatorname{Ren}$, rango o nulidad?
- [ ] ¿Para $\operatorname{Col}$ usé las columnas pivote de $A$ y no las de la escalonada?
- [ ] ¿Para $\operatorname{Ren}$ usé los renglones no nulos de la escalonada?
- [ ] ¿Conté pivotes para el rango y variables libres para la nulidad?
- [ ] ¿Verifiqué rango + nulidad $=n$ (columnas)?
- [ ] ¿Recordé que $A\sim B$ no conserva $\operatorname{Col}$?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
