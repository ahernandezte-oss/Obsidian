# 📘 CHEATSHEET — CEDO · 25/11/2026

> **📇 Ficha del archivo**
> - **Archivo:** `261125_SISTEMAS_REPETIDOS.md`
> - **Tema principal:** Sistemas lineales homogéneos con **autovalores repetidos** y **vectores adjuntos** (generalizados)
> - **Fecha de clase:** 25/11/2026
> - **Fuente:** apuntes manuscritos del 25/11/2026 + transcripción `语音 261125_140541` + teoría estándar
> - **Cómo citarla al resolver:** «📘 Cheatsheet `261125_SISTEMAS_REPETIDOS` §4.1»
> - **Hermanas:** `261111_SISTEMAS_AUTOVALORES` (simples) · `261123_SISTEMAS_COMPLEJOS` (complejos)
> - **Nombre del método en clase:** **método de vectores adjuntos**
> - **Ruta del curso:** sistemas no homogéneos → forma no canónica → Laplace · **parcial: miércoles 9 de diciembre**

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Paso 0 — ¿Sistema lineal de coeficientes constantes?**
- No → EDO escalar o sistema no lineal.
- Sí → Paso 1.

**Paso 1 — Característica y raíces.** Buscar primero $\lambda = 1$ o $\lambda = -1$ (Ruffini).

**Paso 2 — ¿Hay algún autovalor repetido?**
- Todas simples → `261111` (reales) o `261123` (complejos). **Aquí no se usan adjuntos.**
- Alguna repetida → Paso 3.

**Paso 3 — Contar los vectores propios disponibles.**

$$
l = n - r \qquad \left(l = \text{número de autovectores independientes}\right)
$$

| Comparación | Qué significa | Qué hacer |
|---|---|---|
| $l = m$ | hay tantos vectores como multiplicidad | **no** hacen falta adjuntos |
| $l < m$ | faltan $m - l$ vectores | **faltan $m-l$ adjuntos** |

**🔤 Diccionario:** $n$ orden del sistema (para $3\times3$, $n=3$) · $r$ rango de $A-\lambda I$ · $m$ multiplicidad algebraica de $\lambda$ · $l$ multiplicidad geométrica (número de autovectores).

### Tabla de decisión

| Si el enunciado dice… | Método | Fórmula base | 👉 Ir a |
|---|---|---|---|
| $\dot{\vec x} = A\vec x$, $A$ numérica | autovalores | $\det\left(A-\lambda I\right) = 0$ | §2.A |
| la característica da una raíz repetida | contar $l$ | $l = n - r$ | §2.B |
| $l < m$ | **vectores adjuntos** | $\left(A-\lambda I\right)\vec\beta = \vec\alpha$ | §2.C · §4.1 |
| $m = 2$ y $l = 1$ | un adjunto | $\left(\vec\beta_1 + t\vec\alpha\right)e^{\lambda t}$ | §2.D |
| $m = 3$ y $l = 1$ | dos adjuntos | $\left(\vec\beta_2 + t\vec\beta_1 + \tfrac{t^{2}}{2}\vec\alpha\right)e^{\lambda t}$ | §2.E |
| hay además un autovalor simple | superposición | suma de las dos familias | §3 Caso 4 |

### Frases literales del profesor (25/11)

- "**$M$** es multiplicidad; **$l$** son los vectores propios."
- "**$l = n - r$**", con $n$ orden de la matriz y $r$ rango.
- "Si multiplicidad $2$, **solo $1$ adyunto**."
- "Si $m = 3$, **dos vectores adjuntos**, $\vec\beta_1$ y $\vec\beta_2$."
- "Este método se llama **método de vectores adjuntos**."
- "Para el parcial, **máximo sistema $3\times3$**."
- "Siempre buscamos primero $\lambda = 1$ o $-1$."
- "Trabajamos **por componentes**" (no Cramer, no Gauss completo).
- "El primer vector que está dentro del paréntesis **es el mismo que está fuera**."

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Ecuación característica

$$
\det\left(A-\lambda I\right) = 0
$$

**🔤 Diccionario:** $A$ matriz de coeficientes · $\lambda$ autovalor · $I$ identidad del mismo orden.

Para un $3\times3$ se puede usar:

$$
\lambda^{3} - \left(\operatorname{tr}A\right)\lambda^{2} + \left(\text{suma de menores }2\times2\right)\lambda - \det A = 0
$$

**🔤 Diccionario:** $\operatorname{tr}A$ traza · los menores $2\times2$ son los que quedan al tachar fila y columna de cada elemento diagonal · $\det A$ determinante.

### B. Conteo de vectores propios

$$
l = n - r, \qquad \text{faltan } m - l \text{ adjuntos}
$$

**🔤 Diccionario:** $r = \operatorname{rango}\left(A-\lambda I\right)$; se calcula escalonando o mirando si las filas son múltiplos.

### C. Ecuación del vector adjunto

$$
\left(A-\lambda I\right)\vec\beta = \vec\alpha
$$

**🔤 Diccionario:** $\vec\alpha$ autovector ya conocido (el lado derecho **no** es cero) · $\vec\beta$ vector adjunto, la incógnita.

**Cadena** (si hacen falta dos o más):

$$
\left(A-\lambda I\right)\vec\beta_{i+1} = \vec\beta_i, \qquad i = 1, 2, \ldots
$$

**🔤 Diccionario:** cada adjunto se obtiene con el **anterior** como término independiente, no con $\vec\alpha$ otra vez.

### D. Solución para multiplicidad $2$ (un adjunto)

$$
\vec x = C_1\vec\alpha\,e^{\lambda t} + C_2\left(\vec\beta_1 + t\vec\alpha\right)e^{\lambda t}
$$

**🔤 Diccionario:** $\vec\alpha$ autovector · $\vec\beta_1$ adjunto · el $t$ multiplica **al autovector**, no al adjunto.

### E. Solución para multiplicidad $3$ (dos adjuntos)

$$
\vec x = C_1\vec\alpha\,e^{\lambda t} + C_2\left(\vec\beta_1 + t\vec\alpha\right)e^{\lambda t} + C_3\left(\vec\beta_2 + t\vec\beta_1 + \frac{t^{2}}{2}\vec\alpha\right)e^{\lambda t}
$$

**🔤 Diccionario:** $\vec\beta_1$ primer adjunto (satisface $\left(A-\lambda I\right)\vec\beta_1 = \vec\alpha$) · $\vec\beta_2$ segundo adjunto (satisface $\left(A-\lambda I\right)\vec\beta_2 = \vec\beta_1$) · $\frac{t^{2}}{2}$ viene de $2!$ en el denominador.

### F. Forma general de la cadena

$$
\vec\gamma_q = \left(\vec\beta_q + t\vec\beta_{q-1} + \cdots + \frac{t^{q-1}}{\left(q-1\right)!}\vec\beta_1 + \frac{t^{q}}{q!}\vec\alpha\right)e^{\lambda t}
$$

**🔤 Diccionario:** $q$ = posición en la cadena ($q=0$ es el autovector) · los denominadores son factoriales · el orden de los vectores va **de atrás hacia adelante** multiplicando potencias crecientes de $t$.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

### Caso 1 — $m=2$, $l=1$ (un adjunto)

Se resuelve $\left(A-\lambda I\right)\vec\beta = \vec\alpha$ y se escribe:

$$
\vec x = C_1\vec\alpha e^{\lambda t} + C_2\left(\vec\beta + t\vec\alpha\right)e^{\lambda t}
$$

Aporta **dos** constantes, igual que cualquier autovalor doble.

### Caso 2 — $m=3$, $l=1$ (dos adjuntos)

Cadena completa: $\vec\beta_1$ con RHS $\vec\alpha$; $\vec\beta_2$ con RHS $\vec\beta_1$. Solución en §2.E.

### Caso 3 — $m=3$, $l=2$ (un adjunto)

Dos autovectores independientes $\vec\alpha_1, \vec\alpha_2$ y **un** adjunto para uno de ellos:

$$
\vec x = C_1\vec\alpha_1e^{\lambda t} + C_2\vec\alpha_2e^{\lambda t} + C_3\left(\vec\beta + t\vec\alpha_1\right)e^{\lambda t}
$$

### Caso 4 — Mezcla con autovalor simple (superposición)

$$
\vec x = \underbrace{C_1\vec\gamma e^{\mu t}}_{\text{simple}} + \underbrace{C_2\vec\alpha e^{\lambda t} + C_3\left(\vec\beta + t\vec\alpha\right)e^{\lambda t}}_{\text{repetido } m=2}
$$

**🔤 Diccionario:** $\mu$ autovalor simple con autovector $\vec\gamma$ · $\lambda$ autovalor doble · total de constantes = orden del sistema.

### Reglas de oro

| # | Regla | Por qué |
|---|---|---|
| 1 | **Contar $l$ antes de calcular** | decide si hay adjuntos |
| 2 | **Ruffini con $\pm1$ primero** | es lo que el profesor hace siempre |
| 3 | **El adjunto lleva $\vec\alpha$ en el lado derecho** | no se iguala a cero |
| 4 | **La cadena usa el anterior** | $\vec\beta_2$ se calcula con $\vec\beta_1$ |
| 5 | **El $t$ va con el autovector** | $\vec\beta + t\vec\alpha$, no al revés |
| 6 | **Por componentes** | menos error que Gauss completo |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Sistema con autovalor repetido (método de vectores adjuntos)

1. Escribir $A$.
2. Característica; probar $\lambda = 1$, luego $-1$, luego $\pm2$ (Ruffini).
3. Identificar raíces y su multiplicidad $m$.
4. Para la raíz repetida: calcular $r = \operatorname{rango}\left(A-\lambda I\right)$ y $l = n - r$.
5. Si $l = m$: no hay adjuntos, usar solo autovectores.
6. Si $l < m$: resolver $\left(A-\lambda I\right)\vec v = \vec 0$ para el autovector $\vec\alpha$.
7. Resolver $\left(A-\lambda I\right)\vec\beta_1 = \vec\alpha$ con el mismo escalonamiento, **cambiando el término independiente**.
8. Si $m - l \geq 2$: resolver $\left(A-\lambda I\right)\vec\beta_2 = \vec\beta_1$.
9. Escribir la solución con los factores $t$ según §2.D o §2.E.
10. Sumar las contribuciones de los autovalores simples.
11. Verificar con las relaciones de la cadena.

**Plantilla mínima (ejemplo de clase):**

$$
A = \begin{pmatrix} -5 & -4 & 9 \\ 10 & 9 & -10 \\ 1 & 1 & 3 \end{pmatrix}, \qquad \det\left(A-\lambda I\right) = \lambda^{3} - 7\lambda^{2} + 8\lambda + 16 = 0
$$

$$
\lambda = -1 \quad\left(l = 3 - 2 = 1\right) \;\Rightarrow\; \vec\gamma = \begin{pmatrix} 1 \\ -1 \\ 0 \end{pmatrix}
$$

$$
\lambda = 4 \quad\left(m = 2,\ r = 2,\ l = 1\right) \;\Rightarrow\; \text{falta } 1 \text{ adjunto}
$$

$$
\left(A-4I\right)\vec v = \vec 0 \;\Rightarrow\; \vec\alpha = \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}
$$

$$
\left(A-4I\right)\vec\beta = \vec\alpha \;\Rightarrow\; \vec\beta = \begin{pmatrix} 0 \\ 2 \\ 1 \end{pmatrix}
$$

$$
\boxed{\vec x(t) = C_1\begin{pmatrix} 1 \\ -1 \\ 0 \end{pmatrix}e^{-t} + C_2\begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}e^{4t} + C_3\left[\begin{pmatrix} 0 \\ 2 \\ 1 \end{pmatrix} + t\begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}\right]e^{4t}}
$$

### 4.2 Verificación

| Qué | Cómo |
|---|---|
| Autovector | $A\vec\alpha = \lambda\vec\alpha$ |
| Adjunto | $\left(A-\lambda I\right)\vec\beta = \vec\alpha$ |
| Cadena larga | $\left(A-\lambda I\right)\vec\beta_2 = \vec\beta_1$ |
| Solución | sustituir en el sistema; el residual debe ser $\sim10^{-9}$ |
| Constantes | deben sumar el orden del sistema |

---

## ✅ 5. CHECKLIST FINAL

- [ ] Busqué $\lambda=1$ y $\lambda=-1$ antes de la calculadora.
- [ ] Escribí la multiplicidad $m$ de cada raíz.
- [ ] Calculé **$l = n - r$** y lo comparé con $m$.
- [ ] Si $l < m$, hay exactamente $m - l$ adjuntos.
- [ ] El adjunto se resolvió con **$\vec\alpha$ (o el adjunto anterior) en el lado derecho**.
- [ ] El término $t$ multiplica al **autovector**.
- [ ] Los denominadores factoriales están ($1$, $t$, $\frac{t^{2}}{2}$).
- [ ] Sumé la contribución de los autovalores simples.
- [ ] El número de constantes es igual al orden.
- [ ] Verifiqué $A\vec\alpha = \lambda\vec\alpha$ y $\left(A-\lambda I\right)\vec\beta = \vec\alpha$.

---

## ⚠️ 6. TRAMPAS DE ESTA CLASE

| Trampa | Consecuencia | Antídoto |
|---|---|---|
| Igualar el adjunto a cero | se obtiene $\vec\beta = \vec 0$ | el lado derecho es $\vec\alpha$ |
| Usar $\vec\alpha$ para el segundo adjunto | cadena rota | $\vec\beta_2$ se calcula con $\vec\beta_1$ |
| Poner $t$ al adjunto | solución incorrecta | $t$ va con el autovector |
| Olvidar contar $l$ | se inventan o se omiten adjuntos | regla 1 |
| Creer que repetido = $l=1$ siempre | a veces $l=2$ | calcular el rango |
| Olvidar el factorial | falta $\frac{1}{2}$ en $t^{2}$ | §2.E |
| No sumar el autovalor simple | faltan constantes | regla 6 |
