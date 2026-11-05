# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 15/10/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261015_PRODUCTO_PUNTO_CRUZ_Y_PROYECCIONES.md` |
| **Tema principal** | Producto punto, norma, ángulo, proyecciones y producto cruz en $\mathbb{R}^3$ |
| **Fecha base** | 15/10/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261015` + teoría estándar (Grossman cap. 4) |
| **Cómo citarla** | «📘 Cheatsheet `261015_PRODUCTO_PUNTO_CRUZ_Y_PROYECCIONES` §2.D» |
| **Notación** | $u,v,w$ vectores · $\alpha$ escalar · $u\cdot v$ producto punto · $\lVert u\rVert$ norma · $u\times v$ producto cruz · $\theta$ ángulo · $\operatorname{proj}_v u$ proyección · $\hat{\imath},\hat{\jmath},\hat{k}$ base canónica |
| **Complementa** | `261103_ESPACIOS_VECTORIALES` y `261013_DETERMINANTES_Y_MATRICES_ELEMENTALES` — **sin repetir temas** |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿El resultado es escalar o vector?**
- Piden un **número** (ángulo, norma, área, distancia) → producto punto, norma o proyección → §2.A–§2.D.
- Piden un **vector** en $\mathbb{R}^3$ perpendicular a otros dos → producto cruz → §2.E.

**Paso 1 — ¿Qué pide exactamente?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "Calcule $u\cdot v$" | Multiplicar componente a componente y sumar | $u\cdot v=\sum_i u_iv_i$ | §2.A · §4.1 |
| "Halle $\lVert u\rVert$" | Raíz del producto punto consigo mismo | $\lVert u\rVert=\sqrt{u\cdot u}$ | §2.B · §4.1 |
| "Halle el ángulo entre $u$ y $v$" | Coseno del ángulo | $\cos\theta=\dfrac{u\cdot v}{\lVert u\rVert\lVert v\rVert}$ | §2.C · §4.2 |
| "¿Son ortogonales / perpendiculares?" | Producto punto nulo | $u\cdot v=0$ | §3 Caso 2 · §4.5 |
| "Proyecte $u$ sobre $v$" | Escalar por $v$ | $\operatorname{proj}_v u=\dfrac{u\cdot v}{\lVert v\rVert^{2}}\,v$ | §2.D · §4.3 |
| "Descomponga $u$ en paralela + ortogonal a $v$" | Restar la proyección | $u=\operatorname{proj}_v u+(u-\operatorname{proj}_v u)$ | §2.D · §4.3 |
| "Calcule $u\times v$" | Determinante mnemónico con $\hat{\imath},\hat{\jmath},\hat{k}$ | $(u_2v_3-u_3v_2,\ u_3v_1-u_1v_3,\ u_1v_2-u_2v_1)$ | §2.E · §4.4 |
| "¿Es $u\times v$ perpendicular a $u$ y a $v$?" | Producto punto nulo | $u\cdot(u\times v)=0$ | §2.F · §3 Caso 5 |
| "Área del paralelogramo / triángulo" | Norma del producto cruz | $\lVert u\times v\rVert$ | §2.H · §3 Caso 6 |
| "Demuestre una propiedad del producto cruz" | Componente a componente | desarrollo con $\hat{\imath},\hat{\jmath},\hat{k}$ | §4.6 |

**Frases literales del profe → método**
- *"El producto cruz está definido solamente para vectores en $\mathbb{R}^3$"* → fuera de $\mathbb{R}^3$ no existe.
- *"El determinante por definición es un número… es una forma de recordarlo"* → el determinante con $\hat{\imath},\hat{\jmath},\hat{k}$ es **mnemónico**, no formal.
- *"El seno está definido entre cero y pi"* → por eso $\lVert u\times v\rVert=\lVert u\rVert\lVert v\rVert\sin\theta$ sin valor absoluto.
- *"Si el producto punto es cero, el ángulo es 90"* → ortogonalidad.
- *"Recuerda que en la clase pasada me faltó el cuadrado"* → el denominador de la proyección es $\lVert v\rVert^{2}$.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Producto punto
$$u\cdot v=\sum_{i=1}^{n}u_iv_i=u_1v_1+u_2v_2+u_3v_3\quad\text{en }\mathbb{R}^3$$
Propiedades: conmutativa, distributiva respecto a la suma, lineal en el escalar, y **definida positiva**.

**🔤 Diccionario:** $u_i,v_i$ componentes $i$-ésimas · $n$ dimensión del espacio · el resultado es un **escalar**.

### B. Norma
$$\lVert u\rVert=\sqrt{u\cdot u},\qquad \lVert u\rVert^{2}=u\cdot u$$
**🔤 Diccionario:** $\lVert u\rVert$ longitud del vector · $\lVert u\rVert=0\iff u=0$ · vector unitario si $\lVert u\rVert=1$.

### C. Ángulo entre dos vectores
$$\cos\theta=\frac{u\cdot v}{\lVert u\rVert\,\lVert v\rVert},\qquad 0\le\theta\le\pi$$
Signo del producto punto: positivo ⇒ $0\le\theta<90^\circ$ · cero ⇒ $\theta=90^\circ$ · negativo ⇒ $90^\circ<\theta\le180^\circ$.

**🔤 Diccionario:** $\theta$ ángulo entre $u$ y $v$ · el coseno es un número, no un vector.

### D. Proyección y componente ortogonal
$$\operatorname{proj}_v u=\frac{u\cdot v}{\lVert v\rVert^{2}}\,v,\qquad u_{\perp}=u-\operatorname{proj}_v u$$
y se cumple $v\cdot u_{\perp}=0$.

**🔤 Diccionario:** $\operatorname{proj}_v u$ vector sobre la recta de $v$ · $u_{\perp}$ parte perpendicular a $v$ · $\lVert v\rVert^{2}$ (al cuadrado, no la norma sola).

### E. Producto cruz (solo en $\mathbb{R}^3$)
$$u\times v=\begin{vmatrix}\hat{\imath}&\hat{\jmath}&\hat{k}\\ u_1&u_2&u_3\\ v_1&v_2&v_3\end{vmatrix}=(u_2v_3-u_3v_2,\;u_3v_1-u_1v_3,\;u_1v_2-u_2v_1)$$
**🔤 Diccionario:** $\hat{\imath},\hat{\jmath},\hat{k}$ base canónica (vectores, no números) · el resultado es un **vector** de $\mathbb{R}^3$ · el determinante es solo mnemónico.

### F. Propiedades del producto cruz
$$u\times v=-(v\times u),\qquad u\times u=0,\qquad u\times 0=0$$
$$u\times(v+w)=u\times v+u\times w,\qquad (\alpha u)\times v=\alpha(u\times v)$$
$$u\cdot(u\times v)=0,\qquad v\cdot(u\times v)=0$$
**🔤 Diccionario:** $u\times u=0$ ⇒ no hay vector perpendicular a sí mismo · anticonmutativo ⇒ el orden importa.

### G. Desigualdad de Cauchy-Schwarz
$$\lvert u\cdot v\rvert\le\lVert u\rVert\,\lVert v\rVert$$
**🔤 Diccionario:** cota del producto punto · la igualdad ocurre cuando son paralelos.

### H. Identidad de Lagrange y norma del producto cruz
$$\lVert u\times v\rVert^{2}=\lVert u\rVert^{2}\lVert v\rVert^{2}-(u\cdot v)^{2}$$
$$\lVert u\times v\rVert=\lVert u\rVert\,\lVert v\rVert\sin\theta$$
**🔤 Diccionario:** $\theta$ ángulo entre $u$ y $v$ · $\lVert u\times v\rVert$ = área del paralelogramo que forman.

### I. Triple producto escalar
$$u\cdot(v\times w)=\begin{vmatrix}u_1&u_2&u_3\\ v_1&v_2&v_3\\ w_1&w_2&w_3\end{vmatrix}$$
**🔤 Diccionario:** este **sí** es un determinante real (todo son números) · su valor absoluto = volumen del paralelepípedo.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Escalar vs vector:** producto punto → número; producto cruz → vector. Confundirlos arruina el ejercicio.
- **Caso 1 — Dimensión:** producto punto vale en $\mathbb{R}^n$; producto cruz **solo** en $\mathbb{R}^3$.
- **Caso 2 — Ortogonalidad:** $u\cdot v=0$ ⇒ perpendiculares (si $u,v\neq0$).
- **Caso 3 — Paralelismo:** $u\times v=0$ ⇒ paralelos (uno es múltiplo del otro).
- **Caso 4 — No conmutativo:** $u\times v=-(v\times u)$; nunca asumir igualdad.
- **Caso 5 — Perpendicularidad del cruz:** $u\times v$ es perpendicular a $u$ y a $v$ (verificar con producto punto).
- **Caso 6 — Áreas:** $\lVert u\times v\rVert$ = área del paralelogramo; $\tfrac12\lVert u\times v\rVert$ = área del triángulo.
- **Caso 7 — Denominador de la proyección:** es $\lVert v\rVert^{2}$, no $\lVert v\rVert$.
- **Caso 8 — Producto punto vs escalar:** no escribir $u\cdot v\cdot w$ sin paréntesis: $u\cdot v$ es escalar y luego escalar por $w$; distinto de $u\cdot(v\cdot w)$ que no está definido.
- **Caso 9 — Coseno rango:** $\theta\in[0,\pi]$ ⇒ $\sin\theta\ge0$, por eso $\lVert u\times v\rVert=\lVert u\rVert\lVert v\rVert\sin\theta$ sin valor absoluto.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Producto punto y norma
1. Multiplicar componentes homólogas.
2. Sumar.
3. Para la norma, sacar raíz del producto punto consigo mismo.

**Plantilla** ($u=(1,2,3)$, $v=(4,5,6)$):
$$u\cdot v=1\cdot4+2\cdot5+3\cdot6=32$$
$$\lVert u\rVert=\sqrt{1^{2}+2^{2}+3^{2}}=\sqrt{14}$$

### 4.2 Ángulo entre dos vectores
1. Calcular $u\cdot v$.
2. Calcular $\lVert u\rVert$ y $\lVert v\rVert$.
3. Despejar $\theta=\arccos\!\left(\dfrac{u\cdot v}{\lVert u\rVert\lVert v\rVert}\right)$.

**Plantilla** ($u=(1,0)$, $v=(1,1)$):
$$\cos\theta=\frac{1}{1\cdot\sqrt{2}}=\frac{1}{\sqrt{2}}\;\Rightarrow\;\theta=45^{\circ}$$

### 4.3 Proyección sobre un vector
1. Calcular el escalar $\dfrac{u\cdot v}{\lVert v\rVert^{2}}$.
2. Multiplicarlo por $v$.
3. La parte ortogonal es $u-\operatorname{proj}_v u$.

**Plantilla** ($u=(1,2)$, $v=(1,0)$):
$$\operatorname{proj}_v u=\frac{1}{1}(1,0)=(1,0),\qquad u_{\perp}=(1,2)-(1,0)=(0,2)$$
y en efecto $v\cdot u_{\perp}=(1)(0)+(0)(2)=0$.

### 4.4 Producto cruz
1. Armar el determinante mnemónico con $\hat{\imath},\hat{\jmath},\hat{k}$ en la primera fila.
2. Desarrollar cada cofactor.
3. Escribir el vector resultado.
4. Verificar $u\cdot(u\times v)=0$ y $v\cdot(u\times v)=0$.

**Plantilla** ($u=(1,2,3)$, $v=(4,5,6)$):
$$u\times v=(2\cdot6-3\cdot5,\;3\cdot4-1\cdot6,\;1\cdot5-2\cdot4)=(-3,6,-3)$$
$$u\cdot(u\times v)=-3+12-9=0$$

### 4.5 Decidir ortogonalidad o paralelismo
1. Calcular $u\cdot v$: si es $0$ ⇒ ortogonales.
2. Calcular $u\times v$: si es $\vec{0}$ ⇒ paralelos.

**Plantilla:** $u=(1,2,3)$, $w=(2,4,6)$: $u\times w=(0,0,0)$ ⇒ paralelos.

### 4.6 Demostrar una propiedad del producto cruz
1. Escribir $u=(u_1,u_2,u_3)$ y $v=(v_1,v_2,v_3)$.
2. Calcular cada componente con la definición.
3. Comparar componente a componente con el lado derecho.

**Plantilla** ($u\times u=0$):
$$u\times u=(u_2u_3-u_3u_2,\;u_3u_1-u_1u_3,\;u_1u_2-u_2u_1)=(0,0,0)$$

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿El resultado pedido es escalar o vector?
- [ ] ¿Estoy en $\mathbb{R}^3$ si uso producto cruz?
- [ ] ¿Puse $\lVert v\rVert^{2}$ en el denominador de la proyección?
- [ ] ¿Recordé que $u\times v=-(v\times u)$?
- [ ] ¿Verifiqué la perpendicularidad con producto punto?
- [ ] ¿Usé $\sin\theta$ (no $\cos$) para el área?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
