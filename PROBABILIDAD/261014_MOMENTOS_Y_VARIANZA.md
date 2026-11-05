# 📘 CHEATSHEET — PROBABILIDAD · 14/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261014_MOMENTOS_Y_VARIANZA.md`
> - **Fecha de transcripción:** 14/10/2026 (`AAMMDD` = `261014`)
> - **Tema principal:** MOMENTOS Y VARIANZA — momentos respecto al origen y respecto a la media · lema de existencia · varianza · desviación estándar
> - **Fuente:** transcripción de clase. Complementos marcados con `➕`.
> - **Continuidad:** requiere **valor esperado de una transformación** (clase previa). Antecede a `261028_MODELOS_CONTINUOS` (allí se usan estos resultados para Poisson, Gamma y exponencial).
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261014_MOMENTOS_Y_VARIANZA` §2.B».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Qué potencia se pide y respecto a qué punto?**
   - Potencia de $X$ **sin restar** nada → momento **respecto al origen** ($\mu_r'$).
   - Potencia de $X$ **menos su media** → momento **respecto a la media** ($\mu_r$).
2. **Paso 1 — ¿Piden la "dispersión", el "parecido con la media" o el "riesgo"?** → **varianza** (orden 2) o su raíz.
3. **Paso 2 — ¿Conozco $X$ o solo sé que existe su momento?** → si solo hablan de existencia, aplica el **lema** (§2.C).
4. **Paso 3 — ¿El resultado debe estar en unidades interpretables?** → usa **desviación estándar**, no varianza.

**Tabla de decisión (frase del enunciado → qué es → bloque donde está la fórmula):**

| Si el enunciado dice… | Qué es | Fórmula | 👉 Ir a |
|---|---|---|---|
| "halle $E(X^{r})$", "momento de orden $r$", "segundo momento" | momento respecto al **origen** $\mu_r'$ | $\mu_r'=E(X^{r})$ | **§2.A** |
| "desviaciones respecto a la media", "qué tan lejos está del promedio" | momento **central** $\mu_r$ | $\mu_r=E\left[(X-E(X))^{r}\right]$ | **§2.B** |
| "varianza", "dispersión", "momento central de orden 2" | $\mu_2=V(X)$ | $V(X)=E\left[(X-E(X))^{2}\right]$ | **§2.B** + **§2.D** |
| "desviación estándar" o "desviación típica" | raíz de la varianza | $\sigma=\sqrt{V(X)}$ | **§2.D** |
| "¿si existe el momento de orden $r$ existen los menores?" | **lema de existencia** | $0\le s\le r$ | **§2.C** |
| dan $f(x)$ o $p(x)$ y piden $V(X)$ "rápido" | **fórmula recurrente** | $V(X)=E(X^{2})-\left[E(X)\right]^{2}$ | **§3 Regla 1** + **§4.B** |
| piden el rango de valores "que se parecen a la media" | **intervalo** $\mu\pm\sigma$ | $\left[E(X)-\sigma,\ E(X)+\sigma\right]$ | **§3 Regla 4** |
| piden $E\left[(X-c)^{r}\right]$ con $c$ constante | momento respecto a una constante | $\mu_r(c)=E\left[(X-c)^{r}\right]$ | **§2.B** |

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Momentos con respecto al origen (o respecto a cero)

- **Definición:**
$$
\mu_r'=E\left(X^{r}\right)
$$
- **Cómo se calcula (esperanza de una transformación):**
$$
\mu_r'=\sum_{x}x^{r}\,p_X(x)\quad\text{(discreta)},\qquad
\mu_r'=\int_{-\infty}^{\infty}x^{r}f_X(x)\,dx\quad\text{(continua)}
$$
- **Casos que se usan:**
$$
\mu_0'=E(X^{0})=1,\qquad \mu_1'=E(X),\qquad \mu_2'=E(X^{2}),\qquad \mu_3'=E(X^{3})
$$

> **🔤 Diccionario:**
> - $r$: orden del momento (entero; el curso usa $r=0,1,2,3$).
> - $\mu_r'$: momento de orden $r$ **respecto al origen** (lleva prima).
> - $x$: valor que toma la variable; $x^{r}$ es el valor **transformado**.
> - $p_X(x)$: función de masa (caso discreto).
> - $f_X(x)$: función de densidad (caso continuo).
> - Existe solo si la serie o integral **converge absolutamente**.

---

### B. Momentos con respecto a la media (centrales)

- **Definición (requiere que $E(X)$ exista):**
$$
\mu_r=E\left[\left(X-E(X)\right)^{r}\right]
$$
- **Cálculo:**
$$
\mu_r=\sum_{x}\left(x-E(X)\right)^{r}p_X(x)\qquad\text{o}\qquad
\mu_r=\int_{-\infty}^{\infty}\left(x-E(X)\right)^{r}f_X(x)\,dx
$$
- **Casos:**
$$
\mu_1=E\left[X-E(X)\right]=0,\qquad \mu_2=E\left[\left(X-E(X)\right)^{2}\right]=V(X)
$$
- **Caso general con una constante $c$ (en lugar de la media):**
$$
\mu_r(c)=E\left[\left(X-c\right)^{r}\right]
$$

> **🔤 Diccionario:**
> - $\mu_r$: momento central de orden $r$ (**sin** prima).
> - $X-E(X)$: **desviación** del valor respecto a la media; tiene magnitud **y signo**.
> - $\mu_1=0$: las desviaciones positivas y negativas se compensan (por eso $\mu_1$ no mide dispersión).
> - $\mu_2$: promedio de las desviaciones **al cuadrado** → no se cancelan.

---

### C. Lema de existencia de momentos

- **Enunciado:** si $\mu_r'$ existe, entonces $\mu_s'$ existe para todo $s$ real con $0\le s\le r$.
- **Idea de la demostración (caso continuo):**
$$
\lvert x\rvert^{s}\le 1+\lvert x\rvert^{r}\quad(0\le s\le r)
$$
$$
\int_{-\infty}^{\infty}\lvert x\rvert^{s}f_X(x)\,dx\le\int_{-\infty}^{\infty}\left(1+\lvert x\rvert^{r}\right)f_X(x)\,dx=1+\int_{-\infty}^{\infty}\lvert x\rvert^{r}f_X(x)\,dx<+\infty
$$

> **🔤 Diccionario:**
> - $\lvert x\rvert^{s}$: valor absoluto elevado a $s$; se usa para que las dos integrales sean comparables aunque $x<0$.
> - $1+\lvert x\rvert^{r}$: cota que funciona en **ambos** tramos (si $\lvert x\rvert\ge1$ crece como $\lvert x\rvert^{r}$; si $\lvert x\rvert<1$, el $1$ la domina).
> - Conclusión operativa: **si el momento de orden alto existe, los de orden menor también**. Lo recíproco es falso.

---

### D. Varianza y desviación estándar

- **Varianza (segundo momento central):**
$$
V(X)=\mu_2=E\left[\left(X-E(X)\right)^{2}\right]
$$
- **Fórmula recurrente (la que más se usa):**
$$
V(X)=E\left(X^{2}\right)-\left[E(X)\right]^{2}=\mu_2'-\left(\mu_1'\right)^{2}
$$
- **Desviación estándar (o típica):**
$$
\sigma_X=\sqrt{V(X)}
$$
- **Propiedades:**
$$
V(c)=0,\qquad V(X+c)=V(X),\qquad V(aX)=a^{2}V(X),\qquad V(aX+b)=a^{2}V(X)
$$

> **🔤 Diccionario:**
> - $V(X)$: varianza; se escribe también $\operatorname{Var}(X)$ o $\sigma_X^{2}$.
> - $E(X^{2})$: segundo momento respecto al **origen**.
> - $\left[E(X)\right]^{2}$: media **al cuadrado** (no confundir con $E(X^{2})$).
> - $a,b$: constantes; $b$ (traslación) **no** afecta la varianza.
> - Unidades: la varianza va en **unidades al cuadrado**; $\sigma$ en **unidades lineales**.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — Deducción de la fórmula recurrente (linealidad de $E$)**
$$
V(X)=E\left[(X-\mu)^{2}\right]=E\left[X^{2}-2\mu X+\mu^{2}\right]=E(X^{2})-2\mu E(X)+\mu^{2}=E(X^{2})-2\mu^{2}+\mu^{2}=E(X^{2})-\mu^{2}
$$

**🟢 Regla 2 — $\mu_1=0$ siempre (y por qué no sirve)**
- Las desviaciones a izquierda son negativas y a la derecha positivas; sumadas se compensan.
- Para medir dispersión hay que **quitar el signo**: se eleva al cuadrado (no valor absoluto, porque el cuadrado es derivable y acentúa las desviaciones grandes).

**🟢 Regla 3 — Varianza vs. desviación estándar**

| Criterio | Varianza $V(X)$ | Desviación estándar $\sigma_X$ |
|---|---|---|
| Unidades | unidades al cuadrado | unidades **lineales** |
| Interpretable | ✗ (no se sabe qué es "pesos al cuadrado") | ✓ (distancia) |
| Uso | cálculo algebraico | interpretación y reporte |
| Relación | — | $\sigma_X=\sqrt{V(X)}$ |

**🟢 Regla 4 — Interpretación del intervalo $\mu\pm\sigma$**
- Los valores entre $E(X)-\sigma_X$ y $E(X)+\sigma_X$ son los **más parecidos a la media**.
- **Varianza grande** → los valores están lejos de la media y, por tanto, **lejos entre sí** (variable muy dispersa).
- **Varianza pequeña** → los valores se concentran cerca de la media.

**⚠️ Errores de notación que se califican mal**
- $\mu_r'$ (**con** prima) = respecto al origen. $\mu_r$ (**sin** prima) = respecto a la media.
- $E(X^{2})\ne\left[E(X)\right]^{2}$: la diferencia **es** la varianza.
- $\mu_1'=E(X)$ pero $\mu_1=0$.
- $V(2X)=4V(X)$, **no** $2V(X)$.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 📐 A. Algoritmo para un momento respecto al origen $\mu_r'$

1. **Radar:** piden $E(X^{r})$ → momento respecto al origen.
2. **Identifica** el tipo de variable (discreta → suma; continua → integral) y su soporte.
3. **Transforma** cada valor: $x^{r}$.
4. **Pondera** por $p_X(x)$ o $f_X(x)$ y suma o integra.
5. **Verifica:** para $r=0$ debe dar $1$; si $r=1$ debe coincidir con el $E(X)$ ya calculado.

**Plantilla (dado corriente, $p=1/6$):**
$$
\mu_2'=E(X^{2})=\frac{1}{6}\left(1^{2}+2^{2}+3^{2}+4^{2}+5^{2}+6^{2}\right)=\frac{91}{6}\approx 15{,}1667
$$

---

### 📊 B. Algoritmo para la varianza (vía recurrente)

1. **Calcula** $\mu_1'=E(X)$.
2. **Calcula** $\mu_2'=E(X^{2})$.
3. **Aplica** $V(X)=\mu_2'-\left(\mu_1'\right)^{2}$.
4. **Verifica:** $V(X)\ge 0$; si $X$ es constante debe dar $0$; y $V(aX+b)=a^{2}V(X)$.

**Plantilla (dado corriente):**
$$
V(X)=\frac{91}{6}-\left(\frac{7}{2}\right)^{2}=\frac{91}{6}-\frac{49}{4}=\frac{182-147}{12}=\frac{35}{12}\approx 2{,}9167
$$

---

### ∫ C. Algoritmo para la varianza (vía definición, variable continua)

1. **Calcula** $E(X)$.
2. **Plantea** $\displaystyle\int_{\text{soporte}}\left(x-E(X)\right)^{2}f_X(x)\,dx$.
3. **Desarrolla** el cuadrado o usa la recurrente (más rápido).
4. **Verifica** que coincida por las dos vías.

**Plantilla ($f_X(x)=\frac{x}{2}$ en $(0,2)$):**
$$
E(X)=\int_{0}^{2}x\cdot\frac{x}{2}\,dx=\frac{4}{3},\qquad
E(X^{2})=\int_{0}^{2}x^{2}\cdot\frac{x}{2}\,dx=2
$$
$$
V(X)=2-\left(\frac{4}{3}\right)^{2}=2-\frac{16}{9}=\frac{2}{9}\approx 0{,}2222
$$

---

### 📏 D. Algoritmo para la desviación estándar y su lectura

1. **Saca raíz:** $\sigma_X=\sqrt{V(X)}$.
2. **Redondea** con la misma precisión que los datos.
3. **Construye** el intervalo $\left[E(X)-\sigma_X,\ E(X)+\sigma_X\right]$.
4. **Interpreta** en unidades del problema (puntos, horas, pesos…).

**Plantillas de la clase:**

| Variable | $E(X)$ | $V(X)$ | $\sigma_X$ | Intervalo $\mu\pm\sigma$ |
|---|---|---|---|---|
| Dado corriente | $3{,}5$ | $\frac{35}{12}\approx 2{,}9167$ | $\sqrt{\frac{35}{12}}\approx 1{,}7078$ | $\left[1{,}79;\ 5{,}21\right]$ |
| $f(x)=\frac{x}{2}$, $x\in(0,2)$ | $\frac{4}{3}\approx 1{,}3333$ | $\frac{2}{9}\approx 0{,}2222$ | $\frac{\sqrt{2}}{3}\approx 0{,}4714$ | $\left[0{,}86;\ 1{,}80\right]$ |

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿La potencia se pide respecto al **origen** o respecto a la **media**? (prima o sin prima)
- [ ] ¿Usé $p_X(x)$ si es discreta y $f_X(x)$ si es continua, solo sobre el **soporte**?
- [ ] ¿Calculé $E(X^{2})$ **antes** de restar $\left[E(X)\right]^{2}$?
- [ ] ¿El resultado es $\ge 0$? (una varianza negativa es siempre un error)
- [ ] ¿Reporté la **desviación estándar** cuando piden interpretación en unidades?
- [ ] ¿Mantuve $\mu_1'=E(X)$ separado de $\mu_1=0$?
- [ ] ¿Verifiqué con los casos base $\mu_0'=1$ y la propiedad $V(aX+b)=a^{2}V(X)$?
