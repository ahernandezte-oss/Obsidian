# 📘 CHEATSHEET — PROBABILIDAD · 04/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261104_EXPONENCIAL_BETA.md`
> - **Fecha de transcripción:** 04/11/2026 (`AAMMDD` = `261104`)
> - **Tema principal:** EXPONENCIAL Y BETA — Exponencial como caso $r=1$ de Gamma · falta de memoria · función beta · distribución Beta
> - **Fuente:** transcripción de clase. Complementos marcados con `➕`.
> - **Clase anterior:** `261028_MODELOS_CONTINUOS` (Gamma, Erlang, Ji-cuadrado). Esta clase **retoma Gamma y cierra el caso $r=1$**, luego abre Beta.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261104_EXPONENCIAL_BETA` §2.D».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Qué representa la variable?**
   - Un **tiempo hasta un evento** o **tiempo entre dos eventos** → **Exponencial** (o Gamma si son $r$ eventos).
   - Una **fracción, proporción o porcentaje** que vive entre $0$ y $1$ → **Beta**.
   - Un **conteo** de eventos en un intervalo → **Poisson** (clase anterior).
2. **Paso 1 — ¿Aparece la palabra "dado que ya…"?** → **falta de memoria** (§2.B), no integres.
3. **Paso 2 — ¿Dan la media o la tasa?** Si dan $E(X)$, entonces $\lambda=\frac{1}{E(X)}$.
4. **Paso 3 — ¿Piden cola ("más de", "al menos")?** → usa $e^{-\lambda x}$ directamente.

**Tabla de decisión (frase del enunciado → modelo → bloque donde está la fórmula):**

| Si el enunciado dice… | Modelo | Fórmula clave | 👉 Ir a |
|---|---|---|---|
| "tiempo de vida", "tiempo hasta la primera falla", "tiempo entre llegadas" de un proceso de Poisson | **Exponencial** | $f(x)=\lambda e^{-\lambda x}$ | **§2.A** |
| dan la **esperanza** del tiempo (ej.: "esperanza de vida de 200 horas") | **Exponencial** con $\lambda=\frac{1}{E(X)}$ | $\lambda=\frac{1}{E(X)}$ | **§2.A** + **§4.A** |
| "**dado que** ya duró…", "si ya lleva funcionando…", "no ha ocurrido todavía" | **Falta de memoria** | $P(X>x+t\mid X>t)=P(X>x)$ | **§2.B** + **§4.B** |
| "**proporción**, fracción, porcentaje, parte de" que está entre $0$ y $1$ | **Beta** | $f(x)=\frac{1}{B(a,b)}x^{a-1}(1-x)^{b-1}$ | **§2.D** |
| "proporción" y piden $E(X)$ o $V(X)$ | **Beta** | $E(X)=\frac{a}{a+b}$ | **§2.D** + **§4.D** |
| dice que la proporción es **uniforme en $(0,1)$** | **Beta con $a=b=1$** | $f(x)=1$ | **§3 Caso 2** |
| menciona **"Erlang"** | **Gamma** con $r$ entero | $\Gamma(r)=(r-1)!$ | **§3 Caso 0** |
| menciona **"Ji-cuadrado"** | **Gamma** con $\lambda=\frac12$, $r=\frac{k}{2}$ | $E(X)=k$, $V(X)=2k$ | **§3 Caso 1** |
| "gama" con $r=1$ | **Exponencial** | $f(x)=\lambda e^{-\lambda x}$ | **§3 Caso 3** |

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Exponencial (Gamma con $r=1$)

- **Condición:** $X$ = tiempo hasta el primer evento de un proceso de Poisson de intensidad $\lambda$.
- **PDF:**
$$
f(x)=\lambda e^{-\lambda x}\quad\text{para } x>0,\qquad f(x)=0 \text{ en otro caso}
$$
- **FDA (deducida en clase):**
$$
F(x)=P(X\le x)=
\begin{cases}
0 & x\le 0\\[2pt]
1-e^{-\lambda x} & x>0
\end{cases}
$$
- **Cola:**
$$
P(X>x)=1-F(x)=e^{-\lambda x}\quad(x>0)
$$
- **FGM:** $m_X(t)=\left(1-\frac{t}{\lambda}\right)^{-1}$ para $t<\lambda$
- **Media:** $E(X)=\dfrac{1}{\lambda}$
- **Varianza:** $V(X)=\dfrac{1}{\lambda^{2}}$

> **🔤 Diccionario:**
> - $x$: tiempo acumulado (horas, minutos, km…) hasta el evento.
> - $\lambda$: intensidad o tasa de eventos **por unidad de tiempo**; $\lambda>0$.
> - $e$: constante de Euler ($\approx 2{,}71828$).
> - $\lambda x$: exponente **adimensional**; si $\lambda$ está en $\mathrm{h^{-1}}$, $x$ va en horas.
> - ⚠️ El profesor llama a $\lambda$ "parámetro de escala", pero en su fórmula opera como **tasa** (eventos por unidad de tiempo). Con la media: $\lambda=\frac{1}{E(X)}$.

---

### B. Falta de memoria (teorema de la clase)

- **Hipótesis:** $X$ continua con $P(X>0)=1$ (solo toma valores positivos) y $\lambda>0$.
- **Enunciado (doble implicación):**
$$
X\sim\text{Exp}(\lambda)\iff P(X>x+t\mid X>t)=P(X>x)\quad\text{para todo } x,t>0
$$
- **Demostración (la de clase, en 3 líneas):**
$$
P(X>x+t\mid X>t)=\frac{P\big(\{X>x+t\}\cap\{X>t\}\big)}{P(X>t)}=\frac{P(X>x+t)}{P(X>t)}=\frac{e^{-\lambda(x+t)}}{e^{-\lambda t}}=e^{-\lambda x}=P(X>x)
$$
- **Lectura operativa:** el tiempo ya transcurrido **no informa nada** sobre el tiempo que falta. Solo importa el tramo restante.

> **🔤 Diccionario:**
> - $x$: tiempo adicional que se quiere medir (lo que "falta").
> - $t$: tiempo ya transcurrido (el dato condicional).
> - $x+t$: tiempo total desde el origen.
> - $P(X>x+t\mid X>t)$: probabilidad de superar $x+t$ **sabiendo** que ya se superó $t$.

---

### C. Función Beta

- **Definición:**
$$
B(a,b)=\int_{0}^{1}x^{a-1}(1-x)^{b-1}\,dx\qquad a>0,\ b>0
$$
- **Relación con la función Gamma:**
$$
B(a,b)=\frac{\Gamma(a)\,\Gamma(b)}{\Gamma(a+b)}
$$
- **Simetría:** $B(a,b)=B(b,a)$
- **Casos útiles:** $B(1,1)=1$, $B(a,1)=\dfrac{1}{a}$
- **Con enteros:** $B(a,b)=\dfrac{(a-1)!\,(b-1)!}{(a+b-1)!}$

> **🔤 Diccionario:**
> - $a$: primer parámetro de forma (positivo).
> - $b$: segundo parámetro de forma (positivo).
> - $x$: variable de integración en $(0,1)$.
> - $\Gamma(\cdot)$: función gamma; $\Gamma(n)=(n-1)!$ si $n$ es entero.

---

### D. Distribución Beta

- **Condición:** $X$ toma valores en $(0,1)$ y modela **proporciones o fracciones**.
- **PDF:**
$$
f(x)=\frac{1}{B(a,b)}\,x^{a-1}(1-x)^{b-1}\quad(0<x<1),\qquad f(x)=0 \text{ en otro caso}
$$
- **Momento de orden $r$ (fórmula general de la clase):**
$$
E(X^{r})=\frac{\Gamma(r+a)\,\Gamma(a+b)}{\Gamma(r+a+b)\,\Gamma(a)}
$$
- **Media:** $E(X)=\dfrac{a}{a+b}$
- **Segundo momento:** $E(X^{2})=\dfrac{a(a+1)}{(a+b)(a+b+1)}$
- **Varianza:**
$$
V(X)=\frac{ab}{(a+b)^{2}(a+b+1)}
$$

> **🔤 Diccionario:**
> - $x$: proporción observada ($0<x<1$).
> - $a,b$: parámetros de forma; **los da el enunciado** o los estima el estadístico (no se deducen del texto de probabilidad).
> - $B(a,b)$: constante normalizadora (función beta).
> - $r$: orden del momento ($r=1$ media, $r=2$ segundo momento).
> - Nota: la Beta **no** tiene FGM cómoda → para momentos se usa $E(X^{r})$.

---

### E. Puente con el proceso de Poisson (de dónde sale todo)

- **Conteo:** $N(t)$ = número de eventos en $[0,t]$ → $N(t)\sim\text{Poisson}(\lambda t)$.
- **Tiempo entre eventos:** $\sim\text{Exp}(\lambda)$, **con la misma** $\lambda$.
- **Tiempo hasta el $r$-ésimo evento:** $\sim\text{Gamma}(r,\lambda)$. Con $r=1$ → Exponencial.
- **Consecuencia operativa:** si el enunciado da "llamadas por hora", esa $\lambda$ sirve tal cual para el tiempo entre llamadas **en horas**; si piden minutos, reescala.

> **🔤 Diccionario:**
> - $N(t)$: conteo acumulado de eventos hasta el instante $t$.
> - $\lambda$: intensidad del proceso (compartida por Poisson, Exponencial y Gamma).
> - $r$: número de eventos acumulados.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Caso 0 — Erlang**
- Condición: $r$ entero positivo. En la PDF se reemplaza $\Gamma(r)$ por $(r-1)!$.

**🟢 Caso 1 — Ji-cuadrado**
- Condición: $\lambda=\frac12$, $r=\frac{k}{2}$ ($k$ = grados de libertad).
- $E(X)=k$, $V(X)=2k$, $m_X(t)=(1-2t)^{-k/2}$ para $t<\frac12$.

**🟢 Caso 2 — Beta con $a=b=1$ = Uniforme en $(0,1)$**
$$
B(1,1)=\frac{\Gamma(1)\Gamma(1)}{\Gamma(2)}=\frac{1\cdot 1}{1}=1\;\Longrightarrow\;f(x)=1\quad(0<x<1)
$$
- Verificación por momentos: $E(X)=\frac{1}{2}$, $V(X)=\frac{1\cdot 1}{2^{2}\cdot 3}=\frac{1}{12}$ (media y varianza de la uniforme en $(0,1)$).

**🟢 Caso 3 — Gamma con $r=1$ = Exponencial (deducción de clase)**
$$
f(x)=\frac{\lambda^{r}}{\Gamma(r)}x^{r-1}e^{-\lambda x}\;\xrightarrow{\;r=1\;}\;\frac{\lambda}{\Gamma(1)}x^{0}e^{-\lambda x}=\lambda e^{-\lambda x}
$$
- Coherencia: $E(X)=\frac{r}{\lambda}=\frac{1}{\lambda}$ y $V(X)=\frac{r}{\lambda^{2}}=\frac{1}{\lambda^{2}}$.

**⚠️ Cuándo NO usar la exponencial**
- Edad o tiempo de vida de **personas**: la expectativa futura **sí depende** de la edad actual → no hay falta de memoria.
- Fenómenos con **desgaste** (un componente que envejece): la tasa de falla crece con el tiempo.
- La exponencial exige **tasa constante**; si el riesgo cambia, no aplica.

**📐 Valores de $\Gamma$ que se usan al vuelo**
| $\Gamma(n)$ | Valor |
|---|---|
| $\Gamma(1)=0!$ | $1$ |
| $\Gamma(2)=1!$ | $1$ |
| $\Gamma(3)=2!$ | $2$ |
| $\Gamma(4)=3!$ | $6$ |
| $\Gamma(5)=4!$ | $24$ |
| $\Gamma(6)=5!$ | $120$ |
| Recursión | $\Gamma(n+1)=n\,\Gamma(n)$ |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### ⏱️ A. Algoritmo Exponencial (tiempos)

1. **Radar:** tiempo hasta un evento / entre eventos → Exp$(\lambda)$.
2. **Extrae $\lambda$:** si dan la tasa, ya está; si dan la **media**, $\lambda=\frac{1}{E(X)}$.
3. **Escribe** $f(x)=\lambda e^{-\lambda x}$ y $F(x)=1-e^{-\lambda x}$.
4. **Traduce:** "más de $t$" → $e^{-\lambda t}$; "a lo sumo $t$" → $1-e^{-\lambda t}$; "entre $a$ y $b$" → $F(b)-F(a)$.
5. **Verifica:** el resultado está en $[0,1]$ y $E(X)$ coincide con el dato.

**Plantilla (ejemplo de clase):** esperanza de vida $E(X)=200$ h → $\lambda=\frac{1}{200}$, $F(x)=1-e^{-x/200}$.
$$
P(X>200)=e^{-200/200}=e^{-1}\approx 0{,}3679
$$

---

### 🔁 B. Algoritmo Falta de memoria (condicionales)

1. **Verifica** que la variable sea exponencial (o que el enunciado pida explícitamente la propiedad).
2. **Escribe la condicional:** $P(X>\,\text{total}\mid X>\text{transcurrido})$.
3. **Resta:** lo que falta es $\text{total}-\text{transcurrido}$.
4. **Aplica:** resultado $=e^{-\lambda(\text{total}-\text{transcurrido})}$.
5. **Verifica** con la definición: $\dfrac{e^{-\lambda\cdot\text{total}}}{e^{-\lambda\cdot\text{transcurrido}}}$ debe dar lo mismo.

**Plantilla (ejemplo de clase):** $\lambda=\frac{1}{200}$, $P(X>200\mid X>150)$; el total $200=150+50$, así que
$$
P(X>50)=e^{-50/200}=e^{-1/4}\approx 0{,}7788\;(77{,}88\,\%)
$$
El 78 % de las componentes que ya duraron 150 horas también alcanzan las 200.

---

### 🎯 C. Algoritmo Beta (probabilidades de proporciones)

1. **Radar:** proporción, fracción o porcentaje en $(0,1)$ → Beta$(a,b)$.
2. **Identifica** $a$ y $b$ (los da el enunciado).
3. **Calcula** $B(a,b)=\dfrac{(a-1)!\,(b-1)!}{(a+b-1)!}$ usando factoriales.
4. **Escribe la PDF:** $f(x)=\frac{1}{B(a,b)}x^{a-1}(1-x)^{b-1}$.
5. **Integra** en el intervalo pedido; si es cola "más de $c$", calcula $1-\int_0^{c}f$.
6. **Verifica:** densidad integra $1$ y el resultado está en $[0,1]$.

**Plantilla (ejemplo de clase):** $X\sim\text{Beta}(4,2)$.
$$
B(4,2)=\frac{\Gamma(4)\Gamma(2)}{\Gamma(6)}=\frac{3!\,1!}{5!}=\frac{6}{120}=\frac{1}{20}\;\Longrightarrow\;f(x)=20x^{3}(1-x)
$$
$$
P(X>0{,}9)=1-20\int_{0}^{0{,}9}x^{3}(1-x)\,dx=1-20\left[\frac{x^{4}}{4}-\frac{x^{5}}{5}\right]_{0}^{0{,}9}=1-0{,}91854=0{,}08146
$$

---

### 📊 D. Algoritmo Beta (momentos)

1. **Media:** $E(X)=\dfrac{a}{a+b}$.
2. **Si piden varianza:** $V(X)=\dfrac{ab}{(a+b)^{2}(a+b+1)}$.
3. **Si piden el segundo momento:** $E(X^{2})=\dfrac{a(a+1)}{(a+b)(a+b+1)}$.
4. **Verifica** con $a=b=1$ → $E=\frac12$, $V=\frac{1}{12}$ (uniforme).
5. **Interpreta:** una proporción con $E(X)=0{,}6$ significa que en promedio se cubre el 60 %.

**Plantilla (ejemplo de clase):** $a=4$, $b=2$.
$$
E(X)=\frac{4}{6}=\frac{2}{3}\approx 0{,}667,\qquad
V(X)=\frac{4\cdot 2}{6^{2}\cdot 7}=\frac{8}{252}=\frac{2}{63}\approx 0{,}0317
$$
Desviación estándar $\sigma=\sqrt{0{,}0317}\approx 0{,}178$, es decir, la semana típica vende entre $0{,}49$ y $0{,}85$ de lo almacenado.

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿La variable es un **tiempo** (exponencial), una **proporción** (beta) o un **conteo** (Poisson)?
- [ ] Si dan la media, ¿convertí con $\lambda=\frac{1}{E(X)}$?
- [ ] ¿La pregunta dice "**dado que**"? Entonces uso falta de memoria y **solo el tramo que falta**.
- [ ] ¿$\lambda$ y $x$ están en **las mismas unidades**? (el exponente $\lambda x$ debe ser adimensional)
- [ ] En Beta: ¿calculé $B(a,b)$ con factoriales y lo puse en el **denominador** de la PDF?
- [ ] ¿El resultado está entre $0$ y $1$ y la densidad integra $1$?
- [ ] ¿Revisé el caso particular (Beta$(1,1)$ = uniforme; Gamma$(1,\lambda)$ = exponencial) para detectar errores?
