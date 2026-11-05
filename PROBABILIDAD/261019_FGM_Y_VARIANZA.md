# 📘 CHEATSHEET — PROBABILIDAD · 19/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261019_FGM_Y_VARIANZA.md`
> - **Fecha de transcripción:** 19/10/2026 (`AAMMDD` = `261019`)
> - **Tema principal:** FGM Y VARIANZA — propiedades de la varianza · función generadora de momentos · momentos por derivación · unicidad
> - **Fuente:** transcripción de clase. Complementos marcados con `➕`.
> - **Continuidad:** viene de `261014_MOMENTOS_Y_VARIANZA` (momentos y varianza por definición). Antecede a `261028_MODELOS_CONTINUOS` (allí la FGM de la Gamma da directamente $E$ y $V$).
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261019_FGM_Y_VARIANZA` §2.C».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Piden $V(X)$ o piden la FGM?**
   - $V(X)$ con $E(X)$ ya conocido → fórmula recurrente (§2.A).
   - $V(X)$ sin momentos → definición o derivando la FGM.
2. **Paso 1 — ¿Aparece $E\left(e^{tX}\right)$, "$m_X(t)$" o "función generadora de momentos"?** → FGM (§2.B).
3. **Paso 2 — ¿Dicen "use la FGM" o "halle los momentos a partir de $m_X(t)$"?** → derivar y evaluar en $t=0$ (§2.C + §4).
4. **Paso 3 — ¿Solo piden propiedades ($V(aX+b)$, $V(c)$…) o un valor numérico?** → propiedades (§2.D) frente a cálculo.

**Tabla de decisión (frase del enunciado → qué es → bloque donde está la fórmula):**

| Si el enunciado dice… | Qué es | Fórmula | 👉 Ir a |
|---|---|---|---|
| "halle la varianza" y ya se conoce $E(X)$ y $E(X^{2})$ | fórmula recurrente | $V(X)=E(X^{2})-\left[E(X)\right]^{2}$ | **§2.A** + **§4.A** |
| "halle la varianza" desde la densidad / masa y no se conocen los momentos | definición | $V(X)=E\left[(X-E(X))^{2}\right]$ | **§2.A** + **§4.B** |
| "función generadora de momentos", "$m_X(t)$", "$E\left(e^{tX}\right)$" | FGM | $m_X(t)=E\left(e^{tX}\right)$ | **§2.B** |
| "obtenga $E(X)$ y $V(X)$ **usando la FGM**" | derivadas en $t=0$ | $m_X^{(r)}(0)=E\left(X^{r}\right)$ | **§2.C** + **§4.C** |
| "dos variables con la misma $m_X(t)$…" | unicidad | $m_X=m_Y\Rightarrow$ misma distribución | **§2.C** |
| "¿la FGM siempre existe?" | condición de existencia | existe para $t$ en un entorno de $0$ | **§2.B** + **§3** |
| "verifique $V(aX+b)$" / "¿cómo se transforma la varianza?" | propiedades | $V(aX+b)=a^{2}V(X)$ | **§2.D** |
| "menciona **función característica**" | $\varphi_X(t)=E\left(e^{itX}\right)$ | siempre existe | **§3 Regla 5** |
| piden la FGM de Poisson, exponencial o binomial | tabla | ver tabla de §2.E | **§2.E** |

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Varianza (recuento operativo)

- **Definición:**
$$
V(X)=E\left[\left(X-E(X)\right)^{2}\right]
$$
- **Fórmula recurrente (la más rápida):**
$$
V(X)=E\left(X^{2}\right)-\left[E(X)\right]^{2}
$$
- **Cálculo:**
$$
V(X)=\sum_{x}\left(x-E(X)\right)^{2}p_X(x)\qquad\text{o}\qquad
V(X)=\int_{-\infty}^{\infty}\left(x-E(X)\right)^{2}f_X(x)\,dx
$$

> **🔤 Diccionario:**
> - $V(X)$: varianza; también $\operatorname{Var}(X)$ o $\sigma_X^{2}$.
> - $E(X^{2})$: segundo momento respecto al origen.
> - $\left[E(X)\right]^{2}$: la media al cuadrado (**no** es $E(X^{2})$).
> - $p_X(x)$: función de masa (discreta); $f_X(x)$: densidad (continua).

---

### B. Función generadora de momentos (FGM)

- **Definición (existe si hay un entorno de $0$ donde la esperanza es finita):**
$$
m_X(t)=E\left(e^{tX}\right)
$$
- **Cálculo:**
$$
m_X(t)=\sum_{x}e^{tx}\,p_X(x)\qquad\text{o}\qquad
m_X(t)=\int_{-\infty}^{\infty}e^{tx}f_X(x)\,dx
$$
- **Dominio:** existe para $t\in(-h,h)$ con $h>0$; **no siempre existe**.

> **🔤 Diccionario:**
> - $m_X(t)$: FGM de $X$; es función de $t$, **no** de $X$ (la $X$ se integra o suma y desaparece).
> - $t$: variable real de la transformada; no es un dato del problema.
> - $e^{tX}$: la transformación a la que se le toma esperanza.
> - $h$: radio del intervalo alrededor de $0$ donde la integral/serie converge absolutamente.

---

### C. Propiedades de la FGM (las tres que se usaron)

- **1. Existencia de momentos:** si $m_X(t)$ existe en un entorno de $0$, entonces **existen todos** los momentos $\mu_r'=E(X^{r})$.
- **2. Derivadas en cero (la propiedad operativa):**
$$
m_X^{(r)}(0)=\frac{d^{r}}{dt^{r}}m_X(t)\Big|_{t=0}=E\left(X^{r}\right)
$$
- **3. Unicidad:** si $m_X(t)=m_Y(t)$ en un entorno de $0$, entonces $X$ y $Y$ tienen **la misma distribución**.

> **🔤 Diccionario:**
> - $m_X^{(r)}(0)$: derivada $r$-ésima evaluada en $t=0$.
> - $r=1$ da $E(X)$; $r=2$ da $E(X^{2})$ (con este se obtiene $V$).
> - Unicidad: la FGM **identifica** la distribución (es una "huella digital").
> - La recíproca de la propiedad 1 **no** vale: pueden existir todos los momentos y no existir la FGM.

---

### D. Propiedades de la varianza

$$
V(X)\ge 0
$$
$$
V(c)=0\quad\text{si } P(X=c)=1
$$
$$
V(aX)=a^{2}V(X)
$$
$$
V(X+a)=V(X)\quad\text{(trasladar no cambia la dispersión)}
$$
$$
V(X)=0\iff P\left(X=E(X)\right)=1\quad\text{(la variable es constante)}
$$

> **🔤 Diccionario:**
> - $a,c$: constantes reales.
> - $V(aX+b)=a^{2}V(X)$: la varianza **no es lineal**; el desplazamiento $b$ desaparece.
> - $P\left(X=E(X)\right)=1$: la variable toma **casi seguramente** un único valor.

---

### E. Tabla de FGM, momentos y varianza

| Distribución | $m_X(t)$ | $E(X)$ | $E(X^{2})$ | $V(X)$ |
|---|---|---|---|---|
| Poisson $(\lambda)$ | $e^{\lambda\left(e^{t}-1\right)}$ | $\lambda$ | $\lambda^{2}+\lambda$ | $\lambda$ |
| Exponencial $(\lambda)$ | $\left(1-\frac{t}{\lambda}\right)^{-1}$, $t<\lambda$ | $\frac{1}{\lambda}$ | $\frac{2}{\lambda^{2}}$ | $\frac{1}{\lambda^{2}}$ |
| Binomial $(n,p)$ | $\left(pe^{t}+1-p\right)^{n}$ | $np$ | $n(n-1)p^{2}+np$ | $np(1-p)$ |
| ➕ Gamma $(r,\lambda)$ | $\left(1-\frac{t}{\lambda}\right)^{-r}$, $t<\lambda$ | $\frac{r}{\lambda}$ | $\frac{r(r+1)}{\lambda^{2}}$ | $\frac{r}{\lambda^{2}}$ |

> **🔤 Diccionario:**
> - $\lambda$: parámetro de Poisson (conteo) o de la exponencial (tasa de tiempo).
> - $n$: número de ensayos; $p$: probabilidad de éxito; $q=1-p$.
> - $r$: parámetro de forma de la Gamma (fila ➕ vista en `261028_MODELOS_CONTINUOS`).
> - Todas se leen **como potencia base elevada**: en la exponencial conviene escribir $\left(1-\frac{t}{\lambda}\right)^{-1}$ para derivar como potencia.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — La varianza no mide dónde, mide cuán lejos**
- Dos variables con la **misma media** pueden tener **varianzas muy distintas**: el esperado es una medida de **ubicación**; la varianza, de **dispersión**.
- $V(X)$ pequeño → valores concentrados cerca de $E(X)$; $V(X)$ grande → valores dispersos.

**🟢 Regla 2 — Cómo derivar la FGM sin equivocarse**
- Escríbela siempre como **potencia**: $\left(1-\frac{t}{\lambda}\right)^{-1}$ en lugar de $\frac{\lambda}{\lambda-t}$ (así se deriva con la regla de la cadena, sin cocientes).
- Deriva, **evalúa en $t=0$** (todo lo que tenga $t$ se va), y usa $V=m''(0)-\left[m'(0)\right]^{2}$.

**🟢 Regla 3 — Tres resultados de la clase (memorizar)**
- Poisson: $E(X^{2})=\lambda^{2}+\lambda$ → $V(X)=\lambda$ (**media igual a varianza**).
- Exponencial: $E(X^{2})=\frac{2}{\lambda^{2}}$ → $V(X)=\frac{1}{\lambda^{2}}=\left[E(X)\right]^{2}$.
- Binomial: $E(X^{2})=n(n-1)p^{2}+np$ → $V(X)=np(1-p)$.

**🟢 Regla 4 — Deducción de $E(X^{2})$ de Poisson (truco de la clase)**
$$
x^{2}=x(x-1)+x\;\Longrightarrow\;E(X^{2})=\sum_{x\ge 0}x(x-1)\frac{e^{-\lambda}\lambda^{x}}{x!}+\sum_{x\ge 0}x\frac{e^{-\lambda}\lambda^{x}}{x!}=\lambda^{2}+\lambda
$$
(con el cambio $x=j+1$ en la primera suma).

**🟢 Regla 5 — ¿Qué pasa si la FGM no existe?**
- Usar la **función característica** $\varphi_X(t)=E\left(e^{itX}\right)$: **siempre existe** y también caracteriza unívocamente la distribución.
- Diferencia clave: $m_X(t)$ puede no existir; $\varphi_X(t)$ nunca falla.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 📊 A. Algoritmo para $V(X)$ por la fórmula recurrente

1. **Calcula** $\mu_1'=E(X)$.
2. **Calcula** $\mu_2'=E(X^{2})$ (por suma o integral de $x^{2}$).
3. **Aplica** $V(X)=\mu_2'-\left(\mu_1'\right)^{2}$.
4. **Verifica** que $V\ge 0$ y que coincida con la varianza teórica del modelo.

**Plantilla (Poisson):**
$$
E(X)=\lambda,\quad E(X^{2})=\lambda^{2}+\lambda\;\Longrightarrow\;V(X)=\lambda^{2}+\lambda-\lambda^{2}=\lambda
$$

---

### ∫ B. Algoritmo para $V(X)$ por definición (variable continua)

1. **Calcula** $E(X)$.
2. **Plantea** $\displaystyle\int\left(x-E(X)\right)^{2}f_X(x)\,dx$ o la versión recurrente.
3. **Integra por partes** cuando aparezca $x^{2}e^{-\lambda x}$.
4. **Verifica** el resultado contra la tabla de §2.E.

**Plantilla (exponencial):**
$$
E(X^{2})=\int_{0}^{\infty}x^{2}\lambda e^{-\lambda x}dx=\frac{2}{\lambda^{2}}\;\Longrightarrow\;V(X)=\frac{2}{\lambda^{2}}-\frac{1}{\lambda^{2}}=\frac{1}{\lambda^{2}}
$$

---

### 🔁 C. Algoritmo FGM → momentos (el que califica el profesor)

1. **Escribe** $m_X(t)$ **como potencia** y anota su dominio.
2. **Deriva una vez** y evalúa en $t=0$ → $E(X)$.
3. **Deriva dos veces** y evalúa en $t=0$ → $E(X^{2})$.
4. **Cierra** con $V(X)=m_X''(0)-\left[m_X'(0)\right]^{2}$.
5. **Verifica** contra la tabla de §2.E.

**Plantilla (exponencial, $\lambda>0$):**
$$
m_X(t)=\left(1-\frac{t}{\lambda}\right)^{-1}
$$
$$
m_X'(t)=\frac{1}{\lambda}\left(1-\frac{t}{\lambda}\right)^{-2}\;\Rightarrow\;m_X'(0)=\frac{1}{\lambda}
$$
$$
m_X''(t)=\frac{2}{\lambda^{2}}\left(1-\frac{t}{\lambda}\right)^{-3}\;\Rightarrow\;m_X''(0)=\frac{2}{\lambda^{2}}
$$
$$
V(X)=\frac{2}{\lambda^{2}}-\frac{1}{\lambda^{2}}=\frac{1}{\lambda^{2}}
$$

---

### 🎲 D. Algoritmo FGM → momentos en una discreta (binomial)

1. **Identifica** los parámetros $n$ y $p$ (¡hay que conocerlos!).
2. **Deriva** $m_X(t)=\left(pe^{t}+1-p\right)^{n}$ con regla de la cadena.
3. **Evalúa en $t=0$**, sabiendo que $e^{0}=1$ → $m'(0)=np$.
4. **Segunda derivada** → $m''(0)=n(n-1)p^{2}+np$.
5. **Varianza:** $V(X)=np(1-p)$.

**Plantilla:**
$$
m_X'(0)=np,\qquad m_X''(0)=n(n-1)p^{2}+np
$$
$$
V(X)=n(n-1)p^{2}+np-(np)^{2}=np-p^{2}n=np(1-p)
$$

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿Me piden **varianza** (con momentos) o **FGM** (transformada)?
- [ ] ¿Escribí la FGM como **potencia** antes de derivar?
- [ ] ¿Evalué las derivadas en $t=0$ y no en otro valor?
- [ ] ¿Usé $V=m''(0)-\left[m'(0)\right]^{2}$ y no $m''(0)-m'(0)$?
- [ ] ¿$V\ge 0$? ¿Coincide con la tabla de §2.E?
- [ ] ¿Identifiqué los **parámetros** ($\lambda$, $n$, $p$) antes de calcular?
- [ ] Si la FGM no existe, ¿usé la **función característica**?
