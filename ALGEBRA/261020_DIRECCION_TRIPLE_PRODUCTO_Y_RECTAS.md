# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 20/10/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261020_DIRECCION_TRIPLE_PRODUCTO_Y_RECTAS.md` |
| **Tema principal** | Dirección y cosenos directores, triple producto escalar y rectas en $\mathbb{R}^3$ |
| **Fecha base** | 20/10/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261020` + teoría estándar (Grossman cap. 4) |
| **Cómo citarla** | «📘 Cheatsheet `261020_DIRECCION_TRIPLE_PRODUCTO_Y_RECTAS` §2.A» |
| **Notación** | $v=(x,y,z)$ vector de posición · $\lVert v\rVert$ norma · $\alpha,\beta,\gamma$ ángulos directores · $\cos\alpha,\cos\beta,\cos\gamma$ cosenos directores · $u\cdot(v\times w)$ triple producto · $P,Q$ puntos · $L$ recta · $t$ parámetro |
| **No repite** | producto punto, norma, ángulo y propiedades del producto cruz están en `261015` — aquí solo se usan como puente |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿Piden dirección, volumen o una recta?**
- Dirección / ángulos / vector unitario → §2.A, §2.B · §4.1, §4.2.
- Volumen, área de base, coplanaridad → triple producto → §2.C · §4.3.
- Ecuación de una recta → §2.D · §4.4.

**Paso 1 — ¿Qué pide exactamente?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "Halle la dirección de $v$" | Vector unitario | $\dfrac{v}{\lVert v\rVert}$ | §2.A · §4.1 |
| "Halle los cosenos directores" | Cada componente sobre la norma | $\cos\alpha=\dfrac{x}{\lVert v\rVert}$ | §2.A · §4.1 |
| "Halle los ángulos directores" | Inversa del coseno | $\alpha=\arccos(\cos\alpha)$ | §2.A · §4.1 |
| "Vector de magnitud $m$ con cosenos directores dados" | Multiplicar cosenos por $m$ | $v=m\,(\cos\alpha,\cos\beta,\cos\gamma)$ | §2.B · §4.2 |
| "Verifique que los cosenos son de una dirección" | Suma de cuadrados | $\cos^{2}\alpha+\cos^{2}\beta+\cos^{2}\gamma=1$ | §2.A · §3 Caso 2 |
| "Volumen del paralelepípedo" | Triple producto | $\lvert u\cdot(v\times w)\rvert$ | §2.C · §4.3 |
| "¿Son coplanares $u,v,w$?" | Triple producto nulo | $u\cdot(v\times w)=0$ | §2.C · §3 Caso 6 |
| "Ecuación vectorial / paramétrica / simétrica de $L$" | Punto + vector director | $OR=OP+t\,v$ | §2.D · §4.4 |
| "Recta que pasa por dos puntos $P$ y $Q$" | Restar | $v=Q-P$ | §2.D · §4.4 |
| "Demuestre $\lVert u\times v\rVert\le\lVert u\rVert\lVert v\rVert$" | Acotar $\sin\theta$ | $0\le\sin\theta\le1$ | §2.E · §4.5 |
| "¿$u$ y $v$ son paralelos?" | Producto cruz nulo | $u\times v=0$ | §2.E · §4.5 |

**Frases literales del profe → método**
- *"En $\mathbb{R}^3$ la dirección la vamos a definir como el vector unitario"* → dirección = $v/\lVert v\rVert$.
- *"Un solo ángulo en $\mathbb{R}^3$ forma un cono"* → no basta un ángulo: hacen falta tres ángulos directores.
- *"Siempre la suma de los cuadrados de los cosenos directores es uno"* → verificación obligatoria.
- *"Es sencillamente multiplicar cada uno de los cosenos por su norma"* → vector de magnitud dada.
- *"Área de la base por altura"* → así sale el triple producto como volumen.
- *"Las simétricas salen de despejar $t$"* → de las paramétricas.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Dirección, cosenos y ángulos directores
$$\text{dirección de }v=\frac{v}{\lVert v\rVert}$$
$$\cos\alpha=\frac{x}{\lVert v\rVert},\qquad \cos\beta=\frac{y}{\lVert v\rVert},\qquad \cos\gamma=\frac{z}{\lVert v\rVert}$$
$$\cos^{2}\alpha+\cos^{2}\beta+\cos^{2}\gamma=1,\qquad \alpha,\beta,\gamma\in[0,\pi]$$
Si $\lVert v\rVert=1$: $\;v=(\cos\alpha,\cos\beta,\cos\gamma)$.

**🔤 Diccionario:** $\alpha,\beta,\gamma$ ángulos con los ejes $x,y,z$ · $\cos\alpha,\cos\beta,\cos\gamma$ cosenos directores (componentes del vector unitario) · $\lVert v\rVert$ norma · en $\mathbb{R}^2$ basta un ángulo (polares: $(\cos\theta,\sin\theta)$).

### B. Vector con magnitud y dirección dadas
$$v=m\,(\cos\alpha,\cos\beta,\cos\gamma),\qquad \lVert v\rVert=m$$
**🔤 Diccionario:** $m$ magnitud pedida · los cosenos deben cumplir la suma de cuadrados igual a $1$.

### C. Triple producto escalar y volumen
$$u\cdot(v\times w)=\begin{vmatrix}u_1&u_2&u_3\\ v_1&v_2&v_3\\ w_1&w_2&w_3\end{vmatrix},\qquad V=\lvert u\cdot(v\times w)\rvert$$
$$V=\underbrace{\lVert v\times w\rVert}_{\text{área base}}\cdot\underbrace{\lvert u\cdot\hat{n}\rvert}_{\text{altura}},\qquad \hat{n}=\frac{v\times w}{\lVert v\times w\rVert}$$

**🔤 Diccionario:** $V$ volumen del paralelepípedo · $\hat{n}$ vector unitario normal a la base · $\lVert v\times w\rVert$ área de la base · $u\cdot(v\times w)=0$ ⇒ coplanares.

### D. Rectas en $\mathbb{R}^3$
Con punto $P=(x_1,y_1,z_1)$ y vector director $v=(v_1,v_2,v_3)$:
$$\text{vectorial: } (x,y,z)=(x_1,y_1,z_1)+t\,(v_1,v_2,v_3)$$
$$\text{paramétricas: } x=x_1+tv_1,\quad y=y_1+tv_2,\quad z=z_1+tv_3$$
$$\text{simétricas: } \frac{x-x_1}{v_1}=\frac{y-y_1}{v_2}=\frac{z-z_1}{v_3}$$

**🔤 Diccionario:** $t\in\mathbb{R}$ parámetro · $v=Q-P$ vector director (paralelo a la recta) · $P$ punto de paso · en simétricas, si $v_i=0$ se omite esa fracción y se escribe $x_i=x$ constante.

### E. Corolarios del producto cruz
$$\lVert u\times v\rVert\le\lVert u\rVert\,\lVert v\rVert$$
$$u\times v=0\iff u\parallel v\quad(u,v\neq0)$$

**🔤 Diccionario:** la desigualdad sale de $\lVert u\times v\rVert=\lVert u\rVert\lVert v\rVert\sin\theta$ con $\sin\theta\le1$ · $\parallel$ = paralelos (misma recta).

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Dimensión de la dirección:** en $\mathbb{R}^2$ la dirección es un ángulo; en $\mathbb{R}^3$ son **tres** ángulos directores.
- **Caso 1 — Dirección = unitario:** la dirección de $v$ es el vector unitario $v/\lVert v\rVert$, no un ángulo suelto.
- **Caso 2 — Verificación:** los cosenos directores siempre suman $1$ al cuadrado; si no, hay error.
- **Caso 3 — Rango de ángulos:** $\alpha,\beta,\gamma\in[0,\pi]$; el coseno puede ser negativo (componente negativa).
- **Caso 4 — Magnitud:** para un vector de magnitud $m$ se multiplican los cosenos por $m$; no se normaliza de nuevo.
- **Caso 5 — Signo del volumen:** el triple producto puede ser negativo; el **volumen** es su valor absoluto.
- **Caso 6 — Coplanaridad:** $u\cdot(v\times w)=0$ ⇒ los tres vectores son coplanares (volumen $0$).
- **Caso 7 — Base degenerada:** si $v\times w=0$, la base no existe (vectores paralelos) y el volumen es $0$.
- **Caso 8 — Recta:** se necesitan **dos** puntos (o un punto y el vector director). $v=Q-P$; usar $P-Q$ da el vector opuesto, la misma recta.
- **Caso 9 — Simétricas:** solo se escriben si $v_1,v_2,v_3\neq0$; si alguna componente es $0$, esa fracción se omite.
- **Caso 10 — Mano derecha:** el sentido de $u\times v$ se decide con la regla de la mano derecha.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Cosenos y ángulos directores
1. Calcular $\lVert v\rVert$.
2. Dividir cada componente por la norma.
3. Verificar la suma de cuadrados $=1$.
4. Aplicar $\arccos$ a cada coseno.

**Plantilla** ($v=(2,3,6)$, $\lVert v\rVert=7$):
$$\cos\alpha=\frac{2}{7},\quad \cos\beta=\frac{3}{7},\quad \cos\gamma=\frac{6}{7}$$
$$\left(\frac{2}{7}\right)^{2}+\left(\frac{3}{7}\right)^{2}+\left(\frac{6}{7}\right)^{2}=\frac{4+9+36}{49}=1$$
$$\alpha=\arccos\frac{2}{7}\approx73.4^{\circ},\quad \beta\approx64.6^{\circ},\quad \gamma\approx31.0^{\circ}$$

### 4.2 Vector con magnitud y dirección dadas
1. Verificar que los cosenos suman $1$ al cuadrado.
2. Multiplicar cada coseno por la magnitud pedida.

**Plantilla** ($m=7$; $\cos\alpha=\frac{1}{\sqrt{6}}$, $\cos\beta=\frac{1}{\sqrt{3}}$, $\cos\gamma=\frac{1}{\sqrt{2}}$):
$$v=7\left(\frac{1}{\sqrt{6}},\frac{1}{\sqrt{3}},\frac{1}{\sqrt{2}}\right)$$
$$\lVert v\rVert=7\sqrt{\frac{1}{6}+\frac{1}{3}+\frac{1}{2}}=7\sqrt{1}=7$$

### 4.3 Volumen por triple producto
1. Calcular $v\times w$ (o el determinante de las tres filas).
2. Multiplicar escalarmente por $u$.
3. Tomar valor absoluto.

**Plantilla** ($u=(1,1,0)$, $v=(1,0,1)$, $w=(0,1,1)$):
$$u\cdot(v\times w)=\begin{vmatrix}1&1&0\\1&0&1\\0&1&1\end{vmatrix}=-2$$
$$V=\lvert-2\rvert=2$$
y la base mide $\lVert v\times w\rVert=\lVert(-1,-1,1)\rVert=\sqrt{3}$.

### 4.4 Ecuaciones de la recta
1. Vector director $v=Q-P$.
2. Ecuación vectorial con $P$ y $v$.
3. Expandir a paramétricas.
4. Despejar $t$ en cada una para las simétricas.

**Plantilla** ($P=(1,2,3)$, $Q=(4,5,6)$):
$$v=Q-P=(3,3,3)$$
$$(x,y,z)=(1,2,3)+t(3,3,3)$$
$$x=1+3t,\quad y=2+3t,\quad z=3+3t$$
$$\frac{x-1}{3}=\frac{y-2}{3}=\frac{z-3}{3}$$

### 4.5 Demostrar los corolarios
1. Usar $\lVert u\times v\rVert=\lVert u\rVert\lVert v\rVert\sin\theta$.
2. Acotar $0\le\sin\theta\le1$.
3. Para el paralelismo, $\lVert u\times v\rVert=0\iff\sin\theta=0\iff\theta=0$ o $\theta=\pi$.

**Plantilla:**
$$\lVert u\times v\rVert=\lVert u\rVert\lVert v\rVert\sin\theta\le\lVert u\rVert\lVert v\rVert$$
$$u\times v=0\iff\sin\theta=0\iff\theta\in\{0,\pi\}\iff u\parallel v$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Dividí por $\lVert v\rVert$ y no por otra cosa?
- [ ] ¿Verifiqué que los cosenos suman $1$ al cuadrado?
- [ ] ¿Los ángulos quedaron en $[0,\pi]$?
- [ ] ¿Para magnitud $m$ multipliqué los cosenos por $m$?
- [ ] ¿El volumen es valor absoluto del triple producto?
- [ ] ¿Usé dos puntos (o punto + director) para la recta?
- [ ] ¿Omití las fracciones simétricas con denominador $0$?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
