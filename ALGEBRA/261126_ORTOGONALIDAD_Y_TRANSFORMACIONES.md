# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 26/11/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261126_ORTOGONALIDAD_Y_TRANSFORMACIONES.md` |
| **Tema principal** | 4.9 bases ortonormales, Gram-Schmidt, matriz ortogonal y proyecciones + 5.1–5.2 transformaciones lineales |
| **Fecha base** | 26/11/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261126` + `Clase14_Parte2` + `Clase15` (Nakos) |
| **Cómo citarla** | «📘 Cheatsheet `261126_ORTOGONALIDAD_Y_TRANSFORMACIONES` §2.C» |
| **Notación** | $\Vert v\Vert$ norma · $u\cdot v$ producto punto · $H$ subespacio · $H^{\perp}$ complemento · $Q$ ortogonal · $T:V\to W$ |
| **No repite** | proyección sobre un vector → `261015`; coordenadas y base → `261117`/`261119` |
| **🔔 Sincronización** | Copia espejo en `02_NOTAS_OBSIDIAN/ALGEBRA` + push por git el 2026-11-26 ✅ |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿El problema es de ortogonalidad o de funciones?**
- Ortogonalidad: normas, productos punto, bases ortonormales, proyecciones → §2.A–§2.G.
- Transformaciones: $T(x)=Ax$ o $T:V\to W$ → §2.H–§2.K.

**Paso 1 — Tabla de decisión**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "¿El conjunto es ortonormal?" | Producto punto $0$ y norma $1$ | $u_i\cdot u_j=\delta_{ij}$ | §2.A · §3 Caso 0 |
| "¿Un ortogonal es LI?" | Teo 1 (4.9) | vectores no nulos | §2.B |
| "Construya base ortonormal" | Gram-Schmidt | $u_k=w_k/\Vert w_k\Vert$ | §2.C · §4.1 |
| "¿$Q$ es ortogonal?" | $Q^TQ=I$ | $Q^{-1}=Q^T$ | §2.D · §4.3 |
| "Calcule $\operatorname{proj}_H v$" | Base ortonormal de $H$ | $\sum(v\cdot u_i)u_i$ | §2.E · §4.2 |
| "Halle $H^{\perp}$ / $\dim H^{\perp}$" | Definición y Teo 6 | $\dim H^{\perp}=n-\dim H$ | §2.F |
| "Escriba $v=h+p$" | Teo 7 | $h=\operatorname{proj}_H v$, $p=v-h$ | §2.G |
| "¿$T$ es lineal?" | 2 propiedades o Teo 3 | $T(u+v)=T(u)+T(v)$, $T(cu)=cT(u)$ | §2.I · §4.4 |
| "Demuestre $T(0)=0$" | Teo 4 (5.1) | $T(0)=T(0+0)$ | §2.K |
| "Descartar que $T$ sea lineal" | Un contraejemplo | $T(0)\neq0$ o falla una propiedad | §4.5 |

**Frases literales del profe → método**
- *"Un conjunto ortonormal tiene producto punto cero entre diferentes y norma uno"* → dos condiciones, no una.
- *"Todo conjunto ortogonal de vectores diferentes de cero es LI"* → Teo 1 (4.9).
- *"El proceso de Gram-Schmidt es recursivo"* → cada vector se ortogonaliza contra **todos** los anteriores.
- *"Una matriz es ortogonal si su inversa es su transpuesta"* → $Q^TQ=I$.
- *"Las columnas de una matriz ortogonal forman una base ortonormal"* → Teo 3 (4.9).
- *"La proyección sobre $H$ necesita una base ortonormal de $H$"* → si no, primero Gram-Schmidt.
- *"La intersección $H\cap H^{\perp}$ es el vector cero"* → no el escalar cero.
- *"Si $T(0)\neq0$, ya no es lineal"* → descarte rápido.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Norma y conjunto ortonormal
$$\Vert v\Vert=\sqrt{v\cdot v}\ge0,\qquad \Vert v\Vert=0\iff v=0$$
$$S=\{u_1,\dots,u_k\}\ \text{ortonormal}\iff u_i\cdot u_j=\delta_{ij}=\begin{cases}1,&i=j\\0,&i\neq j\end{cases}$$
Si solo se cumple $u_i\cdot u_j=0$ para $i\neq j$, el conjunto es **ortogonal**.

**🔤 Diccionario:** $\delta_{ij}$ delta de Kronecker · la base canónica $\{e_1,\dots,e_n\}$ es ortonormal · ortonormal = ortogonal + norma $1$.

### B. Teorema 1 (4.9) — ortogonal implica LI
$$\text{Si } \{v_1,\dots,v_k\}\ \text{es ortogonal y } v_i\neq0\ \forall i,\ \text{entonces es LI}$$
**🔤 Diccionario:** la ortogonalidad da la independencia gratis · no se exige norma $1$, solo vectores no nulos.

### C. Teorema 2 (4.9) — existencia de base ortonormal (Gram-Schmidt)
Todo subespacio $H$ de $\mathbb{R}^n$ de dimensión $m$ tiene una base ortonormal. Construcción desde una base $\{v_1,\dots,v_m\}$:
$$u_1=\frac{v_1}{\Vert v_1\Vert},\qquad w_k=v_k-\sum_{j=1}^{k-1}(v_k\cdot u_j)u_j,\qquad u_k=\frac{w_k}{\Vert w_k\Vert}$$
**🔤 Diccionario:** $w_k$ componente de $v_k$ ortogonal a los anteriores · $u_k$ versión normalizada · el proceso conserva $\operatorname{Gen}\{v_1,\dots,v_k\}$.

### D. Matriz ortogonal
$$Q\ \text{es ortogonal}\iff Q^{-1}=Q^T\iff Q^TQ=I$$
**Teo 3 (4.9):** $Q$ es ortogonal si y solo si sus columnas forman una base ortonormal de $\mathbb{R}^n$.

**🔤 Diccionario:** $Q$ cuadrada $n\times n$ · $Q^TQ=I$ también implica $QQ^T=I$ · las columnas son ortonormales.

### E. Proyección ortogonal sobre un subespacio
$$\operatorname{proj}_H(v)=(v\cdot u_1)u_1+\dots+(v\cdot u_k)u_k$$
con $\{u_1,\dots,u_k\}$ base **ortonormal** de $H$.

**🔤 Diccionario:** $v\cdot u_i$ escalares (coordenadas) · si la base es ortogonal sin normalizar, se divide entre $\Vert u_i\Vert^2$ · si $H=\operatorname{Gen}\{w\}$, es la proyección sobre un vector (🔗 `261015`).

### F. Complemento ortogonal
$$H^{\perp}=\{x\in\mathbb{R}^n: x\cdot h=0\ \forall h\in H\}$$
**Teo 6 (4.9):** $H^{\perp}$ es subespacio; $H\cap H^{\perp}=\{0\}$; $\dim H^{\perp}=n-\dim H$.

**🔤 Diccionario:** $H^{\perp}$ son los vectores ortogonales a **todo** $H$ · la intersección es el vector $0$, no el escalar · la dimensión es la que "falta" para $n$.

### G. Teorema 7 (4.9) — descomposición ortogonal
$$v=h+p,\qquad h=\operatorname{proj}_H(v)\in H,\quad p=v-h\in H^{\perp}$$
El par $(h,p)$ es único.

**🔤 Diccionario:** $h$ parte en $H$ · $p$ parte ortogonal · $p$ es también $\operatorname{proj}_{H^{\perp}}(v)$.

### H. Transformación matricial
$$T:\mathbb{R}^n\to\mathbb{R}^m,\qquad T(x)=Ax$$
con $A$ de $m\times n$ (matriz estándar de $T$).

**🔤 Diccionario:** dominio $\mathbb{R}^n$ (entradas) · codominio $\mathbb{R}^m$ (salidas) · $A$ tiene $m$ filas y $n$ columnas.

### I. Transformación lineal (Definición 5.2)
$$T:V\to W\ \text{es lineal}\iff T(u+v)=T(u)+T(v)\ \wedge\ T(cu)=cT(u)$$
para todos $u,v\in V$ y $c\in\mathbb{R}$. Si $V=W$, se llama **operador lineal**.

**🔤 Diccionario:** la suma de la izquierda ocurre en $V$ y la de la derecha en $W$ · $T$ respeta suma y producto por escalar.

### J. Teorema 3 (5.1) — forma equivalente
$$T\ \text{es lineal}\iff T(c_1v_1+c_2v_2)=c_1T(v_1)+c_2T(v_2)$$
**🔤 Diccionario:** con $c_1=c_2=1$ se recupera la suma; con $c_2=0$ el producto por escalar · se extiende a $n$ términos.

### K. Teorema 4 (5.1) — propiedades y descarte
$$T(0_V)=0_W,\qquad T(u-v)=T(u)-T(v)$$
**🔤 Diccionario:** si $T(0)\neq0$, $T$ **no** es lineal · $T(0)=0$ es necesario pero **no** suficiente · para descartar, basta un contraejemplo.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Ortogonal vs. ortonormal:** ortogonal exige productos punto nulos; ortonormal exige además norma $1$.
- **Caso 1 — Norma:** un vector ortogonal puede tener norma distinta de $1$; hay que normalizarlo.
- **Caso 2 — Gram-Schmidt:** a $v_k$ se le restan **todas** las proyecciones sobre $u_1,\dots,u_{k-1}$, no solo la última.
- **Caso 3 — GS conserva el generado:** $\operatorname{Gen}\{u_1,\dots,u_k\}=\operatorname{Gen}\{v_1,\dots,v_k\}$.
- **Caso 4 — Matriz ortogonal:** $Q^TQ=I$; también $QQ^T=I$ y $\det Q=\pm1$.
- **Caso 5 — $H^{\perp}$:** $\dim H^{\perp}=n-\dim H$; si $H$ es un plano en $\mathbb{R}^3$, $H^{\perp}$ es una recta.
- **Caso 6 — Intersección:** $H\cap H^{\perp}=\{0\}$; el único vector en ambos es el cero.
- **Caso 7 — $T(0)$:** si $T(0)\neq0$, no es lineal; si $T(0)=0$, hay que probar las dos propiedades.
- **Caso 8 — Matricial ⇒ lineal:** toda $T(x)=Ax$ es lineal (Teo 2, 5.1); el recíproco no siempre es matricial si el dominio es abstracto.
- **Caso 9 — Operador:** $T:V\to V$ se llama operador lineal.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Gram-Schmidt en $\mathbb{R}^3$
1. $u_1=v_1/\Vert v_1\Vert$.
2. $w_2=v_2-(v_2\cdot u_1)u_1$ y $u_2=w_2/\Vert w_2\Vert$.
3. $w_3=v_3-(v_3\cdot u_1)u_1-(v_3\cdot u_2)u_2$ y $u_3=w_3/\Vert w_3\Vert$.
4. Verificar $u_i\cdot u_j=0$ y $\Vert u_i\Vert=1$.

**Plantilla** ($v_1=(1,1,0)$, $v_2=(0,1,1)$, $v_3=(1,0,1)$):
$$u_1=\frac{1}{\sqrt2}(1,1,0),\qquad w_2=\left(-\frac12,\frac12,1\right),\quad u_2=\frac{1}{\sqrt6}(-1,1,2)$$
$$w_3=\left(\frac23,-\frac23,\frac23\right),\qquad u_3=\frac{1}{\sqrt3}(1,-1,1)$$
$$\text{Verificación: }u_i\cdot u_j=0\ (i\neq j),\qquad \Vert u_i\Vert=1$$

### 4.2 Proyección sobre un subespacio
1. Hallar una base de $H$.
2. Ortonormalizarla con Gram-Schmidt.
3. Calcular $\sum(v\cdot u_i)u_i$.
4. Verificar que $v-\operatorname{proj}$ es ortogonal a la base.

**Plantilla** ($H=\{(x,y,z):2x-y+3z=0\}$, $v=(3,-2,4)$):
$$\text{Base de }H:\ (1,2,0),\ (0,3,1)\ \Rightarrow\ u_1=\frac{1}{\sqrt5}(1,2,0),\ u_2=\frac{1}{\sqrt{70}}(-6,3,5)$$
$$\operatorname{proj}_H v=\frac{-1}{\sqrt5}u_1+\frac{-4}{\sqrt{70}}u_2=\left(\frac17,-\frac47,-\frac27\right)$$
$$\text{Verificación: }2\left(\frac17\right)-\left(-\frac47\right)+3\left(-\frac27\right)=0$$

### 4.3 Verificar que $Q$ es ortogonal
1. Calcular $Q^TQ$.
2. Si $Q^TQ=I$, $Q$ es ortogonal (columnas ortonormales).
3. Alternativa: verificar columnas ortonormales una por una.

**Plantilla** ($Q=\begin{pmatrix}1/\sqrt2&-1/\sqrt2\\1/\sqrt2&1/\sqrt2\end{pmatrix}$):
$$Q^TQ=\begin{pmatrix}1&0\\0&1\end{pmatrix}=I\ \Rightarrow\ Q\ \text{es ortogonal}$$

### 4.4 Verificar que $T$ es lineal
1. Tomar $u=(x_1,y_1)$, $v=(x_2,y_2)$ genéricos.
2. Probar $T(u+v)=T(u)+T(v)$.
3. Probar $T(cu)=cT(u)$.
4. Concluir; si es matricial, dar su matriz estándar.

**Plantilla** ($T(x,y)=(2x-3y,\ x+4y)$):
$$T(u+v)=\big(2(x_1+x_2)-3(y_1+y_2),\ (x_1+x_2)+4(y_1+y_2)\big)=T(u)+T(v)$$
$$T(cu)=(2cx-3cy,\ cx+4cy)=c(2x-3y,\ x+4y)=cT(u)$$
$$\text{Matriz estándar: }A=\begin{pmatrix}2&-3\\1&4\end{pmatrix}$$

### 4.5 Descartar que $T$ sea lineal
1. Calcular $T(0)$; si $T(0)\neq0$, no es lineal.
2. Si $T(0)=0$, buscar un contraejemplo con la suma o el escalar.
3. Concluir con el contraejemplo.

**Plantilla** ($f(x,y)=(x,1)$ y $g(x)=x^2$):
$$f(0,0)=(0,1)\neq(0,0)\ \Rightarrow\ f\ \text{no es lineal}$$
$$g(1+1)=4\neq2=g(1)+g(1)\ \Rightarrow\ g\ \text{no es lineal}$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Distingo ortogonal (productos nulos) de ortonormal (además norma $1$)?
- [ ] ¿En Gram-Schmidt resté todas las proyecciones anteriores?
- [ ] ¿Normalicé cada $w_k$ antes de continuar?
- [ ] ¿Verifiqué $Q^TQ=I$ para matriz ortogonal?
- [ ] ¿Usé base ortonormal para la proyección sobre $H$?
- [ ] ¿$\dim H^{\perp}=n-\dim H$ y $H\cap H^{\perp}=\{0\}$?
- [ ] ¿Probé suma y escalar (o $T(0)=0$ para descartar)?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
